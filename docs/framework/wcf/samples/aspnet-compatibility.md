---
description: 詳細については、ASP.NET の互換性に関するページをご覧ください。
title: ASP.NET 互換性
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: a5685481a16d87715d4fc9096055af5be479f459
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778855"
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="a1d07-103">ASP.NET 互換性</span><span class="sxs-lookup"><span data-stu-id="a1d07-103">ASP.NET Compatibility</span></span>

<span data-ttu-id="a1d07-104">このサンプルでは、Windows Communication Foundation (WCF) で ASP.NET 互換モードを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a1d07-104">This sample demonstrates how to enable ASP.NET Compatibility mode in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="a1d07-105">ASP.NET 互換モードで実行されているサービスは、ASP.NET アプリケーションパイプラインに完全に参加し、ファイル/URL 認証、セッション状態、クラスなどの ASP.NET 機能を利用でき <xref:System.Web.HttpContext> ます。</span><span class="sxs-lookup"><span data-stu-id="a1d07-105">Services running in ASP.NET Compatibility mode participate fully in the ASP.NET application pipeline and can make use of ASP.NET features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="a1d07-106"><xref:System.Web.HttpContext>クラスを使用すると、cookie、セッション、およびその他の ASP.NET 機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a1d07-106">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other ASP.NET features.</span></span> <span data-ttu-id="a1d07-107">このモードでは、バインディングは HTTP トランスポートを使用し、サービス自体は IIS でホストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1d07-107">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>

<span data-ttu-id="a1d07-108">このサンプルでは、クライアントはコンソール アプリケーション (.exe) で、サービスはインターネット インフォメーション サービス (IIS) によってホストされています。</span><span class="sxs-lookup"><span data-stu-id="a1d07-108">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="a1d07-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1d07-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="a1d07-110">このサンプルを実行するには、.NET Framework 4 つのアプリケーションプールが必要です。</span><span class="sxs-lookup"><span data-stu-id="a1d07-110">This sample requires a .NET Framework 4 application pool in order to run.</span></span> <span data-ttu-id="a1d07-111">新しいアプリケーション プールの作成または既定のアプリケーション プールの変更を行うには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a1d07-111">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>

1. <span data-ttu-id="a1d07-112">**[コントロール パネル]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="a1d07-112">Open **Control Panel**.</span></span>  <span data-ttu-id="a1d07-113">[**システムとセキュリティ**] 見出しの下にある [**管理ツール**] アプレットを開きます。</span><span class="sxs-lookup"><span data-stu-id="a1d07-113">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="a1d07-114">**インターネットインフォメーションサービス (IIS) マネージャー** アプレットを開きます。</span><span class="sxs-lookup"><span data-stu-id="a1d07-114">Open the **Internet Information Services (IIS) Manager** applet.</span></span>

2. <span data-ttu-id="a1d07-115">[ **接続** ] ウィンドウで treeview を展開します。</span><span class="sxs-lookup"><span data-stu-id="a1d07-115">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="a1d07-116">[ **アプリケーションプール** ] ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="a1d07-116">Select the **Application Pools** node.</span></span>

3. <span data-ttu-id="a1d07-117">既定のアプリケーションプールで .NET Framework 4 を使用するように設定するには (既存のサイトで非互換性の問題が発生する可能性があります)、 **DefaultAppPool** リスト項目を右クリックし、[ **基本設定...**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a1d07-117">To set the default application pool to use .NET Framework 4 (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="a1d07-118">**.Net Framework バージョン** のプルダウンを **.net framework v v4.0.30128** (またはそれ以降) に設定します。</span><span class="sxs-lookup"><span data-stu-id="a1d07-118">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>

4. <span data-ttu-id="a1d07-119">(他のアプリケーションとの互換性を維持するために) .NET Framework 4 を使用する新しいアプリケーションプールを作成するには、[ **アプリケーション** プール] ノードを右クリックし、[ **アプリケーションプールの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a1d07-119">To create a new application pool that uses .NET Framework 4 (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="a1d07-120">新しいアプリケーションプールにという名前を設定し、[ **.Net Framework バージョン** ] プルダウンを [ **.net framework v v4.0.30128** (またはそれ以降)] に設定します。</span><span class="sxs-lookup"><span data-stu-id="a1d07-120">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="a1d07-121">次のセットアップ手順を実行したら、 **ServiceModelSamples** アプリケーションを右クリックし、[ **アプリケーションの管理**]、[ **詳細設定.**..] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="a1d07-121">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="a1d07-122">**アプリケーションプール** を新しいアプリケーションプールに設定します。</span><span class="sxs-lookup"><span data-stu-id="a1d07-122">Set the **Application Pool** to the new application pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a1d07-123">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a1d07-123">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a1d07-124">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a1d07-124">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a1d07-125">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="a1d07-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a1d07-126">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a1d07-126">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`

<span data-ttu-id="a1d07-127">このサンプルは、電卓サービスを実装する [はじめに](getting-started-sample.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="a1d07-127">This sample is based on the [Getting Started](getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="a1d07-128">`ICalculator` コントラクトは、一連の算術演算を実行して実行結果を保持できるように `ICalculatorSession` コントラクトに変更されました。</span><span class="sxs-lookup"><span data-stu-id="a1d07-128">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculatorSession
{
    [OperationContract]
    void Clear();
    [OperationContract]
    void AddTo(double n);
    [OperationContract]
    void SubtractFrom(double n);
    [OperationContract]
    void MultiplyBy(double n);
    [OperationContract]
    void DivideBy(double n);
    [OperationContract]
    double Result();
}
```

<span data-ttu-id="a1d07-129">サービスはこの機能を使用して、複数のサービス操作が呼び出されて計算を実行する際に、各クライアントの状態を保持します。</span><span class="sxs-lookup"><span data-stu-id="a1d07-129">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="a1d07-130">クライアントは `Result` を呼び出して現在の結果を取得したり、`Clear` を呼び出してその結果をクリアし、0 にすることができます。</span><span class="sxs-lookup"><span data-stu-id="a1d07-130">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>

<span data-ttu-id="a1d07-131">サービスは、ASP.NET セッションを使用して、各クライアントセッションの結果を格納します。</span><span class="sxs-lookup"><span data-stu-id="a1d07-131">The service uses the ASP.NET session to store the result for each client session.</span></span> <span data-ttu-id="a1d07-132">これにより、サービスは、サービスへの複数の呼び出しによる各クライアントの実行結果を保持できます。</span><span class="sxs-lookup"><span data-stu-id="a1d07-132">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>

> [!NOTE]
> <span data-ttu-id="a1d07-133">ASP.NET セッション状態と WCF セッションは、非常に異なるものです。</span><span class="sxs-lookup"><span data-stu-id="a1d07-133">ASP.NET session state and WCF sessions are very different things.</span></span> <span data-ttu-id="a1d07-134">WCF セッションの詳細については、「 [セッション](session.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1d07-134">See [Session](session.md) for details on WCF sessions.</span></span>

<span data-ttu-id="a1d07-135">このサービスは、ASP.NET セッション状態に対してより深い依存関係を持ち、ASP.NET 互換モードが正常に機能することを必要とします。</span><span class="sxs-lookup"><span data-stu-id="a1d07-135">The service has an intimate dependency on ASP.NET session state and requires ASP.NET compatibility mode to function correctly.</span></span> <span data-ttu-id="a1d07-136">これらの要件は、`AspNetCompatibilityRequirements` 属性を適用することにより宣言によって表されます。</span><span class="sxs-lookup"><span data-stu-id="a1d07-136">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>

```csharp
[AspNetCompatibilityRequirements(RequirementsMode =
                       AspNetCompatibilityRequirementsMode.Required)]
public class CalculatorService : ICalculatorSession
{
    double Result
    {  // store result in AspNet Session
       get {
          if (HttpContext.Current.Session["Result"] != null)
             return (double)HttpContext.Current.Session["Result"];
          return 0.0D;
       }
       set
       {
          HttpContext.Current.Session["Result"] = value;
       }
    }
    public void Clear()
    {
        Result = 0.0D;
    }
    public void AddTo(double n)
    {
        Result += n;
    }
    public void SubtractFrom(double n)
    {
        Result -= n;
    }
    public void MultiplyBy(double n)
    {
        Result *= n;
    }
    public void DivideBy(double n)
    {
        Result /= n;
    }
    public double Result()
    {
        return Result;
    }
}
```

<span data-ttu-id="a1d07-137">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a1d07-137">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a1d07-138">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a1d07-138">Press ENTER in the client window to shut down the client.</span></span>

```console
0, + 100, - 50, * 17.65, / 2 = 441.25
Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a1d07-139">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="a1d07-139">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="a1d07-140">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a1d07-140">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="a1d07-141">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a1d07-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="a1d07-142">ソリューションをビルドした後、Setup.bat を実行して IIS 7.0 で ServiceModelSamples アプリケーションを設定します。</span><span class="sxs-lookup"><span data-stu-id="a1d07-142">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="a1d07-143">これで、ServiceModelSamples ディレクトリが IIS 7.0 アプリケーションとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="a1d07-143">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="a1d07-144">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a1d07-144">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a1d07-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1d07-145">See also</span></span>

- <span data-ttu-id="a1d07-146">[AppFabric のホストおよび永続化のサンプル](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a1d07-146">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
