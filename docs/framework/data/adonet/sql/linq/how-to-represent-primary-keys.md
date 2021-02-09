---
description: '詳細情報: 方法:主キーを表す'
title: '方法: 主キーを表す'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 1fbac2d60bd730718b5330bfd48910a61deae15c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723609"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="ab63f-103">方法: 主キーを表す</span><span class="sxs-lookup"><span data-stu-id="ab63f-103">How to: Represent Primary Keys</span></span>

<span data-ttu-id="ab63f-104">データベース列の主キーを表すプロパティまたはフィールドを指定するには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性の <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="ab63f-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="ab63f-105">コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab63f-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ab63f-106">では、計算列は主キーとしてサポートされません。</span><span class="sxs-lookup"><span data-stu-id="ab63f-106">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="ab63f-107">プロパティまたはフィールドを主キーとして指定するには</span><span class="sxs-lookup"><span data-stu-id="ab63f-107">To designate a property or field as a primary key</span></span>  
  
1. <span data-ttu-id="ab63f-108"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="ab63f-108">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="ab63f-109">値として `true` を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab63f-109">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab63f-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab63f-110">See also</span></span>

- [<span data-ttu-id="ab63f-111">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="ab63f-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="ab63f-112">方法: コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="ab63f-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
