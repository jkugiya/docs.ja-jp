---
title: コード分析の警告を抑制する
description: .NET コード分析の違反を抑制するためのさまざまな方法について説明します。
ms.date: 01/28/2021
ms-topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- code analysis, suppress warnings
- suppress code analysis warnings
ms.openlocfilehash: a2c85a032c8754be2a1c5c6c8cee06754b3231f2
ms.sourcegitcommit: 8f71a6c655a9c39d5223401aed76c02ba00e03ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2021
ms.locfileid: "107740554"
---
# <a name="how-to-suppress-code-analysis-warnings"></a><span data-ttu-id="8d38b-103">コード分析の警告を抑制する方法</span><span class="sxs-lookup"><span data-stu-id="8d38b-103">How to suppress code analysis warnings</span></span>

<span data-ttu-id="8d38b-104">この記事では、.NET アプリのビルド時にコード分析からの警告を抑制するためのさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8d38b-104">This article covers the various ways you can suppress warnings from code analysis when you build your .NET app.</span></span>

> [!TIP]
> <span data-ttu-id="8d38b-105">開発環境として Visual Studio を使用している場合、"*電球*" メニューに、警告を非表示にするコードを生成するオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="8d38b-105">If you're using Visual Studio as your development environment, the *light bulb* menu provides options that generate the code to suppress warnings for you.</span></span> <span data-ttu-id="8d38b-106">詳細については、「[違反を抑制する](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d38b-106">For more information, see [Suppress violations](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations).</span></span>

## <a name="disable-the-rule"></a><span data-ttu-id="8d38b-107">規則を無効にする</span><span class="sxs-lookup"><span data-stu-id="8d38b-107">Disable the rule</span></span>

<span data-ttu-id="8d38b-108">警告の原因となっているコード分析規則を無効にすると、ファイルまたはプロジェクト全体に対して規則が無効になります (使用する[構成ファイル](configuration-files.md)のスコープによって異なります)。</span><span class="sxs-lookup"><span data-stu-id="8d38b-108">By disabling the code analysis rule that's causing the warning, you disable the rule for your entire file or project (depending on the scope of the [configuration file](configuration-files.md) that you use).</span></span> <span data-ttu-id="8d38b-109">規則を無効にするには、構成ファイルでその重大度を `none` に設定します。</span><span class="sxs-lookup"><span data-stu-id="8d38b-109">To disable the rule, set its severity to `none` in the configuration file.</span></span>

```ini
[*.{cs,vb}]
dotnet_diagnostic.<rule-ID>.severity = none
```

<span data-ttu-id="8d38b-110">規則の重大度の詳細については、[規則の重大度の構成](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d38b-110">For more information about rule severities, see [Configure rule severity](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).</span></span>

## <a name="use-a-preprocessor-directive"></a><span data-ttu-id="8d38b-111">プリプロセッサ ディレクティブを使用する</span><span class="sxs-lookup"><span data-stu-id="8d38b-111">Use a preprocessor directive</span></span>

<span data-ttu-id="8d38b-112">[#pragma warning (C#)](../../csharp/language-reference/preprocessor-directives.md#pragma-warning) または [Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md) ディレクティブを使用して、特定のコード行に対してのみ警告を抑制にします。</span><span class="sxs-lookup"><span data-stu-id="8d38b-112">Use a [#pragma warning (C#)](../../csharp/language-reference/preprocessor-directives.md#pragma-warning) or [Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md) directive to suppress the warning for only a specific line of code.</span></span>

```csharp
    try { ... }
    catch (Exception e)
    {
#pragma warning disable CA2200 // Rethrow to preserve stack details
        throw e;
#pragma warning restore CA2200 // Rethrow to preserve stack details
    }
```

```vb
    Try
        ...
    Catch e As Exception
#Disable Warning CA2200 ' Rethrow to preserve stack details
        Throw e
#Enable Warning CA2200 ' Rethrow to preserve stack details
    End Try
```

## <a name="use-the-suppressmessageattribute"></a><span data-ttu-id="8d38b-113">SuppressMessageAttribute を使用する</span><span class="sxs-lookup"><span data-stu-id="8d38b-113">Use the SuppressMessageAttribute</span></span>

<span data-ttu-id="8d38b-114"><xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> を使用すると、ソース ファイルまたはプロジェクトのグローバル抑制ファイル (*GlobalSuppressions.cs* または *GlobalSuppressions.vb*) のいずれかで警告を抑制することができます。</span><span class="sxs-lookup"><span data-stu-id="8d38b-114">You can use a <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> to suppress a warning either in the source file or in a global suppressions file for the project (*GlobalSuppressions.cs* or *GlobalSuppressions.vb*).</span></span> <span data-ttu-id="8d38b-115">この属性は、プロジェクトまたはファイルの特定の部分でのみ警告を抑制する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="8d38b-115">This attribute provides a way to suppress a warning in only certain parts of your project or file.</span></span>

<span data-ttu-id="8d38b-116"><xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 属性の 2 つの必須の位置指定パラメーターは、規則の *category* と *rule ID* です。</span><span class="sxs-lookup"><span data-stu-id="8d38b-116">The two required, positional parameters for the <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribute are the *category* of the rule and the *rule ID*.</span></span> <span data-ttu-id="8d38b-117">次のコード スニペットは、これらのパラメーターに `"Usage"` と `"CA2200:Rethrow to preserve stack details"` を渡します。</span><span class="sxs-lookup"><span data-stu-id="8d38b-117">The following code snippet passes `"Usage"` and `"CA2200:Rethrow to preserve stack details"` for these parameters.</span></span>

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.")]
private static void IngorableCharacters()
{
    try
    {
        ...
    }
    catch (Exception e)
    {
        throw e;
    }
}
```

<span data-ttu-id="8d38b-118">グローバル抑制ファイルに属性を追加する場合は、抑制の[スコープ](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope)を `"member"` などの目的のレベルに設定します。</span><span class="sxs-lookup"><span data-stu-id="8d38b-118">If you add the attribute to the global suppressions file, you [scope](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) the suppression to the desired level, for example `"member"`.</span></span> <span data-ttu-id="8d38b-119"><xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> プロパティを使用して、警告を抑制すべき API を指定します。</span><span class="sxs-lookup"><span data-stu-id="8d38b-119">You specify the API where the warning should be suppressed using the <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> property.</span></span>

```csharp
[assembly: SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.", Scope = "member", Target = "~M:MyApp.Program.IngorableCharacters")]
```

<span data-ttu-id="8d38b-120">明示的に指定されたユーザー ソースにマップされない、コンパイラによって生成されるコードの警告を抑制するには、抑制属性をグローバル抑制ファイル内に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d38b-120">To suppress warnings for compiler-generated code that doesn't map to explicitly provided user source, you must put the suppression attribute in a global suppressions file.</span></span> <span data-ttu-id="8d38b-121">たとえば、次のコードは、コンパイラによって出力されたコンストラクターに対する違反を抑制します。</span><span class="sxs-lookup"><span data-stu-id="8d38b-121">For example, the following code suppresses a violation against a compiler-emitted constructor:</span></span>

```csharp
[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="MyTools.Type..ctor()")]
```

## <a name="see-also"></a><span data-ttu-id="8d38b-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d38b-122">See also</span></span>

- [<span data-ttu-id="8d38b-123">違反を抑制する (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="8d38b-123">Suppress violations (Visual Studio)</span></span>](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)
