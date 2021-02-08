---
description: '詳細については、「方法: Atom と RSS の両方としてフィードを公開する」を参照してください。'
title: '方法: Atom および RSS の両方としてフィードを公開する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: 5afe08b2c1d9fc687563e124061fe7fb59257180
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793780"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="65d0b-103">方法: Atom および RSS の両方としてフィードを公開する</span><span class="sxs-lookup"><span data-stu-id="65d0b-103">How to: Expose a Feed as Both Atom and RSS</span></span>

<span data-ttu-id="65d0b-104">Windows Communication Foundation (WCF) を使用すると、配信フィードを公開するサービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="65d0b-104">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="65d0b-105">このトピックでは、Atom 1.0 と RSS 2.0 の両方を使用して配信フィードを公開する配信サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-105">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="65d0b-106">このサービスは、どちらかの配信フォーマットを返すエンドポイントを公開します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-106">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="65d0b-107">簡略化のため、この例で使用するサービスは自己ホスト型です。</span><span class="sxs-lookup"><span data-stu-id="65d0b-107">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="65d0b-108">運用環境では、このタイプのサービスは IIS または WAS でホストされます。</span><span class="sxs-lookup"><span data-stu-id="65d0b-108">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> <span data-ttu-id="65d0b-109">さまざまな WCF ホスティングオプションの詳細については、「 [ホスティング](hosting.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65d0b-109">For more information about the different WCF hosting options, see [Hosting](hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="65d0b-110">基本的な配信サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="65d0b-110">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="65d0b-111"><xref:System.ServiceModel.Web.WebGetAttribute> 属性でマークされたインターフェイスを使用して、サービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-111">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="65d0b-112">配信フィードとして公開される各操作は、<xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-112">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="65d0b-113"><xref:System.ServiceModel.Web.WebGetAttribute> のパラメーターに注意してください。</span><span class="sxs-lookup"><span data-stu-id="65d0b-113">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> <span data-ttu-id="65d0b-114">`UriTemplate` は、このサービス操作を呼び出すために使用される URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-114">`UriTemplate` specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="65d0b-115">このパラメーターの文字列には、リテラルと変数が中かっこ ({*format*}) で格納されています。</span><span class="sxs-lookup"><span data-stu-id="65d0b-115">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="65d0b-116">この変数は、サービス操作の `format` パラメーターに対応します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-116">This variable corresponds to the service operation's `format` parameter.</span></span> <span data-ttu-id="65d0b-117">詳細については、「<xref:System.UriTemplate>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65d0b-117">For more information, see <xref:System.UriTemplate>.</span></span> <span data-ttu-id="65d0b-118">`BodyStyle` は、このサービス操作が送受信するメッセージの書き方に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="65d0b-118">`BodyStyle` affects how the messages that this service operation sends and receives are written.</span></span> <span data-ttu-id="65d0b-119"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> は、このサービス操作に送受信されるデータが、インフラストラクチャにより定義された XML 要素でラップされないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-119"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> <span data-ttu-id="65d0b-120">詳細については、「<xref:System.ServiceModel.Web.WebMessageBodyStyle>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65d0b-120">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="65d0b-121">このインターフェイスのサービス操作により返される型を指定するには、<xref:System.ServiceModel.ServiceKnownTypeAttribute> を使用します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-121">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2. <span data-ttu-id="65d0b-122">サービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-122">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3. <span data-ttu-id="65d0b-123"><xref:System.ServiceModel.Syndication.SyndicationFeed> オブジェクトを作成し、作成者、カテゴリ、および説明を追加します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-123">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4. <span data-ttu-id="65d0b-124">複数の <xref:System.ServiceModel.Syndication.SyndicationItem> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-124">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5. <span data-ttu-id="65d0b-125"><xref:System.ServiceModel.Syndication.SyndicationItem> オブジェクトをフィードに追加します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-125">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6. <span data-ttu-id="65d0b-126">format パラメーターを使用して、要求された形式を返します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-126">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="65d0b-127">サービスをホストするには</span><span class="sxs-lookup"><span data-stu-id="65d0b-127">To host the service</span></span>  
  
1. <span data-ttu-id="65d0b-128"><xref:System.ServiceModel.Web.WebServiceHost> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-128">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="65d0b-129"><xref:System.ServiceModel.Web.WebServiceHost> クラスは、エンドポイントがコードまたは構成で指定されない限り、自動的にエンドポイントをサービスのベース アドレスで追加します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-129">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="65d0b-130">次の例は、既定のエンドポイントが公開されるので、エンドポイントは指定されません。</span><span class="sxs-lookup"><span data-stu-id="65d0b-130">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2. <span data-ttu-id="65d0b-131">サービス ホストを開き、サービスからフィードを読み込み、フィードを表示してから、ユーザーが Enter キーを押すのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="65d0b-131">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="65d0b-132">HTTP GET を使用して GetBlog を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="65d0b-132">To call GetBlog with an HTTP GET</span></span>  
  
1. <span data-ttu-id="65d0b-133">Internet Explorer を開き、次の URL を入力して、enter キーを押します `http://localhost:8000/BlogService/GetBlog` 。</span><span class="sxs-lookup"><span data-stu-id="65d0b-133">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span>
  
     <span data-ttu-id="65d0b-134">URL には、サービスのベースアドレス ( `http://localhost:8000/BlogService` )、エンドポイントの相対アドレス、および呼び出すサービス操作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="65d0b-134">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="65d0b-135">コードから GetBlog() を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="65d0b-135">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="65d0b-136">ベース アドレスと呼び出すメソッドを使用して <xref:System.Xml.XmlReader> を作成します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-136">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="65d0b-137">静的な <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> メソッドを呼び出し、作成した <xref:System.Xml.XmlReader> を渡します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-137">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="65d0b-138">これにより、サービス操作が呼び出され、サービス操作から返されたフォーマッタが新しい <xref:System.ServiceModel.Syndication.SyndicationFeed> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="65d0b-138">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="65d0b-139">フィード オブジェクトにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="65d0b-139">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="65d0b-140">例</span><span class="sxs-lookup"><span data-stu-id="65d0b-140">Example</span></span>  

 <span data-ttu-id="65d0b-141">この例の完全なコードの一覧を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="65d0b-141">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="65d0b-142">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="65d0b-142">Compiling the Code</span></span>  

 <span data-ttu-id="65d0b-143">上記のコードのコンパイル時には、System.ServiceModel.dll と System.ServiceModel.Web.dll が参照されます。</span><span class="sxs-lookup"><span data-stu-id="65d0b-143">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d0b-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="65d0b-144">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
