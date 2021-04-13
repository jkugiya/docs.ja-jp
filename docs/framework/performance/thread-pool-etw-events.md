---
title: スレッド プール ETW イベント
description: .NET 内のスレッドに関する情報を収集するスレッド プール ETW イベントについて確認します。 スレッド プール イベントは、ワーカー スレッド プール イベントまたは I/O スレッド プール イベントです。
ms.date: 03/30/2017
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
ms.openlocfilehash: 8b00c20e82ee1b1efa6a8a123e66a4cfc239143b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236170"
---
# <a name="thread-pool-etw-events"></a><span data-ttu-id="1ee9a-104">スレッド プール ETW イベント</span><span class="sxs-lookup"><span data-stu-id="1ee9a-104">Thread Pool ETW Events</span></span>

<span data-ttu-id="1ee9a-105">これらのイベントは、ワーカー スレッドと I/O スレッドに関する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-105">These events collect information about worker and I/O threads.</span></span>  
  
 <span data-ttu-id="1ee9a-106">スレッド プール イベントには 2 つのグループがあります。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-106">There are two groups of thread pool events:</span></span>  
  
- <span data-ttu-id="1ee9a-107">[ワーカー スレッド プール イベント](#worker-thread-pool-events)は、アプリケーションがどのようにスレッド プールを使用するかに関する情報と、コンカレンシー制御におけるワークロードの効果に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-107">[Worker thread pool events](#worker-thread-pool-events), which provide information about how an application uses the thread pool, and the effect of workloads on concurrency control.</span></span>  
  
- <span data-ttu-id="1ee9a-108">[I/O スレッド プール イベント](#io-thread-events)は、スレッド プールで作成、無効化、無効化解除、または終了した I/O スレッドに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-108">[I/O thread pool events](#io-thread-events), which provide information about I/O threads that are created, retired, unretired, or terminated in the thread pool.</span></span>  

## <a name="worker-thread-pool-events"></a><span data-ttu-id="1ee9a-109">ワーカー スレッド プール イベント</span><span class="sxs-lookup"><span data-stu-id="1ee9a-109">Worker Thread Pool Events</span></span>

 <span data-ttu-id="1ee9a-110">これらのイベントは、ランタイムのワーカー スレッドのプールに関連付けられており、スレッド イベントに関する通知 (スレッドが作成されたり停止されたりした場合など) を提供します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-110">These events relate to the runtime's worker thread pool and provide notifications for thread events (for example, when a thread is created or stopped).</span></span> <span data-ttu-id="1ee9a-111">ワーカー スレッド プールは、スレッドの数が計測されたスループットに基づいて計算されるアダプティブ アルゴリズムを使用して、コンカレンシー制御を実行します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-111">The worker thread pool uses an adaptive algorithm for concurrency control, where the number of threads is calculated based on the measured throughput.</span></span> <span data-ttu-id="1ee9a-112">ワーカー スレッド プール イベントを使用すると、アプリケーションで使用されるスレッド プールの様子や特定のワークロードがコンカレンシー制御に与える影響などを理解することができます。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-112">Worker thread pool events can be used to understand how an application is using the thread pool, and the effect that certain workloads may have on concurrency control.</span></span>  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a><span data-ttu-id="1ee9a-113">ThreadPoolWorkerThreadStart および ThreadPoolWorkerThreadStop</span><span class="sxs-lookup"><span data-stu-id="1ee9a-113">ThreadPoolWorkerThreadStart and ThreadPoolWorkerThreadStop</span></span>  

 <span data-ttu-id="1ee9a-114">次の表に、これらのイベントのキーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-114">The following table shows the keyword and level for these events.</span></span> <span data-ttu-id="1ee9a-115">(詳細については、「 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-115">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="1ee9a-116">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="1ee9a-116">Keyword for raising the event</span></span>|<span data-ttu-id="1ee9a-117">レベル</span><span class="sxs-lookup"><span data-stu-id="1ee9a-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="1ee9a-118">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1ee9a-118">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1ee9a-119">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="1ee9a-119">Informational (4)</span></span>|  
  
 <span data-ttu-id="1ee9a-120">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-120">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="1ee9a-121">イベント</span><span class="sxs-lookup"><span data-stu-id="1ee9a-121">Event</span></span>|<span data-ttu-id="1ee9a-122">イベント ID</span><span class="sxs-lookup"><span data-stu-id="1ee9a-122">Event ID</span></span>|<span data-ttu-id="1ee9a-123">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="1ee9a-123">Raised when</span></span>|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="1ee9a-124">50</span><span class="sxs-lookup"><span data-stu-id="1ee9a-124">50</span></span>|<span data-ttu-id="1ee9a-125">ワーカー スレッドが作成された。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-125">A worker thread is created.</span></span>|  
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="1ee9a-126">51</span><span class="sxs-lookup"><span data-stu-id="1ee9a-126">51</span></span>|<span data-ttu-id="1ee9a-127">ワーカー スレッドが停止された。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-127">A worker thread is stopped.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="1ee9a-128">52</span><span class="sxs-lookup"><span data-stu-id="1ee9a-128">52</span></span>|<span data-ttu-id="1ee9a-129">ワーカー スレッドが無効にされた。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-129">A worker thread retires.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="1ee9a-130">53</span><span class="sxs-lookup"><span data-stu-id="1ee9a-130">53</span></span>|<span data-ttu-id="1ee9a-131">提供終了になったワーカー スレッドが再びアクティブになった。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-131">A retired worker thread becomes active again.</span></span>|  
  
 <span data-ttu-id="1ee9a-132">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-132">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="1ee9a-133">フィールド名</span><span class="sxs-lookup"><span data-stu-id="1ee9a-133">Field name</span></span>|<span data-ttu-id="1ee9a-134">データ型</span><span class="sxs-lookup"><span data-stu-id="1ee9a-134">Data type</span></span>|<span data-ttu-id="1ee9a-135">説明</span><span class="sxs-lookup"><span data-stu-id="1ee9a-135">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="1ee9a-136">ActiveWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="1ee9a-136">ActiveWorkerThreadCount</span></span>|<span data-ttu-id="1ee9a-137">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="1ee9a-137">win:UInt32</span></span>|<span data-ttu-id="1ee9a-138">作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-138">Number of worker threads available to process work, including those that are already processing work.</span></span>|  
|<span data-ttu-id="1ee9a-139">RetiredWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="1ee9a-139">RetiredWorkerThreadCount</span></span>|<span data-ttu-id="1ee9a-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="1ee9a-140">win:UInt32</span></span>|<span data-ttu-id="1ee9a-141">作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-141">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|  
|<span data-ttu-id="1ee9a-142">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1ee9a-142">ClrInstanceID</span></span>|<span data-ttu-id="1ee9a-143">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="1ee9a-143">Win:UInt16</span></span>|<span data-ttu-id="1ee9a-144">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="threadpoolworkerthreadadjustment"></a><span data-ttu-id="1ee9a-145">ThreadPoolWorkerThreadAdjustment</span><span class="sxs-lookup"><span data-stu-id="1ee9a-145">ThreadPoolWorkerThreadAdjustment</span></span>  

 <span data-ttu-id="1ee9a-146">これらのスレッド プール イベントは、スレッドの挿入 (コンカレンシー制御) アルゴリズムの動作を理解したりデバッグしたりするための情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-146">These thread pool events provide information for understanding and debugging the behavior of the thread injection (concurrency control) algorithm.</span></span> <span data-ttu-id="1ee9a-147">この情報は、ワーカー スレッド プールによって内部で使用されます。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-147">The information is used internally by the worker thread pool.</span></span>  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a><span data-ttu-id="1ee9a-148">ThreadPoolWorkerThreadAdjustmentSample</span><span class="sxs-lookup"><span data-stu-id="1ee9a-148">ThreadPoolWorkerThreadAdjustmentSample</span></span>  

 <span data-ttu-id="1ee9a-149">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-149">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="1ee9a-150">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="1ee9a-150">Keyword for raising the event</span></span>|<span data-ttu-id="1ee9a-151">レベル</span><span class="sxs-lookup"><span data-stu-id="1ee9a-151">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="1ee9a-152">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1ee9a-152">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1ee9a-153">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="1ee9a-153">Informational (4)</span></span>|  
  
 <span data-ttu-id="1ee9a-154">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-154">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="1ee9a-155">イベント</span><span class="sxs-lookup"><span data-stu-id="1ee9a-155">Event</span></span>|<span data-ttu-id="1ee9a-156">イベント ID</span><span class="sxs-lookup"><span data-stu-id="1ee9a-156">Event ID</span></span>|<span data-ttu-id="1ee9a-157">説明</span><span class="sxs-lookup"><span data-stu-id="1ee9a-157">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="1ee9a-158">54</span><span class="sxs-lookup"><span data-stu-id="1ee9a-158">54</span></span>|<span data-ttu-id="1ee9a-159">1 つのサンプルの情報のコレクションを参照します。つまり、特定のコンカレンシー レベルの特定の時刻におけるスループットの測定値です。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-159">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|  
  
 <span data-ttu-id="1ee9a-160">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-160">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="1ee9a-161">フィールド名</span><span class="sxs-lookup"><span data-stu-id="1ee9a-161">Field name</span></span>|<span data-ttu-id="1ee9a-162">データ型</span><span class="sxs-lookup"><span data-stu-id="1ee9a-162">Data type</span></span>|<span data-ttu-id="1ee9a-163">説明</span><span class="sxs-lookup"><span data-stu-id="1ee9a-163">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="1ee9a-164">スループット</span><span class="sxs-lookup"><span data-stu-id="1ee9a-164">Throughput</span></span>|<span data-ttu-id="1ee9a-165">win:Double</span><span class="sxs-lookup"><span data-stu-id="1ee9a-165">win:Double</span></span>|<span data-ttu-id="1ee9a-166">時間の単位あたりの入力候補の数です。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-166">Number of completions per unit of time.</span></span>|  
|<span data-ttu-id="1ee9a-167">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1ee9a-167">ClrInstanceID</span></span>|<span data-ttu-id="1ee9a-168">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="1ee9a-168">Win:UInt16</span></span>|<span data-ttu-id="1ee9a-169">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-169">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a><span data-ttu-id="1ee9a-170">ThreadPoolWorkerThreadAdjustmentAdjustment</span><span class="sxs-lookup"><span data-stu-id="1ee9a-170">ThreadPoolWorkerThreadAdjustmentAdjustment</span></span>  

 <span data-ttu-id="1ee9a-171">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-171">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="1ee9a-172">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="1ee9a-172">Keyword for raising the event</span></span>|<span data-ttu-id="1ee9a-173">レベル</span><span class="sxs-lookup"><span data-stu-id="1ee9a-173">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="1ee9a-174">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1ee9a-174">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1ee9a-175">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="1ee9a-175">Informational (4)</span></span>|  
  
 <span data-ttu-id="1ee9a-176">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-176">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="1ee9a-177">イベント</span><span class="sxs-lookup"><span data-stu-id="1ee9a-177">Event</span></span>|<span data-ttu-id="1ee9a-178">イベント ID</span><span class="sxs-lookup"><span data-stu-id="1ee9a-178">Event ID</span></span>|<span data-ttu-id="1ee9a-179">説明</span><span class="sxs-lookup"><span data-stu-id="1ee9a-179">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="1ee9a-180">55</span><span class="sxs-lookup"><span data-stu-id="1ee9a-180">55</span></span>|<span data-ttu-id="1ee9a-181">スレッドの挿入 (山登り法) アルゴリズムが、コンカレンシー レベルに変更があったと判断した場合に、コントロールの変更を記録します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-181">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|  
  
 <span data-ttu-id="1ee9a-182">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-182">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="1ee9a-183">フィールド名</span><span class="sxs-lookup"><span data-stu-id="1ee9a-183">Field name</span></span>|<span data-ttu-id="1ee9a-184">データ型</span><span class="sxs-lookup"><span data-stu-id="1ee9a-184">Data type</span></span>|<span data-ttu-id="1ee9a-185">説明</span><span class="sxs-lookup"><span data-stu-id="1ee9a-185">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="1ee9a-186">AverageThroughput</span><span class="sxs-lookup"><span data-stu-id="1ee9a-186">AverageThroughput</span></span>|<span data-ttu-id="1ee9a-187">win:Double</span><span class="sxs-lookup"><span data-stu-id="1ee9a-187">win:Double</span></span>|<span data-ttu-id="1ee9a-188">計測のサンプルの平均のスループット。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-188">Average throughput of a sample of measurements.</span></span>|  
|<span data-ttu-id="1ee9a-189">NewWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="1ee9a-189">NewWorkerThreadCount</span></span>|<span data-ttu-id="1ee9a-190">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="1ee9a-190">win:UInt32</span></span>|<span data-ttu-id="1ee9a-191">新しいアクティブなワーカー スレッド数。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-191">New number of active worker threads.</span></span>|  
|<span data-ttu-id="1ee9a-192">理由</span><span class="sxs-lookup"><span data-stu-id="1ee9a-192">Reason</span></span>|<span data-ttu-id="1ee9a-193">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="1ee9a-193">win:UInt32</span></span>|<span data-ttu-id="1ee9a-194">調整の理由。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-194">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="1ee9a-195">0x00 - ウォーム アップ。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-195">0x00 - Warmup.</span></span><br /><br /> <span data-ttu-id="1ee9a-196">0x01 - 初期化。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-196">0x01 - Initializing.</span></span><br /><br /> <span data-ttu-id="1ee9a-197">0x02 - ランダムな移動。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-197">0x02 - Random move.</span></span><br /><br /> <span data-ttu-id="1ee9a-198">0x03 - 上昇移動。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-198">0x03 - Climbing move.</span></span><br /><br /> <span data-ttu-id="1ee9a-199">0x04 - 変更点。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-199">0x04 - Change point.</span></span><br /><br /> <span data-ttu-id="1ee9a-200">0x05 - 安定化。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-200">0x05 - Stabilizing.</span></span><br /><br /> <span data-ttu-id="1ee9a-201">0x06 - 不足。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-201">0x06 - Starvation.</span></span><br /><br /> <span data-ttu-id="1ee9a-202">0x07 - スレッドのタイムアウト。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-202">0x07 - Thread timed out.</span></span>|  
|<span data-ttu-id="1ee9a-203">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1ee9a-203">ClrInstanceID</span></span>|<span data-ttu-id="1ee9a-204">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="1ee9a-204">Win:UInt16</span></span>|<span data-ttu-id="1ee9a-205">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-205">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a><span data-ttu-id="1ee9a-206">ThreadPoolWorkerThreadAdjustmentStats</span><span class="sxs-lookup"><span data-stu-id="1ee9a-206">ThreadPoolWorkerThreadAdjustmentStats</span></span>  

 <span data-ttu-id="1ee9a-207">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-207">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="1ee9a-208">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="1ee9a-208">Keyword for raising the event</span></span>|<span data-ttu-id="1ee9a-209">レベル</span><span class="sxs-lookup"><span data-stu-id="1ee9a-209">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="1ee9a-210">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1ee9a-210">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1ee9a-211">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="1ee9a-211">Informational (4)</span></span>|  
  
 <span data-ttu-id="1ee9a-212">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-212">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="1ee9a-213">イベント</span><span class="sxs-lookup"><span data-stu-id="1ee9a-213">Event</span></span>|<span data-ttu-id="1ee9a-214">イベント ID</span><span class="sxs-lookup"><span data-stu-id="1ee9a-214">Event ID</span></span>|<span data-ttu-id="1ee9a-215">説明</span><span class="sxs-lookup"><span data-stu-id="1ee9a-215">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="1ee9a-216">56</span><span class="sxs-lookup"><span data-stu-id="1ee9a-216">56</span></span>|<span data-ttu-id="1ee9a-217">スレッド プールに関するデータを収集します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-217">Gathers data on the thread pool.</span></span>|  
  
 <span data-ttu-id="1ee9a-218">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-218">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="1ee9a-219">フィールド名</span><span class="sxs-lookup"><span data-stu-id="1ee9a-219">Field name</span></span>|<span data-ttu-id="1ee9a-220">データ型</span><span class="sxs-lookup"><span data-stu-id="1ee9a-220">Data type</span></span>|<span data-ttu-id="1ee9a-221">説明</span><span class="sxs-lookup"><span data-stu-id="1ee9a-221">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="1ee9a-222">Duration</span><span class="sxs-lookup"><span data-stu-id="1ee9a-222">Duration</span></span>|<span data-ttu-id="1ee9a-223">win:Double</span><span class="sxs-lookup"><span data-stu-id="1ee9a-223">win:Double</span></span>|<span data-ttu-id="1ee9a-224">これらの統計情報が収集される時間数 (秒)。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-224">Amount of time, in seconds, during which these statistics were collected.</span></span>|  
|<span data-ttu-id="1ee9a-225">スループット</span><span class="sxs-lookup"><span data-stu-id="1ee9a-225">Throughput</span></span>|<span data-ttu-id="1ee9a-226">win:Double</span><span class="sxs-lookup"><span data-stu-id="1ee9a-226">win:Double</span></span>|<span data-ttu-id="1ee9a-227">この間隔中の 1 秒あたりの入力候補の平均数。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-227">Average number of completions per second during this interval.</span></span>|  
|<span data-ttu-id="1ee9a-228">ThreadWave</span><span class="sxs-lookup"><span data-stu-id="1ee9a-228">ThreadWave</span></span>|<span data-ttu-id="1ee9a-229">win:Double</span><span class="sxs-lookup"><span data-stu-id="1ee9a-229">win:Double</span></span>|<span data-ttu-id="1ee9a-230">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-230">Reserved for internal use.</span></span>|  
|<span data-ttu-id="1ee9a-231">ThroughputWave</span><span class="sxs-lookup"><span data-stu-id="1ee9a-231">ThroughputWave</span></span>|<span data-ttu-id="1ee9a-232">win:Double</span><span class="sxs-lookup"><span data-stu-id="1ee9a-232">win:Double</span></span>|<span data-ttu-id="1ee9a-233">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-233">Reserved for internal use.</span></span>|  
|<span data-ttu-id="1ee9a-234">ThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="1ee9a-234">ThroughputErrorEstimate</span></span>|<span data-ttu-id="1ee9a-235">win:Double</span><span class="sxs-lookup"><span data-stu-id="1ee9a-235">win:Double</span></span>|<span data-ttu-id="1ee9a-236">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-236">Reserved for internal use.</span></span>|  
|<span data-ttu-id="1ee9a-237">AverageThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="1ee9a-237">AverageThroughputErrorEstimate</span></span>|<span data-ttu-id="1ee9a-238">win:Double</span><span class="sxs-lookup"><span data-stu-id="1ee9a-238">win:Double</span></span>|<span data-ttu-id="1ee9a-239">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-239">Reserved for internal use.</span></span>|  
|<span data-ttu-id="1ee9a-240">ThroughputRatio</span><span class="sxs-lookup"><span data-stu-id="1ee9a-240">ThroughputRatio</span></span>|<span data-ttu-id="1ee9a-241">win:Double</span><span class="sxs-lookup"><span data-stu-id="1ee9a-241">win:Double</span></span>|<span data-ttu-id="1ee9a-242">この間隔中にアクティブなワーカー スレッドの数の変動によって引き起こされる、スループットの相対的な向上。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-242">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|  
|<span data-ttu-id="1ee9a-243">Confidence</span><span class="sxs-lookup"><span data-stu-id="1ee9a-243">Confidence</span></span>|<span data-ttu-id="1ee9a-244">win:Double</span><span class="sxs-lookup"><span data-stu-id="1ee9a-244">win:Double</span></span>|<span data-ttu-id="1ee9a-245">ThroughputRatio フィールドの有効性の測定結果。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-245">A measure of the validity of the ThroughputRatio field.</span></span>|  
|<span data-ttu-id="1ee9a-246">NewcontrolSetting</span><span class="sxs-lookup"><span data-stu-id="1ee9a-246">NewcontrolSetting</span></span>|<span data-ttu-id="1ee9a-247">win:Double</span><span class="sxs-lookup"><span data-stu-id="1ee9a-247">win:Double</span></span>|<span data-ttu-id="1ee9a-248">アクティブなスレッド数の将来のバリエーションのベースラインとして使用するアクティブなワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-248">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|  
|<span data-ttu-id="1ee9a-249">NewThreadWaveMagnitude</span><span class="sxs-lookup"><span data-stu-id="1ee9a-249">NewThreadWaveMagnitude</span></span>|<span data-ttu-id="1ee9a-250">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="1ee9a-250">Win:UInt16</span></span>|<span data-ttu-id="1ee9a-251">アクティブなスレッド数の、将来のバリエーションの大きさを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-251">The magnitude of future variations in active thread count.</span></span>|  
|<span data-ttu-id="1ee9a-252">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1ee9a-252">ClrInstanceID</span></span>|<span data-ttu-id="1ee9a-253">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="1ee9a-253">Win:UInt16</span></span>|<span data-ttu-id="1ee9a-254">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-254">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="io-thread-events"></a><span data-ttu-id="1ee9a-255">I/O スレッド イベント</span><span class="sxs-lookup"><span data-stu-id="1ee9a-255">I/O Thread Events</span></span>  

 <span data-ttu-id="1ee9a-256">これらのスレッド プール イベントは、I/O スレッド プール (完了ポート) にあるスレッドで発生します。これは非同期です。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-256">These thread pool events occur for threads in the I/O thread pool (completion ports), which is asynchronous.</span></span>  
  
### <a name="iothreadcreate_v1"></a><span data-ttu-id="1ee9a-257">IOThreadCreate_V1</span><span class="sxs-lookup"><span data-stu-id="1ee9a-257">IOThreadCreate_V1</span></span>  

 <span data-ttu-id="1ee9a-258">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-258">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="1ee9a-259">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="1ee9a-259">Keyword for raising the event</span></span>|<span data-ttu-id="1ee9a-260">レベル</span><span class="sxs-lookup"><span data-stu-id="1ee9a-260">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="1ee9a-261">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1ee9a-261">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1ee9a-262">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="1ee9a-262">Informational (4)</span></span>|  
  
 <span data-ttu-id="1ee9a-263">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-263">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="1ee9a-264">イベント</span><span class="sxs-lookup"><span data-stu-id="1ee9a-264">Event</span></span>|<span data-ttu-id="1ee9a-265">イベント ID</span><span class="sxs-lookup"><span data-stu-id="1ee9a-265">Event ID</span></span>|<span data-ttu-id="1ee9a-266">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="1ee9a-266">Raised when</span></span>|  
|-|-|-|  
|`IOThreadCreate_V1`|<span data-ttu-id="1ee9a-267">44</span><span class="sxs-lookup"><span data-stu-id="1ee9a-267">44</span></span>|<span data-ttu-id="1ee9a-268">I/O スレッドがスレッド プールに作成された。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-268">An I/O thread is created in the thread pool.</span></span>|  
  
 <span data-ttu-id="1ee9a-269">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-269">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="1ee9a-270">フィールド名</span><span class="sxs-lookup"><span data-stu-id="1ee9a-270">Field name</span></span>|<span data-ttu-id="1ee9a-271">データ型</span><span class="sxs-lookup"><span data-stu-id="1ee9a-271">Data type</span></span>|<span data-ttu-id="1ee9a-272">説明</span><span class="sxs-lookup"><span data-stu-id="1ee9a-272">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="1ee9a-273">Count</span><span class="sxs-lookup"><span data-stu-id="1ee9a-273">Count</span></span>|<span data-ttu-id="1ee9a-274">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="1ee9a-274">win:UInt64</span></span>|<span data-ttu-id="1ee9a-275">新しく作成されたスレッドを含む、I/O のスレッドの数です。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-275">Number of I/O threads, including the newly created thread.</span></span>|  
|<span data-ttu-id="1ee9a-276">NumRetired</span><span class="sxs-lookup"><span data-stu-id="1ee9a-276">NumRetired</span></span>|<span data-ttu-id="1ee9a-277">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="1ee9a-277">win:UInt64</span></span>|<span data-ttu-id="1ee9a-278">提供終了になったワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-278">Number of retired worker threads.</span></span>|  
|<span data-ttu-id="1ee9a-279">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1ee9a-279">ClrInstanceID</span></span>|<span data-ttu-id="1ee9a-280">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="1ee9a-280">Win:UInt16</span></span>|<span data-ttu-id="1ee9a-281">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-281">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadretire_v1"></a><span data-ttu-id="1ee9a-282">IOThreadRetire_V1</span><span class="sxs-lookup"><span data-stu-id="1ee9a-282">IOThreadRetire_V1</span></span>  

 <span data-ttu-id="1ee9a-283">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="1ee9a-284">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="1ee9a-284">Keyword for raising the event</span></span>|<span data-ttu-id="1ee9a-285">レベル</span><span class="sxs-lookup"><span data-stu-id="1ee9a-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="1ee9a-286">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1ee9a-286">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1ee9a-287">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="1ee9a-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="1ee9a-288">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="1ee9a-289">イベント</span><span class="sxs-lookup"><span data-stu-id="1ee9a-289">Event</span></span>|<span data-ttu-id="1ee9a-290">イベント ID</span><span class="sxs-lookup"><span data-stu-id="1ee9a-290">Event ID</span></span>|<span data-ttu-id="1ee9a-291">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="1ee9a-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|<span data-ttu-id="1ee9a-292">46</span><span class="sxs-lookup"><span data-stu-id="1ee9a-292">46</span></span>|<span data-ttu-id="1ee9a-293">I/O スレッドが、提供終了の候補になる。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-293">An I/O thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="1ee9a-294">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="1ee9a-295">フィールド名</span><span class="sxs-lookup"><span data-stu-id="1ee9a-295">Field name</span></span>|<span data-ttu-id="1ee9a-296">データ型</span><span class="sxs-lookup"><span data-stu-id="1ee9a-296">Data type</span></span>|<span data-ttu-id="1ee9a-297">説明</span><span class="sxs-lookup"><span data-stu-id="1ee9a-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="1ee9a-298">Count</span><span class="sxs-lookup"><span data-stu-id="1ee9a-298">Count</span></span>|<span data-ttu-id="1ee9a-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="1ee9a-299">win:UInt64</span></span>|<span data-ttu-id="1ee9a-300">スレッド プールに残っている I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-300">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="1ee9a-301">NumRetired</span><span class="sxs-lookup"><span data-stu-id="1ee9a-301">NumRetired</span></span>|<span data-ttu-id="1ee9a-302">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="1ee9a-302">win:UInt64</span></span>|<span data-ttu-id="1ee9a-303">提供終了になった I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-303">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="1ee9a-304">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1ee9a-304">ClrInstanceID</span></span>|<span data-ttu-id="1ee9a-305">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="1ee9a-305">Win:UInt16</span></span>|<span data-ttu-id="1ee9a-306">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-306">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadunretire_v1"></a><span data-ttu-id="1ee9a-307">IOThreadUnretire_V1</span><span class="sxs-lookup"><span data-stu-id="1ee9a-307">IOThreadUnretire_V1</span></span>  

 <span data-ttu-id="1ee9a-308">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-308">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="1ee9a-309">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="1ee9a-309">Keyword for raising the event</span></span>|<span data-ttu-id="1ee9a-310">レベル</span><span class="sxs-lookup"><span data-stu-id="1ee9a-310">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="1ee9a-311">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1ee9a-311">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1ee9a-312">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="1ee9a-312">Informational (4)</span></span>|  
  
 <span data-ttu-id="1ee9a-313">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-313">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="1ee9a-314">イベント</span><span class="sxs-lookup"><span data-stu-id="1ee9a-314">Event</span></span>|<span data-ttu-id="1ee9a-315">イベント ID</span><span class="sxs-lookup"><span data-stu-id="1ee9a-315">Event ID</span></span>|<span data-ttu-id="1ee9a-316">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="1ee9a-316">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|<span data-ttu-id="1ee9a-317">47</span><span class="sxs-lookup"><span data-stu-id="1ee9a-317">47</span></span>|<span data-ttu-id="1ee9a-318">スレッドが提供終了の候補になってから待機期間内に I/O が到着したため I/O スレッドが提供終了解除された。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-318">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="1ee9a-319">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-319">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="1ee9a-320">フィールド名</span><span class="sxs-lookup"><span data-stu-id="1ee9a-320">Field name</span></span>|<span data-ttu-id="1ee9a-321">データ型</span><span class="sxs-lookup"><span data-stu-id="1ee9a-321">Data type</span></span>|<span data-ttu-id="1ee9a-322">説明</span><span class="sxs-lookup"><span data-stu-id="1ee9a-322">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="1ee9a-323">Count</span><span class="sxs-lookup"><span data-stu-id="1ee9a-323">Count</span></span>|<span data-ttu-id="1ee9a-324">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="1ee9a-324">win:UInt64</span></span>|<span data-ttu-id="1ee9a-325">これを含む、スレッド プール内の I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-325">Number of I/O threads in the thread pool, including this one.</span></span>|  
|<span data-ttu-id="1ee9a-326">NumRetired</span><span class="sxs-lookup"><span data-stu-id="1ee9a-326">NumRetired</span></span>|<span data-ttu-id="1ee9a-327">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="1ee9a-327">win:UInt64</span></span>|<span data-ttu-id="1ee9a-328">提供終了になった I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-328">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="1ee9a-329">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1ee9a-329">ClrInstanceID</span></span>|<span data-ttu-id="1ee9a-330">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="1ee9a-330">Win:UInt16</span></span>|<span data-ttu-id="1ee9a-331">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-331">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadterminate"></a><span data-ttu-id="1ee9a-332">IOThreadTerminate</span><span class="sxs-lookup"><span data-stu-id="1ee9a-332">IOThreadTerminate</span></span>  

 <span data-ttu-id="1ee9a-333">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-333">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="1ee9a-334">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="1ee9a-334">Keyword for raising the event</span></span>|<span data-ttu-id="1ee9a-335">レベル</span><span class="sxs-lookup"><span data-stu-id="1ee9a-335">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="1ee9a-336">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1ee9a-336">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1ee9a-337">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="1ee9a-337">Informational (4)</span></span>|  
  
 <span data-ttu-id="1ee9a-338">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-338">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="1ee9a-339">イベント</span><span class="sxs-lookup"><span data-stu-id="1ee9a-339">Event</span></span>|<span data-ttu-id="1ee9a-340">イベント ID</span><span class="sxs-lookup"><span data-stu-id="1ee9a-340">Event ID</span></span>|<span data-ttu-id="1ee9a-341">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="1ee9a-341">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|<span data-ttu-id="1ee9a-342">45</span><span class="sxs-lookup"><span data-stu-id="1ee9a-342">45</span></span>|<span data-ttu-id="1ee9a-343">スレッド プール内の I/O スレッドが終了した。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-343">An I/O thread is terminated in the thread pool.</span></span>|  
  
 <span data-ttu-id="1ee9a-344">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-344">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="1ee9a-345">フィールド名</span><span class="sxs-lookup"><span data-stu-id="1ee9a-345">Field name</span></span>|<span data-ttu-id="1ee9a-346">データ型</span><span class="sxs-lookup"><span data-stu-id="1ee9a-346">Data type</span></span>|<span data-ttu-id="1ee9a-347">説明</span><span class="sxs-lookup"><span data-stu-id="1ee9a-347">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="1ee9a-348">Count</span><span class="sxs-lookup"><span data-stu-id="1ee9a-348">Count</span></span>|<span data-ttu-id="1ee9a-349">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="1ee9a-349">win:UInt64</span></span>|<span data-ttu-id="1ee9a-350">スレッド プールに残っている I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-350">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="1ee9a-351">NumRetired</span><span class="sxs-lookup"><span data-stu-id="1ee9a-351">NumRetired</span></span>|<span data-ttu-id="1ee9a-352">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="1ee9a-352">win:UInt64</span></span>|<span data-ttu-id="1ee9a-353">提供終了になった I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-353">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="1ee9a-354">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1ee9a-354">ClrInstanceID</span></span>|<span data-ttu-id="1ee9a-355">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="1ee9a-355">Win:UInt16</span></span>|<span data-ttu-id="1ee9a-356">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="1ee9a-356">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ee9a-357">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ee9a-357">See also</span></span>

- [<span data-ttu-id="1ee9a-358">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="1ee9a-358">CLR ETW Events</span></span>](clr-etw-events.md)
