---
title: 破壊的変更:NotifyIcon。テキストの最大文字数の増加
description: .NET 6 での破壊的変更について学習します。NotifyIcon.Text プロパティのテキストの最大長が増加しています。
ms.date: 01/19/2021
ms.openlocfilehash: f87b98dd852ce202689ae9360bee9b6cfbf01794
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255777"
---
# <a name="notifyicontext-maximum-text-length-increased"></a>NotifyIcon。テキストの最大文字数の増加

<xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> プロパティに許可されるテキストの最大長が、63 から 127 に増加しました。

## <a name="change-description"></a>変更の説明

以前のバージョンの .NET では、<xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> プロパティに許可されるテキストの最大長は 63 文字です。 .NET 6 以降では、許可されるテキストの最大長は 127 文字です。 いずれのバージョンでも、制限を超える値を設定しようとすると <xref:System.ArgumentException> がスローされます。

## <a name="reason-for-change"></a>変更理由

[基になる Windows API](/windows/win32/api/shellapi/ns-shellapi-notifyicondataw#nif_showtip-0x00000080) に従うように、許可されるテキストの最大長が増加しました。 Windows API は Windows 2000 で更新されましたが、互換性の理由から、このプロパティのサイズ制限は .NET Framework で更新されませんでした。

## <a name="version-introduced"></a>導入されたバージョン

.NET 6 Preview 1

## <a name="recommended-action"></a>推奨アクション

コードを確認し、必要に応じて任意の既存のガード条件を緩和します。

## <a name="affected-apis"></a>影響を受ける API

<xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.NotifyIcon.Text`

### Category

Windows Forms

-->
