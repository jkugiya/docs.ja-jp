---
title: ThreadPool ランタイム イベント
description: .NET Core のスレッド プールに関する診断情報を収集する .NET ランタイム スレッド プール イベントを参照してください。 スレッド プール イベントは、ワーカー スレッド プール イベントまたは I/O スレッド プール イベントです。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- ThreadPool events (CoreCLR)
- ETW, thread pool events (CoreCLR)
ms.openlocfilehash: cdd6041c5842d4922c60e33daf6db366f7d35327
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594121"
---
# <a name="net-runtime-thread-pool-events"></a>.NET ランタイム スレッド プール イベント

これらのイベントは、スレッドプールのワーカー スレッドと I/O スレッドに関する情報を収集します。 診断のためにこれらのイベントを使用する方法の詳細については、[.NET アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)に関するページを参照してください。

## <a name="iothreadcreate_v1-event"></a>IOThreadCreate_V1 イベント

 次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|情報提供 (4)|

 次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------------------------------|-----------|
|`IOThreadCreate_V1`|44|I/O スレッドがスレッド プールに作成された。|

 次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|新しく作成されたスレッドを含む、I/O のスレッドの数です。|
|`NumRetired`|`win:UInt64`|提供終了になったワーカー スレッドの数。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="iothreadterminate_v1-event"></a>IOThreadTerminate_V1 イベント

 次の表に、キーワードとレベルを示します

|イベントを発生させるキーワード|Level
|-----------------------------------|-----------
|`ThreadingKeyword` (0x10000)|情報提供 (4)

 次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`IOThreadTerminate`|45|スレッド プール内の I/O スレッドが終了した。|

 次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|スレッド プールに残っている I/O スレッドの数。|
|`NumRetired`|`win:UInt64`|提供終了になった I/O スレッドの数。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="iothreadretire_v1-event"></a>IOThreadRetire_V1 イベント

 次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|情報提供 (4)|

 次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`IOThreadRetire_V1`|46|I/O スレッドが、提供終了の候補になる。|

 次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|スレッド プールに残っている I/O スレッドの数。|
|`NumRetired`|`win:UInt64`|提供終了になった I/O スレッドの数。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="iothreadunretire_v1-event"></a>IOThreadUnretire_V1 イベント

 次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|情報提供 (4)|

 次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`IOThreadUnretire_V1`|47|スレッドが提供終了の候補になってから待機期間内に I/O が到着したため I/O スレッドが提供終了解除された。|

 次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|これを含む、スレッド プール内の I/O スレッドの数。|
|`NumRetired`|`win:UInt64`|提供終了になった I/O スレッドの数。|
|`ClrInstanceID`|`Win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="threadpoolworkerthreadstart-event"></a>ThreadPoolWorkerThreadStart イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStart`|50|ワーカー スレッドが作成された。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。|
|`RetiredWorkerThreadCount`|`win:UInt32`|作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="threadpoolworkerthreadstop-event"></a>ThreadPoolWorkerThreadStop イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStop`|51|ワーカー スレッドが停止された。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。|
|`RetiredWorkerThreadCount`|`win:UInt32`|作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="threadpoolworkerthreadwait-event"></a>ThreadPoolWorkerThreadWait イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadWait`|57|ワーカー スレッドが作業の待機を開始します。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。|
|`RetiredWorkerThreadCount`|`win:UInt32`|作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="threadpoolworkerthreadretirementstart-event"></a>ThreadPoolWorkerThreadRetirementStart イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStart`|52|ワーカー スレッドが無効にされた。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。|
|`RetiredWorkerThreadCount`|`win:UInt32`|作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="threadpoolworkerthreadretirementstop-event"></a>ThreadPoolWorkerThreadRetirementStop イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|情報提供 (4)|

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStop`|53|提供終了になったワーカー スレッドが再びアクティブになった。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。|
|`RetiredWorkerThreadCount`|`win:UInt32`|作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="threadpoolworkerthreadadjustmentsample-event"></a>ThreadPoolWorkerThreadAdjustmentSample イベント

 次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|情報提供 (4)|

 次の表に、イベント情報を示します。

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentSample`|54|1 つのサンプルの情報のコレクションを参照します。つまり、特定のコンカレンシー レベルの特定の時刻におけるスループットの測定値です。|

 次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`Throughput`|`win:Double`|時間の単位あたりの入力候補の数です。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="threadpoolworkerthreadadjustmentadjustment-event"></a>ThreadPoolWorkerThreadAdjustmentAdjustment イベント

 次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|情報提供 (4)|

 次の表に、イベント情報を示します。

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|55|スレッドの挿入 (山登り法) アルゴリズムが、コンカレンシー レベルに変更があったと判断した場合に、コントロールの変更を記録します。|

 次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`AverageThroughput`|`win:Double`|計測のサンプルの平均のスループット。|
|`NewWorkerThreadCount`|`win:UInt32`|新しいアクティブなワーカー スレッド数。|
|`Reason`|`win:UInt32`|調整の理由。<br /><br /> `0x0` - ウォームアップ。<br /><br /> `0x1` - 初期化中。<br /><br /> `0x2` - ランダムな移動。<br /><br /> `0x3` - 上昇移動。<br /><br /> `0x4` - 変更点。<br /><br /> `0x5` - 安定化。<br /><br /> `0x6` - 不足。<br /><br /> `0x7` - スレッドのタイムアウト。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="threadpoolworkerthreadadjustmentstats-event"></a>ThreadPoolWorkerThreadAdjustmentStats イベント

 次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|詳細 (5)

 次の表に、イベント情報を示します。

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentStats`|56|スレッド プールに関するデータを収集します。|

 次の表に、イベント データを示します

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`Duration`|`win:Double`|これらの統計情報が収集される時間数 (秒)。|
|`Throughput`|`win:Double`|この間隔中の 1 秒あたりの入力候補の平均数。|
|`ThreadWave`|`win:Double`|内部使用のために予約されています。|
|`ThroughputWave`|`win:Double`|内部使用のために予約されています。|
|`ThroughputErrorEstimate`|`win:Double`|内部使用のために予約されています。|
|`AverageThroughputErrorEstimate`|`win:Double`|内部使用のために予約されています。|
|`ThroughputRatio`|`win:Double`|この間隔中にアクティブなワーカー スレッドの数の変動によって引き起こされる、スループットの相対的な向上。|
|`Confidence`|`win:Double`|ThroughputRatio フィールドの有効性の測定結果。|
|`NewcontrolSetting`|`win:Double`|アクティブなスレッド数の将来のバリエーションのベースラインとして使用するアクティブなワーカー スレッドの数。|
|`NewThreadWaveMagnitude`|`win:UInt16`|アクティブなスレッド数の、将来のバリエーションの大きさを指定します。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="threadpoolenqueue-event"></a>ThreadPoolEnqueue イベント

 次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|詳細 (5)

 次の表に、イベント情報を示します。

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ThreadPoolEnqueue`|61|作業項目がスレッド プールキューにエンキューされました。|

 次の表に、イベント データを示します

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|作業要求へのポインター。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="threadpooldequeue-event"></a>ThreadPoolDequeue イベント

 次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|詳細 (5)

 次の表に、イベント情報を示します。

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ThreadPoolDequeue`|62|作業項目がスレッド プール キューからデキューされました。|

 次の表に、イベント データを示します

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|作業要求へのポインター。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="threadpoolioenqueue-event"></a>ThreadPoolIOEnqueue イベント

 次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|詳細 (5)

 次の表に、イベント情報を示します。

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ThreadPoolIOEnqueue`|63|スレッドが非同期 IO 発生後に IO 完了通知をエンキューします。|

 次の表に、イベント データを示します

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|内部使用のために予約されています。|
|`Overlapped`|`win:Pointer`|内部使用のために予約されています。|
|`MultiDequeues`|`win:Boolean`|内部使用のために予約されています。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="threadpooliodequeue-event"></a>ThreadPoolIODequeue イベント

 次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|詳細 (5)

 次の表に、イベント情報を示します。

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ThreadPoolIODequeue`|64|スレッドが IO 完了通知をデキューします。|

 次の表に、イベント データを示します

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|内部使用のために予約されています。|
|`Overlapped`|`win:Pointer`|内部使用のために予約されています。|
|`MultiDequeues`|`win:Boolean`|内部使用のために予約されています。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="threadpooliopack-event"></a>ThreadPoolIOPack イベント

 次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|詳細 (5)|

 次の表に、イベント情報を示します。

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`ThreadPoolIOPack`|65|ThreadPool の重複 IO パックが呼び出されます。|

 次の表に、イベント データを示します

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|内部使用のために予約されています。|
|`Overlapped`|`win:Pointer`|内部使用のために予約されています。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="threadcreating-event"></a>ThreadCreating イベント

 次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|情報提供 (4)|

 次の表に、イベント情報を示します。

|Event|イベント ID|説明|
|----------------|---------------|-----------------|
|`ThreadCreating`|70|スレッドが作成されました。|

 次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|スレッド ID|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="threadrunning-event"></a>ThreadRunning イベント

 次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|情報提供 (4)|

 次の表に、イベント情報を示します。

|Event|イベント ID|説明|
|----------------|---------------|-----------------|
|`ThreadRunning`|71|スレッドが実行を開始しました。|

 次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|スレッド ID|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|
