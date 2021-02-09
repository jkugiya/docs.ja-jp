---
description: '詳細情報: 方法:クラスとしてテーブルを表す'
title: '方法: クラスとしてテーブルを表す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 9ec5b7309d7d10eaa6e4da6cd6fe4b1d03df1dd9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723583"
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="23e1f-103">方法: クラスとしてテーブルを表す</span><span class="sxs-lookup"><span data-stu-id="23e1f-103">How to: Represent Tables as Classes</span></span>

<span data-ttu-id="23e1f-104">データベース テーブルに関連付けられたエンティティ クラスとしてクラスを指定するには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="23e1f-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="23e1f-105">データベース テーブルにクラスを対応付けるには</span><span class="sxs-lookup"><span data-stu-id="23e1f-105">To map a class to a database table</span></span>  
  
- <span data-ttu-id="23e1f-106">クラス宣言に <xref:System.Data.Linq.Mapping.TableAttribute> 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="23e1f-106">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23e1f-107">例</span><span class="sxs-lookup"><span data-stu-id="23e1f-107">Example</span></span>  

 <span data-ttu-id="23e1f-108">次のコードでは、`Customer` データベース テーブルに関連付けられたエンティティ クラスとして、`Customers` クラスを確立します。</span><span class="sxs-lookup"><span data-stu-id="23e1f-108">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="23e1f-109">名前が推論できる場合は、<xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> プロパティを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="23e1f-109">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="23e1f-110">名前を指定しない場合は、プロパティまたはフィールドと同じ名前であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="23e1f-110">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23e1f-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="23e1f-111">See also</span></span>

- [<span data-ttu-id="23e1f-112">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="23e1f-112">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="23e1f-113">方法: コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="23e1f-113">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
