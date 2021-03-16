---
title: 破壊的変更:カスタマイズされたセル スタイルのフォントが DataGridView によってリセットされなくなった
description: セル スタイル フォントがカスタマイズされている場合、アンビエント フォントと一致させるために既定のセルスタイル フォントが DataGridView によってリセットされなくなったという、.NET 5 の破壊的変更について学習します。
ms.date: 10/18/2020
ms.openlocfilehash: fd28fb5a0b508157289dde1b720522ed49163e31
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256129"
---
# <a name="datagridview-no-longer-resets-fonts-for-customized-cell-styles"></a>カスタマイズされたセル スタイルのフォントが DataGridView によってリセットされなくなった

アンビエント フォントが変更されても、セル スタイル フォントがカスタマイズされている場合、アンビエント フォントと一致させるために既定のセルスタイル フォントが <xref:System.Windows.Forms.DataGridViewElement.DataGridView> によってリセットされなくなりました。

## <a name="change-description"></a>変更内容

以前のバージョンの .NET では、アンビエント フォントが変更されると、<xref:System.Windows.Forms.DataGridView.DefaultCellStyle>、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>、および <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> の各プロパティのユーザー定義フォントが <xref:System.Windows.Forms.DataGridViewElement.DataGridView> によってリセットされ、オーバーライドされます。

.NET 5 以降では、<xref:System.Windows.Forms.DataGridView.DefaultCellStyle>、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>、<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> のいずれかのプロパティでフォント設定を構成すると、アンビエント フォントが変更された場合でも、これらの設定が保持されます。 フォントをカスタマイズしないこれらのプロパティのフォントは、いずれもアンビエント フォントの設定に合わせて変更されます。

## <a name="reason-for-change"></a>変更理由

[.NET Core 3.0 の既定のフォントの変更](../../winforms.md#default-control-font-changed-to-segoe-ui-9-pt)により、さまざまなセル スタイルの既定のフォント設定も変更されました。 この動作は、<xref:System.Windows.Forms.DataGridViewElement.DataGridView> コントロールのカスタム スタイルに依存するアプリには望ましくなく、これらのアプリの .NET Framework から .NET 5.0 への移行を妨げます。

## <a name="version-introduced"></a>導入されたバージョン

.NET 5.0

## <a name="recommended-action"></a>推奨される操作

お客様側では何もする必要はありません。 ただし、<xref:System.Windows.Forms.DataGridView.DefaultCellStyle>、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>、<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> のいずれかのプロパティでフォントをカスタマイズし、そのフォントをアンビエント フォントと一致させるには、各プロパティの <xref:System.Windows.Forms.DataGridViewCellStyle.Font?displayProperty=nameWithType> を `null` に設定します。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.DataGridView.DefaultCellStyle`
- `P:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle`
- `P:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle`

### Category

- Windows Forms

-->
