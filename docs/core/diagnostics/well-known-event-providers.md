---
title: .NET の既知のイベント プロバイダー
description: .NET ランタイムおよびライブラリによって公開されているプロバイダーとイベントを確認します。
ms.topic: reference
ms.date: 12/21/2020
ms.openlocfilehash: 37aa9551397bb3e3e8858a1289ddc3921327b722
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105168"
---
# <a name="well-known-event-providers-in-net"></a>.NET の既知のイベント プロバイダー

.NET ランタイムおよびライブラリで、さまざまなイベント プロバイダーを通じて診断イベントが書き込まれます。 診断のニーズに応じて、有効にする適切なプロバイダーを選択できます。 この記事では、.NET ランタイムおよびライブラリで最もよく使用されるいくつかのイベント プロバイダーについて説明します。

## <a name="coreclr"></a>CoreCLR

### <a name="microsoft-windows-dotnetruntime-provider"></a>"Microsoft-Windows-DotNETRuntime" プロバイダー

このプロバイダーでは、GC、ローダー、JIT、例外、およびその他のイベントを含む、.NET ランタイムからのさまざまなイベントを出力します。 このプロバイダーの各イベントの詳細については、[ランタイム プロバイダー イベントの一覧](../../fundamentals/diagnostics/runtime-events.md)に関するページを参照してください。

### <a name="microsoft-dotnetcore-sampleprofiler-provider"></a>"Microsoft-DotNETCore-SampleProfiler" プロバイダー

このプロバイダーは、マネージド呼び出し履歴の CPU サンプリングに使用される .NET ランタイム イベント プロバイダーです。 有効な場合、各スレッドのマネージド呼び出し履歴のスナップショットが 10 ミリ秒ごとに取り込まれます。 この取り込みを有効にするには、`Informational` 以上の <xref:System.Diagnostics.Tracing.EventLevel> を指定する必要があります。

## <a name="framework-libraries"></a>フレームワーク ライブラリ

### <a name="microsoft-extensions-dependencyinjection-provider"></a>"Microsoft-Extensions-DependencyInjection" プロバイダー

このプロバイダーにより、DependencyInjection からの情報がログに記録されます。 次の表には、`Microsoft-Extensions-DependencyInjection` プロバイダーによってログに記録されるイベントが示されています。

|イベント名|Level|説明|
|----------|-----|-----------|
|`CallSiteBuilt`|詳細 (5)|呼び出しサイトが構築されました。|
|`ServiceResolved`|詳細 (5)|サービスが解決されました。|
|`ExpressionTreeGenerated`|詳細 (5)|式ツリーが生成されました。|
|`DynamicMethodBuilt`|詳細 (5)|<xref:System.Reflection.Emit.DynamicMethod> が構築されました。|

### <a name="systembuffersarraypooleventsource-provider"></a>"System.Buffers.ArrayPoolEventSource" プロバイダー

このプロバイダーにより、ArrayPool からの情報がログに記録されます。 次の表には、`ArrayPoolEventSource` によってログに記録されるイベントが示されています。

|イベント名|Level|説明|
|----------|-----|-----------|
|`BufferRented`|詳細 (5)|バッファーは正常にレンタルされています。|
|`BufferAllocated`|情報提供 (4)|バッファーはプールによって割り当てられています。|
|`BufferReturned`|詳細 (5)|バッファーはプールに返されます。|
|`BufferTrimmed`|情報提供 (4)|メモリが不足しているか非アクティブであるため、バッファーが解放されようとしています。|
|`BufferTrimPoll`|情報提供 (4)|バッファーをトリミングするための確認が行われています。|

### <a name="systemnethttp-provider"></a>"System.Net.Http" プロバイダー

このプロバイダーにより、HTTP スタックからの情報がログに記録されます。 次の表には、`System.Net.Http` プロバイダーによってログに記録されるイベントが示されています。

|イベント名|Level|説明|
|----------|-----|-----------|
|RequestStart|情報提供 (4)|HTTP 要求が開始されました。|
|RequestStop|情報提供 (4)|HTTP 要求が完了しました。|
|RequestFailed|エラー (2)|HTTP 要求に失敗しました。|
|ConnectionEstablished|情報提供 (4)|HTTP 接続が確立されました。|
|ConnectionClosed|情報提供 (4)|HTTP 接続が閉じられました。|
|RequestLeftQueue|情報提供 (4)|HTTP 要求が要求キューを離れました。|
|RequestHeadersStart|情報提供 (4)|ヘッダーの HTTP 要求が開始されました。|
|RequestHeaderStop|情報提供 (4)|ヘッダーの HTTP 要求が完了しました。|
|RequestContentStart|情報提供 (4)|コンテンツの HTTP 要求が開始されました。|
|RequestContentStop|情報提供 (4)|コンテンツの HTTP 要求が完了しました。|
|ResponseHeadersStart|情報提供 (4)|ヘッダーの HTTP 応答が開始されました。|
|ResponseHeaderStop|情報提供 (4)|ヘッダーの HTTP 応答が完了しました。|
|ResponseContentStart|情報提供 (4)|コンテンツの HTTP 応答が開始されました。|
|ResponseContentStop|情報提供 (4)|コンテンツの HTTP 応答が完了しました。|

### <a name="systemnetnameresolution-provider"></a>"System.Net.NameResolution" プロバイダー

このプロバイダーにより、ドメイン名の解決に関する情報がログに記録されます。 次の表には、`System.Net.NameResolution` によってログに記録されるイベントが示されています。

|イベント名|Level|説明|
|----------|-----|-----------|
|`ResolutionStart`|情報提供 (4)|ドメイン名の解決が開始されました。|
|`ResolutionStop`|情報提供 (4)|ドメイン名の解決が完了しました。|
|`ResolutionFailed`|情報提供 (4)|ドメイン名の解決に失敗しました。|

### <a name="systemnetsockets-provider"></a>"System.Net.Sockets" プロバイダー

このプロバイダーにより、<xref:System.Net.Sockets.Socket> からの情報がログに記録されます。 次の表には、`System.Net.Sockets` プロバイダーによってログに記録されるイベントが示されています。

|イベント名|Level|説明|
|----------|-----|-----------|
|`ConnectStart`|情報提供 (4)|ソケット接続の開始の試行が開始されました。|
|`ConnectStop`|情報提供 (4)|ソケット接続の開始の試行が完了しました。|
|`ConnectFailed`|情報提供 (4)|ソケット接続の開始の試行に失敗しました。|
|`AcceptStart`|情報提供 (4)|ソケット接続の受け入れの試行が開始されました。|
|`AcceptStop`|情報提供 (4)|ソケット接続の受け入れの試行が完了しました。|
|`AcceptFailed`|情報提供 (4)|ソケット接続の受け入れの試行に失敗しました。|

### <a name="systemthreadingtaskstpleventsource-provider"></a>"System.Threading.Tasks.TplEventSource" プロバイダー

このプロバイダーにより、タスク スケジューラ イベントなどの[タスク並列ライブラリ](../../standard/parallel-programming/task-parallel-library-tpl.md)の情報がログに記録されます。 次の表には、`TplEventSource` によってログに記録されるイベントが示されています。

|イベント名|キーワード|Level|説明|
|----------|-------|-----|-----------|
|`TaskScheduled`|`TaskTransfer`(`0x1`)<br /><br />`Tasks`(`0x2`)|情報提供 (4)|<xref:System.Threading.Tasks.Task> がタスク スケジューラのキューに登録されています。|
|`TaskStarted`|`Tasks`(`0x2`)|情報提供 (4)|<xref:System.Threading.Tasks.Task> の実行が開始されました。|
|`TaskCompleted`|`TaskStops`(`0x40`)|情報提供 (4)|<xref:System.Threading.Tasks.Task> の実行が完了しました。|
|`TaskWaitBegin`|`TaskTransfer`(`0x1`)<br /><br />`TaskWait`(`0x2`)|情報提供 (4)|<xref:System.Threading.Tasks.Task> の完了の暗黙的または明示的な待機が開始されたときに発生します。|
|`TaskWaitEnd`|`Tasks`(`0x2`)|詳細 (5)|<xref:System.Threading.Tasks.Task> 完了の待機の状態が戻ったときに発生します。|
|`TaskWaitContinuationStarted`|`Tasks`(`0x2`)|詳細 (5)|`TaskWaitEnd` に関連付けられた作業 (メソッド) が開始されたときに発生します。|
|`TaskWaitContinuationCompleted`|`TaskStops`(`0x40`)|詳細 (5)|`TaskWaitEnd` に関連付けられた作業 (メソッド) が完了したときに発生します。|
|`AwaitTaskContinuationScheduled`|`TaskTransfer`(`0x1`)<br /><br />`Tasks`(`0x2`)|情報提供 (4)|<xref:System.Threading.Tasks.Task> の非同期継続がスケジュールされている場合に発生します。|

## <a name="aspnet-core"></a>ASP.NET Core

ASP.NET Core には、ASP.NET Core スタックでの問題の診断に役立ついくつかのイベントも用意されています。

ASP.NET Core のイベントとそれらを消費する方法の詳細については、「[.NET Core および ASP.NET Core でのログ記録](/aspnet/core/fundamentals/logging/)」を参照してください。

## <a name="entity-framework-core"></a>Entity Framework コア

EF Core からは、EF Core で問題診断を支援するイベントも提供されます。

EF Core でのイベントとそれを使用する方法については、「[EF Core での .NET イベント](/ef/core/logging-events-diagnostics/events)」を参照してください。
