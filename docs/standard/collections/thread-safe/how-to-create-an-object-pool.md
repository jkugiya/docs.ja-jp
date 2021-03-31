---
description: '詳細情報: ConcurrentBag を使用したオブジェクト プールの作成'
title: ConcurrentBag を使用してオブジェクト プールを作成する
ms.date: 05/01/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
ms.openlocfilehash: c14f77fcedaab8e7e1ac09eb065d1a8d0198e127
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99676041"
---
# <a name="create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="1d0eb-103">ConcurrentBag を使用してオブジェクト プールを作成する</span><span class="sxs-lookup"><span data-stu-id="1d0eb-103">Create an object pool by using a ConcurrentBag</span></span>

<span data-ttu-id="1d0eb-104">この例では、<xref:System.Collections.Concurrent.ConcurrentBag%601> を使用してオブジェクト プールを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-104">This example shows how to use a <xref:System.Collections.Concurrent.ConcurrentBag%601> to implement an object pool.</span></span> <span data-ttu-id="1d0eb-105">オブジェクト プールは、クラスの複数のインスタンスが必要であり、クラスの作成または破棄に大きなコストがかかる状況で、アプリケーションのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-105">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="1d0eb-106">クライアント プログラムが新しいオブジェクトを要求すると、オブジェクト プールは最初に既に作成されてプールに返されているオブジェクトを提供しようとします。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-106">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="1d0eb-107">使用できるオブジェクトがない場合にのみ、新しいオブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-107">If none is available, only then is a new object created.</span></span>

<span data-ttu-id="1d0eb-108"><xref:System.Collections.Concurrent.ConcurrentBag%601> は、高速での挿入と削除をサポートしており、同じスレッドが項目の追加と削除の両方を行うときは特に高速であるため、オブジェクトの格納に使用されます。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-108">The <xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="1d0eb-109">この例は、<xref:System.Collections.Concurrent.IProducerConsumerCollection%601> を中心に構築するようにさらに拡張できます。これは、<xref:System.Collections.Concurrent.ConcurrentQueue%601> や <xref:System.Collections.Concurrent.ConcurrentStack%601> と同じようにバッグ データの構造を実装します。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-109">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

> [!TIP]
> <span data-ttu-id="1d0eb-110">この記事では、オブジェクトを再利用できるよう格納しておくために、基になる同時実行型と共に、独自の実装のオブジェクト プールのを作成する方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-110">This article defines how to write your own implementation of an object pool with an underlying concurrent type to store objects for reuse.</span></span> <span data-ttu-id="1d0eb-111">ただし、<xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType> 型は <xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName> 名前空間に既に存在します。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-111">However, the <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType> type already exists under the <xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="1d0eb-112">実装をご自分で作成する前に、多くの追加機能がある、利用可能な型を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="1d0eb-112">Consider using the available type before creating your own implementation, which includes many additional features.</span></span>

## <a name="example"></a><span data-ttu-id="1d0eb-113">例</span><span class="sxs-lookup"><span data-stu-id="1d0eb-113">Example</span></span>

[!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
[!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]

## <a name="see-also"></a><span data-ttu-id="1d0eb-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d0eb-114">See also</span></span>

- [<span data-ttu-id="1d0eb-115">スレッドセーフなコレクション</span><span class="sxs-lookup"><span data-stu-id="1d0eb-115">Thread-Safe Collections</span></span>](index.md)
