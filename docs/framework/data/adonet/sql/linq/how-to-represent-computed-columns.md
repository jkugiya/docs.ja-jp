---
description: '詳細情報: 方法:計算列を表す'
title: '方法: 計算列を表す'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: 5f3b4898cd29c148665c6696b0b3abab42bd071c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695620"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="ffa93-103">方法: 計算列を表す</span><span class="sxs-lookup"><span data-stu-id="ffa93-103">How to: Represent Computed Columns</span></span>

<span data-ttu-id="ffa93-104">計算の結果が格納される列を表すには、<xref:System.Data.Linq.Mapping.ColumnAttribute> 属性の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="ffa93-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="ffa93-105">コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffa93-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ffa93-106">では、計算列は主キーとしてサポートされません。</span><span class="sxs-lookup"><span data-stu-id="ffa93-106">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="ffa93-107">計算列を表すには</span><span class="sxs-lookup"><span data-stu-id="ffa93-107">To represent a computed column</span></span>  
  
1. <span data-ttu-id="ffa93-108"><xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="ffa93-108">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="ffa93-109"><xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> プロパティに数式を表す文字列を代入します。</span><span class="sxs-lookup"><span data-stu-id="ffa93-109">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffa93-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffa93-110">See also</span></span>

- [<span data-ttu-id="ffa93-111">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="ffa93-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="ffa93-112">方法: コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="ffa93-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
