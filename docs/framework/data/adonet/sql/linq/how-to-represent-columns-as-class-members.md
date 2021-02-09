---
description: '詳細情報: 方法:クラス メンバーとして列を表す'
title: '方法: クラス メンバーとして列を表す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: 81c35060298cde0081d040f1f874728c23d9c8ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695776"
---
# <a name="how-to-represent-columns-as-class-members"></a><span data-ttu-id="c950f-103">方法: クラス メンバーとして列を表す</span><span class="sxs-lookup"><span data-stu-id="c950f-103">How to: Represent Columns as Class Members</span></span>

<span data-ttu-id="c950f-104">フィールドまたはプロパティをデータベース列に関連付けるには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="c950f-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to associate a field or property with a database column.</span></span>  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a><span data-ttu-id="c950f-105">フィールドまたはプロパティをデータベース列に対応付けるには</span><span class="sxs-lookup"><span data-stu-id="c950f-105">To map a field or property to a database column</span></span>  
  
- <span data-ttu-id="c950f-106">プロパティまたはフィールドの宣言に <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="c950f-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to the property or field declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c950f-107">例</span><span class="sxs-lookup"><span data-stu-id="c950f-107">Example</span></span>  

 <span data-ttu-id="c950f-108">次の例では、`CustomerID` クラス内の `Customer` フィールドを `CustomerID` データベース テーブル内の `Customers` 列に対応付けます。</span><span class="sxs-lookup"><span data-stu-id="c950f-108">The following code maps the `CustomerID` field in the `Customer` class to the `CustomerID` column in the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 <span data-ttu-id="c950f-109">名前が推論できる場合は、<xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> プロパティを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c950f-109">You do not have to specify the <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="c950f-110">名前を指定しない場合は、プロパティまたはフィールドと同じ名前であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="c950f-110">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c950f-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="c950f-111">See also</span></span>

- [<span data-ttu-id="c950f-112">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="c950f-112">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="c950f-113">方法: コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="c950f-113">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
