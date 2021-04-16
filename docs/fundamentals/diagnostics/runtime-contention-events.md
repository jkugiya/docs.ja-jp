---
title: モニターのロック競合ランタイム イベント
description: モニターのロック競合に固有の情報を収集する ETW イベントを参照してください。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- monitor lock contention events (CoreCLR)
- ETW, EventPipe, LTTng contention events (CoreCLR)
ms.openlocfilehash: 38e5f493d4b223b4839dbd6f814cf656722189b2
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594054"
---
# <a name="net-runtime-contention-events"></a>.NET ランタイム競合イベント

これらのランタイム イベントは、`Monitor.Enter` または C# の lock キーワードなど、モニターのロック競合に関する情報をキャプチャします。 診断のためにこれらのイベントを使用する方法の詳細については、[.NET アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)に関するページを参照してください。

## <a name="contentionstart_v1-event"></a>ContentionStart_V1 イベント

このイベントは、モニターのロック競合の開始時に生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|情報提供 (4)|

 次の表にイベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|81|モニターのロック競合が開始します。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|マネージドの場合は `0`、ネイティブの場合は `1` です。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="contentionstop_v1-event"></a>ContentionStop_V1 イベント

このイベントは、モニターのロック競合の終了時に生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|情報提供 (4)|

 次の表にイベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ContentionStop_V1`|91|モニターのロック競合が終了します。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|マネージドの場合は `0`、ネイティブの場合は `1` です。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|
|`DurationNs`|`win:Double`|競合の継続時間 (ナノ秒単位)。|
