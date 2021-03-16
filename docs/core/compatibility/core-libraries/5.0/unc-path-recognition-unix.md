---
title: 破壊的変更:Unix での UNC パスの URI 認識
description: Core .NET ライブラリでの .NET 5 の破壊的変更について学習します。この変更後、URI クラスにより、2 つのスラッシュで始まる文字列が Unix 上の UNC パスとして認識されるようになりました。
ms.date: 11/01/2020
ms.openlocfilehash: 65baaad5e1be7a8f61e3e62c976fd7e28f48730f
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257025"
---
# <a name="uri-recognition-of-unc-paths-on-unix"></a>Unix での UNC パスの URI 認識

Unix オペレーティング システム上で、2 つのスラッシュ (`//`) で始まる文字列が <xref:System.Uri> クラスによって UNC (汎用名前付け規則) パスとして認識されるようになりました。 この変更により、すべてのプラットフォームでそのような文字列の動作の一貫性が確保されるようになります。

## <a name="change-description"></a>変更の説明

以前のバージョンの .NET では、Unix オペレーティング システム上で、2 つのスラッシュで始まる文字列 (`//contoso`など) が <xref:System.Uri> クラスによって絶対ファイル パスとして認識されます。 ただし、Windows では、そのような文字列は UNC パスとして認識されます。

.NET 5 以降、Unix を含むすべてのプラットフォーム上で、2 つのスラッシュで始まる文字列は <xref:System.Uri> クラスによって UNC パスとして認識されます。 さらに、プロパティは UNC セマンティクスに従って動作します。

- <xref:System.Uri.IsUnc?displayProperty=nameWithType> は、`true` を返します。
- パス内の円記号は、スラッシュに置き換えられます。 たとえば、`//first\second` を `//first/second` にします。
- <xref:System.Uri.LocalPath?displayProperty=nameWithType> によって文字のパーセントエンコードは行われません。 たとえば、`//first/\uFFF0` は `//first/%EF%BF%B0` に変換 "*されません*"。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

開発者側では、何も行う必要はありません。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->
