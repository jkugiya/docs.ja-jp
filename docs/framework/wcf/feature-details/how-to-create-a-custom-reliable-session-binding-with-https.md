---
description: '詳細については、「方法: HTTPS を使用してカスタムの信頼できるセッションのバインディングを作成する」を参照してください。'
title: '方法: カスタムの信頼できるセッションによる HTTPS を使用したバインディングを作成する'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: 97e0386c3694552099a623a319f566fa4db2a39b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756176"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a><span data-ttu-id="5e145-103">方法: カスタムの信頼できるセッションによる HTTPS を使用したバインディングを作成する</span><span class="sxs-lookup"><span data-stu-id="5e145-103">How to: Create a Custom Reliable Session Binding with HTTPS</span></span>

<span data-ttu-id="5e145-104">ここでは、信頼できるセッションを使用した SSL (Secure Sockets Layer) トランスポート セキュリティの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5e145-104">This topic demonstrates the use of Secure Sockets Layer (SSL) transport security with reliable sessions.</span></span> <span data-ttu-id="5e145-105">HTTPS 上で信頼できるセッションを使用するには、信頼できるセッションと HTTPS トランスポートを使用するカスタム バインドを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e145-105">To use a reliable session over HTTPS, you must create a custom binding that uses a reliable session and the HTTPS transport.</span></span> <span data-ttu-id="5e145-106">信頼できるセッションは、コードを使用するか、構成ファイルで宣言によって、強制的に有効にします。</span><span class="sxs-lookup"><span data-stu-id="5e145-106">You enable the reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="5e145-107">この手順では、クライアントとサービスの構成ファイルを使用して、信頼できるセッションと要素を有効にし [**\<httpsTransport>**](../../configure-apps/file-schema/wcf/httpstransport.md) ます。</span><span class="sxs-lookup"><span data-stu-id="5e145-107">This procedure uses the client and service configuration files to enable the reliable session and the [**\<httpsTransport>**](../../configure-apps/file-schema/wcf/httpstransport.md) element.</span></span>

<span data-ttu-id="5e145-108">この手順の重要な部分は、 **\<endpoint>** 構成要素に `bindingConfiguration` という名前のカスタムバインディング構成を参照する属性が含まれていることです `reliableSessionOverHttps` 。</span><span class="sxs-lookup"><span data-stu-id="5e145-108">The key part of this procedure is that the **\<endpoint>** configuration element contain a `bindingConfiguration` attribute that references a custom binding configuration named `reliableSessionOverHttps`.</span></span> <span data-ttu-id="5e145-109">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)構成要素は、この名前を参照して、信頼できるセッションと HTTPS トランスポートを使用して **\<reliableSession>** 、要素と要素を含めることを指定し **\<httpsTransport>** ます。</span><span class="sxs-lookup"><span data-stu-id="5e145-109">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to specify that a reliable session and the HTTPS transport are used by including **\<reliableSession>** and **\<httpsTransport>** elements.</span></span>

<span data-ttu-id="5e145-110">この例のソースコピーについては、「HTTPS を使用した [カスタムバインディングの信頼できるセッション](../samples/custom-binding-reliable-session-over-https.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e145-110">For the source copy of this example, see [Custom Binding Reliable Session over HTTPS](../samples/custom-binding-reliable-session-over-https.md).</span></span>

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="5e145-111">HTTPS で信頼できるセッションを使用するための CustomBinding でサービスを構成する</span><span class="sxs-lookup"><span data-stu-id="5e145-111">Configure the service with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="5e145-112">サービスの種類にサービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="5e145-112">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. <span data-ttu-id="5e145-113">サービス クラスにサービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="5e145-113">Implement the service contract in a service class.</span></span> <span data-ttu-id="5e145-114">サービスの実装内では、アドレスまたはバインド情報が指定されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5e145-114">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="5e145-115">構成ファイルからアドレスやバインド情報を取得するためのコードを記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5e145-115">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. <span data-ttu-id="5e145-116"> `CalculatorService` `reliableSessionOverHttps` 信頼できるセッションと HTTPS トランスポートを使用するという名前のカスタムバインディングを使用して、のエンドポイントを構成するためのWeb.configファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="5e145-116">Create a *Web.config* file to configure an endpoint for the `CalculatorService` with a custom binding named `reliableSessionOverHttps` that uses a reliable session and the HTTPS transport.</span></span>

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. <span data-ttu-id="5e145-117">次の行を含む .svc ファイルを作成 *し* ます。</span><span class="sxs-lookup"><span data-stu-id="5e145-117">Create a *Service.svc* file that contains the line:</span></span>

   `<%@ServiceHost language=c# Service="CalculatorService" %>`

1. <span data-ttu-id="5e145-118">サービスの *.svc* ファイルをインターネットインフォメーションサービス (IIS) 仮想ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="5e145-118">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="5e145-119">HTTPS で信頼できるセッションを使用するようにクライアントを構成する (CustomBinding)</span><span class="sxs-lookup"><span data-stu-id="5e145-119">Configure the client with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="5e145-120">コマンドラインから [ServiceModel メタデータユーティリティツール (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) を使用して、サービスメタデータからコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="5e145-120">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="5e145-121">生成されるクライアントには、 `ICalculator` クライアント実装が満たす必要のあるサービスコントラクトを定義するインターフェイスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5e145-121">The client that's generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. <span data-ttu-id="5e145-122">生成されたクライアント アプリケーションは `ClientCalculator` も実装します。</span><span class="sxs-lookup"><span data-stu-id="5e145-122">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="5e145-123">サービスの実装内でアドレスとバインディング情報が指定されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5e145-123">Note that the address and binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="5e145-124">構成ファイルからアドレスおよびバインド情報を取得するコードを記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5e145-124">You aren't required to write code to retrieve the address and binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. <span data-ttu-id="5e145-125">`reliableSessionOverHttps`HTTPS トランスポートと信頼できるセッションを使用するように、という名前のカスタムバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="5e145-125">Configure a custom binding named `reliableSessionOverHttps` to use the HTTPS transport and reliable sessions.</span></span>

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. <span data-ttu-id="5e145-126">アプリケーションで `ClientCalculator` のインスタンスを作成し、サービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5e145-126">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. <span data-ttu-id="5e145-127">クライアントをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="5e145-127">Compile and run the client.</span></span>  

## <a name="net-framework-security"></a><span data-ttu-id="5e145-128">.NET Framework のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="5e145-128">.NET Framework security</span></span>

<span data-ttu-id="5e145-129">このサンプルで使用される証明書は *Makecert.exe* で作成されたテスト証明書であるため、ブラウザーからなどの HTTPS アドレスにアクセスしようとすると、セキュリティの警告が表示され `https://localhost/servicemodelsamples/service.svc` ます。</span><span class="sxs-lookup"><span data-stu-id="5e145-129">Because the certificate used in this sample is a test certificate created with *Makecert.exe*, a security alert appears when you try to access an HTTPS address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e145-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e145-130">See also</span></span>

- [<span data-ttu-id="5e145-131">信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="5e145-131">Reliable Sessions</span></span>](reliable-sessions.md)
