---
description: '詳細情報: 方法:データベースの名前を指定する'
title: '方法: データベースの名前を指定する'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: 231c78830e009ed3414609eb6dbe05c3745f3e05
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785888"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="b908e-103">方法: データベースの名前を指定する</span><span class="sxs-lookup"><span data-stu-id="b908e-103">How to: Specify Database Names</span></span>

<span data-ttu-id="b908e-104"><xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 属性の <xref:System.Data.Linq.Mapping.DatabaseAttribute> プロパティを使用すると、接続によってデータベースの名前が提供されない場合に、名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b908e-104">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="b908e-105">コード例については、「<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b908e-105">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="b908e-106">データベースの名前を指定するには</span><span class="sxs-lookup"><span data-stu-id="b908e-106">To specify the name of the database</span></span>  
  
1. <span data-ttu-id="b908e-107">データベースのクラス宣言に <xref:System.Data.Linq.Mapping.DatabaseAttribute> 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="b908e-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2. <span data-ttu-id="b908e-108"><xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 属性に <xref:System.Data.Linq.Mapping.DatabaseAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="b908e-108">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3. <span data-ttu-id="b908e-109"><xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> プロパティ値を目的の名前に設定します。</span><span class="sxs-lookup"><span data-stu-id="b908e-109">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b908e-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="b908e-110">See also</span></span>

- [<span data-ttu-id="b908e-111">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="b908e-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="b908e-112">方法: コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="b908e-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
