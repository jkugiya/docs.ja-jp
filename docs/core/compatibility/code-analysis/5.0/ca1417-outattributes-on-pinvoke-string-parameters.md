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
# <a name="warning-ca1417-outattribute-on-string-parameter-for-pinvoke"></a>警告 CA1417:P/Invoke 用の文字列パラメーターの OutAttribute

.NET コード アナライザー ルール [CA1417](/visualstudio/code-quality/ca1417) は、.NET 5.0 以降では既定で有効になっています。 <xref:System.String> パラメーターが値渡しされ、<xref:System.Runtime.InteropServices.OutAttribute> でマークされる[プラットフォーム呼び出し (P/Invoke)](../../../../standard/native-interop/pinvoke.md) メソッド定義に対して、ビルド警告が生成されます。

## <a name="change-description"></a>変更内容

.NET 5 以降、.NET SDK には [.NET ソース コード アナライザー](../../../../fundamentals/code-analysis/overview.md)が含まれています。 これらのルールのいくつかは、[CA1417](/visualstudio/code-quality/ca1417) を含め、既定で有効になっています。 このルールに違反し、警告をエラーとして扱うように構成されているコードがプロジェクトに含まれている場合、この変更によってビルドが破損する可能性があります。

<xref:System.String> パラメーターが <xref:System.Runtime.InteropServices.OutAttribute> 属性でマークされ、値渡しされる [P/Invoke](../../../../standard/native-interop/pinvoke.md) メソッド定義には、ルール CA1417 によってフラグが立てられます。 次に例を示します。

```csharp
[DllImport("MyLibrary")]
private static extern void PIMethod([Out] string s);
```

.NET ランタイムでは、インターン プールと呼ばれるテーブルが保持されます。これには、プログラム内の各一意のリテラル文字列への単一の参照が含まれています。 <xref:System.Runtime.InteropServices.OutAttribute> でマークされたインターン文字列が P/Invoke メソッドに値渡しされる場合、ランタイムが不安定になる可能性があります。 文字列インターンの詳細については、<xref:System.String.Intern(System.String)?displayProperty=nameWithType> に関する注釈を参照してください。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

- 変更された文字列データを呼び出し元にマーシャリングする必要がある場合は、代わりに文字列を参照渡しにします。

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(out string s);
  ```

- 変更した文字列データを呼び出し元にマーシャリングする必要がない場合は、<xref:System.Runtime.InteropServices.OutAttribute> を削除するだけです。

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(string s);
  ```

  詳細については、[CA1417](/visualstudio/code-quality/ca1417) を参照してください。

- コード分析を完全に無効にするには、プロジェクト ファイルで `EnableNETAnalyzers` を `false` に設定します。 詳細については、「[EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)」を参照してください。

## <a name="affected-apis"></a>影響を受ける API

API 分析では検出できません。

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
