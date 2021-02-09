---
description: '詳細情報: 方法:データ サービスの結果のページングを有効にする (WCF Data Services)'
title: '方法: データ サービスの結果のページングを有効にする (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 27a2b37f432d906022d06492b2f687681d9b9ac8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765335"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="5ce17-103">方法: データ サービスの結果のページングを有効にする (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="5ce17-103">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="5ce17-104">WCF Data Services では、データ サービス クエリによって返されるエンティティの数を制限できます。</span><span class="sxs-lookup"><span data-stu-id="5ce17-104">WCF Data Services enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="5ce17-105">ページ制限は、サービスの初期化時に呼び出されるメソッドで定義され、エンティティ セットごとに設定できます。</span><span class="sxs-lookup"><span data-stu-id="5ce17-105">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="5ce17-106">ページングが有効である場合、フィードの最終的なエントリには、データの次のページへのリンクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5ce17-106">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="5ce17-107">詳細については、「[データ サービスの構成](configuring-the-data-service-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ce17-107">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="5ce17-108">このトピックでは、返された `Customers` エンティティ セットおよび `Orders` エンティティ セットのページングを有効にするためにデータ サービスを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5ce17-108">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="5ce17-109">このトピックの例では、Northwind サンプル データ サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="5ce17-109">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="5ce17-110">このサービスは、[WCF Data Services クイック スタート](quickstart-wcf-data-services.md)を完了したときに作成されます。</span><span class="sxs-lookup"><span data-stu-id="5ce17-110">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="5ce17-111">返された Customer エンティティ セットおよび Orders エンティティ セットのページングを有効化する方法</span><span class="sxs-lookup"><span data-stu-id="5ce17-111">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
- <span data-ttu-id="5ce17-112">データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5ce17-112">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="5ce17-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ce17-113">See also</span></span>

- [<span data-ttu-id="5ce17-114">遅延コンテンツの読み込み</span><span class="sxs-lookup"><span data-stu-id="5ce17-114">Loading Deferred Content</span></span>](loading-deferred-content-wcf-data-services.md)
- [<span data-ttu-id="5ce17-115">方法: ページングされた結果を読み込む</span><span class="sxs-lookup"><span data-stu-id="5ce17-115">How to: Load Paged Results</span></span>](how-to-load-paged-results-wcf-data-services.md)
