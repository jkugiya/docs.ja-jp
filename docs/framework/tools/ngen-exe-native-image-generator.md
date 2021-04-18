---
title: Ngen.exe (ネイティブ イメージ ジェネレーター)
description: Ngen.exe (ネイティブ イメージ ジェネレーター) を確認します。 ネイティブ イメージを作成してローカルのネイティブ イメージ キャッシュにインストールすることで、マネージド アプリケーションのパフォーマンスを向上させます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Native Image Generator
- images [.NET Framework], native
- side-by-side execution, native images
- assemblies [.NET Framework], native image
- Ngen.exe
- native image generation
- native image cache
- publisher policy applied for native images
- invalid images
- BypassNGenAttribute
- System.Runtime.BypassNGenAttribute
ms.assetid: 44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66
ms.openlocfilehash: 480d5172a7ccec0c58b5b615226c836a358cb603
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494702"
---
# <a name="ngenexe-native-image-generator"></a><span data-ttu-id="a141b-104">Ngen.exe (ネイティブ イメージ ジェネレーター)</span><span class="sxs-lookup"><span data-stu-id="a141b-104">Ngen.exe (Native Image Generator)</span></span>

<span data-ttu-id="a141b-105">ネイティブ イメージ ジェネレーター (Ngen.exe) は、マネージド アプリケーションのパフォーマンスを向上するツールです。</span><span class="sxs-lookup"><span data-stu-id="a141b-105">The Native Image Generator (Ngen.exe) is a tool that improves the performance of managed applications.</span></span> <span data-ttu-id="a141b-106">Ngen.exe は、コンパイルされたプロセッサ固有のマシン コードを含むファイルであるネイティブ イメージを作成してローカル コンピューターのネイティブ イメージ キャッシュにインストールします。</span><span class="sxs-lookup"><span data-stu-id="a141b-106">Ngen.exe creates native images, which are files containing compiled processor-specific machine code, and installs them into the native image cache on the local computer.</span></span> <span data-ttu-id="a141b-107">ランタイムは、Just-In-Time (JIT) コンパイラを使用してオリジナルのアセンブリをコンパイルする代わりに、キャッシュにあるネイティブ イメージを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-107">The runtime can use native images from the cache instead of using the just-in-time (JIT) compiler to compile the original assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="a141b-108">Ngen.exe によって、.NET Framework のみをターゲットとするアセンブリのネイティブ イメージがコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="a141b-108">Ngen.exe compiles native images for assemblies that target the .NET Framework only.</span></span> <span data-ttu-id="a141b-109">.Net Core 用の同等のネイティブ イメージ ジェネレーターは、[CrossGen](https://github.com/dotnet/runtime/blob/main/docs/workflow/building/coreclr/crossgen.md) です。</span><span class="sxs-lookup"><span data-stu-id="a141b-109">The equivalent native image generator for .NET Core is [CrossGen](https://github.com/dotnet/runtime/blob/main/docs/workflow/building/coreclr/crossgen.md).</span></span>

<span data-ttu-id="a141b-110">.NET Framework 4 では、次の変更が Ngen.exe に加えられました。</span><span class="sxs-lookup"><span data-stu-id="a141b-110">Changes to Ngen.exe in the .NET Framework 4:</span></span>

- <span data-ttu-id="a141b-111">Ngen.exe によるアセンブリのコンパイルが完全信頼で行われるようになり、コード アクセス セキュリティ (CAS: Code Access Security) ポリシーが評価されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a141b-111">Ngen.exe now compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>

- <span data-ttu-id="a141b-112">Ngen.exe で生成されたネイティブ イメージを、部分信頼で実行されているアプリケーションに読み込むことができなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a141b-112">Native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span>

<span data-ttu-id="a141b-113">.NET Framework Version 2.0 では、次の変更が Ngen.exe に加えられました。</span><span class="sxs-lookup"><span data-stu-id="a141b-113">Changes to Ngen.exe in the .NET Framework version 2.0:</span></span>

- <span data-ttu-id="a141b-114">アセンブリと共にその依存関係もインストールされることで、Ngen.exe の構文が簡略化されました。</span><span class="sxs-lookup"><span data-stu-id="a141b-114">Installing an assembly also installs its dependencies, simplifying the syntax of Ngen.exe.</span></span>

- <span data-ttu-id="a141b-115">ネイティブ イメージをアプリケーション ドメイン間で共有できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a141b-115">Native images can now be shared across application domains.</span></span>

- <span data-ttu-id="a141b-116">新しいアクションの `update` は、無効になっていたイメージを再作成します。</span><span class="sxs-lookup"><span data-stu-id="a141b-116">A new action, `update`, re-creates images that have been invalidated.</span></span>

- <span data-ttu-id="a141b-117">アクションの実行は、コンピューターのアイドル時間を使用してイメージを生成してインストールするサービスによって遅らせることができます。</span><span class="sxs-lookup"><span data-stu-id="a141b-117">Actions can be deferred for execution by a service that uses idle time on the computer to generate and install images.</span></span>

- <span data-ttu-id="a141b-118">イメージを無効化する原因の一部が解決されました。</span><span class="sxs-lookup"><span data-stu-id="a141b-118">Some causes of image invalidation have been eliminated.</span></span>

<span data-ttu-id="a141b-119">Windows 8 の場合、「[ネイティブ イメージ タスク](#native-image-task)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a141b-119">On Windows 8, see [Native Image Task](#native-image-task).</span></span>

<span data-ttu-id="a141b-120">Ngen.exe とネイティブ イメージ サービスの使用に関する追加情報については、「[ネイティブ イメージ サービス](#native-image-service)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a141b-120">For additional information on using Ngen.exe and the native image service, see [Native Image Service](#native-image-service).</span></span>

> [!NOTE]
> <span data-ttu-id="a141b-121">.NET Framework バージョン 1.0 とバージョン 1.1 の Ngen.exe 構文は、「[ネイティブ イメージ ジェネレーター (Ngen.exe) のレガシ構文](/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100))」に記されています。</span><span class="sxs-lookup"><span data-stu-id="a141b-121">Ngen.exe syntax for versions 1.0 and 1.1 of the .NET Framework can be found in [Native Image Generator (Ngen.exe) Legacy Syntax](/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).</span></span>

<span data-ttu-id="a141b-122">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a141b-122">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="a141b-123">ツールを実行するには、[、Visual Studio 開発者コマンド プロンプトまたは Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) を使用します。</span><span class="sxs-lookup"><span data-stu-id="a141b-123">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>

<span data-ttu-id="a141b-124">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="a141b-124">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="a141b-125">構文</span><span class="sxs-lookup"><span data-stu-id="a141b-125">Syntax</span></span>

```console
ngen action [options]
```

```console
ngen /? | /help
```

## <a name="actions"></a><span data-ttu-id="a141b-126">アクション</span><span class="sxs-lookup"><span data-stu-id="a141b-126">Actions</span></span>

<span data-ttu-id="a141b-127">各 `action` の構文を示す表を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a141b-127">The following table shows the syntax of each `action`.</span></span> <span data-ttu-id="a141b-128">`action` の各部分の説明については、「[引数](#ArgumentTable)」、「[優先順位](#PriorityTable)」、「[シナリオ](#ScenarioTable)」、および「[構成](#ConfigTable)」の各表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a141b-128">For descriptions of the individual parts of an `action`, see the [Arguments](#ArgumentTable), [Priority Levels](#PriorityTable), [Scenarios](#ScenarioTable), and [Config](#ConfigTable) tables.</span></span> <span data-ttu-id="a141b-129">`options` およびヘルプ スイッチについては、「[オプション](#OptionTable)」の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a141b-129">The [Options](#OptionTable) table describes the `options` and the help switches.</span></span>

|<span data-ttu-id="a141b-130">アクション</span><span class="sxs-lookup"><span data-stu-id="a141b-130">Action</span></span>|<span data-ttu-id="a141b-131">説明</span><span class="sxs-lookup"><span data-stu-id="a141b-131">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="a141b-132">`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span><span class="sxs-lookup"><span data-stu-id="a141b-132">`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span></span>|<span data-ttu-id="a141b-133">アセンブリおよびそれに依存する項目のネイティブ イメージを生成してネイティブ イメージ キャッシュにインストールします。</span><span class="sxs-lookup"><span data-stu-id="a141b-133">Generate native images for an assembly and its dependencies and install the images in the native image cache.</span></span><br /><br /> <span data-ttu-id="a141b-134">`/queue` を指定すると、アクションはネイティブ イメージ サービスのキューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="a141b-134">If `/queue` is specified, the action is queued for the native image service.</span></span> <span data-ttu-id="a141b-135">既定の優先順位は 3 です。</span><span class="sxs-lookup"><span data-stu-id="a141b-135">The default priority is 3.</span></span> <span data-ttu-id="a141b-136">「[優先順位](#PriorityTable)」の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a141b-136">See the [Priority Levels](#PriorityTable) table.</span></span>|
|<span data-ttu-id="a141b-137">`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span><span class="sxs-lookup"><span data-stu-id="a141b-137">`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span></span>|<span data-ttu-id="a141b-138">アセンブリのネイティブ イメージとその依存関係をネイティブ イメージ キャッシュから削除します。</span><span class="sxs-lookup"><span data-stu-id="a141b-138">Delete the native images of an assembly and its dependencies from the native image cache.</span></span><br /><br /> <span data-ttu-id="a141b-139">単一のイメージとその依存関係をアンインストールするには、そのイメージをインストールしたときと同じコマンド ライン引数を使用します。</span><span class="sxs-lookup"><span data-stu-id="a141b-139">To uninstall a single image and its dependencies, use the same command-line arguments that were used to install the image.</span></span> <span data-ttu-id="a141b-140">**注:** .NET Framework 4 以降では、アクション `uninstall` \* はサポートされなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a141b-140">**Note:**  Starting with the .NET Framework 4, the action `uninstall` \* is no longer supported.</span></span>|
|<span data-ttu-id="a141b-141">`update` [`/queue`]</span><span class="sxs-lookup"><span data-stu-id="a141b-141">`update` [`/queue`]</span></span>|<span data-ttu-id="a141b-142">無効になったネイティブ イメージを更新します。</span><span class="sxs-lookup"><span data-stu-id="a141b-142">Update native images that have become invalid.</span></span><br /><br /> <span data-ttu-id="a141b-143">`/queue` を指定すると、更新はネイティブ イメージ サービスのキューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="a141b-143">If `/queue` is specified, the updates are queued for the native image service.</span></span> <span data-ttu-id="a141b-144">更新は常に優先順位 3 でスケジュールされるため、コンピューターがアイドル状態のときに実行されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-144">Updates are always scheduled at priority 3, so they run when the computer is idle.</span></span>|
|<span data-ttu-id="a141b-145">`display` [`assemblyName` &#124; `assemblyPath`]</span><span class="sxs-lookup"><span data-stu-id="a141b-145">`display` [`assemblyName` &#124; `assemblyPath`]</span></span>|<span data-ttu-id="a141b-146">アセンブリのネイティブ イメージとその依存関係の状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="a141b-146">Display the state of the native images for an assembly and its dependencies.</span></span><br /><br /> <span data-ttu-id="a141b-147">引数を指定しなければ、ネイティブ イメージ キャッシュのすべての内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-147">If no argument is supplied, everything in the native image cache is displayed.</span></span>|
|<span data-ttu-id="a141b-148">`executeQueuedItems` [<code>1&#124;2&#124;3</code>]</span><span class="sxs-lookup"><span data-stu-id="a141b-148">`executeQueuedItems` [<code>1&#124;2&#124;3</code>]</span></span><br /><br /> <span data-ttu-id="a141b-149">\- または -</span><span class="sxs-lookup"><span data-stu-id="a141b-149">-or-</span></span><br /><br /> <span data-ttu-id="a141b-150">`eqi` [1&#124;2&#124;3]</span><span class="sxs-lookup"><span data-stu-id="a141b-150">`eqi` [1&#124;2&#124;3]</span></span>|<span data-ttu-id="a141b-151">キューに置かれているコンパイル ジョブを実行します。</span><span class="sxs-lookup"><span data-stu-id="a141b-151">Execute queued compilation jobs.</span></span><br /><br /> <span data-ttu-id="a141b-152">優先順位を指定すると、優先順位が高いかまたは同じコンパイル ジョブが実行されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-152">If a priority is specified, compilation jobs with greater or equal priority are executed.</span></span> <span data-ttu-id="a141b-153">優先順位を指定しなければ、キューに置かれているすべてのコンパイル ジョブが実行されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-153">If no priority is specified, all queued compilation jobs are executed.</span></span>|
|<span data-ttu-id="a141b-154">`queue` {`pause` &#124; `continue` &#124; `status`}</span><span class="sxs-lookup"><span data-stu-id="a141b-154">`queue` {`pause` &#124; `continue` &#124; `status`}</span></span>|<span data-ttu-id="a141b-155">ネイティブ イメージ サービスを一時停止するか、停止しているサービスを再開するか、またはサービスの状態を照会します。</span><span class="sxs-lookup"><span data-stu-id="a141b-155">Pause the native image service, allow the paused service to continue, or query the status of the service.</span></span>|

<a name="ArgumentTable"></a>

## <a name="arguments"></a><span data-ttu-id="a141b-156">引数</span><span class="sxs-lookup"><span data-stu-id="a141b-156">Arguments</span></span>

|<span data-ttu-id="a141b-157">引数</span><span class="sxs-lookup"><span data-stu-id="a141b-157">Argument</span></span>|<span data-ttu-id="a141b-158">説明</span><span class="sxs-lookup"><span data-stu-id="a141b-158">Description</span></span>|
|--------------|-----------------|
|`assemblyName`|<span data-ttu-id="a141b-159">アセンブリの完全な表示名。</span><span class="sxs-lookup"><span data-stu-id="a141b-159">The full display name of the assembly.</span></span> <span data-ttu-id="a141b-160">たとえば、`"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"` のようにします。</span><span class="sxs-lookup"><span data-stu-id="a141b-160">For example, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span></span> <span data-ttu-id="a141b-161">**注:** `myAssembly` アクションおよび `display` アクションに対しては、`uninstall` などのように部分的なアセンブリ名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-161">**Note:**  You can supply a partial assembly name, such as `myAssembly`, for the `display` and `uninstall` actions.</span></span> <br /><br /> <span data-ttu-id="a141b-162">Ngen.exe の各コマンド ラインに指定できるアセンブリは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="a141b-162">Only one assembly can be specified per Ngen.exe command line.</span></span>|
|`assemblyPath`|<span data-ttu-id="a141b-163">アセンブリの明示的なパスを返します。</span><span class="sxs-lookup"><span data-stu-id="a141b-163">The explicit path of the assembly.</span></span> <span data-ttu-id="a141b-164">フル パスまたは相対パスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-164">You can specify a full or relative path.</span></span><br /><br /> <span data-ttu-id="a141b-165">パスを指定せずにファイル名を指定する場合、アセンブリは現在のディレクトリに存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-165">If you specify a file name without a path, the assembly must be located in the current directory.</span></span><br /><br /> <span data-ttu-id="a141b-166">Ngen.exe の各コマンド ラインに指定できるアセンブリは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="a141b-166">Only one assembly can be specified per Ngen.exe command line.</span></span>|

<a name="PriorityTable"></a>

## <a name="priority-levels"></a><span data-ttu-id="a141b-167">優先順位</span><span class="sxs-lookup"><span data-stu-id="a141b-167">Priority Levels</span></span>

|<span data-ttu-id="a141b-168">優先度</span><span class="sxs-lookup"><span data-stu-id="a141b-168">Priority</span></span>|<span data-ttu-id="a141b-169">説明</span><span class="sxs-lookup"><span data-stu-id="a141b-169">Description</span></span>|
|--------------|-----------------|
|`1`|<span data-ttu-id="a141b-170">ネイティブ イメージが生成され、アイドル時間まで待たずに直ちにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a141b-170">Native images are generated and installed immediately, without waiting for idle time.</span></span>|
|`2`|<span data-ttu-id="a141b-171">ネイティブ イメージが生成され、アイドル時間まで待たずにインストールされますが、優先順位 1 のすべてのアクション (およびその依存関係) が完了した後にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a141b-171">Native images are generated and installed without waiting for idle time, but after all priority 1 actions (and their dependencies) have completed.</span></span>|
|`3`|<span data-ttu-id="a141b-172">コンピューターがアイドル状態になったことをネイティブ イメージ サービスが検出するとネイティブ イメージがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a141b-172">Native images are installed when the native image service detects that the computer is idle.</span></span> <span data-ttu-id="a141b-173">「[ネイティブ イメージ サービス](#native-image-service)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a141b-173">See [Native Image Service](#native-image-service).</span></span>|

<a name="ScenarioTable"></a>

## <a name="scenarios"></a><span data-ttu-id="a141b-174">シナリオ</span><span class="sxs-lookup"><span data-stu-id="a141b-174">Scenarios</span></span>

|<span data-ttu-id="a141b-175">シナリオ</span><span class="sxs-lookup"><span data-stu-id="a141b-175">Scenario</span></span>|<span data-ttu-id="a141b-176">説明</span><span class="sxs-lookup"><span data-stu-id="a141b-176">Description</span></span>|
|--------------|-----------------|
|`/Debug`|<span data-ttu-id="a141b-177">デバッガーで使用できるネイティブ イメージを生成します。</span><span class="sxs-lookup"><span data-stu-id="a141b-177">Generate native images that can be used under a debugger.</span></span>|
|`/Profile`|<span data-ttu-id="a141b-178">プロファイラーで使用できるネイティブ イメージを生成します。</span><span class="sxs-lookup"><span data-stu-id="a141b-178">Generate native images that can be used under a profiler.</span></span>|
|`/NoDependencies`|<span data-ttu-id="a141b-179">指定されたシナリオのオプションに必要なネイティブ イメージの最小数を生成します。</span><span class="sxs-lookup"><span data-stu-id="a141b-179">Generate the minimum number of native images required by the specified scenario options.</span></span>|

<a name="ConfigTable"></a>

## <a name="config"></a><span data-ttu-id="a141b-180">構成</span><span class="sxs-lookup"><span data-stu-id="a141b-180">Config</span></span>

|<span data-ttu-id="a141b-181">構成</span><span class="sxs-lookup"><span data-stu-id="a141b-181">Configuration</span></span>|<span data-ttu-id="a141b-182">説明</span><span class="sxs-lookup"><span data-stu-id="a141b-182">Description</span></span>|
|-------------------|-----------------|
|<span data-ttu-id="a141b-183">`/ExeConfig:` `exePath`</span><span class="sxs-lookup"><span data-stu-id="a141b-183">`/ExeConfig:` `exePath`</span></span>|<span data-ttu-id="a141b-184">指定された実行可能アセンブリの構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="a141b-184">Use the configuration of the specified executable assembly.</span></span><br /><br /> <span data-ttu-id="a141b-185">Ngen.exe は、依存関係にバインドする際に、ローダーと同じ決定をする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-185">Ngen.exe needs to make the same decisions as the loader when binding to dependencies.</span></span> <span data-ttu-id="a141b-186"><xref:System.Reflection.Assembly.Load%2A> メソッドを使用して共有コンポーネントが実行時に読み込まれると、読み込まれた依存関係のバージョンなどの共有コンポーネント用に読み込まれた依存関係はアプリケーションの構成ファイルによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-186">When a shared component is loaded at run time, using the <xref:System.Reflection.Assembly.Load%2A> method, the application's configuration file determines the dependencies that are loaded for the shared component — for example, the version of a dependency that is loaded.</span></span> <span data-ttu-id="a141b-187">`/ExeConfig` スイッチは、実行時にどの依存関係を読み込むかに関するガイダンスを Ngen.exe に提供します。</span><span class="sxs-lookup"><span data-stu-id="a141b-187">The `/ExeConfig` switch gives Ngen.exe guidance on which dependencies would be loaded at run time.</span></span>|
|<span data-ttu-id="a141b-188">`/AppBase:` `directoryPath`</span><span class="sxs-lookup"><span data-stu-id="a141b-188">`/AppBase:` `directoryPath`</span></span>|<span data-ttu-id="a141b-189">依存関係を検索するときは、アプリケーション ベースに指定されているディレクトリを使用します。</span><span class="sxs-lookup"><span data-stu-id="a141b-189">When locating dependencies, use the specified directory as the application base.</span></span>|

<a name="OptionTable"></a>

## <a name="options"></a><span data-ttu-id="a141b-190">オプション</span><span class="sxs-lookup"><span data-stu-id="a141b-190">Options</span></span>

|<span data-ttu-id="a141b-191">オプション</span><span class="sxs-lookup"><span data-stu-id="a141b-191">Option</span></span>|<span data-ttu-id="a141b-192">[説明]</span><span class="sxs-lookup"><span data-stu-id="a141b-192">Description</span></span>|
|------------|-----------------|
|`/nologo`|<span data-ttu-id="a141b-193">Microsoft 著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="a141b-193">Suppress the Microsoft startup banner display.</span></span>|
|`/silent`|<span data-ttu-id="a141b-194">成功メッセージを表示しません。</span><span class="sxs-lookup"><span data-stu-id="a141b-194">Suppress the display of success messages.</span></span>|
|`/verbose`|<span data-ttu-id="a141b-195">デバッグの詳細情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="a141b-195">Display detailed information for debugging.</span></span>|
|<span data-ttu-id="a141b-196">`/help`, `/?`</span><span class="sxs-lookup"><span data-stu-id="a141b-196">`/help`, `/?`</span></span>|<span data-ttu-id="a141b-197">現在のリリースのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="a141b-197">Display command syntax and options for the current release.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a141b-198">Remarks</span><span class="sxs-lookup"><span data-stu-id="a141b-198">Remarks</span></span>

<span data-ttu-id="a141b-199">Ngen.exe を実行するには、管理特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="a141b-199">To run Ngen.exe, you must have administrative privileges.</span></span>

> [!CAUTION]
> <span data-ttu-id="a141b-200">完全に信頼されていないアセンブリで Ngen.exe を実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="a141b-200">Do not run Ngen.exe on assemblies that are not fully trusted.</span></span> <span data-ttu-id="a141b-201">.NET Framework 4 以降では、Ngen.exe によるアセンブリのコンパイルが完全信頼で行われるようになり、コード アクセス セキュリティ (CAS) ポリシーが評価されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a141b-201">Starting with the .NET Framework 4, Ngen.exe compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>

<span data-ttu-id="a141b-202">.NET Framework 4 以降では、Ngen.exe で生成されたネイティブ イメージを、部分信頼で実行されているアプリケーションに読み込むことができなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a141b-202">Starting with the .NET Framework 4, the native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span> <span data-ttu-id="a141b-203">代わりに、Just-In-Time (JIT) コンパイラが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-203">Instead, the just-in-time (JIT) compiler is invoked.</span></span>

<span data-ttu-id="a141b-204">Ngen.exe は、`install` アクションへの `assemblyname` 引数で指定されたアセンブリおよびそのすべての依存項目のネイティブ イメージを生成します。</span><span class="sxs-lookup"><span data-stu-id="a141b-204">Ngen.exe generates native images for the assembly specified by the `assemblyname` argument to the `install` action and all its dependencies.</span></span> <span data-ttu-id="a141b-205">依存関係は、アセンブリ マニフェストを参照して決定されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-205">Dependencies are determined from references in the assembly manifest.</span></span> <span data-ttu-id="a141b-206">依存関係を別個にインストールする必要があるのは、アプリケーションがリフレクションを使用して依存関係を読み込む場合だけです。たとえば <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> メソッドを呼び出して依存関係を読み込む場合などです。</span><span class="sxs-lookup"><span data-stu-id="a141b-206">The only scenario in which you need to install a dependency separately is when the application loads it using reflection, for example by calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a141b-207">ネイティブ イメージに <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> メソッドは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="a141b-207">Do not use the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method with native images.</span></span> <span data-ttu-id="a141b-208">実行コンテキストの他のアセンブリは、このメソッドを使用して読み込まれるイメージを使用できません。</span><span class="sxs-lookup"><span data-stu-id="a141b-208">An image loaded with this method cannot be used by other assemblies in the execution context.</span></span>

<span data-ttu-id="a141b-209">Ngen.exe は依存関係のカウントを保持します。</span><span class="sxs-lookup"><span data-stu-id="a141b-209">Ngen.exe maintains a count on dependencies.</span></span> <span data-ttu-id="a141b-210">たとえば、`MyAssembly.exe` と `YourAssembly.exe` がネイティブ イメージ キャッシュにインストールされており、この両方とも `OurDependency.dll` を参照するとします。</span><span class="sxs-lookup"><span data-stu-id="a141b-210">For example, suppose `MyAssembly.exe` and `YourAssembly.exe` are both installed in the native image cache, and both have references to `OurDependency.dll`.</span></span> <span data-ttu-id="a141b-211">`MyAssembly.exe` がアンインストールされても、`OurDependency.dll` はアンインストールされません。</span><span class="sxs-lookup"><span data-stu-id="a141b-211">If `MyAssembly.exe` is uninstalled, `OurDependency.dll` is not uninstalled.</span></span> <span data-ttu-id="a141b-212">これが削除されるのは、`YourAssembly.exe` もアンインストールされた場合だけです。</span><span class="sxs-lookup"><span data-stu-id="a141b-212">It is only removed when `YourAssembly.exe` is also uninstalled.</span></span>

<span data-ttu-id="a141b-213">アセンブリのネイティブ イメージをグローバル アセンブリ キャッシュに生成している場合は表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a141b-213">If you are generating a native image for an assembly in the global assembly cache, specify its display name.</span></span> <span data-ttu-id="a141b-214">以下を参照してください。<xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a141b-214">See <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="a141b-215">Ngen.exe が生成するネイティブ イメージは、アプリケーション ドメイン間で共有できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-215">The native images that Ngen.exe generates can be shared across application domains.</span></span> <span data-ttu-id="a141b-216">つまり、アプリケーション ドメイン間でアセンブリを共有する必要のあるアプリケーション シナリオでは Ngen.exe を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-216">This means you can use Ngen.exe in application scenarios that require assemblies to be shared across application domains.</span></span> <span data-ttu-id="a141b-217">ドメイン中立性は、次の手順で指定します。</span><span class="sxs-lookup"><span data-stu-id="a141b-217">To specify domain neutrality:</span></span>

- <span data-ttu-id="a141b-218">アプリケーションに <xref:System.LoaderOptimizationAttribute> 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="a141b-218">Apply the <xref:System.LoaderOptimizationAttribute> attribute to your application.</span></span>

- <span data-ttu-id="a141b-219">新しいアプリケーション ドメインのセットアップ情報を作成するときは、<xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="a141b-219">Set the <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> property when you create setup information for a new application domain.</span></span>

<span data-ttu-id="a141b-220">複数のアプリケーション ドメインに同じアセンブリを読み込むときは、必ずドメイン中立のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="a141b-220">Always use domain-neutral code when loading the same assembly into multiple application domains.</span></span> <span data-ttu-id="a141b-221">共有ドメインに読み込んだ後に非共有アプリケーション ドメインに読み込んだネイティブ イメージは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a141b-221">If a native image is loaded into a nonshared application domain after having been loaded into a shared domain, it cannot be used.</span></span>

> [!NOTE]
> <span data-ttu-id="a141b-222">ドメイン中立コードはアンロードできません。また、特に静的メンバーにアクセスする際にパフォーマンスがわずかに低下します。</span><span class="sxs-lookup"><span data-stu-id="a141b-222">Domain-neutral code cannot be unloaded, and performance may be slightly slower, particularly when accessing static members.</span></span>

<span data-ttu-id="a141b-223">「解説」セクションの内容:</span><span class="sxs-lookup"><span data-stu-id="a141b-223">In this Remarks section:</span></span>

- [<span data-ttu-id="a141b-224">別のシナリオのためのイメージの生成</span><span class="sxs-lookup"><span data-stu-id="a141b-224">Generating images for different scenarios</span></span>](#Scenarios)

- [<span data-ttu-id="a141b-225">ネイティブ イメージを使用する状況の決定</span><span class="sxs-lookup"><span data-stu-id="a141b-225">Determining when to Use native images</span></span>](#WhenToUse)

  - [<span data-ttu-id="a141b-226">メモリ使用の改善</span><span class="sxs-lookup"><span data-stu-id="a141b-226">Improved memory use</span></span>](#Memory)

  - [<span data-ttu-id="a141b-227">アプリケーションの起動の高速化</span><span class="sxs-lookup"><span data-stu-id="a141b-227">Faster application startup</span></span>](#Startup)

  - [<span data-ttu-id="a141b-228">使用における考慮事項のまとめ</span><span class="sxs-lookup"><span data-stu-id="a141b-228">Summary of usage considerations</span></span>](#UsageSummary)

- [<span data-ttu-id="a141b-229">アセンブリのベース アドレスの重要性</span><span class="sxs-lookup"><span data-stu-id="a141b-229">Importance of assembly base addresses</span></span>](#BaseAddresses)

- [<span data-ttu-id="a141b-230">ハード バインディング</span><span class="sxs-lookup"><span data-stu-id="a141b-230">Hard binding</span></span>](#HardBinding)

  - [<span data-ttu-id="a141b-231">依存関係のバインディング ヒントの指定</span><span class="sxs-lookup"><span data-stu-id="a141b-231">Specifying a binding hint for a dependency</span></span>](#DependencyHint)

  - [<span data-ttu-id="a141b-232">アセンブリの既定のバインディング ヒントの指定</span><span class="sxs-lookup"><span data-stu-id="a141b-232">Specifying a default binding hint for an assembly</span></span>](#AssemblyHint)

- [<span data-ttu-id="a141b-233">遅延処理</span><span class="sxs-lookup"><span data-stu-id="a141b-233">Deferred processing</span></span>](#Deferred)

- [<span data-ttu-id="a141b-234">ネイティブ イメージと JIT コンパイル</span><span class="sxs-lookup"><span data-stu-id="a141b-234">Native images and JIT compilation</span></span>](#JITCompilation)

  - [<span data-ttu-id="a141b-235">無効なイメージ</span><span class="sxs-lookup"><span data-stu-id="a141b-235">Invalid images</span></span>](#InvalidImages)

- [<span data-ttu-id="a141b-236">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a141b-236">Troubleshooting</span></span>](#Troubleshooting)

  - [<span data-ttu-id="a141b-237">アセンブリ バインディング ログ ビューアー</span><span class="sxs-lookup"><span data-stu-id="a141b-237">Assembly Binding Log Viewer</span></span>](#Fusion)

  - [<span data-ttu-id="a141b-238">JITCompilationStart マネージド デバッグ アシスタント</span><span class="sxs-lookup"><span data-stu-id="a141b-238">The JITCompilationStart managed debugging assistant</span></span>](#MDA)

  - [<span data-ttu-id="a141b-239">ネイティブ イメージ生成の中止</span><span class="sxs-lookup"><span data-stu-id="a141b-239">Opting out of native image generation</span></span>](#OptOut)

<a name="Scenarios"></a>

## <a name="generating-images-for-----different-scenarios"></a><span data-ttu-id="a141b-240">別のシナリオのためのイメージの生成</span><span class="sxs-lookup"><span data-stu-id="a141b-240">Generating images for     different scenarios</span></span>

<span data-ttu-id="a141b-241">アセンブリのネイティブ イメージが生成された後でそのアセンブリを実行する場合、ランタイムは、常にこのネイティブ イメージを自動的に検索して使用しようとします。</span><span class="sxs-lookup"><span data-stu-id="a141b-241">After you have generated a native image for an assembly, the runtime automatically attempts to locate and use this native   image each time it runs the assembly.</span></span> <span data-ttu-id="a141b-242">使用シナリオによっては、複数のイメージを生成できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-242">Multiple images can be generated, depending on usage scenarios.</span></span>

<span data-ttu-id="a141b-243">たとえば、デバッグまたはプロファイルの目的でアセンブリを実行する場合、ランタイムは、`/Debug` または `/Profile` の各オプションを指定して生成されたネイティブ イメージを検索します。</span><span class="sxs-lookup"><span data-stu-id="a141b-243">For example, if you run an assembly in a debugging or profiling scenario, the runtime looks for a native image that was generated with the `/Debug` or `/Profile` options.</span></span> <span data-ttu-id="a141b-244">一致するネイティブ イメージが見つからない場合、ランタイムは標準の JIT コンパイルに戻ります。</span><span class="sxs-lookup"><span data-stu-id="a141b-244">If it is unable to find a matching native image, the runtime reverts to standard JIT compilation.</span></span> <span data-ttu-id="a141b-245">ネイティブ イメージをデバッグする唯一の方法は、`/Debug` オプションを使用してネイティブ イメージを作成することです。</span><span class="sxs-lookup"><span data-stu-id="a141b-245">The only way to debug native images is to create a native image with the `/Debug` option.</span></span>

<span data-ttu-id="a141b-246">`uninstall` アクションもシナリオを認識するため、すべてのシナリオまたは指定したシナリオだけをアンインストールできます。</span><span class="sxs-lookup"><span data-stu-id="a141b-246">The `uninstall` action also recognize scenarios, so you can uninstall all scenarios or only selected scenarios.</span></span>

<a name="WhenToUse"></a>

## <a name="determining-when-to-use-native-images"></a><span data-ttu-id="a141b-247">ネイティブ イメージを使用する状況の決定</span><span class="sxs-lookup"><span data-stu-id="a141b-247">Determining when to Use native images</span></span>

<span data-ttu-id="a141b-248">ネイティブ イメージによって、メモリ使用の改善と起動時間の短縮の 2 つの領域においてパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="a141b-248">Native images can provide performance improvements in two areas: improved memory use and reduced startup time.</span></span>

> [!NOTE]
> <span data-ttu-id="a141b-249">ネイティブ イメージのパフォーマンスは、コード、データ アクセス パターン、モジュール境界を超える呼び出しの数、他のアプリケーションによって既に読み込まれている依存関係の数などの多くの要素に依存するため分析が困難です。</span><span class="sxs-lookup"><span data-stu-id="a141b-249">Performance of native images depends on a number of factors that make analysis difficult, such as code and data access patterns, how many calls are made across module boundaries, and how many dependencies have already been loaded by other applications.</span></span> <span data-ttu-id="a141b-250">ネイティブ イメージがアプリケーションの利益になるかどうかを確認する唯一の方法は、主な配置シナリオにおいて慎重にパフォーマンスを測定することです。</span><span class="sxs-lookup"><span data-stu-id="a141b-250">The only way to determine whether native images benefit your application is by careful performance measurements in your key deployment scenarios.</span></span>

<a name="Memory"></a>

### <a name="improved-memory-use"></a><span data-ttu-id="a141b-251">メモリ使用の改善</span><span class="sxs-lookup"><span data-stu-id="a141b-251">Improved memory use</span></span>

<span data-ttu-id="a141b-252">プロセス間でコードを共有する場合は、ネイティブ イメージによってメモリ使用を大いに改善できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-252">Native images can significantly improve memory use when code is shared between processes.</span></span> <span data-ttu-id="a141b-253">ネイティブ イメージは Windows PE ファイルのため、.dll ファイルの単一のコピーを複数のプロセスで共有できます。これに対して、JIT コンパイラが生成するネイティブ コードは、プライベート メモリに格納されるため共有できません。</span><span class="sxs-lookup"><span data-stu-id="a141b-253">Native images are Windows PE files, so a single copy of a .dll file can be shared by multiple processes; by contrast, native code produced by the JIT compiler is stored in private memory and cannot be shared.</span></span>

<span data-ttu-id="a141b-254">ターミナル サービスで実行されるアプリケーションも、共有されたコード ページの恩恵を受けることができます。</span><span class="sxs-lookup"><span data-stu-id="a141b-254">Applications that are run under terminal services can also benefit from shared code pages.</span></span>

<span data-ttu-id="a141b-255">さらに、JIT コンパイラを読み込まないため、各アプリケーション インスタンスが使用する固定メモリの量も減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="a141b-255">In addition, not loading the JIT compiler saves a fixed amount of memory for each application instance.</span></span>

<a name="Startup"></a>

### <a name="faster-application-startup"></a><span data-ttu-id="a141b-256">アプリケーションの起動の高速化</span><span class="sxs-lookup"><span data-stu-id="a141b-256">Faster application startup</span></span>

<span data-ttu-id="a141b-257">Ngen.exe によってアセンブリをプリコンパイルすることにより、一部のアプリケーションの起動時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-257">Precompiling assemblies with Ngen.exe can improve the startup time for some applications.</span></span> <span data-ttu-id="a141b-258">一般に、最初のアプリケーションが起動されると、その後のアプリケーションが使用する共有コンポーネントが読み込まれるため、アプリケーションがコンポーネント アセンブリを共有している場合にアプリケーションの起動時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-258">In general, gains can be made when applications share component assemblies because after the first application has been started the shared components are already loaded for subsequent applications.</span></span> <span data-ttu-id="a141b-259">アプリケーションのすべてのアセンブリをハード ディスクから読み込む必要があるコールド スタートでは、ハード ディスクのアクセス時間の影響の方が大きいため、ネイティブ イメージから受け取る恩恵はそれほど大きくありません。</span><span class="sxs-lookup"><span data-stu-id="a141b-259">Cold startup, in which all the assemblies in an application must be loaded from the hard disk, does not benefit as much from native images because the hard disk access time predominates.</span></span>

<span data-ttu-id="a141b-260">メイン アプリケーション アセンブリにハード バインディングされているすべてのイメージは同時に読み込む必要があるため、ハード バインディングは起動時間に影響します。</span><span class="sxs-lookup"><span data-stu-id="a141b-260">Hard binding can affect startup time, because all images that are hard bound to the main application assembly must be loaded at the same time.</span></span>

> [!NOTE]
> <span data-ttu-id="a141b-261">.NET Framework 3.5 Service Pack 1 より前のバージョンでは、厳密な名前付きの共有コンポーネントをグローバル アセンブリ キャッシュに配置する必要があります。これは、グローバル アセンブリ キャッシュ以外に配置されている厳密な名前付きのアセンブリに対してローダーが余分な検証を行うため、起動時間は短縮されず、実質的にネイティブ イメージを使用する意味がなくなります。</span><span class="sxs-lookup"><span data-stu-id="a141b-261">Before the .NET Framework 3.5 Service Pack 1, you should put shared, strong-named components in the global assembly cache, because the loader performs extra validation on strong-named assemblies that are not in the global assembly cache, effectively eliminating any improvement in startup time gained by using native images.</span></span> <span data-ttu-id="a141b-262">.NET Framework 3.5 SP1 で導入された最適化により、この余分な検証は削除されました。</span><span class="sxs-lookup"><span data-stu-id="a141b-262">Optimizations that were introduced in the .NET Framework 3.5 SP1 removed the extra validation.</span></span>

<a name="UsageSummary"></a>

### <a name="summary-of-usage-considerations"></a><span data-ttu-id="a141b-263">使用における考慮事項のまとめ</span><span class="sxs-lookup"><span data-stu-id="a141b-263">Summary of usage considerations</span></span>

<span data-ttu-id="a141b-264">次の一般的な考慮事項とアプリケーションの考慮事項は、アプリケーションにネイティブ イメージを使用するかどうかを評価する際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a141b-264">The following general considerations and application considerations may assist you in deciding whether to undertake the effort of evaluating native images for your application:</span></span>

- <span data-ttu-id="a141b-265">ネイティブ イメージでは、JIT コンパイル、タイプ セーフ検証などの多くの起動時アクティビティが不要なため、MSIL より読み込みが高速になります。</span><span class="sxs-lookup"><span data-stu-id="a141b-265">Native images load faster than MSIL because they eliminate the need for many startup activities, such as JIT compilation and type-safety verification.</span></span>

- <span data-ttu-id="a141b-266">ネイティブ イメージでは JIT コンパイラが不要なため、必要な初期作業セットが少なくてすみます。</span><span class="sxs-lookup"><span data-stu-id="a141b-266">Native images require a smaller initial working set because there is no need for the JIT compiler.</span></span>

- <span data-ttu-id="a141b-267">ネイティブ イメージによって、プロセス間でコードを共有できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-267">Native images enable code sharing between processes.</span></span>

- <span data-ttu-id="a141b-268">ネイティブ イメージは MSIL アセンブリよりも多くのハード ディスク容量を必要とし、生成にかなりの時間を要する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-268">Native images require more hard disk space than MSIL assemblies and may require considerable time to generate.</span></span>

- <span data-ttu-id="a141b-269">ネイティブ イメージは保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-269">Native images must be maintained.</span></span>

  - <span data-ttu-id="a141b-270">元のアセンブリまたはその依存関係のいずれかに対してサービスを提供する場合は、イメージを再生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-270">Images need to be regenerated when the original assembly or one of its dependencies is serviced.</span></span>

  - <span data-ttu-id="a141b-271">アプリケーションまたはシナリオごとに異なるネイティブ イメージを使用する場合、1 つのアセンブリで複数のネイティブ イメージが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-271">A single assembly may need multiple native images for use in different applications or different scenarios.</span></span> <span data-ttu-id="a141b-272">たとえば、2 つのアプリケーションの構成情報で、同じ依存アセンブリに対してバインディング決定が異なる場合です。</span><span class="sxs-lookup"><span data-stu-id="a141b-272">For example, the configuration information in two applications might result in different binding decisions for the same dependent assembly.</span></span>

  - <span data-ttu-id="a141b-273">ネイティブ イメージは管理者が作成する必要があります。つまり Administrators グループの Windows アカウントから作成します。</span><span class="sxs-lookup"><span data-stu-id="a141b-273">Native images must be generated by an administrator; that is, from a Windows account in the Administrators group.</span></span>

<span data-ttu-id="a141b-274">このような一般的な考慮事項に加えて、ネイティブ イメージによってパフォーマンスが向上するかどうかを検討する場合は、アプリケーションの特性も考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-274">In addition to these general considerations, the nature of your application must be considered when determining whether native images might provide a performance benefit:</span></span>

- <span data-ttu-id="a141b-275">多くの共有コンポーネントを使用する環境でアプリケーションを実行する場合は、ネイティブ イメージによってコンポーネントを複数のプロセスで共有できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-275">If your application runs in an environment that uses many shared components, native images allow the components to be shared by multiple processes.</span></span>

- <span data-ttu-id="a141b-276">アプリケーションが複数のアプリケーション ドメインを使用する場合は、ネイティブ イメージによってドメイン間でコード ページを共有できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-276">If your application uses multiple application domains, native images allow code pages to be shared across domains.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a141b-277">.NET Framework Version 1.0 と 1.1 では、アプリケーション ドメイン間でネイティブ イメージを共有することはできません。</span><span class="sxs-lookup"><span data-stu-id="a141b-277">In the .NET Framework versions 1.0 and 1.1, native images cannot be shared across application domains.</span></span> <span data-ttu-id="a141b-278">Version 2.0 以降では可能です。</span><span class="sxs-lookup"><span data-stu-id="a141b-278">This is not the case in version 2.0 or later.</span></span>

- <span data-ttu-id="a141b-279">アプリケーションをターミナル サーバーで実行する場合は、ネイティブ イメージによってコード ページを共有できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-279">If your application will be run under Terminal Server, native images allow sharing of code pages.</span></span>

- <span data-ttu-id="a141b-280">サイズの大きなアプリケーションでは、一般にネイティブ イメージにコンパイルすることでパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="a141b-280">Large applications generally benefit from compilation to native images.</span></span> <span data-ttu-id="a141b-281">サイズの小さなアプリケーションでは、一般にあまり有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="a141b-281">Small applications generally do not benefit.</span></span>

- <span data-ttu-id="a141b-282">長時間実行するアプリケーションでは、ランタイム JIT コンパイルのパフォーマンスの方がネイティブ イメージよりも若干優れています。</span><span class="sxs-lookup"><span data-stu-id="a141b-282">For long-running applications, run-time JIT compilation performs slightly better than native images.</span></span> <span data-ttu-id="a141b-283">ハード バインディングによって、このパフォーマンスの違いをある程度緩和できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-283">(Hard binding can mitigate this performance difference to some degree.)</span></span>

<a name="BaseAddresses"></a>

## <a name="importance-of-assembly-base-addresses"></a><span data-ttu-id="a141b-284">アセンブリのベース アドレスの重要性</span><span class="sxs-lookup"><span data-stu-id="a141b-284">Importance of assembly base addresses</span></span>

<span data-ttu-id="a141b-285">ネイティブ イメージは Windows PE ファイルのため、他の実行可能ファイルと同様に再ベースの問題があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-285">Because native images are Windows PE files, they are subject to the same rebasing issues as other executable files.</span></span> <span data-ttu-id="a141b-286">ハード バインディングを使用する場合、再配置のパフォーマンス コストはさらに増大します。</span><span class="sxs-lookup"><span data-stu-id="a141b-286">The performance cost of relocation is even more pronounced if hard binding is employed.</span></span>

<span data-ttu-id="a141b-287">ネイティブ イメージにベース アドレスを設定するには、コンパイラの適切なオプションを使用してアセンブリのベース アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="a141b-287">To set the base address for a native image, use the appropriate option of your compiler to set the base address for the assembly.</span></span> <span data-ttu-id="a141b-288">Ngen.exe は、このベース アドレスをネイティブ イメージに使用します。</span><span class="sxs-lookup"><span data-stu-id="a141b-288">Ngen.exe uses this base address for the native image.</span></span>

> [!NOTE]
> <span data-ttu-id="a141b-289">ネイティブ イメージは、元になるマネージド アセンブリより大きくなります。</span><span class="sxs-lookup"><span data-stu-id="a141b-289">Native images are larger than the managed assemblies from which they were created.</span></span> <span data-ttu-id="a141b-290">ベース アドレスは、この大きなサイズを考慮して算出する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-290">Base addresses must be calculated to allow for these larger sizes.</span></span>

<span data-ttu-id="a141b-291">dumpbin.exe などのツールを使用すると、ネイティブ イメージの推奨ベース アドレスを表示できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-291">You can use a tool such as dumpbin.exe to view the preferred base address of a native image.</span></span>

<a name="HardBinding"></a>

## <a name="hard-binding"></a><span data-ttu-id="a141b-292">ハード バインディング</span><span class="sxs-lookup"><span data-stu-id="a141b-292">Hard binding</span></span>

<span data-ttu-id="a141b-293">ハード バインディングによってスループットが向上し、ネイティブ イメージの作業セットのサイズが小さくなります。</span><span class="sxs-lookup"><span data-stu-id="a141b-293">Hard binding increases throughput and reduces working set size for native images.</span></span> <span data-ttu-id="a141b-294">ハード バインディングの短所は、アセンブリを読み込む際にアセンブリにハード バインディングされているすべてのイメージを読み込む必要があることです。</span><span class="sxs-lookup"><span data-stu-id="a141b-294">The disadvantage of hard binding is that all the images that are hard bound to an assembly must be loaded when the assembly is loaded.</span></span> <span data-ttu-id="a141b-295">これによって、大きなアプリケーションの起動時間がかなり長くなります。</span><span class="sxs-lookup"><span data-stu-id="a141b-295">This can significantly increase startup time for a large application.</span></span>

<span data-ttu-id="a141b-296">ハード バインディングは、すべてのアプリケーションのパフォーマンスが重要な意味を持つシナリオで読み込まれる依存関係に適しています。</span><span class="sxs-lookup"><span data-stu-id="a141b-296">Hard binding is appropriate for dependencies that are loaded in all your application's performance-critical scenarios.</span></span> <span data-ttu-id="a141b-297">ネイティブ イメージの使用のすべての局面において言えることですが、ハード バインディングによってアプリケーションのパフォーマンスが向上するかどうかを確認する唯一の方法は、パフォーマンスを慎重に測定することです。</span><span class="sxs-lookup"><span data-stu-id="a141b-297">As with any aspect of native image use, careful performance measurements are the only way to determine whether hard binding improves your application's performance.</span></span>

<span data-ttu-id="a141b-298"><xref:System.Runtime.CompilerServices.DependencyAttribute> 属性と <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> 属性によって、ハード バインディング ヒントを Ngen.exe に提供できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-298">The <xref:System.Runtime.CompilerServices.DependencyAttribute> and <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> attributes allow you to provide hard binding hints to Ngen.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="a141b-299">この 2 つの属性は、コマンドではなく Ngen.exe へのヒントです。</span><span class="sxs-lookup"><span data-stu-id="a141b-299">These attributes are hints to Ngen.exe, not commands.</span></span> <span data-ttu-id="a141b-300">これらの属性を使用してもハード バインディングは保証されません。</span><span class="sxs-lookup"><span data-stu-id="a141b-300">Using them does not guarantee hard binding.</span></span> <span data-ttu-id="a141b-301">属性の意味は、今後のリリースで変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-301">The meaning of these attributes may change in future releases.</span></span>

<a name="DependencyHint"></a>

### <a name="specifying-a-binding-hint-for-a-dependency"></a><span data-ttu-id="a141b-302">依存関係のバインディング ヒントの指定</span><span class="sxs-lookup"><span data-stu-id="a141b-302">Specifying a binding hint for a dependency</span></span>

<span data-ttu-id="a141b-303">アセンブリに <xref:System.Runtime.CompilerServices.DependencyAttribute> を適用して、指定された依存関係が読み込まれるかどうかを示します</span><span class="sxs-lookup"><span data-stu-id="a141b-303">Apply the <xref:System.Runtime.CompilerServices.DependencyAttribute> to an assembly to indicate the likelihood that a specified dependency will be loaded.</span></span> <span data-ttu-id="a141b-304"><xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> は、ハード バインディングが適切であることを示します。<xref:System.Runtime.CompilerServices.LoadHint.Default> は、依存関係の既定値を使用する必要があることを示します。<xref:System.Runtime.CompilerServices.LoadHint.Sometimes> は、ハード バインディングが適切ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="a141b-304"><xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> indicates that hard binding is appropriate, <xref:System.Runtime.CompilerServices.LoadHint.Default> indicates that the default for the dependency should be used, and <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> indicates that hard binding is not appropriate.</span></span>

<span data-ttu-id="a141b-305">2 つの依存関係があるアセンブリのための属性のコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a141b-305">The following code shows the attributes for an assembly that has two dependencies.</span></span> <span data-ttu-id="a141b-306">最初の依存関係 (Assembly1) はハード バインディングに適しており、2 番目 (Assembly2) は適していません。</span><span class="sxs-lookup"><span data-stu-id="a141b-306">The first dependency (Assembly1) is an appropriate candidate for hard binding, and the second (Assembly2) is not.</span></span>

```vb
Imports System.Runtime.CompilerServices
<Assembly:DependencyAttribute("Assembly1", LoadHint.Always)>
<Assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)>
```

```csharp
using System.Runtime.CompilerServices;
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)]
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)]
```

```cpp
using namespace System::Runtime::CompilerServices;
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)];
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)];
```

<span data-ttu-id="a141b-307">アセンブリ名には、ファイル名拡張子は含めません。</span><span class="sxs-lookup"><span data-stu-id="a141b-307">The assembly name does not include the file name extension.</span></span> <span data-ttu-id="a141b-308">表示名を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-308">Display names can be used.</span></span>

<a name="AssemblyHint"></a>

### <a name="specifying-a-default-binding-hint-for-an-assembly"></a><span data-ttu-id="a141b-309">アセンブリの既定のバインディング ヒントの指定</span><span class="sxs-lookup"><span data-stu-id="a141b-309">Specifying a default binding hint for an assembly</span></span>

<span data-ttu-id="a141b-310">既定のバインディング ヒントは、依存するアプリケーションが即座に頻繁に使用するアセンブリだけに必要です。</span><span class="sxs-lookup"><span data-stu-id="a141b-310">Default binding hints are only needed for assemblies that will be used immediately and frequently by any application that has a dependency on them.</span></span> <span data-ttu-id="a141b-311">そのようなアセンブリには、<xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> と共に <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> を適用して、ハード バインディングを使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="a141b-311">Apply the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> with <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> to such assemblies to specify that hard binding should be used.</span></span>

> [!NOTE]
> <span data-ttu-id="a141b-312"><xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> 以外の値を使用してこの属性を適用しても、この属性をまったく適用しない場合と結果は同じため、このカテゴリに属さない .dll アセンブリに <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> を適用する理由はありません。</span><span class="sxs-lookup"><span data-stu-id="a141b-312">There is no reason to apply <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to .dll assemblies that do not fall into this category, because applying the attribute with any value other than <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> has the same effect as not applying the attribute at all.</span></span>

<span data-ttu-id="a141b-313">Microsoft では、<xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> を使用して、mscorlib.dll などのごく一部の .NET Framework のアセンブリの既定値としてハード バインディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="a141b-313">Microsoft uses the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to specify that hard binding is the default for a very small number of assemblies in the .NET Framework, such as mscorlib.dll.</span></span>

<a name="Deferred"></a>

## <a name="deferred-processing"></a><span data-ttu-id="a141b-314">遅延処理</span><span class="sxs-lookup"><span data-stu-id="a141b-314">Deferred processing</span></span>

<span data-ttu-id="a141b-315">非常に大きいアプリケーションのネイティブ イメージの生成には、かなりの時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="a141b-315">Generation of native images for a very large application can take considerable time.</span></span> <span data-ttu-id="a141b-316">同様に、共有コンポーネントへの変更またはコンピューター設定への変更には、多くのネイティブ イメージの更新が必要になります。</span><span class="sxs-lookup"><span data-stu-id="a141b-316">Similarly, changes to a shared component or changes to computer settings might require many native images to be updated.</span></span> <span data-ttu-id="a141b-317">`install` アクションと `update` アクションには `/queue` オプションがあり、これによって、ネイティブ イメージ サービスによる遅延実行をキューに置くことができます。</span><span class="sxs-lookup"><span data-stu-id="a141b-317">The `install` and `update` actions have a `/queue` option that queues the operation for deferred execution by the native image service.</span></span> <span data-ttu-id="a141b-318">さらに、Ngen.exe には、サービスを制御するための `queue` アクションと `executeQueuedItems` アクションがあります。</span><span class="sxs-lookup"><span data-stu-id="a141b-318">In addition, Ngen.exe has `queue` and `executeQueuedItems` actions that provide some control over the service.</span></span> <span data-ttu-id="a141b-319">詳細については、「[ネイティブ イメージ サービス](#native-image-service)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a141b-319">For more information, see [Native Image Service](#native-image-service).</span></span>

<a name="JITCompilation"></a>

## <a name="native-images-and-jit-compilation"></a><span data-ttu-id="a141b-320">ネイティブ イメージと JIT コンパイル</span><span class="sxs-lookup"><span data-stu-id="a141b-320">Native images and JIT compilation</span></span>

<span data-ttu-id="a141b-321">生成できないメソッドがアセンブリ内にある場合、Ngen.exe が生成するネイティブ イメージにそのメソッドは含まれません。</span><span class="sxs-lookup"><span data-stu-id="a141b-321">If Ngen.exe encounters any methods in an assembly that it cannot generate, it excludes them from the native image.</span></span> <span data-ttu-id="a141b-322">ランタイムは、このアセンブリの実行中に JIT コンパイルに戻し、ネイティブ イメージから除外されたこれらのメソッドを処理します。</span><span class="sxs-lookup"><span data-stu-id="a141b-322">When the runtime executes this assembly, it reverts to JIT compilation for the methods that were not included in the native image.</span></span>

<span data-ttu-id="a141b-323">さらに、アセンブリがアップグレードされた場合、または何らかの理解によってイメージが無効になった場合、ネイティブ イメージは使用されません。</span><span class="sxs-lookup"><span data-stu-id="a141b-323">In addition, native images are not used if the assembly has been upgraded, or if the image has been invalidated for any reason.</span></span>

<a name="InvalidImages"></a>

### <a name="invalid-images"></a><span data-ttu-id="a141b-324">無効なイメージ</span><span class="sxs-lookup"><span data-stu-id="a141b-324">Invalid images</span></span>

<span data-ttu-id="a141b-325">Ngen.exe を使用してアセンブリのネイティブ イメージを作成する場合、出力は指定したコマンド ライン オプションおよび使用するコンピューター上の設定に依存します。</span><span class="sxs-lookup"><span data-stu-id="a141b-325">When you use Ngen.exe to create a native image of an assembly, the output depends upon the command-line options that you specify and certain settings on your computer.</span></span> <span data-ttu-id="a141b-326">影響のある設定は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a141b-326">These settings include the following:</span></span>

- <span data-ttu-id="a141b-327">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="a141b-327">The version of .NET Framework.</span></span>

- <span data-ttu-id="a141b-328">アセンブリの正確な ID (ID は再コンパイル時に変更されます)。</span><span class="sxs-lookup"><span data-stu-id="a141b-328">The exact identity of the assembly (recompilation changes identity).</span></span>

- <span data-ttu-id="a141b-329">アセンブリが参照するすべてのアセンブリの正確な ID (ID は再コンパイル時に変更されます)。</span><span class="sxs-lookup"><span data-stu-id="a141b-329">The exact identity of all assemblies that the assembly references (recompilation changes identity).</span></span>

- <span data-ttu-id="a141b-330">セキュリティ関連の要因。</span><span class="sxs-lookup"><span data-stu-id="a141b-330">Security factors.</span></span>

<span data-ttu-id="a141b-331">Ngen.exe は、ネイティブ イメージを生成するときに上記の情報を記録します。</span><span class="sxs-lookup"><span data-stu-id="a141b-331">Ngen.exe records this information when it generates a native image.</span></span> <span data-ttu-id="a141b-332">アセンブリが実行されると、ランタイムは、コンピューターの現在の環境と一致するオプションおよび設定を指定して生成されたネイティブ イメージを検索します。</span><span class="sxs-lookup"><span data-stu-id="a141b-332">When you execute an assembly, the runtime looks for the native image generated with options and settings that match the computer's current environment.</span></span> <span data-ttu-id="a141b-333">一致するネイティブ イメージが見つからない場合、ランタイムはアセンブリを JIT コンパイルに戻します。</span><span class="sxs-lookup"><span data-stu-id="a141b-333">The runtime reverts to JIT compilation of an assembly if it cannot find a matching native image.</span></span> <span data-ttu-id="a141b-334">コンピューターの設定および環境が次のように変更されると、ネイティブ イメージは無効になります。</span><span class="sxs-lookup"><span data-stu-id="a141b-334">The following changes to a computer's settings and environment cause native images to become invalid:</span></span>

- <span data-ttu-id="a141b-335">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="a141b-335">The version of .NET Framework.</span></span>

     <span data-ttu-id="a141b-336">更新プログラムを .NET Framework に適用すると、Ngen.exe を使用して作成したすべてのネイティブ イメージは、無効になります。</span><span class="sxs-lookup"><span data-stu-id="a141b-336">If you apply an update to .NET Framework, all native images that you have created using Ngen.exe become invalid.</span></span> <span data-ttu-id="a141b-337">したがって、.NET Framework の更新では、常に `Ngen Update` コマンドが実行されてすべてのネイティブ イメージが再生成されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-337">For this reason, all updates of .NET Framework execute the `Ngen Update` command, to ensure that all native images are regenerated.</span></span> <span data-ttu-id="a141b-338">インストールする .NET Framework ライブラリの新しいネイティブ イメージが .NET Framework によって自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-338">.NET Framework automatically creates new native images for the .NET Framework libraries that it installs.</span></span>

- <span data-ttu-id="a141b-339">アセンブリの正確な ID。</span><span class="sxs-lookup"><span data-stu-id="a141b-339">The exact identity of the assembly.</span></span>

     <span data-ttu-id="a141b-340">アセンブリを再コンパイルすると、アセンブリの対応するネイティブ イメージは無効になります。</span><span class="sxs-lookup"><span data-stu-id="a141b-340">If you recompile an assembly, the assembly's corresponding native image becomes invalid.</span></span>

- <span data-ttu-id="a141b-341">アセンブリが参照するすべてのアセンブリの正確な ID。</span><span class="sxs-lookup"><span data-stu-id="a141b-341">The exact identity of any assemblies the assembly references.</span></span>

     <span data-ttu-id="a141b-342">マネージド アセンブリを更新する場合、そのアセンブリに直接または間接に依存するすべてのネイティブ イメージが無効になるため、これらを再生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-342">If you update a managed assembly, all native images that directly or indirectly depend on that assembly become invalid and need to be regenerated.</span></span> <span data-ttu-id="a141b-343">これには、通常の参照と強くバインドされた依存関係も含まれます。</span><span class="sxs-lookup"><span data-stu-id="a141b-343">This includes both ordinary references and hard-bound dependencies.</span></span> <span data-ttu-id="a141b-344">ソフトウェア更新プログラムを適用するときには、インストール プログラムで `Ngen Update` コマンドを実行して、依存するすべてのネイティブ イメージを再生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-344">Whenever a software update is applied, the installation program should execute an `Ngen Update` command to ensure that all dependent native images are regenerated.</span></span>

- <span data-ttu-id="a141b-345">セキュリティ関連の要因。</span><span class="sxs-lookup"><span data-stu-id="a141b-345">Security factors.</span></span>

     <span data-ttu-id="a141b-346">アセンブリに事前に与えられていたアクセス許可を制限するマシン セキュリティ ポリシーを変更すると、そのアセンブリのコンパイル済みのネイティブ イメージが無効になることがあります。</span><span class="sxs-lookup"><span data-stu-id="a141b-346">Changing machine security policy to restrict permissions previously granted to an assembly can cause a previously compiled native image for that assembly to become invalid.</span></span>

     <span data-ttu-id="a141b-347">共通言語ランタイムがコード アクセス セキュリティを管理する方法と、アクセス許可を使用する方法の詳細については、「[コード アクセス セキュリティ](../misc/code-access-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a141b-347">For detailed information about how the common language runtime administers code access security and how to use permissions, see [Code Access Security](../misc/code-access-security.md).</span></span>

<a name="Troubleshooting"></a>

## <a name="troubleshooting"></a><span data-ttu-id="a141b-348">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a141b-348">Troubleshooting</span></span>

<span data-ttu-id="a141b-349">次のトラブルシューティングのトピックでは、アプリケーションで使用されているネイティブ イメージと使用できないネイティブ イメージ、JIT コンパイラがメソッドのコンパイルを開始するタイミングの判別、および指定されたメソッドのネイティブ イメージ コンパイルを中止する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a141b-349">The following troubleshooting topics allow you to see which native images are being used and which cannot be used by your application, to determine when the JIT compiler starts to compile a method, and shows how to opt out of native image compilation of specified methods.</span></span>

<a name="Fusion"></a>

### <a name="assembly-binding-log-viewer"></a><span data-ttu-id="a141b-350">アセンブリ バインディング ログ ビューアー</span><span class="sxs-lookup"><span data-stu-id="a141b-350">Assembly Binding Log Viewer</span></span>

<span data-ttu-id="a141b-351">アプリケーションでネイティブ イメージが使用されているかどうかを確認するには、[Fuslogvw.exe (アセンブリ バインディング ログ ビューアー)](fuslogvw-exe-assembly-binding-log-viewer.md) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-351">To confirm that native images are being used by your application, you can use the [Fuslogvw.exe (Assembly Binding Log Viewer)](fuslogvw-exe-assembly-binding-log-viewer.md).</span></span> <span data-ttu-id="a141b-352">バインディング ログ ビューアーのウィンドウの **[ログのカテゴリ]** ボックスで、 **[ネイティブ イメージ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a141b-352">Select **Native Images** in the **Log Categories** box on the binding log viewer window.</span></span> <span data-ttu-id="a141b-353">Fuslogvw.exe は、ネイティブ イメージが拒否された理由に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="a141b-353">Fuslogvw.exe provides information about why a native image was rejected.</span></span>

<a name="MDA"></a>

### <a name="the-jitcompilationstart-managed-debugging-assistant"></a><span data-ttu-id="a141b-354">JITCompilationStart マネージド デバッグ アシスタント</span><span class="sxs-lookup"><span data-stu-id="a141b-354">The JITCompilationStart managed debugging assistant</span></span>

<span data-ttu-id="a141b-355">[jitCompilationStart](../debug-trace-profile/jitcompilationstart-mda.md) マネージド デバッグ アシスタント (MDA) を使用すると、JIT コンパイラが関数のコンパイルを開始するタイミングを判別できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-355">You can use the [jitCompilationStart](../debug-trace-profile/jitcompilationstart-mda.md) managed debugging assistant (MDA) to determine when the JIT compiler starts to compile a function.</span></span>

<a name="OptOut"></a>

### <a name="opting-out-of-native-image-generation"></a><span data-ttu-id="a141b-356">ネイティブ イメージ生成の中止</span><span class="sxs-lookup"><span data-stu-id="a141b-356">Opting out of native image generation</span></span>

<span data-ttu-id="a141b-357">場合によっては、NGen.exe が特定のメソッドのネイティブ イメージを生成することが困難であったり、メソッドをネイティブ イメージにコンパイルするのではなく JIT コンパイルしたいことがあります。</span><span class="sxs-lookup"><span data-stu-id="a141b-357">In some cases, NGen.exe may have difficulty generating a native image for a specific method, or you may prefer that the method be JIT compiled rather then compiled to a native image.</span></span> <span data-ttu-id="a141b-358">そのような場合、`System.Runtime.BypassNGenAttribute` 属性を使用して、NGen.exe が特定のメソッドのネイティブ イメージを生成するのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="a141b-358">In this case, you can use the `System.Runtime.BypassNGenAttribute` attribute to prevent NGen.exe from generating a native image for a particular method.</span></span> <span data-ttu-id="a141b-359">この属性は、ネイティブ イメージに含めたくないコードを持つ各メソッドに個別に適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-359">The attribute must be applied individually to each method whose code you do not want to include in the native image.</span></span> <span data-ttu-id="a141b-360">NGen.exe はこの属性を認識し、対応するメソッドのネイティブ イメージにコードを生成しません。</span><span class="sxs-lookup"><span data-stu-id="a141b-360">NGen.exe recognizes the attribute and does not generate code in the native image for the corresponding method.</span></span>

<span data-ttu-id="a141b-361">ただし、`BypassNGenAttribute` は .NET Framework クラス ライブラリ内の型としては定義されていません。</span><span class="sxs-lookup"><span data-stu-id="a141b-361">Note, however, that `BypassNGenAttribute` is not defined as a type in the .NET Framework Class Library.</span></span> <span data-ttu-id="a141b-362">コード内で属性を使用するには、最初に次のように定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-362">In order to consume the attribute in your code, you must first define it as follows:</span></span>

[!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
[!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]

<span data-ttu-id="a141b-363">この後、メソッドごとに属性を適用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a141b-363">You can then apply the attribute on a per-method basis.</span></span> <span data-ttu-id="a141b-364">次の例は、`ExampleClass.ToJITCompile` メソッドのネイティブ イメージを生成しないようにネイティブ イメージ ジェネレーターに指示しています。</span><span class="sxs-lookup"><span data-stu-id="a141b-364">The following example instructs the Native Image Generator that it should not generate a native image for the `ExampleClass.ToJITCompile` method.</span></span>

[!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
[!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]

## <a name="examples"></a><span data-ttu-id="a141b-365">使用例</span><span class="sxs-lookup"><span data-stu-id="a141b-365">Examples</span></span>

<span data-ttu-id="a141b-366">次のコマンドは、現在のディレクトリにある `ClientApp.exe` のネイティブ イメージを生成し、ネイティブ イメージ キャッシュにインストールします。</span><span class="sxs-lookup"><span data-stu-id="a141b-366">The following command generates a native image for `ClientApp.exe`, located in the current directory, and installs the image in the native image cache.</span></span> <span data-ttu-id="a141b-367">アセンブリの構成ファイルが存在する場合、Ngen.exe はその構成ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="a141b-367">If a configuration file exists for the assembly, Ngen.exe uses it.</span></span> <span data-ttu-id="a141b-368">さらに、ネイティブ イメージは、`ClientApp.exe` が参照するあらゆる .dll ファイルに対して生成されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-368">In addition, native images are generated for any .dll files that `ClientApp.exe` references.</span></span>

```console
ngen install ClientApp.exe
```

<span data-ttu-id="a141b-369">Ngen.exe によってインストールされるイメージは、ルートとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="a141b-369">An image installed with Ngen.exe is also called a root.</span></span> <span data-ttu-id="a141b-370">ルートは、アプリケーションまたは共有コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="a141b-370">A root can be an application or a shared component.</span></span>

<span data-ttu-id="a141b-371">指定したパスにある `MyAssembly.exe` のネイティブ イメージを生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a141b-371">The following command generates a native image for `MyAssembly.exe` with the specified path.</span></span>

```console
ngen install c:\myfiles\MyAssembly.exe
```

<span data-ttu-id="a141b-372">アセンブリおよびその依存関係を検索する場合、Ngen.exe は共通言語ランタイムと同じプローブ ロジックを使用します。</span><span class="sxs-lookup"><span data-stu-id="a141b-372">When locating assemblies and their dependencies, Ngen.exe uses the same probing logic used by the common language runtime.</span></span> <span data-ttu-id="a141b-373">既定では、`ClientApp.exe` が格納されているディレクトリがアプリケーションのベース ディレクトリとして使用され、すべてのアセンブリのプローブはこのディレクトリから始まります。</span><span class="sxs-lookup"><span data-stu-id="a141b-373">By default, the directory that contains `ClientApp.exe` is used as the application base directory, and all assembly probing begins in this directory.</span></span> <span data-ttu-id="a141b-374">この動作は、`/AppBase` オプションを使用してオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="a141b-374">You can override this behavior by using the `/AppBase` option.</span></span>

> [!NOTE]
> <span data-ttu-id="a141b-375">この動作は、アプリケーション ベースが現在のディレクトリに設定される .NET Framework Version 1.0 と 1.1 における Ngen.exe から変更されています。</span><span class="sxs-lookup"><span data-stu-id="a141b-375">This is a change from Ngen.exe behavior in the .NET Framework versions 1.0 and 1.1, where the application base is set to the current directory.</span></span>

<span data-ttu-id="a141b-376">アセンブリは、参照を伴わない依存関係を持つことができます。たとえば、<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> メソッドを使用して .dll ファイルを読み込む場合などです。</span><span class="sxs-lookup"><span data-stu-id="a141b-376">An assembly can have a dependency without a reference, for example if it loads a .dll file by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a141b-377">アプリケーション アセンブリの構成情報と `/ExeConfig` オプションを使用して、このような .dll ファイルのネイティブ イメージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-377">You can create a native image for such a .dll file by using configuration information for the application assembly, with the `/ExeConfig` option.</span></span> <span data-ttu-id="a141b-378">`MyLib.dll,` の構成情報を使用して `MyApp.exe` のネイティブ イメージを生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a141b-378">The following command generates a native image for `MyLib.dll,` using the configuration information from `MyApp.exe`.</span></span>

```console
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

<span data-ttu-id="a141b-379">この方法でインストールされたアセンブリは、アプリケーションと共に削除されません。</span><span class="sxs-lookup"><span data-stu-id="a141b-379">Assemblies installed in this way are not removed when the application is removed.</span></span>

<span data-ttu-id="a141b-380">依存関係をアンインストールするには、それをインストールしたときと同じコマンド ライン オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="a141b-380">To uninstall a dependency, use the same command-line options that were used to install it.</span></span> <span data-ttu-id="a141b-381">前の例から `MyLib.dll` をアンインストールするコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a141b-381">The following command uninstalls the `MyLib.dll` from the previous example.</span></span>

```console
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

<span data-ttu-id="a141b-382">グローバル アセンブリ キャッシュにアセンブリのネイティブ イメージを作成するには、アセンブリの表示名を使用します。</span><span class="sxs-lookup"><span data-stu-id="a141b-382">To create a native image for an assembly in the global assembly cache, use the display name of the assembly.</span></span> <span data-ttu-id="a141b-383">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a141b-383">For example:</span></span>

```console
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
```

<span data-ttu-id="a141b-384">NGen.exe は、インストールする各シナリオに対して個別のイメージ セットを生成します。</span><span class="sxs-lookup"><span data-stu-id="a141b-384">NGen.exe generates a separate set of images for each scenario you install.</span></span> <span data-ttu-id="a141b-385">たとえば、次のコマンドはネイティブ イメージの通常操作用の完全なセット、デバッグ用の完全なセット、およびプロファイル用の第 3 のセットをインストールします。</span><span class="sxs-lookup"><span data-stu-id="a141b-385">For example, the following commands install a complete set of native images for normal operation, another complete set for debugging, and a third for profiling:</span></span>

```console
ngen install MyApp.exe
ngen install MyApp.exe /debug
ngen install MyApp.exe /profile
```

### <a name="displaying-the-native-image-cache"></a><span data-ttu-id="a141b-386">ネイティブ イメージ キャッシュの表示</span><span class="sxs-lookup"><span data-stu-id="a141b-386">Displaying the Native Image Cache</span></span>

<span data-ttu-id="a141b-387">ネイティブ イメージは、キャッシュにインストールすると、Ngen.exe を使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-387">Once native images are installed in the cache, they can be displayed using Ngen.exe.</span></span> <span data-ttu-id="a141b-388">ネイティブ イメージ キャッシュ内のすべてのネイティブ イメージを表示するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a141b-388">The following command displays all native images in the native image cache.</span></span>

```console
ngen display
```

<span data-ttu-id="a141b-389">`display` アクションは最初にすべてのルート アセンブリを表示し、次にコンピューター上のすべてのネイティブ イメージの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="a141b-389">The `display` action lists all the root assemblies first, followed by a list of all the native images on the computer.</span></span>

<span data-ttu-id="a141b-390">アセンブリの情報だけを表示する場合は、アセンブリの簡易名を使用します。</span><span class="sxs-lookup"><span data-stu-id="a141b-390">Use the simple name of an assembly to display information only for that assembly.</span></span> <span data-ttu-id="a141b-391">次のコマンドは、部分名 `MyAssembly` に一致するネイティブ イメージ キャッシュのすべてのネイティブ イメージ、その依存関係、および `MyAssembly` に依存するすべてのルートを表示します。</span><span class="sxs-lookup"><span data-stu-id="a141b-391">The following command displays all native images in the native image cache that match the partial name `MyAssembly`, their dependencies, and all roots that have a dependency on `MyAssembly`:</span></span>

```console
ngen display MyAssembly
```

<span data-ttu-id="a141b-392">共有コンポーネント アセンブリに依存するルートを知ることは、共有コンポーネントがアップグレードされた後の `update` アクションの影響を予測する際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a141b-392">Knowing what roots depend on a shared component assembly is useful in gauging the impact of an `update` action after the shared component is upgraded.</span></span>

<span data-ttu-id="a141b-393">アセンブリのファイル拡張子を指定する場合は、パスを指定するか、またはアセンブリが格納されているディレクトリから Ngen.exe を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-393">If you specify an assembly's file extension, you must either specify the path or execute Ngen.exe from the directory containing the assembly:</span></span>

```console
ngen display c:\myApps\MyAssembly.exe
```

<span data-ttu-id="a141b-394">ネイティブ イメージ キャッシュ内で `MyAssembly` という名前を持ち、バージョン 1.0.0.0 であるすべてのネイティブ イメージを表示するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a141b-394">The following command displays all native images in the native image cache with the name `MyAssembly` and the version 1.0.0.0.</span></span>

```console
ngen display "myAssembly, version=1.0.0.0"
```

### <a name="updating-images"></a><span data-ttu-id="a141b-395">イメージの更新</span><span class="sxs-lookup"><span data-stu-id="a141b-395">Updating Images</span></span>

<span data-ttu-id="a141b-396">一般に、共有コンポーネントがアップグレードされると、イメージが更新されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-396">Images are typically updated after a shared component has been upgraded.</span></span> <span data-ttu-id="a141b-397">イメージまたは依存関係が変更されたすべてのネイティブ イメージを更新するには、引数なしで `update` アクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="a141b-397">To update all native images that have changed, or whose dependencies have changed, use the `update` action with no arguments.</span></span>

```console
ngen update
```

<span data-ttu-id="a141b-398">すべてのイメージを更新するプロセスは、長くなることがあります。</span><span class="sxs-lookup"><span data-stu-id="a141b-398">Updating all images can be a lengthy process.</span></span> <span data-ttu-id="a141b-399">ネイティブ イメージ サービスによる更新は、`/queue` オプションを使用してキューに置くことができます。</span><span class="sxs-lookup"><span data-stu-id="a141b-399">You can queue the updates for execution by the native image service by using the `/queue` option.</span></span> <span data-ttu-id="a141b-400">`/queue` オプションとインストールの優先順位の詳細については、「[ネイティブ イメージ サービス](#native-image-service)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a141b-400">For more information on the `/queue` option and installation priorities, see [Native Image Service](#native-image-service).</span></span>

```console
ngen update /queue
```

### <a name="uninstalling-images"></a><span data-ttu-id="a141b-401">イメージのアンインストール</span><span class="sxs-lookup"><span data-stu-id="a141b-401">Uninstalling Images</span></span>

<span data-ttu-id="a141b-402">Ngen.exe は、共有コンポーネントに依存するすべてのアセンブリが削除された場合だけ共有コンポーネントが削除されるように依存関係の一覧を維持します。</span><span class="sxs-lookup"><span data-stu-id="a141b-402">Ngen.exe maintains a list of dependencies, so that shared components are removed only when all assemblies that depend on them have been removed.</span></span> <span data-ttu-id="a141b-403">また、ルートとしてインストールされた共有コンポーネントは削除されません。</span><span class="sxs-lookup"><span data-stu-id="a141b-403">In addition, a shared component is not removed if it has been installed as a root.</span></span>

<span data-ttu-id="a141b-404">次のコマンドは、ルートの `ClientApp.exe` のすべてのシナリオをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="a141b-404">The following command uninstalls all scenarios for the root `ClientApp.exe`:</span></span>

```console
ngen uninstall ClientApp
```

<span data-ttu-id="a141b-405">`uninstall` アクションは、特定のシナリオを削除するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-405">The `uninstall` action can be used to remove specific scenarios.</span></span> <span data-ttu-id="a141b-406">次のコマンドは、ルートの `ClientApp.exe` のすべてのデバッグ シナリオをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="a141b-406">The following command uninstalls all debug scenarios for `ClientApp.exe`:</span></span>

```console
ngen uninstall ClientApp /debug
```

> [!NOTE]
> <span data-ttu-id="a141b-407">`/debug` シナリオをアンインストールしても、`/profile` と `/debug.` の両方を含むシナリオはアンインストールされません。</span><span class="sxs-lookup"><span data-stu-id="a141b-407">Uninstalling `/debug` scenarios does not uninstall a scenario that includes both `/profile` and `/debug.`</span></span>

<span data-ttu-id="a141b-408">次のコマンドは、`ClientApp.exe` の特定のバージョンのすべてのシナリオをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="a141b-408">The following command uninstalls all scenarios for a specific version of `ClientApp.exe`:</span></span>

```console
ngen uninstall "ClientApp, Version=1.0.0.0"
```

<span data-ttu-id="a141b-409">次のコマンドは、`"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` のすべてのシナリオまたはアセンブリのデバッグ シナリオだけをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="a141b-409">The following commands uninstall all scenarios for `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` or just the debug scenario for that assembly:</span></span>

```console
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug
```

<span data-ttu-id="a141b-410">`install` アクションと同様に、拡張子を指定する場合は、アセンブリが格納されているディレクトリから Ngen.exe を実行するか、またはフル パスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-410">As with the `install` action, supplying an extension requires either executing Ngen.exe from the directory containing the assembly or specifying a full path.</span></span>

<span data-ttu-id="a141b-411">ネイティブ イメージ サービスに関連する例については、「[ネイティブ イメージ サービス](#native-image-service)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a141b-411">For examples relating to the native image service, see [Native Image Service](#native-image-service).</span></span>

## <a name="native-image-task"></a><span data-ttu-id="a141b-412">ネイティブ イメージ タスク</span><span class="sxs-lookup"><span data-stu-id="a141b-412">Native Image Task</span></span>

<span data-ttu-id="a141b-413">ネイティブ イメージ タスクは、ネイティブ イメージを生成および保持する Windows タスクです。</span><span class="sxs-lookup"><span data-stu-id="a141b-413">The native image task is a Windows task that generates and maintains native images.</span></span> <span data-ttu-id="a141b-414">ネイティブ イメージ タスクは、サポートされるシナリオでネイティブ イメージを自動的に生成し、解放します。</span><span class="sxs-lookup"><span data-stu-id="a141b-414">The native image task generates and reclaims native images automatically for supported scenarios.</span></span> <span data-ttu-id="a141b-415">また、インストーラーが、[Ngen.exe (ネイティブ イメージ ジェネレーター)](ngen-exe-native-image-generator.md) を使用して、遅延時にネイティブ イメージを生成および更新できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a141b-415">It also enables installers to use [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md) to create and update native images at a deferred time.</span></span>

<span data-ttu-id="a141b-416">各アーキテクチャを対象とするアプリケーションのコンパイルを許可するために、ネイティブ イメージ タスクはコンピューターでサポートされる CPU アーキテクチャごとに一度登録されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-416">The native image task is registered once for each CPU architecture supported on a computer, to allow compilation for applications that target each architecture:</span></span>

|<span data-ttu-id="a141b-417">タスク名</span><span class="sxs-lookup"><span data-stu-id="a141b-417">Task name</span></span>|<span data-ttu-id="a141b-418">32 ビット コンピューター</span><span class="sxs-lookup"><span data-stu-id="a141b-418">32-bit computer</span></span>|<span data-ttu-id="a141b-419">64 ビット コンピューター</span><span class="sxs-lookup"><span data-stu-id="a141b-419">64-bit computer</span></span>|
|---------------|----------------------|----------------------|
|<span data-ttu-id="a141b-420">NET Framework NGEN v4.0.30319</span><span class="sxs-lookup"><span data-stu-id="a141b-420">NET Framework NGEN v4.0.30319</span></span>|<span data-ttu-id="a141b-421">はい</span><span class="sxs-lookup"><span data-stu-id="a141b-421">Yes</span></span>|<span data-ttu-id="a141b-422">はい</span><span class="sxs-lookup"><span data-stu-id="a141b-422">Yes</span></span>|
|<span data-ttu-id="a141b-423">NET Framework NGEN v4.0.30319 64</span><span class="sxs-lookup"><span data-stu-id="a141b-423">NET Framework NGEN v4.0.30319 64</span></span>|<span data-ttu-id="a141b-424">いいえ</span><span class="sxs-lookup"><span data-stu-id="a141b-424">No</span></span>|<span data-ttu-id="a141b-425">はい</span><span class="sxs-lookup"><span data-stu-id="a141b-425">Yes</span></span>|

<span data-ttu-id="a141b-426">ネイティブ イメージ タスクは、Windows 8 以降の実行時に .NET Framework 4.5 以降のバージョンで使用できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-426">The native image task is available in the .NET Framework 4.5 and later versions, when running on Windows 8 or later.</span></span> <span data-ttu-id="a141b-427">Windows の以前のバージョンでは、.NET Framework は[ネイティブ イメージ サービス](#native-image-service)を使用します。</span><span class="sxs-lookup"><span data-stu-id="a141b-427">On earlier versions of Windows, the .NET Framework uses the [Native Image Service](#native-image-service).</span></span>

### <a name="task-lifetime"></a><span data-ttu-id="a141b-428">タスクの有効期間</span><span class="sxs-lookup"><span data-stu-id="a141b-428">Task Lifetime</span></span>

<span data-ttu-id="a141b-429">一般に、Windows タスク スケジューラは、毎晩、コンピューターがアイドル状態のときにネイティブ イメージ タスクを開始します。</span><span class="sxs-lookup"><span data-stu-id="a141b-429">In general, the Windows Task Scheduler starts the native image task every night when the computer is idle.</span></span> <span data-ttu-id="a141b-430">このタスクでは、アプリケーション インストーラーによってキューに入れられている遅延作業、遅延されているネイティブ イメージ更新要求、自動イメージ作成がないかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="a141b-430">The task checks for any deferred work that is queued by application installers, any deferred native image update requests, and any automatic image creation.</span></span> <span data-ttu-id="a141b-431">このタスクは未完了の作業項目を完了すると、停止します。</span><span class="sxs-lookup"><span data-stu-id="a141b-431">The task completes outstanding work items and then shuts down.</span></span> <span data-ttu-id="a141b-432">このタスクの実行中にコンピューターがアイドル状態になると、タスクは停止します。</span><span class="sxs-lookup"><span data-stu-id="a141b-432">If the computer stops being idle while the task is running, the task stops.</span></span>

<span data-ttu-id="a141b-433">また、ネイティブ イメージ タスクは手動で開始することもできます。その場合には、タスク スケジューラ UI を使用するか、NGen.exe を手動で呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a141b-433">You can also start the native image task manually through the Task Scheduler UI or through manual calls to NGen.exe.</span></span> <span data-ttu-id="a141b-434">このいずれかの方法でこのタスクを開始すると、コンピューターがアイドル状態でなくなると実行を続行します。</span><span class="sxs-lookup"><span data-stu-id="a141b-434">If the task is started through either of these methods, it will continue running when the computer is no longer idle.</span></span> <span data-ttu-id="a141b-435">NGen.exe を使用して手動で作成されたイメージは、アプリケーション インストーラーで予測可能な動作を有効にするために優先順位が設定されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-435">Images created manually by using NGen.exe are prioritized to enable predictable behavior for application installers.</span></span>

## <a name="native-image-service"></a><span data-ttu-id="a141b-436">ネイティブ イメージ サービス</span><span class="sxs-lookup"><span data-stu-id="a141b-436">Native Image Service</span></span>

<span data-ttu-id="a141b-437">ネイティブ イメージ サービスは、ネイティブ イメージを生成および保持する Windows サービスです。</span><span class="sxs-lookup"><span data-stu-id="a141b-437">The native image service is a Windows service that generates and maintains native images.</span></span> <span data-ttu-id="a141b-438">ネイティブ イメージ サービスによって、開発者はコンピューターがアイドル状態になるまでネイティブ イメージのインストールと更新を遅延できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-438">The native image service allows the developer to defer the installation and update of native images to periods when the computer is idle.</span></span>

<span data-ttu-id="a141b-439">通常ネイティブ イメージ サービスは、アプリケーションまたはアップデートのインストール プログラム (インストーラー) によって開始されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-439">Normally, the native image service is initiated by the installation program (installer) for an application or update.</span></span> <span data-ttu-id="a141b-440">優先順位 3 のアクションでは、サービスはコンピューターのアイドル時間に実行します。</span><span class="sxs-lookup"><span data-stu-id="a141b-440">For priority 3 actions, the service executes during idle time on the computer.</span></span> <span data-ttu-id="a141b-441">このサービスは自身の状態を保存するため、再起動を繰り返しても必要に応じて続けて実行できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-441">The service saves its state and is capable of continuing through multiple reboots if necessary.</span></span> <span data-ttu-id="a141b-442">複数のイメージ コンパイルをキューに配置できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-442">Multiple image compilations can be queued.</span></span>

<span data-ttu-id="a141b-443">このサービスは、手動の Ngen.exe コマンドともやり取りします。</span><span class="sxs-lookup"><span data-stu-id="a141b-443">The service also interacts with the manual Ngen.exe command.</span></span> <span data-ttu-id="a141b-444">手動で実行するコマンドは、バックグラウンド アクティビティより優先されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-444">Manual commands take precedence over background activity.</span></span>

> [!NOTE]
> <span data-ttu-id="a141b-445">Windows Vista では、ネイティブ イメージ サービスに表示される名前は "Microsoft.NET Framework NGEN v2.0.50727_X86" または "Microsoft.NET Framework NGEN v2.0.50727_X64" です。</span><span class="sxs-lookup"><span data-stu-id="a141b-445">On Windows Vista, the name displayed for the native image service is "Microsoft.NET Framework NGEN v2.0.50727_X86" or "Microsoft.NET Framework NGEN v2.0.50727_X64".</span></span> <span data-ttu-id="a141b-446">これより前のすべてのバージョンの Microsoft Windows では、名前は ".NET Runtime Optimization Service v2.0.50727_X86" または ".NET Runtime Optimization Service v2.0.50727_X64" です。</span><span class="sxs-lookup"><span data-stu-id="a141b-446">On all earlier versions of Microsoft Windows, the name is ".NET Runtime Optimization Service v2.0.50727_X86" or ".NET Runtime Optimization Service v2.0.50727_X64".</span></span>

### <a name="launching-deferred-operations"></a><span data-ttu-id="a141b-447">遅延の操作の起動</span><span class="sxs-lookup"><span data-stu-id="a141b-447">Launching Deferred Operations</span></span>

<span data-ttu-id="a141b-448">インストールまたはアップグレードを開始する前に、サービスを停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a141b-448">Before beginning an installation or upgrade, pausing the service is recommended.</span></span> <span data-ttu-id="a141b-449">これによって、インストーラーがファイルをコピーするか、またはアセンブリをグローバル アセンブリ キャッシュに格納している間に、サービスが実行されないようにできます。</span><span class="sxs-lookup"><span data-stu-id="a141b-449">This ensures that the service does not execute while the installer is copying files or putting assemblies in the global assembly cache.</span></span> <span data-ttu-id="a141b-450">次の Ngen.exe のコマンド ラインによって、サービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="a141b-450">The following Ngen.exe command line pauses the service:</span></span>

```console
ngen queue pause
```

<span data-ttu-id="a141b-451">すべての遅延操作がキューに置かれた後に、次のコマンドによってサービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="a141b-451">When all deferred operations have been queued, the following command allows the service to resume:</span></span>

```console
ngen queue continue
```

<span data-ttu-id="a141b-452">新しいアプリケーションをインストールする場合または共有コンポーネントを更新する場合にネイティブ イメージの生成を遅延するには、`install` アクションまたは `update` アクションで `/queue` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="a141b-452">To defer native image generation when installing a new application or when updating a shared component, use the `/queue` option with the `install` or `update` actions.</span></span> <span data-ttu-id="a141b-453">次の Ngen.exe のコマンド ラインは、共有コンポーネントのネイティブ イメージをインストールし、影響を受けるすべてのルートの更新を実行します。</span><span class="sxs-lookup"><span data-stu-id="a141b-453">The following Ngen.exe command lines install a native image for a shared component and perform an update of all roots that may have been affected:</span></span>

```console
ngen install MyComponent /queue
ngen update /queue
```

<span data-ttu-id="a141b-454">`update` アクションは、`MyComponent` を使用するネイティブ イメージだけでなく、無効になったすべてのネイティブ イメージを再作成します。</span><span class="sxs-lookup"><span data-stu-id="a141b-454">The `update` action regenerates all native images that have been invalidated, not just those that use `MyComponent`.</span></span>

<span data-ttu-id="a141b-455">多くのルートで構成されるアプリケーションでは、遅延されたアクションの優先順位を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-455">If your application consists of many roots, you can control the priority of the deferred actions.</span></span> <span data-ttu-id="a141b-456">次のコマンドは、次の 3 つのルートのインストールをキューに置きます。</span><span class="sxs-lookup"><span data-stu-id="a141b-456">The following commands queue the installation of three roots.</span></span> <span data-ttu-id="a141b-457">`Assembly1` がアイドル時間まで待たずに最初にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a141b-457">`Assembly1` is installed first, without waiting for idle time.</span></span> <span data-ttu-id="a141b-458">`Assembly2` もアイドル時間まで待たずにインストールされますが、優先順位 1 のアクションがすべてインストールされた後にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a141b-458">`Assembly2` is also installed without waiting for idle time, but after all priority 1 actions have completed.</span></span> <span data-ttu-id="a141b-459">`Assembly3` は、コンピューターがアイドル状態になったことをサービスが検出するとインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a141b-459">`Assembly3` is installed when the service detects that the computer is idle.</span></span>

```console
ngen install Assembly1 /queue:1
ngen install Assembly2 /queue:2
ngen install Assembly3 /queue:3
```

<span data-ttu-id="a141b-460">`executeQueuedItems` アクションを使用すると、キューに置かれているアクションを同時に強制的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-460">You can force queued actions to occur synchronously by using the `executeQueuedItems` action.</span></span> <span data-ttu-id="a141b-461">オプションの優先順位を指定すると、このアクションは同等またはそれ以下の優先順位を持っているキュー内のアクションだけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-461">If you supply the optional priority, this action affects only the queued actions that have equal or lower priority.</span></span> <span data-ttu-id="a141b-462">既定の優先順位は 3 であるため、次の Ngen.exe コマンドは、キューに置かれているすべてのアクションを即座に処理し、その処理が完了するまで戻りません。</span><span class="sxs-lookup"><span data-stu-id="a141b-462">The default priority is 3, so the following Ngen.exe command processes all queued actions immediately, and does not return until they are finished:</span></span>

```console
ngen executeQueuedItems
```

<span data-ttu-id="a141b-463">Ngen.exe は同期コマンドを実行し、ネイティブ イメージ サービスは使用しません。</span><span class="sxs-lookup"><span data-stu-id="a141b-463">Synchronous commands are executed by Ngen.exe and do not use the native image service.</span></span> <span data-ttu-id="a141b-464">ネイティブ イメージ サービスの実行中に Ngen.exe を使用してアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-464">You can execute actions using Ngen.exe while the native image service is running.</span></span>

### <a name="service-shutdown"></a><span data-ttu-id="a141b-465">サービスのシャットダウン</span><span class="sxs-lookup"><span data-stu-id="a141b-465">Service Shutdown</span></span>

<span data-ttu-id="a141b-466">`/queue` オプションを組み込んだ Ngen.exe コマンドの実行によって開始されたサービスは、すべてのアクションが完了するまでバックグラウンドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="a141b-466">After being initiated by the execution of an Ngen.exe command that includes the `/queue` option, the service runs in the background until all actions have been completed.</span></span> <span data-ttu-id="a141b-467">このサービスは自身の状態を保存するため、再起動を繰り返しても必要に応じて処理を継続できます。</span><span class="sxs-lookup"><span data-stu-id="a141b-467">The service saves its state so that it can continue through multiple reboots if necessary.</span></span> <span data-ttu-id="a141b-468">キューに待機しているアクションがないことを検出したサービスは、次回コンピューターの再起動のときに再起動されないように自身の状態をリセットしてから、シャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="a141b-468">When the service detects that there are no more actions queued, it resets its status so that it will not restart the next time the computer is booted, and then it shuts itself down.</span></span>

### <a name="service-interaction-with-clients"></a><span data-ttu-id="a141b-469">クライアントとサービスとのやり取り</span><span class="sxs-lookup"><span data-stu-id="a141b-469">Service Interaction with Clients</span></span>

<span data-ttu-id="a141b-470">.NET Framework Version 2.0 では、必ず Ngen.exe というコマンド ライン ツールを使用してネイティブ イメージ サービスとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="a141b-470">In the .NET Framework version 2.0, the only interaction with the native image service is through the command-line tool Ngen.exe.</span></span> <span data-ttu-id="a141b-471">インストール スクリプトでコマンド ライン ツールを使用してネイティブ イメージ サービスのアクションをキューに置いたり、サービスとやり取りしたりします。</span><span class="sxs-lookup"><span data-stu-id="a141b-471">Use the command-line tool in installation scripts to queue actions for the native image service and to interact with the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="a141b-472">関連項目</span><span class="sxs-lookup"><span data-stu-id="a141b-472">See also</span></span>

- [<span data-ttu-id="a141b-473">ツール</span><span class="sxs-lookup"><span data-stu-id="a141b-473">Tools</span></span>](index.md)
- [<span data-ttu-id="a141b-474">マネージド実行プロセス</span><span class="sxs-lookup"><span data-stu-id="a141b-474">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="a141b-475">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="a141b-475">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="a141b-476">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="a141b-476">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
