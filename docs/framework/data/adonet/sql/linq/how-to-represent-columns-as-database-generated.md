---
description: '詳細情報: 方法:列をデータベース生成列として表す'
title: '方法: 列をデータベース生成列として表す'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: 01828ef3f73257d20023168f0ea471ee7e3863c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695633"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="d2260-103">方法: 列をデータベース生成列として表す</span><span class="sxs-lookup"><span data-stu-id="d2260-103">How to: Represent Columns as Database-Generated</span></span>

<span data-ttu-id="d2260-104">データベース生成列を表すフィールドまたはプロパティを指定するには、<xref:System.Data.Linq.Mapping.ColumnAttribute> 属性の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="d2260-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="d2260-105">コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2260-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="d2260-106">データベース生成列を表すフィールドまたはプロパティを指定するには</span><span class="sxs-lookup"><span data-stu-id="d2260-106">To designate a field or property as representing a database-generated column</span></span>  
  
1. <span data-ttu-id="d2260-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="d2260-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="d2260-108">プロパティ値を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="d2260-108">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2260-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2260-109">See also</span></span>

- [<span data-ttu-id="d2260-110">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="d2260-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="d2260-111">方法: コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="d2260-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
