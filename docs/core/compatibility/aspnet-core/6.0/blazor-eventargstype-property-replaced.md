---
title: '破壊的変更: Blazor: WebEventDescriptor.EventArgsType プロパティが置き換えられました'
description: WebEventDescriptor.EventArgsType プロパティが EventName プロパティに置き換えられた ASP.NET Core 6.0 の破壊的変更について説明します。
ms.author: scaddie
ms.date: 02/24/2021
no-loc:
- Blazor
ms.openlocfilehash: c9e866813707114f912ffe83309b0f95c2c9a0f2
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497009"
---
# <a name="blazor-no-loc-textwebeventdescriptoreventargstype-property-replaced"></a>Blazor: :::no-loc text="WebEventDescriptor.EventArgsType"::: プロパティが置き換えられました

<xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor> クラスは、JavaScript から .NET にイベントをやり取りするための Blazor の内部プロトコルの一部です。 通常、このクラスは、アプリ コードではなく、プラットフォームの作成者によって使用されます。

ASP.NET Core 6.0 以降、`WebEventDescriptor` の <xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType%2A> プロパティは新しい `EventName` プロパティに置き換えられています。 この変更は低レベルのプラットフォーム実装の詳細であるため、アプリ コードに影響する可能性はほとんどありません。

## <a name="version-introduced"></a>導入されたバージョン

6.0

## <a name="old-behavior"></a>以前の動作

ASP.NET Core 5.0 以前の場合、プロパティ `EventArgsType` には、DOM イベントの種類のグループに対して非標準の Blazor 固有のカテゴリ名を記述します。 たとえば、`click` と `mousedown` のイベントはいずれも `mouse` の `EventArgsType` 値 にマップされていました。 同様に、`cut`、`copy`、および `paste` のイベントは、`clipboard` の `EventArgsType` 値にマップされます。 これらのカテゴリ名は、受信イベントの引数データを逆シリアル化する際に使用される .NET 型を決定するために使用されます。

## <a name="new-behavior"></a>新しい動作

ASP.NET Core 6.0 以降、新しいプロパティ `EventName` には元のイベントの名前のみを指定します。 たとえば、`click`、`mousedown`、`cut`、`copy`、`paste` などです。 Blazor 固有のカテゴリ名を指定する必要はなくなりました。 そのため、以前のプロパティ `EventArgsType` は削除されました。

## <a name="reason-for-change"></a>変更理由

プル要求 [dotnet/aspnetcore#29993](https://github.com/dotnet/aspnetcore/pull/29993) で、カスタムのイベント引数クラスのサポートが導入されました。 このサポートの一部として、フレームワークは、事前に定義されたカテゴリのセットに適合するすべてのイベントに依存しなくなりました。 フレームワークに必要な情報は元のイベント名のみになりました。

## <a name="recommended-action"></a>推奨アクション

アプリ コードは影響を受けないため、変更する必要はありません。

カスタムの Blazor レンダリング プラットフォームを構築する場合は、必要に応じてイベントを `Renderer` にディスパッチするためのメカニズムを更新します。 イベント カテゴリに関するハードコーディングされたルールを、元の生のイベント名を指定する場合よりも簡単なロジックに置き換えます。

## <a name="affected-apis"></a>影響を受ける API

<xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`P:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType`

-->
