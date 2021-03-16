---
title: 破壊的変更:一部の API によって ArgumentNullException がスローされる
description: .NET 6 での破壊的変更について説明します。一部の API で引数が検証され、ArgumentNullException がスローされるようになりました。
ms.date: 01/29/2021
ms.openlocfilehash: ca7f32739237715657350f52d2523b0ce378364d
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255738"
---
# <a name="some-apis-throw-argumentnullexception"></a>一部の API によって ArgumentNullException がスローされる

一部の API で入力パラメーターが検証されるようになり、入力引数が `null` で呼び出された場合、以前は <xref:System.NullReferenceException> がスローされていたものが、<xref:System.ArgumentNullException> がスローされるようになりました。

## <a name="change-description"></a>変更内容

以前のバージョンの .NET では、影響を受ける API を呼び出すときに引数を `null` にすると、<xref:System.NullReferenceException> がスローされます。

.NET 6 以降では、影響を受ける API を呼び出すときに引数を `null` にすると、<xref:System.ArgumentNullException> がスローされます。

## <a name="reason-for-change"></a>変更理由

<xref:System.ArgumentNullException> のスローは、.NET ランタイムの動作に準拠しています。 例外の原因になった引数が明確に伝わることにより、デバッグのエクスペリエンスが向上します。

## <a name="version-introduced"></a>導入されたバージョン

.NET 6.0

## <a name="recommended-action"></a>推奨アクション

- コードをレビューし、必要に応じて、影響を受ける API に `null` 入力引数を渡さないように更新します。
- コードで <xref:System.NullReferenceException> を処理している場合は、置き換えるか、<xref:System.ArgumentNullException> 用のハンドラーを別に追加します。

## <a name="affected-apis"></a>影響を受ける API

次の表に、影響を受けるプロパティを一覧表示します。

| プロパティ | 変更されたバージョン |
|-|-|-|-|
| <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName> | Preview 1 |

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`

### Category

Windows Forms

-->
