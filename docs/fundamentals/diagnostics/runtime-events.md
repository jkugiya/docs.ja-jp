---
title: ランタイム イベント
description: ETW、LTTng、または EventPipe で使用できる .NET ランタイム (CoreCLR) によって生成される診断イベントを確認します。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- runtime events (CoreCLR)
- ETW, EventPipe runtime events (CoreCLR)
ms.openlocfilehash: 33fa7275ce40934ce043b4d0dba5749c37515755
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594049"
---
# <a name="net-runtime-events"></a>.NET ランタイム イベント

.NET ランタイム (CoreCLR) は、`ETW`、`LTTng`、`EventPipe` などのさまざまなメカニズムで使用できる .NET アプリケーションの問題を診断するために使用できるさまざまなイベントを生成します。

このドキュメントは、.NET Core ランタイムで発生するイベントの参考ガイドです。

.NET Framework のランタイム イベントについては、「[CLR ETW イベント](../../framework/performance/clr-etw-events.md)」を参照してください。

## <a name="in-this-section"></a>このセクションの内容

[競合イベント](runtime-contention-events.md)\
これらのイベントは、モニターのロック競合に関する情報を収集します。

[ガベージ コレクション イベント](runtime-garbage-collection-events.md)\
これらのイベントは、ガベージ コレクションに関連する情報を収集します。 ガベージ コレクションが実行された回数、ガベージ コレクションの間に解放されたメモリの量など、診断やデバッグに役立つ情報を入手できます。

[例外イベント](runtime-exception-events.md)\
これらのランタイム イベントは、スローされる例外に関する情報をキャプチャします。

[相互運用イベント](runtime-interop-events.md)\
これらのランタイム イベントは、共通中間言語 (CIL) のスタブ生成に関する情報をキャプチャします。

[ローダーおよびバインダー イベント](runtime-loader-binder-events.md)\
これらのイベントは、アセンブリ、およびモジュールのロードとアンロードに関連する情報を収集します。

[メソッド イベント](runtime-method-events.md)\
これらのイベントは、メソッド固有の情報を収集します。 これらのイベントのペイロードは、シンボルの解決に必要です。 さらに、これらのイベントは、メソッドが呼び出された回数などの有用な情報を提供します。

[スレッド イベント](runtime-thread-events.md)\
これらのイベントは、ワーカー スレッドと I/O スレッドに関する情報を収集します。

[型イベント](runtime-type-events.md)\
これらのイベントは、型システムに関する情報を収集します。
