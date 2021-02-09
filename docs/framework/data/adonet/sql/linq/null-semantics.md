---
description: '詳細情報: null セマンティクス'
title: null セマンティクス
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: 2326cd20a225f31693260aa038477f1f6090d02f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695579"
---
# <a name="null-semantics"></a><span data-ttu-id="ceb50-103">null セマンティクス</span><span class="sxs-lookup"><span data-stu-id="ceb50-103">Null Semantics</span></span>

<span data-ttu-id="ceb50-104">次の表では、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のドキュメントで `null` (Visual Basic では `Nothing`) に関する問題について説明されている各部分へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="ceb50-104">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="ceb50-105">トピック</span><span class="sxs-lookup"><span data-stu-id="ceb50-105">Topic</span></span>|<span data-ttu-id="ceb50-106">説明</span><span class="sxs-lookup"><span data-stu-id="ceb50-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ceb50-107">SQL と CLR の型の不一致</span><span class="sxs-lookup"><span data-stu-id="ceb50-107">SQL-CLR Type Mismatches</span></span>](sql-clr-type-mismatches.md)|<span data-ttu-id="ceb50-108">このトピックの「null セマンティクス」セクションでは、3 つの状態を持つ SQL のブール値と、2 つの状態を持つ共通言語ランタイム (CLR) の <xref:System.Boolean>、リテラルの `Nothing` (Visual Basic) と `null` (C#)、および関連するその他の話題について説明されています。</span><span class="sxs-lookup"><span data-stu-id="ceb50-108">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="ceb50-109">標準クエリ演算子の変換</span><span class="sxs-lookup"><span data-stu-id="ceb50-109">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)|<span data-ttu-id="ceb50-110">このトピックの「null セマンティクス」セクションでは、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]での null の比較のセマンティクスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ceb50-110">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="ceb50-111">System.String メソッド</span><span class="sxs-lookup"><span data-stu-id="ceb50-111">System.String Methods</span></span>](system-string-methods.md)|<span data-ttu-id="ceb50-112">このトピックの「.NET との相違」セクションでは、 <xref:System.String.LastIndexOf%2A> の戻り値が 0 の場合に、文字列が null の場合と、見つかった位置が 0 の場合の両方があることについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ceb50-112">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="ceb50-113">数値のシーケンスの合計の計算</span><span class="sxs-lookup"><span data-stu-id="ceb50-113">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="ceb50-114">null のみを含むシーケンスまたは空のシーケンスの場合に、<xref:System.Linq.Enumerable.Sum%2A> 演算子が 0 ではなく `null` (Visual Basic では `Nothing`) に評価されることについて説明されています。</span><span class="sxs-lookup"><span data-stu-id="ceb50-114">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ceb50-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ceb50-115">See also</span></span>

- [<span data-ttu-id="ceb50-116">データ型と関数</span><span class="sxs-lookup"><span data-stu-id="ceb50-116">Data Types and Functions</span></span>](data-types-and-functions.md)
