---
title: ガベージ コレクター構成の設定
description: ガベージ コレクターでの .NET Core アプリ用のメモリの管理方法を構成するための、実行時設定について学習します。
ms.date: 07/10/2020
ms.topic: reference
ms.openlocfilehash: 17df3ec8473750edfca4999972c56be1e8a5feec
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106496658"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="b172e-103">ガベージ コレクションの実行時構成オプション</span><span class="sxs-lookup"><span data-stu-id="b172e-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="b172e-104">このページには、実行時に変更できるガベージ コレクター (GC) の設定に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b172e-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="b172e-105">実行中のアプリのピーク時のパフォーマンスを実現しようとしている場合は、これらの設定の使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="b172e-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="b172e-106">しかし、一般的な状況では、既定値でほとんどのアプリケーションに最適なパフォーマンスが得られます。</span><span class="sxs-lookup"><span data-stu-id="b172e-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="b172e-107">このページでは、設定はグループにまとめられます。</span><span class="sxs-lookup"><span data-stu-id="b172e-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="b172e-108">各グループ内の設定は一般的に、特定の結果を得るために相互に組み合わせて使用されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="b172e-109">これらの設定は、実行中にアプリで動的に変更することもできます。したがって、設定した実行時の設定が上書きされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b172e-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="b172e-110">[待機時間レベル](../../standard/garbage-collection/latency.md)などの一部の設定は、通常、デザイン時に API を介してのみ設定されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="b172e-111">このページでは、このような設定は省略されています。</span><span class="sxs-lookup"><span data-stu-id="b172e-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="b172e-112">数値の場合、*runtimeconfig.json* ファイルの設定には 10 進表記、環境変数の設定には 16 進表記を使用します。</span><span class="sxs-lookup"><span data-stu-id="b172e-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="b172e-113">16 進値の場合は、プレフィックス "0x" を付けても付けなくても指定できます。</span><span class="sxs-lookup"><span data-stu-id="b172e-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="b172e-114">ガベージ コレクションのフレーバー</span><span class="sxs-lookup"><span data-stu-id="b172e-114">Flavors of garbage collection</span></span>

<span data-ttu-id="b172e-115">ガベージ コレクションの主な 2 つのフレーバーは、ワークステーション GC とサーバー GC です。</span><span class="sxs-lookup"><span data-stu-id="b172e-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="b172e-116">2 つの間の相違点について詳しくは、「[ワークステーションとサーバーのガベージ コレクション](../../standard/garbage-collection/workstation-server-gc.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b172e-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="b172e-117">ガベージ コレクションのサブフレーバーは、バックグラウンドと非同時実行です。</span><span class="sxs-lookup"><span data-stu-id="b172e-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="b172e-118">ガベージ コレクションのフレーバーを選択するには、以下の設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="b172e-118">Use the following settings to select flavors of garbage collection:</span></span>

- [<span data-ttu-id="b172e-119">ワークステーションとサーバーの GC</span><span class="sxs-lookup"><span data-stu-id="b172e-119">Workstation vs. server GC</span></span>](#workstation-vs-server)
- [<span data-ttu-id="b172e-120">バックグラウンド GC</span><span class="sxs-lookup"><span data-stu-id="b172e-120">Background GC</span></span>](#background-gc)

### <a name="workstation-vs-server"></a><span data-ttu-id="b172e-121">ワークステーションとサーバー</span><span class="sxs-lookup"><span data-stu-id="b172e-121">Workstation vs. server</span></span>

- <span data-ttu-id="b172e-122">アプリケーションで、ワークステーション ガベージ コレクションとサーバー ガベージ コレクションのどちらを使用するかを構成します。</span><span class="sxs-lookup"><span data-stu-id="b172e-122">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="b172e-123">既定:ワークステーション ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="b172e-123">Default: Workstation garbage collection.</span></span> <span data-ttu-id="b172e-124">これは、値を `false` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="b172e-124">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="b172e-125">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-125">Setting name</span></span> | <span data-ttu-id="b172e-126">値</span><span class="sxs-lookup"><span data-stu-id="b172e-126">Values</span></span> | <span data-ttu-id="b172e-127">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-127">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-128">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-128">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="b172e-129">`false` - ワークステーション</span><span class="sxs-lookup"><span data-stu-id="b172e-129">`false` - workstation</span></span><br/><span data-ttu-id="b172e-130">`true` - サーバー</span><span class="sxs-lookup"><span data-stu-id="b172e-130">`true` - server</span></span> | <span data-ttu-id="b172e-131">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="b172e-131">.NET Core 1.0</span></span> |
| <span data-ttu-id="b172e-132">**MSBuild のプロパティ**</span><span class="sxs-lookup"><span data-stu-id="b172e-132">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="b172e-133">`false` - ワークステーション</span><span class="sxs-lookup"><span data-stu-id="b172e-133">`false` - workstation</span></span><br/><span data-ttu-id="b172e-134">`true` - サーバー</span><span class="sxs-lookup"><span data-stu-id="b172e-134">`true` - server</span></span> | <span data-ttu-id="b172e-135">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="b172e-135">.NET Core 1.0</span></span> |
| <span data-ttu-id="b172e-136">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-136">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="b172e-137">`0` - ワークステーション</span><span class="sxs-lookup"><span data-stu-id="b172e-137">`0` - workstation</span></span><br/><span data-ttu-id="b172e-138">`1` - サーバー</span><span class="sxs-lookup"><span data-stu-id="b172e-138">`1` - server</span></span> | <span data-ttu-id="b172e-139">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="b172e-139">.NET Core 1.0</span></span> |
| <span data-ttu-id="b172e-140">**.NET Framework 用の app.config**</span><span class="sxs-lookup"><span data-stu-id="b172e-140">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="b172e-141">GCServer</span><span class="sxs-lookup"><span data-stu-id="b172e-141">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="b172e-142">`false` - ワークステーション</span><span class="sxs-lookup"><span data-stu-id="b172e-142">`false` - workstation</span></span><br/><span data-ttu-id="b172e-143">`true` - サーバー</span><span class="sxs-lookup"><span data-stu-id="b172e-143">`true` - server</span></span> |  |

#### <a name="examples"></a><span data-ttu-id="b172e-144">使用例</span><span class="sxs-lookup"><span data-stu-id="b172e-144">Examples</span></span>

<span data-ttu-id="b172e-145">*runtimeconfig.json* ファイル:</span><span class="sxs-lookup"><span data-stu-id="b172e-145">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="b172e-146">プロジェクト ファイル:</span><span class="sxs-lookup"><span data-stu-id="b172e-146">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="background-gc"></a><span data-ttu-id="b172e-147">バックグラウンド GC</span><span class="sxs-lookup"><span data-stu-id="b172e-147">Background GC</span></span>

- <span data-ttu-id="b172e-148">バックグラウンド (同時実行) ガベージ コレクションを有効にするかどうかを構成します。</span><span class="sxs-lookup"><span data-stu-id="b172e-148">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="b172e-149">既定:バックグラウンド GC を使用します。</span><span class="sxs-lookup"><span data-stu-id="b172e-149">Default: Use background GC.</span></span> <span data-ttu-id="b172e-150">これは、値を `true` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="b172e-150">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="b172e-151">詳しくは、「[バックグラウンド ガベージ コレクション](../../standard/garbage-collection/background-gc.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b172e-151">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="b172e-152">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-152">Setting name</span></span> | <span data-ttu-id="b172e-153">値</span><span class="sxs-lookup"><span data-stu-id="b172e-153">Values</span></span> | <span data-ttu-id="b172e-154">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-154">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-155">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-155">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="b172e-156">`true` - バックグラウンド GC</span><span class="sxs-lookup"><span data-stu-id="b172e-156">`true` - background GC</span></span><br/><span data-ttu-id="b172e-157">`false` -非同時実行 GC</span><span class="sxs-lookup"><span data-stu-id="b172e-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="b172e-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="b172e-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="b172e-159">**MSBuild のプロパティ**</span><span class="sxs-lookup"><span data-stu-id="b172e-159">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="b172e-160">`true` - バックグラウンド GC</span><span class="sxs-lookup"><span data-stu-id="b172e-160">`true` - background GC</span></span><br/><span data-ttu-id="b172e-161">`false` -非同時実行 GC</span><span class="sxs-lookup"><span data-stu-id="b172e-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="b172e-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="b172e-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="b172e-163">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-163">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="b172e-164">`1` - バックグラウンド GC</span><span class="sxs-lookup"><span data-stu-id="b172e-164">`1` - background GC</span></span><br/><span data-ttu-id="b172e-165">`0` -非同時実行 GC</span><span class="sxs-lookup"><span data-stu-id="b172e-165">`0` - non-concurrent GC</span></span> | <span data-ttu-id="b172e-166">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="b172e-166">.NET Core 1.0</span></span> |
| <span data-ttu-id="b172e-167">**.NET Framework 用の app.config**</span><span class="sxs-lookup"><span data-stu-id="b172e-167">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="b172e-168">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="b172e-168">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="b172e-169">`true` - バックグラウンド GC</span><span class="sxs-lookup"><span data-stu-id="b172e-169">`true` - background GC</span></span><br/><span data-ttu-id="b172e-170">`false` -非同時実行 GC</span><span class="sxs-lookup"><span data-stu-id="b172e-170">`false` - non-concurrent GC</span></span> |  |

#### <a name="examples"></a><span data-ttu-id="b172e-171">使用例</span><span class="sxs-lookup"><span data-stu-id="b172e-171">Examples</span></span>

<span data-ttu-id="b172e-172">*runtimeconfig.json* ファイル:</span><span class="sxs-lookup"><span data-stu-id="b172e-172">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="b172e-173">プロジェクト ファイル:</span><span class="sxs-lookup"><span data-stu-id="b172e-173">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="b172e-174">リソース使用量を管理する</span><span class="sxs-lookup"><span data-stu-id="b172e-174">Manage resource usage</span></span>

<span data-ttu-id="b172e-175">次の設定を使用して、ガベージ コレクターのメモリとプロセッサの使用量を管理します。</span><span class="sxs-lookup"><span data-stu-id="b172e-175">Use the following settings to manage the garbage collector's memory and processor usage:</span></span>

- [<span data-ttu-id="b172e-176">関係付け</span><span class="sxs-lookup"><span data-stu-id="b172e-176">Affinitize</span></span>](#affinitize)
- [<span data-ttu-id="b172e-177">関係付けマスク</span><span class="sxs-lookup"><span data-stu-id="b172e-177">Affinitize mask</span></span>](#affinitize-mask)
- [<span data-ttu-id="b172e-178">関係付け範囲</span><span class="sxs-lookup"><span data-stu-id="b172e-178">Affinitize ranges</span></span>](#affinitize-ranges)
- [<span data-ttu-id="b172e-179">CPU グループ</span><span class="sxs-lookup"><span data-stu-id="b172e-179">CPU groups</span></span>](#cpu-groups)
- [<span data-ttu-id="b172e-180">ヒープ数</span><span class="sxs-lookup"><span data-stu-id="b172e-180">Heap count</span></span>](#heap-count)
- [<span data-ttu-id="b172e-181">ヒープの制限</span><span class="sxs-lookup"><span data-stu-id="b172e-181">Heap limit</span></span>](#heap-limit)
- [<span data-ttu-id="b172e-182">ヒープの制限の割合</span><span class="sxs-lookup"><span data-stu-id="b172e-182">Heap limit percent</span></span>](#heap-limit-percent)
- [<span data-ttu-id="b172e-183">使用率の高いメモリの割合</span><span class="sxs-lookup"><span data-stu-id="b172e-183">High memory percent</span></span>](#high-memory-percent)
- [<span data-ttu-id="b172e-184">オブジェクトごとのヒープの制限</span><span class="sxs-lookup"><span data-stu-id="b172e-184">Per-object-heap limits</span></span>](#per-object-heap-limits)
- [<span data-ttu-id="b172e-185">オブジェクトごとのヒープの制限の割合</span><span class="sxs-lookup"><span data-stu-id="b172e-185">Per-object-heap limit percents</span></span>](#per-object-heap-limit-percents)
- [<span data-ttu-id="b172e-186">VM の保持</span><span class="sxs-lookup"><span data-stu-id="b172e-186">Retain VM</span></span>](#retain-vm)

<span data-ttu-id="b172e-187">これらの設定のいくつかの詳細については、[ワークステーションおよびサーバー GC 間の妥協点](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/)に関するブログ エントリを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b172e-187">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="heap-count"></a><span data-ttu-id="b172e-188">ヒープ数</span><span class="sxs-lookup"><span data-stu-id="b172e-188">Heap count</span></span>

- <span data-ttu-id="b172e-189">ガベージ コレクターによって作成されるヒープの数を制限します。</span><span class="sxs-lookup"><span data-stu-id="b172e-189">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="b172e-190">サーバー ガベージ コレクションにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-190">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="b172e-191">[GC プロセッサの関係](#affinitize)が有効になっている場合 (既定値)、ヒープ数の設定では、最初の `n` プロセッサに `n` GC ヒープやスレッドを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="b172e-191">If [GC processor affinity](#affinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="b172e-192">([関係付けマスク](#affinitize-mask)または[関係付け範囲](#affinitize-ranges)の設定を使用して、関係付けるプロセッサを正確に指定します)。</span><span class="sxs-lookup"><span data-stu-id="b172e-192">(Use the [affinitize mask](#affinitize-mask) or [affinitize ranges](#affinitize-ranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="b172e-193">[GC プロセッサの関係](#affinitize)が無効になっている場合、この設定によって GC ヒープの数が制限されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-193">If [GC processor affinity](#affinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="b172e-194">詳細については、[GCHeapCount の解説](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b172e-194">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="b172e-195">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-195">Setting name</span></span> | <span data-ttu-id="b172e-196">値</span><span class="sxs-lookup"><span data-stu-id="b172e-196">Values</span></span> | <span data-ttu-id="b172e-197">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-197">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-198">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-198">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="b172e-199">"*10 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-199">*decimal value*</span></span> | <span data-ttu-id="b172e-200">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b172e-200">.NET Core 3.0</span></span> |
| <span data-ttu-id="b172e-201">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-201">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="b172e-202">"*16 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-202">*hexadecimal value*</span></span> | <span data-ttu-id="b172e-203">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b172e-203">.NET Core 3.0</span></span> |
| <span data-ttu-id="b172e-204">**.NET Framework 用の app.config**</span><span class="sxs-lookup"><span data-stu-id="b172e-204">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="b172e-205">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="b172e-205">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="b172e-206">"*10 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-206">*decimal value*</span></span> | <span data-ttu-id="b172e-207">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="b172e-207">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="b172e-208">例:</span><span class="sxs-lookup"><span data-stu-id="b172e-208">Example:</span></span>

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
> <span data-ttu-id="b172e-209">*runtimeconfig.json* でオプションを設定する場合は、10 進値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-209">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="b172e-210">環境変数としてオプションを設定する場合は、16 進値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-210">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="b172e-211">たとえば、ヒープの数を 16 に制限する場合、値は JSON ファイルでは 16、環境変数では 0x10 または 10 になります。</span><span class="sxs-lookup"><span data-stu-id="b172e-211">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="affinitize-mask"></a><span data-ttu-id="b172e-212">関係付けマスク</span><span class="sxs-lookup"><span data-stu-id="b172e-212">Affinitize mask</span></span>

- <span data-ttu-id="b172e-213">ガベージ コレクター スレッドで使用する必要がある正確なプロセッサを指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-213">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="b172e-214">[GC プロセッサの関係](#affinitize)が無効になっている場合、この設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-214">If [GC processor affinity](#affinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="b172e-215">サーバー ガベージ コレクションにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-215">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="b172e-216">この値は、プロセスで使用できるプロセッサを定義するビット マスクです。</span><span class="sxs-lookup"><span data-stu-id="b172e-216">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="b172e-217">たとえば、10 進値の 1023 (環境変数を使用する場合は、16 進値の 0x3FF または 3FF) は、バイナリ表記では 0011 1111 1111 となります。</span><span class="sxs-lookup"><span data-stu-id="b172e-217">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="b172e-218">これにより、最初の 10 プロセッサが使用されることが指定されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-218">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="b172e-219">次の 10 プロセッサ (つまり、10 から 19 プロセッサ) を指定するには、10 進値の 1047552 (または 16 進値の 0xFFC00 または FFC00) を指定します。これは、バイナリ値の 1111 1111 1100 0000 0000 に相当します。</span><span class="sxs-lookup"><span data-stu-id="b172e-219">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="b172e-220">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-220">Setting name</span></span> | <span data-ttu-id="b172e-221">値</span><span class="sxs-lookup"><span data-stu-id="b172e-221">Values</span></span> | <span data-ttu-id="b172e-222">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-222">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-223">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-223">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="b172e-224">"*10 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-224">*decimal value*</span></span> | <span data-ttu-id="b172e-225">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b172e-225">.NET Core 3.0</span></span> |
| <span data-ttu-id="b172e-226">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-226">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="b172e-227">"*16 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-227">*hexadecimal value*</span></span> | <span data-ttu-id="b172e-228">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b172e-228">.NET Core 3.0</span></span> |
| <span data-ttu-id="b172e-229">**.NET Framework 用の app.config**</span><span class="sxs-lookup"><span data-stu-id="b172e-229">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="b172e-230">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="b172e-230">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="b172e-231">"*10 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-231">*decimal value*</span></span> | <span data-ttu-id="b172e-232">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="b172e-232">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="b172e-233">例:</span><span class="sxs-lookup"><span data-stu-id="b172e-233">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="affinitize-ranges"></a><span data-ttu-id="b172e-234">関係付け範囲</span><span class="sxs-lookup"><span data-stu-id="b172e-234">Affinitize ranges</span></span>

- <span data-ttu-id="b172e-235">ガベージ コレクター スレッドに使用するプロセッサのリストを指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-235">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="b172e-236">この設定は [System.GC.HeapAffinitizeMask](#affinitize-mask) に似ていますが、64 を超えるプロセッサを指定できる点が異なります。</span><span class="sxs-lookup"><span data-stu-id="b172e-236">This setting is similar to [System.GC.HeapAffinitizeMask](#affinitize-mask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="b172e-237">Windows オペレーティング システムの場合、プロセッサの番号または範囲の前に、対応する [CPU グループ](/windows/win32/procthread/processor-groups)を付けます。たとえば、"0:1-10,0:12,1:50-52,1:70" となります。</span><span class="sxs-lookup"><span data-stu-id="b172e-237">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="b172e-238">[GC プロセッサの関係](#affinitize)が無効になっている場合、この設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-238">If [GC processor affinity](#affinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="b172e-239">サーバー ガベージ コレクションにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-239">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="b172e-240">詳細については、Maoni Stephens のブログの「[CPU が 64 を超えるコンピューター上での GC のための CPU 構成の向上](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b172e-240">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="b172e-241">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-241">Setting name</span></span> | <span data-ttu-id="b172e-242">値</span><span class="sxs-lookup"><span data-stu-id="b172e-242">Values</span></span> | <span data-ttu-id="b172e-243">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-243">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-244">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-244">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="b172e-245">プロセッサ番号またはプロセッサ番号の範囲のコンマ区切りリスト。</span><span class="sxs-lookup"><span data-stu-id="b172e-245">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="b172e-246">Unix の例:"1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="b172e-246">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="b172e-247">Windows の例:"0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="b172e-247">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="b172e-248">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b172e-248">.NET Core 3.0</span></span> |
| <span data-ttu-id="b172e-249">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-249">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="b172e-250">プロセッサ番号またはプロセッサ番号の範囲のコンマ区切りリスト。</span><span class="sxs-lookup"><span data-stu-id="b172e-250">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="b172e-251">Unix の例:"1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="b172e-251">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="b172e-252">Windows の例:"0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="b172e-252">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="b172e-253">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b172e-253">.NET Core 3.0</span></span> |

<span data-ttu-id="b172e-254">例:</span><span class="sxs-lookup"><span data-stu-id="b172e-254">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="cpu-groups"></a><span data-ttu-id="b172e-255">CPU グループ</span><span class="sxs-lookup"><span data-stu-id="b172e-255">CPU groups</span></span>

- <span data-ttu-id="b172e-256">ガベージ コレクターで [CPU グループ](/windows/win32/procthread/processor-groups)を使用するかどうかを構成します。</span><span class="sxs-lookup"><span data-stu-id="b172e-256">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="b172e-257">64 ビットの Windows コンピューターに複数の CPU グループがある (つまり、64 を超えるプロセッサがある) 場合、この要素を有効にすると、すべての CPU グループ全体にガベージ コレクションが拡張されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-257">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="b172e-258">ガベージ コレクターではすべてのコアを使用し、ヒープを作成して分散させます。</span><span class="sxs-lookup"><span data-stu-id="b172e-258">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="b172e-259">64 ビット Windows オペレーティング システムのみのサーバー ガベージ コレクションに適用されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-259">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="b172e-260">既定:GC は複数の CPU グループに拡張されません。</span><span class="sxs-lookup"><span data-stu-id="b172e-260">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="b172e-261">これは、値を `0` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="b172e-261">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="b172e-262">詳細については、Maoni Stephens のブログの「[CPU が 64 を超えるコンピューター上での GC のための CPU 構成の向上](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b172e-262">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="b172e-263">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-263">Setting name</span></span> | <span data-ttu-id="b172e-264">値</span><span class="sxs-lookup"><span data-stu-id="b172e-264">Values</span></span> | <span data-ttu-id="b172e-265">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-265">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-266">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-266">**runtimeconfig.json**</span></span> | `System.GC.CpuGroup` | <span data-ttu-id="b172e-267">`0` - 無効</span><span class="sxs-lookup"><span data-stu-id="b172e-267">`0` - disabled</span></span><br/><span data-ttu-id="b172e-268">`1` - 有効</span><span class="sxs-lookup"><span data-stu-id="b172e-268">`1` - enabled</span></span> | <span data-ttu-id="b172e-269">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b172e-269">.NET 5.0</span></span> |
| <span data-ttu-id="b172e-270">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-270">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="b172e-271">`0` - 無効</span><span class="sxs-lookup"><span data-stu-id="b172e-271">`0` - disabled</span></span><br/><span data-ttu-id="b172e-272">`1` - 有効</span><span class="sxs-lookup"><span data-stu-id="b172e-272">`1` - enabled</span></span> | <span data-ttu-id="b172e-273">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="b172e-273">.NET Core 1.0</span></span> |
| <span data-ttu-id="b172e-274">**.NET Framework 用の app.config**</span><span class="sxs-lookup"><span data-stu-id="b172e-274">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="b172e-275">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="b172e-275">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="b172e-276">`false` - 無効</span><span class="sxs-lookup"><span data-stu-id="b172e-276">`false` - disabled</span></span><br/><span data-ttu-id="b172e-277">`true` - 有効</span><span class="sxs-lookup"><span data-stu-id="b172e-277">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="b172e-278">すべての CPU グループ全体にスレッド プールからのスレッドも分散するように共通言語ランタイム (CLR) を構成するには、[Thread_UseAllCpuGroups 要素](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)オプションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="b172e-278">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="b172e-279">.NET Core アプリの場合は、`COMPlus_Thread_UseAllCpuGroups` 環境変数の値を `1` に設定することによって、このオプションを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="b172e-279">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="affinitize"></a><span data-ttu-id="b172e-280">関係付け</span><span class="sxs-lookup"><span data-stu-id="b172e-280">Affinitize</span></span>

- <span data-ttu-id="b172e-281">ガベージ コレクション スレッドをプロセッサに "*関係付ける*" かどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-281">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="b172e-282">GC スレッドを関係付けることは、その特定の CPU でのみ実行できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="b172e-282">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="b172e-283">各 GC スレッドに対してヒープが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-283">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="b172e-284">サーバー ガベージ コレクションにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-284">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="b172e-285">既定:ガベージ コレクション スレッドをプロセッサに関係付けます。</span><span class="sxs-lookup"><span data-stu-id="b172e-285">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="b172e-286">これは、値を `false` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="b172e-286">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="b172e-287">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-287">Setting name</span></span> | <span data-ttu-id="b172e-288">値</span><span class="sxs-lookup"><span data-stu-id="b172e-288">Values</span></span> | <span data-ttu-id="b172e-289">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-289">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-290">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-290">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="b172e-291">`false` -関係付ける</span><span class="sxs-lookup"><span data-stu-id="b172e-291">`false` - affinitize</span></span><br/><span data-ttu-id="b172e-292">`true` -関係付けない</span><span class="sxs-lookup"><span data-stu-id="b172e-292">`true` - don't affinitize</span></span> | <span data-ttu-id="b172e-293">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b172e-293">.NET Core 3.0</span></span> |
| <span data-ttu-id="b172e-294">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-294">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="b172e-295">`0` -関係付ける</span><span class="sxs-lookup"><span data-stu-id="b172e-295">`0` - affinitize</span></span><br/><span data-ttu-id="b172e-296">`1` -関係付けない</span><span class="sxs-lookup"><span data-stu-id="b172e-296">`1` - don't affinitize</span></span> | <span data-ttu-id="b172e-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b172e-297">.NET Core 3.0</span></span> |
| <span data-ttu-id="b172e-298">**.NET Framework 用の app.config**</span><span class="sxs-lookup"><span data-stu-id="b172e-298">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="b172e-299">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="b172e-299">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="b172e-300">`false` -関係付ける</span><span class="sxs-lookup"><span data-stu-id="b172e-300">`false` - affinitize</span></span><br/><span data-ttu-id="b172e-301">`true` -関係付けない</span><span class="sxs-lookup"><span data-stu-id="b172e-301">`true` - don't affinitize</span></span> | <span data-ttu-id="b172e-302">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="b172e-302">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="b172e-303">例:</span><span class="sxs-lookup"><span data-stu-id="b172e-303">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="heap-limit"></a><span data-ttu-id="b172e-304">ヒープの制限</span><span class="sxs-lookup"><span data-stu-id="b172e-304">Heap limit</span></span>

- <span data-ttu-id="b172e-305">GC ヒープおよび GC ブックキーピングに対して、最大コミット サイズをバイト単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-305">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="b172e-306">この設定は 64 ビットのコンピューターにのみ該当します。</span><span class="sxs-lookup"><span data-stu-id="b172e-306">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="b172e-307">[オブジェクトごとのヒープの制限](#per-object-heap-limits)が構成されている場合、この設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-307">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="b172e-308">特定のケースにのみ該当する既定値は、20 MB より大、またはコンテナーのメモリ制限の 75% より大です。</span><span class="sxs-lookup"><span data-stu-id="b172e-308">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="b172e-309">次の場合に既定値は該当します。</span><span class="sxs-lookup"><span data-stu-id="b172e-309">The default value applies if:</span></span>

  - <span data-ttu-id="b172e-310">プロセスが、メモリ制限が指定されたコンテナー内で実行されています。</span><span class="sxs-lookup"><span data-stu-id="b172e-310">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="b172e-311">[System.GC.HeapHardLimitPercent](#heap-limit-percent) が設定されていません。</span><span class="sxs-lookup"><span data-stu-id="b172e-311">[System.GC.HeapHardLimitPercent](#heap-limit-percent) is not set.</span></span>

| | <span data-ttu-id="b172e-312">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-312">Setting name</span></span> | <span data-ttu-id="b172e-313">値</span><span class="sxs-lookup"><span data-stu-id="b172e-313">Values</span></span> | <span data-ttu-id="b172e-314">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-314">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-315">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-315">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="b172e-316">"*10 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-316">*decimal value*</span></span> | <span data-ttu-id="b172e-317">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b172e-317">.NET Core 3.0</span></span> |
| <span data-ttu-id="b172e-318">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-318">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="b172e-319">"*16 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-319">*hexadecimal value*</span></span> | <span data-ttu-id="b172e-320">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b172e-320">.NET Core 3.0</span></span> |

<span data-ttu-id="b172e-321">例:</span><span class="sxs-lookup"><span data-stu-id="b172e-321">Example:</span></span>

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
> <span data-ttu-id="b172e-322">*runtimeconfig.json* でオプションを設定する場合は、10 進値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-322">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="b172e-323">環境変数としてオプションを設定する場合は、16 進値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-323">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="b172e-324">たとえば、ヒープのハード制限を 200 メビバイト (MiB) に指定する場合、値は JSON ファイルでは 209715200、環境変数では 0xC800000 または C800000 になります。</span><span class="sxs-lookup"><span data-stu-id="b172e-324">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="heap-limit-percent"></a><span data-ttu-id="b172e-325">ヒープの制限の割合</span><span class="sxs-lookup"><span data-stu-id="b172e-325">Heap limit percent</span></span>

- <span data-ttu-id="b172e-326">許容可能な GC ヒープの使用量を、物理メモリ合計に対する割合として指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-326">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="b172e-327">この設定は、[System.GC.HeapHardLimit](#heap-limit) も設定されている場合、無視されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-327">If [System.GC.HeapHardLimit](#heap-limit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="b172e-328">この設定は 64 ビットのコンピューターにのみ該当します。</span><span class="sxs-lookup"><span data-stu-id="b172e-328">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="b172e-329">プロセスが、メモリ制限が指定されたコンテナー内で実行されている場合、パーセンテージはそのメモリ制限に対するパーセンテージとして計算されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-329">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="b172e-330">[オブジェクトごとのヒープの制限](#per-object-heap-limits)が構成されている場合、この設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-330">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="b172e-331">特定のケースにのみ該当する既定値は、20 MB より大、またはコンテナーのメモリ制限の 75% より大です。</span><span class="sxs-lookup"><span data-stu-id="b172e-331">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="b172e-332">次の場合に既定値は該当します。</span><span class="sxs-lookup"><span data-stu-id="b172e-332">The default value applies if:</span></span>

  - <span data-ttu-id="b172e-333">プロセスが、メモリ制限が指定されたコンテナー内で実行されています。</span><span class="sxs-lookup"><span data-stu-id="b172e-333">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="b172e-334">[System.GC.HeapHardLimit](#heap-limit) が設定されていません。</span><span class="sxs-lookup"><span data-stu-id="b172e-334">[System.GC.HeapHardLimit](#heap-limit) is not set.</span></span>

| | <span data-ttu-id="b172e-335">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-335">Setting name</span></span> | <span data-ttu-id="b172e-336">値</span><span class="sxs-lookup"><span data-stu-id="b172e-336">Values</span></span> | <span data-ttu-id="b172e-337">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-337">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-338">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-338">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="b172e-339">"*10 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-339">*decimal value*</span></span> | <span data-ttu-id="b172e-340">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b172e-340">.NET Core 3.0</span></span> |
| <span data-ttu-id="b172e-341">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-341">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="b172e-342">"*16 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-342">*hexadecimal value*</span></span> | <span data-ttu-id="b172e-343">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b172e-343">.NET Core 3.0</span></span> |

<span data-ttu-id="b172e-344">例:</span><span class="sxs-lookup"><span data-stu-id="b172e-344">Example:</span></span>

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
> <span data-ttu-id="b172e-345">*runtimeconfig.json* でオプションを設定する場合は、10 進値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-345">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="b172e-346">環境変数としてオプションを設定する場合は、16 進値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-346">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="b172e-347">たとえば、ヒープの使用量を 30% に制限する場合、値は JSON ファイルでは 30、環境変数では 0x1E または 1E になります。</span><span class="sxs-lookup"><span data-stu-id="b172e-347">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="per-object-heap-limits"></a><span data-ttu-id="b172e-348">オブジェクトごとのヒープの制限</span><span class="sxs-lookup"><span data-stu-id="b172e-348">Per-object-heap limits</span></span>

<span data-ttu-id="b172e-349">オブジェクトごとのヒープに基づいて、GC で許容されるヒープ使用量を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b172e-349">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="b172e-350">ヒープには、大きなオブジェクト ヒープ (LOH)、小さなオブジェクト ヒープ (SOH)、固定オブジェクト ヒープ (POH) があります。</span><span class="sxs-lookup"><span data-stu-id="b172e-350">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

- <span data-ttu-id="b172e-351">`COMPLUS_GCHeapHardLimitSOH`、`COMPLUS_GCHeapHardLimitLOH`、`COMPLUS_GCHeapHardLimitPOH` 設定のいずれかの値を指定する場合、`COMPLUS_GCHeapHardLimitSOH` と `COMPLUS_GCHeapHardLimitLOH` の値も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b172e-351">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, or `COMPLUS_GCHeapHardLimitPOH` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH`.</span></span> <span data-ttu-id="b172e-352">そうしないと、ランタイムでの初期化が失敗します。</span><span class="sxs-lookup"><span data-stu-id="b172e-352">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="b172e-353">`COMPLUS_GCHeapHardLimitPOH` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="b172e-353">The default value for `COMPLUS_GCHeapHardLimitPOH` is 0.</span></span> <span data-ttu-id="b172e-354">`COMPLUS_GCHeapHardLimitSOH` と `COMPLUS_GCHeapHardLimitLOH` には既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="b172e-354">`COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH` don't have default values.</span></span>

| | <span data-ttu-id="b172e-355">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-355">Setting name</span></span> | <span data-ttu-id="b172e-356">値</span><span class="sxs-lookup"><span data-stu-id="b172e-356">Values</span></span> | <span data-ttu-id="b172e-357">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-357">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-358">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-358">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitSOH` | <span data-ttu-id="b172e-359">"*10 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-359">*decimal value*</span></span> | <span data-ttu-id="b172e-360">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b172e-360">.NET 5.0</span></span> |
| <span data-ttu-id="b172e-361">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-361">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOH` | <span data-ttu-id="b172e-362">"*16 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-362">*hexadecimal value*</span></span> | <span data-ttu-id="b172e-363">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b172e-363">.NET 5.0</span></span> |

| | <span data-ttu-id="b172e-364">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-364">Setting name</span></span> | <span data-ttu-id="b172e-365">値</span><span class="sxs-lookup"><span data-stu-id="b172e-365">Values</span></span> | <span data-ttu-id="b172e-366">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-366">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-367">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-367">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitLOH` | <span data-ttu-id="b172e-368">"*10 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-368">*decimal value*</span></span> | <span data-ttu-id="b172e-369">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b172e-369">.NET 5.0</span></span> |
| <span data-ttu-id="b172e-370">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-370">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOH` | <span data-ttu-id="b172e-371">"*16 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-371">*hexadecimal value*</span></span> | <span data-ttu-id="b172e-372">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b172e-372">.NET 5.0</span></span> |

| | <span data-ttu-id="b172e-373">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-373">Setting name</span></span> | <span data-ttu-id="b172e-374">値</span><span class="sxs-lookup"><span data-stu-id="b172e-374">Values</span></span> | <span data-ttu-id="b172e-375">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-375">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-376">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-376">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPOH` | <span data-ttu-id="b172e-377">"*10 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-377">*decimal value*</span></span> | <span data-ttu-id="b172e-378">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b172e-378">.NET 5.0</span></span> |
| <span data-ttu-id="b172e-379">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-379">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOH` | <span data-ttu-id="b172e-380">"*16 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-380">*hexadecimal value*</span></span> | <span data-ttu-id="b172e-381">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b172e-381">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="b172e-382">*runtimeconfig.json* でオプションを設定する場合は、10 進値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-382">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="b172e-383">環境変数としてオプションを設定する場合は、16 進値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-383">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="b172e-384">たとえば、ヒープのハード制限を 200 メビバイト (MiB) に指定する場合、値は JSON ファイルでは 209715200、環境変数では 0xC800000 または C800000 になります。</span><span class="sxs-lookup"><span data-stu-id="b172e-384">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="per-object-heap-limit-percents"></a><span data-ttu-id="b172e-385">オブジェクトごとのヒープの制限の割合</span><span class="sxs-lookup"><span data-stu-id="b172e-385">Per-object-heap limit percents</span></span>

<span data-ttu-id="b172e-386">オブジェクトごとのヒープに基づいて、GC で許容されるヒープ使用量を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b172e-386">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="b172e-387">ヒープには、大きなオブジェクト ヒープ (LOH)、小さなオブジェクト ヒープ (SOH)、固定オブジェクト ヒープ (POH) があります。</span><span class="sxs-lookup"><span data-stu-id="b172e-387">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

- <span data-ttu-id="b172e-388">`COMPLUS_GCHeapHardLimitSOHPercent`、`COMPLUS_GCHeapHardLimitLOHPercent`、`COMPLUS_GCHeapHardLimitPOHPercent` 設定のいずれかの値を指定する場合、`COMPLUS_GCHeapHardLimitSOHPercent` と `COMPLUS_GCHeapHardLimitLOHPercent` の値も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b172e-388">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOHPercent`, `COMPLUS_GCHeapHardLimitLOHPercent`, or `COMPLUS_GCHeapHardLimitPOHPercent` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOHPercent` and `COMPLUS_GCHeapHardLimitLOHPercent`.</span></span> <span data-ttu-id="b172e-389">そうしないと、ランタイムでの初期化が失敗します。</span><span class="sxs-lookup"><span data-stu-id="b172e-389">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="b172e-390">`COMPLUS_GCHeapHardLimitSOH`、`COMPLUS_GCHeapHardLimitLOH`、および `COMPLUS_GCHeapHardLimitPOH` が指定されている場合、これらの設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-390">These settings are ignored if `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, and `COMPLUS_GCHeapHardLimitPOH` are specified.</span></span>
- <span data-ttu-id="b172e-391">値 1 は、GC によって合計物理メモリの 1% がそのオブジェクト ヒープに使用されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="b172e-391">A value of 1 means that GC uses 1% of total physical memory for that object heap.</span></span>
- <span data-ttu-id="b172e-392">各値は、ゼロより大きく、100 未満である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b172e-392">Each value must be greater than zero and less than 100.</span></span> <span data-ttu-id="b172e-393">また、3 つのパーセンテージ値の合計は、100 未満である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b172e-393">Additionally, the sum of the three percentage values must be less than 100.</span></span> <span data-ttu-id="b172e-394">それ以外の場合、ランタイムでの初期化が失敗します。</span><span class="sxs-lookup"><span data-stu-id="b172e-394">Otherwise, the runtime will fail to initialize.</span></span>

| | <span data-ttu-id="b172e-395">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-395">Setting name</span></span> | <span data-ttu-id="b172e-396">値</span><span class="sxs-lookup"><span data-stu-id="b172e-396">Values</span></span> | <span data-ttu-id="b172e-397">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-397">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-398">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-398">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitSOHPercent` | <span data-ttu-id="b172e-399">"*10 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-399">*decimal value*</span></span> | <span data-ttu-id="b172e-400">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b172e-400">.NET 5.0</span></span> |
| <span data-ttu-id="b172e-401">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-401">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOHPercent` | <span data-ttu-id="b172e-402">"*16 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-402">*hexadecimal value*</span></span> | <span data-ttu-id="b172e-403">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b172e-403">.NET 5.0</span></span> |

| | <span data-ttu-id="b172e-404">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-404">Setting name</span></span> | <span data-ttu-id="b172e-405">値</span><span class="sxs-lookup"><span data-stu-id="b172e-405">Values</span></span> | <span data-ttu-id="b172e-406">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-406">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-407">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-407">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitLOHPercent` | <span data-ttu-id="b172e-408">"*10 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-408">*decimal value*</span></span> | <span data-ttu-id="b172e-409">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b172e-409">.NET 5.0</span></span> |
| <span data-ttu-id="b172e-410">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-410">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOHPercent` | <span data-ttu-id="b172e-411">"*16 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-411">*hexadecimal value*</span></span> | <span data-ttu-id="b172e-412">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b172e-412">.NET 5.0</span></span> |

| | <span data-ttu-id="b172e-413">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-413">Setting name</span></span> | <span data-ttu-id="b172e-414">値</span><span class="sxs-lookup"><span data-stu-id="b172e-414">Values</span></span> | <span data-ttu-id="b172e-415">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-415">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-416">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-416">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPOHPercent` | <span data-ttu-id="b172e-417">"*10 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-417">*decimal value*</span></span> | <span data-ttu-id="b172e-418">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b172e-418">.NET 5.0</span></span> |
| <span data-ttu-id="b172e-419">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-419">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOHPercent` | <span data-ttu-id="b172e-420">"*16 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-420">*hexadecimal value*</span></span> | <span data-ttu-id="b172e-421">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b172e-421">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="b172e-422">*runtimeconfig.json* でオプションを設定する場合は、10 進値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-422">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="b172e-423">環境変数としてオプションを設定する場合は、16 進値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-423">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="b172e-424">たとえば、ヒープの使用量を 30% に制限する場合、値は JSON ファイルでは 30、環境変数では 0x1E または 1E になります。</span><span class="sxs-lookup"><span data-stu-id="b172e-424">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="high-memory-percent"></a><span data-ttu-id="b172e-425">使用率の高いメモリの割合</span><span class="sxs-lookup"><span data-stu-id="b172e-425">High memory percent</span></span>

<span data-ttu-id="b172e-426">メモリの負荷は、使用されている物理メモリの割合によって示されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-426">Memory load is indicated by the percentage of physical memory in use.</span></span> <span data-ttu-id="b172e-427">既定では、物理メモリの負荷が **90%** に達すると、ガベージコレクションがより積極的に完全に実行され、ガベージ コレクションが圧縮されてページングが回避されるようになります。</span><span class="sxs-lookup"><span data-stu-id="b172e-427">By default, when the physical memory load reaches **90%**, garbage collection becomes more aggressive about doing full, compacting garbage collections to avoid paging.</span></span> <span data-ttu-id="b172e-428">メモリの負荷が 90% 未満の場合、GC によって、フル ガベージ コレクションに対するバックグラウンド コレクションが優先されます。一時停止は短くなりますが、ヒープ サイズの合計はそれほど小さくなりません。</span><span class="sxs-lookup"><span data-stu-id="b172e-428">When memory load is below 90%, GC favors background collections for full garbage collections, which have shorter pauses but don't reduce the total heap size by much.</span></span> <span data-ttu-id="b172e-429">大量のメモリ (80 GB 以上) が搭載されたコンピューターでは、負荷のしきい値は 90% から 97% が既定値です。</span><span class="sxs-lookup"><span data-stu-id="b172e-429">On machines with a significant amount of memory (80GB or more), the default load threshold is between 90% and 97%.</span></span>

<span data-ttu-id="b172e-430">使用率の高いメモリの負荷のしきい値は、`COMPlus_GCHighMemPercent` 環境変数、または `System.GC.HighMemoryPercent` JSON 構成設定によって調整できます。</span><span class="sxs-lookup"><span data-stu-id="b172e-430">The high memory load threshold can be adjusted by the `COMPlus_GCHighMemPercent` environment variable or `System.GC.HighMemoryPercent` JSON configuration setting.</span></span> <span data-ttu-id="b172e-431">ヒープ サイズを制御する場合は、しきい値の調整を検討してください。</span><span class="sxs-lookup"><span data-stu-id="b172e-431">Consider adjusting the threshold if you want to control heap size.</span></span> <span data-ttu-id="b172e-432">たとえば、64 GB のメモリを搭載したコンピューター上で最も優先度の高いプロセスでは、使用可能なメモリが 10% あれば、GC が反応を開始するのが妥当です。</span><span class="sxs-lookup"><span data-stu-id="b172e-432">For example, for the dominant process on a machine with 64GB of memory, it's reasonable for GC to start reacting when there's 10% of memory available.</span></span> <span data-ttu-id="b172e-433">ただし、サイズの小さいプロセス、たとえば 1 GB のメモリしか消費しないプロセスでは、使用可能なメモリが 10% 未満でも、GC を快適に実行できます。</span><span class="sxs-lookup"><span data-stu-id="b172e-433">But for smaller processes, for example, a process that only consumes 1GB of memory, GC can comfortably run with less than 10% of memory available.</span></span> <span data-ttu-id="b172e-434">このような小さいプロセスでは、しきい値を高く設定することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="b172e-434">For these smaller processes, consider setting the threshold higher.</span></span> <span data-ttu-id="b172e-435">一方、大きなプロセスでヒープ サイズを小さくする場合は、使用可能な物理メモリが十分にあったとしても、このしきい値を低くすると、GC がすぐに反応してヒープを圧縮できるため、方法としては効率的です。</span><span class="sxs-lookup"><span data-stu-id="b172e-435">On the other hand, if you want larger processes to have smaller heap sizes (even when there's plenty of physical memory available), lowering this threshold is an effective way for GC to react sooner to compact the heap down.</span></span>

> [!NOTE]
> <span data-ttu-id="b172e-436">コンテナーで実行されているプロセスの場合、GC によって、コンテナーの制限に基づいて物理メモリが考慮されます。</span><span class="sxs-lookup"><span data-stu-id="b172e-436">For processes running in a container, GC considers the physical memory based on the container limit.</span></span>

| | <span data-ttu-id="b172e-437">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-437">Setting name</span></span> | <span data-ttu-id="b172e-438">値</span><span class="sxs-lookup"><span data-stu-id="b172e-438">Values</span></span> | <span data-ttu-id="b172e-439">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-439">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-440">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-440">**runtimeconfig.json**</span></span> | `System.GC.HighMemoryPercent` | <span data-ttu-id="b172e-441">"*10 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-441">*decimal value*</span></span> | <span data-ttu-id="b172e-442">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b172e-442">.NET 5.0</span></span> |
| <span data-ttu-id="b172e-443">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-443">**Environment variable**</span></span> | `COMPlus_GCHighMemPercent` | <span data-ttu-id="b172e-444">"*16 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-444">*hexadecimal value*</span></span> | <span data-ttu-id="b172e-445">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b172e-445">.NET Core 3.0</span></span><br/><span data-ttu-id="b172e-446">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="b172e-446">.NET Framework 4.7.2</span></span> |

> [!TIP]
> <span data-ttu-id="b172e-447">*runtimeconfig.json* でオプションを設定する場合は、10 進値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-447">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="b172e-448">環境変数としてオプションを設定する場合は、16 進値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-448">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="b172e-449">たとえば、使用率の高いメモリのしきい値を 75% に設定するための値は、JSON ファイルに対しては 75、環境変数に対しては 0x4B または 4B となります。</span><span class="sxs-lookup"><span data-stu-id="b172e-449">For example, to set the high memory threshold to 75%, the values would be 75 for the JSON file and 0x4B or 4B for the environment variable.</span></span>

### <a name="retain-vm"></a><span data-ttu-id="b172e-450">VM の保持</span><span class="sxs-lookup"><span data-stu-id="b172e-450">Retain VM</span></span>

- <span data-ttu-id="b172e-451">削除する必要があるセグメントを、後で使用するためにスタンバイ リストに配置するか、解放してオペレーティング システム (OS) に戻すかを構成します。</span><span class="sxs-lookup"><span data-stu-id="b172e-451">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="b172e-452">既定:セグメントを解放してオペレーティング システムに戻します。</span><span class="sxs-lookup"><span data-stu-id="b172e-452">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="b172e-453">これは、値を `false` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="b172e-453">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="b172e-454">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-454">Setting name</span></span> | <span data-ttu-id="b172e-455">値</span><span class="sxs-lookup"><span data-stu-id="b172e-455">Values</span></span> | <span data-ttu-id="b172e-456">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-456">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-457">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-457">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="b172e-458">`false` -OS に解放する</span><span class="sxs-lookup"><span data-stu-id="b172e-458">`false` - release to OS</span></span><br/><span data-ttu-id="b172e-459">`true` - スタンバイに配置する</span><span class="sxs-lookup"><span data-stu-id="b172e-459">`true` - put on standby</span></span> | <span data-ttu-id="b172e-460">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="b172e-460">.NET Core 1.0</span></span> |
| <span data-ttu-id="b172e-461">**MSBuild のプロパティ**</span><span class="sxs-lookup"><span data-stu-id="b172e-461">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="b172e-462">`false` -OS に解放する</span><span class="sxs-lookup"><span data-stu-id="b172e-462">`false` - release to OS</span></span><br/><span data-ttu-id="b172e-463">`true` - スタンバイに配置する</span><span class="sxs-lookup"><span data-stu-id="b172e-463">`true` - put on standby</span></span> | <span data-ttu-id="b172e-464">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="b172e-464">.NET Core 1.0</span></span> |
| <span data-ttu-id="b172e-465">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-465">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="b172e-466">`0` -OS に解放する</span><span class="sxs-lookup"><span data-stu-id="b172e-466">`0` - release to OS</span></span><br/><span data-ttu-id="b172e-467">`1` - スタンバイに配置する</span><span class="sxs-lookup"><span data-stu-id="b172e-467">`1` - put on standby</span></span> | <span data-ttu-id="b172e-468">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="b172e-468">.NET Core 1.0</span></span> |

#### <a name="examples"></a><span data-ttu-id="b172e-469">使用例</span><span class="sxs-lookup"><span data-stu-id="b172e-469">Examples</span></span>

<span data-ttu-id="b172e-470">*runtimeconfig.json* ファイル:</span><span class="sxs-lookup"><span data-stu-id="b172e-470">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="b172e-471">プロジェクト ファイル:</span><span class="sxs-lookup"><span data-stu-id="b172e-471">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="b172e-472">大きいページ</span><span class="sxs-lookup"><span data-stu-id="b172e-472">Large pages</span></span>

- <span data-ttu-id="b172e-473">ヒープのハード制限が設定されている場合に、大きいページを使用する必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-473">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="b172e-474">既定:ヒープのハード制限が設定されている場合は、大きいページを使用しません。</span><span class="sxs-lookup"><span data-stu-id="b172e-474">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="b172e-475">これは、値を `0` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="b172e-475">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="b172e-476">これは試験段階の設定です。</span><span class="sxs-lookup"><span data-stu-id="b172e-476">This is an experimental setting.</span></span>

| | <span data-ttu-id="b172e-477">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-477">Setting name</span></span> | <span data-ttu-id="b172e-478">値</span><span class="sxs-lookup"><span data-stu-id="b172e-478">Values</span></span> | <span data-ttu-id="b172e-479">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-479">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-480">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-480">**runtimeconfig.json**</span></span> | <span data-ttu-id="b172e-481">N/A</span><span class="sxs-lookup"><span data-stu-id="b172e-481">N/A</span></span> | <span data-ttu-id="b172e-482">該当なし</span><span class="sxs-lookup"><span data-stu-id="b172e-482">N/A</span></span> | <span data-ttu-id="b172e-483">N/A</span><span class="sxs-lookup"><span data-stu-id="b172e-483">N/A</span></span> |
| <span data-ttu-id="b172e-484">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-484">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="b172e-485">`0` - 無効</span><span class="sxs-lookup"><span data-stu-id="b172e-485">`0` - disabled</span></span><br/><span data-ttu-id="b172e-486">`1` - 有効</span><span class="sxs-lookup"><span data-stu-id="b172e-486">`1` - enabled</span></span> | <span data-ttu-id="b172e-487">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b172e-487">.NET Core 3.0</span></span> |

## <a name="allow-large-objects"></a><span data-ttu-id="b172e-488">大きなオブジェクトを許可する</span><span class="sxs-lookup"><span data-stu-id="b172e-488">Allow large objects</span></span>

- <span data-ttu-id="b172e-489">合計サイズが 2 ギガバイト (GB) を超える配列に対して、64 ビット プラットフォームでのガベージ コレクター サポートを構成します。</span><span class="sxs-lookup"><span data-stu-id="b172e-489">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="b172e-490">既定:GC では、2 GB を超える配列がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b172e-490">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="b172e-491">これは、値を `1` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="b172e-491">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="b172e-492">このオプションは、将来のバージョンの .NET で廃止される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b172e-492">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="b172e-493">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-493">Setting name</span></span> | <span data-ttu-id="b172e-494">値</span><span class="sxs-lookup"><span data-stu-id="b172e-494">Values</span></span> | <span data-ttu-id="b172e-495">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-495">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-496">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-496">**runtimeconfig.json**</span></span> | <span data-ttu-id="b172e-497">N/A</span><span class="sxs-lookup"><span data-stu-id="b172e-497">N/A</span></span> | <span data-ttu-id="b172e-498">該当なし</span><span class="sxs-lookup"><span data-stu-id="b172e-498">N/A</span></span> | <span data-ttu-id="b172e-499">N/A</span><span class="sxs-lookup"><span data-stu-id="b172e-499">N/A</span></span> |
| <span data-ttu-id="b172e-500">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-500">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="b172e-501">`1` - 有効</span><span class="sxs-lookup"><span data-stu-id="b172e-501">`1` - enabled</span></span><br/> <span data-ttu-id="b172e-502">`0` - 無効</span><span class="sxs-lookup"><span data-stu-id="b172e-502">`0` - disabled</span></span> | <span data-ttu-id="b172e-503">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="b172e-503">.NET Core 1.0</span></span> |
| <span data-ttu-id="b172e-504">**.NET Framework 用の app.config**</span><span class="sxs-lookup"><span data-stu-id="b172e-504">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="b172e-505">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="b172e-505">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="b172e-506">`1` - 有効</span><span class="sxs-lookup"><span data-stu-id="b172e-506">`1` - enabled</span></span><br/> <span data-ttu-id="b172e-507">`0` - 無効</span><span class="sxs-lookup"><span data-stu-id="b172e-507">`0` - disabled</span></span> | <span data-ttu-id="b172e-508">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="b172e-508">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="b172e-509">大きなオブジェクト ヒープのしきい値</span><span class="sxs-lookup"><span data-stu-id="b172e-509">Large object heap threshold</span></span>

- <span data-ttu-id="b172e-510">オブジェクトが大きなオブジェクト ヒープ (LOH) に移る原因となる、しきい値のサイズ (バイト単位) を指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-510">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="b172e-511">既定のしきい値は 85,000 バイトです。</span><span class="sxs-lookup"><span data-stu-id="b172e-511">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="b172e-512">指定する値は、既定のしきい値より大きくする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b172e-512">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="b172e-513">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-513">Setting name</span></span> | <span data-ttu-id="b172e-514">値</span><span class="sxs-lookup"><span data-stu-id="b172e-514">Values</span></span> | <span data-ttu-id="b172e-515">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-515">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-516">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-516">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="b172e-517">"*10 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-517">*decimal value*</span></span> | <span data-ttu-id="b172e-518">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="b172e-518">.NET Core 1.0</span></span> |
| <span data-ttu-id="b172e-519">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-519">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="b172e-520">"*16 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-520">*hexadecimal value*</span></span> | <span data-ttu-id="b172e-521">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="b172e-521">.NET Core 1.0</span></span> |
| <span data-ttu-id="b172e-522">**.NET Framework 用の app.config**</span><span class="sxs-lookup"><span data-stu-id="b172e-522">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="b172e-523">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="b172e-523">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="b172e-524">"*10 進値*"</span><span class="sxs-lookup"><span data-stu-id="b172e-524">*decimal value*</span></span> | <span data-ttu-id="b172e-525">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="b172e-525">.NET Framework 4.8</span></span> |

<span data-ttu-id="b172e-526">例:</span><span class="sxs-lookup"><span data-stu-id="b172e-526">Example:</span></span>

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
> <span data-ttu-id="b172e-527">*runtimeconfig.json* でオプションを設定する場合は、10 進値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-527">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="b172e-528">環境変数としてオプションを設定する場合は、16 進値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-528">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="b172e-529">たとえば、しきい値のサイズを 120,000 バイトに設定する場合、値は JSON ファイルでは 120000、環境変数では 0x1D4C0 または 1D4C0 になります。</span><span class="sxs-lookup"><span data-stu-id="b172e-529">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="b172e-530">スタンドアロン GC</span><span class="sxs-lookup"><span data-stu-id="b172e-530">Standalone GC</span></span>

- <span data-ttu-id="b172e-531">ランタイムで読み込む対象となる、ガベージ コレクターを含むライブラリへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="b172e-531">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="b172e-532">詳細については、「[スタンドアロン GC ローダーの設計](https://github.com/dotnet/runtime/blob/main/docs/design/features/standalone-gc-loading.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b172e-532">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/main/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="b172e-533">設定の名前</span><span class="sxs-lookup"><span data-stu-id="b172e-533">Setting name</span></span> | <span data-ttu-id="b172e-534">値</span><span class="sxs-lookup"><span data-stu-id="b172e-534">Values</span></span> | <span data-ttu-id="b172e-535">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b172e-535">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="b172e-536">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="b172e-536">**runtimeconfig.json**</span></span> | <span data-ttu-id="b172e-537">N/A</span><span class="sxs-lookup"><span data-stu-id="b172e-537">N/A</span></span> | <span data-ttu-id="b172e-538">該当なし</span><span class="sxs-lookup"><span data-stu-id="b172e-538">N/A</span></span> | <span data-ttu-id="b172e-539">N/A</span><span class="sxs-lookup"><span data-stu-id="b172e-539">N/A</span></span> |
| <span data-ttu-id="b172e-540">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="b172e-540">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="b172e-541">*string_path*</span><span class="sxs-lookup"><span data-stu-id="b172e-541">*string_path*</span></span> | <span data-ttu-id="b172e-542">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b172e-542">.NET Core 2.0</span></span> |
