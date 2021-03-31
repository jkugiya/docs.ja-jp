---
description: '詳細情報: パイプラインでブロッキング コレクションの配列を使用する方法'
title: '方法: パイプラインでブロッキング コレクションの配列を使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
ms.openlocfilehash: 7b8d0da612a7e742c85b1133908b8d54a4f9b0fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99676054"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="29c5b-103">方法: パイプラインでブロッキング コレクションの配列を使用する</span><span class="sxs-lookup"><span data-stu-id="29c5b-103">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>

<span data-ttu-id="29c5b-104">次の例は、<xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> や <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> などの静的メソッドで <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> オブジェクトの配列を使用し、コンポーネント間の高速で柔軟なデータ転送を実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="29c5b-104">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29c5b-105">例</span><span class="sxs-lookup"><span data-stu-id="29c5b-105">Example</span></span>  

 <span data-ttu-id="29c5b-106">次の例では、各オブジェクトが同時にデータを入力コレクションから取得し、変換して、出力コレクションに渡す、基本的なパイプラインの実装を示します。</span><span class="sxs-lookup"><span data-stu-id="29c5b-106">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="29c5b-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="29c5b-107">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="29c5b-108">スレッドセーフなコレクション</span><span class="sxs-lookup"><span data-stu-id="29c5b-108">Thread-Safe Collections</span></span>](index.md)
