---
title: 破壊的変更:TextInfo.ListSeparator 値の変更
description: .NET 5 の破壊的変更について説明します。これにより、バージョン 5.0 と 5.0.1 間で TextInfo.ListSeparator の既定値が変更されました。
ms.date: 12/10/2020
ms.openlocfilehash: 9a319da8ea8e3cbf62cbf4730e553b03f5bfdc89
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256726"
---
# <a name="textinfolistseparator-values-changed"></a>TextInfo.ListSeparator 値の変更

すべてのオペレーティング システムで、さまざまなカルチャの既定の <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 値が変更されています。

## <a name="change-description"></a>変更の説明

.NET 5.0.0 では、[NLS から ICU ライブラリへの切り替え](icu-globalization-api.md)の一環として、Windows 上のさまざまなカルチャの既定の <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 値が変更されました。 International Components for Unicode (ICU) から取得された小数点区切りの値は、<xref:System.Globalization.TextInfo.ListSeparator> 値として使用されていました。 Linux と macOS 上では、<xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 値に変更はありませんでした。つまり、小数点区切りの値は引き続き使用されました。

.NET 5.0.1 以降のバージョンのすべてのオペレーティング システムでは、<xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> の値は NLS から取得される値と同じです。 Windows の場合、これは、値が .NET Framework および .NET Core 1.0 から 3.1 の値と同じであることを意味します。 Linux と macOS の場合、<xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 値は Windows の <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 値と一致するようになりました。

次の表は、<xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 値の変更をまとめたものです。

| | .NET Framework<br/>.NET Core 1.0 から 3.1 | .NET 5 | .NET 5.0.1 |
-|-|-|-
| **Windows** | NLS から取得されます | ICU の小数点区切り。<br/>NLS に戻すことができます。 | NLS と同じです |
| **Linux と macOS** | ICU の小数点区切り | ICU の小数点区切り | NLS と同じです |

## <a name="version-introduced"></a>導入されたバージョン

5.0.1

## <a name="reason-for-change"></a>変更理由

コンマ区切り値 (CSV) ファイルを解析するときに <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> プロパティを使用していて、新しい <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 値によってその解析が中断された、と開発者から報告されました。

## <a name="recommended-action"></a>推奨アクション

コードが以前の小数点区切り値に依存している場合は、目的の <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 値をハードコーディングすることができます。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=fullName>

<!--

#### Category

- Globalization

### Affected APIs

- `P:System.Globalization.TextInfo.ListSeparator`

-->
