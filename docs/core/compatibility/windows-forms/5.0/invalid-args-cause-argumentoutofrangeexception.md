---
title: '破壊的変更: WinForms プロパティによる ArgumentOutOfRangeException のスロー'
description: .NET 5 での破壊的変更について学習します。この変更により、一部の Windows フォームのプロパティは、無効な引数の ArgumentOutOfRangeException をスローするようになりました。
ms.date: 06/18/2020
ms.openlocfilehash: 493669af1ed5646d93e7c7d2688afd40f3fa731c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256154"
---
# <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a>WinForms プロパティによる ArgumentOutOfRangeException のスロー

一部の Windows フォーム プロパティで、無効な引数に対して <xref:System.ArgumentOutOfRangeException> がスローされるようになりました。以前はスローされませんでした。

## <a name="change-description"></a>変更の説明

以前は、これらのプロパティでは、範囲外の引数が渡されたときに <xref:System.NullReferenceException>、<xref:System.IndexOutOfRangeException>、<xref:System.ArgumentException> などのさまざまな例外がスローされていました。 .NET 5 以降、これらのプロパティでは、範囲外の引数が渡されたときに <xref:System.ArgumentOutOfRangeException> がスローされるようになりました。

<xref:System.ArgumentOutOfRangeException> をスローすることは、.NET ランタイムの動作に準拠しています。 また、どの引数が無効であるのかが明確に伝えられることで、デバッグ エクスペリエンスも向上します。

## <a name="version-introduced"></a>導入されたバージョン

.NET 5.0

## <a name="recommended-action"></a>推奨アクション

- 無効な引数を渡さないようにコードを更新します。
- 必要に応じて、プロパティを設定するときに <xref:System.ArgumentOutOfRangeException> を処理します。

## <a name="affected-apis"></a>影響を受ける API

次の表に、影響を受けるプロパティとパラメーターの一覧を示します。

> [!div class="mx-tdBreakAll"]
> | プロパティ | パラメーター名 | 追加されたバージョン |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | 5.0 Preview 5 |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | 5.0 Preview 6 |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | 5.0 Preview 6 |

<!--

### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

### Category

Windows Forms

-->
