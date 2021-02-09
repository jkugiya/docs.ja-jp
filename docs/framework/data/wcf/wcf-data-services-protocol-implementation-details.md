---
description: '詳細情報: WCF Data Services プロトコル実装の詳細'
title: WCF Data Services プロトコル実装の詳細
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 123f41859fdf579a75bb925a63619e4089577911
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748246"
---
# <a name="wcf-data-services-protocol-implementation-details"></a><span data-ttu-id="09824-103">WCF Data Services プロトコル実装の詳細</span><span class="sxs-lookup"><span data-stu-id="09824-103">WCF Data Services Protocol Implementation Details</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

## <a name="odata-protocol-implementation-details"></a><span data-ttu-id="09824-104">OData プロトコル実装の詳細</span><span class="sxs-lookup"><span data-stu-id="09824-104">OData Protocol Implementation Details</span></span>  

<span data-ttu-id="09824-105">Open Data Protocol (OData) では、プロトコルを実装するデータ サービスが、特定の機能の最小セットを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09824-105">The Open Data Protocol (OData) requires that a data service that implements the protocol provide a certain minimum set of functionalities.</span></span> <span data-ttu-id="09824-106">これらの機能は、"すべきこと" と "必ずしなければならないこと" に関して、プロトコル ドキュメントで説明されています。</span><span class="sxs-lookup"><span data-stu-id="09824-106">These functionalities are described in the protocol documents in terms of "should" and "must".</span></span> <span data-ttu-id="09824-107">その他のオプション機能は、"できること" に関して説明されています。</span><span class="sxs-lookup"><span data-stu-id="09824-107">Other optional functionality is described in terms of "may".</span></span> <span data-ttu-id="09824-108">この記事では、現在 WCF Data Services で実装されていないオプション機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="09824-108">This article describes these optional functionalities that are not currently implemented by WCF Data Services.</span></span>
  
### <a name="support-for-the-format-query-option"></a><span data-ttu-id="09824-109">$format クエリ オプションのサポート</span><span class="sxs-lookup"><span data-stu-id="09824-109">Support for the $format Query Option</span></span>  

 <span data-ttu-id="09824-110">OData プロトコルでは、JavaScript Notation (JSON) フィードと Atom フィードの両方がサポートされており、OData の `$format` システム クエリ オプションを使用すると、クライアントで応答フィードの形式を要求できます。</span><span class="sxs-lookup"><span data-stu-id="09824-110">The OData protocol supports both JavaScript Notation (JSON) and Atom feeds, and OData provides the `$format` system query option to allow a client to request the format of the response feed.</span></span> <span data-ttu-id="09824-111">このシステム クエリ オプションは、データ サービスでサポートされている場合、要求の Accept ヘッダーの値をオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="09824-111">This system query option, if supported by the data service, must override the value of the Accept header of the request.</span></span> <span data-ttu-id="09824-112">WCF Data Services では、JSON フィードと Atom フィードのどちらでも返すことができます。</span><span class="sxs-lookup"><span data-stu-id="09824-112">WCF Data Services supports returning both JSON and Atom feeds.</span></span> <span data-ttu-id="09824-113">ただし、既定の実装では `$format` クエリ オプションをサポートしておらず、Accept ヘッダーの値だけを使用して応答の形式を決定します。</span><span class="sxs-lookup"><span data-stu-id="09824-113">However, the default implementation does not support the `$format` query option and uses only the value of the Accept header to determine the format of the response.</span></span> <span data-ttu-id="09824-114">クライアントが Accept ヘッダーを設定できない場合のように、データ サービスで `$format` クエリ オプションをサポートしなければならないこともあります。</span><span class="sxs-lookup"><span data-stu-id="09824-114">There are cases when your data service may need to support the `$format` query option, such as when clients cannot set the Accept header.</span></span> <span data-ttu-id="09824-115">このようなシナリオをサポートするには、このオプションを URI で処理するように、データ サービスを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09824-115">To support these scenarios, you must extend your data service to handle this option in the URI.</span></span>
  
## <a name="wcf-data-services-behaviors"></a><span data-ttu-id="09824-116">WCF Data Services の動作</span><span class="sxs-lookup"><span data-stu-id="09824-116">WCF Data Services Behaviors</span></span>  

 <span data-ttu-id="09824-117">次の WCF Data Services の動作は、OData プロトコルでは明示的に定義されていません。</span><span class="sxs-lookup"><span data-stu-id="09824-117">The following WCF Data Services behaviors are not explicitly defined by the OData protocol:</span></span>  
  
### <a name="default-sorting-behavior"></a><span data-ttu-id="09824-118">既定の並べ替え動作</span><span class="sxs-lookup"><span data-stu-id="09824-118">Default Sorting Behavior</span></span>  

 <span data-ttu-id="09824-119">データ サービスに送信されるクエリ要求に、`$top` または `$skip` システム クエリ オプションが含まれ、`$orderby` システム クエリ オプションが含まれていない場合、返されるフィードはキー プロパティで昇順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="09824-119">When a query request that is sent to the data service includes a `$top` or `$skip` system query option and does not include the `$orderby` system query option, the returned feed is sorted by the key properties, in ascending order.</span></span> <span data-ttu-id="09824-120">これは、結果を正しくページングするには並べ替えが必要であるためです。</span><span class="sxs-lookup"><span data-stu-id="09824-120">This is because ordering is required to ensure the correct paging of results.</span></span> <span data-ttu-id="09824-121">そのために、データ サービスがクエリに並べ替え式を追加します。</span><span class="sxs-lookup"><span data-stu-id="09824-121">To do this, the data service adds an ordering expression to the query.</span></span> <span data-ttu-id="09824-122">この動作は、データ サービスでサーバー ドリブン ページングが有効になっている場合にも発生します。</span><span class="sxs-lookup"><span data-stu-id="09824-122">This behavior also occurs when server-driven paging is enabled in the data service.</span></span> <span data-ttu-id="09824-123">詳細については、「[データ サービスの構成](configuring-the-data-service-wcf-data-services.md)」を参照してください。返されるフィードの並べ替えを制御するには、クエリ URI に `$orderby` を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="09824-123">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).To control the ordering of the returned feed, you should include `$orderby` in the query URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09824-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="09824-124">See also</span></span>

- [<span data-ttu-id="09824-125">WCF Data Services の定義</span><span class="sxs-lookup"><span data-stu-id="09824-125">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="09824-126">WCF Data Services クライアント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="09824-126">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
