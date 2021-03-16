---
title: 破壊的変更:Unix 上で ASCII 以外の文字を含む URI パスが正しく解析される
description: Core .NET ライブラリでの .NET 5 の破壊的変更について学習します。この変更後、Unix プラットフォームで非 ASCII 文字を含む絶対 URI パスによって正しく解析が行われるようになりました。
ms.date: 11/01/2020
ms.openlocfilehash: 50e9b4597a5ac0b73732a38ce662037292777a03
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257415"
---
# <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a>Unix 上で ASCII 以外の文字を含む URI パスが正しく解析される

<xref:System.Uri?displayProperty=fullName> クラス内のバグが修正され、Unix プラットフォーム上で ASCII 以外の文字を含む絶対 URI パスが正しく解析されるようになりました。

## <a name="change-description"></a>変更の説明

以前のバージョンの .NET では、Unix プラットフォーム上で ASCII 以外の文字を含む絶対 URI パスが正しく解析されず、パスのセグメントに重複が生じます。 (絶対パスとは、"/" で始まるものです)。 .NET 5.0 ではこの解析の問題が修正されました。 以前のバージョンの .NET から .NET 5 以降に移行すると、<xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>、<xref:System.Uri.ToString?displayProperty=nameWithType>、およびその他の <xref:System.Uri> メンバーによって生成され出力される値は異なるものとなります。

Unix 上で実行する場合は、次のコードの出力を検討してください。

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

以前のバージョンの .NET での出力:

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

.NET 5 以降のバージョンでの出力:

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

重複したパス セグメントの発生が予期される、および明らかであるコードがある場合は、そのコードを削除できます。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Uri?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->
