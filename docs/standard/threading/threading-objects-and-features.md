---
description: '詳細情報: スレッド処理オブジェクトと機能'
title: スレッド処理オブジェクトと機能
ms.date: 10/01/2018
helpviewer_keywords:
- threading [.NET], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
ms.openlocfilehash: 7e8167c42780ccc70c37a10bbb3a65483efabb24
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675417"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="67872-103">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="67872-103">Threading objects and features</span></span>

<span data-ttu-id="67872-104">.NET では、<xref:System.Threading.Thread?displayProperty=nameWithType> クラスの他に、マルチ スレッド アプリケーションを開発するのに役立つ複数のクラスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="67872-104">Along with the <xref:System.Threading.Thread?displayProperty=nameWithType> class, .NET provides a number of classes that help you develop multithreaded applications.</span></span> <span data-ttu-id="67872-105">次の記事では、それらのクラスの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="67872-105">The following articles provide overview of those classes:</span></span>

|<span data-ttu-id="67872-106">タイトル</span><span class="sxs-lookup"><span data-stu-id="67872-106">Title</span></span>|<span data-ttu-id="67872-107">説明</span><span class="sxs-lookup"><span data-stu-id="67872-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="67872-108">マネージド スレッド プール</span><span class="sxs-lookup"><span data-stu-id="67872-108">The managed thread pool</span></span>](the-managed-thread-pool.md)|<span data-ttu-id="67872-109">.NET によって管理されるワーカー スレッドのプールを提供する <xref:System.Threading.ThreadPool?displayProperty=nameWithType> について説明します。</span><span class="sxs-lookup"><span data-stu-id="67872-109">Describes the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> class, which provides a pool of worker threads that are managed by .NET.</span></span>|  
|[<span data-ttu-id="67872-110">タイマー</span><span class="sxs-lookup"><span data-stu-id="67872-110">Timers</span></span>](timers.md)|<span data-ttu-id="67872-111">マルチスレッド環境で使用できる .NET タイマーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="67872-111">Describes .NET timers that can be used in a multithreaded environment.</span></span>|
|[<span data-ttu-id="67872-112">同期プリミティブの概要</span><span class="sxs-lookup"><span data-stu-id="67872-112">Overview of synchronization primitives</span></span>](overview-of-synchronization-primitives.md)|<span data-ttu-id="67872-113">共有リソースへのアクセスを同期化する場合や、スレッドの相互作用を制御する場合に使用できる型について説明します。</span><span class="sxs-lookup"><span data-stu-id="67872-113">Describes types that can be used to synchronize access to a shared resource or control thread interaction.</span></span>|
|[<span data-ttu-id="67872-114">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="67872-114">EventWaitHandle</span></span>](eventwaithandle.md)|<span data-ttu-id="67872-115">スレッドの同期イベントを表す <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="67872-115">Describes the <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> class, which represents a thread synchronization event.</span></span>|
|[<span data-ttu-id="67872-116">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="67872-116">CountdownEvent</span></span>](countdownevent.md)|<span data-ttu-id="67872-117">そのカウントがゼロのときに設定されるスレッド同期イベントを表す <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="67872-117">Describes the <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> class, which represents a thread synchronization event that becomes set when its count is zero.</span></span>|
|[<span data-ttu-id="67872-118">ミューテックス</span><span class="sxs-lookup"><span data-stu-id="67872-118">Mutexes</span></span>](mutexes.md)|<span data-ttu-id="67872-119">共有リソースへの排他アクセスを付与する <xref:System.Threading.Mutex?displayProperty=nameWithType> クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="67872-119">Describes the <xref:System.Threading.Mutex?displayProperty=nameWithType> class, which grants exclusive access to a shared resource.</span></span>|
|[<span data-ttu-id="67872-120">Semaphore と SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="67872-120">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)|<span data-ttu-id="67872-121">共有リソースまたはリソースのプールに同時にアクセスできるスレッドの数を制限する <xref:System.Threading.Semaphore?displayProperty=nameWithType> について説明します。</span><span class="sxs-lookup"><span data-stu-id="67872-121">Describes the <xref:System.Threading.Semaphore?displayProperty=nameWithType> class, which limits number of threads that can access a shared resource or a pool of resources concurrently.</span></span>|
|[<span data-ttu-id="67872-122">バリア</span><span class="sxs-lookup"><span data-stu-id="67872-122">Barrier</span></span>](barrier.md)|<span data-ttu-id="67872-123">段階的な操作におけるスレッドの調整のためのバリア パターンを実装する <xref:System.Threading.Barrier?displayProperty=nameWithType> クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="67872-123">Describes the <xref:System.Threading.Barrier?displayProperty=nameWithType> class, which implements the barrier pattern for coordination of threads in phased operations.</span></span>|
|[<span data-ttu-id="67872-124">SpinLock</span><span class="sxs-lookup"><span data-stu-id="67872-124">SpinLock</span></span>](spinlock.md)|<span data-ttu-id="67872-125">特定の下位レベルのシナリオで <xref:System.Threading.Monitor?displayProperty=nameWithType> ロックの代わりに軽量クラスとして使用できる <xref:System.Threading.SpinLock?displayProperty=nameWithType> 構造体について説明します。</span><span class="sxs-lookup"><span data-stu-id="67872-125">Describes the <xref:System.Threading.SpinLock?displayProperty=nameWithType> structure, which is a lightweight alternative to the <xref:System.Threading.Monitor?displayProperty=nameWithType> class for certain low-level locking scenarios.</span></span>|
|[<span data-ttu-id="67872-126">SpinWait</span><span class="sxs-lookup"><span data-stu-id="67872-126">SpinWait</span></span>](spinwait.md)|<span data-ttu-id="67872-127">スピンベースの待機のサポートを提供する <xref:System.Threading.SpinWait?displayProperty=nameWithType> 構造体について説明します。</span><span class="sxs-lookup"><span data-stu-id="67872-127">Describes the <xref:System.Threading.SpinWait?displayProperty=nameWithType> structure, which provides support for spin-based waiting.</span></span>|

## <a name="see-also"></a><span data-ttu-id="67872-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="67872-128">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [<span data-ttu-id="67872-129">スレッドの使用とスレッド処理</span><span class="sxs-lookup"><span data-stu-id="67872-129">Using threads and threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="67872-130">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="67872-130">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)
- [<span data-ttu-id="67872-131">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="67872-131">Parallel Programming</span></span>](../parallel-programming/index.md)
- [<span data-ttu-id="67872-132">タスク並列ライブラリ (TPL)</span><span class="sxs-lookup"><span data-stu-id="67872-132">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)
