---
title: 破壊的変更:CA1417:P/Invoke 用の文字列パラメーターの OutAttribute
description: コード分析ルール CA1417 の有効化によって発生する .NET 5 での破壊的変更について説明します。
ms.date: 09/29/2020
ms.openlocfilehash: 74aa6dc867bc1eb62e32dd086dd6b43f62e7f01f
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257831"
---
# <a name="warning-ca1417-outattribute-on-string-parameter-for-pinvoke"></a><span data-ttu-id="22e4d-103">警告 CA1417:P/Invoke 用の文字列パラメーターの OutAttribute</span><span class="sxs-lookup"><span data-stu-id="22e4d-103">Warning CA1417: OutAttribute on string parameter for P/Invoke</span></span>

<span data-ttu-id="22e4d-104">.NET コード アナライザー ルール [CA1417](/visualstudio/code-quality/ca1417) は、.NET 5.0 以降では既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="22e4d-104">.NET code analyzer rule [CA1417](/visualstudio/code-quality/ca1417) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="22e4d-105"><xref:System.String> パラメーターが値渡しされ、<xref:System.Runtime.InteropServices.OutAttribute> でマークされる[プラットフォーム呼び出し (P/Invoke)](../../../../standard/native-interop/pinvoke.md) メソッド定義に対して、ビルド警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="22e4d-105">It produces a build warning for any [Platform Invoke (P/Invoke)](../../../../standard/native-interop/pinvoke.md) method definitions where a <xref:System.String> parameter is passed by value and marked with <xref:System.Runtime.InteropServices.OutAttribute>.</span></span>

## <a name="change-description"></a><span data-ttu-id="22e4d-106">変更内容</span><span class="sxs-lookup"><span data-stu-id="22e4d-106">Change description</span></span>

<span data-ttu-id="22e4d-107">.NET 5 以降、.NET SDK には [.NET ソース コード アナライザー](../../../../fundamentals/code-analysis/overview.md)が含まれています。</span><span class="sxs-lookup"><span data-stu-id="22e4d-107">Starting in .NET 5, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="22e4d-108">これらのルールのいくつかは、[CA1417](/visualstudio/code-quality/ca1417) を含め、既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="22e4d-108">Several of these rules are enabled, by default, including [CA1417](/visualstudio/code-quality/ca1417).</span></span> <span data-ttu-id="22e4d-109">このルールに違反し、警告をエラーとして扱うように構成されているコードがプロジェクトに含まれている場合、この変更によってビルドが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="22e4d-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="22e4d-110"><xref:System.String> パラメーターが <xref:System.Runtime.InteropServices.OutAttribute> 属性でマークされ、値渡しされる [P/Invoke](../../../../standard/native-interop/pinvoke.md) メソッド定義には、ルール CA1417 によってフラグが立てられます。</span><span class="sxs-lookup"><span data-stu-id="22e4d-110">Rule CA1417 flags [P/Invoke](../../../../standard/native-interop/pinvoke.md) method definitions where a <xref:System.String> parameter is marked with the <xref:System.Runtime.InteropServices.OutAttribute> attribute and is passed by value.</span></span> <span data-ttu-id="22e4d-111">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="22e4d-111">For example:</span></span>

```csharp
[DllImport("MyLibrary")]
private static extern void PIMethod([Out] string s);
```

<span data-ttu-id="22e4d-112">.NET ランタイムでは、インターン プールと呼ばれるテーブルが保持されます。これには、プログラム内の各一意のリテラル文字列への単一の参照が含まれています。</span><span class="sxs-lookup"><span data-stu-id="22e4d-112">The .NET runtime maintains a table, called the intern pool, that contains a single reference to each unique literal string in a program.</span></span> <span data-ttu-id="22e4d-113"><xref:System.Runtime.InteropServices.OutAttribute> でマークされたインターン文字列が P/Invoke メソッドに値渡しされる場合、ランタイムが不安定になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="22e4d-113">If an interned string marked with <xref:System.Runtime.InteropServices.OutAttribute> is passed by value to a P/Invoke method, the runtime can be destabilized.</span></span> <span data-ttu-id="22e4d-114">文字列インターンの詳細については、<xref:System.String.Intern(System.String)?displayProperty=nameWithType> に関する注釈を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22e4d-114">For more information about string interning, see the remarks for <xref:System.String.Intern(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="22e4d-115">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="22e4d-115">Version introduced</span></span>

<span data-ttu-id="22e4d-116">5.0</span><span class="sxs-lookup"><span data-stu-id="22e4d-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="22e4d-117">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="22e4d-117">Recommended action</span></span>

- <span data-ttu-id="22e4d-118">変更された文字列データを呼び出し元にマーシャリングする必要がある場合は、代わりに文字列を参照渡しにします。</span><span class="sxs-lookup"><span data-stu-id="22e4d-118">If you need to marshal modified string data back to the caller, pass the string by reference instead.</span></span>

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(out string s);
  ```

- <span data-ttu-id="22e4d-119">変更した文字列データを呼び出し元にマーシャリングする必要がない場合は、<xref:System.Runtime.InteropServices.OutAttribute> を削除するだけです。</span><span class="sxs-lookup"><span data-stu-id="22e4d-119">If you don't need to marshal modified string data back to the caller, simply remove the <xref:System.Runtime.InteropServices.OutAttribute>.</span></span>

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(string s);
  ```

  <span data-ttu-id="22e4d-120">詳細については、[CA1417](/visualstudio/code-quality/ca1417) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22e4d-120">For more information, see [CA1417](/visualstudio/code-quality/ca1417).</span></span>

- <span data-ttu-id="22e4d-121">コード分析を完全に無効にするには、プロジェクト ファイルで `EnableNETAnalyzers` を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="22e4d-121">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="22e4d-122">詳細については、「[EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22e4d-122">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="22e4d-123">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="22e4d-123">Affected APIs</span></span>

<span data-ttu-id="22e4d-124">API 分析では検出できません。</span><span class="sxs-lookup"><span data-stu-id="22e4d-124">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
