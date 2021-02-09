---
description: '詳細情報: 方法:列をタイムスタンプ列またはバージョン列として表現する'
title: '方法: 列をタイムスタンプ列またはバージョン列として表現する'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: 042e6a62c66b3f1ef522453157560e5e4c0f7de6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712507"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="d8601-103">方法: 列をタイムスタンプ列またはバージョン列として表現する</span><span class="sxs-lookup"><span data-stu-id="d8601-103">How to: Represent Columns as Timestamp or Version Columns</span></span>

<span data-ttu-id="d8601-104">データベースのタイムスタンプまたはバージョン番号を保持するデータベース列を表すフィールドまたはプロパティを指定するには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性の <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="d8601-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="d8601-105">コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8601-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="d8601-106">タイムスタンプ列またはバージョン列を表すフィールドまたはプロパティを指定するには</span><span class="sxs-lookup"><span data-stu-id="d8601-106">To designate a field or property as representing a timestamp or version column</span></span>  
  
1. <span data-ttu-id="d8601-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="d8601-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="d8601-108"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> プロパティ値を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="d8601-108">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8601-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8601-109">See also</span></span>

- [<span data-ttu-id="d8601-110">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="d8601-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="d8601-111">方法: コンカレンシーの競合を検査するメンバーを指定する</span><span class="sxs-lookup"><span data-stu-id="d8601-111">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [<span data-ttu-id="d8601-112">方法: コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="d8601-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
