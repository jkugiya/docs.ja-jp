---
title: '破壊的変更:Blazor: Blazor アプリのルーティング ロジックの変更'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: Blazor:Blazor アプリのルーティング ロジックの変更'
ms.author: scaddie
ms.date: 12/14/2020
ms.openlocfilehash: cec05b26319fc8302261e41cc868dd73b46c8af0
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497828"
---
# <a name="blazor-route-precedence-logic-changed-in-blazor-apps"></a>Blazor: Blazor アプリにおけるルート優先順位のロジックの変更

Blazor のルーティング実装のバグによって、ルートの優先順位の決定方法が影響を受けました。 このバグは、キャッチオール ルート、または Blazor アプリ内の省略可能なパラメーターを使用するルートに影響します。

## <a name="version-introduced"></a>導入されたバージョン

5.0.1

## <a name="old-behavior"></a>以前の動作

誤った動作により、優先順位の高いルートよりも優先順位の低いルートの方が先に検討され、照合されます。 たとえば、`{*slug}` ルートが `/customer/{id}` よりも先に照合されます。

## <a name="new-behavior"></a>新しい動作

現在の動作は、ASP.NET Core アプリに定義されているルーティング動作により近くなりました。 このフレームワークにより、まず各セグメントのルートの優先順位が決まります。 ルートの長さは、優先順位が同じ場合の 2 番目の条件としてのみ使用されます。

## <a name="reason-for-change"></a>変更理由

元の動作は、実装のバグと考えられています。 目標として、Blazor アプリのルーティング システムは、ASP.NET Core の他の部分のルーティング システムと同じように動作する必要があります。

## <a name="recommended-action"></a>推奨アクション

以前のバージョンの Blazor から 5.x にアップグレードする場合は、`Router` コンポーネントの `PreferExactMatches` 属性を使用します。 この属性を使用して、正しい動作を選択できます。 次に例を示します。

```razor
<Router AppAssembly="@typeof(Program).Assembly" PreferExactMatches="true">
```

`PreferExactMatches` が `true` に設定されている場合、ルートの照合時にワイルドカードよりも完全一致が優先されます。

## <a name="affected-apis"></a>影響を受ける API

なし

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
