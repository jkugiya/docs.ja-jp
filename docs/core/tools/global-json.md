---
title: global.json の概要
description: .NET CLI コマンドを実行するときに global.json ファイルを使用して .NET SDK のバージョンを設定する方法について説明します。
ms.topic: how-to
ms.date: 05/01/2020
ms.custom: updateeachrelease
ms.openlocfilehash: cc471cf5b50cf91c38b46607ccf38bd4d087aa6a
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104142"
---
# <a name="globaljson-overview"></a><span data-ttu-id="bc525-103">global.json の概要</span><span class="sxs-lookup"><span data-stu-id="bc525-103">global.json overview</span></span>

<span data-ttu-id="bc525-104">**この記事の対象:** ✔️ .NET Core 2.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="bc525-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<span data-ttu-id="bc525-105">*global.json* ファイルを使うと、.NET CLI コマンドを実行するときに使う .NET SDK のバージョンを定義できます。</span><span class="sxs-lookup"><span data-stu-id="bc525-105">The *global.json* file allows you to define which .NET SDK version is used when you run .NET CLI commands.</span></span> <span data-ttu-id="bc525-106">.NET SDK の選択は、プロジェクトのターゲットであるランタイムの指定とは関係ありません。</span><span class="sxs-lookup"><span data-stu-id="bc525-106">Selecting the .NET SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="bc525-107">.NET SDK のバージョンは、使われている .NET CLI のバージョンを示します。</span><span class="sxs-lookup"><span data-stu-id="bc525-107">The .NET SDK version indicates which versions of the .NET CLI is used.</span></span>

<span data-ttu-id="bc525-108">通常は、最新バージョンの SDK ツールを使うので、*global.json* ファイルは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="bc525-108">In general, you want to use the latest version of the SDK tools, so no *global.json* file is needed.</span></span> <span data-ttu-id="bc525-109">一部の高度なシナリオでは、SDK ツールのバージョンを管理する必要がある場合があります。この記事では、この方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc525-109">In some advanced scenarios, you might want to control the version of the SDK tools, and this article explains how to do this.</span></span>

<span data-ttu-id="bc525-110">代わりにランタイムを指定する方法について詳しくは、「[ターゲット フレームワーク](../../standard/frameworks.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bc525-110">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="bc525-111">.NET SDK は、現在の作業ディレクトリ (プロジェクト ディレクトリと同じではない場合があります) 内、またはその親ディレクトリのいずれかで、*global.json* ファイルを探します。</span><span class="sxs-lookup"><span data-stu-id="bc525-111">The .NET SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="bc525-112">global.json のスキーマ</span><span class="sxs-lookup"><span data-stu-id="bc525-112">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="bc525-113">SDK</span><span class="sxs-lookup"><span data-stu-id="bc525-113">sdk</span></span>

<span data-ttu-id="bc525-114">型: `object`</span><span class="sxs-lookup"><span data-stu-id="bc525-114">Type: `object`</span></span>

<span data-ttu-id="bc525-115">選択する .NET SDK についての情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="bc525-115">Specifies information about the .NET SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="bc525-116">version</span><span class="sxs-lookup"><span data-stu-id="bc525-116">version</span></span>

- <span data-ttu-id="bc525-117">型: `string`</span><span class="sxs-lookup"><span data-stu-id="bc525-117">Type: `string`</span></span>

- <span data-ttu-id="bc525-118">.NET Core 1.0 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="bc525-118">Available since: .NET Core 1.0 SDK.</span></span>

<span data-ttu-id="bc525-119">使用する .NET SDK のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="bc525-119">The version of the .NET SDK to use.</span></span>

<span data-ttu-id="bc525-120">このフィールドでは:</span><span class="sxs-lookup"><span data-stu-id="bc525-120">This field:</span></span>

- <span data-ttu-id="bc525-121">ワイルドカードはサポートされていません。つまり、完全なバージョン番号を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc525-121">Doesn't have wildcard support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="bc525-122">バージョン範囲はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="bc525-122">Doesn't support version ranges.</span></span>

#### <a name="allowprerelease"></a><span data-ttu-id="bc525-123">allowPrerelease</span><span class="sxs-lookup"><span data-stu-id="bc525-123">allowPrerelease</span></span>

- <span data-ttu-id="bc525-124">型: `boolean`</span><span class="sxs-lookup"><span data-stu-id="bc525-124">Type: `boolean`</span></span>

- <span data-ttu-id="bc525-125">.NET Core 3.0 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="bc525-125">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="bc525-126">使用する SDK バージョンを選択するときに、SDK リゾルバーでプレリリース バージョンを考慮する必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="bc525-126">Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>

<span data-ttu-id="bc525-127">この値を明示的に設定しない場合、Visual Studio から実行しているかどうかによって既定値が決まります。</span><span class="sxs-lookup"><span data-stu-id="bc525-127">If you don't set this value explicitly, the default value depends on whether you're running from Visual Studio:</span></span>

- <span data-ttu-id="bc525-128">Visual Studio を使用して **いない** 場合、既定値は `true` になります。</span><span class="sxs-lookup"><span data-stu-id="bc525-128">If you're **not** in Visual Studio, the default value is `true`.</span></span>
- <span data-ttu-id="bc525-129">Visual Studio を使用している場合は、要求されたプレリリース状態が使用されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-129">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="bc525-130">つまり、Visual Studio のプレビュー バージョンを使用している場合、または ( **[ツール]**  >  **[オプション]**  >  **[環境]**  >  **[プレビュー機能]** で) **[.NET Core SDK のプレビューを使用する]** オプションを設定している場合、既定値は `true` で、それ以外の場合は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="bc525-130">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), the default value is `true`; otherwise, `false`.</span></span>

#### <a name="rollforward"></a><span data-ttu-id="bc525-131">rollForward</span><span class="sxs-lookup"><span data-stu-id="bc525-131">rollForward</span></span>

- <span data-ttu-id="bc525-132">型: `string`</span><span class="sxs-lookup"><span data-stu-id="bc525-132">Type: `string`</span></span>

- <span data-ttu-id="bc525-133">.NET Core 3.0 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="bc525-133">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="bc525-134">SDK バージョンを選択するときに、特定の SDK バージョンがない場合のフォールバックとして、またはより新しいバージョンを使用するためのディレクティブとして使用するロールフォワード ポリシー。</span><span class="sxs-lookup"><span data-stu-id="bc525-134">The roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span> <span data-ttu-id="bc525-135">[バージョン](#version) は、`latestMajor` に設定する場合を除き、`rollForward` 値を使用して指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc525-135">A [version](#version) must be specified with a `rollForward` value, unless you're setting it to `latestMajor`.</span></span>
<span data-ttu-id="bc525-136">既定のロールフォワード動作は、[照合ルール](#matching-rules)によって決まります。</span><span class="sxs-lookup"><span data-stu-id="bc525-136">The default roll forward behavior is determined by the [matching rules](#matching-rules).</span></span>

<span data-ttu-id="bc525-137">使用可能なポリシーとその動作を理解するには、`x.y.znn` の形式で SDK バージョンの次の定義を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="bc525-137">To understand the available policies and their behavior, consider the following definitions for an SDK version in the format `x.y.znn`:</span></span>

- <span data-ttu-id="bc525-138">`x` はメジャー バージョンです。</span><span class="sxs-lookup"><span data-stu-id="bc525-138">`x` is the major version.</span></span>
- <span data-ttu-id="bc525-139">`y` はマイナー バージョンです。</span><span class="sxs-lookup"><span data-stu-id="bc525-139">`y` is the minor version.</span></span>
- <span data-ttu-id="bc525-140">`z` は機能帯です。</span><span class="sxs-lookup"><span data-stu-id="bc525-140">`z` is the feature band.</span></span>
- <span data-ttu-id="bc525-141">`nn` はパッチ バージョンです。</span><span class="sxs-lookup"><span data-stu-id="bc525-141">`nn` is the patch version.</span></span>

<span data-ttu-id="bc525-142">`rollForward` キーの有効値を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="bc525-142">The following table shows the possible values for the `rollForward` key:</span></span>

| <span data-ttu-id="bc525-143">[値]</span><span class="sxs-lookup"><span data-stu-id="bc525-143">Value</span></span>         | <span data-ttu-id="bc525-144">動作</span><span class="sxs-lookup"><span data-stu-id="bc525-144">Behavior</span></span> |
| ------------- | ---------- |
| `patch`       | <span data-ttu-id="bc525-145">指定されたバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc525-145">Uses the specified version.</span></span> <br> <span data-ttu-id="bc525-146">見つからない場合は、最新のパッチ レベルにロールフォワードします。</span><span class="sxs-lookup"><span data-stu-id="bc525-146">If not found, rolls forward to the latest patch level.</span></span> <br> <span data-ttu-id="bc525-147">見つからない場合は、失敗します。</span><span class="sxs-lookup"><span data-stu-id="bc525-147">If not found, fails.</span></span> <br><br> <span data-ttu-id="bc525-148">この値は、以前のバージョンの SDK の従来の動作です。</span><span class="sxs-lookup"><span data-stu-id="bc525-148">This value is the legacy behavior from the earlier versions of the SDK.</span></span> |
| `feature`     | <span data-ttu-id="bc525-149">指定されたメジャー、マイナー、および機能帯に対して最新のパッチ レベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc525-149">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="bc525-150">見つからない場合は、同じメジャーまたはマイナー内の次の上位の機能帯にロールフォワードし、その機能帯に最新のパッチ レベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc525-150">If not found, rolls forward to the next higher feature band within the same major/minor and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="bc525-151">見つからない場合は、失敗します。</span><span class="sxs-lookup"><span data-stu-id="bc525-151">If not found, fails.</span></span> |
| `minor`       | <span data-ttu-id="bc525-152">指定されたメジャー、マイナー、および機能帯に対して最新のパッチ レベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc525-152">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="bc525-153">見つからない場合は、同じメジャー バージョンまたはマイナー バージョン内の次の上位の機能帯にロールフォワードし、その機能帯に最新のパッチ レベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc525-153">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="bc525-154">見つからない場合は、同じメジャー内の次の上位のマイナーおよび機能帯にロールフォワードし、その機能帯に最新のパッチ レベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc525-154">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="bc525-155">見つからない場合は、失敗します。</span><span class="sxs-lookup"><span data-stu-id="bc525-155">If not found, fails.</span></span> |
| `major`       | <span data-ttu-id="bc525-156">指定されたメジャー、マイナー、および機能帯に対して最新のパッチ レベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc525-156">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="bc525-157">見つからない場合は、同じメジャー バージョンまたはマイナー バージョン内の次の上位の機能帯にロールフォワードし、その機能帯に最新のパッチ レベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc525-157">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="bc525-158">見つからない場合は、同じメジャー内の次の上位のマイナーおよび機能帯にロールフォワードし、その機能帯に最新のパッチ レベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc525-158">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="bc525-159">見つからない場合は、次の上位のメジャー、マイナー、機能帯にロールフォワードし、その機能帯に最新のパッチ レベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc525-159">If not found, rolls forward to the next higher major, minor, and feature band and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="bc525-160">見つからない場合は、失敗します。</span><span class="sxs-lookup"><span data-stu-id="bc525-160">If not found, fails.</span></span> |
| `latestPatch` | <span data-ttu-id="bc525-161">要求されたメジャー、マイナー、および機能帯が、指定された値以上のパッチ レベルと一致する、インストールされている最新のパッチ レベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc525-161">Uses the latest installed patch level that matches the requested major, minor, and feature band with a patch level and that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="bc525-162">見つからない場合は、失敗します。</span><span class="sxs-lookup"><span data-stu-id="bc525-162">If not found, fails.</span></span> |
| `latestFeature` | <span data-ttu-id="bc525-163">要求されたメジャーおよびマイナーと一致し、機能帯とパッチ レベルが指定された値以上である、インストールされているものの中で最も高い機能帯とパッチ レベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc525-163">Uses the highest installed feature band and patch level that matches the requested major and minor with a feature band and patch level that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="bc525-164">見つからない場合は、失敗します。</span><span class="sxs-lookup"><span data-stu-id="bc525-164">If not found, fails.</span></span> |
| `latestMinor` | <span data-ttu-id="bc525-165">要求されたメジャーと一致し、マイナー、機能帯、パッチ レベルが指定された値以上である、インストールされているものの中で最も高いマイナー、機能帯、パッチ レベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc525-165">Uses the highest installed minor, feature band, and patch level that matches the requested major with a minor, feature band, and patch level that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="bc525-166">見つからない場合は、失敗します。</span><span class="sxs-lookup"><span data-stu-id="bc525-166">If not found, fails.</span></span> |
| `latestMajor` | <span data-ttu-id="bc525-167">バージョンが指定された値以上である、インストールされているものの中で最も高い .NET SDK を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc525-167">Uses the highest installed .NET SDK with a version that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="bc525-168">見つからない場合は、失敗します。</span><span class="sxs-lookup"><span data-stu-id="bc525-168">If not found, fail.</span></span> |
| `disable`     | <span data-ttu-id="bc525-169">ロールフォワードしません。</span><span class="sxs-lookup"><span data-stu-id="bc525-169">Doesn't roll forward.</span></span> <span data-ttu-id="bc525-170">完全一致が必要です。</span><span class="sxs-lookup"><span data-stu-id="bc525-170">Exact match required.</span></span> |

### <a name="msbuild-sdks"></a><span data-ttu-id="bc525-171">msbuild-sdks</span><span class="sxs-lookup"><span data-stu-id="bc525-171">msbuild-sdks</span></span>

<span data-ttu-id="bc525-172">型: `object`</span><span class="sxs-lookup"><span data-stu-id="bc525-172">Type: `object`</span></span>

<span data-ttu-id="bc525-173">個々のプロジェクトではなく、1 か所でプロジェクト SDK バージョンを管理できます。</span><span class="sxs-lookup"><span data-stu-id="bc525-173">Lets you control the project SDK version in one place rather than in each individual project.</span></span> <span data-ttu-id="bc525-174">詳細については、「[プロジェクト SDK の解決方法](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc525-174">For more information, see [How project SDKs are resolved](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved).</span></span>

## <a name="examples"></a><span data-ttu-id="bc525-175">使用例</span><span class="sxs-lookup"><span data-stu-id="bc525-175">Examples</span></span>

<span data-ttu-id="bc525-176">次の例は、プレリリース バージョンを使用しない方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bc525-176">The following example shows how to not use prerelease versions:</span></span>

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

<span data-ttu-id="bc525-177">次の例は、指定したバージョン以上の、インストールされている最新バージョンを使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bc525-177">The following example shows how to use the highest version installed that is greater or equal than the specified version.</span></span> <span data-ttu-id="bc525-178">この JSON では、2.2.200 より前の SDK バージョンがすべて禁止され、3.0.xxx や 3.1.xxx など、2.2.200 以降のバージョンがすべて許可されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-178">The JSON shown disallows any SDK version earlier than 2.2.200 and allows 2.2.200 or any later version, including 3.0.xxx and 3.1.xxx.</span></span>

```json
{
  "sdk": {
    "version": "2.2.200",
    "rollForward": "latestMajor"
  }
}
```

<span data-ttu-id="bc525-179">次の例は、指定された正確なバージョンを使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bc525-179">The following example shows how to use the exact specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

<span data-ttu-id="bc525-180">次の例では、特定のメジャー バージョンとマイナー バージョンでインストールされる最新の機能バンドと修正プログラムのバージョンを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bc525-180">The following example shows how to use the latest feature band and patch version installed of a specific major and minor version.</span></span> <span data-ttu-id="bc525-181">この JSON では、3.1.102 より前の SDK バージョンがすべて禁止され、3.1.103 や 3.1.200 など、3.1.102 とそれ以降の 3.1.xxx バージョンがすべて許可されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-181">The JSON shown disallows any SDK version earlier than 3.1.102 and allows 3.1.102 or any later 3.1.xxx version, such as 3.1.103 or 3.1.200.</span></span>

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestFeature"
  }
}
```

<span data-ttu-id="bc525-182">次の例は、特定のバージョンのインストールされている最新のパッチ バージョンを使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bc525-182">The following example shows how to use the highest patch version installed of a specific version.</span></span> <span data-ttu-id="bc525-183">この JSON では、3.1.102 より前の SDK バージョンがすべて禁止され、3.1.103 や 3.1.199 など、3.1.102 とそれ以降の 3.1.1xx バージョンがすべて許可されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-183">The JSON shown disallows any SDK version earlier than 3.1.102 and allows 3.1.102 or any later 3.1.1xx version, such as 3.1.103 or 3.1.199.</span></span>

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-cli"></a><span data-ttu-id="bc525-184">global.json と .NET CLI</span><span class="sxs-lookup"><span data-stu-id="bc525-184">global.json and the .NET CLI</span></span>

<span data-ttu-id="bc525-185">ご使用のマシンにインストールされている SDK のバージョンを把握しておくと、*global.json* ファイルにそれを設定するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="bc525-185">It's helpful to know which SDK versions are installed on your machine to set one in the *global.json* file.</span></span> <span data-ttu-id="bc525-186">その方法の詳細については、[.NET が既にインストールされていることを確認する方法](../install/how-to-detect-installed-versions.md#check-sdk-versions)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc525-186">For more information on how to do that, see [How to check that .NET is already installed](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span></span>

<span data-ttu-id="bc525-187">.NET SDK の別のバージョンをコンピューターにインストールするには、[.NET のダウンロード](https://dotnet.microsoft.com/download/dotnet) ページにアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="bc525-187">To install additional .NET SDK versions on your machine, visit the [Download .NET](https://dotnet.microsoft.com/download/dotnet) page.</span></span>

<span data-ttu-id="bc525-188">次の例のような [dotnet new](dotnet-new.md) コマンドを実行することにより、新しい *global.json* ファイルを現在のディレクトリに作成できます。</span><span class="sxs-lookup"><span data-stu-id="bc525-188">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a><span data-ttu-id="bc525-189">照合ルール</span><span class="sxs-lookup"><span data-stu-id="bc525-189">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="bc525-190">照合ルールは、すべてのインストール済み .NET のインストール済みランタイムで共通の `dotnet.exe` エントリ ポイントによって管理されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-190">The matching rules are governed by the `dotnet.exe` entry point, which is common across all installed .NET installed runtimes.</span></span> <span data-ttu-id="bc525-191">複数のランタイムがサイドバイサイドでインストールされている場合、または *global.json* ファイルを使用している場合は、インストールされている最も新しいバージョンの .NET ランタイムの照合ルールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-191">The matching rules for the latest installed version of the .NET Runtime are used when you have multiple runtimes installed side-by-side or if or you're using a *global.json* file.</span></span>

## <a name="net-core-3x"></a>[<span data-ttu-id="bc525-192">.NET Core 3.x</span><span class="sxs-lookup"><span data-stu-id="bc525-192">.NET Core 3.x</span></span>](#tab/netcore3x)

<span data-ttu-id="bc525-193">.NET Core 3.0 以降では、使用する SDK のバージョンを決定するときに次のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-193">Starting with .NET Core 3.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="bc525-194">*global.json* ファイルが見つからない場合、または *global.json* で SDK のバージョンまたは `allowPrerelease` 値が指定されていない場合は、インストールされている最新バージョンの SDK が使用されます (`rollForward` を `latestMajor` に設定するのと同じ)。</span><span class="sxs-lookup"><span data-stu-id="bc525-194">If no *global.json* file is found, or *global.json* doesn't specify an SDK version nor an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="bc525-195">プレリリース SDK のバージョンを考慮するかどうかは、`dotnet` の呼び出し方法によって決まります。</span><span class="sxs-lookup"><span data-stu-id="bc525-195">Whether prerelease SDK versions are considered depends on how `dotnet` is being invoked.</span></span>
  - <span data-ttu-id="bc525-196">Visual Studio を使用して **いない** 場合は、プレリリース バージョンが考慮されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-196">If you're **not** in Visual Studio, prerelease versions are considered.</span></span>
  - <span data-ttu-id="bc525-197">Visual Studio を使用している場合は、要求されたプレリリース状態が使用されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-197">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="bc525-198">つまり、Visual Studio のプレビュー バージョンを使用している場合、または ( **[ツール]**  >  **[オプション]**  >  **[環境]**  >  **[プレビュー機能]** で) **[.NET Core SDK のプレビューを使用する]** オプションを設定している場合、プレリリース バージョンが考慮され、それ以外の場合は、リリース バージョンのみが考慮されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-198">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), prerelease versions are considered; otherwise, only release versions are considered.</span></span>
- <span data-ttu-id="bc525-199">SDK のバージョンは指定していないが `allowPrerelease` 値を指定している *global.json* ファイルが見つかった場合は、インストールされている最新の SDK バージョンが使用されます (`rollForward` を `latestMajor` に設定するのと同じ)。</span><span class="sxs-lookup"><span data-stu-id="bc525-199">If a *global.json* file is found that doesn't specify an SDK version but it specifies an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="bc525-200">最新の SDK バージョンをリリースまたはプレリリースにできるかどうかは、`allowPrerelease` の値によって決まります。</span><span class="sxs-lookup"><span data-stu-id="bc525-200">Whether the latest SDK version can be release or prerelease depends on the value of `allowPrerelease`.</span></span> <span data-ttu-id="bc525-201">`true` は、プレリリースバージョンが考慮されることを示し、`false` は、リリース バージョンのみが考慮されることを示します。</span><span class="sxs-lookup"><span data-stu-id="bc525-201">`true` indicates prerelease versions are considered; `false` indicates that only release versions are considered.</span></span>
- <span data-ttu-id="bc525-202">*global.json* ファイルが見つかり、そこで SDK バージョンが指定されている場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="bc525-202">If a *global.json* file is found and it specifies an SDK version:</span></span>

  - <span data-ttu-id="bc525-203">`rollForward` 値が設定されていない場合、`latestPatch` が既定の `rollForward` ポリシーとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-203">If no `rollForward` value is set, it uses `latestPatch` as the default `rollForward` policy.</span></span> <span data-ttu-id="bc525-204">それ以外の場合は、「[rollForward](#rollforward)」セクションで各値とその動作を確認します。</span><span class="sxs-lookup"><span data-stu-id="bc525-204">Otherwise, check each value and their behavior in the [rollForward](#rollforward) section.</span></span>
  - <span data-ttu-id="bc525-205">「[allowPrerelease](#allowprerelease)」セクションには、プレリリース バージョンが考慮されるかどうか、`allowPrerelease` が設定されていない場合の既定の動作についての説明があります。</span><span class="sxs-lookup"><span data-stu-id="bc525-205">Whether prerelease versions are considered and what's the default behavior when `allowPrerelease` isn't set is described in the [allowPrerelease](#allowprerelease) section.</span></span>

## <a name="net-core-2x"></a>[<span data-ttu-id="bc525-206">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bc525-206">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="bc525-207">.NET Core 2.x SDK では、使用する SDK のバージョンを決定するときに次のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-207">In .NET Core 2.x SDK, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="bc525-208">*global.json* ファイルが見つからない場合、または *global.json* で SDK のバージョンが指定されていない場合は、インストールされている最新バージョンの SDK が使用されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-208">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="bc525-209">SDK の最新バージョンはリリースまたはプレリリースのどちらでもよく、最も高いバージョン番号が採用されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-209">Latest SDK version can be either release or prerelease - the highest version number wins.</span></span>
- <span data-ttu-id="bc525-210">*global.json* で SDK のバージョンが指定されている場合:</span><span class="sxs-lookup"><span data-stu-id="bc525-210">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="bc525-211">指定されている SDK のバージョンがコンピューターで見つかった場合は、その厳密なバージョンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-211">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="bc525-212">指定されている SDK のバージョンがコンピューターで見つからない場合は、そのバージョンの SDK の **パッチ バージョン** でインストールされている最新のものが使用されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-212">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="bc525-213">インストールされている最新の SDK **パッチ バージョン** は、リリースまたはプレリリースのどちらでもよく、最も高いバージョン番号が採用されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-213">Latest installed SDK **patch version** can be either release or prerelease - the highest version number wins.</span></span> <span data-ttu-id="bc525-214">.NET Core 2.1 以降では、指定されている **パッチ バージョン** より低い **パッチ バージョン** は、SDK の選択で無視されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-214">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="bc525-215">指定されたバージョンの SDK および適切な SDK **パッチ バージョン** が見つからない場合は、エラーがスローされます。</span><span class="sxs-lookup"><span data-stu-id="bc525-215">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="bc525-216">SDK のバージョンは次の部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-216">The SDK version is composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="bc525-217">SDK バージョン 2.1.100 以降の番号の最後の部分 (`xyz`) の最初の桁 (`x`) は、.NET Core SDK の **機能リリース** を表します。</span><span class="sxs-lookup"><span data-stu-id="bc525-217">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="bc525-218">一般に、リリース サイクルは .NET Core より .NET Core SDK の方が速くなります。</span><span class="sxs-lookup"><span data-stu-id="bc525-218">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="bc525-219">**パッチ バージョン** は、SDK バージョン 2.1.100 以降の番号の最後の部分 (`xyz`) の最後の 2 桁 (`yz`) で定義されます。</span><span class="sxs-lookup"><span data-stu-id="bc525-219">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="bc525-220">たとえば、SDK のバージョンとして `2.1.300` を指定した場合、SDK の選択では `2.1.399` まで検索されますが、`2.1.400` は `2.1.300` のパッチ バージョンとして考慮されません。</span><span class="sxs-lookup"><span data-stu-id="bc525-220">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="bc525-221">.NET Core SDK のバージョン `2.1.100` から `2.1.201` までは、バージョン番号体系の移行の間にリリースされたため、`xyz` の表記を正しく処理していません。</span><span class="sxs-lookup"><span data-stu-id="bc525-221">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="bc525-222">*global.json* ファイルでこれらのバージョンを指定する場合は、指定するバージョンがターゲット コンピューター上にあることを確認するよう強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bc525-222">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

---

## <a name="troubleshoot-build-warnings"></a><span data-ttu-id="bc525-223">ビルドの警告のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="bc525-223">Troubleshoot build warnings</span></span>

* <span data-ttu-id="bc525-224">次の警告は、プロジェクトがプレリリース バージョンの .NET Core SDK を使用してコンパイルされたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="bc525-224">The following warning indicates that your project was compiled using a prerelease version of the .NET Core SDK:</span></span>

  > <span data-ttu-id="bc525-225">.NET Core SDK のプレビュー バージョンを使用しています。</span><span class="sxs-lookup"><span data-stu-id="bc525-225">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="bc525-226">現在のプロジェクトの global.json ファイルを使用して、SDK のバージョンを定義できます。</span><span class="sxs-lookup"><span data-stu-id="bc525-226">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="bc525-227">詳しくは <https://go.microsoft.com/fwlink/?linkid=869452> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc525-227">More at <https://go.microsoft.com/fwlink/?linkid=869452>.</span></span>

  <span data-ttu-id="bc525-228">.NET Core SDK のバージョンには高品質の履歴とコミットメントがあります。</span><span class="sxs-lookup"><span data-stu-id="bc525-228">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="bc525-229">ただし、プレリリース バージョンを使用しない場合は、「[allowPrerelease](#allowprerelease)」セクションで、.NET Core 3.0 SDK 以降のバージョンで使用できるさまざまな方法を確認してください。</span><span class="sxs-lookup"><span data-stu-id="bc525-229">However, if you don't want to use a prerelease version, check the different strategies you can use with the .NET Core 3.0 SDK or a later version in the [allowPrerelease](#allowprerelease) section.</span></span> <span data-ttu-id="bc525-230">.NET Core 3.0 以降のランタイムまたは SDK がインストールされていないマシンの場合は、*global.json* ファイルを作成し、使用する正確なバージョンを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc525-230">For machines that have never had a .NET Core 3.0 or higher Runtime or SDK installed, you need to create a *global.json* file and specify the exact version you want to use.</span></span>

* <span data-ttu-id="bc525-231">次の警告は、プロジェクトのターゲットが EF Core 1.0 または 1.1 であり、.NET Core 2.1 SDK 以降のバージョンと互換性がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="bc525-231">The following warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions:</span></span>

  > <span data-ttu-id="bc525-232">スタートアップ プロジェクト '{startupProject}' で、フレームワーク '.NETCoreApp' バージョン '{targetFrameworkVersion}'</span><span class="sxs-lookup"><span data-stu-id="bc525-232">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="bc525-233">がターゲットになっています。このバージョンの Entity Framework Core .NET コマンド ライン ツールは、バージョン 2.0 以降のみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="bc525-233">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="bc525-234">古いバージョンのツールの使用については、<https://go.microsoft.com/fwlink/?linkid=871254> をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bc525-234">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254>.</span></span>

  <span data-ttu-id="bc525-235">.NET Core 2.1 SDK (バージョン 2.1.300) 以降で、`dotnet ef` コマンドは SDK に含まれています。</span><span class="sxs-lookup"><span data-stu-id="bc525-235">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="bc525-236">プロジェクトをコンパイルするには、.NET Core 2.0 SDK (バージョン 2.1.201) またはそれ以前のバージョンをご利用のコンピューター上にインストールし、*global.json* ファイルを使用して必要な SDK バージョンを定義します。</span><span class="sxs-lookup"><span data-stu-id="bc525-236">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) or earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="bc525-237">`dotnet ef` コマンドの詳細については、「[EF Core .NET コマンドライン ツール](/ef/core/miscellaneous/cli/dotnet)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc525-237">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="bc525-238">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc525-238">See also</span></span>

- [<span data-ttu-id="bc525-239">プロジェクト SDK の解決方法</span><span class="sxs-lookup"><span data-stu-id="bc525-239">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
