---
description: '詳細情報: ジェネリック リストへのシーケンスの変換'
title: ジェネリック リストへのシーケンスの変換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab76d93-6898-4e75-b76f-290a66ecead8
ms.openlocfilehash: e9832fd366f22b77674fb4c83f6af7ce89a552c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663119"
---
# <a name="convert-a-sequence-to-a-generic-list"></a><span data-ttu-id="c52cb-103">ジェネリック リストへのシーケンスの変換</span><span class="sxs-lookup"><span data-stu-id="c52cb-103">Convert a Sequence to a Generic List</span></span>

<span data-ttu-id="c52cb-104">シーケンスからジェネリック リストを作成するには、<xref:System.Linq.Enumerable.ToList%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="c52cb-104">Use <xref:System.Linq.Enumerable.ToList%2A> to create a generic List from a sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c52cb-105">例</span><span class="sxs-lookup"><span data-stu-id="c52cb-105">Example</span></span>  

 <span data-ttu-id="c52cb-106">次のサンプルでは、<xref:System.Linq.Enumerable.ToList%2A> を使用して、クエリを直ちにジェネリック <xref:System.Collections.Generic.List%601> に評価します。</span><span class="sxs-lookup"><span data-stu-id="c52cb-106">The following sample uses <xref:System.Linq.Enumerable.ToList%2A> to immediately evaluate a query into a generic <xref:System.Collections.Generic.List%601>.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#45](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#45)]
 [!code-vb[DLinqQueryExamples#45](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="c52cb-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="c52cb-107">See also</span></span>

- [<span data-ttu-id="c52cb-108">クエリの例</span><span class="sxs-lookup"><span data-stu-id="c52cb-108">Query Examples</span></span>](query-examples.md)
