---
description: '詳細情報: 関数 (Entity SQL)'
title: 関数 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: c557d264587a1d40194971d756e6b5c75a3856aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786304"
---
# <a name="functions-entity-sql"></a><span data-ttu-id="05ca9-103">関数 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="05ca9-103">Functions (Entity SQL)</span></span>

<span data-ttu-id="05ca9-104">Entity SQL では、ユーザー定義関数、正規の関数、およびプロバイダー固有の関数がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="05ca9-104">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="05ca9-105">ユーザー定義関数は、概念モデルまたはクエリでインラインで指定されます。</span><span class="sxs-lookup"><span data-stu-id="05ca9-105">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="05ca9-106">詳しくは、「[ユーザー定義関数](user-defined-functions-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="05ca9-106">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="05ca9-107">正規の関数は Entity Framework で定義済みであり、データ プロバイダーによってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="05ca9-107">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="05ca9-108">プロバイダーによってサポートされていない関数を呼び出すと、Entity SQL コマンドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="05ca9-108">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="05ca9-109">そのため、通常は、プロバイダー固有の名前空間にあるストア固有の関数よりも正規の関数が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="05ca9-109">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="05ca9-110">詳しくは、「[正規関数](canonical-functions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="05ca9-110">For more information, see [Canonical Functions](canonical-functions.md).</span></span>  
  
 <span data-ttu-id="05ca9-111">Microsoft SQL クライアント マネージド プロバイダーは、プロバイダー固有の一連の関数を提供しています。</span><span class="sxs-lookup"><span data-stu-id="05ca9-111">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="05ca9-112">詳細については、「[Entity Framework 用 SqlClient 関数](../sqlclient-for-ef-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05ca9-112">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05ca9-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="05ca9-113">In This Section</span></span>  

 [<span data-ttu-id="05ca9-114">ユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="05ca9-114">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="05ca9-115">関数のオーバーロードの解決方法</span><span class="sxs-lookup"><span data-stu-id="05ca9-115">Function Overload Resolution</span></span>](function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="05ca9-116">集計関数</span><span class="sxs-lookup"><span data-stu-id="05ca9-116">Aggregate Functions</span></span>](../aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="05ca9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="05ca9-117">See also</span></span>

- [<span data-ttu-id="05ca9-118">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="05ca9-118">Entity SQL Overview</span></span>](entity-sql-overview.md)
