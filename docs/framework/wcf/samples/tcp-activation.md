---
description: TCP アクティブ化に関する詳細情報
title: TCP アクティベーション
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: bfa98eff1bcab31df3e28d46e77d90456020507c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685635"
---
# <a name="tcp-activation"></a><span data-ttu-id="55736-103">TCP アクティベーション</span><span class="sxs-lookup"><span data-stu-id="55736-103">TCP Activation</span></span>

<span data-ttu-id="55736-104">このサンプルでは、net.tcp プロトコルで通信するサービスをアクティブ化するために、Windows プロセス アクティブ化サービス (WAS) を使用してサービスをホストする方法について示します。</span><span class="sxs-lookup"><span data-stu-id="55736-104">This sample demonstrates hosting a service that uses Windows Process Activation Services (WAS) to activate a service that communicates over the net.tcp protocol.</span></span> <span data-ttu-id="55736-105">このサンプルは、 [はじめに](getting-started-sample.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="55736-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>

> [!NOTE]
> <span data-ttu-id="55736-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55736-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="55736-107">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="55736-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="55736-108">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="55736-108">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="55736-109">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="55736-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="55736-110">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="55736-110">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`

<span data-ttu-id="55736-111">このサンプルは、クライアント コンソール プログラム (.exe) と、WAS によってアクティブ化されるワーカー プロセス内でホストされるサービス ライブラリ (.dll) で構成されています。</span><span class="sxs-lookup"><span data-stu-id="55736-111">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by WAS.</span></span> <span data-ttu-id="55736-112">クライアント アクティビティは、コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="55736-112">Client activity is visible in the console window.</span></span>

<span data-ttu-id="55736-113">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="55736-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="55736-114">コントラクトは `ICalculator` インターフェイスによって定義されており、算術演算 (Add、Subtract、Multiply、および Divide) を公開しています。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="55736-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code:</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="55736-115">このサービス実装は、計算を行い、結果を返します。</span><span class="sxs-lookup"><span data-stu-id="55736-115">The service implementation calculates and returns the appropriate result:</span></span>

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="55736-116">このサンプルでは、TCP ポート共有が有効でセキュリティが無効になっている net.tcp バインディングの変化形を使用します。</span><span class="sxs-lookup"><span data-stu-id="55736-116">The sample uses a variant of the net.tcp binding with TCP port sharing enabled and security turned off.</span></span> <span data-ttu-id="55736-117">セキュリティ保護された TCP バインディングを使用する場合は、サーバーのセキュリティ モードを必要な設定に変更し、クライアントで Svcutil.exe を再実行して更新クライアントの構成ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="55736-117">If you want to use a secured TCP binding, change the server's security mode to the desired setting and re-run Svcutil.exe on the client to generate an update client configuration file.</span></span>

<span data-ttu-id="55736-118">サービスの構成を次のサンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="55736-118">The following sample shows the configuration for the service:</span></span>

```xml
<system.serviceModel>

    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexTcpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netTcpBinding>
        <binding name="PortSharingBinding" portSharingEnabled="true">
          <security mode="None" />
        </binding>
      </netTcpBinding>
    </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

<span data-ttu-id="55736-119">クライアントのエンドポイントが構成されます。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="55736-119">The client's endpoint is configured as shown in the following sample code:</span></span>

```xml
<system.serviceModel>
    <bindings>
        <netTcpBinding>
          <binding name="NetTcpBinding_ICalculator">
            <security mode="None"/>
          </binding>
        </netTcpBinding>
    </bindings>
    <client>
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />
    </client>
</system.serviceModel>
```

<span data-ttu-id="55736-120">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="55736-120">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="55736-121">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="55736-121">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="55736-122">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="55736-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="55736-123">IIS 7.0 がインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="55736-123">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="55736-124">WAS のアクティブ化には IIS 7.0 が必要です。</span><span class="sxs-lookup"><span data-stu-id="55736-124">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="55736-125">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="55736-125">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="55736-126">さらに、WCF 非 HTTP アクティブ化コンポーネントをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="55736-126">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="55736-127">**[スタート]** メニューの **[コントロール パネル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55736-127">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="55736-128">[ **プログラムと機能**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="55736-128">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="55736-129">[ **Windows コンポーネントの有効化または無効化] を** クリックします。</span><span class="sxs-lookup"><span data-stu-id="55736-129">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="55736-130">[ **Microsoft .NET Framework 3.0** ] ノードを展開し、[ **WINDOWS COMMUNICATION FOUNDATION の非 HTTP アクティブ化** ] 機能をオンにします。</span><span class="sxs-lookup"><span data-stu-id="55736-130">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="55736-131">TCP アクティベーションをサポートするよう WAS を構成します。</span><span class="sxs-lookup"><span data-stu-id="55736-131">Configure WAS to support TCP activation.</span></span>

    <span data-ttu-id="55736-132">便宜上次の 2 つの手順が、サンプル ディレクトリにある AddNetTcpSiteBinding.cmd というバッチ ファイルに実装されています。</span><span class="sxs-lookup"><span data-stu-id="55736-132">As a convenience, the following two steps are implemented in a batch file called AddNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="55736-133">net.tcp アクティベーションをサポートするには、既定の Web サイトをあらかじめ net.tcp ポートにバインドしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="55736-133">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="55736-134">これは、インターネット インフォメーション サービス 7.0 (IIS) 管理ツール セットと共にインストールされる Appcmd.exe を使用して行います。</span><span class="sxs-lookup"><span data-stu-id="55736-134">This can be done using Appcmd.exe, which is installed with the Internet Information Services 7.0 (IIS) management toolset.</span></span> <span data-ttu-id="55736-135">管理者レベルのコマンド プロンプトから、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="55736-135">From an administrator-level command prompt, run the following command:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!TIP]
        > <span data-ttu-id="55736-136">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="55736-136">This command is a single line of text.</span></span> <span data-ttu-id="55736-137">このコマンドは、net.tcp サイト バインディングを、TCP ポート 808 で任意のホスト名をリッスンする既定の Web サイトに追加します。</span><span class="sxs-lookup"><span data-stu-id="55736-137">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any hostname.</span></span>

    2. <span data-ttu-id="55736-138">サイト内のすべてのアプリケーションが同じ net.tcp バインディングを共有しますが、net.tcp サポートの有効化はアプリケーションごとに指定できます。</span><span class="sxs-lookup"><span data-stu-id="55736-138">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="55736-139">/servicemodelsamples アプリケーションで net.tcp を有効にするには、管理者レベルのコマンド プロンプトから、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="55736-139">To enable net.tcp for the /servicemodelsamples application, run the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp
        ```

        > [!NOTE]
        > <span data-ttu-id="55736-140">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="55736-140">This command is a single line of text.</span></span> <span data-ttu-id="55736-141">このコマンドにより、との両方を使用して/servicemodelsamples アプリケーションにアクセスできるようになり `http://localhost/servicemodelsamples` `net.tcp://localhost/servicemodelsamples` ます。</span><span class="sxs-lookup"><span data-stu-id="55736-141">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="55736-142">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="55736-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="55736-143">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="55736-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    <span data-ttu-id="55736-144">このサンプル用に追加した net.tcp サイト バインディングを削除します。</span><span class="sxs-lookup"><span data-stu-id="55736-144">Remove the net.tcp site binding you added for this sample.</span></span>

    <span data-ttu-id="55736-145">便宜上次の 2 つの手順が、サンプル ディレクトリにある RemoveNetTcpSiteBinding.cmd というバッチ ファイルに実装されています。</span><span class="sxs-lookup"><span data-stu-id="55736-145">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="55736-146">管理者レベルのコマンド プロンプトから次のコマンドを実行して、有効なプロトコルの一覧から net.tcp を削除します。</span><span class="sxs-lookup"><span data-stu-id="55736-146">Remove net.tcp from the list of enabled protocols by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="55736-147">このコマンドは、全体で 1 行のテキストになるように入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55736-147">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="55736-148">管理者レベルのコマンド プロンプトから次のコマンドを実行して、net.tcp サイト バインディングを削除します。</span><span class="sxs-lookup"><span data-stu-id="55736-148">Remove the net.tcp site binding by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="55736-149">このコマンドは、全体で 1 行のテキストになるように入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55736-149">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="55736-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="55736-150">See also</span></span>

- <span data-ttu-id="55736-151">[AppFabric のホストおよび永続化のサンプル](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="55736-151">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
