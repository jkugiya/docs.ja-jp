---
title: '破壊的変更:CA1416: プラットフォームの互換性'
description: .NET 5 での破壊的変更について学習します。これは、コード分析ルール CA1416 の有効化によって発生します。
ms.date: 09/29/2020
ms.openlocfilehash: 0464e7bb5a494543c0201efa4630e82897b464c0
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257857"
---
# <a name="warning-ca1416-platform-compatibility"></a><span data-ttu-id="7e056-103">警告 CA1416:プラットフォームの互換性</span><span class="sxs-lookup"><span data-stu-id="7e056-103">Warning CA1416: Platform compatibility</span></span>

<span data-ttu-id="7e056-104">.NET コード アナライザー ルール [CA1416](/visualstudio/code-quality/ca1416) は、.NET 5.0 以降では既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="7e056-104">.NET code analyzer rule [CA1416](/visualstudio/code-quality/ca1416) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="7e056-105">オペレーティング システムが検証されていない呼び出しサイトからのプラットフォーム固有の API への呼び出しに対し、ビルドの警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7e056-105">It produces a build warning for calls to platform-specific APIs from call sites that don't verify the operating system.</span></span>

## <a name="change-description"></a><span data-ttu-id="7e056-106">変更内容</span><span class="sxs-lookup"><span data-stu-id="7e056-106">Change description</span></span>

<span data-ttu-id="7e056-107">.NET 5 以降、.NET SDK には [.NET ソース コード アナライザー](../../../../fundamentals/code-analysis/overview.md)が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7e056-107">Starting in .NET 5, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="7e056-108">これらのルールのいくつかは、[CA1416](/visualstudio/code-quality/ca1416) を含め、既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="7e056-108">Several of these rules are enabled, by default, including [CA1416](/visualstudio/code-quality/ca1416).</span></span> <span data-ttu-id="7e056-109">このルールに違反し、警告をエラーとして扱うように構成されているコードがプロジェクトに含まれている場合、この変更によってビルドが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7e056-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span> <span data-ttu-id="7e056-110">ルール CA1416 では、プラットフォームのコンテキストが検証されていない場所からプラットフォーム固有の API を使用していることが通知されます。</span><span class="sxs-lookup"><span data-stu-id="7e056-110">Rule CA1416 informs you when you're using platform-specific APIs from places where the platform context isn't verified.</span></span>

<span data-ttu-id="7e056-111">ルール [CA1416](/visualstudio/code-quality/ca1416) のプラットフォーム互換性アナライザーは、.NET 5.0 の他の新機能の一部と連携して動作します。</span><span class="sxs-lookup"><span data-stu-id="7e056-111">Rule [CA1416](/visualstudio/code-quality/ca1416), the platform compatibility analyzer, works hand-in-hand with some other features that are new in .NET 5.0.</span></span> <span data-ttu-id="7e056-112">.NET 5 において導入された <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> と <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> では、API がサポートされて "*いる*"、またはサポートされて "*いない*" プラットフォームを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7e056-112">.NET 5 introduces the <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> and <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>, which let you specify the platforms that an API *is* or *isn't* supported on.</span></span> <span data-ttu-id="7e056-113">これらの属性が存在しない場合、API はすべてのプラットフォームでサポートされているものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="7e056-113">In the absence of these attributes, an API is assumed to be supported on all platforms.</span></span> <span data-ttu-id="7e056-114">これらの属性は、Core .NET ライブラリ内のプラットフォーム固有の API に適用されています。</span><span class="sxs-lookup"><span data-stu-id="7e056-114">These attributes have been applied to platform-specific APIs in the core .NET libraries.</span></span>

<span data-ttu-id="7e056-115">プロジェクトで使用されている API が、プロジェクトのターゲット プラットフォームでは使用できないものである場合、ルール [CA1416](/visualstudio/code-quality/ca1416) により、プラットフォームのコンテキストが検証されないプラットフォーム固有のすべての API 呼び出しに、フラグが設定されます。</span><span class="sxs-lookup"><span data-stu-id="7e056-115">In projects that target platforms for which APIs that they use aren't available, rule [CA1416](/visualstudio/code-quality/ca1416) flags any platform-specific API call where the platform context isn't verified.</span></span> <span data-ttu-id="7e056-116"><xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> 属性および <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> 属性で装飾されている API のほとんどでは、サポートされていないオペレーティング システムで呼び出されると、<xref:System.PlatformNotSupportedException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="7e056-116">Most of the APIs that are now decorated with the <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> and <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> attributes throw <xref:System.PlatformNotSupportedException> exceptions when they're invoked on an unsupported operating system.</span></span> <span data-ttu-id="7e056-117">これらの API はプラットフォーム固有としてマークされるようになったので、ルール [CA1416](/visualstudio/code-quality/ca1416) は、OS のチェックを呼び出しサイトに追加することで、実行時の <xref:System.PlatformNotSupportedException> 例外を回避するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7e056-117">Now that these APIs are marked as platform-specific, rule [CA1416](/visualstudio/code-quality/ca1416) helps you prevent run-time <xref:System.PlatformNotSupportedException> exceptions by adding OS checks to your call sites.</span></span>

## <a name="examples"></a><span data-ttu-id="7e056-118">例</span><span class="sxs-lookup"><span data-stu-id="7e056-118">Examples</span></span>

- <span data-ttu-id="7e056-119"><xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType> メソッドは Windows でのみサポートされており、`[SupportedOSPlatform("windows")]` で修飾されます。</span><span class="sxs-lookup"><span data-stu-id="7e056-119">The <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType> method is only supported on Windows and is decorated with `[SupportedOSPlatform("windows")]`.</span></span> <span data-ttu-id="7e056-120">次のコードでは、プロジェクトの[ターゲット](../../../../standard/frameworks.md)が `net5.0` である場合 (ただし `net5.0-windows` は除きます)、ビルド時に CA1416 警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7e056-120">The following code will produce a CA1416 warning at build time if the project [targets](../../../../standard/frameworks.md) `net5.0` (but not `net5.0-windows`).</span></span> <span data-ttu-id="7e056-121">警告を回避するために実行できる対応については、「[推奨アクション](#recommended-action)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e056-121">For actions you can take to avoid the warning, see [Recommended action](#recommended-action).</span></span>

  ```csharp
  public void PlayCMajor()
  {
      Console.Beep(261, 1000);
  }
  ```

- <span data-ttu-id="7e056-122"><xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> メソッドは、ブラウザーではサポートされておらず、`[UnsupportedOSPlatform("browser")]` で修飾されます。</span><span class="sxs-lookup"><span data-stu-id="7e056-122">The <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> method is not supported in the browser and is decorated with `[UnsupportedOSPlatform("browser")]`.</span></span> <span data-ttu-id="7e056-123">次のコードでは、プロジェクトでブラウザー プラットフォームがサポートされている場合、ビルド時に CA1416 警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7e056-123">The following code will produce a CA1416 warning at build time if the project supports the browser platform.</span></span>

  ```csharp
  public void CreateImage()
  {
      Image newImage = Image.FromFile("SampImag.jpg");
  }
  ```

  > [!TIP]
  >
  > - <span data-ttu-id="7e056-124">Blazor WebAssembly プロジェクトおよび Razor クラス ライブラリ プロジェクトには、ブラウザー サポートが自動的に含まれます。</span><span class="sxs-lookup"><span data-stu-id="7e056-124">Blazor WebAssembly projects and Razor class library projects include browser support automatically.</span></span>
  > - <span data-ttu-id="7e056-125">プロジェクトのサポート対象プラットフォームとしてブラウザーを手動で追加するには、プロジェクト ファイルに次のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="7e056-125">To manually add the browser as a supported platform for your project, add the following entry to your project file:</span></span>
  >
  >  ```xml
  >  <ItemGroup>
  >    <SupportedPlatform Include="browser" />
  >  </ItemGroup>
  >  ```

## <a name="version-introduced"></a><span data-ttu-id="7e056-126">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="7e056-126">Version introduced</span></span>

<span data-ttu-id="7e056-127">5.0</span><span class="sxs-lookup"><span data-stu-id="7e056-127">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="7e056-128">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="7e056-128">Recommended action</span></span>

<span data-ttu-id="7e056-129">コードが適切なプラットフォームで実行されている場合にのみ、プラットフォーム固有の API を呼び出すようにします。</span><span class="sxs-lookup"><span data-stu-id="7e056-129">Ensure that platform-specific APIs are only called when the code is running on an appropriate platform.</span></span> <span data-ttu-id="7e056-130">プラットフォーム固有の API を呼び出す前に、<xref:System.OperatingSystem?displayProperty=nameWithType> クラスの `Is<Platform>` メソッドのいずれか (<xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> など) を使用して、現在のオペレーティング システムを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="7e056-130">You can check the current operating system using one of the `Is<Platform>` methods in the <xref:System.OperatingSystem?displayProperty=nameWithType> class, for example, <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType>, before calling a platform-specific API.</span></span>

<span data-ttu-id="7e056-131">`if` ステートメントの条件内で、`Is<Platform>` メソッドのいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7e056-131">You can use one of the `Is<Platform>` methods in the condition of an `if` statement:</span></span>

```csharp
public void PlayCMajor()
{
    if (OperatingSystem.IsWindows())
    {
        Console.Beep(261, 1000);
    }
}
```

<span data-ttu-id="7e056-132">または、`if` ステートメントを追加して実行時のオーバーヘッドを増やしたくない場合は、代わりに <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7e056-132">Or, if you don't want the overhead of an additional `if` statement at run time, call <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> instead:</span></span>

```csharp
public void PlayCMajor()
{
    Debug.Assert(OperatingSystem.IsWindows());
    Console.Beep(261, 1000);
}
```

<span data-ttu-id="7e056-133">ライブラリを作成している場合は、API をプラットフォーム固有としてマークできます。</span><span class="sxs-lookup"><span data-stu-id="7e056-133">If you're authoring a library, you can mark your API as platform-specific.</span></span> <span data-ttu-id="7e056-134">この場合、要件を確認する責任は呼び出し元にあります。</span><span class="sxs-lookup"><span data-stu-id="7e056-134">In this case, the burden of checking requirements falls on your callers.</span></span> <span data-ttu-id="7e056-135">特定のメソッドや型、またはアセンブリ全体をマークできます。</span><span class="sxs-lookup"><span data-stu-id="7e056-135">You can mark specific methods or types or an entire assembly.</span></span>

```csharp
[SupportedOSPlatform("windows")]
public void PlayCMajor()
{
    Console.Beep(261, 1000);
}
```

<span data-ttu-id="7e056-136">すべての呼び出しサイトを修正したくない場合は、次のいずれかのオプションを選択して警告を抑制できます。</span><span class="sxs-lookup"><span data-stu-id="7e056-136">If you don't want to fix all your call sites, you can choose one of the following options to suppress the warning:</span></span>

- <span data-ttu-id="7e056-137">ルール CA1416 を抑制するには、`#pragma` または [-nowarn](../../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) コンパイラ フラグを使用するか、.editorconfig ファイルで[ルールの重大度を `none` に設定](../../../../fundamentals/code-analysis/configuration-options.md#severity-level)します。</span><span class="sxs-lookup"><span data-stu-id="7e056-137">To suppress rule CA1416, you can do so using `#pragma` or the [-nowarn](../../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) compiler flag, or by [setting the rule's severity](../../../../fundamentals/code-analysis/configuration-options.md#severity-level) to `none` in an .editorconfig file.</span></span>

  ```csharp
  public void PlayCMajor()
  {
  #pragma warning disable CA1416
      Console.Beep(261, 1000);
  #pragma warning restore CA1416
  }
  ```

- <span data-ttu-id="7e056-138">コード分析を完全に無効にするには、プロジェクト ファイルで `EnableNETAnalyzers` を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="7e056-138">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="7e056-139">詳細については、「[EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e056-139">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="7e056-140">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="7e056-140">Affected APIs</span></span>

<span data-ttu-id="7e056-141">Windows プラットフォームの場合:</span><span class="sxs-lookup"><span data-stu-id="7e056-141">For Windows platform:</span></span>

- <span data-ttu-id="7e056-142"><https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md> に記載されているすべての API。</span><span class="sxs-lookup"><span data-stu-id="7e056-142">All APIs listed at <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md>.</span></span>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>

<span data-ttu-id="7e056-143">Blazor WebAssembly の場合:</span><span class="sxs-lookup"><span data-stu-id="7e056-143">For Blazor WebAssembly platform:</span></span>

- <span data-ttu-id="7e056-144"><https://github.com/dotnet/runtime/issues/41087> に記載されているすべての API。</span><span class="sxs-lookup"><span data-stu-id="7e056-144">All APIs listed at <https://github.com/dotnet/runtime/issues/41087>.</span></span>

<!--

### Affected APIs

- ``

### Category

- Code analysis
- Core .NET libraries

-->

## <a name="see-also"></a><span data-ttu-id="7e056-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e056-145">See also</span></span>

- [<span data-ttu-id="7e056-146">CA1416:プラットフォームの互換性を検証する</span><span class="sxs-lookup"><span data-stu-id="7e056-146">CA1416: Validate platform compatibility</span></span>](/visualstudio/code-quality/ca1416)
- [<span data-ttu-id="7e056-147">.NET API アナライザー</span><span class="sxs-lookup"><span data-stu-id="7e056-147">.NET API analyzer</span></span>](../../../../standard/analyzers/api-analyzer.md)
