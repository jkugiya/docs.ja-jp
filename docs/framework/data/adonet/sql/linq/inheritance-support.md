---
description: '詳細情報: 継承のサポート'
title: 継承のサポート
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: ff6956441ab72f720151e42bd9358c8df1170e09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803868"
---
# <a name="inheritance-support"></a><span data-ttu-id="02d0d-103">継承のサポート</span><span class="sxs-lookup"><span data-stu-id="02d0d-103">Inheritance Support</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="02d0d-104">では、"*シングル テーブル マッピング*" がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="02d0d-104">supports *single-table mapping*.</span></span> <span data-ttu-id="02d0d-105">これは、1 つの継承階層全体が単一のデータベース テーブルに保存されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="02d0d-105">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="02d0d-106">テーブルには、階層構造内で使用され得るすべてのデータ列の平坦化された共用体が格納されます </span><span class="sxs-lookup"><span data-stu-id="02d0d-106">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="02d0d-107">(2 つのテーブルを 1 つに結合し、元のテーブルのいずれかにあった行が新しいテーブルに含まれるようにした結果、1 つの共用体が形成されます)。行によって表されるインスタンスの型に適合しない列には null が設定されます。</span><span class="sxs-lookup"><span data-stu-id="02d0d-107">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="02d0d-108">シングル テーブル マッピング形式は、継承を表す最も単純な形式であり、多くのクエリのカテゴリで良好なパフォーマンス特性を示します。</span><span class="sxs-lookup"><span data-stu-id="02d0d-108">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="02d0d-109">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] でこのマッピングを実装するには、継承階層のルート クラスで属性および属性プロパティを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="02d0d-109">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="02d0d-110">詳細については、[継承階層を割り当てる](how-to-map-inheritance-hierarchies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02d0d-110">For more information, see [How to: Map Inheritance Hierarchies](how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="02d0d-111">Visual Studio を使用している開発者は、オブジェクト リレーショナル デザイナーを使用して継承改装をマップすることもできます。</span><span class="sxs-lookup"><span data-stu-id="02d0d-111">Developers using Visual Studio can also use the Object Relational Designer to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02d0d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="02d0d-112">See also</span></span>

- [<span data-ttu-id="02d0d-113">背景情報</span><span class="sxs-lookup"><span data-stu-id="02d0d-113">Background Information</span></span>](background-information.md)
