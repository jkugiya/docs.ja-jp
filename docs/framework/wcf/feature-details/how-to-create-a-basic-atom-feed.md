---
description: '詳細については、「方法: 基本的な Atom フィードを作成する」を参照してください。'
title: '方法: 基本的な ATOM フィードを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
ms.openlocfilehash: 4f4fa6e5b4e2b6935fb51cbc200e5ed9e03843ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734790"
---
# <a name="how-to-create-a-basic-atom-feed"></a><span data-ttu-id="194a2-103">方法: 基本的な ATOM フィードを作成する</span><span class="sxs-lookup"><span data-stu-id="194a2-103">How to: Create a Basic Atom Feed</span></span>

<span data-ttu-id="194a2-104">Windows Communication Foundation (WCF) を使用すると、配信フィードを公開するサービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="194a2-104">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="194a2-105">ここでは、ATOM 配信フィードを公開する配信サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="194a2-105">This topic discusses how to create a syndication service that exposes an Atom syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="194a2-106">基本的な配信サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="194a2-106">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="194a2-107"><xref:System.ServiceModel.Web.WebGetAttribute> 属性でマークされたインターフェイスを使用して、サービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="194a2-107">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="194a2-108">配信フィードとして公開される各操作は、<xref:System.ServiceModel.Syndication.Atom10FeedFormatter> オブジェクトを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="194a2-108">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> object.</span></span>  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="194a2-109"><xref:System.ServiceModel.Web.WebGetAttribute> を適用するすべてのサービス操作は、HTTP GET 要求にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="194a2-109">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> are mapped to HTTP GET requests.</span></span> <span data-ttu-id="194a2-110">他の HTTP メソッドに操作をマッピングするには、代わりに <xref:System.ServiceModel.Web.WebInvokeAttribute> を使用します。</span><span class="sxs-lookup"><span data-stu-id="194a2-110">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> <span data-ttu-id="194a2-111">詳細については、「 [方法: 基本的な WCF WEB HTTP サービスを作成](how-to-create-a-basic-wcf-web-http-service.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="194a2-111">For more information, see [How to: Create a Basic WCF Web HTTP Service](how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2. <span data-ttu-id="194a2-112">サービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="194a2-112">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3. <span data-ttu-id="194a2-113"><xref:System.ServiceModel.Syndication.SyndicationFeed> オブジェクトを作成し、作成者、カテゴリ、および説明を追加します。</span><span class="sxs-lookup"><span data-stu-id="194a2-113">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4. <span data-ttu-id="194a2-114">複数の <xref:System.ServiceModel.Syndication.SyndicationItem> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="194a2-114">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5. <span data-ttu-id="194a2-115"><xref:System.ServiceModel.Syndication.SyndicationItem> オブジェクトをフィードに追加します。</span><span class="sxs-lookup"><span data-stu-id="194a2-115">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6. <span data-ttu-id="194a2-116">フィードを返します。</span><span class="sxs-lookup"><span data-stu-id="194a2-116">Return the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="194a2-117">サービスをホストするには</span><span class="sxs-lookup"><span data-stu-id="194a2-117">To host the service</span></span>  
  
1. <span data-ttu-id="194a2-118"><xref:System.ServiceModel.Web.WebServiceHost> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="194a2-118">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2. <span data-ttu-id="194a2-119">サービス ホストを開き、サービスからフィードを読み込み、フィードを表示してから、ユーザーが Enter キーを押すのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="194a2-119">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="194a2-120">HTTP GET で GetBlog() を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="194a2-120">To call GetBlog() with an HTTP GET</span></span>  
  
1. <span data-ttu-id="194a2-121">Internet Explorer を開き、次の URL を入力して、enter キーを押します。 `http://localhost:8000/BlogService/GetBlog`</span><span class="sxs-lookup"><span data-stu-id="194a2-121">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`</span></span>  
  
     <span data-ttu-id="194a2-122">URL には、サービスのベースアドレス ( `http://localhost:8000/BlogService` )、エンドポイントの相対アドレス、および呼び出すサービス操作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="194a2-122">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="194a2-123">コードから GetBlog() を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="194a2-123">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="194a2-124">ベース アドレスと呼び出すメソッドを使用して <xref:System.Xml.XmlReader> を作成します。</span><span class="sxs-lookup"><span data-stu-id="194a2-124">Create a <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="194a2-125">静的な <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> メソッドを呼び出し、作成した <xref:System.Xml.XmlReader> を渡します。</span><span class="sxs-lookup"><span data-stu-id="194a2-125">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="194a2-126">これにより、サービス操作が呼び出され、サービス操作から返されたフォーマッタが新しい <xref:System.ServiceModel.Syndication.SyndicationFeed> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="194a2-126">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="194a2-127">フィード オブジェクトにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="194a2-127">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="194a2-128">例</span><span class="sxs-lookup"><span data-stu-id="194a2-128">Example</span></span>  

 <span data-ttu-id="194a2-129">この例の完全なコードの一覧を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="194a2-129">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="194a2-130">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="194a2-130">Compiling the Code</span></span>  

 <span data-ttu-id="194a2-131">上記のコードのコンパイル時には、System.ServiceModel.dll と System.ServiceModel.Web.dll が参照されます。</span><span class="sxs-lookup"><span data-stu-id="194a2-131">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="194a2-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="194a2-132">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
