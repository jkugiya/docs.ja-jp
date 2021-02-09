---
description: '詳細情報: 方法:プライベート ストレージ フィールドを指定する'
title: '方法: プライベート ストレージ フィールドを指定する'
ms.date: 03/30/2017
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
ms.openlocfilehash: 09f3566ca85a69f27794329ae12fc45d88bb518c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785901"
---
# <a name="how-to-specify-private-storage-fields"></a><span data-ttu-id="48c54-103">方法: プライベート ストレージ フィールドを指定する</span><span class="sxs-lookup"><span data-stu-id="48c54-103">How to: Specify Private Storage Fields</span></span>

<span data-ttu-id="48c54-104">基になるストレージ フィールドの名前を指定するには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の <xref:System.Data.Linq.Mapping.DataAttribute> 属性の <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="48c54-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property on the <xref:System.Data.Linq.Mapping.DataAttribute> attribute to designate the name of an underlying storage field.</span></span>  
  
 <span data-ttu-id="48c54-105">コード例については、「<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48c54-105">For code examples, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a><span data-ttu-id="48c54-106">基になるストレージ フィールドの名前を指定するには</span><span class="sxs-lookup"><span data-stu-id="48c54-106">To specify the name of an underlying storage field</span></span>  
  
1. <span data-ttu-id="48c54-107"><xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="48c54-107">Add the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="48c54-108">フィールドの名前を <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> プロパティの値として代入します。</span><span class="sxs-lookup"><span data-stu-id="48c54-108">Assign the name of the field as the value of the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48c54-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="48c54-109">See also</span></span>

- [<span data-ttu-id="48c54-110">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="48c54-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="48c54-111">方法: コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="48c54-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
