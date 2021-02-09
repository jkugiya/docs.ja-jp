---
description: '詳細情報: 方法:リフレクション プロバイダーでフィードをカスタマイズする (WCF Data Services)'
title: '方法: リフレクション プロバイダーでフィードをカスタマイズする (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: 91ac9cd3a5e882714335ce1d4ef29510d4640534
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765634"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="1e7a5-103">方法: リフレクション プロバイダーでフィードをカスタマイズする (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="1e7a5-103">How to: Customize Feeds with the Reflection Provider (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="1e7a5-104">WCF Data Services では、データ サービス応答の Atom シリアル化をカスタマイズして、AtomPub プロトコルで定義されている未使用の要素にエンティティのプロパティをマップできます。</span><span class="sxs-lookup"><span data-stu-id="1e7a5-104">WCF Data Services enables you to customize the Atom serialization in a data service response so that properties of an entity may be mapped to unused elements that are defined in the AtomPub protocol.</span></span> <span data-ttu-id="1e7a5-105">このトピックでは、リフレクション プロバイダーを使用して、定義されているデータ モデル内のエンティティ型のマッピング属性を定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1e7a5-105">This topic shows how to define mapping attributes for the entity types in a data model that is defined by using the reflection provider.</span></span> <span data-ttu-id="1e7a5-106">詳細については、「[フィードのカスタマイズ](feed-customization-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e7a5-106">For more information, see [Feed Customization](feed-customization-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="1e7a5-107">次の例のデータ モデルは、トピック「[方法: リフレクション プロバイダーを使用してデータ サービスを作成する](create-a-data-service-using-rp-wcf-data-services.md)」で定義されています。</span><span class="sxs-lookup"><span data-stu-id="1e7a5-107">The data model for this example is defined in the topic [How to: Create a Data Service Using the Reflection Provider](create-a-data-service-using-rp-wcf-data-services.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e7a5-108">例</span><span class="sxs-lookup"><span data-stu-id="1e7a5-108">Example</span></span>  

 <span data-ttu-id="1e7a5-109">次の例では、`Order` 型の両方のプロパティが既存の Atom 要素にマップされます。</span><span class="sxs-lookup"><span data-stu-id="1e7a5-109">In the following example, both properties of the `Order` type are mapped to existing Atom elements.</span></span> <span data-ttu-id="1e7a5-110">`Product` 型の `Item` プロパティは、別の名前空間のカスタム フィード属性にマップされます。</span><span class="sxs-lookup"><span data-stu-id="1e7a5-110">The `Product` property of the `Item` type is mapped to a custom feed attribute in a separate namespace.</span></span>  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a><span data-ttu-id="1e7a5-111">例</span><span class="sxs-lookup"><span data-stu-id="1e7a5-111">Example</span></span>  

 <span data-ttu-id="1e7a5-112">前の例では、URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items` に次の結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="1e7a5-112">The previous example returns the following result for the URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span></span>  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a><span data-ttu-id="1e7a5-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e7a5-113">See also</span></span>

- [<span data-ttu-id="1e7a5-114">リフレクション プロバイダー</span><span class="sxs-lookup"><span data-stu-id="1e7a5-114">Reflection Provider</span></span>](reflection-provider-wcf-data-services.md)
