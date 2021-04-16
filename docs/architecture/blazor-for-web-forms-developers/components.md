---
title: Blazor を使用して再利用可能な UI コンポーネントを構築する
description: Blazor を使用して再利用可能な UI コンポーネントを構築する方法と、それらが ASP.NET Web Forms コントロールとどのように比較されるかについて説明します。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/18/2019
ms.openlocfilehash: fd560c84c095dffc3718a7709af904d9ba722a18
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "97512770"
---
# <a name="build-reusable-ui-components-with-blazor"></a>Blazor を使用して再利用可能な UI コンポーネントを構築する

ASP.NET Web Forms の優れた点の 1 つは、再利用可能なユーザー インターフェイス (UI) コードを再利用可能な UI コントロールにカプセル化できることです。 *.ascx* ファイルを使用してマークアップでカスタム ユーザー コントロールを定義できます。 デザイナーの完全なサポートを備えたコードで、複雑なサーバー コントロールを作成することもできます。

Blazor では、"*コンポーネント*" による UI カプセル化もサポートされています。 コンポーネントとは:

- 自己完結型のひとまとまりの UI です。
- 自身の状態およびレンダリング ロジックを保持します。
- UI イベント ハンドラーを定義し、入力データにバインドし、自身のライフサイクルを管理できます。
- 通常、Razor 構文を使用して *.razor* ファイルで定義されます。

## <a name="an-introduction-to-razor"></a>Razor の概要

Razor は、HTML および C# に基づく軽量のマークアップ テンプレート言語です。 Razor を使用すると、マークアップと C# のコードをシームレスに切り替えて、コンポーネントのレンダリング ロジックを定義できます。 *.razor* ファイルがコンパイルされると、レンダリング ロジックは構造化された方法で .NET クラスに取り込まれます。 コンパイル済みクラスの名前は、 *.razor* ファイルの名前から取得されます。 名前空間は、プロジェクトの既定の名前空間とフォルダー パスから取得されます。また、`@namespace` ディレクティブを使用して名前空間を明示的に指定することもできます (Razor ディレクティブの詳細については後述します)。

コンポーネントのレンダリング ロジックは、通常の HTML マークアップと、C# によって追加される動的ロジックを使用して作成されます。 `@` 文字は、C# に切り替えるために使用されます。 HTML に戻すと、通常は Razor で適切に把握されます。 たとえば、次のコンポーネントでは、`<p>` タグが現在の時刻でレンダリングされます。

```razor
<p>@DateTime.Now</p>
```

C# の式の開始と終了を明示的に指定するには、かっこを使用します。

```razor
<p>@(DateTime.Now)</p>
```

Razor では、レンダリング ロジックで C# の制御フローを使用することも簡単になります。 たとえば、次のような HTML を条件付きでレンダリングできます。

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

または、次のような通常の C# `foreach` ループを使用して項目の一覧を生成することもできます。

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

ASP.NET Web Forms のディレクティブと同様に、Razor のディレクティブでは Razor コンポーネントのコンパイル方法の多くの側面を制御します。 たとえば、コンポーネントの次のような点です。

- 名前空間
- 基本クラス
- 実装されるインターフェイス
- ジェネリック パラメーター
- [インポートされた名前空間]
- ルート

Razor ディレクティブは、`@` 文字で始まり、通常はファイルの先頭にある新しい行の先頭で使用されます。 たとえば、`@namespace` ディレクティブでは、コンポーネントの名前空間が定義されます。

```razor
@namespace MyComponentNamespace
```

次の表は、Blazor で使用されるさまざまな Razor ディレクティブと、ASP.NET Web Forms でそれに相当するもの (存在する場合) をまとめたものです。

|ディレクティブ    |説明|例|Web Forms で相当するもの|
|-------------|-----------|-------|--------------------|
|`@attribute` |コンポーネントにクラス レベルの属性を追加します|`@attribute [Authorize]`|なし|
|`@code`      |コンポーネントにクラス メンバーを追加します|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|指定されたインターフェイスを実装します|`@implements IDisposable`|コードビハインドを使用する|
|`@inherits`  |指定された基本クラスを継承します|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |コンポーネントにサービスを挿入します|`@inject IJSRuntime JS`|なし|
|`@layout`    |コンポーネントのレイアウト コンポーネントを指定します|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |コンポーネントの名前空間を設定します|`@namespace MyNamespace`|なし|
|`@page`      |コンポーネントのルートを指定します|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |コンポーネントのジェネリック型パラメーターを指定します|`@typeparam TItem`|コードビハインドを使用する|
|`@using`     |スコープに取り込む名前空間を指定します|`@using MyComponentNamespace`|*web.config* に名前空間を追加する|

また、Razor コンポーネントでは、要素に対して "*ディレクティブ属性*" を広範に使用して、コンポーネントのコンパイル方法のさまざまな側面 (イベント処理、データ バインディング、コンポーネントと要素の参照など)を制御します。 ディレクティブ属性はすべて、共通の汎用構文に従います。かっこ内の値は省略可能です。

```razor
@directive(-suffix(:name))(="value")
```

次の表は、Blazor で使用される Razor ディレクティブのさまざまな属性をまとめたものです。

|属性    |説明|例|
|-------------|-----------|-------|
|`@attributes`|属性のディクショナリをレンダリングします|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |双方向のデータ バインディングを作成します    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |指定されたイベントのイベント ハンドラーを追加します|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |コレクション内の要素を保持するために比較アルゴリズムで使用するキーを指定します|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |コンポーネントまたは HTML 要素への参照をキャプチャします|`<MyDialog @ref="myDialog" />`|

Blazor で使用されるさまざまなディレクティブ (`@onclick`、`@bind`、`@ref` など) については、以下の各セクションと以降の章で説明します。

*.aspx* および *.ascx* ファイルで使用される構文の多くに、類似の Razor 構文があります。 次に、ASP.NET Web Forms と Razor の構文を簡単に比較します。

|機能                      |Web フォーム           |構文               |Razor         |構文 |
|-----------------------------|--------------------|---------------------|--------------|-------|
|ディレクティブ                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|コード ブロック                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|式<br>(HTML エンコード)|`<%: %>`            |`<%:DateTime.Now %>` |暗黙的: `@`<br>明示的: `@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|コメント                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|データ バインディング                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

Razor コンポーネント クラスにメンバーを追加するには、`@code` ディレクティブを使用します。 この手法は、ASP.NET Web Forms のユーザー コントロールまたはページで `<script runat="server">...</script>` ブロックを使用するのと似ています。

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

Razor は C# に基づいているため、C# プロジェクト ( *.csproj*) 内からコンパイルする必要があります。 Visual Basic プロジェクト ( *.vbproj*) から *.razor* ファイルをコンパイルすることはできません。 ただし、Blazor プロジェクトから Visual Basic プロジェクトを参照することはできます。 逆も同様です。

Razor 構文の完全なリファレンスについては、「[ASP.NET Core の Razor 構文リファレンス](/aspnet/core/mvc/views/razor)」を参照してください。

## <a name="use-components"></a>コンポーネントを使う

コンポーネントでは、通常の HTML の他に、他のコンポーネントをレンダリング ロジックの一部として使用することもできます。 Razor でコンポーネントを使用するための構文は、ASP.NET Web Forms アプリでユーザー コントロールを使用する場合と似ています。 コンポーネントは、コンポーネントの型名と一致する要素タグを使用して指定されます。 たとえば、次のように `Counter` コンポーネントを追加できます。

```razor
<Counter />
```

ASP.NET Web Forms とは異なり、Blazor のコンポーネントでは次のようになります。

- 要素のプレフィックスは使用しません (例: `asp:`)。
- ページまたは *web.config* での登録は必要ありません。

Razor コンポーネントについては .NET 型と同様に考えてください。なぜなら、まさにそのようなものだからです。 コンポーネントを含むアセンブリが参照されると、コンポーネントが使用可能になります。 コンポーネントの名前空間をスコープに取り込むには、`@using` ディレクティブを適用します。

```razor
@using MyComponentLib

<Counter />
```

既定の Blazor プロジェクトに見られるように、`@using` ディレクティブを *_Imports.razor* ファイルに配置して、同じディレクトリおよび子ディレクトリ内のすべての *.razor* ファイルにインポートされるようにするのが一般的です。

コンポーネントの名前空間がスコープ内にない場合は、C# の場合と同様に、完全な型名を使用してコンポーネントを指定できます。

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>コンポーネントのパラメーター

ASP.NET Web Forms では、パブリック プロパティを使用して、パラメーターとデータをコントロールにフローできます。 これらのプロパティは、属性を使用してマークアップで設定することも、コードで直接設定することもできます。 Blazor のコンポーネントも同様の方法で動作しますが、コンポーネントのプロパティがコンポーネントのパラメーターと見なされるようにするために `[Parameter]` 属性でマークする必要もあります。

次の `Counter` コンポーネントでは、`IncrementAmount` というコンポーネント パラメーターを定義しています。これを使用して、ボタンがクリックされるたびに `Counter` をインクリメントする量を指定できます。

```razor
<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    int currentCount = 0;

    [Parameter]
    public int IncrementAmount { get; set; } = 1;

    void IncrementCount()
    {
        currentCount+=IncrementAmount;
    }
}
```

Blazor でコンポーネント パラメーターを指定するには、ASP.NET Web Forms の場合と同様に属性を使用します。

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>イベント ハンドラー

ASP.NET Web Forms と Blazor のどちらにも、UI イベントを処理するためのイベント ベースのプログラミング モデルが用意されています。 このようなイベントの例としては、ボタンのクリックやテキスト入力などがあります。 ASP.NET Web Forms では、HTML サーバー コントロールを使用して、DOM によって公開される UI イベントを処理したり、Web サーバー コントロールによって公開されるイベントを処理したりすることができます。 イベントは、フォームのポストバック要求を介してサーバー上に表示されます。 次の Web Forms のボタンをクリックする例を考えてみましょう。

*Counter.ascx*

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

Blazor では、`@on{event}` という形式のディレクティブ属性を使用して、DOM UI イベントのハンドラーを直接登録できます。 プレースホルダー `{event}` はイベントの名前を表します。 たとえば、次のようにボタンのクリックをリッスンできます。

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

イベント ハンドラーでは、イベントに関する詳細情報を提供するために、イベント固有の省略可能な引数を受け取ることができます。 たとえば、マウス イベントでは `MouseEventArgs` 引数を受け取ることができますが、必須ではありません。

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

イベント ハンドラーのメソッド グループを参照する代わりに、ラムダ式を使用できます。 ラムダ式を使用すると、スコープ内の他の値を閉じ込めることができます。

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

イベント ハンドラーは、同期または非同期で実行できます。 たとえば、次の `OnClick` イベント ハンドラーは非同期的に実行されます。

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

イベントが処理されると、コンポーネントの状態の変更を考慮してコンポーネントがレンダリングされます。 非同期イベント ハンドラーでは、ハンドラーの実行が完了した直後にコンポーネントがレンダリングされます。 非同期の `Task` の完了後に、コンポーネントは "*再び*" レンダリングされます。 この非同期実行モードでは、非同期の `Task` がまだ進行している間に、適切な UI をレンダリングすることができます。

```razor
<button @onclick="ShowMessage">Get message</button>

@if (showMessage)
{
    @if (message == null)
    {
        <p><em>Loading...</em></p>
    }
    else
    {
        <p>The message is: @message</p>
    }
}

@code
{
    bool showMessage = false;
    string message;

    public async Task ShowMessage()
    {
        showMessage = true;
        message = await MessageService.GetMessageAsync();
    }
}
```

コンポーネントでは、`EventCallback<TValue>` 型のコンポーネント パラメーターを定義することで、独自のイベントを定義することもできます。 イベント コールバックでは、省略可能な引数、同期または非同期、メソッド グループ、ラムダ式など、DOM UI イベント ハンドラーのすべてのバリエーションがサポートされます。

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>データ バインディング

Blazor には、UI コンポーネントのデータをコンポーネントの状態にバインドするための簡単なメカニズムが用意されています。 この方法は、データ ソースから UI コントロールにデータをバインドするための ASP.NET Web Forms の機能とは異なります。 さまざまなデータ ソースからのデータの処理については、「[データの処理](data.md)」セクションで説明します。

UI コンポーネントからコンポーネントの状態への双方向のデータ バインディングを作成するには、`@bind` ディレクティブ属性を使用します。 次の例では、チェック ボックスの値が `isChecked` フィールドにバインドされています。

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

コンポーネントがレンダリングされると、チェック ボックスの値が `isChecked` フィールドの値に設定されます。 ユーザーがチェック ボックスを切り替えると、`onchange` イベントが発生し、`isChecked` フィールドが新しい値に設定されます。 この場合の `@bind` 構文は、次のマークアップに相当します。

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

バインドに使用するイベントを変更するには、`@bind:event` 属性を使用します。

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

コンポーネントでは、パラメーターへのデータ バインディングもサポートできます。 データ バインドには、バインド可能なパラメーターと同じ名前でイベント コールバック パラメーターを定義します。 "Changed" というサフィックスが名前に追加されます。

*PasswordBox.razor*

```razor
Password: <input
    value="@Password"
    @oninput="OnPasswordChanged"
    type="@(showPassword ? "text" : "password")" />

<label><input type="checkbox" @bind="showPassword" />Show password</label>

@code {
    private bool showPassword;

    [Parameter]
    public string Password { get; set; }

    [Parameter]
    public EventCallback<string> PasswordChanged { get; set; }

    private Task OnPasswordChanged(ChangeEventArgs e)
    {
        Password = e.Value.ToString();
        return PasswordChanged.InvokeAsync(Password);
    }
}
```

データ バインディングを基になる UI 要素に連結するには、`@bind` 属性を使用するのではなく、UI 要素で直接に値を設定し、イベントを処理します。

コンポーネント パラメーターにバインドするには、`@bind-{Parameter}` 属性を使用して、バインド先のパラメーターを指定します。

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>状態変更

コンポーネントの状態が通常の UI イベントまたはイベント コールバックの外部で変更された場合、コンポーネントでは、再レンダリングが必要であることを手動で通知する必要があります。 コンポーネントの状態が変更されたことを通知するには、コンポーネントで `StateHasChanged` メソッドを呼び出します。

次の例のコンポーネントでは、アプリの他の部分による更新が可能な、`AppState` サービスからのメッセージが表示されます。 コンポーネントでは、その `StateHasChanged` メソッドを `AppState.OnChange` イベントに登録して、メッセージが更新されるたびにコンポーネントがレンダリングされるようにします。

```csharp
public class AppState
{
    public string Message { get; }

    // Lets components receive change notifications
    public event Action OnChange;

    public void UpdateMessage(string message)
    {
        Message = message;
        NotifyStateChanged();
    }

    private void NotifyStateChanged() => OnChange?.Invoke();
}
```

```razor
@inject AppState AppState

<p>App message: @AppState.Message</p>

@code {
    protected override void OnInitialized()
    {
        AppState.OnChange += StateHasChanged
    }
}
```

## <a name="component-lifecycle"></a>コンポーネントのライフサイクル

ASP.NET Web Forms フレームワークには、モジュール、ページ、およびコントロールに対して明確に定義されたライフサイクル メソッドがあります。 たとえば、次のコントロールでは、`Init`、`Load`、および `UnLoad` の各ライフサイクル イベントのイベント ハンドラーを実装しています。

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Blazor コンポーネントには、明確に定義されたライフサイクルもあります。 コンポーネントのライフサイクルは、コンポーネントの状態を初期化し、コンポーネントの高度な動作を実装するために使用できます。

Blazor のコンポーネント ライフサイクル メソッドのすべてに、同期バージョンと非同期バージョンの両方があります。 コンポーネントのレンダリングは同期的です。 コンポーネントのレンダリングの一部として非同期ロジックを実行することはできません。 すべての非同期ロジックは、`async` ライフサイクル メソッドの一部として実行する必要があります。

### <a name="oninitialized"></a>OnInitialized

`OnInitialized` および `OnInitializedAsync` メソッドは、コンポーネントの初期化に使用されます。 コンポーネントは通常、最初のレンダリング後に初期化されます。 コンポーネントは、初期化された後、最終的に破棄されるまでに、複数回レンダリングされる可能性があります。 `OnInitialized` メソッドは、ASP.NET Web Forms のページおよびコントロールでの `Page_Load` イベントに似ています。

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>OnParametersSet

`OnParametersSet` および `OnParametersSetAsync` メソッドは、コンポーネントが親からパラメーターを受け取り、値がプロパティに割り当てられるときに呼び出されます。 これらのメソッドは、コンポーネントの初期化後、および "*コンポーネントがレンダリングされるたびに*" 実行されます。

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>OnAfterRender

`OnAfterRender` および `OnAfterRenderAsync` メソッドは、コンポーネントのレンダリングが完了した後に呼び出されます。 この時点で、要素参照とコンポーネント参照が設定されます (これらの概念については後述します)。 この時点で、ブラウザーとの対話機能が有効になっています。 DOM および JavaScript の実行との対話を安全に実行できます。

```csharp
protected override void OnAfterRender(bool firstRender)
{
    if (firstRender)
    {
        ...
    }
}
protected override async Task OnAfterRenderAsync(bool firstRender)
{
    if (firstRender)
    {
        await ...
    }
}
```

`OnAfterRender` と `OnAfterRenderAsync` は、"*サーバー上でプリレンダリングするときには呼び出されません*"。

`firstRender` パラメーターの値は、コンポーネントが初めてレンダリングされるときには `true` で、それ以外の場合は `false` です。

### <a name="idisposable"></a>IDisposable

Blazor コンポーネントで `IDisposable` を実装すると、コンポーネントが UI から削除されたときにリソースを破棄できます。 Razor コンポーネントでは、`@implements` ディレクティブを使用して `IDispose` を実装できます。

```razor
@using System
@implements IDisposable

...

@code {
    public void Dispose()
    {
        ...
    }
}
```

## <a name="capture-component-references"></a>コンポーネント参照のキャプチャ

ASP.NET Web Forms では、ID を参照することによって、コントロール インスタンスをコード内で直接操作するのが一般的です。 Blazor では、コンポーネントへの参照をキャプチャして操作することもできますが、これはあまり一般的ではありません。

Blazor でコンポーネント参照をキャプチャするには、`@ref` ディレクティブ属性を使用します。 属性の値は、参照されるコンポーネントと同じ型の設定可能フィールドの名前と一致している必要があります。

```razor
<MyLoginDialog @ref="loginDialog" ... />

@code {
    MyLoginDialog loginDialog;

    void OnSomething()
    {
        loginDialog.Show();
    }
}
```

親コンポーネントがレンダリングされると、フィールドに子コンポーネント インスタンスが設定されます。 その後、コンポーネント インスタンスに対してメソッドの呼び出しやその他の操作を行うことができます。

コンポーネント参照を使用してコンポーネントの状態を直接操作することは推奨されません。 そのようにすると、コンポーネントが適時に自動的にレンダリングされなくなります。

## <a name="capture-element-references"></a>要素参照のキャプチャ

Blazor コンポーネントでは、要素への参照をキャプチャできます。 ASP.NET Web Forms の HTML サーバー コントロールとは異なり、Blazor で要素参照を使用して DOM を直接操作することはできません。 Blazor では、DOM 比較アルゴリズムを使用して、ほとんどの DOM 対話が処理されます。 Blazor のキャプチャされた要素参照は不透明です。 ただし、JavaScript 相互運用呼び出しで特定の要素参照を渡すために使用されます。 JavaScript 相互運用機能の詳細については、[ASP.NET Core Blazor の JavaScript 相互運用機能](/aspnet/core/blazor/javascript-interop)に関するページを参照してください。

## <a name="templated-components"></a>テンプレート コンポーネント

ASP.NET Web Forms では、"*テンプレート コントロール*" を作成できます。 開発者は、テンプレート コントロールを使用して、コンテナー コントロールのレンダリングに使用する HTML の一部を指定できます。 テンプレート化されたサーバー コントロールを構築するメカニズムは複雑ですが、ユーザーによるカスタマイズが可能な方法でデータをレンダリングできる、強力なシナリオを実現します。 テンプレート コントロールの例として、`Repeater` や `DataList` などが挙げられます。

Blazor コンポーネントは、`RenderFragment` または `RenderFragment<T>` 型のコンポーネント パラメーターを定義することによってテンプレート化することもできます。 `RenderFragment` は、コンポーネントによってレンダリングできるひとまとまりの Razor マークアップを表します。 `RenderFragment<T>` は、レンダー フラグメントのレンダリング時に指定できるパラメーターを受け取る、ひとまとまりの Razor マークアップです。

### <a name="child-content"></a>子コンテンツ

Blazor コンポーネントでは、子コンテンツを `RenderFragment` としてキャプチャし、そのコンテンツをコンポーネント レンダリングの一部としてレンダリングできます。 子コンテンツをキャプチャするには、`RenderFragment` 型のコンポーネント パラメーターを定義し、`ChildContent` という名前を付けます。

*ChildContentComponent.razor*

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

その後、親コンポーネントでは、通常の Razor 構文を使用して子コンテンツを提供できます。

```razor
<ChildContentComponent>
    <ChildContent>
        <p>The time is @DateTime.Now</p>
    </ChildContent>
</ChildContentComponent>
```

### <a name="template-parameters"></a>テンプレート パラメーター

また、Blazor のテンプレート コンポーネントでは、`RenderFragment` または `RenderFragment<T>` 型のコンポーネント パラメーターを複数定義することもできます。 `RenderFragment<T>` のパラメーターは、呼び出されたときに指定できます。 コンポーネントのジェネリック型パラメーターを指定するには、Razor ディレクティブ `@typeparam` を使用します。

*SimpleListView.razor*

```razor
@typeparam TItem

@Heading

<ul>
@foreach (var item in Items)
{
    <li>@ItemTemplate(item)</li>
}
</ul>

@code {
    [Parameter]
    public RenderFragment Heading { get; set; }

    [Parameter]
    public RenderFragment<TItem> ItemTemplate { get; set; }

    [Parameter]
    public IEnumerable<TItem> Items { get; set; }
}
```

テンプレート コンポーネントを使用する場合、テンプレート パラメーターは、パラメーターの名前と一致する子要素を使用して指定することができます。 要素として渡される `RenderFragment<T>` 型のコンポーネント引数には、`context` という名前の暗黙的なパラメーターがあります。 この実装パラメーターの名前は、子要素の `Context` 属性を使用して変更できます。 任意のジェネリック型パラメーターを、型パラメーターの名前と一致する属性を使用して指定できます。 可能な場合は、型パラメーターが推論されます。

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Context="message">
        <p>The message is: @message</p>
    </ItemTemplate>
</SimpleListView>
```

このコンポーネントの出力は次のようになります。

```html
<h1>My list</h1>
<ul>
    <li><p>The message is: message1</p></li>
    <li><p>The message is: message2</p></li>
<ul>
```

## <a name="code-behind"></a>分離コード

Blazor コンポーネントは通常、単一の *.razor* ファイルで作成されます。 ただし、分離コード ファイルを使用して、コードとマークアップを分離することもできます。 コンポーネント ファイルを使用するには、コンポーネント ファイルのファイル名と一致し、 *.cs* 拡張子を追加した C# ファイルを追加します (*Counter.razor.cs*)。 コンポーネントの基本クラスを定義するには、C# ファイルを使用します。 基本クラスには任意の名前を付けることができますが、コンポーネント クラスと同じ名前を付けて `Base` 拡張子を追加するのが一般的です (`CounterBase`)。 コンポーネント ベースのクラスも、`ComponentBase` から派生する必要があります。 次に、Razor コンポーネント ファイルで、`@inherits` ディレクティブを追加してコンポーネントの基本クラスを指定します (`@inherits CounterBase`)。

*Counter.razor*

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

*Counter.razor.cs*

```csharp
public class CounterBase : ComponentBase
{
    protected int currentCount = 0;

    protected void IncrementCount()
    {
        currentCount++;
    }
}
```

基本クラスのコンポーネントのメンバーの可視性は、コンポーネント クラスから参照できるように `protected` または `public` である必要があります。

## <a name="additional-resources"></a>その他のリソース

上記は、Blazor コンポーネントのすべての側面を網羅するものではありません。 [ASP.NET Core Razor コンポーネントの作成と使用](/aspnet/core/blazor/components)の方法について詳しくは、Blazor のドキュメントを参照してください。

>[!div class="step-by-step"]
>[前へ](app-startup.md)
>[次へ](pages-routing-layouts.md)
