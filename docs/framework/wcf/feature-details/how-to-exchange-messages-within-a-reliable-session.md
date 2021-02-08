---
description: '詳細については、「方法: 信頼できるセッション内でメッセージを交換する」を参照してください。'
title: '方法: 信頼されたセッション内のメッセージを変換する'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: e4a8f6a180b9c2ff9471558997034d02acc817e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802906"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="00ad9-103">方法: 信頼されたセッション内のメッセージを変換する</span><span class="sxs-lookup"><span data-stu-id="00ad9-103">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="00ad9-104">このトピックでは、信頼できるセッションを有効にするために必要な手順について説明します。ここでは、信頼できるセッションを (既定ではなく) オプションでサポートするシステム指定のバインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="00ad9-104">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="00ad9-105">信頼できるセッションは、コードまたは構成ファイルで宣言によって強制的に有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="00ad9-105">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="00ad9-106">この手順では、クライアントとサービスの構成ファイルを使用して、信頼できるセッションを有効にし、メッセージが送信された順序と同じ順序で到着することを指定します。</span><span class="sxs-lookup"><span data-stu-id="00ad9-106">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="00ad9-107">この手順の重要な部分は、エンドポイント構成要素に、 `bindingConfiguration` という名前のバインディング構成を参照する属性が含まれていることです `Binding1` 。</span><span class="sxs-lookup"><span data-stu-id="00ad9-107">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="00ad9-108">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)構成要素は、要素の属性をに設定することによって、信頼できるセッションを有効にするために、この名前を参照し `enabled` [**\<reliableSession>**](/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) `true` ます。</span><span class="sxs-lookup"><span data-stu-id="00ad9-108">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) element to `true`.</span></span> <span data-ttu-id="00ad9-109">信頼できるセッションで順序付き配信の保証を指定するには、`ordered` 属性を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="00ad9-109">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="00ad9-110">この例のソースコピーについては、「 [WS Reliable Session](../samples/ws-reliable-session.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00ad9-110">For the source copy of this example, see [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="00ad9-111">信頼できるセッションを使用するようにサービスを WSHttpBinding で構成する</span><span class="sxs-lookup"><span data-stu-id="00ad9-111">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="00ad9-112">サービスの種類にサービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="00ad9-112">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="00ad9-113">サービス クラスにサービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="00ad9-113">Implement the service contract in a service class.</span></span> <span data-ttu-id="00ad9-114">サービスの実装内では、アドレスまたはバインド情報が指定されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="00ad9-114">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="00ad9-115">構成ファイルからアドレスやバインド情報を取得するためのコードを記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="00ad9-115">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="00ad9-116">*Web.config* ファイルを作成して、 `CalculatorService` <xref:System.ServiceModel.WSHttpBinding> 信頼できるセッションを有効にし、必要なメッセージを順次配信するを使用するのエンドポイントを構成します。</span><span class="sxs-lookup"><span data-stu-id="00ad9-116">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="00ad9-117">次の行を含む .svc ファイルを作成 *し* ます。</span><span class="sxs-lookup"><span data-stu-id="00ad9-117">Create a *Service.svc* file that contains the line:</span></span>

   ```aspx-csharp
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="00ad9-118">サービスの *.svc* ファイルをインターネットインフォメーションサービス (IIS) 仮想ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="00ad9-118">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="00ad9-119">信頼できるセッションを使用するようにクライアントを WSHttpBinding で構成する</span><span class="sxs-lookup"><span data-stu-id="00ad9-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="00ad9-120">コマンドラインから [ServiceModel メタデータユーティリティツール (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) を使用して、サービスメタデータからコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="00ad9-120">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="00ad9-121">生成されたクライアントには、 `ICalculator` クライアント実装が満たす必要のあるサービスコントラクトを定義するインターフェイスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="00ad9-121">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="00ad9-122">生成されたクライアント アプリケーションは `ClientCalculator` も実装します。</span><span class="sxs-lookup"><span data-stu-id="00ad9-122">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="00ad9-123">サービスの実装内でアドレスおよびバインド情報が指定されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="00ad9-123">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="00ad9-124">構成ファイルからアドレスやバインド情報を取得するためのコードを記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="00ad9-124">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="00ad9-125">また *Svcutil.exe* は、クラスを使用するクライアントの構成も生成し <xref:System.ServiceModel.WSHttpBinding> ます。</span><span class="sxs-lookup"><span data-stu-id="00ad9-125">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="00ad9-126">Visual Studio を使用する場合は、構成ファイルに *App.config* 名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="00ad9-126">Name the configuration file *App.config* when using Visual Studio.</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="00ad9-127">アプリケーションでのインスタンスを作成 `ClientCalculator` し、サービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="00ad9-127">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="00ad9-128">クライアントをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="00ad9-128">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="00ad9-129">例</span><span class="sxs-lookup"><span data-stu-id="00ad9-129">Example</span></span>

<span data-ttu-id="00ad9-130">システム指定のバインディングの中には、信頼できるセッションを既定でサポートするものがあります。</span><span class="sxs-lookup"><span data-stu-id="00ad9-130">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="00ad9-131">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="00ad9-131">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="00ad9-132">信頼できるセッションをサポートするカスタムバインディングを作成する方法の例については、「 [方法: HTTPS を使用してカスタムの信頼できるセッションのバインディングを作成](how-to-create-a-custom-reliable-session-binding-with-https.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00ad9-132">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="00ad9-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="00ad9-133">See also</span></span>

- [<span data-ttu-id="00ad9-134">信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="00ad9-134">Reliable Sessions</span></span>](reliable-sessions.md)
