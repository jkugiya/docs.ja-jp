---
description: 詳細については、「Windows Communication Foundation で使用するための Windows プロセスアクティブ化サービスの構成」を参照してください。
title: Windows Communication Foundation で使用するための Windows プロセス アクティブ化サービスを設定する
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: b98cc776b3a0bd860b4837ba70d58d10a83827dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780623"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="cc5d6-103">Windows Communication Foundation で使用するための Windows プロセス アクティブ化サービスを設定する</span><span class="sxs-lookup"><span data-stu-id="cc5d6-103">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>

<span data-ttu-id="cc5d6-104">このトピックでは、windows Vista で Windows プロセスアクティブ化サービス (WAS) をセットアップして、HTTP ネットワークプロトコルでは通信しない Windows Communication Foundation (WCF) サービスをホストする手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-104">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="cc5d6-105">以降の各セクションで、この構成に関する手順について概説します。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-105">The following sections outline the steps for this configuration:</span></span>  
  
- <span data-ttu-id="cc5d6-106">必要な WCF アクティブ化コンポーネントをインストール (または、のインストールを確認) します。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-106">Install (or confirm the installation of) the WCF activation components required.</span></span>  
  
- <span data-ttu-id="cc5d6-107">使用するネットワーク プロトコル バインドを含む WAS サイトを作成するか、新しいプロトコル バインドを既存のサイトに追加します。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-107">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
- <span data-ttu-id="cc5d6-108">サービスをホストするアプリケーションを作成し、必要なネットワーク プロトコルを使用するようにそのアプリケーションを設定します。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-108">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
- <span data-ttu-id="cc5d6-109">非 HTTP エンドポイントを公開する WCF サービスを構築します。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-109">Build a WCF service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="cc5d6-110">非 HTTP バインドを使用したサイトの構成</span><span class="sxs-lookup"><span data-stu-id="cc5d6-110">Configuring a Site with Non-HTTP bindings</span></span>  

 <span data-ttu-id="cc5d6-111">WAS で非 HTTP バインドを使用するには、サイト バインドを WAS 構成に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-111">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="cc5d6-112">WAS の構成ストアは、%windir%\system32\inetsrv\config ディレクトリにある applicationHost.config ファイルです。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-112">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="cc5d6-113">この構成ストアは、WAS と IIS 7.0 の両方で共有されます。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-113">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="cc5d6-114">applicationHost.config は、任意の標準テキスト エディター (メモ帳など) で開くことが可能な XML テキスト ファイルです。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-114">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="cc5d6-115">ただし、IIS 7.0 のコマンドライン構成ツール (appcmd.exe) を使用して、HTTP 以外のサイトバインドを追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-115">However, the IIS 7.0 command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="cc5d6-116">次のコマンドは、appcmd.exe を使用して、既定の Web サイトに net.tcp サイト バインドを追加します (このコマンドは 1 行で入力します)。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-116">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="cc5d6-117">このコマンドは、次に示す行を applicationHost.config ファイルに追加することによって、既定の Web サイトに新しい net.tcp バインドを追加します。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-117">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="cc5d6-118">非 HTTP プロトコルを使用するためのアプリケーションの設定</span><span class="sxs-lookup"><span data-stu-id="cc5d6-118">Enabling an Application to Use Non-HTTP Protocols</span></span>  

 <span data-ttu-id="cc5d6-119">個々のネットワークプロトコルをアプリケーションレベルで有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-119">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="cc5d6-120">次のコマンドは、`Default Web Site` で動作するアプリケーションに対して、HTTP プロトコルと net.tcp プロトコルの両方を有効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-120">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="cc5d6-121">有効なプロトコルの一覧は、 \<applicationDefaults> ApplicationHost.config に格納されているサイトの XML 構成の要素で設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-121">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="cc5d6-122">次の applicationHost.config からの XML コードは、HTTP プロトコルと非 HTTP プロトコルの両方にバインドされたサイトを示しています。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-122">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="cc5d6-123">非 HTTP プロトコルのサポートに必要な追加の構成は、コメントで付記されています。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-123">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
      <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
      </application>  
      <bindings>  
            <!-- The following two lines are added by the command. -->
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults
      applicationPool="DefaultAppPool"
      <!-- The following line is inserted by the command. -->
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 <span data-ttu-id="cc5d6-124">非 HTTP アクティブ化の WAS を使用するサービスをアクティブ化しようとしたときに、WAS をインストールおよび構成していない場合、次のエラーが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-124">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="cc5d6-125">このエラーが表示された場合は、非 HTTP アクティブ化の WAS が適切にインストールおよび構成されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-125">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> <span data-ttu-id="cc5d6-126">詳細については、「 [方法: WCF アクティブ化コンポーネントをインストールおよび構成](how-to-install-and-configure-wcf-activation-components.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-126">For more information, see [How to: Install and Configure WCF Activation Components](how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="cc5d6-127">非 HTTP のアクティブ化で WAS を使用する WCF サービスの構築</span><span class="sxs-lookup"><span data-stu-id="cc5d6-127">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  

 <span data-ttu-id="cc5d6-128">WAS をインストールして構成する手順 (「 [方法: WCF アクティブ化コンポーネントをインストールおよび構成](how-to-install-and-configure-wcf-activation-components.md)する」を参照してください) を実行すると、アクティブ化のために was を使用するようにサービスを構成することは、IIS でホストされるサービスの構成に似ています。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-128">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="cc5d6-129">WAS によってアクティブ化される WCF サービスを構築する方法の詳細については、「 [How to: Host a WCF service IN was](how-to-host-a-wcf-service-in-was.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc5d6-129">For detailed instructions about building a WAS-activated WCF service, see [How to: Host a WCF Service in WAS](how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc5d6-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc5d6-130">See also</span></span>

- [<span data-ttu-id="cc5d6-131">Windows プロセス アクティブ化サービスでのホスティング</span><span class="sxs-lookup"><span data-stu-id="cc5d6-131">Hosting in Windows Process Activation Service</span></span>](hosting-in-windows-process-activation-service.md)
- <span data-ttu-id="cc5d6-132">[AppFabric のホスティング機能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="cc5d6-132">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
