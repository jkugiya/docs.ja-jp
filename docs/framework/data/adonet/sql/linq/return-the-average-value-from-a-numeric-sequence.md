---
description: '詳細情報: 一連の数値の平均値の取得'
title: 一連の数値の平均値の取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee3b8673-a2e7-4b2d-9b5c-4972ff9e665d
ms.openlocfilehash: 4e0415c9ef981364fc3d6481ed6455f132e84932
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663067"
---
# <a name="return-the-average-value-from-a-numeric-sequence"></a><span data-ttu-id="7ff4a-103">一連の数値の平均値の取得</span><span class="sxs-lookup"><span data-stu-id="7ff4a-103">Return the Average Value From a Numeric Sequence</span></span>

<span data-ttu-id="7ff4a-104"><xref:System.Linq.Enumerable.Average%2A> 演算子は、一連の数値の平均値を計算します。</span><span class="sxs-lookup"><span data-stu-id="7ff4a-104">The <xref:System.Linq.Enumerable.Average%2A> operator computes the average of a sequence of numeric values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ff4a-105">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で整数値の `Average` が変換されるときには、倍精度浮動小数点数ではなく整数として計算されます。</span><span class="sxs-lookup"><span data-stu-id="7ff4a-105">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Average` of integer values is computed as an integer, not as a double.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ff4a-106">例</span><span class="sxs-lookup"><span data-stu-id="7ff4a-106">Example</span></span>  

 <span data-ttu-id="7ff4a-107">次の例は、`Freight` テーブルの `Orders` の平均値を返します。</span><span class="sxs-lookup"><span data-stu-id="7ff4a-107">The following example returns the average of `Freight` values in the `Orders` table.</span></span>  
  
 <span data-ttu-id="7ff4a-108">Northwind サンプル データベースでは、結果は `78.2442` になります。</span><span class="sxs-lookup"><span data-stu-id="7ff4a-108">Results from the sample Northwind database would be `78.2442`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#1)]
 [!code-vb[DLinqQueryExamples#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="7ff4a-109">例</span><span class="sxs-lookup"><span data-stu-id="7ff4a-109">Example</span></span>  

 <span data-ttu-id="7ff4a-110">次の例は、`Products` テーブルのすべての `Products` の単価の平均値を返します。</span><span class="sxs-lookup"><span data-stu-id="7ff4a-110">The following example returns the average of the unit price of all `Products` in the `Products` table.</span></span>  
  
 <span data-ttu-id="7ff4a-111">Northwind サンプル データベースでは、結果は `28.8663` になります。</span><span class="sxs-lookup"><span data-stu-id="7ff4a-111">Results from the sample Northwind database would be `28.8663`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#2)]
 [!code-vb[DLinqQueryExamples#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="7ff4a-112">例</span><span class="sxs-lookup"><span data-stu-id="7ff4a-112">Example</span></span>  

 <span data-ttu-id="7ff4a-113">次の例は、`Average` 演算子を使用して、カテゴリ内の平均単価よりも単価が高い `Products` を見つけます。</span><span class="sxs-lookup"><span data-stu-id="7ff4a-113">The following example uses the `Average` operator to find those `Products` whose unit price is higher than the average unit price of the category it belongs to.</span></span> <span data-ttu-id="7ff4a-114">その後、結果をグループ別に表示します。</span><span class="sxs-lookup"><span data-stu-id="7ff4a-114">The example then displays the results in groups.</span></span>  
  
 <span data-ttu-id="7ff4a-115">この例の戻り値の型は匿名型なので、C# で `var` キーワードを使用する必要がある点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="7ff4a-115">Note that this example requires the use of the `var` keyword in C#, because the return type is anonymous.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#3)]
 [!code-vb[DLinqQueryExamples#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#3)]  
  
 <span data-ttu-id="7ff4a-116">Northwind サンプル データベースに対してこのクエリを実行すると、結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7ff4a-116">If you run this query against the Northwind sample database, the results should resemble of the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `Ipoh Coffee`  
  
 `2`  
  
 `Grandma's Boysenberry Spread`  
  
 `Northwoods Cranberry Sauce`  
  
 `Sirop d'érable`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `Gumbär Gummibärchen`  
  
 `Schoggi Schokolade`  
  
 `Tarte au sucre`  
  
 `4`  
  
 `Queso Manchego La Pastora`  
  
 `Mascarpone Fabioli`  
  
 `Raclette Courdavault`  
  
 `Camembert Pierrot`  
  
 `Gudbrandsdalsost`  
  
 `Mozzarella di Giovanni`  
  
 `5`  
  
 `Gustaf's Knäckebröd`  
  
 `Gnocchi di nonna Alice`  
  
 `Wimmers gute Semmelknödel`  
  
 `6`  
  
 `Mishi Kobe Niku`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Rössle Sauerkraut`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Ikura`  
  
 `Carnarvon Tigers`  
  
 `Nord-Ost Matjeshering`  
  
 `Gravad lax`  
  
## <a name="see-also"></a><span data-ttu-id="7ff4a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ff4a-117">See also</span></span>

- [<span data-ttu-id="7ff4a-118">集計クエリ</span><span class="sxs-lookup"><span data-stu-id="7ff4a-118">Aggregate Queries</span></span>](aggregate-queries.md)
