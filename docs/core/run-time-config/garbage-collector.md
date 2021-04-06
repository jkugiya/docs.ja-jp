---
title: ガベージ コレクター構成の設定
description: ガベージ コレクターでの .NET Core アプリ用のメモリの管理方法を構成するための、実行時設定について学習します。
ms.date: 07/10/2020
ms.topic: reference
ms.openlocfilehash: 1bae00d2fc6e80811986bbb111f38582720f8487
ms.sourcegitcommit: 872ca41d1c26f39d0aef57cc365d09503bac780d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2021
ms.locfileid: "106288079"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>ガベージ コレクションの実行時構成オプション

このページには、実行時に変更できるガベージ コレクター (GC) の設定に関する情報が含まれています。 実行中のアプリのピーク時のパフォーマンスを実現しようとしている場合は、これらの設定の使用を検討してください。 しかし、一般的な状況では、既定値でほとんどのアプリケーションに最適なパフォーマンスが得られます。

このページでは、設定はグループにまとめられます。 各グループ内の設定は一般的に、特定の結果を得るために相互に組み合わせて使用されます。

> [!NOTE]
>
> - これらの設定は、実行中にアプリで動的に変更することもできます。したがって、設定した実行時の設定が上書きされる可能性があります。
> - [待機時間レベル](../../standard/garbage-collection/latency.md)などの一部の設定は、通常、デザイン時に API を介してのみ設定されます。 このページでは、このような設定は省略されています。
> - 数値の場合、*runtimeconfig.json* ファイルの設定には 10 進表記、環境変数の設定には 16 進表記を使用します。 16 進値の場合は、プレフィックス "0x" を付けても付けなくても指定できます。

## <a name="flavors-of-garbage-collection"></a>ガベージ コレクションのフレーバー

ガベージ コレクションの主な 2 つのフレーバーは、ワークステーション GC とサーバー GC です。 2 つの間の相違点について詳しくは、「[ワークステーションとサーバーのガベージ コレクション](../../standard/garbage-collection/workstation-server-gc.md)」をご覧ください。

ガベージ コレクションのサブフレーバーは、バックグラウンドと非同時実行です。

ガベージ コレクションのフレーバーを選択するには、以下の設定を使用します。

- [ワークステーションとサーバーの GC](#workstation-vs-server)
- [バックグラウンド GC](#background-gc)

### <a name="workstation-vs-server"></a>ワークステーションとサーバー

- アプリケーションで、ワークステーション ガベージ コレクションとサーバー ガベージ コレクションのどちらを使用するかを構成します。
- 既定:ワークステーション ガベージ コレクション。 これは、値を `false` に設定した場合と同じです。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.Server` | `false` - ワークステーション<br/>`true` - サーバー | .NET Core 1.0 |
| **MSBuild のプロパティ** | `ServerGarbageCollection` | `false` - ワークステーション<br/>`true` - サーバー | .NET Core 1.0 |
| **環境変数** | `COMPlus_gcServer` | `0` - ワークステーション<br/>`1` - サーバー | .NET Core 1.0 |
| **.NET Framework 用の app.config** | [GCServer](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false` - ワークステーション<br/>`true` - サーバー |  |

#### <a name="examples"></a>使用例

*runtimeconfig.json* ファイル:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

プロジェクト ファイル:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="background-gc"></a>バックグラウンド GC

- バックグラウンド (同時実行) ガベージ コレクションを有効にするかどうかを構成します。
- 既定:バックグラウンド GC を使用します。 これは、値を `true` に設定した場合と同じです。
- 詳しくは、「[バックグラウンド ガベージ コレクション](../../standard/garbage-collection/background-gc.md)」をご覧ください。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.Concurrent` | `true` - バックグラウンド GC<br/>`false` -非同時実行 GC | .NET Core 1.0 |
| **MSBuild のプロパティ** | `ConcurrentGarbageCollection` | `true` - バックグラウンド GC<br/>`false` -非同時実行 GC | .NET Core 1.0 |
| **環境変数** | `COMPlus_gcConcurrent` | `1` - バックグラウンド GC<br/>`0` -非同時実行 GC | .NET Core 1.0 |
| **.NET Framework 用の app.config** | [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true` - バックグラウンド GC<br/>`false` -非同時実行 GC |  |

#### <a name="examples"></a>使用例

*runtimeconfig.json* ファイル:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

プロジェクト ファイル:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a>リソース使用量を管理する

次の設定を使用して、ガベージ コレクターのメモリとプロセッサの使用量を管理します。

- [関係付け](#affinitize)
- [関係付けマスク](#affinitize-mask)
- [関係付け範囲](#affinitize-ranges)
- [CPU グループ](#cpu-groups)
- [ヒープ数](#heap-count)
- [ヒープの制限](#heap-limit)
- [ヒープの制限の割合](#heap-limit-percent)
- [使用率の高いメモリの割合](#high-memory-percent)
- [オブジェクトごとのヒープの制限](#per-object-heap-limits)
- [オブジェクトごとのヒープの制限の割合](#per-object-heap-limit-percents)
- [VM の保持](#retain-vm)

これらの設定のいくつかの詳細については、[ワークステーションおよびサーバー GC 間の妥協点](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/)に関するブログ エントリを参照してください。

### <a name="heap-count"></a>ヒープ数

- ガベージ コレクターによって作成されるヒープの数を制限します。
- サーバー ガベージ コレクションにのみ適用されます。
- [GC プロセッサの関係](#affinitize)が有効になっている場合 (既定値)、ヒープ数の設定では、最初の `n` プロセッサに `n` GC ヒープやスレッドを関連付けます。 ([関係付けマスク](#affinitize-mask)または[関係付け範囲](#affinitize-ranges)の設定を使用して、関係付けるプロセッサを正確に指定します)。
- [GC プロセッサの関係](#affinitize)が無効になっている場合、この設定によって GC ヒープの数が制限されます。
- 詳細については、[GCHeapCount の解説](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)に関する記述を参照してください。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapCount` | "*10 進値*" | .NET Core 3.0 |
| **環境変数** | `COMPlus_GCHeapCount` | "*16 進値*" | .NET Core 3.0 |
| **.NET Framework 用の app.config** | [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | "*10 進値*" | .NET Framework 4.6.2 |

例:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapCount": 16
      }
   }
}
```

> [!TIP]
> *runtimeconfig.json* でオプションを設定する場合は、10 進値を指定します。 環境変数としてオプションを設定する場合は、16 進値を指定します。 たとえば、ヒープの数を 16 に制限する場合、値は JSON ファイルでは 16、環境変数では 0x10 または 10 になります。

### <a name="affinitize-mask"></a>関係付けマスク

- ガベージ コレクター スレッドで使用する必要がある正確なプロセッサを指定します。
- [GC プロセッサの関係](#affinitize)が無効になっている場合、この設定は無視されます。
- サーバー ガベージ コレクションにのみ適用されます。
- この値は、プロセスで使用できるプロセッサを定義するビット マスクです。 たとえば、10 進値の 1023 (環境変数を使用する場合は、16 進値の 0x3FF または 3FF) は、バイナリ表記では 0011 1111 1111 となります。 これにより、最初の 10 プロセッサが使用されることが指定されます。 次の 10 プロセッサ (つまり、10 から 19 プロセッサ) を指定するには、10 進値の 1047552 (または 16 進値の 0xFFC00 または FFC00) を指定します。これは、バイナリ値の 1111 1111 1100 0000 0000 に相当します。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapAffinitizeMask` | "*10 進値*" | .NET Core 3.0 |
| **環境変数** | `COMPlus_GCHeapAffinitizeMask` | "*16 進値*" | .NET Core 3.0 |
| **.NET Framework 用の app.config** | [GCHeapAffinitizeMask](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | "*10 進値*" | .NET Framework 4.6.2 |

例:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="affinitize-ranges"></a>関係付け範囲

- ガベージ コレクター スレッドに使用するプロセッサのリストを指定します。
- この設定は [System.GC.HeapAffinitizeMask](#affinitize-mask) に似ていますが、64 を超えるプロセッサを指定できる点が異なります。
- Windows オペレーティング システムの場合、プロセッサの番号または範囲の前に、対応する [CPU グループ](/windows/win32/procthread/processor-groups)を付けます。たとえば、"0:1-10,0:12,1:50-52,1:70" となります。
- [GC プロセッサの関係](#affinitize)が無効になっている場合、この設定は無視されます。
- サーバー ガベージ コレクションにのみ適用されます。
- 詳細については、Maoni Stephens のブログの「[CPU が 64 を超えるコンピューター上での GC のための CPU 構成の向上](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/)」を参照してください。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.GCHeapAffinitizeRanges` | プロセッサ番号またはプロセッサ番号の範囲のコンマ区切りリスト。<br/>Unix の例:"1-10,12,50-52,70"<br/>Windows の例:"0:1-10,0:12,1:50-52,1:70" | .NET Core 3.0 |
| **環境変数** | `COMPlus_GCHeapAffinitizeRanges` | プロセッサ番号またはプロセッサ番号の範囲のコンマ区切りリスト。<br/>Unix の例:"1-10,12,50-52,70"<br/>Windows の例:"0:1-10,0:12,1:50-52,1:70" | .NET Core 3.0 |

例:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="cpu-groups"></a>CPU グループ

- ガベージ コレクターで [CPU グループ](/windows/win32/procthread/processor-groups)を使用するかどうかを構成します。

  64 ビットの Windows コンピューターに複数の CPU グループがある (つまり、64 を超えるプロセッサがある) 場合、この要素を有効にすると、すべての CPU グループ全体にガベージ コレクションが拡張されます。 ガベージ コレクターではすべてのコアを使用し、ヒープを作成して分散させます。

- 64 ビット Windows オペレーティング システムのみのサーバー ガベージ コレクションに適用されます。
- 既定:GC は複数の CPU グループに拡張されません。 これは、値を `0` に設定した場合と同じです。
- 詳細については、Maoni Stephens のブログの「[CPU が 64 を超えるコンピューター上での GC のための CPU 構成の向上](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/)」を参照してください。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.CpuGroup` | `0` - 無効<br/>`1` - 有効 | .NET 5.0 |
| **環境変数** | `COMPlus_GCCpuGroup` | `0` - 無効<br/>`1` - 有効 | .NET Core 1.0 |
| **.NET Framework 用の app.config** | [GCCpuGroup](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false` - 無効<br/>`true` - 有効 |  |

> [!NOTE]
> すべての CPU グループ全体にスレッド プールからのスレッドも分散するように共通言語ランタイム (CLR) を構成するには、[Thread_UseAllCpuGroups 要素](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)オプションを有効にします。 .NET Core アプリの場合は、`COMPlus_Thread_UseAllCpuGroups` 環境変数の値を `1` に設定することによって、このオプションを有効にすることができます。

### <a name="affinitize"></a>関係付け

- ガベージ コレクション スレッドをプロセッサに "*関係付ける*" かどうかを指定します。 GC スレッドを関係付けることは、その特定の CPU でのみ実行できることを意味します。 各 GC スレッドに対してヒープが作成されます。
- サーバー ガベージ コレクションにのみ適用されます。
- 既定:ガベージ コレクション スレッドをプロセッサに関係付けます。 これは、値を `false` に設定した場合と同じです。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.NoAffinitize` | `false` -関係付ける<br/>`true` -関係付けない | .NET Core 3.0 |
| **環境変数** | `COMPlus_GCNoAffinitize` | `0` -関係付ける<br/>`1` -関係付けない | .NET Core 3.0 |
| **.NET Framework 用の app.config** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false` -関係付ける<br/>`true` -関係付けない | .NET Framework 4.6.2 |

例:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="heap-limit"></a>ヒープの制限

- GC ヒープおよび GC ブックキーピングに対して、最大コミット サイズをバイト単位で指定します。
- この設定は 64 ビットのコンピューターにのみ該当します。
- [オブジェクトごとのヒープの制限](#per-object-heap-limits)が構成されている場合、この設定は無視されます。
- 特定のケースにのみ該当する既定値は、20 MB より大、またはコンテナーのメモリ制限の 75% より大です。 次の場合に既定値は該当します。

  - プロセスが、メモリ制限が指定されたコンテナー内で実行されています。
  - [System.GC.HeapHardLimitPercent](#heap-limit-percent) が設定されていません。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimit` | "*10 進値*" | .NET Core 3.0 |
| **環境変数** | `COMPlus_GCHeapHardLimit` | "*16 進値*" | .NET Core 3.0 |

例:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimit": 209715200
      }
   }
}
```

> [!TIP]
> *runtimeconfig.json* でオプションを設定する場合は、10 進値を指定します。 環境変数としてオプションを設定する場合は、16 進値を指定します。 たとえば、ヒープのハード制限を 200 メビバイト (MiB) に指定する場合、値は JSON ファイルでは 209715200、環境変数では 0xC800000 または C800000 になります。

### <a name="heap-limit-percent"></a>ヒープの制限の割合

- 許容可能な GC ヒープの使用量を、物理メモリ合計に対する割合として指定します。
- この設定は、[System.GC.HeapHardLimit](#heap-limit) も設定されている場合、無視されます。
- この設定は 64 ビットのコンピューターにのみ該当します。
- プロセスが、メモリ制限が指定されたコンテナー内で実行されている場合、パーセンテージはそのメモリ制限に対するパーセンテージとして計算されます。
- [オブジェクトごとのヒープの制限](#per-object-heap-limits)が構成されている場合、この設定は無視されます。
- 特定のケースにのみ該当する既定値は、20 MB より大、またはコンテナーのメモリ制限の 75% より大です。 次の場合に既定値は該当します。

  - プロセスが、メモリ制限が指定されたコンテナー内で実行されています。
  - [System.GC.HeapHardLimit](#heap-limit) が設定されていません。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimitPercent` | "*10 進値*" | .NET Core 3.0 |
| **環境変数** | `COMPlus_GCHeapHardLimitPercent` | "*16 進値*" | .NET Core 3.0 |

例:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimitPercent": 30
      }
   }
}
```

> [!TIP]
> *runtimeconfig.json* でオプションを設定する場合は、10 進値を指定します。 環境変数としてオプションを設定する場合は、16 進値を指定します。 たとえば、ヒープの使用量を 30% に制限する場合、値は JSON ファイルでは 30、環境変数では 0x1E または 1E になります。

### <a name="per-object-heap-limits"></a>オブジェクトごとのヒープの制限

オブジェクトごとのヒープに基づいて、GC で許容されるヒープ使用量を指定できます。 ヒープには、大きなオブジェクト ヒープ (LOH)、小さなオブジェクト ヒープ (SOH)、固定オブジェクト ヒープ (POH) があります。

- `COMPLUS_GCHeapHardLimitSOH`、`COMPLUS_GCHeapHardLimitLOH`、`COMPLUS_GCHeapHardLimitPOH` 設定のいずれかの値を指定する場合、`COMPLUS_GCHeapHardLimitSOH` と `COMPLUS_GCHeapHardLimitLOH` の値も指定する必要があります。 そうしないと、ランタイムでの初期化が失敗します。
- `COMPLUS_GCHeapHardLimitPOH` の既定値は 0 です。 `COMPLUS_GCHeapHardLimitSOH` と `COMPLUS_GCHeapHardLimitLOH` には既定値はありません。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimitSOH` | "*10 進値*" | .NET 5.0 |
| **環境変数** | `COMPLUS_GCHeapHardLimitSOH` | "*16 進値*" | .NET 5.0 |

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimitLOH` | "*10 進値*" | .NET 5.0 |
| **環境変数** | `COMPLUS_GCHeapHardLimitLOH` | "*16 進値*" | .NET 5.0 |

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimitPOH` | "*10 進値*" | .NET 5.0 |
| **環境変数** | `COMPLUS_GCHeapHardLimitPOH` | "*16 進値*" | .NET 5.0 |

> [!TIP]
> *runtimeconfig.json* でオプションを設定する場合は、10 進値を指定します。 環境変数としてオプションを設定する場合は、16 進値を指定します。 たとえば、ヒープのハード制限を 200 メビバイト (MiB) に指定する場合、値は JSON ファイルでは 209715200、環境変数では 0xC800000 または C800000 になります。

### <a name="per-object-heap-limit-percents"></a>オブジェクトごとのヒープの制限の割合

オブジェクトごとのヒープに基づいて、GC で許容されるヒープ使用量を指定できます。 ヒープには、大きなオブジェクト ヒープ (LOH)、小さなオブジェクト ヒープ (SOH)、固定オブジェクト ヒープ (POH) があります。

- `COMPLUS_GCHeapHardLimitSOHPercent`、`COMPLUS_GCHeapHardLimitLOHPercent`、`COMPLUS_GCHeapHardLimitPOHPercent` 設定のいずれかの値を指定する場合、`COMPLUS_GCHeapHardLimitSOHPercent` と `COMPLUS_GCHeapHardLimitLOHPercent` の値も指定する必要があります。 そうしないと、ランタイムでの初期化が失敗します。
- `COMPLUS_GCHeapHardLimitSOH`、`COMPLUS_GCHeapHardLimitLOH`、および `COMPLUS_GCHeapHardLimitPOH` が指定されている場合、これらの設定は無視されます。
- 値 1 は、GC によって合計物理メモリの 1% がそのオブジェクト ヒープに使用されることを意味します。
- 各値は、ゼロより大きく、100 未満である必要があります。 また、3 つのパーセンテージ値の合計は、100 未満である必要があります。 それ以外の場合、ランタイムでの初期化が失敗します。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimitSOHPercent` | "*10 進値*" | .NET 5.0 |
| **環境変数** | `COMPLUS_GCHeapHardLimitSOHPercent` | "*16 進値*" | .NET 5.0 |

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimitLOHPercent` | "*10 進値*" | .NET 5.0 |
| **環境変数** | `COMPLUS_GCHeapHardLimitLOHPercent` | "*16 進値*" | .NET 5.0 |

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimitPOHPercent` | "*10 進値*" | .NET 5.0 |
| **環境変数** | `COMPLUS_GCHeapHardLimitPOHPercent` | "*16 進値*" | .NET 5.0 |

> [!TIP]
> *runtimeconfig.json* でオプションを設定する場合は、10 進値を指定します。 環境変数としてオプションを設定する場合は、16 進値を指定します。 たとえば、ヒープの使用量を 30% に制限する場合、値は JSON ファイルでは 30、環境変数では 0x1E または 1E になります。

### <a name="high-memory-percent"></a>使用率の高いメモリの割合

メモリの負荷は、使用されている物理メモリの割合によって示されます。 既定では、物理メモリの負荷が **90%** に達すると、ガベージコレクションがより積極的に完全に実行され、ガベージ コレクションが圧縮されてページングが回避されるようになります。 メモリの負荷が 90% 未満の場合、GC によって、フル ガベージ コレクションに対するバックグラウンド コレクションが優先されます。一時停止は短くなりますが、ヒープ サイズの合計はそれほど小さくなりません。 大量のメモリ (80 GB 以上) が搭載されたコンピューターでは、負荷のしきい値は 90% から 97% が既定値です。

使用率の高いメモリの負荷のしきい値は、`COMPlus_GCHighMemPercent` 環境変数、または `System.GC.HighMemoryPercent` JSON 構成設定によって調整できます。 ヒープ サイズを制御する場合は、しきい値の調整を検討してください。 たとえば、64 GB のメモリを搭載したコンピューター上で最も優先度の高いプロセスでは、使用可能なメモリが 10% あれば、GC が反応を開始するのが妥当です。 ただし、サイズの小さいプロセス、たとえば 1 GB のメモリしか消費しないプロセスでは、使用可能なメモリが 10% 未満でも、GC を快適に実行できます。 このような小さいプロセスでは、しきい値を高く設定することを検討してください。 一方、大きなプロセスでヒープ サイズを小さくする場合は、使用可能な物理メモリが十分にあったとしても、このしきい値を低くすると、GC がすぐに反応してヒープを圧縮できるため、方法としては効率的です。

> [!NOTE]
> コンテナーで実行されているプロセスの場合、GC によって、コンテナーの制限に基づいて物理メモリが考慮されます。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HighMemoryPercent` | "*10 進値*" | .NET 5.0 |
| **環境変数** | `COMPlus_GCHighMemPercent` | "*16 進値*" | |

> [!TIP]
> *runtimeconfig.json* でオプションを設定する場合は、10 進値を指定します。 環境変数としてオプションを設定する場合は、16 進値を指定します。 たとえば、使用率の高いメモリのしきい値を 75% に設定するための値は、JSON ファイルに対しては 75、環境変数に対しては 0x4B または 4B となります。

### <a name="retain-vm"></a>VM の保持

- 削除する必要があるセグメントを、後で使用するためにスタンバイ リストに配置するか、解放してオペレーティング システム (OS) に戻すかを構成します。
- 既定:セグメントを解放してオペレーティング システムに戻します。 これは、値を `false` に設定した場合と同じです。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.RetainVM` | `false` -OS に解放する<br/>`true` - スタンバイに配置する | .NET Core 1.0 |
| **MSBuild のプロパティ** | `RetainVMGarbageCollection` | `false` -OS に解放する<br/>`true` - スタンバイに配置する | .NET Core 1.0 |
| **環境変数** | `COMPlus_GCRetainVM` | `0` -OS に解放する<br/>`1` - スタンバイに配置する | .NET Core 1.0 |

#### <a name="examples"></a>使用例

*runtimeconfig.json* ファイル:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

プロジェクト ファイル:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a>大きいページ

- ヒープのハード制限が設定されている場合に、大きいページを使用する必要があるかどうかを指定します。
- 既定:ヒープのハード制限が設定されている場合は、大きいページを使用しません。 これは、値を `0` に設定した場合と同じです。
- これは試験段階の設定です。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | N/A | 該当なし | N/A |
| **環境変数** | `COMPlus_GCLargePages` | `0` - 無効<br/>`1` - 有効 | .NET Core 3.0 |

## <a name="allow-large-objects"></a>大きなオブジェクトを許可する

- 合計サイズが 2 ギガバイト (GB) を超える配列に対して、64 ビット プラットフォームでのガベージ コレクター サポートを構成します。
- 既定:GC では、2 GB を超える配列がサポートされます。 これは、値を `1` に設定した場合と同じです。
- このオプションは、将来のバージョンの .NET で廃止される可能性があります。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | N/A | 該当なし | N/A |
| **環境変数** | `COMPlus_gcAllowVeryLargeObjects` | `1` - 有効<br/> `0` - 無効 | .NET Core 1.0 |
| **.NET Framework 用の app.config** | [gcAllowVeryLargeObjects](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | `1` - 有効<br/> `0` - 無効 | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>大きなオブジェクト ヒープのしきい値

- オブジェクトが大きなオブジェクト ヒープ (LOH) に移る原因となる、しきい値のサイズ (バイト単位) を指定します。
- 既定のしきい値は 85,000 バイトです。
- 指定する値は、既定のしきい値より大きくする必要があります。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.LOHThreshold` | "*10 進値*" | .NET Core 1.0 |
| **環境変数** | `COMPlus_GCLOHThreshold` | "*16 進値*" | .NET Core 1.0 |
| **.NET Framework 用の app.config** | [GCLOHThreshold](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | "*10 進値*" | .NET Framework 4.8 |

例:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.LOHThreshold": 120000
      }
   }
}
```

> [!TIP]
> *runtimeconfig.json* でオプションを設定する場合は、10 進値を指定します。 環境変数としてオプションを設定する場合は、16 進値を指定します。 たとえば、しきい値のサイズを 120,000 バイトに設定する場合、値は JSON ファイルでは 120000、環境変数では 0x1D4C0 または 1D4C0 になります。

## <a name="standalone-gc"></a>スタンドアロン GC

- ランタイムで読み込む対象となる、ガベージ コレクターを含むライブラリへのパスを指定します。
- 詳細については、「[スタンドアロン GC ローダーの設計](https://github.com/dotnet/runtime/blob/main/docs/design/features/standalone-gc-loading.md)」を参照してください。

| | 設定の名前 | 値 | 導入されたバージョン |
| - | - | - | - |
| **runtimeconfig.json** | N/A | 該当なし | N/A |
| **環境変数** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
