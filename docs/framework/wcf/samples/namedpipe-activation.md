---
description: '詳細情報: NamedPipe のアクティブ化'
title: NamedPipe アクティベーション
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: 4955511f24d831f4aa9e3aa67fdb3f6a218d7af0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752209"
---
# <a name="namedpipe-activation"></a><span data-ttu-id="87337-103">NamedPipe アクティベーション</span><span class="sxs-lookup"><span data-stu-id="87337-103">NamedPipe Activation</span></span>

<span data-ttu-id="87337-104">このサンプルでは、名前付きパイプを介して通信するサービスをアクティブ化するために、Windows プロセス アクティブ化サービス (WAS: Windows Process Activation Service) を使用してサービスをホストする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="87337-104">This sample demonstrates hosting a service that uses Windows Process Activation Service (WAS) to activate a service that communicates over names pipes.</span></span> <span data-ttu-id="87337-105">このサンプルは [はじめに](getting-started-sample.md) に基づいており、Windows Vista を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87337-105">This sample is based on the [Getting Started](getting-started-sample.md) and requires Windows Vista to run.</span></span>

> [!NOTE]
> <span data-ttu-id="87337-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87337-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="87337-107">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="87337-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="87337-108">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="87337-108">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="87337-109">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="87337-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="87337-110">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="87337-110">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a><span data-ttu-id="87337-111">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="87337-111">Sample Details</span></span>

<span data-ttu-id="87337-112">このサンプルは、クライアント コンソール プログラム (.exe) と、Windows プロセス アクティブ化サービス (WAS) によってアクティブ化されるワーカー プロセス内でホストされるサービス ライブラリ (.dll) で構成されています。</span><span class="sxs-lookup"><span data-stu-id="87337-112">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by the Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="87337-113">クライアント アクティビティは、コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="87337-113">Client activity is visible in the console window.</span></span>

<span data-ttu-id="87337-114">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="87337-114">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="87337-115">コントラクトは `ICalculator` インターフェイスによって定義されており、算術演算 (Add、Subtract、Multiply、および Divide) を公開しています。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="87337-115">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code.</span></span>

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

<span data-ttu-id="87337-116">クライアントは指定された算術演算を同期要求し、サービスの実装は計算を行って結果を返します。</span><span class="sxs-lookup"><span data-stu-id="87337-116">The client makes synchronous requests to a given math operation and the service implementation calculates and returns the appropriate result.</span></span>

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

<span data-ttu-id="87337-117">このサンプルでは、セキュリティ保護を行わないように変更された `netNamedPipeBinding` バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="87337-117">The sample uses a modified `netNamedPipeBinding` binding with no security.</span></span> <span data-ttu-id="87337-118">バインディングは、クライアントとサービスの構成ファイルに指定されます。</span><span class="sxs-lookup"><span data-stu-id="87337-118">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="87337-119">サービスのバインディングの種類は、エンドポイント要素の `binding` 属性に指定されます。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87337-119">The binding type for the service is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>

<span data-ttu-id="87337-120">セキュリティ保護された名前付きパイプ バインディングを使用する場合は、サーバーのセキュリティ モードを必要なセキュリティ設定に変更し、クライアントで svcutil.exe を再実行して更新されたクライアントの構成ファイルを取得します。</span><span class="sxs-lookup"><span data-stu-id="87337-120">If you want use a secured named pipe binding, change the server's security mode to the desired security setting and run svcutil.exe again on the client to obtain an updated client configuration file.</span></span>

```xml
<system.serviceModel>
        <services>
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">

        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->
        <endpoint address=""
                  binding="netNamedPipeBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexNamedPipeBinding"
                  contract="IMetadataExchange" />
      </service>
        </services>
        <bindings>
            <netNamedPipeBinding>
                <binding name="Binding1" >
                    <security mode = "None">
                    </security>
                </binding >
            </netNamedPipeBinding>
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

<span data-ttu-id="87337-121">クライアントのエンドポイント情報が構成されます。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="87337-121">The client’s endpoint information is configured as shown in the following sample code.</span></span>

```xml
<system.serviceModel>

    <client>
      <endpoint name=""
                          address="net.pipe://localhost/servicemodelsamples/service.svc"
                          binding="netNamedPipeBinding"
                          bindingConfiguration="Binding1"
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>

    <bindings>

      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.
            Each property is configured with the default value. -->

      <netNamedPipeBinding>
        <binding name="Binding1"
                         maxBufferSize="65536"
                         maxConnections="10">
          <security mode = "None">
          </security>
        </binding >

      </netNamedPipeBinding>
    </bindings>

  </system.serviceModel>
```

<span data-ttu-id="87337-122">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="87337-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="87337-123">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="87337-123">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="87337-124">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="87337-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="87337-125">IIS 7.0 がインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="87337-125">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="87337-126">WAS のアクティブ化には IIS 7.0 が必要です。</span><span class="sxs-lookup"><span data-stu-id="87337-126">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="87337-127">[Windows Communication Foundation のサンプルに対して1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="87337-127">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="87337-128">さらに、WCF 非 HTTP アクティブ化コンポーネントをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="87337-128">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="87337-129">**[スタート]** メニューの **[コントロール パネル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="87337-129">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="87337-130">[ **プログラムと機能**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="87337-130">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="87337-131">[ **Windows コンポーネントの有効化または無効化] を** クリックします。</span><span class="sxs-lookup"><span data-stu-id="87337-131">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="87337-132">[ **Microsoft .NET Framework 3.0** ] ノードを展開し、[ **WINDOWS COMMUNICATION FOUNDATION の非 HTTP アクティブ化** ] 機能をオンにします。</span><span class="sxs-lookup"><span data-stu-id="87337-132">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="87337-133">名前付きパイプのアクティブ化をサポートするように Windows プロセス アクティブ化サービス (WAS) を構成します。</span><span class="sxs-lookup"><span data-stu-id="87337-133">Configure the Windows Process Activation Service (WAS) to support named pipe activation.</span></span>

    <span data-ttu-id="87337-134">便宜上、次の 2 つの手順が、サンプル ディレクトリにある AddNetPipeSiteBinding.cmd というバッチ ファイルに実装されています。</span><span class="sxs-lookup"><span data-stu-id="87337-134">As a convenience, the following two steps are implemented in a batch file called AddNetPipeSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="87337-135">net.pipe のアクティブ化をサポートするには、既定の Web サイトをあらかじめ net.pipe プロトコルにバインドしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="87337-135">To support net.pipe activation, the default Web site must first be bound to the net.pipe protocol.</span></span> <span data-ttu-id="87337-136">これは、IIS7.0 管理ツール セットと共にインストールされる appcmd.exe を使用して行います。</span><span class="sxs-lookup"><span data-stu-id="87337-136">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="87337-137">権限のレベルが高い (管理者の) コマンド プロンプトで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="87337-137">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="87337-138">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="87337-138">This command is a single line of text.</span></span>

        <span data-ttu-id="87337-139">このコマンドによって、既定の Web サイトに net.pipe サイト バインディングを追加します。</span><span class="sxs-lookup"><span data-stu-id="87337-139">This command adds a net.pipe site binding to the default Web site.</span></span>

    2. <span data-ttu-id="87337-140">サイト内のすべてのアプリケーションが同じ net.pipe バインディングを共有しますが、net.pipe サポートの有効化はアプリケーションごとに指定できます。</span><span class="sxs-lookup"><span data-stu-id="87337-140">Although all applications within a site share a common net.pipe binding, each application can enable net.pipe support individually.</span></span> <span data-ttu-id="87337-141">/servicemodelsamples アプリケーションで net.pipe を有効にするには、権限のレベルが高いコマンド プロンプトから、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="87337-141">To enable net.pipe for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > <span data-ttu-id="87337-142">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="87337-142">This command is a single line of text.</span></span>

        <span data-ttu-id="87337-143">このコマンドにより、との両方を使用して/servicemodelsamples アプリケーションにアクセスできるようになり `http://localhost/servicemodelsamples` `net.tcp://localhost/servicemodelsamples` ます。</span><span class="sxs-lookup"><span data-stu-id="87337-143">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="87337-144">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="87337-144">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="87337-145">このサンプル用に追加した net.pipe サイト バインディングを削除します。</span><span class="sxs-lookup"><span data-stu-id="87337-145">Remove the net.pipe site binding you added for this sample.</span></span>

    <span data-ttu-id="87337-146">便宜上、次の 2 つの手順が、サンプル ディレクトリにある RemoveNetPipeSiteBinding.cmd というバッチ ファイルに実装されています。</span><span class="sxs-lookup"><span data-stu-id="87337-146">As a convenience, the following two steps are implemented in a batch file called RemoveNetPipeSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="87337-147">権限のレベルが高いコマンド プロンプトから次のコマンドを実行して、有効なプロトコルの一覧から net.tcp を削除します。</span><span class="sxs-lookup"><span data-stu-id="87337-147">Remove net.tcp from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="87337-148">このコマンドは、全体で 1 行のテキストになるように入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87337-148">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="87337-149">権限のレベルが高いコマンド プロンプトから次のコマンドを実行して、net.tcp サイト バインディングを削除します。</span><span class="sxs-lookup"><span data-stu-id="87337-149">Remove the net.tcp site binding by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="87337-150">このコマンドは、全体で 1 行のテキストになるように入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87337-150">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="87337-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="87337-151">See also</span></span>

- <span data-ttu-id="87337-152">[AppFabric のホストおよび永続化のサンプル](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="87337-152">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
