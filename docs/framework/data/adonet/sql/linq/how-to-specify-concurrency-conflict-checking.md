---
description: '詳細情報: 方法:コンカレンシーの競合のチェックを指定する'
title: '方法: コンカレンシーの競合のチェックを指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: a1c1c771dba95e558d86764d023625a63e9e53bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785927"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a><span data-ttu-id="c8a25-103">方法: コンカレンシーの競合のチェックを指定する</span><span class="sxs-lookup"><span data-stu-id="c8a25-103">How to: Specify Concurrency-Conflict Checking</span></span>

<span data-ttu-id="c8a25-104"><xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すときにコンカレンシーの競合をチェックするデータベース列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c8a25-104">You can specify which columns of the database are to be checked for concurrency conflicts when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="c8a25-105">詳細については、[コンカレンシーの競合を検査するメンバーを指定する](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8a25-105">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8a25-106">例</span><span class="sxs-lookup"><span data-stu-id="c8a25-106">Example</span></span>  

 <span data-ttu-id="c8a25-107">次のコード例では、更新の確認時に `HomePage` メンバーを検査しないことを指定しています。</span><span class="sxs-lookup"><span data-stu-id="c8a25-107">The following code specifies that the `HomePage` member should never be tested during update checks.</span></span> <span data-ttu-id="c8a25-108">詳細については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8a25-108">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c8a25-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8a25-109">See also</span></span>

- [<span data-ttu-id="c8a25-110">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="c8a25-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="c8a25-111">方法: コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="c8a25-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
