---
description: UDP のアクティブ化に関する詳細情報
title: UDP アクティベーション
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 8ee5e6363265ddc74d27884ef40354108da17581
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798226"
---
# <a name="udp-activation"></a><span data-ttu-id="ccfc3-103">UDP アクティベーション</span><span class="sxs-lookup"><span data-stu-id="ccfc3-103">UDP Activation</span></span>

<span data-ttu-id="ccfc3-104">このサンプルは、 [Transport: UDP](transport-udp.md) サンプルを基にしています。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-104">This sample is based on the [Transport: UDP](transport-udp.md) sample.</span></span> <span data-ttu-id="ccfc3-105">[Transport: UDP](transport-udp.md)サンプルを拡張して、Windows プロセスアクティブ化サービス (WAS) を使用したプロセスのアクティブ化をサポートします。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-105">It extends the [Transport: UDP](transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="ccfc3-106">サンプルは、次の 3 つの主要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-106">The sample consists of three major pieces:</span></span>  
  
- <span data-ttu-id="ccfc3-107">UDP プロトコル アクティベータ。アクティベーション対象のアプリケーションの代わりに UDP メッセージを受信するスタンドアロンのプロセスです。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-107">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
- <span data-ttu-id="ccfc3-108">UDP カスタム トランスポートを使用してメッセージを送信するクライアント。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-108">A client that uses the UDP custom transport to send messages.</span></span>  
  
- <span data-ttu-id="ccfc3-109">UDP カスタム トランスポート経由でメッセージを受信するサービス。WAS によってアクティブ化されるワーカー プロセス内でホストされています。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-109">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="ccfc3-110">UDP プロトコル アクティベータ</span><span class="sxs-lookup"><span data-stu-id="ccfc3-110">UDP Protocol Activator</span></span>  

 <span data-ttu-id="ccfc3-111">UDP プロトコルアクティベーターは、WCF クライアントと WCF サービスの間のブリッジです。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-111">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="ccfc3-112">トランスポート層で UDP プロトコルを介するデータ通信を実現します。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-112">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="ccfc3-113">主な機能は、次の 2 つです。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-113">It has two major functions:</span></span>  
  
- <span data-ttu-id="ccfc3-114">WAS リスナ アダプタ (LA)。WAS と連携し、受信メッセージに応答してプロセスをアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-114">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
- <span data-ttu-id="ccfc3-115">UDP プロトコル リスナ。アクティベーション対象のアプリケーションの代わりに UDP メッセージを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-115">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="ccfc3-116">このアクティベータは、サーバー コンピュータ上でスタンドアロン プログラムとして実行される必要があります。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-116">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="ccfc3-117">通常、WAS リスナ アダプタ (NetTcpActivator や NetPipeActivator など) は、長時間にわたって実行される Windows サービスに実装されます。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-117">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="ccfc3-118">ただしこのサンプルでは、単純化してわかりやすくするために、このプロトコル アクティベータをスタンドアロン アプリケーションとして実装しています。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-118">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="ccfc3-119">WAS リスナ アダプタ</span><span class="sxs-lookup"><span data-stu-id="ccfc3-119">WAS Listener Adapter</span></span>  

 <span data-ttu-id="ccfc3-120">UDP の WAS リスナ アダプタは `UdpListenerAdapter` クラスに実装されています。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-120">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="ccfc3-121">これは WAS とやり取りするモジュールで、UDP プロトコル用アプリケーションのアクティベーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-121">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="ccfc3-122">これは、次の Webhost API を呼び出すことによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-122">This is achieved by calling the following Webhost APIs:</span></span>  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="ccfc3-123">このリスナ アダプタは、`WebhostRegisterProtocol` を最初に呼び出した後、applicationHost.config (%windir%\system32\inetsrv 内にあります) に登録されているすべてのアプリケーションの WAS からコールバック `ApplicationCreated` を受信します。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-123">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="ccfc3-124">このサンプルで処理するのは、(プロトコル ID が "net.udp" の) UDP プロトコルが有効なアプリケーションだけです。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-124">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="ccfc3-125">他の実装でこのアプリケーションへの動的な構成変更 (アプリケーションを無効から有効に移行する場合など) に応答する場合、そうした実装では異なる方法でアプリケーションを処理することがあります。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-125">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="ccfc3-126">コールバック `ConfigManagerInitializationCompleted` が受信される場合、WAS により、プロトコルの初期化に関するすべての通知が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-126">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="ccfc3-127">その時点で、リスナ アダプタはアクティベーション要求を処理する準備ができています。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-127">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="ccfc3-128">アプリケーションに初めて新しい要求が届くと、このリスナ アダプタは `WebhostOpenListenerChannelInstance` を WAS に呼び出します。ワーカー プロセスがまだ開始されていない場合は、これにより開始されます。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-128">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="ccfc3-129">次に、プロトコル ハンドラが読み込まれ、リスナ アダプタと仮想アプリケーション間の通信を開始できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-129">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="ccfc3-130">リスナーアダプターは、次のように <> セクションの% SystemRoot% \System32\inetsrv\ApplicationHost.config に登録され `listenerAdapters` ます。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-130">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="ccfc3-131">プロトコル リスナ</span><span class="sxs-lookup"><span data-stu-id="ccfc3-131">Protocol Listener</span></span>  

 <span data-ttu-id="ccfc3-132">UDP プロトコル リスナはプロトコル アクティベータ内部のモジュールで、仮想アプリケーションの代わりに UDP エンドポイントでリッスンします。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-132">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="ccfc3-133">これは `UdpSocketListener` クラスに実装されています。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-133">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="ccfc3-134">エンドポイントは `IPEndpoint` として表され、このポート番号はサイトのプロトコルのバインディングから抽出されます。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-134">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="ccfc3-135">サービスの制御</span><span class="sxs-lookup"><span data-stu-id="ccfc3-135">Control Service</span></span>  

 <span data-ttu-id="ccfc3-136">このサンプルでは、WCF を使用して、アクティベーターと WAS ワーカープロセス間の通信を行います。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-136">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="ccfc3-137">アクティベータに存在するサービスは、コントロール サービスと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-137">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="ccfc3-138">プロトコル ハンドラー</span><span class="sxs-lookup"><span data-stu-id="ccfc3-138">Protocol Handlers</span></span>  

 <span data-ttu-id="ccfc3-139">リスナ アダプタが `WebhostOpenListenerChannelInstance` を呼び出した後、ワーカー プロセスが開始されていない場合は WAS プロセス マネージャによって開始されます。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-139">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="ccfc3-140">ワーカー プロセス内部のアプリケーション マネージャは、UDP プロセス プロトコル ハンドラ (PPH) を読み込み、`ListenerChannelId` を要求します。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-140">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="ccfc3-141">PPH は、呼び出しを有効にし `IAdphManager` ます。`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="ccfc3-141">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="ccfc3-142">を実行して、UDP AppDomain プロトコルハンドラー (ADPH) を開始します。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-142">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="ccfc3-143">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="ccfc3-143">HostedUDPTransportConfiguration</span></span>  

 <span data-ttu-id="ccfc3-144">この情報は、Web.config で次のように登録されます。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-144">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="ccfc3-145">このサンプルの特殊なセットアップ</span><span class="sxs-lookup"><span data-stu-id="ccfc3-145">Special Setup for This Sample</span></span>  

 <span data-ttu-id="ccfc3-146">このサンプルは、Windows Vista、Windows Server 2008、または Windows 7 でのみビルドおよび実行可能です。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-146">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="ccfc3-147">サンプルを実行するには、最初にすべてのコンポーネントを正しくセットアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-147">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="ccfc3-148">サンプルをインストールするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-148">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="ccfc3-149">このサンプルをセットアップするには</span><span class="sxs-lookup"><span data-stu-id="ccfc3-149">To set up this sample</span></span>  
  
1. <span data-ttu-id="ccfc3-150">次のコマンドを使用して、ASP.NET 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-150">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="ccfc3-151">Windows Vista でプロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-151">Build the project on Windows Vista.</span></span> <span data-ttu-id="ccfc3-152">コンパイル後、ビルド後のフェーズで次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-152">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    - <span data-ttu-id="ccfc3-153">UDP バインディングを [既定の Web サイト] のサイトにインストールします。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-153">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    - <span data-ttu-id="ccfc3-154">物理パス "%SystemDrive%\inetpub\wwwroot\servicemodelsamples" をポイントする、仮想アプリケーション "ServiceModelSamples" を作成します。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-154">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    - <span data-ttu-id="ccfc3-155">さらに、この仮想アプリケーションの "net.udp" プロトコルを有効にします。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-155">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3. <span data-ttu-id="ccfc3-156">ユーザー インターフェイス アプリケーション "WasNetActivator.exe" を起動します。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-156">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="ccfc3-157">[ **セットアップ** ] タブをクリックし、次のチェックボックスをオンにして、[ **インストール** ] をクリックしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-157">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    - <span data-ttu-id="ccfc3-158">UDP リスナ アダプタ</span><span class="sxs-lookup"><span data-stu-id="ccfc3-158">UDP Listener Adapter</span></span>  
  
    - <span data-ttu-id="ccfc3-159">UDP プロトコル ハンドラ</span><span class="sxs-lookup"><span data-stu-id="ccfc3-159">UDP Protocol Handlers</span></span>  
  
4. <span data-ttu-id="ccfc3-160">ユーザーインターフェイスアプリケーション "WasNetActivator.exe" の [ **アクティブ化** ] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-160">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="ccfc3-161">[ **開始** ] ボタンをクリックして、リスナーアダプターを開始します。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-161">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="ccfc3-162">これで、プログラムを実行する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-162">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ccfc3-163">このサンプルの実行後は、Cleanup.bat を実行して、[既定の Web サイト] から net.udp バインディングを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-163">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="ccfc3-164">使用例</span><span class="sxs-lookup"><span data-stu-id="ccfc3-164">Sample Usage</span></span>  

 <span data-ttu-id="ccfc3-165">コンパイル後、次の 4 つの異なるバイナリが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-165">After compilation, there are four different binaries generated:</span></span>  
  
- <span data-ttu-id="ccfc3-166">Client.exe: クライアント コード。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-166">Client.exe: The client code.</span></span> <span data-ttu-id="ccfc3-167">App.config は、クライアント構成ファイルの Client.exe.config にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-167">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
- <span data-ttu-id="ccfc3-168">UDPActivation.dll: 主要なすべての UDP 実装を含むライブラリ。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-168">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
- <span data-ttu-id="ccfc3-169">Service.dll: サービス コード。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-169">Service.dll: The service code.</span></span> <span data-ttu-id="ccfc3-170">これは、ServiceModelSamples 仮想アプリケーションの \bin ディレクトリにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-170">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="ccfc3-171">サービスファイルは Service .svc であり、構成ファイルは Web.config です。コンパイル後、これらは次の場所にコピーされます:%Systemdrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="ccfc3-171">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
- <span data-ttu-id="ccfc3-172">WasNetActivator: UDP アクティベータ プログラム。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-172">WasNetActivator: The UDP activator program.</span></span>  
  
- <span data-ttu-id="ccfc3-173">必要なすべての要素が正しくインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-173">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="ccfc3-174">サンプルを実行する方法を、次の手順に示します。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-174">The following steps show how to run the sample:</span></span>  
  
1. <span data-ttu-id="ccfc3-175">次の Windows サービスが開始されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-175">Ensure that the following Windows services have been started:</span></span>  
  
    - <span data-ttu-id="ccfc3-176">Windows プロセス アクティブ化サービス (WAS)。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-176">Windows Process Activation Service (WAS).</span></span>  
  
    - <span data-ttu-id="ccfc3-177">インターネット インフォメーション サービス (IIS): W3SVC。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-177">Internet Information Services (IIS): W3SVC.</span></span>  
  
2. <span data-ttu-id="ccfc3-178">次に、アクティベータ WasNetActivator.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-178">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="ccfc3-179">[ **アクティブ化** ] タブのドロップダウンリストで、唯一のプロトコルである **UDP** が選択されています。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-179">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="ccfc3-180">[ **開始** ] ボタンをクリックして、アクティベーターを開始します。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-180">Click the **Start** button to start the activator.</span></span>  
  
3. <span data-ttu-id="ccfc3-181">アクティベータが開始されると、コマンド ウィンドウで Client.exe を実行することにより、クライアント コードを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-181">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="ccfc3-182">このサンプルの出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-182">The following is the sample output:</span></span>  
  
    ```console  
    Testing Udp Activation.  
    Start the status service.  
    Sending UDP datagrams.  
    Type a word that you want to say to the server: Hello, world!  
        Sending datagram: Hello, world![0]  
        Sending datagram: Hello, world![1]  
        Sending datagram: Hello, world![2]  
        Sending datagram: Hello, world![3]  
        Sending datagram: Hello, world![4]  
    Calling UDP duplex contract (ICalculatorContract).  
        0 + 0 = 0  
        1 + 2 = 3  
        2 + 4 = 6  
        3 + 6 = 9  
        4 + 8 = 12  
    Getting status and dump server traces:  
        Operation 'Hello' is called: Hello, world![0]  
        Operation 'Hello' is called: Hello, world![1]  
        Operation 'Hello' is called: Hello, world![2]  
        Operation 'Hello' is called: Hello, world![3]  
        Operation 'Hello' is called: Hello, world![4]  
        Operation 'Add' is called: 0 + 0  
        Operation 'Add' is called: 1 + 2  
        Operation 'Add' is called: 2 + 4  
        Operation 'Add' is called: 3 + 6  
        Operation 'Add' is called: 4 + 8  
    Press <ENTER> to complete test.  
    ```  
  
> [!IMPORTANT]
> <span data-ttu-id="ccfc3-183">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-183">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ccfc3-184">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-184">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ccfc3-185">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-185">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ccfc3-186">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ccfc3-186">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
