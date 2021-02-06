---
description: 詳細については、「HttpCookieSession」を参照してください。
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: b5b5a94cd6c019e39d95c1581ce88dbca4460ba6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631958"
---
# <a name="httpcookiesession"></a><span data-ttu-id="b33ec-103">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="b33ec-103">HttpCookieSession</span></span>

<span data-ttu-id="b33ec-104">このサンプルでは、カスタム プロトコル チャネルを作成し、セッション管理用の HTTP クッキーを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-104">This sample demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span> <span data-ttu-id="b33ec-105">このチャネルは、Windows Communication Foundation (WCF) サービスと ASMX クライアント間、または WCF クライアントと ASMX サービス間の通信を可能にします。</span><span class="sxs-lookup"><span data-stu-id="b33ec-105">This channel enables communication between Windows Communication Foundation (WCF) services and ASMX clients or between WCF clients and ASMX services.</span></span>  
  
 <span data-ttu-id="b33ec-106">セッションベースの ASMX Web サービスでクライアントが Web メソッドを呼び出すと、ASP.NET エンジンは次の処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-106">When a client calls a Web method in an ASMX Web service that is session-based, the ASP.NET engine does the following:</span></span>  
  
- <span data-ttu-id="b33ec-107">一意の ID (セッション ID) を生成します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-107">Generates a unique ID (session ID).</span></span>  
  
- <span data-ttu-id="b33ec-108">セッション オブジェクトを生成し、一意の ID に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-108">Generates the session object and associates it with the unique ID.</span></span>  
  
- <span data-ttu-id="b33ec-109">一意の IDを Set-Cookie HTTP 応答ヘッダーに追加し、クライアントに送信します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-109">Adds the unique ID to a Set-Cookie HTTP response header and sends it to the client.</span></span>  
  
- <span data-ttu-id="b33ec-110">送信されるセッション ID に基づき、以降の呼び出しでクライアントを識別します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-110">Identifies the client on subsequent calls based on the session ID it sends to it.</span></span>  
  
 <span data-ttu-id="b33ec-111">クライアントは、サーバーに対する以降の要求にこのセッション ID を含めます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-111">The client includes this session ID in its subsequent requests to the server.</span></span> <span data-ttu-id="b33ec-112">サーバーはクライアントのセッション ID を使用して、現在の HTTP コンテキストに適切なセッション オブジェクトを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-112">The server uses the session ID from the client to load the appropriate session object for the current HTTP context.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b33ec-113">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b33ec-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b33ec-114">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b33ec-114">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b33ec-115">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="b33ec-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b33ec-116">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-116">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a><span data-ttu-id="b33ec-117">HttpCookieSession チャネルのメッセージ交換パターン</span><span class="sxs-lookup"><span data-stu-id="b33ec-117">HttpCookieSession Channel Message Exchange Pattern</span></span>  

 <span data-ttu-id="b33ec-118">このサンプルでは、ASMX などのシナリオのセッションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="b33ec-118">This sample enables sessions for ASMX-like scenarios.</span></span> <span data-ttu-id="b33ec-119">チャネル スタックの一番下には、<xref:System.ServiceModel.Channels.IRequestChannel> と <xref:System.ServiceModel.Channels.IReplyChannel> をサポートする HTTP トランスポートがあります。</span><span class="sxs-lookup"><span data-stu-id="b33ec-119">At the bottom of our channel stack, we have the HTTP transport that supports <xref:System.ServiceModel.Channels.IRequestChannel> and <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="b33ec-120">これはチャネルのジョブで、より高いレベルのチャネル スタックにセッションを提供します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-120">It is the job of the channel to provide sessions to the higher levels of the channel stack.</span></span> <span data-ttu-id="b33ec-121">このサンプルでは、セッションをサポートする 2 つのチャネル (<xref:System.ServiceModel.Channels.IRequestSessionChannel> および <xref:System.ServiceModel.Channels.IReplySessionChannel>) を実装します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-121">The sample implements two channels, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> and <xref:System.ServiceModel.Channels.IReplySessionChannel>) that support sessions.</span></span>  
  
## <a name="service-channel"></a><span data-ttu-id="b33ec-122">サービス チャネル</span><span class="sxs-lookup"><span data-stu-id="b33ec-122">Service Channel</span></span>  

 <span data-ttu-id="b33ec-123">このサンプルでは、`HttpCookieReplySessionChannelListener` クラスでサービス チャネルを提供します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-123">The sample provides a service channel in the `HttpCookieReplySessionChannelListener` class.</span></span> <span data-ttu-id="b33ec-124">このクラスは <xref:System.ServiceModel.Channels.IChannelListener> インターフェイスを実装し、チャネル スタックの低いレベルにある <xref:System.ServiceModel.Channels.IReplyChannel> チャネルを <xref:System.ServiceModel.Channels.IReplySessionChannel> に変換します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-124">This class implements the <xref:System.ServiceModel.Channels.IChannelListener> interface and converts the <xref:System.ServiceModel.Channels.IReplyChannel> channel from lower in the channel stack to a <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="b33ec-125">このプロセスは、次の部分に分かれています。</span><span class="sxs-lookup"><span data-stu-id="b33ec-125">This process can be divided into the following parts:</span></span>  
  
- <span data-ttu-id="b33ec-126">チャネル リスナが開かれると、チャネル リスナは内部リスナの内部チャネルを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-126">When the channel listener is opened, it accepts an inner channel from its inner listener.</span></span> <span data-ttu-id="b33ec-127">内部リスナはデータグラム リスナであり、受け入れられたチャネルの有効期間は内部リスナの有効期間から切り離されるため、次のように、内部リスナを閉じて内部チャネルの保持のみを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-127">Because the inner listener is a datagram listener and the lifetime of an accepted channel is decoupled from the lifetime of the listener, we can close the inner listener and only hold on to the inner channel</span></span>  
  
    ```csharp  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- <span data-ttu-id="b33ec-128">チャネル リスナを開くプロセスが完了したら、次のようにメッセージ ループをセットアップし、内部チャネルからメッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-128">When the open process completes, we set up a message loop to receive messages from the inner channel.</span></span>  
  
    ```csharp  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       this.completeReceiveCallback ??= new WaitCallback(CompleteReceiveCallback);
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
- <span data-ttu-id="b33ec-129">メッセージが到着したら、サービス チャネルはセッション識別子を調べ、非多重化を行って適切なセッション チャネルに変換します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-129">When a message arrives, the service channel examines the session identifier and de-multiplexes to the appropriate session channel.</span></span> <span data-ttu-id="b33ec-130">このチャネル リスナは、セッション識別子をセッション チャネル インスタンスにマップするディクショナリを保持します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-130">The channel listener maintains a dictionary that maps the session identifiers to the session channel instances.</span></span>  
  
    ```csharp  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 <span data-ttu-id="b33ec-131">`HttpCookieReplySessionChannel` クラスは、<xref:System.ServiceModel.Channels.IReplySessionChannel> を実装しています。</span><span class="sxs-lookup"><span data-stu-id="b33ec-131">The `HttpCookieReplySessionChannel` class implements <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="b33ec-132">より高いレベルのチャネル スタックは <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> メソッドを呼び出し、このセッションの要求を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-132">Higher levels of the channel stack call the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method to read requests for this session.</span></span> <span data-ttu-id="b33ec-133">各セッション チャネルにはプライベート メッセージ キューがあり、サービス チャネルによって設定されます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-133">Each session channel has a private message queue that is populated by the service channel.</span></span>  
  
```csharp  
InputQueue<RequestContext> requestQueue;  
```  
  
 <span data-ttu-id="b33ec-134">ユーザーが <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> メソッドを呼び出したときに、このメッセージ キューにメッセージがない場合は、チャネルは指定された時間分待機した後にシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="b33ec-134">In the case when someone calls the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method and there are no messages in the message queue, the channel waits for a specified amount of time before shutting itself down.</span></span> <span data-ttu-id="b33ec-135">これにより、WCF 以外のクライアント用に作成されたセッションチャネルがクリーンアップされます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-135">This cleans up the session channels created for non-WCF clients.</span></span>  
  
 <span data-ttu-id="b33ec-136">`channelMapping` を使用して `ReplySessionChannels` を追跡します。受け入れられたすべてのチャネルが閉じられた後で、基になる `innerChannel` を閉じます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-136">We use the `channelMapping` to track the `ReplySessionChannels`, and we do not close our underlying `innerChannel` until all the accepted channels have been closed.</span></span> <span data-ttu-id="b33ec-137">この方法により、`HttpCookieReplySessionChannel` は `HttpCookieReplySessionChannelListener` の有効期間を過ぎても存在できます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-137">This way `HttpCookieReplySessionChannel` can exist beyond the lifetime of `HttpCookieReplySessionChannelListener`.</span></span> <span data-ttu-id="b33ec-138">また、リスナのガベージ コレクトは気にする必要はありません。受け入れられたチャネルは、`OnClosed` コールバックを介してそのチャネルのリスナへの参照を保持するためです。</span><span class="sxs-lookup"><span data-stu-id="b33ec-138">We also do not have to worry about the listener getting garbage collected underneath us because the accepted channels keep a reference to their listener through the `OnClosed` callback.</span></span>  
  
## <a name="client-channel"></a><span data-ttu-id="b33ec-139">クライアント チャネル</span><span class="sxs-lookup"><span data-stu-id="b33ec-139">Client channel</span></span>  

 <span data-ttu-id="b33ec-140">対応するクライアント チャネルは、`HttpCookieSessionChannelFactory` クラスにあります。</span><span class="sxs-lookup"><span data-stu-id="b33ec-140">The corresponding client channel is in the `HttpCookieSessionChannelFactory` class.</span></span> <span data-ttu-id="b33ec-141">チャネルの作成中、チャネル ファクトリは内部要求チャネルを `HttpCookieRequestSessionChannel` でラップします。</span><span class="sxs-lookup"><span data-stu-id="b33ec-141">During channel creation, the channel factory wraps the inner request channel with an `HttpCookieRequestSessionChannel`.</span></span> <span data-ttu-id="b33ec-142">`HttpCookieRequestSessionChannel` クラスは、基になる要求チャネルへの呼び出しを転送します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-142">The `HttpCookieRequestSessionChannel` class forwards the calls to the underlying request channel.</span></span> <span data-ttu-id="b33ec-143">クライアントがプロキシを閉じると、`HttpCookieRequestSessionChannel` はチャネルが閉じられようとしていることを示すメッセージをサービスに送信します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-143">When the client closes the proxy, `HttpCookieRequestSessionChannel` sends a message to the service that indicates that the channel is being closed.</span></span> <span data-ttu-id="b33ec-144">そのため、サービス チャネル スタックは、使用中のセッション チャネルを正常にシャットダウンできます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-144">Thus, the service channel stack can gracefully shutdown the session channel that is in use.</span></span>  
  
## <a name="binding-and-binding-element"></a><span data-ttu-id="b33ec-145">バインディングとバインディング要素</span><span class="sxs-lookup"><span data-stu-id="b33ec-145">Binding and Binding Element</span></span>  

 <span data-ttu-id="b33ec-146">サービスとクライアントのチャネルを作成したら、次の手順として、それらを WCF ランタイムに統合します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-146">After creating the service and client channels, the next step is to integrate them into the WCF runtime.</span></span> <span data-ttu-id="b33ec-147">チャネルは、バインディングとバインド要素を介して WCF に公開されます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-147">Channels are exposed to WCF through bindings and binding elements.</span></span> <span data-ttu-id="b33ec-148">バインディングは、1 つまたは複数のバインディング要素で構成されています。</span><span class="sxs-lookup"><span data-stu-id="b33ec-148">A binding consists of one or many binding elements.</span></span> <span data-ttu-id="b33ec-149">WCF には、システム定義のバインディングがいくつか用意されています。たとえば、BasicHttpBinding や WSHttpBinding などです。</span><span class="sxs-lookup"><span data-stu-id="b33ec-149">WCF offers several system-defined bindings; for example, BasicHttpBinding or WSHttpBinding.</span></span> <span data-ttu-id="b33ec-150">`HttpCookieSessionBindingElement` クラスには、バインディング要素の実装が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b33ec-150">The `HttpCookieSessionBindingElement` class contains the implementation for the binding element.</span></span> <span data-ttu-id="b33ec-151">この実装によってチャネル リスナとチャネル ファクトリの作成メソッドがオーバーライドされ、必要なチャネル リスナまたはチャネル ファクトリがインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-151">It overrides the channel listener and channel factory creation methods to do the necessary channel listener or channel factory instantiations.</span></span>  
  
 <span data-ttu-id="b33ec-152">このサンプルでは、サービスの説明のポリシー アサーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-152">The sample uses policy assertions for the service description.</span></span> <span data-ttu-id="b33ec-153">これにより、サンプルのチャネルの要件を、そのサービスを利用できる他のクライアントに公開できます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-153">This allows the sample to publish its channel requirements to other clients that can consume the service.</span></span> <span data-ttu-id="b33ec-154">たとえば、このバインド要素はポリシー アサーションを公開し、セッションがサポートされていることを潜在的なクライアントに通知します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-154">For example, this binding element publishes policy assertions to let potential clients know that it supports sessions.</span></span> <span data-ttu-id="b33ec-155">このサンプルでは、バインディング要素の構成で `ExchangeTerminateMessage` プロパティが有効になっています。そのため、サービスで余分なメッセージ交換アクションがサポートされ、セッションでのメッセージ交換が終了されることを示すために必要なアサーションが追加されます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-155">Because the sample enables the `ExchangeTerminateMessage` property in the binding element configuration, it adds the necessary assertions to show that the service supports an extra message exchange action to terminate the session conversation.</span></span> <span data-ttu-id="b33ec-156">その後、クライアントはこのアクションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-156">Clients can then use this action.</span></span> <span data-ttu-id="b33ec-157">`HttpCookieSessionBindingElement` から作成されたポリシー アサーションを、次の WSDL コードに示します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-157">The following WSDL code shows the policy assertions created from the `HttpCookieSessionBindingElement`.</span></span>  
  
```xml  
<wsp:Policy wsu:Id="HttpCookieSessionBinding_IWcfCookieSessionService_policy" xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wsp:ExactlyOne>  
<wsp:All>  
<wspe:Utf816FFFECharacterEncoding xmlns:wspe="http://schemas.xmlsoap.org/ws/2004/09/policy/encoding"/>  
<mhsc:httpSessionCookie xmlns:mhsc="http://samples.microsoft.com/wcf/mhsc/policy"/>  
</wsp:All>  
</wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="b33ec-158">`HttpCookieSessionBinding` クラスは、システム指定のバインディング要素を使用する定義済みバインディングです。</span><span class="sxs-lookup"><span data-stu-id="b33ec-158">The `HttpCookieSessionBinding` class is a system-provided binding that uses the binding element described previously.</span></span>  
  
## <a name="adding-the-channel-to-the-configuration-system"></a><span data-ttu-id="b33ec-159">構成システムへのチャネルの追加</span><span class="sxs-lookup"><span data-stu-id="b33ec-159">Adding the Channel to the Configuration System</span></span>  

 <span data-ttu-id="b33ec-160">このサンプルでは、構成を使用してサンプル チャネルを公開する 2 つのクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-160">The sample provides two classes that expose the sample channel through configuration.</span></span> <span data-ttu-id="b33ec-161">1 つ目のクラスは、<xref:System.ServiceModel.Configuration.BindingElementExtensionElement> の `HttpCookieSessionBindingElement` です。</span><span class="sxs-lookup"><span data-stu-id="b33ec-161">The first is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> for the `HttpCookieSessionBindingElement`.</span></span> <span data-ttu-id="b33ec-162">実装の大部分は `HttpCookieSessionBindingConfigurationElement` で代行されます。これは <xref:System.ServiceModel.Configuration.StandardBindingElement> の派生です。</span><span class="sxs-lookup"><span data-stu-id="b33ec-162">The bulk of the implementation is delegated to the `HttpCookieSessionBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="b33ec-163">`HttpCookieSessionBindingConfigurationElement` には、`HttpCookieSessionBindingElement` のプロパティに対応するプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="b33ec-163">The `HttpCookieSessionBindingConfigurationElement` has properties that correspond to the properties on `HttpCookieSessionBindingElement`.</span></span>  
  
### <a name="binding-element-extension-section"></a><span data-ttu-id="b33ec-164">要素拡張セクションのバインディング</span><span class="sxs-lookup"><span data-stu-id="b33ec-164">Binding Element Extension Section</span></span>  

 <span data-ttu-id="b33ec-165">セクション `HttpCookieSessionBindingElementSection` は <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> で、`HttpCookieSessionBindingElement` を構成システムに公開します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-165">The section `HttpCookieSessionBindingElementSection` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `HttpCookieSessionBindingElement` to the configuration system.</span></span> <span data-ttu-id="b33ec-166">構成セクション名をいくつかオーバーライドして、バインド要素の種類とバインド要素の作成方法が定義されます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-166">With a few overrides the configuration section name, the type of the binding element and how to create the binding element are defined.</span></span> <span data-ttu-id="b33ec-167">その後、次のようにして拡張セクションを構成ファイルに登録できます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-167">We can then register the extension section in a configuration file as follows:</span></span>  
  
```xml  
<configuration>
    <system.serviceModel>
      <extensions>
        <bindingElementExtensions>
          <add name="httpCookieSession"
               type=  
"Microsoft.ServiceModel.Samples.HttpCookieSessionBindingElementElement,
                    HttpCookieSessionExtension, Version=1.0.0.0,
                    Culture=neutral, PublicKeyToken=null"/>  
        </bindingElementExtensions >  
      </extensions>  
  
      <bindings>  
      <customBinding>  
        <binding name="allowCookiesBinding">  
          <textMessageEncoding messageVersion="Soap11WSAddressing10" />  
          <httpCookieSession sessionTimeout="10" exchangeTerminateMessage="true" />  
          <httpTransport allowCookies="true" />  
        </binding>  
      </customBinding>  
      </bindings>
    </system.serviceModel>
</configuration>  
```  
  
## <a name="test-code"></a><span data-ttu-id="b33ec-168">テスト コード</span><span class="sxs-lookup"><span data-stu-id="b33ec-168">Test Code</span></span>  

 <span data-ttu-id="b33ec-169">このサンプルのトランスポートを使用するテスト コードは、クライアント ディレクトリとサービス ディレクトリで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-169">Test code for using this sample transport is available in the Client and Service directories.</span></span> <span data-ttu-id="b33ec-170">2つのテストで構成されます。1つのテストでは、クライアントでがに設定されたバインディングを使用 `allowCookies` `true` します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-170">It consists of two tests—one test uses a binding with `allowCookies` set to `true` on the client.</span></span> <span data-ttu-id="b33ec-171">2 つ目のテストは、バインディングで明示的なシャットダウン (メッセージ交換の終了) を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b33ec-171">The second test enables explicit shutdown (using the terminate message exchange) on the binding.</span></span>  
  
 <span data-ttu-id="b33ec-172">このサンプルを実行すると、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b33ec-172">When you run the sample, you should see the following output:</span></span>  
  
```console  
Simple binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
Smart binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b33ec-173">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="b33ec-173">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b33ec-174">次のコマンドを使用して、ASP.NET 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="b33ec-174">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="b33ec-175">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b33ec-175">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="b33ec-176">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b33ec-176">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="b33ec-177">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b33ec-177">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
