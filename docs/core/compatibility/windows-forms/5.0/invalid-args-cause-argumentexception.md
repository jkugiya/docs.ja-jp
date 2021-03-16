---
title: '破壊的変更: WinForms メソッドで ArgumentException がスローされるようになった'
description: .NET 5 での破壊的変更について学習します。一部の Windows フォーム メソッドで、無効な引数に対する ArgumentException がスローされるようになりました。
ms.date: 07/18/2020
ms.openlocfilehash: 9823e9162a562081cdd64346a502ca136b51fa75
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256140"
---
# <a name="winforms-methods-now-throw-argumentexception"></a>WinForms メソッドで ArgumentException がスローされるようになった

一部の Windows フォーム メソッドで、無効な引数に対して <xref:System.ArgumentException> がスローされるようになりました。以前はスローされませんでした。

## <a name="change-description"></a>変更の説明

以前は、予期しない型または不適切な型の引数を特定の Windows フォーム メソッドに渡すと、不確定な状態になりました。 .NET 5 以降では、そのようなメソッドに無効な引数を渡すと、<xref:System.ArgumentException> がスローされるようになりました。

<xref:System.ArgumentException> をスローすることは、.NET ランタイムの動作に準拠しています。 また、どの引数が無効であるのかが明確に伝えられることで、デバッグ エクスペリエンスも向上します。

## <a name="version-introduced"></a>導入されたバージョン

.NET 5.0

## <a name="recommended-action"></a>推奨アクション

- 無効な引数を渡さないようにコードを更新します。
- 必要に応じて、メソッドを呼び出したときの <xref:System.ArgumentException> を処理します。

## <a name="affected-apis"></a>影響を受ける API

次の表では、影響を受けるメソッドとパラメーターを示します。

| メソッド | パラメーター名 | 条件 | 追加されたバージョン |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | 引数が <xref:System.Windows.Forms.TabPage> 型ではありません。 | Preview 1 |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | 引数が `null`、<xref:System.String.Empty?displayProperty=nameWithType>、または空白です。 | Preview 5 |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | 指定のカルチャに `InputLanguage` を取得できません。 | Preview 7 |

<!--

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

### Category

Windows Forms

-->
