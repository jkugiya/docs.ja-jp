---
description: '詳細情報: 方法:データ サービスへのアクセスを有効にする (WCF Data Services)'
title: '方法: データ サービスへのアクセスを有効にする (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 42be9c4c31da7bbbfef07958deef685d52df597b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765426"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="446ec-103">方法: データ サービスへのアクセスを有効にする (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="446ec-103">How to: Enable Access to the Data Service (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="446ec-104">WCF Data Services では、データ サービスによって公開されているリソースに明示的にアクセス権を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="446ec-104">In WCF Data Services, you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="446ec-105">つまり、新しいデータ サービスを作成した後も、個々のリソースに対し、エンティティ セットとして明示的にアクセスを許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="446ec-105">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="446ec-106">このトピックでは、[クイックスタート](quickstart-wcf-data-services.md)を完了するときに作成する Northwind データ サービスの 5 つのエンティティ セットへの読み取りおよび書き込みアクセスを有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="446ec-106">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="446ec-107"><xref:System.Data.Services.EntitySetRights> 列挙体は <xref:System.FlagsAttribute> を使用して定義されているので、論理和演算子を使用して 1 つのエンティティ セットに複数のアクセス許可を指定できます。</span><span class="sxs-lookup"><span data-stu-id="446ec-107">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="446ec-108">ASP.NET アプリケーションにアクセスできるクライアントは、データ サービスによって公開されるリソースにもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="446ec-108">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="446ec-109">運用データ サービスで、リソースへの承認されていないアクセスを防止するために、アプリケーション自身もセキュリティで保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="446ec-109">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="446ec-110">詳細については、「[ASP.NET Web サイトのセキュリティ保護](/previous-versions/aspnet/91f66yxt(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="446ec-110">For more information, see [Securing ASP.NET Web Sites](/previous-versions/aspnet/91f66yxt(v=vs.100)).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="446ec-111">データ サービスへのアクセスを有効にするには</span><span class="sxs-lookup"><span data-stu-id="446ec-111">To enable access to the data service</span></span>  
  
- <span data-ttu-id="446ec-112">データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="446ec-112">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="446ec-113">これにより、クライアントから `Orders` および `Order_Details` エンティティ セットへの読み取りおよび書き込みアクセスと、`Customers` エンティティ セットへの読み取り専用アクセスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="446ec-113">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="446ec-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="446ec-114">See also</span></span>

- [<span data-ttu-id="446ec-115">方法: IIS 上で実行する WCF Data Service を開発する</span><span class="sxs-lookup"><span data-stu-id="446ec-115">How to: Develop a WCF Data Service Running on IIS</span></span>](how-to-develop-a-wcf-data-service-running-on-iis.md)
- [<span data-ttu-id="446ec-116">データ サービスの構成</span><span class="sxs-lookup"><span data-stu-id="446ec-116">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
