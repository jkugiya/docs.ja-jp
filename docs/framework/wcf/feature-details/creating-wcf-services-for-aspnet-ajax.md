---
description: 詳細については、ASP.NET AJAX 用の WCF サービスの作成に関するページを参照してください。
title: ASP.NET AJAX 用の WCF サービスの作成
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: e4ab977db5632de0c9e825e03369506d4917709f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705123"
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a><span data-ttu-id="e2488-103">ASP.NET AJAX 用の WCF サービスの作成</span><span class="sxs-lookup"><span data-stu-id="e2488-103">Creating WCF Services for ASP.NET AJAX</span></span>

<span data-ttu-id="e2488-104">Microsoft ASP.NET AJAX により、応答性に優れ、使い慣れたユーザー インターフェイス要素を使用して、充実したユーザー エクスペリエンスを提供する Web ページを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="e2488-104">Microsoft ASP.NET AJAX enables you to quickly create Web pages that include a rich user experience with responsive and familiar user interface elements.</span></span> <span data-ttu-id="e2488-105">ASP.NET AJAX には、ブラウザーに依存しない ECMAScript (JavaScript) テクノロジとダイナミック HTML (DHTML) テクノロジを組み込んだクライアント スクリプト ライブラリが用意されており、これらのライブラリが ASP.NET 2.0 サーバー ベース開発プラットフォームと統合されます。</span><span class="sxs-lookup"><span data-stu-id="e2488-105">ASP.NET AJAX provides client-script libraries that incorporate cross-browser ECMAScript (JavaScript) and dynamic HTML (DHTML) technologies, and it integrates them with the ASP.NET 2.0 server-based development platform.</span></span> <span data-ttu-id="e2488-106">ASP.NET AJAX を使用することで、Web アプリケーションのユーザー エクスペリエンスと効率を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="e2488-106">By using ASP.NET AJAX, you can improve the user experience and the efficiency of your Web applications.</span></span>

<span data-ttu-id="e2488-107">ASP.NET AJAX は、クライアント スクリプト ライブラリとサーバー コンポーネントを統合した強固な開発フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="e2488-107">ASP.NET AJAX consists of client-script libraries and of server components that are integrated to provide a robust development framework.</span></span> <span data-ttu-id="e2488-108">ASP.NET ページからサービスにアクセスする場合、サービス URL をページ上の ASP.NET スクリプト マネージャーに追加すると、標準の JavaScript 関数の呼び出しとまったく同じに見える JavaScript コードを使い、サービス操作を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e2488-108">To access a service from an ASP.NET page: once the service URL is added to the ASP.NET Script Manager control on the page, service operations may be invoked using JavaScript code that looks exactly like a regular JavaScript function call.</span></span>

<span data-ttu-id="e2488-109">適切な ASP.NET AJAX エンドポイントを追加することによって、ほとんどの Windows Communication Foundation (WCF) サービスが ASP.NET AJAX と互換性のあるサービスとして公開される場合があります。</span><span class="sxs-lookup"><span data-stu-id="e2488-109">Most Windows Communication Foundation (WCF) services may be exposed as a service compatible with ASP.NET AJAX by adding an appropriate ASP.NET AJAX endpoint.</span></span>

<span data-ttu-id="e2488-110">Visual Studio を使用している場合は、ASP.NET Web サイトまたは Web アプリケーションを操作するときに [ **新しい項目の追加** ] ダイアログボックスで使用できる、AJAX 対応 WCF サービス用のビルド済みテンプレートを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e2488-110">If you are using Visual Studio, you may use a pre-built template for AJAX-enabled WCF services, available in the **Add New Item** dialog when working with ASP.NET Web Sites or Web Applications.</span></span>

<span data-ttu-id="e2488-111">Visual Studio テンプレートを使用しない場合、ASP.NET AJAX エンドポイントを作成するには次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="e2488-111">If you are not using the Visual Studio templates, there are two ways to create an ASP.NET AJAX endpoint:</span></span>

- <span data-ttu-id="e2488-112">構成を使用せずに、動的ホスト アクティブ化を使用してエンドポイントを作成する。</span><span class="sxs-lookup"><span data-stu-id="e2488-112">Create the endpoint using dynamic host activation without using any configuration.</span></span> <span data-ttu-id="e2488-113">これは、WCF 構成システムの操作に慣れていない場合の最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="e2488-113">This is the most basic approach if you are unfamiliar with the WCF configuration system.</span></span> <span data-ttu-id="e2488-114">詳細については、「 [方法: 構成を使用せずに ASP.NET AJAX エンドポイントを追加する](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2488-114">For more information, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>

- <span data-ttu-id="e2488-115">構成を使用して、AJAX 対応エンドポイントを WCF サービスに追加します。</span><span class="sxs-lookup"><span data-stu-id="e2488-115">Add an AJAX-enabled endpoint to a WCF service using configuration.</span></span> <span data-ttu-id="e2488-116">詳細については、「 [方法: 構成を使用して ASP.NET AJAX エンドポイントを追加](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2488-116">For more information, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>

<span data-ttu-id="e2488-117">「 [WCF WEB HTTP プログラミングモデルの概要](wcf-web-http-programming-model-overview.md) 」で説明されている Web プログラミングモデルは、ASP.NET AJAX サービスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="e2488-117">The Web Programming Model described in the [WCF Web HTTP Programming Model Overview](wcf-web-http-programming-model-overview.md) may be used with ASP.NET AJAX services.</span></span> <span data-ttu-id="e2488-118">具体的には次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e2488-118">Specifically:</span></span>

- <span data-ttu-id="e2488-119"><xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性を使用して、HTTP GET 動詞と HTTP POST 動詞のいずれかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="e2488-119">You can use the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to select between HTTP GET and HTTP POST verbs.</span></span> <span data-ttu-id="e2488-120">正しく使用すれば、アプリケーションのパフォーマンスを大幅に向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="e2488-120">If used correctly, this may significantly improve your application’s performance.</span></span> <span data-ttu-id="e2488-121">詳細については、「 [方法: ASP.NET AJAX エンドポイントに対して HTTP POST 要求または HTTP GET 要求を選択する](http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2488-121">For more information, see [How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints](http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).</span></span>

- <span data-ttu-id="e2488-122"><xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> および <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> プロパティを使用して、サービスが返すデータを、既定の JSON (JavaScript Object Notation) ではなく XML データにすることができます。</span><span class="sxs-lookup"><span data-stu-id="e2488-122">You can use the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> and <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> properties to cause your service to return XML data instead of the default JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="e2488-123">これを ASP.NET AJAX フレームワークで行うと、JavaScript クライアントは XML DOM オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e2488-123">Doing this with the ASP.NET AJAX framework causes the JavaScript client to receive an XML DOM object.</span></span>

  > [!WARNING]
  > <span data-ttu-id="e2488-124">この動作を機能させるには、コンテンツ タイプを text/xml に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2488-124">Your operation must set the content type to text/xml for this to work.</span></span> <span data-ttu-id="e2488-125">設定しない場合、JavaScript クライアントは XML DOM オブジェクトではなく XML を含む文字列を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e2488-125">Otherwise, the JavaScript client will receive a string containing the XML instead of an XML DOM object.</span></span>

    <span data-ttu-id="e2488-126">コンテンツ タイプが適切に設定された XML データを返す操作の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e2488-126">The following is an example of an operation that returns XML data with the content type set appropriately:</span></span>

  ```csharp
  [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]
  public XElement GetData()
  {
      XElement x;
      //Get some data here...

      WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";
      return x;
  }
  ```

- <span data-ttu-id="e2488-127">ASP.NET AJAX との互換性が必要な場合、<xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性の他の属性は変更できません。</span><span class="sxs-lookup"><span data-stu-id="e2488-127">No other properties on the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes can be changed if compatibility with ASP.NET AJAX is required.</span></span> <span data-ttu-id="e2488-128">ASP.NET AJAX 呼び出し規約に違反しない限り、Web プログラミング モデルのその他の機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e2488-128">Other aspects of the Web Programming Model can be used as long as the ASP.NET AJAX calling conventions are not violated.</span></span>

 <span data-ttu-id="e2488-129">より高度なシナリオでは、WCF での AJAX サポートの詳細をいくつか理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2488-129">More advanced scenarios require some additional details of AJAX support in WCF be understood:</span></span>

- <span data-ttu-id="e2488-130">JavaScript を使用して AJAX ページクライアントと WCF サービスの間でデータが転送される方法を理解するには、.NET Framework 型を JavaScript の型にマップする方法の詳細については、「 [FOR JSON とその他のデータ転送形式のサポート](support-for-json-and-other-data-transfer-formats.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2488-130">To understand how data is transferred between an AJAX page client and a WCF service using JavaScript, and for details on how .NET Framework types map to JavaScript types, see [Support for JSON and Other Data Transfer Formats](support-for-json-and-other-data-transfer-formats.md).</span></span>

- <span data-ttu-id="e2488-131">たとえば、URL ベースの認証や ASP.NET セッション情報へのアクセスなどの ASP.NET 機能を活用するには、構成で ASP.NET 互換モードを有効にします。</span><span class="sxs-lookup"><span data-stu-id="e2488-131">To take advantage of ASP.NET features, for example, URL-based authentication and accessing the ASP.NET session information, you may want to enable the ASP.NET Compatibility Mode through configuration.</span></span>

<span data-ttu-id="e2488-132">WCF の AJAX エンドポイントは、ASP.NET AJAX フレームワークなしでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="e2488-132">AJAX endpoints in WCF may even be consumed without the ASP.NET AJAX framework.</span></span> <span data-ttu-id="e2488-133">これを行うには、WCF における AJAX サポートのサポートアーキテクチャを理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2488-133">Doing so requires an understanding of the support architecture of AJAX support in WCF.</span></span> <span data-ttu-id="e2488-134">このアーキテクチャの詳細については、「 [WCF WEB HTTP プログラミングオブジェクトモデル](wcf-web-http-programming-object-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2488-134">For a discussion of this architecture, see [WCF Web HTTP Programming Object Model](wcf-web-http-programming-object-model.md).</span></span> <span data-ttu-id="e2488-135">この方法を示すコードサンプルについては、「 [JSON および XML を使用した AJAX サービス](../samples/ajax-service-with-json-and-xml-sample.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2488-135">For a code sample demonstrating this approach, see the [AJAX Service with JSON and XML](../samples/ajax-service-with-json-and-xml-sample.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2488-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2488-136">See also</span></span>

- [<span data-ttu-id="e2488-137">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="e2488-137">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="e2488-138">方法: 構成を使用せずに ASP.NET AJAX エンドポイントを追加する</span><span class="sxs-lookup"><span data-stu-id="e2488-138">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)
- [<span data-ttu-id="e2488-139">方法: 構成を使用して ASP.NET AJAX エンドポイントを追加する</span><span class="sxs-lookup"><span data-stu-id="e2488-139">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
- [<span data-ttu-id="e2488-140">方法: ASP.NET AJAX エンドポイントのために HTTP POST または HTTP GET を選択する</span><span class="sxs-lookup"><span data-stu-id="e2488-140">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>](http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
