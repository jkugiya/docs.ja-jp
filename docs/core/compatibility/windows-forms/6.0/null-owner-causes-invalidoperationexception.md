---
title: '.NET 6 の破壊的変更: DataGridView 関連の API が InvalidOperationException をスローする'
description: .NET 6 での破壊的変更について学習します。オブジェクトの DataGridViewCellAccessibleObject.Owner 値が null の場合に、DataGridView に関連する一部の API で例外がスローされます。
ms.date: 03/29/2021
ms.openlocfilehash: 3726296bb93c88d438e45ea832bf9070ace69dd0
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/31/2021
ms.locfileid: "106080664"
---
# <a name="datagridview-related-apis-now-throw-invalidoperationexception"></a>DataGridView 関連の API が InvalidOperationException をスローするようになった

<xref:System.Windows.Forms.DataGridView> に関連する API の一部で、オブジェクトの <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> 値が `null` の場合、<xref:System.InvalidOperationException> をスローするようになりました。

## <a name="change-description"></a>変更内容

以前のバージョンの .NET では、影響を受ける API からは、呼び出し時、<xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> プロパティ値が `null` であれば、<xref:System.NullReferenceException> がスローされます。 .NET 6 以降、これらの API では、呼び出し時、<xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> プロパティ値が `null` の場合、<xref:System.NullReferenceException> ではなく <xref:System.InvalidOperationException> がスローされます。

## <a name="reason-for-change"></a>変更理由

<xref:System.InvalidOperationException> をスローすることは、.NET ランタイムの動作に準拠しています。 また、無効なプロパティが明確に伝えられることでデバッグ作業が快適になります。

## <a name="version-introduced"></a>導入されたバージョン

.NET 6.0

## <a name="recommended-action"></a>推奨アクション

コードを見直し、必要であれば、影響を受ける型の <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> プロパティを `null` として構築しないよう、コードを変更します。

## <a name="affected-apis"></a>影響を受ける API

次の表に、影響を受けるプロパティとメソッドの一覧を示します。

> [!div class="mx-tdBreakAll"]
> | 影響を受けるメソッドまたはプロパティ | 追加されたバージョン |
> |-|-|
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Bounds?displayProperty=fullName> | Preview 4 |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.DefaultAction?displayProperty=fullName> | Preview 4 |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Name?displayProperty=fullName> | Preview 4 |
>| <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)?displayProperty=fullName> | Preview 4 |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.State?displayProperty=fullName> | Preview 4 |

## <a name="see-also"></a>関連項目

- [DataGridView 関連の API が InvalidOperationException をスローする (.NET 5)](../5.0/null-owner-causes-invalidoperationexception.md)

<!--

### Affected APIs

- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Bounds`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Name`
- `M:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.State`

### Category

Windows Forms

-->
