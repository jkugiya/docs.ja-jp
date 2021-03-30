---
title: コード分析の警告を抑制する
description: .NET コード分析の違反を抑制するためのさまざまな方法について説明します。
ms.date: 01/28/2021
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- code analysis, suppress warnings
- suppress code analysis warnings
ms.openlocfilehash: a8fdfbddd2393f9c6c8cd882a63a9ecc6cb1dc95
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637040"
---
# <a name="how-to-suppress-code-analysis-warnings"></a>コード分析の警告を抑制する方法

この記事では、.NET アプリのビルド時にコード分析からの警告を抑制するためのさまざまな方法について説明します。

> [!TIP]
> 開発環境として Visual Studio を使用している場合、"*電球*" メニューに、警告を非表示にするコードを生成するオプションが用意されています。 詳細については、「[違反を抑制する](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)」を参照してください。

## <a name="disable-the-rule"></a>規則を無効にする

警告の原因となっているコード分析規則を無効にすると、ファイルまたはプロジェクト全体に対して規則が無効になります (使用する[構成ファイル](configuration-files.md)のスコープによって異なります)。 規則を無効にするには、構成ファイルでその重大度を `none` に設定します。

```ini
[*.{cs,vb}]
dotnet_diagnostic.<rule-ID>.severity = none
```

規則の重大度の詳細については、[規則の重大度の構成](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level)に関するセクションを参照してください。

## <a name="use-a-preprocessor-directive"></a>プリプロセッサ ディレクティブを使用する

[#pragma warning (C#)](../../csharp/language-reference/preprocessor-directives.md#pragma-warning) または [Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md) ディレクティブを使用して、特定のコード行に対してのみ警告を抑制にします。

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

## <a name="use-the-suppressmessageattribute"></a>SuppressMessageAttribute を使用する

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> を使用すると、ソース ファイルまたはプロジェクトのグローバル抑制ファイル (*GlobalSuppressions.cs* または *GlobalSuppressions.vb*) のいずれかで警告を抑制することができます。 この属性は、プロジェクトまたはファイルの特定の部分でのみ警告を抑制する方法を提供します。

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 属性の 2 つの必須の位置指定パラメーターは、規則の *category* と *rule ID* です。 次のコード スニペットは、これらのパラメーターに `"Usage"` と `"CA2200:Rethrow to preserve stack details"` を渡します。

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

グローバル抑制ファイルに属性を追加する場合は、抑制の[スコープ](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope)を `"member"` などの目的のレベルに設定します。 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> プロパティを使用して、警告を抑制すべき API を指定します。

```csharp
[assembly: SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.", Scope = "member", Target = "~M:MyApp.Program.IngorableCharacters")]
```

明示的に指定されたユーザー ソースにマップされない、コンパイラによって生成されるコードの警告を抑制するには、抑制属性をグローバル抑制ファイル内に配置する必要があります。 たとえば、次のコードは、コンパイラによって出力されたコンストラクターに対する違反を抑制します。

```csharp
[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="MyTools.Type..ctor()")]
```

## <a name="see-also"></a>関連項目

- [違反を抑制する (Visual Studio)](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)
