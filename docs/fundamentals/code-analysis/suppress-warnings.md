---
title: コード分析の警告を表示しない
description: .NET コード分析の違反を抑制するためのさまざまな方法について説明します。
ms.date: 01/28/2021
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- code analysis, suppress warnings
- suppress code analysis warnings
ms.openlocfilehash: b08e93089975a59fabfeb0daaf6a2a6454b2c7e8
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99217263"
---
# <a name="how-to-suppress-code-analysis-warnings"></a><span data-ttu-id="5ca00-103">コード分析の警告を非表示にする方法</span><span class="sxs-lookup"><span data-stu-id="5ca00-103">How to suppress code analysis warnings</span></span>

<span data-ttu-id="5ca00-104">この記事では、.NET アプリのビルド時にコード分析からの警告を抑制するためのさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5ca00-104">This article covers the various ways you can suppress warnings from code analysis when you build your .NET app.</span></span>

> [!TIP]
> <span data-ttu-id="5ca00-105">開発環境として Visual Studio を使用している場合、 *電球* メニューには、警告を非表示にするコードを生成するオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="5ca00-105">If you're using Visual Studio as your development environment, the *light bulb* menu provides options that generate the code to suppress warnings for you.</span></span> <span data-ttu-id="5ca00-106">詳細については、「 [違反の抑制](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ca00-106">For more information, see [Suppress violations](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations).</span></span>

## <a name="disable-the-rule"></a><span data-ttu-id="5ca00-107">ルールを無効にする</span><span class="sxs-lookup"><span data-stu-id="5ca00-107">Disable the rule</span></span>

<span data-ttu-id="5ca00-108">警告の原因となっているコード分析規則を無効にすると、ファイルまたはプロジェクト全体の規則が無効になります (使用する [構成ファイル](configuration-files.md) のスコープによって異なります)。</span><span class="sxs-lookup"><span data-stu-id="5ca00-108">By disabling the code analysis rule that's causing the warning, you disable the rule for your entire file or project (depending on the scope of the [configuration file](configuration-files.md) that you use).</span></span> <span data-ttu-id="5ca00-109">ルールを無効にするには、構成ファイルで重要度をに設定し `none` ます。</span><span class="sxs-lookup"><span data-stu-id="5ca00-109">To disable the rule, set its severity to `none` in the configuration file.</span></span>

```ini
[*.{cs,vb}]
dotnet_diagnostic.<rule-ID>.severity = none
```

<span data-ttu-id="5ca00-110">規則の重大度の詳細については、「 [規則の重要度の構成](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ca00-110">For more information about rule severities, see [Configure rule severity](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).</span></span>

## <a name="use-a-preprocessor-directive"></a><span data-ttu-id="5ca00-111">プリプロセッサディレクティブを使用する</span><span class="sxs-lookup"><span data-stu-id="5ca00-111">Use a preprocessor directive</span></span>

<span data-ttu-id="5ca00-112">[#Pragma warning (C#)](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)または[Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md)ディレクティブを使用して、特定のコード行についてのみ警告を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="5ca00-112">Use a [#pragma warning (C#)](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) or [Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md) directive to suppress the warning for only a specific line of code.</span></span>

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

## <a name="use-the-suppressmessageattribute"></a><span data-ttu-id="5ca00-113">SuppressMessageAttribute を使用する</span><span class="sxs-lookup"><span data-stu-id="5ca00-113">Use the SuppressMessageAttribute</span></span>

<span data-ttu-id="5ca00-114">を使用すると、 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> ソースファイルまたはプロジェクトのグローバル抑制ファイル (*GlobalSuppressions.cs* または *globalsuppressions*) のいずれかで警告を非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="5ca00-114">You can use a <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> to suppress a warning either in the source file or in a global suppressions file for the project (*GlobalSuppressions.cs* or *GlobalSuppressions.vb*).</span></span> <span data-ttu-id="5ca00-115">この属性は、プロジェクトまたはファイルの特定の部分のみで警告を非表示にする方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="5ca00-115">This attribute provides a way to suppress a warning in only certain parts of your project or file.</span></span>

<span data-ttu-id="5ca00-116">属性の2つの必須の位置指定パラメーター <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> は、ルールの *カテゴリ* と *ルール ID* です。</span><span class="sxs-lookup"><span data-stu-id="5ca00-116">The two required, positional parameters for the <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribute are the *category* of the rule and the *rule ID*.</span></span> <span data-ttu-id="5ca00-117">次のコードスニペットは `"Usage"` 、 `"CA2200:Rethrow to preserve stack details"` これらのパラメーターにとを渡します。</span><span class="sxs-lookup"><span data-stu-id="5ca00-117">The following code snippet passes `"Usage"` and `"CA2200:Rethrow to preserve stack details"` for these parameters.</span></span>

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

<span data-ttu-id="5ca00-118">グローバル抑制ファイルに属性を追加する場合は、抑制の範囲を目的のレベルに [限定](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) します。たとえば、のようにし `"member"` ます。</span><span class="sxs-lookup"><span data-stu-id="5ca00-118">If you add the attribute to the global suppressions file, you [scope](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) the suppression to the desired level, for example `"member"`.</span></span> <span data-ttu-id="5ca00-119">警告を抑制する API は、プロパティを使用して指定し <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> ます。</span><span class="sxs-lookup"><span data-stu-id="5ca00-119">You specify the API where the warning should be suppressed using the <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> property.</span></span>

```csharp
[assembly: SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.", Scope = "member", Target = "~M:MyApp.Program.IngorableCharacters")]
```

<span data-ttu-id="5ca00-120">明示的に指定されたユーザーソースにマップされない、コンパイラによって生成されるコードの警告を抑制するには、抑制属性をグローバル抑制ファイルに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ca00-120">To suppress warnings for compiler-generated code that doesn't map to explicitly provided user source, you must put the suppression attribute in a global suppressions file.</span></span> <span data-ttu-id="5ca00-121">たとえば、次のコードは、コンパイラによって生成されたコンストラクターに対する違反を抑制します。</span><span class="sxs-lookup"><span data-stu-id="5ca00-121">For example, the following code suppresses a violation against a compiler-emitted constructor:</span></span>

```csharp
[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="MyTools.Type..ctor()")]
```

## <a name="see-also"></a><span data-ttu-id="5ca00-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ca00-122">See also</span></span>

- [<span data-ttu-id="5ca00-123">違反を抑制する (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="5ca00-123">Suppress violations (Visual Studio)</span></span>](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)
