---
title: デバッグとプロファイルの構成設定
description: .NET Core アプリのデバッグとプロファイルを構成するランタイム設定について説明します。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: dd96862582f13adc19df7572b1865800b18d9954
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875019"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="774a5-103">デバッグとプロファイルのランタイム構成オプション</span><span class="sxs-lookup"><span data-stu-id="774a5-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="774a5-104">診断を有効化する</span><span class="sxs-lookup"><span data-stu-id="774a5-104">Enable diagnostics</span></span>

- <span data-ttu-id="774a5-105">デバッガー、プロファイラー、EventPipe 診断を有効にするか、または無効にするかを構成します。</span><span class="sxs-lookup"><span data-stu-id="774a5-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="774a5-106">この設定を省略すると、診断は有効になります。</span><span class="sxs-lookup"><span data-stu-id="774a5-106">If you omit this setting, diagnostics are enabled.</span></span> <span data-ttu-id="774a5-107">これは、値を `1` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="774a5-107">This is equivalent to setting the value to `1`.</span></span>

| | <span data-ttu-id="774a5-108">設定の名前</span><span class="sxs-lookup"><span data-stu-id="774a5-108">Setting name</span></span> | <span data-ttu-id="774a5-109">値</span><span class="sxs-lookup"><span data-stu-id="774a5-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="774a5-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="774a5-110">**runtimeconfig.json**</span></span> | <span data-ttu-id="774a5-111">N/A</span><span class="sxs-lookup"><span data-stu-id="774a5-111">N/A</span></span> | <span data-ttu-id="774a5-112">N/A</span><span class="sxs-lookup"><span data-stu-id="774a5-112">N/A</span></span> |
| <span data-ttu-id="774a5-113">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="774a5-113">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="774a5-114">`1` - 有効</span><span class="sxs-lookup"><span data-stu-id="774a5-114">`1` - enabled</span></span><br/><span data-ttu-id="774a5-115">`0` - 無効</span><span class="sxs-lookup"><span data-stu-id="774a5-115">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="774a5-116">プロファイルを有効にする</span><span class="sxs-lookup"><span data-stu-id="774a5-116">Enable profiling</span></span>

- <span data-ttu-id="774a5-117">現在実行中のプロセスに対してプロファイルを有効にするかどうかを構成します。</span><span class="sxs-lookup"><span data-stu-id="774a5-117">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="774a5-118">この設定を省略すると、プロファイルは無効になります。</span><span class="sxs-lookup"><span data-stu-id="774a5-118">If you omit this setting, profiling is disabled.</span></span> <span data-ttu-id="774a5-119">これは、値を `0` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="774a5-119">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="774a5-120">設定の名前</span><span class="sxs-lookup"><span data-stu-id="774a5-120">Setting name</span></span> | <span data-ttu-id="774a5-121">値</span><span class="sxs-lookup"><span data-stu-id="774a5-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="774a5-122">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="774a5-122">**runtimeconfig.json**</span></span> | <span data-ttu-id="774a5-123">N/A</span><span class="sxs-lookup"><span data-stu-id="774a5-123">N/A</span></span> | <span data-ttu-id="774a5-124">N/A</span><span class="sxs-lookup"><span data-stu-id="774a5-124">N/A</span></span> |
| <span data-ttu-id="774a5-125">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="774a5-125">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="774a5-126">`0` - 無効</span><span class="sxs-lookup"><span data-stu-id="774a5-126">`0` - disabled</span></span><br/><span data-ttu-id="774a5-127">`1` - 有効</span><span class="sxs-lookup"><span data-stu-id="774a5-127">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="774a5-128">プロファイラー GUID</span><span class="sxs-lookup"><span data-stu-id="774a5-128">Profiler GUID</span></span>

- <span data-ttu-id="774a5-129">現在実行中のプロセスに読み込むプロファイラーの GUID を指定します。</span><span class="sxs-lookup"><span data-stu-id="774a5-129">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="774a5-130">設定の名前</span><span class="sxs-lookup"><span data-stu-id="774a5-130">Setting name</span></span> | <span data-ttu-id="774a5-131">値</span><span class="sxs-lookup"><span data-stu-id="774a5-131">Values</span></span> |
| - | - | - |
| <span data-ttu-id="774a5-132">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="774a5-132">**runtimeconfig.json**</span></span> | <span data-ttu-id="774a5-133">N/A</span><span class="sxs-lookup"><span data-stu-id="774a5-133">N/A</span></span> | <span data-ttu-id="774a5-134">N/A</span><span class="sxs-lookup"><span data-stu-id="774a5-134">N/A</span></span> |
| <span data-ttu-id="774a5-135">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="774a5-135">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="774a5-136">*string-guid*</span><span class="sxs-lookup"><span data-stu-id="774a5-136">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="774a5-137">プロファイラーの場所</span><span class="sxs-lookup"><span data-stu-id="774a5-137">Profiler location</span></span>

- <span data-ttu-id="774a5-138">現在実行中のプロセス (32 ビット プロセスまたは 64 ビット プロセス) に読み込むプロファイラー DLL へのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="774a5-138">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="774a5-139">複数の変数が設定されている場合、ビット固有の変数が優先されます。</span><span class="sxs-lookup"><span data-stu-id="774a5-139">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="774a5-140">これらは、ロードするプロファイラーのビットを指定します。</span><span class="sxs-lookup"><span data-stu-id="774a5-140">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="774a5-141">詳細については、「[プロファイラー ライブラリを検索する](https://github.com/dotnet/runtime/blob/main/docs/design/coreclr/profiling/Profiler%20Loading.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774a5-141">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/main/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="774a5-142">設定の名前</span><span class="sxs-lookup"><span data-stu-id="774a5-142">Setting name</span></span> | <span data-ttu-id="774a5-143">値</span><span class="sxs-lookup"><span data-stu-id="774a5-143">Values</span></span> |
| - | - | - |
| <span data-ttu-id="774a5-144">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="774a5-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="774a5-145">*string-path*</span><span class="sxs-lookup"><span data-stu-id="774a5-145">*string-path*</span></span> |
| <span data-ttu-id="774a5-146">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="774a5-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="774a5-147">*string-path*</span><span class="sxs-lookup"><span data-stu-id="774a5-147">*string-path*</span></span> |
| <span data-ttu-id="774a5-148">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="774a5-148">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="774a5-149">*string-path*</span><span class="sxs-lookup"><span data-stu-id="774a5-149">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="774a5-150">パフォーマンス マップの作成</span><span class="sxs-lookup"><span data-stu-id="774a5-150">Write perf map</span></span>

- <span data-ttu-id="774a5-151">Linux システムでの */tmp/perf-$pid.map* の作成を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="774a5-151">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="774a5-152">この設定を省略すると、パフォーマンス マップの作成は無効になります。</span><span class="sxs-lookup"><span data-stu-id="774a5-152">If you omit this setting, writing the perf map is disabled.</span></span> <span data-ttu-id="774a5-153">これは、値を `0` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="774a5-153">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="774a5-154">設定の名前</span><span class="sxs-lookup"><span data-stu-id="774a5-154">Setting name</span></span> | <span data-ttu-id="774a5-155">値</span><span class="sxs-lookup"><span data-stu-id="774a5-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="774a5-156">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="774a5-156">**runtimeconfig.json**</span></span> | <span data-ttu-id="774a5-157">N/A</span><span class="sxs-lookup"><span data-stu-id="774a5-157">N/A</span></span> | <span data-ttu-id="774a5-158">N/A</span><span class="sxs-lookup"><span data-stu-id="774a5-158">N/A</span></span> |
| <span data-ttu-id="774a5-159">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="774a5-159">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="774a5-160">`0` - 無効</span><span class="sxs-lookup"><span data-stu-id="774a5-160">`0` - disabled</span></span><br/><span data-ttu-id="774a5-161">`1` - 有効</span><span class="sxs-lookup"><span data-stu-id="774a5-161">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="774a5-162">パフォーマンス ログのマーカー</span><span class="sxs-lookup"><span data-stu-id="774a5-162">Perf log markers</span></span>

- <span data-ttu-id="774a5-163">指定したシグナルのパフォーマンス ログでのマーカーとしての受け入れおよび無視を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="774a5-163">Enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="774a5-164">この設定を省略すると、指定したシグナルは無視されません。</span><span class="sxs-lookup"><span data-stu-id="774a5-164">If you omit this setting, the specified signal is not ignored.</span></span> <span data-ttu-id="774a5-165">これは、値を `0` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="774a5-165">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="774a5-166">設定の名前</span><span class="sxs-lookup"><span data-stu-id="774a5-166">Setting name</span></span> | <span data-ttu-id="774a5-167">値</span><span class="sxs-lookup"><span data-stu-id="774a5-167">Values</span></span> |
| - | - | - |
| <span data-ttu-id="774a5-168">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="774a5-168">**runtimeconfig.json**</span></span> | <span data-ttu-id="774a5-169">N/A</span><span class="sxs-lookup"><span data-stu-id="774a5-169">N/A</span></span> | <span data-ttu-id="774a5-170">N/A</span><span class="sxs-lookup"><span data-stu-id="774a5-170">N/A</span></span> |
| <span data-ttu-id="774a5-171">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="774a5-171">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="774a5-172">`0` - 無効</span><span class="sxs-lookup"><span data-stu-id="774a5-172">`0` - disabled</span></span><br/><span data-ttu-id="774a5-173">`1` - 有効</span><span class="sxs-lookup"><span data-stu-id="774a5-173">`1` - enabled</span></span> |

> [!NOTE]
> <span data-ttu-id="774a5-174">この設定は、[COMPlus_PerfMapEnabled](#write-perf-map) が省略されるか、または `0` (無効) に設定されている場合は、無視されます。</span><span class="sxs-lookup"><span data-stu-id="774a5-174">This setting is ignored if [COMPlus_PerfMapEnabled](#write-perf-map) is omitted or set to `0` (that is, disabled).</span></span>
