---
title: .NET の既知の EventCounter
description: .NET ランタイムとライブラリによって公開されている EventCounter を確認します。
ms.topic: reference
ms.date: 12/17/2020
ms.openlocfilehash: fc07ace22f1580d547c33b897bcd1bb9a1de15c3
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106496723"
---
# <a name="well-known-eventcounters-in-net"></a>.NET の既知の EventCounter

.NET のランタイムとライブラリによって、さまざまなパフォーマンスの問題を特定して診断するために使用できる複数の [`EventCounter`](./event-counters.md) が実装され、公開されています。 このドキュメントは、これらの `EventCounters` を監視するために使用できるプロバイダーとその説明に関するリファレンスです。

## <a name="systemruntime-counters"></a>System.Runtime カウンター

次のカウンターは、.NET ランタイム (CoreCLR) の一部として公開され、[`RuntimeEventSource.cs`](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs) に保持されます。

| カウンタ | 説明 |
|--|--|
| :::no-loc text="% Time in GC since last GC"::: (`time-in-gc`) | 最後の GC からの GC の時間 (パーセント) |
| :::no-loc text="Allocation Rate"::: (`alloc-rate`) | 更新間隔ごとに割り当てられたバイト数 |
| :::no-loc text="CPU Usage"::: (`cpu-usage`) | すべてのシステム CPU リソースに対するプロセスの CPU 使用率 (%) |
| :::no-loc text="Exception Count"::: (`exception-count`) | 発生した例外の数 |
| :::no-loc text="GC Heap Size"::: (`gc-heap-size`) | <xref:System.GC.GetTotalMemory(System.Boolean)?displayProperty=nameWithType> に基づいて割り当てられていると考えられるバイト数 |
| :::no-loc text="Gen 0 GC Count"::: (`gen-0-gc-count`) | 更新間隔ごとに Gen 0 で GC が発生した回数 |
| :::no-loc text="Gen 0 Size"::: (`gen-0-size`) | Gen 0 GC のバイト数 |
| :::no-loc text="Gen 1 GC Count"::: (`gen-1-gc-count`) | 更新間隔ごとに Gen 1 で GC が発生した回数 |
| :::no-loc text="Gen 1 Size"::: (`gen-1-size`) | Gen 1 GC のバイト数 |
| :::no-loc text="Gen 2 GC Count"::: (`gen-2-gc-count`) | 更新間隔ごとに Gen 2 で GC が発生した回数 |
| :::no-loc text="Gen 2 Size"::: (`gen-2-size`) | Gen 2 GC のバイト数 |
| :::no-loc text="LOH Size"::: (`loh-size`) | ラージ オブジェクト ヒープのバイト数 |
| :::no-loc text="POH Size"::: (`poh-size`) | ピン留めされたオブジェクト ヒープのバイト数 (.NET 5 以降のバージョンで取得可能) |
| :::no-loc text="GC Fragmentation"::: (`gc-fragmentation`) | GC ヒープの断片化 (.NET 5 以降のバージョンで取得可能) |
| :::no-loc text="Monitor Lock Contention Count"::: (`monitor-lock-contention-count`) | <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> に基づく、モニターのロックを取得しようとするときに競合があった回数 |
| :::no-loc text="Number of Active Timers"::: (`active-timer-count`) | <xref:System.Threading.Timer.ActiveCount?displayProperty=nameWithType> に基づく、現在アクティブになっている <xref:System.Threading.Timer> インスタンスの数 |
| :::no-loc text="Number of Assemblies Loaded"::: (`assembly-count`) | 特定の時点でプロセスに読み込まれた <xref:System.Reflection.Assembly> インスタンスの数 |
| :::no-loc text="ThreadPool Completed Work Item Count"::: (`threadpool-completed-items-count`) | <xref:System.Threading.ThreadPool> で、これまでに処理された作業項目の数 |
| :::no-loc text="ThreadPool Queue Length"::: (`threadpool-queue-length`) | <xref:System.Threading.ThreadPool> 内の処理対象のキューに現在登録されている作業項目の数 |
| :::no-loc text="ThreadPool Thread Count"::: (`threadpool-thread-count`) | <xref:System.Threading.ThreadPool.ThreadCount?displayProperty=nameWithType> に基づく、<xref:System.Threading.ThreadPool> に現在存在しているスレッド プールのスレッドの数 |
| :::no-loc text="Working Set"::: (`working-set`) | <xref:System.Environment.WorkingSet?displayProperty=nameWithType> に基づく、ある時点でプロセス コンテキストにマップされた物理メモリの量 |
| :::no-loc text="IL Bytes Jitted"::: (`il-bytes-jitted`) | JIT コンパイルされる IL のバイト単位の合計サイズ (.NET 5 以降のバージョンで取得可能) |
| :::no-loc text="Method Jitted Count"::: (`method-jitted-count`) | JIT コンパイルされるメソッドの数 (.NET 5 以降のバージョンで取得可能) |
| :::no-loc text="GC Committed Bytes"::: (`gc-committed-bytes`) | GC によってコミットされたバイト数 (.NET 6 以降のバージョンで使用可能) |

## <a name="microsoftaspnetcorehosting-counters"></a>"Microsoft.AspNetCore.Hosting" カウンター

次のカウンターは、[ASP.NET Core](/aspnet/core) の一部として公開され、[`HostingEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/main/src/Hosting/Hosting/src/Internal/HostingEventSource.cs) に保持されます。

| カウンター | 説明 |
|--|--|
| :::no-loc text="Current Requests"::: (`current-requests`) | 開始したが、まだ停止していない要求の合計数 |
| :::no-loc text="Failed Requests"::: (`failed-requests`) | アプリの有効期間中に発生した、失敗した要求の合計数 |
| :::no-loc text="Request Rate"::: (`requests-per-second`) | 更新間隔ごとに発生する要求の数 |
| :::no-loc text="Total Requests"::: (`total-requests`) | アプリの有効期間中に発生した要求の合計数 |

## <a name="microsoftaspnetcorehttpconnections-counters"></a>"Microsoft.AspNetCore.Http.Connections" カウンター

次のカウンターは、[ASP.NET Core SignalR](/aspnet/core/signalr/introduction) の一部として公開され、[`HttpConnectionsEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/main/src/SignalR/common/Http.Connections/src/Internal/HttpConnectionsEventSource.cs) に保持されます。

| カウンター | 説明 |
|--|--|
| :::no-loc text="Average Connection Duration"::: (`connections-duration`) | 接続の平均継続時間 (ミリ秒) |
| :::no-loc text="Current Connections"::: (`current-connections`) | 開始したが、まだ停止していないアクティブな接続の数 |
| :::no-loc text="Total Connections Started"::: (`connections-started`) | 開始した接続の合計数 |
| :::no-loc text="Total Connections Stopped"::: (`connections-stopped`) | 停止した接続の合計数 |
| :::no-loc text="Total Connections Timed Out"::: (`connections-timed-out`) | タイム アウトした接続の合計数 |

## <a name="microsoft-aspnetcore-server-kestrel-counters"></a>"Microsoft-AspNetCore-Server-Kestrel" カウンター

次のカウンターは、[ASP.NET Core Kestrel Web サーバー](/aspnet/core/fundamentals/servers/kestrel)の一部として公開され、[`KestrelEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/main/src/Servers/Kestrel/Core/src/Internal/Infrastructure/KestrelEventSource.cs) に保持されます。

| カウンター | 説明 |
|--|--|
| :::no-loc text="Connection Queue Length"::: (`connection-queue-length`) | 接続キューの現在の長さ |
| :::no-loc text="Connection Rate"::: (`connections-per-second`) | 更新間隔ごとの Web サーバーへの接続数 |
| :::no-loc text="Current Connections"::: (`current-connections`) | Web サーバーへのアクティブな接続の現在の数 |
| :::no-loc text="Current TLS Handshakes"::: (`current-tls-handshakes`) | TLS ハンドシェイクの現在の数 |
| :::no-loc text="Current Upgraded Requests (WebSockets)"::: (`current-upgraded-requests`) | アップグレードされた要求の現在の数 (WebSocket) |
| :::no-loc text="Failed TLS Handshakes"::: (`failed-tls-handshakes`) | 失敗した TLS ハンドシェイクの合計数 |
| :::no-loc text="Request Queue Length"::: (`request-queue-length`) | 要求キューの現在の長さ |
| :::no-loc text="TLS Handshake Rate"::: (`tls-handshakes-per-second`) | 更新間隔ごとの TLS ハンドシェイクの数 |
| :::no-loc text="Total Connections"::: (`total-connections`) | Web サーバーへの接続の合計数 |
| :::no-loc text="Total TLS Handshakes"::: (`total-tls-handshakes`) | Web サーバーとの TLS ハンドシェイクの合計数 |

## <a name="systemnethttp-counters"></a>"System.Net.Http" カウンター

以下のカウンターは、HTTP スタックによって発行されます。  これらのカウンターは、.NET 5 以降のバージョンでのみ使用できます。

| カウンタ | 説明 |
|--|--|
| :::no-loc text="Requests Started"::: (`requests-started`) | プロセスの開始以降に開始された要求の数 |
| :::no-loc text="Requests Started Rate"::: (`requests-started-rate`) | 更新間隔ごとに開始された要求の数 |
| :::no-loc text="Requests Failed"::: (`requests-failed`) | プロセスの開始以降に失敗した要求の数 |
| :::no-loc text="Requests Failed Rate"::: (`requests-failed-rate`) | 更新間隔ごとに失敗した要求の数 |
| :::no-loc text="Current Requests"::: (`current-requests`) | 開始したが、まだ完了も失敗もしていない、現在アクティブな HTTP 要求の数 |
| :::no-loc text="Current HTTP 1.1 Connections"::: (`http11-connections-current-total`) | 開始したが、まだ完了も失敗もしていない、現在の HTTP 1.1 接続の数 |
| :::no-loc text="Current HTTP 2.0 Connections"::: (`http20-connections-current-total`) | 開始したが、まだ完了も失敗もしていない、現在の HTTP 2.0 接続の数 |
| :::no-loc text="HTTP 1.1 Requests Queue Duration"::: (`http11-requests-queue-duration`) | HTTP 1.1 要求が要求キューで費やした平均時間 |
| :::no-loc text="HTTP 2.0 Requests Queue Duration"::: (`http20-requests-queue-duration`) | HTTP 2.0 要求が要求キューで費やした平均時間 |

## <a name="systemnetnameresolution-counters"></a>"System.Net.NameResolution" カウンター

以下のカウンターは、DNS 参照に関連するメトリックを追跡します。 これらのカウンターは、.NET 5 以降のバージョンでのみ使用できます。

| カウンタ | 説明 |
|--|--|
| :::no-loc text="DNS Lookups Requested"::: (`dns-lookups-requested`) | プロセスの開始以降に要求された DNS 参照の数 |
| :::no-loc text="Average DNS Lookup Duration"::: (`dns-lookups-duration`) | DNS 参照にかかった平均時間 |

## <a name="systemnetsecurity-counters"></a>"System.Net.Security" カウンター

以下のカウンターは、トランスポート層セキュリティ プロトコルに関連するメトリックを追跡します。  これらのカウンターは、.NET 5 以降のバージョンでのみ使用できます。

| カウンタ | 説明 |
|--|--|
| :::no-loc text="TLS handshakes completed"::: (`tls-handshake-rate`) | 更新間隔ごとに完了した TLS ハンドシェイクの数 |
| :::no-loc text="Total TLS handshakes completed"::: (`total-tls-handshakes`) | プロセスの開始以降に完了した TLS ハンドシェイクの合計数 |
| :::no-loc text="Current TLS handshakes"::: (`current-tls-handshakes`) | 開始したがまだ完了していない、現在の TLS ハンドシェイクの数 |
| :::no-loc text="Total TLS handshakes failed"::: (`failed-tls-handshakes`) | プロセスの開始以降に失敗した TLS ハンドシェイクの合計数 |
| :::no-loc text="All TLS Sessions Active"::: (`all-tls-sessions-open`) | 任意のバージョンのアクティブな TLS セッションの数 |
| :::no-loc text="TLS 1.0 Sessions Active"::: (`tls10-sessions-open`) | アクティブな TLS 1.0 セッションの数 |
| :::no-loc text="TLS 1.1 Sessions Active"::: (`tls11-sessions-open`) | アクティブな TLS 1.1 セッションの数 |
| :::no-loc text="TLS 1.2 Sessions Active"::: (`tls12-sessions-open`) | アクティブな TLS 1.2 セッションの数 |
| :::no-loc text="TLS 1.3 Sessions Active"::: (`tls13-sessions-open`) | アクティブな TLS 1.3 セッションの数 |
| :::no-loc text="TLS Handshake Duration"::: (`all-tls-handshake-duration`) | すべての TLS ハンドシェイクの平均継続時間 |
| :::no-loc text="TLS 1.0 Handshake Duration"::: (`tls10-handshake-duration`) | TLS 1.0 ハンドシェイクの平均継続時間 |
| :::no-loc text="TLS 1.1 Handshake Duration"::: (`tls11-handshake-duration`) | TLS 1.1 ハンドシェイクの平均継続時間 |
| :::no-loc text="TLS 1.2 Handshake Duration"::: (`tls12-handshake-duration`) | TLS 1.2 ハンドシェイクの平均継続時間 |
| :::no-loc text="TLS 1.3 Handshake Duration"::: (`tls13-handshake-duration`) | TLS 1.3 ハンドシェイクの平均継続時間 |

## <a name="systemnetsockets-counters-available-on-net-5-and-later-versions"></a>"System.Net.Sockets" カウンター (.NET 5 以降のバージョンで使用可能)

以下のカウンターは、<xref:System.Net.Sockets.Socket> に関連するメトリックを追跡します。

| カウンタ | 説明 |
|--|--|
| :::no-loc text="Outgoing Connections Established"::: (`outgoing-connections-established`) | プロセスの開始以降に確立された発信接続の合計数 |
| :::no-loc text="Incoming Connections Established"::: (`incoming-connections-established`) | プロセスの開始以降に確立された着信接続の合計数 |
| :::no-loc text="Bytes Received"::: (`bytes-received`) | プロセスの開始以降に受信した合計バイト数 |
| :::no-loc text="Bytes Sent"::: (`bytes-sent`) | プロセスの開始以降に送信した合計バイト数 |
| :::no-loc text="Datagrams Received"::: (`datagrams-received`) | プロセスの開始以降に受信したデータグラムの合計数 |
| :::no-loc text="Datagrams Sent"::: (`datagrams-sent`) | プロセスの開始以降に送信したデータグラムの合計数 |
