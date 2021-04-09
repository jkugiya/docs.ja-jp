---
title: '破壊的変更:Blazor: RenderTreeFrame の readonly のパブリック フィールドのプロパティ化'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: Blazor:RenderTreeFrame の readonly のパブリック フィールドのプロパティ化'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c4d70279b4280b079570099b82b056299405508b
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498166"
---
# <a name="blazor-rendertreeframe-readonly-public-fields-have-become-properties"></a>Blazor: RenderTreeFrame の readonly のパブリック フィールドのプロパティ化

ASP.NET Core 3.0 および 3.1 の <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> 構造体では、<xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType>、<xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence> などのさまざまな `readonly public` フィールドが公開されています。 このすべての `readonly public` フィールドが、ASP.NET Core 5.0 RC1 以降のバージョンで、`readonly public` プロパティに変更されています。

この変更は、次の理由により多くの開発者に影響しません。

* コンポーネントの定義に単純に `.razor` ファイルを使用する (または <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder> を手動で呼び出す) どのアプリまたはライブラリでも、この型は直接参照されません。
* `RenderTreeFrame` 型自体が実装の詳細と見なされ、フレームワーク外で使用するものとはみなされていません。 ASP.NET Core 3.0 以降には、型が直接使用される場合にコンパイラ警告が発行されるアナライザーが含まれています。
* `RenderTreeFrame` が直接参照される場合でも、この変更ではバイナリは中断させますが、ソースは中断させません。 つまり、既存のお使いのソース コードは正常にコンパイルされ、動作します。 .NET Core 3.x フレームワークに対してコンパイルされ、それらのバイナリが .NET 5.0 RC1 以降のフレームワークに対して実行される場合にのみ、問題が発生します。

ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#25727](https://github.com/dotnet/aspnetcore/issues/25727) を参照してください。

## <a name="version-introduced"></a>導入されたバージョン

5.0 RC1

## <a name="old-behavior"></a>以前の動作

`RenderTreeFrame` のパブリック メンバーはフィールドとして定義されていました。 たとえば、`renderTreeFrame.Sequence` や `renderTreeFrame.ElementName`す。

## <a name="new-behavior"></a>新しい動作

`RenderTreeFrame` のパブリック メンバーは、以前と同じ名前でプロパティとして定義されます。 たとえば、`renderTreeFrame.Sequence` や `renderTreeFrame.ElementName`す。

この変更以降、以前のプリコンパイル済みのコードが再コンパイルされていない場合、*MissingFieldException:フィールドが見つかりません:'Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType'* のような例外がスローされる場合があります。

## <a name="reason-for-change"></a>変更理由

この変更は、ASP.NET Core 5.0 でレンダリングされる Blazor コンポーネントに影響力の大きいパフォーマンス向上を実装するために必要でした。 安全性とカプセル化については、同じレベルが維持されています。

## <a name="recommended-action"></a>推奨アクション

多くの Blazor 開発者は、この変更の影響を受けません。 変更の影響は、ライブラリ作成者とパッケージ作成者の方が受ける可能性は高いですが、まれなケースにおいてです。 具体的には、次のように開発している場合です。

* アプリを開発していて、ASP.NET Core 3.x を使用するか、5.0 RC1 以降にアップグレードする場合は、自分自身のコードを変更する必要はありません。 ただし、依存しているライブラリをこの変更に対応するためにアップグレードした場合は、そのライブラリを新しいバージョンに更新する必要があります。
* ライブラリを開発していて、ASP.NET Core 5.0 RC1 以降のみをサポートするようにしたい場合は、何もする必要はありません。 お使いのプロジェクト ファイルで、`net5.0` 以降のバージョンの `<TargetFramework>` 値は宣言するようにします。
* ライブラリを開発していて、ASP.NET Core 3.x *と* 5.0 の両方をサポートする場合、自分のコードで `RenderTreeFrame` メンバーを読み取るか判断します。 たとえば、`someRenderTreeFrame.FrameType` を評価するかです。
  * 多くのライブラリでは、`.razor` コンポーネントを含むライブラリを含む `RenderTreeFrame` メンバーは読み取りません。 この場合、何もする必要はありません。
  * ただし、自分のライブラリでそれが行われる場合は、`netstandard2.1` と `net5.0` の両方をターゲットにしてサポートされるようにする必要があります。 お使いのプロジェクト ファイルを次のように変更します。
    * 既存の `<TargetFramework>` 要素を `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>` に置き換えます。
    * サポートする両バージョンに対応できるよう、条件付き `Microsoft.AspNetCore.Components` パッケージ参照を使用します。 次に例を示します。

        ```xml
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="3.0.0" Condition="'$(TargetFramework)' == 'netstandard2.0'" />
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="5.0.0-rc.1.*" Condition="'$(TargetFramework)' != 'netstandard2.0'" />
        ```

詳細については、[@jsakamoto が `Toolbelt.Blazor.HeadElement` ライブラリをどのようにアップグレードしたかの違いを示した](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51)ページを参照してください。

## <a name="affected-apis"></a>影響を受ける API

<xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame`

-->
