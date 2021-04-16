---
title: ページ、ルーティング、レイアウト
description: Blazor でページを作成する方法、クライアント側のルーティングを使用する方法、およびページ レイアウトを管理する方法について説明します。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/19/2019
ms.openlocfilehash: 714ba0be7c2014895a75250a47e6ce448863eb6c
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "88267790"
---
# <a name="pages-routing-and-layouts"></a>ページ、ルーティング、レイアウト

ASP.NET Web Forms アプリは、 *.aspx* ファイルで定義された複数のページで構成されます。 各ページのアドレスは、プロジェクト内の物理ファイル パスに基づいています。 ブラウザーがページに要求を行うと、ページの内容がサーバーに動的にレンダリングされます。 このレンダリングは、ページの HTML マークアップとそのサーバー コントロールの両方に相当します。

Blazor では、アプリの各ページは、1 つまたは複数のルートを指定する *.razor* ファイルで通常定義されているコンポーネントです。 ルーティングはほとんどの場合、特定のサーバー要求を介さずにクライアント側で行われます。 ブラウザーはまず、アプリのルート アドレスに要求を行います。 その後、Blazor アプリ内のルート `Router` コンポーネントが、受信ナビゲーション要求を処理し、正しいコンポーネントに要求を行います。

Blazor では "*ディープ リンクの設定*" もサポートされます。 ディープ リンクの設定は、ブラウザーがアプリのルート以外の特定のルートに対して要求を行うときに発生します。 サーバーに送信されるディープ リンクの要求は Blazor アプリにルーティングされ、その後、クライアント側への要求が正しいコンポーネントにルーティングされます。

ASP.NET Web Forms の単純なページには、次のマークアップが含まれる場合があります。

*Name.aspx*

```aspx-csharp
<%@ Page Title="Name" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Name.aspx.cs" Inherits="WebApplication1.Name" %>

<asp:Content ID="BodyContent" ContentPlaceHolderID="MainContent" runat="server">
    <div>
        What is your name?<br />
        <asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
        <asp:Button ID="Button1" runat="server" Text="Submit" OnClick="Button1_Click" />
    </div>
    <div>
        <asp:Literal ID="Literal1" runat="server" />
    </div>
</asp:Content>
```

*Name.aspx.cs*

```csharp
public partial class Name : System.Web.UI.Page
{
    protected void Button1_Click1(object sender, EventArgs e)
    {
        Literal1.Text = "Hello " + TextBox1.Text;
    }
}
```

Blazor アプリの同等のページは、次のようになります。

*Name.razor*

```razor
@page "/Name"
@layout MainLayout

<div>
    What is your name?<br />
    <input @bind="text" />
    <button @onclick="OnClick">Submit</button>
</div>
<div>
    @if (name != null)
    {
        @:Hello @name
    }
</div>

@code {
    string text;
    string name;

    void OnClick() {
        name = text;
    }
}
```

## <a name="create-pages"></a>ページを作成する

Blazor でページを作成するには、コンポーネントを作成し、`@page` Razor ディレクティブを追加して、コンポーネントのルートを指定します。 `@page` ディレクティブは、そのコンポーネントに追加するルート テンプレートである 1 つのパラメーターを受け取ります。

```razor
@page "/counter"
```

ルート テンプレート パラメーターは必須です。 ASP.NET Web Forms とは異なり、Blazor コンポーネントへのルートがそのファイルの場所から推論されることは "*ありません*" (ただし、その機能が将来追加される可能性があります)。

ルート テンプレートの構文は、ASP.NET Web Forms でのルーティングに使用される基本構文と同じです。 ルート パラメーターは、テンプレート内で中かっこを使用して指定されます。 Blazor では、ルート値を同じ名前のコンポーネント パラメーターにバインドします (大文字と小文字は区別されません)。

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

ルート パラメーターの値に制約を指定することもできます。 たとえば、製品 ID を `int` に制約するには次のようにします。

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

Blazor でサポートされているルート制約の完全な一覧については、「[ルート制約](/aspnet/core/blazor/routing#route-constraints)」を参照してください。

## <a name="router-component"></a>ルーター コンポーネント

Blazor でのルーティングは、`Router` コンポーネントによって処理されます。 `Router` コンポーネントは通常、アプリのルート コンポーネント (*App.razor*) で使用されます。

```razor
<Router AppAssembly="@typeof(Program).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
    </Found>
    <NotFound>
        <LayoutView Layout="@typeof(MainLayout)">
            <p>Sorry, there's nothing at this address.</p>
        </LayoutView>
    </NotFound>
</Router>
```

`Router` コンポーネントは、指定された `AppAssembly` 内で、および必要に応じて指定された `AdditionalAssemblies` 内で、ルーティング可能なコンポーネントを検出します。 ブラウザーが移動するとき、`Router` はナビゲーションをインターセプトし、ルートがアドレスと一致する場合は抽出された `RouteData` を使用して `Found` パラメーターの内容をレンダリングし、それ以外の場合、`Router` はその `NotFound` パラメーターを表示します。

`RouteView` コンポーネントは、`RouteData` によって指定された一致するコンポーネントをそのレイアウトを使用してレンダリングします (レイアウトがある場合)。 一致するコンポーネントにレイアウトがない場合は、必要に応じて指定された `DefaultLayout` が使用されます。

`LayoutView` コンポーネントは、指定されたレイアウト内で子コンテンツをレンダリングします。 レイアウトについては、この章で後ほど詳しく説明します。

## <a name="navigation"></a>［ナビゲーション］

ASP.NET Web Forms では、ブラウザーにリダイレクト応答を返すことによって、別のページへのナビゲーションをトリガーします。 次に例を示します。

```csharp
protected void NavigateButton_Click(object sender, EventArgs e)
{
    Response.Redirect("Counter");
}
```

Blazor では通常、リダイレクト応答を返すことはできません。 Blazor では、要求/応答モデルは使用されません。 ただし、JavaScript の場合と同様に、ブラウザーのナビゲーションを直接トリガーできます。

Blazor には、次のために使用できる `NavigationManager` サービスが用意されています。

- 現在のブラウザー アドレスを取得する
- ベース アドレスを取得する
- ナビゲーションをトリガーする
- アドレスが変更されたときに通知を受け取る

別のアドレスに移動するには、`NavigateTo` メソッドを使用します。

```razor
@page "/"
@inject NavigationManager NavigationManager

<button @onclick="Navigate">Navigate</button>

@code {
    void Navigate() {
        NavigationManager.NavigateTo("counter");
    }
}
```

すべての `NavigationManager` メンバーの説明については、「[URI およびナビゲーション状態ヘルパー](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers)」を参照してください。

## <a name="base-urls"></a>ベース URL

Blazor アプリがベース パスの下にデプロイされている場合は、ルーティングが正しく動作するために、`<base>` タグを使用して、ページ メタデータにベース URL を指定する必要があります。 アプリのホスト ページが Razor を使用してサーバーでレンダリングされる場合は、`~/` 構文を使用してアプリのベース アドレスを指定できます。 ホスト ページが静的な HTML の場合は、ベース URL を明示的に指定する必要があります。

```html
<base href="~/" />
```

## <a name="page-layout"></a>ページのレイアウト

ASP.NET Web Forms のページ レイアウトは、マスター ページによって処理されます。 マスター ページは、1 つまたは複数のコンテンツ プレースホルダーを持つテンプレートを定義します。このプレースホルダーは、後で個々のページで提供できます。 マスター ページは *.master* ファイルで定義され、`<%@ Master %>` ディレクティブで始まります。 *.master* ファイルの内容は *.aspx* ページと同じようにコード化されますが、ページがコンテンツを提供できる場所をマークするための `<asp:ContentPlaceHolder>` コントロールが追加されています。

*Site.master*

```aspx-csharp
<%@ Master Language="C#" AutoEventWireup="true" CodeBehind="Site.master.cs" Inherits="WebApplication1.SiteMaster" %>

<!DOCTYPE html>
<html lang="en">
<head runat="server">
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title><%: Page.Title %> - My ASP.NET Application</title>
    <link href="~/favicon.ico" rel="shortcut icon" type="image/x-icon" />
</head>
<body>
    <form runat="server">
        <div class="container body-content">
            <asp:ContentPlaceHolder ID="MainContent" runat="server">
            </asp:ContentPlaceHolder>
            <hr />
            <footer>
                <p>&copy; <%: DateTime.Now.Year %> - My ASP.NET Application</p>
            </footer>
        </div>
    </form>
</body>
</html>
```

Blazor では、レイアウト コンポーネントを使用してページ レイアウトを処理します。 レイアウト コンポーネントは `LayoutComponentBase` を継承します。これは、ページの内容をレンダリングするために使用できる `RenderFragment` 型の単一の `Body` プロパティを定義します。

*MainLayout.razor*

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

レイアウトが指定されたページがレンダリングされるとき、レイアウトが `Body` プロパティをレンダリングする場所で指定されたレイアウトのコンテンツの内部にページがレンダリングされます。

ページにレイアウトを適用するには、`@layout` ディレクティブを使用します。

```razor
@layout MainLayout
```

*_Imports.razor* ファイルを使用して、フォルダーおよびサブフォルダー内のすべてのコンポーネントのレイアウトを指定できます。 [ルーター コンポーネント](#router-component)を使用して、すべてのページの既定のレイアウトを指定することもできます。

マスター ページでは複数のコンテンツ プレースホルダーを定義できますが、Blazor のレイアウトには 1 つの `Body` プロパティしかありません。 Blazor レイアウト コンポーネントのこの制限は、今後のリリースで対処される予定です。

ASP.NET Web Forms のマスター ページは入れ子にすることができます。 つまり、マスター ページでマスター ページを使用することもできます。 Blazor のレイアウト コンポーネントも入れ子にすることができます。 レイアウト コンポーネントをレイアウト コンポーネントに適用できます。 内側のレイアウトのコンテンツは外側のレイアウト内にレンダリングされます。

*ChildLayout.razor*

```razor
@layout MainLayout
<h2>Child layout</h2>
<div>
    @Body
</div>
```

*Index.razor*

```razor
@page "/"
@layout ChildLayout
<p>I'm in a nested layout!</p>
```

ページのレンダリングされた出力は次のようになります。

```html
<h1>Main layout</h1>
<div>
    <h2>Child layout</h2>
    <div>
        <p>I'm in a nested layout!</p>
    </div>
</div>
```

Blazor のレイアウトでは、ページのルート HTML 要素 (`<html>`、 `<body>`、`<head>` など) は通常は定義されません。 ルート HTML 要素は代わりに Blazor アプリのホスト ページで定義され、このページはアプリの初期 HTML コンテンツをレンダリングするために使用されます (「[Blazor をブートストラップする](project-structure.md#bootstrap-blazor)」を参照してください)。 ホスト ページでは、前後のマークアップを使用して、アプリの複数のルート コンポーネントをレンダリングできます。

ページなどの Blazor のコンポーネントは `<script>` タグをレンダリングできません。 このレンダリング制限が存在するのは、`<script>` タグは一度読み込まれると変更できないためです。 Razor 構文を使用してタグを動的にレンダリングしようとすると、予期しない動作が発生することがあります。 代わりに、すべての `<script>` タグをアプリのホスト ページに追加する必要があります。

>[!div class="step-by-step"]
>[前へ](components.md)
>[次へ](state-management.md)
