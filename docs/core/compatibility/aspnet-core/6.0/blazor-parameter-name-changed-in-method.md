---
title: '破壊的変更:Blazor: RequestImageFileAsync メソッドで変更されたパラメーター名'
description: 'ASP.NET Core 6.0 での破壊的変更について学習します。タイトル: Blazor:RequestImageFileAsync メソッドで変更されたパラメーター名'
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: 61518ba246c1d390861261ecb5a9f18a5695c1fd
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106496983"
---
# <a name="blazor-parameter-name-changed-in-requestimagefileasync-method"></a>Blazor: RequestImageFileAsync メソッドで変更されたパラメーター名

`RequestImageFileAsync` メソッドの `maxWith` パラメーターの名前が `maxWith` から `maxWidth` に変更されました。

## <a name="version-introduced"></a>導入されたバージョン

6.0 Preview 1

## <a name="old-behavior"></a>以前の動作

パラメーター名のスペルは `maxWith` です。

## <a name="new-behavior"></a>新しい動作

パラメーター名のスペルは `maxWidth` です。

## <a name="reason-for-change"></a>変更理由

元のパラメーター名はタイプミスでした。

## <a name="recommended-action"></a>推奨される操作

`RequestImageFile` API で名前付きパラメーターを使用している場合は、`maxWith` パラメーター名を `maxWidth` に更新してください。 それ以外の場合、変更は必要ありません。

## <a name="affected-apis"></a>影響を受ける API

<xref:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`Overload:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync`

-->
