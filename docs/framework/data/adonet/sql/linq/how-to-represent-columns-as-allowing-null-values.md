---
description: '詳細情報: 方法:null 値を許可する列として列を表す'
title: '方法: null 値を許可する列として列を表す'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: 019affd13fa9c2629c6a0ec66c42f19842a4d824
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695906"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="57981-103">方法: null 値を許可する列として列を表す</span><span class="sxs-lookup"><span data-stu-id="57981-103">How to: Represent Columns as Allowing Null Values</span></span>

<span data-ttu-id="57981-104">データベース列が null 値を保持できることを指定するには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性の <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="57981-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="57981-105">コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57981-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="57981-106">null 値を許可する列を指定するには</span><span class="sxs-lookup"><span data-stu-id="57981-106">To designate a column as allowing null values</span></span>  
  
1. <span data-ttu-id="57981-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="57981-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="57981-108"><xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> プロパティ値を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="57981-108">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57981-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="57981-109">See also</span></span>

- [<span data-ttu-id="57981-110">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="57981-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="57981-111">方法: コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="57981-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
