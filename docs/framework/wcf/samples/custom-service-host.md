---
description: '詳細情報: カスタムサービスホスト'
title: カスタム サービス ホスト
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: a18c3ec10eef5fc2c436a2fc2665ea73ed963384
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752445"
---
# <a name="custom-service-host"></a><span data-ttu-id="00e94-103">カスタム サービス ホスト</span><span class="sxs-lookup"><span data-stu-id="00e94-103">Custom Service Host</span></span>

<span data-ttu-id="00e94-104">このサンプルでは、<xref:System.ServiceModel.ServiceHost> クラスから派生したカスタムのサービス ホストを使用して、サービスの実行時動作を変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="00e94-104">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="00e94-105">この方法は、多数のサービスを共通方式で構成するという方法の代わりに使用でき、再利用可能です。</span><span class="sxs-lookup"><span data-stu-id="00e94-105">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="00e94-106">このサンプルでは、<xref:System.ServiceModel.Activation.ServiceHostFactory> クラスを使用して、カスタムの ServiceHost を、インターネット インフォメーション サービス (IIS) または Windows プロセス アクティブ化サービス (WAS) でホストされる環境で使用する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="00e94-106">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="00e94-107">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="00e94-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="00e94-108">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="00e94-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="00e94-109">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="00e94-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="00e94-110">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="00e94-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="00e94-111">シナリオについて</span><span class="sxs-lookup"><span data-stu-id="00e94-111">About the scenario</span></span>

 <span data-ttu-id="00e94-112">機密性の高いサービスメタデータが誤って公開されるのを防ぐために、Windows Communication Foundation (WCF) サービスの既定の構成では、メタデータの公開が無効になっています。</span><span class="sxs-lookup"><span data-stu-id="00e94-112">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="00e94-113">この動作は既定ではセキュリティで保護されていますが、サービスのメタデータ公開動作が構成で明示的に有効になっていない限り、サービスの呼び出しに必要なクライアントコードを生成するためにメタデータインポートツール (Svcutil.exe など) を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="00e94-113">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service's metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="00e94-114">多数のサービスのメタデータ公開を有効にすると、同一の構成要素が各サービスに追加されます。この結果、本質的に同じ構成情報が大量に発生することになります。</span><span class="sxs-lookup"><span data-stu-id="00e94-114">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="00e94-115">各サービスを個別に構成する代わりに、メタデータ公開を有効化する命令型コードを一度だけプログラミングして、そのコードを複数のサービスで再利用するという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="00e94-115">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="00e94-116">この方法を使用するには、<xref:System.ServiceModel.ServiceHost> から派生する新しいクラスを作成し、`ApplyConfiguration`() メソッドをオーバーライドして命令型コードでメタデータ公開動作を追加します。</span><span class="sxs-lookup"><span data-stu-id="00e94-116">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="00e94-117">このサンプルでは、わかりやすくするために、セキュリティで保護されていないメタデータ公開エンドポイントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="00e94-117">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="00e94-118">このようなエンドポイントは、匿名の認証されていないコンシューマーが使用できる可能性があり、サービスのメタデータの公開が適切であることを保証するために、このようなエンドポイントをデプロイする前に注意する必要が</span><span class="sxs-lookup"><span data-stu-id="00e94-118">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service's metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="00e94-119">カスタム ServiceHost の実装</span><span class="sxs-lookup"><span data-stu-id="00e94-119">Implementing a custom ServiceHost</span></span>

 <span data-ttu-id="00e94-120"><xref:System.ServiceModel.ServiceHost> クラスは、便利な仮想メソッドを多数公開しています。継承側でこの仮想メソッドをオーバーライドして、サービスの実行時動作を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="00e94-120">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="00e94-121">たとえば、`ApplyConfiguration`() メソッドはサービスの構成情報を構成ストアから読み取り、それに応じてホストの <xref:System.ServiceModel.Description.ServiceDescription> を変更します。</span><span class="sxs-lookup"><span data-stu-id="00e94-121">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="00e94-122">既定の実装では、アプリケーションの構成ファイルから構成を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="00e94-122">The default implementation reads configuration from the application's configuration file.</span></span> <span data-ttu-id="00e94-123">カスタム実装では、`ApplyConfiguration`() をオーバーライドすれば、命令型コードを使用して <xref:System.ServiceModel.Description.ServiceDescription> にさらに変更を加えることや、既定の構成ストア全体を置き換えることも可能です (</span><span class="sxs-lookup"><span data-stu-id="00e94-123">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="00e94-124">たとえば、アプリケーションの構成ファイルではなく、データベースからサービスのエンドポイント構成を読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="00e94-124">For example, to read a service's endpoint configuration from a database instead of the application's configuration file.</span></span>  
  
 <span data-ttu-id="00e94-125">このサンプルでは、サービスの構成ファイルにこの動作が明示的に追加されていない場合でも、ServiceMetadataBehavior (メタデータの公開を有効にする) を追加するカスタム ServiceHost を作成します。</span><span class="sxs-lookup"><span data-stu-id="00e94-125">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior (which enables metadata publishing) even if this behavior is not explicitly added in the service's configuration file.</span></span> <span data-ttu-id="00e94-126">これを実現するには、から継承して () をオーバーライドする新しいクラスを作成し <xref:System.ServiceModel.ServiceHost> `ApplyConfiguration` ます。</span><span class="sxs-lookup"><span data-stu-id="00e94-126">To accomplish this, create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
```csharp
class SelfDescribingServiceHost : ServiceHost  
{  
    public SelfDescribingServiceHost(Type serviceType, params Uri[] baseAddresses)  
        : base(serviceType, baseAddresses) { }  
  
    //Overriding ApplyConfiguration() allows us to
    //alter the ServiceDescription prior to opening  
    //the service host.
    protected override void ApplyConfiguration()  
    {  
        //First, we call base.ApplyConfiguration()  
        //to read any configuration that was provided for  
        //the service we're hosting. After this call,  
        //this.Description describes the service  
        //as it was configured.  
        base.ApplyConfiguration();
  
        //(rest of implementation elided for clarity)  
    }  
}  
```  
  
 <span data-ttu-id="00e94-127">アプリケーションの構成ファイルで提供されている構成を無視したくないので、() の最初のオーバーライド `ApplyConfiguration` は基本実装を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="00e94-127">Because we do not want to ignore any configuration that has been provided in the application's configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="00e94-128">このメソッドが完了した後で、次の命令型コードを使用して、サービス記述に <xref:System.ServiceModel.Description.ServiceMetadataBehavior> を追加します。</span><span class="sxs-lookup"><span data-stu-id="00e94-128">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
```csharp
ServiceMetadataBehavior mexBehavior = this.Description.Behaviors.Find<ServiceMetadataBehavior>();  
if (mexBehavior == null)  
{  
    mexBehavior = new ServiceMetadataBehavior();  
    this.Description.Behaviors.Add(mexBehavior);  
}  
else  
{  
    //Metadata behavior has already been configured,
    //so we do not have any work to do.  
    return;  
}  
```  
  
 <span data-ttu-id="00e94-129">`ApplyConfiguration`() のオーバーライドでの最後の処理は、既定のメタデータ エンドポイントの追加です。</span><span class="sxs-lookup"><span data-stu-id="00e94-129">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="00e94-130">慣例により、サービスホストの BaseAddresses コレクション内の各 URI に対して1つのメタデータエンドポイントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="00e94-130">By convention, one metadata endpoint is created for each URI in the service host's BaseAddresses collection.</span></span>  
  
```csharp
//Add a metadata endpoint at each base address  
//using the "/mex" addressing convention  
foreach (Uri baseAddress in this.BaseAddresses)  
{  
    if (baseAddress.Scheme == Uri.UriSchemeHttp)  
    {  
        mexBehavior.HttpGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeHttps)  
    {  
        mexBehavior.HttpsGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpsBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetPipe)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexNamedPipeBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetTcp)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexTcpBinding(),  
                                "mex");  
    }  
}  
```  
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="00e94-131">自己ホストでのカスタム ServiceHost の使用</span><span class="sxs-lookup"><span data-stu-id="00e94-131">Using a custom ServiceHost in self-host</span></span>  

 <span data-ttu-id="00e94-132">カスタム ServiceHost の実装が完成したので、これを使用して任意のサービスにメタデータ公開動作を追加できるようになりました。追加するには、`SelfDescribingServiceHost` のインスタンス内でサービスをホストします。</span><span class="sxs-lookup"><span data-stu-id="00e94-132">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="00e94-133">カスタム ServiceHost を自己ホストのシナリオで使用する方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="00e94-133">The following code shows how to use it in the self-host scenario.</span></span>  
  
```csharp
SelfDescribingServiceHost host =
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="00e94-134">既定のクラスを使用してサービスをホストしていたかのように、カスタムホストは引き続きアプリケーションの構成ファイルからサービスのエンドポイント構成を読み取り <xref:System.ServiceModel.ServiceHost> ます。</span><span class="sxs-lookup"><span data-stu-id="00e94-134">Our custom host still reads the service's endpoint configuration from the application's configuration file, as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="00e94-135">ただし、カスタム ホストの内部でメタデータ公開を有効にするというロジックを追加したので、構成の中でメタデータ公開動作を明示的に有効化することは不要になりました。</span><span class="sxs-lookup"><span data-stu-id="00e94-135">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="00e94-136">この方法のメリットがはっきりと現れるのは、開発するアプリケーションに複数のサービスがあり、同じ構成要素を繰り返し記述することなく各サービスでメタデータ公開を有効化できるようにする場合です。</span><span class="sxs-lookup"><span data-stu-id="00e94-136">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="00e94-137">IIS または WAS でのカスタム ServiceHost の使用</span><span class="sxs-lookup"><span data-stu-id="00e94-137">Using a custom ServiceHost in IIS or WAS</span></span>  

 <span data-ttu-id="00e94-138">カスタム サービス ホストを自己ホストのシナリオで使用することは簡単です。サービス ホストのインスタンスを作成して開くことは、アプリケーションのコードで行うからです。</span><span class="sxs-lookup"><span data-stu-id="00e94-138">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="00e94-139">ただし、IIS または WAS のホスト環境では、WCF インフラストラクチャは、受信メッセージに応答してサービスのホストを動的にインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="00e94-139">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service's host in response to incoming messages.</span></span> <span data-ttu-id="00e94-140">このホスト環境でもカスタム サービス ホストを使用できますが、ServiceHostFactory の形式でコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00e94-140">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="00e94-141">次に示すコードは、カスタム <xref:System.ServiceModel.Activation.ServiceHostFactory> のインスタンスを返す、`SelfDescribingServiceHost` の派生クラスの例です。</span><span class="sxs-lookup"><span data-stu-id="00e94-141">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
```csharp
public class SelfDescribingServiceHostFactory : ServiceHostFactory  
{  
    protected override ServiceHost CreateServiceHost(Type serviceType,
     Uri[] baseAddresses)  
    {  
        //All the custom factory does is return a new instance  
        //of our custom host class. The bulk of the custom logic should  
        //live in the custom host (as opposed to the factory)
        //for maximum  
        //reuse value outside of the IIS/WAS hosting environment.  
        return new SelfDescribingServiceHost(serviceType,
                                             baseAddresses);  
    }  
}  
```  
  
 <span data-ttu-id="00e94-142">ご覧のように、カスタム ServiceHostFactory の実装は簡単です。</span><span class="sxs-lookup"><span data-stu-id="00e94-142">As you can see, implementing a custom ServiceHostFactory is straightforward.</span></span> <span data-ttu-id="00e94-143">すべてのカスタム ロジックは ServiceHost 実装内部にあり、このファクトリによって派生クラスのインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="00e94-143">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="00e94-144">サービス実装でカスタムファクトリを使用するには、サービスの .svc ファイルに追加のメタデータを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00e94-144">To use a custom factory with a service implementation, we must add some additional metadata to the service's .svc file.</span></span>  
  
```aspx-csharp
<% @ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 <span data-ttu-id="00e94-145">ここでは、 `Factory` ディレクティブに追加の属性を追加 `@ServiceHost` し、属性の値としてカスタムファクトリの CLR 型名を渡しました。</span><span class="sxs-lookup"><span data-stu-id="00e94-145">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute's value.</span></span> <span data-ttu-id="00e94-146">IIS または WAS がこのサービスのメッセージを受信すると、WCF ホスティングインフラストラクチャは、まず ServiceHostFactory のインスタンスを作成してから、を呼び出してサービスホスト自体をインスタンス化し `ServiceHostFactory.CreateServiceHost()` ます。</span><span class="sxs-lookup"><span data-stu-id="00e94-146">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiates the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="00e94-147">サンプルの実行</span><span class="sxs-lookup"><span data-stu-id="00e94-147">Running the sample</span></span>  

 <span data-ttu-id="00e94-148">このサンプルでは、完全に機能するクライアントとサービスの実装を提供していますが、サンプルのポイントは、カスタムホストを使用してサービスの実行時の動作を変更する方法を示しています。次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="00e94-148">Although this sample does provide a fully functional client and service implementation, the point of the sample is to illustrate how to alter a service's run-time behavior by means of a custom host., do the following steps:</span></span>  
  
### <a name="observe-the-effect-of-the-custom-host"></a><span data-ttu-id="00e94-149">カスタムホストの効果を確認する</span><span class="sxs-lookup"><span data-stu-id="00e94-149">Observe the effect of the custom host</span></span>
  
1. <span data-ttu-id="00e94-150">サービスの Web.config ファイルを開き、サービスのメタデータを明示的に有効にする構成がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="00e94-150">Open the service's Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2. <span data-ttu-id="00e94-151">サービスの .svc ファイルを開き、 @ServiceHost ディレクティブにカスタム ServiceHostFactory の名前を指定するファクトリ属性が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="00e94-151">Open the service's .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
### <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="00e94-152">サンプルをセットアップ、ビルド、および実行する</span><span class="sxs-lookup"><span data-stu-id="00e94-152">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="00e94-153">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="00e94-153">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="00e94-154">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="00e94-154">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="00e94-155">ソリューションをビルドした後、Setup.bat を実行して IIS 7.0 で ServiceModelSamples アプリケーションを設定します。</span><span class="sxs-lookup"><span data-stu-id="00e94-155">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="00e94-156">これで、ServiceModelSamples ディレクトリが IIS 7.0 アプリケーションとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="00e94-156">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="00e94-157">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="00e94-157">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

5. <span data-ttu-id="00e94-158">IIS 7.0 アプリケーションを削除するには、 *Cleanup.bat* を実行します。</span><span class="sxs-lookup"><span data-stu-id="00e94-158">To remove the IIS 7.0 application, run *Cleanup.bat*.</span></span>

## <a name="see-also"></a><span data-ttu-id="00e94-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="00e94-159">See also</span></span>

- [<span data-ttu-id="00e94-160">方法: IIS で WCF サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="00e94-160">How to: Host a WCF Service in IIS</span></span>](../feature-details/how-to-host-a-wcf-service-in-iis.md)
