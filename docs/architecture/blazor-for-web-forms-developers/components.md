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
# <a name="build-reusable-ui-components-with-blazor"></a><span data-ttu-id="69a9d-103">Blazor を使用して再利用可能な UI コンポーネントを構築する</span><span class="sxs-lookup"><span data-stu-id="69a9d-103">Build reusable UI components with Blazor</span></span>

<span data-ttu-id="69a9d-104">ASP.NET Web Forms の優れた点の 1 つは、再利用可能なユーザー インターフェイス (UI) コードを再利用可能な UI コントロールにカプセル化できることです。</span><span class="sxs-lookup"><span data-stu-id="69a9d-104">One of the beautiful things about ASP.NET Web Forms is how it enables encapsulation of reusable pieces of user interface (UI) code into reusable UI controls.</span></span> <span data-ttu-id="69a9d-105">*.ascx* ファイルを使用してマークアップでカスタム ユーザー コントロールを定義できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-105">Custom user controls can be defined in markup using *.ascx* files.</span></span> <span data-ttu-id="69a9d-106">デザイナーの完全なサポートを備えたコードで、複雑なサーバー コントロールを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-106">You can also build elaborate server controls in code with full designer support.</span></span>

<span data-ttu-id="69a9d-107">Blazor では、"*コンポーネント*" による UI カプセル化もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="69a9d-107">Blazor also supports UI encapsulation through *components*.</span></span> <span data-ttu-id="69a9d-108">コンポーネントとは:</span><span class="sxs-lookup"><span data-stu-id="69a9d-108">A component:</span></span>

- <span data-ttu-id="69a9d-109">自己完結型のひとまとまりの UI です。</span><span class="sxs-lookup"><span data-stu-id="69a9d-109">Is a self-contained chunk of UI.</span></span>
- <span data-ttu-id="69a9d-110">自身の状態およびレンダリング ロジックを保持します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-110">Maintains its own state and rendering logic.</span></span>
- <span data-ttu-id="69a9d-111">UI イベント ハンドラーを定義し、入力データにバインドし、自身のライフサイクルを管理できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-111">Can define UI event handlers, bind to input data, and manage its own lifecycle.</span></span>
- <span data-ttu-id="69a9d-112">通常、Razor 構文を使用して *.razor* ファイルで定義されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-112">Is typically defined in a *.razor* file using Razor syntax.</span></span>

## <a name="an-introduction-to-razor"></a><span data-ttu-id="69a9d-113">Razor の概要</span><span class="sxs-lookup"><span data-stu-id="69a9d-113">An introduction to Razor</span></span>

<span data-ttu-id="69a9d-114">Razor は、HTML および C# に基づく軽量のマークアップ テンプレート言語です。</span><span class="sxs-lookup"><span data-stu-id="69a9d-114">Razor is a light-weight markup templating language based on HTML and C#.</span></span> <span data-ttu-id="69a9d-115">Razor を使用すると、マークアップと C# のコードをシームレスに切り替えて、コンポーネントのレンダリング ロジックを定義できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-115">With Razor, you can seamlessly transition between markup and C# code to define your component rendering logic.</span></span> <span data-ttu-id="69a9d-116">*.razor* ファイルがコンパイルされると、レンダリング ロジックは構造化された方法で .NET クラスに取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-116">When the *.razor* file is compiled, the rendering logic is captured in a structured way in a .NET class.</span></span> <span data-ttu-id="69a9d-117">コンパイル済みクラスの名前は、 *.razor* ファイルの名前から取得されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-117">The name of the compiled class is taken from the *.razor* file name.</span></span> <span data-ttu-id="69a9d-118">名前空間は、プロジェクトの既定の名前空間とフォルダー パスから取得されます。また、`@namespace` ディレクティブを使用して名前空間を明示的に指定することもできます (Razor ディレクティブの詳細については後述します)。</span><span class="sxs-lookup"><span data-stu-id="69a9d-118">The namespace is taken from the default namespace for the project and the folder path, or you can explicitly specify the namespace using the `@namespace` directive (more on Razor directives below).</span></span>

<span data-ttu-id="69a9d-119">コンポーネントのレンダリング ロジックは、通常の HTML マークアップと、C# によって追加される動的ロジックを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-119">A component's rendering logic is authored using normal HTML markup with dynamic logic added using C#.</span></span> <span data-ttu-id="69a9d-120">`@` 文字は、C# に切り替えるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-120">The `@` character is used to transition to C#.</span></span> <span data-ttu-id="69a9d-121">HTML に戻すと、通常は Razor で適切に把握されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-121">Razor is typically smart about figuring out when you've switched back to HTML.</span></span> <span data-ttu-id="69a9d-122">たとえば、次のコンポーネントでは、`<p>` タグが現在の時刻でレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-122">For example, the following component renders a `<p>` tag with the current time:</span></span>

```razor
<p>@DateTime.Now</p>
```

<span data-ttu-id="69a9d-123">C# の式の開始と終了を明示的に指定するには、かっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-123">To explicitly specify the beginning and ending of a C# expression, use parentheses:</span></span>

```razor
<p>@(DateTime.Now)</p>
```

<span data-ttu-id="69a9d-124">Razor では、レンダリング ロジックで C# の制御フローを使用することも簡単になります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-124">Razor also makes it easy to use C# control flow in your rendering logic.</span></span> <span data-ttu-id="69a9d-125">たとえば、次のような HTML を条件付きでレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-125">For example, you can conditionally render some HTML like this:</span></span>

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

<span data-ttu-id="69a9d-126">または、次のような通常の C# `foreach` ループを使用して項目の一覧を生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-126">Or you can generate a list of items using a normal C# `foreach` loop like this:</span></span>

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

<span data-ttu-id="69a9d-127">ASP.NET Web Forms のディレクティブと同様に、Razor のディレクティブでは Razor コンポーネントのコンパイル方法の多くの側面を制御します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-127">Razor directives, like directives in ASP.NET Web Forms, control many aspects of how a Razor component is compiled.</span></span> <span data-ttu-id="69a9d-128">たとえば、コンポーネントの次のような点です。</span><span class="sxs-lookup"><span data-stu-id="69a9d-128">Examples include the component's:</span></span>

- <span data-ttu-id="69a9d-129">名前空間</span><span class="sxs-lookup"><span data-stu-id="69a9d-129">Namespace</span></span>
- <span data-ttu-id="69a9d-130">基本クラス</span><span class="sxs-lookup"><span data-stu-id="69a9d-130">Base class</span></span>
- <span data-ttu-id="69a9d-131">実装されるインターフェイス</span><span class="sxs-lookup"><span data-stu-id="69a9d-131">Implemented interfaces</span></span>
- <span data-ttu-id="69a9d-132">ジェネリック パラメーター</span><span class="sxs-lookup"><span data-stu-id="69a9d-132">Generic parameters</span></span>
- <span data-ttu-id="69a9d-133">[インポートされた名前空間]</span><span class="sxs-lookup"><span data-stu-id="69a9d-133">Imported namespaces</span></span>
- <span data-ttu-id="69a9d-134">ルート</span><span class="sxs-lookup"><span data-stu-id="69a9d-134">Routes</span></span>

<span data-ttu-id="69a9d-135">Razor ディレクティブは、`@` 文字で始まり、通常はファイルの先頭にある新しい行の先頭で使用されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-135">Razor directives start with the `@` character and are typically used at the start of a new line at the start of the file.</span></span> <span data-ttu-id="69a9d-136">たとえば、`@namespace` ディレクティブでは、コンポーネントの名前空間が定義されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-136">For example, the `@namespace` directive defines the component's namespace:</span></span>

```razor
@namespace MyComponentNamespace
```

<span data-ttu-id="69a9d-137">次の表は、Blazor で使用されるさまざまな Razor ディレクティブと、ASP.NET Web Forms でそれに相当するもの (存在する場合) をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="69a9d-137">The following table summarizes the various Razor directives used in Blazor and their ASP.NET Web Forms equivalents, if they exist.</span></span>

|<span data-ttu-id="69a9d-138">ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="69a9d-138">Directive</span></span>    |<span data-ttu-id="69a9d-139">説明</span><span class="sxs-lookup"><span data-stu-id="69a9d-139">Description</span></span>|<span data-ttu-id="69a9d-140">例</span><span class="sxs-lookup"><span data-stu-id="69a9d-140">Example</span></span>|<span data-ttu-id="69a9d-141">Web Forms で相当するもの</span><span class="sxs-lookup"><span data-stu-id="69a9d-141">Web Forms equivalent</span></span>|
|-------------|-----------|-------|--------------------|
|`@attribute` |<span data-ttu-id="69a9d-142">コンポーネントにクラス レベルの属性を追加します</span><span class="sxs-lookup"><span data-stu-id="69a9d-142">Adds a class-level attribute to the component</span></span>|`@attribute [Authorize]`|<span data-ttu-id="69a9d-143">なし</span><span class="sxs-lookup"><span data-stu-id="69a9d-143">None</span></span>|
|`@code`      |<span data-ttu-id="69a9d-144">コンポーネントにクラス メンバーを追加します</span><span class="sxs-lookup"><span data-stu-id="69a9d-144">Adds class members to the component</span></span>|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|<span data-ttu-id="69a9d-145">指定されたインターフェイスを実装します</span><span class="sxs-lookup"><span data-stu-id="69a9d-145">Implements the specified interface</span></span>|`@implements IDisposable`|<span data-ttu-id="69a9d-146">コードビハインドを使用する</span><span class="sxs-lookup"><span data-stu-id="69a9d-146">Use code-behind</span></span>|
|`@inherits`  |<span data-ttu-id="69a9d-147">指定された基本クラスを継承します</span><span class="sxs-lookup"><span data-stu-id="69a9d-147">Inherits from the specified base class</span></span>|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |<span data-ttu-id="69a9d-148">コンポーネントにサービスを挿入します</span><span class="sxs-lookup"><span data-stu-id="69a9d-148">Injects a service into the component</span></span>|`@inject IJSRuntime JS`|<span data-ttu-id="69a9d-149">なし</span><span class="sxs-lookup"><span data-stu-id="69a9d-149">None</span></span>|
|`@layout`    |<span data-ttu-id="69a9d-150">コンポーネントのレイアウト コンポーネントを指定します</span><span class="sxs-lookup"><span data-stu-id="69a9d-150">Specifies a layout component for the component</span></span>|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |<span data-ttu-id="69a9d-151">コンポーネントの名前空間を設定します</span><span class="sxs-lookup"><span data-stu-id="69a9d-151">Sets the namespace for the component</span></span>|`@namespace MyNamespace`|<span data-ttu-id="69a9d-152">なし</span><span class="sxs-lookup"><span data-stu-id="69a9d-152">None</span></span>|
|`@page`      |<span data-ttu-id="69a9d-153">コンポーネントのルートを指定します</span><span class="sxs-lookup"><span data-stu-id="69a9d-153">Specifies the route for the component</span></span>|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |<span data-ttu-id="69a9d-154">コンポーネントのジェネリック型パラメーターを指定します</span><span class="sxs-lookup"><span data-stu-id="69a9d-154">Specifies a generic type parameter for the component</span></span>|`@typeparam TItem`|<span data-ttu-id="69a9d-155">コードビハインドを使用する</span><span class="sxs-lookup"><span data-stu-id="69a9d-155">Use code-behind</span></span>|
|`@using`     |<span data-ttu-id="69a9d-156">スコープに取り込む名前空間を指定します</span><span class="sxs-lookup"><span data-stu-id="69a9d-156">Specifies a namespace to bring into scope</span></span>|`@using MyComponentNamespace`|<span data-ttu-id="69a9d-157">*web.config* に名前空間を追加する</span><span class="sxs-lookup"><span data-stu-id="69a9d-157">Add namespace in *web.config*</span></span>|

<span data-ttu-id="69a9d-158">また、Razor コンポーネントでは、要素に対して "*ディレクティブ属性*" を広範に使用して、コンポーネントのコンパイル方法のさまざまな側面 (イベント処理、データ バインディング、コンポーネントと要素の参照など)を制御します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-158">Razor components also make extensive use of *directive attributes* on elements to control various aspects of how components get compiled (event handling, data binding, component & element references, and so on).</span></span> <span data-ttu-id="69a9d-159">ディレクティブ属性はすべて、共通の汎用構文に従います。かっこ内の値は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="69a9d-159">Directive attributes all follow a common generic syntax where the values in parenthesis are optional:</span></span>

```razor
@directive(-suffix(:name))(="value")
```

<span data-ttu-id="69a9d-160">次の表は、Blazor で使用される Razor ディレクティブのさまざまな属性をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="69a9d-160">The following table summarizes the various attributes for Razor directives used in Blazor.</span></span>

|<span data-ttu-id="69a9d-161">属性</span><span class="sxs-lookup"><span data-stu-id="69a9d-161">Attribute</span></span>    |<span data-ttu-id="69a9d-162">説明</span><span class="sxs-lookup"><span data-stu-id="69a9d-162">Description</span></span>|<span data-ttu-id="69a9d-163">例</span><span class="sxs-lookup"><span data-stu-id="69a9d-163">Example</span></span>|
|-------------|-----------|-------|
|`@attributes`|<span data-ttu-id="69a9d-164">属性のディクショナリをレンダリングします</span><span class="sxs-lookup"><span data-stu-id="69a9d-164">Renders a dictionary of attributes</span></span>|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |<span data-ttu-id="69a9d-165">双方向のデータ バインディングを作成します</span><span class="sxs-lookup"><span data-stu-id="69a9d-165">Creates a two-way data binding</span></span>    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |<span data-ttu-id="69a9d-166">指定されたイベントのイベント ハンドラーを追加します</span><span class="sxs-lookup"><span data-stu-id="69a9d-166">Adds an event handler for the specified event</span></span>|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |<span data-ttu-id="69a9d-167">コレクション内の要素を保持するために比較アルゴリズムで使用するキーを指定します</span><span class="sxs-lookup"><span data-stu-id="69a9d-167">Specifies a key to be used by the diffing algorithm for preserving elements in a collection</span></span>|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |<span data-ttu-id="69a9d-168">コンポーネントまたは HTML 要素への参照をキャプチャします</span><span class="sxs-lookup"><span data-stu-id="69a9d-168">Captures a reference to the component or HTML element</span></span>|`<MyDialog @ref="myDialog" />`|

<span data-ttu-id="69a9d-169">Blazor で使用されるさまざまなディレクティブ (`@onclick`、`@bind`、`@ref` など) については、以下の各セクションと以降の章で説明します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-169">The various directive attributes used by Blazor (`@onclick`, `@bind`, `@ref`, and so on) are covered in the sections below and later chapters.</span></span>

<span data-ttu-id="69a9d-170">*.aspx* および *.ascx* ファイルで使用される構文の多くに、類似の Razor 構文があります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-170">Many of the syntaxes used in *.aspx* and *.ascx* files have parallel syntaxes in Razor.</span></span> <span data-ttu-id="69a9d-171">次に、ASP.NET Web Forms と Razor の構文を簡単に比較します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-171">Below is a simple comparison of the syntaxes for ASP.NET Web Forms and Razor.</span></span>

|<span data-ttu-id="69a9d-172">機能</span><span class="sxs-lookup"><span data-stu-id="69a9d-172">Feature</span></span>                      |<span data-ttu-id="69a9d-173">Web フォーム</span><span class="sxs-lookup"><span data-stu-id="69a9d-173">Web Forms</span></span>           |<span data-ttu-id="69a9d-174">構文</span><span class="sxs-lookup"><span data-stu-id="69a9d-174">Syntax</span></span>               |<span data-ttu-id="69a9d-175">Razor</span><span class="sxs-lookup"><span data-stu-id="69a9d-175">Razor</span></span>         |<span data-ttu-id="69a9d-176">構文</span><span class="sxs-lookup"><span data-stu-id="69a9d-176">Syntax</span></span> |
|-----------------------------|--------------------|---------------------|--------------|-------|
|<span data-ttu-id="69a9d-177">ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="69a9d-177">Directives</span></span>                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|<span data-ttu-id="69a9d-178">コード ブロック</span><span class="sxs-lookup"><span data-stu-id="69a9d-178">Code blocks</span></span>                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|<span data-ttu-id="69a9d-179">式</span><span class="sxs-lookup"><span data-stu-id="69a9d-179">Expressions</span></span><br><span data-ttu-id="69a9d-180">(HTML エンコード)</span><span class="sxs-lookup"><span data-stu-id="69a9d-180">(HTML-encoded)</span></span>|`<%: %>`            |`<%:DateTime.Now %>` |<span data-ttu-id="69a9d-181">暗黙的: `@`</span><span class="sxs-lookup"><span data-stu-id="69a9d-181">Implicit: `@`</span></span><br><span data-ttu-id="69a9d-182">明示的: `@()`</span><span class="sxs-lookup"><span data-stu-id="69a9d-182">Explicit: `@()`</span></span>|`@DateTime.Now`<br>`@(DateTime.Now)`|
|<span data-ttu-id="69a9d-183">コメント</span><span class="sxs-lookup"><span data-stu-id="69a9d-183">Comments</span></span>                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|<span data-ttu-id="69a9d-184">データ バインディング</span><span class="sxs-lookup"><span data-stu-id="69a9d-184">Data binding</span></span>                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

<span data-ttu-id="69a9d-185">Razor コンポーネント クラスにメンバーを追加するには、`@code` ディレクティブを使用します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-185">To add members to the Razor component class, use the `@code` directive.</span></span> <span data-ttu-id="69a9d-186">この手法は、ASP.NET Web Forms のユーザー コントロールまたはページで `<script runat="server">...</script>` ブロックを使用するのと似ています。</span><span class="sxs-lookup"><span data-stu-id="69a9d-186">This technique is similar to using a `<script runat="server">...</script>` block in an ASP.NET Web Forms user control or page.</span></span>

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

<span data-ttu-id="69a9d-187">Razor は C# に基づいているため、C# プロジェクト ( *.csproj*) 内からコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-187">Because Razor is based on C#, it must be compiled from within a C# project (*.csproj*).</span></span> <span data-ttu-id="69a9d-188">Visual Basic プロジェクト ( *.vbproj*) から *.razor* ファイルをコンパイルすることはできません。</span><span class="sxs-lookup"><span data-stu-id="69a9d-188">You can't compile *.razor* files from a Visual Basic project (*.vbproj*).</span></span> <span data-ttu-id="69a9d-189">ただし、Blazor プロジェクトから Visual Basic プロジェクトを参照することはできます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-189">You can still reference Visual Basic projects from your Blazor project.</span></span> <span data-ttu-id="69a9d-190">逆も同様です。</span><span class="sxs-lookup"><span data-stu-id="69a9d-190">The opposite is true too.</span></span>

<span data-ttu-id="69a9d-191">Razor 構文の完全なリファレンスについては、「[ASP.NET Core の Razor 構文リファレンス](/aspnet/core/mvc/views/razor)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69a9d-191">For a full Razor syntax reference, see [Razor syntax reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span></span>

## <a name="use-components"></a><span data-ttu-id="69a9d-192">コンポーネントを使う</span><span class="sxs-lookup"><span data-stu-id="69a9d-192">Use components</span></span>

<span data-ttu-id="69a9d-193">コンポーネントでは、通常の HTML の他に、他のコンポーネントをレンダリング ロジックの一部として使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-193">Aside from normal HTML, components can also use other components as part of their rendering logic.</span></span> <span data-ttu-id="69a9d-194">Razor でコンポーネントを使用するための構文は、ASP.NET Web Forms アプリでユーザー コントロールを使用する場合と似ています。</span><span class="sxs-lookup"><span data-stu-id="69a9d-194">The syntax for using a component in Razor is similar to using a user control in an ASP.NET Web Forms app.</span></span> <span data-ttu-id="69a9d-195">コンポーネントは、コンポーネントの型名と一致する要素タグを使用して指定されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-195">Components are specified using an element tag that matches the type name of the component.</span></span> <span data-ttu-id="69a9d-196">たとえば、次のように `Counter` コンポーネントを追加できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-196">For example, you can add a `Counter` component like this:</span></span>

```razor
<Counter />
```

<span data-ttu-id="69a9d-197">ASP.NET Web Forms とは異なり、Blazor のコンポーネントでは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-197">Unlike ASP.NET Web Forms, components in Blazor:</span></span>

- <span data-ttu-id="69a9d-198">要素のプレフィックスは使用しません (例: `asp:`)。</span><span class="sxs-lookup"><span data-stu-id="69a9d-198">Don't use an element prefix (for example, `asp:`).</span></span>
- <span data-ttu-id="69a9d-199">ページまたは *web.config* での登録は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="69a9d-199">Don't require registration on the page or in the *web.config*.</span></span>

<span data-ttu-id="69a9d-200">Razor コンポーネントについては .NET 型と同様に考えてください。なぜなら、まさにそのようなものだからです。</span><span class="sxs-lookup"><span data-stu-id="69a9d-200">Think of Razor components like you would .NET types, because that's exactly what they are.</span></span> <span data-ttu-id="69a9d-201">コンポーネントを含むアセンブリが参照されると、コンポーネントが使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-201">If the assembly containing the component is referenced, then the component is available for use.</span></span> <span data-ttu-id="69a9d-202">コンポーネントの名前空間をスコープに取り込むには、`@using` ディレクティブを適用します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-202">To bring the component's namespace into scope, apply the `@using` directive:</span></span>

```razor
@using MyComponentLib

<Counter />
```

<span data-ttu-id="69a9d-203">既定の Blazor プロジェクトに見られるように、`@using` ディレクティブを *_Imports.razor* ファイルに配置して、同じディレクトリおよび子ディレクトリ内のすべての *.razor* ファイルにインポートされるようにするのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="69a9d-203">As seen in the default Blazor projects, it's common to put `@using` directives into a *_Imports.razor* file so that they're imported into all *.razor* files in the same directory and in child directories.</span></span>

<span data-ttu-id="69a9d-204">コンポーネントの名前空間がスコープ内にない場合は、C# の場合と同様に、完全な型名を使用してコンポーネントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-204">If the namespace for a component isn't in scope, you can specify a component using its full type name, as you can in C#:</span></span>

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a><span data-ttu-id="69a9d-205">コンポーネントのパラメーター</span><span class="sxs-lookup"><span data-stu-id="69a9d-205">Component parameters</span></span>

<span data-ttu-id="69a9d-206">ASP.NET Web Forms では、パブリック プロパティを使用して、パラメーターとデータをコントロールにフローできます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-206">In ASP.NET Web Forms, you can flow parameters and data to controls using public properties.</span></span> <span data-ttu-id="69a9d-207">これらのプロパティは、属性を使用してマークアップで設定することも、コードで直接設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-207">These properties can be set in markup using attributes or set directly in code.</span></span> <span data-ttu-id="69a9d-208">Blazor のコンポーネントも同様の方法で動作しますが、コンポーネントのプロパティがコンポーネントのパラメーターと見なされるようにするために `[Parameter]` 属性でマークする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-208">Blazor components work in a similar fashion, although the component properties must also be marked with the `[Parameter]` attribute to be considered component parameters.</span></span>

<span data-ttu-id="69a9d-209">次の `Counter` コンポーネントでは、`IncrementAmount` というコンポーネント パラメーターを定義しています。これを使用して、ボタンがクリックされるたびに `Counter` をインクリメントする量を指定できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-209">The following `Counter` component defines a component parameter called `IncrementAmount` that can be used to specify the amount that the `Counter` should be incremented each time the button is clicked.</span></span>

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

<span data-ttu-id="69a9d-210">Blazor でコンポーネント パラメーターを指定するには、ASP.NET Web Forms の場合と同様に属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-210">To specify a component parameter in Blazor, use an attribute as you would in ASP.NET Web Forms:</span></span>

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a><span data-ttu-id="69a9d-211">イベント ハンドラー</span><span class="sxs-lookup"><span data-stu-id="69a9d-211">Event handlers</span></span>

<span data-ttu-id="69a9d-212">ASP.NET Web Forms と Blazor のどちらにも、UI イベントを処理するためのイベント ベースのプログラミング モデルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="69a9d-212">Both ASP.NET Web Forms and Blazor provide an event-based programming model for handling UI events.</span></span> <span data-ttu-id="69a9d-213">このようなイベントの例としては、ボタンのクリックやテキスト入力などがあります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-213">Examples of such events include button clicks and text input.</span></span> <span data-ttu-id="69a9d-214">ASP.NET Web Forms では、HTML サーバー コントロールを使用して、DOM によって公開される UI イベントを処理したり、Web サーバー コントロールによって公開されるイベントを処理したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-214">In ASP.NET Web Forms, you use HTML server controls to handle UI events exposed by the DOM, or you can handle events exposed by web server controls.</span></span> <span data-ttu-id="69a9d-215">イベントは、フォームのポストバック要求を介してサーバー上に表示されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-215">The events are surfaced on the server through form post-back requests.</span></span> <span data-ttu-id="69a9d-216">次の Web Forms のボタンをクリックする例を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="69a9d-216">Consider the following Web Forms button click example:</span></span>

<span data-ttu-id="69a9d-217">*Counter.ascx*</span><span class="sxs-lookup"><span data-stu-id="69a9d-217">*Counter.ascx*</span></span>

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

<span data-ttu-id="69a9d-218">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="69a9d-218">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

<span data-ttu-id="69a9d-219">Blazor では、`@on{event}` という形式のディレクティブ属性を使用して、DOM UI イベントのハンドラーを直接登録できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-219">In Blazor, you can register handlers for DOM UI events directly using directive attributes of the form `@on{event}`.</span></span> <span data-ttu-id="69a9d-220">プレースホルダー `{event}` はイベントの名前を表します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-220">The `{event}` placeholder represents the name of the event.</span></span> <span data-ttu-id="69a9d-221">たとえば、次のようにボタンのクリックをリッスンできます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-221">For example, you can listen for button clicks like this:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

<span data-ttu-id="69a9d-222">イベント ハンドラーでは、イベントに関する詳細情報を提供するために、イベント固有の省略可能な引数を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-222">Event handlers can accept an optional, event-specific argument to provide more information about the event.</span></span> <span data-ttu-id="69a9d-223">たとえば、マウス イベントでは `MouseEventArgs` 引数を受け取ることができますが、必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="69a9d-223">For example, mouse events can take a `MouseEventArgs` argument, but it isn't required.</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

<span data-ttu-id="69a9d-224">イベント ハンドラーのメソッド グループを参照する代わりに、ラムダ式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-224">Instead of referring to a method group for an event handler, you can use a lambda expression.</span></span> <span data-ttu-id="69a9d-225">ラムダ式を使用すると、スコープ内の他の値を閉じ込めることができます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-225">A lambda expression allows you to close over other in-scope values.</span></span>

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

<span data-ttu-id="69a9d-226">イベント ハンドラーは、同期または非同期で実行できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-226">Event handlers can execute synchronously or asynchronously.</span></span> <span data-ttu-id="69a9d-227">たとえば、次の `OnClick` イベント ハンドラーは非同期的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-227">For example, the following `OnClick` event handler executes asynchronously:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

<span data-ttu-id="69a9d-228">イベントが処理されると、コンポーネントの状態の変更を考慮してコンポーネントがレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-228">After an event is handled, the component is rendered to account for any component state changes.</span></span> <span data-ttu-id="69a9d-229">非同期イベント ハンドラーでは、ハンドラーの実行が完了した直後にコンポーネントがレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-229">With asynchronous event handlers, the component is rendered immediately after the handler execution completes.</span></span> <span data-ttu-id="69a9d-230">非同期の `Task` の完了後に、コンポーネントは "*再び*" レンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-230">The component is rendered *again* after the asynchronous `Task` completes.</span></span> <span data-ttu-id="69a9d-231">この非同期実行モードでは、非同期の `Task` がまだ進行している間に、適切な UI をレンダリングすることができます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-231">This asynchronous execution mode provides an opportunity to render some appropriate UI while the asynchronous `Task` is still in progress.</span></span>

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

<span data-ttu-id="69a9d-232">コンポーネントでは、`EventCallback<TValue>` 型のコンポーネント パラメーターを定義することで、独自のイベントを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-232">Components can also define their own events by defining a component parameter of type `EventCallback<TValue>`.</span></span> <span data-ttu-id="69a9d-233">イベント コールバックでは、省略可能な引数、同期または非同期、メソッド グループ、ラムダ式など、DOM UI イベント ハンドラーのすべてのバリエーションがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-233">Event callbacks support all the variations of DOM UI event handlers: optional arguments, synchronous or asynchronous, method groups, or lambda expressions.</span></span>

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a><span data-ttu-id="69a9d-234">データ バインディング</span><span class="sxs-lookup"><span data-stu-id="69a9d-234">Data binding</span></span>

<span data-ttu-id="69a9d-235">Blazor には、UI コンポーネントのデータをコンポーネントの状態にバインドするための簡単なメカニズムが用意されています。</span><span class="sxs-lookup"><span data-stu-id="69a9d-235">Blazor provides a simple mechanism to bind data from a UI component to the component's state.</span></span> <span data-ttu-id="69a9d-236">この方法は、データ ソースから UI コントロールにデータをバインドするための ASP.NET Web Forms の機能とは異なります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-236">This approach differs from the features in ASP.NET Web Forms for binding data from data sources to UI controls.</span></span> <span data-ttu-id="69a9d-237">さまざまなデータ ソースからのデータの処理については、「[データの処理](data.md)」セクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-237">We'll cover handling data from different data sources in the [Dealing with data](data.md) section.</span></span>

<span data-ttu-id="69a9d-238">UI コンポーネントからコンポーネントの状態への双方向のデータ バインディングを作成するには、`@bind` ディレクティブ属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-238">To create a two-way data binding from a UI component to the component's state, use the `@bind` directive attribute.</span></span> <span data-ttu-id="69a9d-239">次の例では、チェック ボックスの値が `isChecked` フィールドにバインドされています。</span><span class="sxs-lookup"><span data-stu-id="69a9d-239">In the following example, the value of the check box is bound to the `isChecked` field.</span></span>

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

<span data-ttu-id="69a9d-240">コンポーネントがレンダリングされると、チェック ボックスの値が `isChecked` フィールドの値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-240">When the component is rendered, the value of the checkbox is set to the value of the `isChecked` field.</span></span> <span data-ttu-id="69a9d-241">ユーザーがチェック ボックスを切り替えると、`onchange` イベントが発生し、`isChecked` フィールドが新しい値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-241">When the user toggles the checkbox, the `onchange` event is fired and the `isChecked` field is set to the new value.</span></span> <span data-ttu-id="69a9d-242">この場合の `@bind` 構文は、次のマークアップに相当します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-242">The `@bind` syntax in this case is equivalent to the following markup:</span></span>

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

<span data-ttu-id="69a9d-243">バインドに使用するイベントを変更するには、`@bind:event` 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-243">To change the event used for the bind, use the `@bind:event` attribute.</span></span>

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

<span data-ttu-id="69a9d-244">コンポーネントでは、パラメーターへのデータ バインディングもサポートできます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-244">Components can also support data binding to their parameters.</span></span> <span data-ttu-id="69a9d-245">データ バインドには、バインド可能なパラメーターと同じ名前でイベント コールバック パラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-245">To data bind, define an event callback parameter with the same name as the bindable parameter.</span></span> <span data-ttu-id="69a9d-246">"Changed" というサフィックスが名前に追加されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-246">The "Changed" suffix is added to the name.</span></span>

<span data-ttu-id="69a9d-247">*PasswordBox.razor*</span><span class="sxs-lookup"><span data-stu-id="69a9d-247">*PasswordBox.razor*</span></span>

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

<span data-ttu-id="69a9d-248">データ バインディングを基になる UI 要素に連結するには、`@bind` 属性を使用するのではなく、UI 要素で直接に値を設定し、イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-248">To chain a data binding to an underlying UI element, set the value and handle the event directly on the UI element instead of using the `@bind` attribute.</span></span>

<span data-ttu-id="69a9d-249">コンポーネント パラメーターにバインドするには、`@bind-{Parameter}` 属性を使用して、バインド先のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-249">To bind to a component parameter, use a `@bind-{Parameter}` attribute to specify the parameter to which you want to bind.</span></span>

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a><span data-ttu-id="69a9d-250">状態変更</span><span class="sxs-lookup"><span data-stu-id="69a9d-250">State changes</span></span>

<span data-ttu-id="69a9d-251">コンポーネントの状態が通常の UI イベントまたはイベント コールバックの外部で変更された場合、コンポーネントでは、再レンダリングが必要であることを手動で通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-251">If the component's state has changed outside of a normal UI event or event callback, then the component must manually signal that it needs to be rendered again.</span></span> <span data-ttu-id="69a9d-252">コンポーネントの状態が変更されたことを通知するには、コンポーネントで `StateHasChanged` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-252">To signal that a component's state has changed, call the `StateHasChanged` method on the component.</span></span>

<span data-ttu-id="69a9d-253">次の例のコンポーネントでは、アプリの他の部分による更新が可能な、`AppState` サービスからのメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-253">In the example below, a component displays a message from an `AppState` service that can be updated by other parts of the app.</span></span> <span data-ttu-id="69a9d-254">コンポーネントでは、その `StateHasChanged` メソッドを `AppState.OnChange` イベントに登録して、メッセージが更新されるたびにコンポーネントがレンダリングされるようにします。</span><span class="sxs-lookup"><span data-stu-id="69a9d-254">The component registers its `StateHasChanged` method with the `AppState.OnChange` event so that the component is rendered whenever the message gets updated.</span></span>

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

## <a name="component-lifecycle"></a><span data-ttu-id="69a9d-255">コンポーネントのライフサイクル</span><span class="sxs-lookup"><span data-stu-id="69a9d-255">Component lifecycle</span></span>

<span data-ttu-id="69a9d-256">ASP.NET Web Forms フレームワークには、モジュール、ページ、およびコントロールに対して明確に定義されたライフサイクル メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-256">The ASP.NET Web Forms framework has well-defined lifecycle methods for modules, pages, and controls.</span></span> <span data-ttu-id="69a9d-257">たとえば、次のコントロールでは、`Init`、`Load`、および `UnLoad` の各ライフサイクル イベントのイベント ハンドラーを実装しています。</span><span class="sxs-lookup"><span data-stu-id="69a9d-257">For example, the following control implements event handlers for the `Init`, `Load`, and `UnLoad` lifecycle events:</span></span>

<span data-ttu-id="69a9d-258">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="69a9d-258">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

<span data-ttu-id="69a9d-259">Blazor コンポーネントには、明確に定義されたライフサイクルもあります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-259">Blazor components also have a well-defined lifecycle.</span></span> <span data-ttu-id="69a9d-260">コンポーネントのライフサイクルは、コンポーネントの状態を初期化し、コンポーネントの高度な動作を実装するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-260">A component's lifecycle can be used to initialize component state and implement advanced component behaviors.</span></span>

<span data-ttu-id="69a9d-261">Blazor のコンポーネント ライフサイクル メソッドのすべてに、同期バージョンと非同期バージョンの両方があります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-261">All of Blazor's component lifecycle methods have both synchronous and asynchronous versions.</span></span> <span data-ttu-id="69a9d-262">コンポーネントのレンダリングは同期的です。</span><span class="sxs-lookup"><span data-stu-id="69a9d-262">Component rendering is synchronous.</span></span> <span data-ttu-id="69a9d-263">コンポーネントのレンダリングの一部として非同期ロジックを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="69a9d-263">You can't run asynchronous logic as part of the component rendering.</span></span> <span data-ttu-id="69a9d-264">すべての非同期ロジックは、`async` ライフサイクル メソッドの一部として実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-264">All asynchronous logic must execute as part of an `async` lifecycle method.</span></span>

### <a name="oninitialized"></a><span data-ttu-id="69a9d-265">OnInitialized</span><span class="sxs-lookup"><span data-stu-id="69a9d-265">OnInitialized</span></span>

<span data-ttu-id="69a9d-266">`OnInitialized` および `OnInitializedAsync` メソッドは、コンポーネントの初期化に使用されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-266">The `OnInitialized` and `OnInitializedAsync` methods are used to initialize the component.</span></span> <span data-ttu-id="69a9d-267">コンポーネントは通常、最初のレンダリング後に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-267">A component is typically initialized after it's first rendered.</span></span> <span data-ttu-id="69a9d-268">コンポーネントは、初期化された後、最終的に破棄されるまでに、複数回レンダリングされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-268">After a component is initialized, it may be rendered multiple times before it's eventually disposed.</span></span> <span data-ttu-id="69a9d-269">`OnInitialized` メソッドは、ASP.NET Web Forms のページおよびコントロールでの `Page_Load` イベントに似ています。</span><span class="sxs-lookup"><span data-stu-id="69a9d-269">The `OnInitialized` method is similar to the `Page_Load` event in ASP.NET Web Forms pages and controls.</span></span>

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a><span data-ttu-id="69a9d-270">OnParametersSet</span><span class="sxs-lookup"><span data-stu-id="69a9d-270">OnParametersSet</span></span>

<span data-ttu-id="69a9d-271">`OnParametersSet` および `OnParametersSetAsync` メソッドは、コンポーネントが親からパラメーターを受け取り、値がプロパティに割り当てられるときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-271">The `OnParametersSet` and `OnParametersSetAsync` methods are called when a component has received parameters from its parent and the value are assigned to properties.</span></span> <span data-ttu-id="69a9d-272">これらのメソッドは、コンポーネントの初期化後、および "*コンポーネントがレンダリングされるたびに*" 実行されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-272">These methods are executed after component initialization and *each time the component is rendered*.</span></span>

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a><span data-ttu-id="69a9d-273">OnAfterRender</span><span class="sxs-lookup"><span data-stu-id="69a9d-273">OnAfterRender</span></span>

<span data-ttu-id="69a9d-274">`OnAfterRender` および `OnAfterRenderAsync` メソッドは、コンポーネントのレンダリングが完了した後に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-274">The `OnAfterRender` and `OnAfterRenderAsync` methods are called after a component has finished rendering.</span></span> <span data-ttu-id="69a9d-275">この時点で、要素参照とコンポーネント参照が設定されます (これらの概念については後述します)。</span><span class="sxs-lookup"><span data-stu-id="69a9d-275">Element and component references are populated at this point (more on these concepts below).</span></span> <span data-ttu-id="69a9d-276">この時点で、ブラウザーとの対話機能が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="69a9d-276">Interactivity with the browser is enabled at this point.</span></span> <span data-ttu-id="69a9d-277">DOM および JavaScript の実行との対話を安全に実行できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-277">Interactions with the DOM and JavaScript execution can safely take place.</span></span>

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

<span data-ttu-id="69a9d-278">`OnAfterRender` と `OnAfterRenderAsync` は、"*サーバー上でプリレンダリングするときには呼び出されません*"。</span><span class="sxs-lookup"><span data-stu-id="69a9d-278">`OnAfterRender` and `OnAfterRenderAsync` *aren't called when prerendering on the server*.</span></span>

<span data-ttu-id="69a9d-279">`firstRender` パラメーターの値は、コンポーネントが初めてレンダリングされるときには `true` で、それ以外の場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="69a9d-279">The `firstRender` parameter is `true` the first time the component is rendered; otherwise, its value is `false`.</span></span>

### <a name="idisposable"></a><span data-ttu-id="69a9d-280">IDisposable</span><span class="sxs-lookup"><span data-stu-id="69a9d-280">IDisposable</span></span>

<span data-ttu-id="69a9d-281">Blazor コンポーネントで `IDisposable` を実装すると、コンポーネントが UI から削除されたときにリソースを破棄できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-281">Blazor components can implement `IDisposable` to dispose of resources when the component is removed from the UI.</span></span> <span data-ttu-id="69a9d-282">Razor コンポーネントでは、`@implements` ディレクティブを使用して `IDispose` を実装できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-282">A Razor component can implement `IDispose` by using the `@implements` directive:</span></span>

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

## <a name="capture-component-references"></a><span data-ttu-id="69a9d-283">コンポーネント参照のキャプチャ</span><span class="sxs-lookup"><span data-stu-id="69a9d-283">Capture component references</span></span>

<span data-ttu-id="69a9d-284">ASP.NET Web Forms では、ID を参照することによって、コントロール インスタンスをコード内で直接操作するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="69a9d-284">In ASP.NET Web Forms, it's common to manipulate a control instance directly in code by referring to its ID.</span></span> <span data-ttu-id="69a9d-285">Blazor では、コンポーネントへの参照をキャプチャして操作することもできますが、これはあまり一般的ではありません。</span><span class="sxs-lookup"><span data-stu-id="69a9d-285">In Blazor, it's also possible to capture and manipulate a reference to a component, although it's much less common.</span></span>

<span data-ttu-id="69a9d-286">Blazor でコンポーネント参照をキャプチャするには、`@ref` ディレクティブ属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-286">To capture a component reference in Blazor, use the `@ref` directive attribute.</span></span> <span data-ttu-id="69a9d-287">属性の値は、参照されるコンポーネントと同じ型の設定可能フィールドの名前と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-287">The value of the attribute should match the name of a settable field with the same type as the referenced component.</span></span>

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

<span data-ttu-id="69a9d-288">親コンポーネントがレンダリングされると、フィールドに子コンポーネント インスタンスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-288">When the parent component is rendered, the field is populated with the child component instance.</span></span> <span data-ttu-id="69a9d-289">その後、コンポーネント インスタンスに対してメソッドの呼び出しやその他の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-289">You can then call methods on, or otherwise manipulate, the component instance.</span></span>

<span data-ttu-id="69a9d-290">コンポーネント参照を使用してコンポーネントの状態を直接操作することは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="69a9d-290">Manipulating component state directly using component references isn't recommended.</span></span> <span data-ttu-id="69a9d-291">そのようにすると、コンポーネントが適時に自動的にレンダリングされなくなります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-291">Doing so prevents the component from being rendered automatically at the correct times.</span></span>

## <a name="capture-element-references"></a><span data-ttu-id="69a9d-292">要素参照のキャプチャ</span><span class="sxs-lookup"><span data-stu-id="69a9d-292">Capture element references</span></span>

<span data-ttu-id="69a9d-293">Blazor コンポーネントでは、要素への参照をキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-293">Blazor components can capture references to an element.</span></span> <span data-ttu-id="69a9d-294">ASP.NET Web Forms の HTML サーバー コントロールとは異なり、Blazor で要素参照を使用して DOM を直接操作することはできません。</span><span class="sxs-lookup"><span data-stu-id="69a9d-294">Unlike HTML server controls in ASP.NET Web Forms, you can't manipulate the DOM directly using an element reference in Blazor.</span></span> <span data-ttu-id="69a9d-295">Blazor では、DOM 比較アルゴリズムを使用して、ほとんどの DOM 対話が処理されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-295">Blazor handles most DOM interactions for you using its DOM diffing algorithm.</span></span> <span data-ttu-id="69a9d-296">Blazor のキャプチャされた要素参照は不透明です。</span><span class="sxs-lookup"><span data-stu-id="69a9d-296">Captured element references in Blazor are opaque.</span></span> <span data-ttu-id="69a9d-297">ただし、JavaScript 相互運用呼び出しで特定の要素参照を渡すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-297">However, they're used to pass a specific element reference in a JavaScript interop call.</span></span> <span data-ttu-id="69a9d-298">JavaScript 相互運用機能の詳細については、[ASP.NET Core Blazor の JavaScript 相互運用機能](/aspnet/core/blazor/javascript-interop)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="69a9d-298">For more information about JavaScript interop, see [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span></span>

## <a name="templated-components"></a><span data-ttu-id="69a9d-299">テンプレート コンポーネント</span><span class="sxs-lookup"><span data-stu-id="69a9d-299">Templated components</span></span>

<span data-ttu-id="69a9d-300">ASP.NET Web Forms では、"*テンプレート コントロール*" を作成できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-300">In ASP.NET Web Forms, you can create *templated controls*.</span></span> <span data-ttu-id="69a9d-301">開発者は、テンプレート コントロールを使用して、コンテナー コントロールのレンダリングに使用する HTML の一部を指定できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-301">Templated controls enable the developer to specify a portion of the HTML used to render a container control.</span></span> <span data-ttu-id="69a9d-302">テンプレート化されたサーバー コントロールを構築するメカニズムは複雑ですが、ユーザーによるカスタマイズが可能な方法でデータをレンダリングできる、強力なシナリオを実現します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-302">The mechanics of building templated server controls are complex, but they enable powerful scenarios for rendering data in a user customizable way.</span></span> <span data-ttu-id="69a9d-303">テンプレート コントロールの例として、`Repeater` や `DataList` などが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-303">Examples of templated controls include `Repeater` and `DataList`.</span></span>

<span data-ttu-id="69a9d-304">Blazor コンポーネントは、`RenderFragment` または `RenderFragment<T>` 型のコンポーネント パラメーターを定義することによってテンプレート化することもできます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-304">Blazor components can also be templated by defining component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="69a9d-305">`RenderFragment` は、コンポーネントによってレンダリングできるひとまとまりの Razor マークアップを表します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-305">A `RenderFragment` represents a chunk of Razor markup that can then be rendered by the component.</span></span> <span data-ttu-id="69a9d-306">`RenderFragment<T>` は、レンダー フラグメントのレンダリング時に指定できるパラメーターを受け取る、ひとまとまりの Razor マークアップです。</span><span class="sxs-lookup"><span data-stu-id="69a9d-306">A `RenderFragment<T>` is a chunk of Razor markup that takes a parameter that can be specified when the render fragment is rendered.</span></span>

### <a name="child-content"></a><span data-ttu-id="69a9d-307">子コンテンツ</span><span class="sxs-lookup"><span data-stu-id="69a9d-307">Child content</span></span>

<span data-ttu-id="69a9d-308">Blazor コンポーネントでは、子コンテンツを `RenderFragment` としてキャプチャし、そのコンテンツをコンポーネント レンダリングの一部としてレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-308">Blazor components can capture their child content as a `RenderFragment` and render that content as part of the component rendering.</span></span> <span data-ttu-id="69a9d-309">子コンテンツをキャプチャするには、`RenderFragment` 型のコンポーネント パラメーターを定義し、`ChildContent` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-309">To capture child content, define a component parameter of type `RenderFragment` and name it `ChildContent`.</span></span>

<span data-ttu-id="69a9d-310">*ChildContentComponent.razor*</span><span class="sxs-lookup"><span data-stu-id="69a9d-310">*ChildContentComponent.razor*</span></span>

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

<span data-ttu-id="69a9d-311">その後、親コンポーネントでは、通常の Razor 構文を使用して子コンテンツを提供できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-311">A parent component can then supply child content using normal Razor syntax.</span></span>

```razor
<ChildContentComponent>
    <ChildContent>
        <p>The time is @DateTime.Now</p>
    </ChildContent>
</ChildContentComponent>
```

### <a name="template-parameters"></a><span data-ttu-id="69a9d-312">テンプレート パラメーター</span><span class="sxs-lookup"><span data-stu-id="69a9d-312">Template parameters</span></span>

<span data-ttu-id="69a9d-313">また、Blazor のテンプレート コンポーネントでは、`RenderFragment` または `RenderFragment<T>` 型のコンポーネント パラメーターを複数定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-313">A templated Blazor component can also define multiple component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="69a9d-314">`RenderFragment<T>` のパラメーターは、呼び出されたときに指定できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-314">The parameter for a `RenderFragment<T>` can be specified when it's invoked.</span></span> <span data-ttu-id="69a9d-315">コンポーネントのジェネリック型パラメーターを指定するには、Razor ディレクティブ `@typeparam` を使用します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-315">To specify a generic type parameter for a component, use the `@typeparam` Razor directive.</span></span>

<span data-ttu-id="69a9d-316">*SimpleListView.razor*</span><span class="sxs-lookup"><span data-stu-id="69a9d-316">*SimpleListView.razor*</span></span>

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

<span data-ttu-id="69a9d-317">テンプレート コンポーネントを使用する場合、テンプレート パラメーターは、パラメーターの名前と一致する子要素を使用して指定することができます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-317">When using a templated component, the template parameters can be specified using child elements that match the names of the parameters.</span></span> <span data-ttu-id="69a9d-318">要素として渡される `RenderFragment<T>` 型のコンポーネント引数には、`context` という名前の暗黙的なパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-318">Component arguments of type `RenderFragment<T>` passed as elements have an implicit parameter named `context`.</span></span> <span data-ttu-id="69a9d-319">この実装パラメーターの名前は、子要素の `Context` 属性を使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-319">You can change the name of this implement parameter using the `Context` attribute on the child element.</span></span> <span data-ttu-id="69a9d-320">任意のジェネリック型パラメーターを、型パラメーターの名前と一致する属性を使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-320">Any generic type parameters can be specified using an attribute that matches the name of the type parameter.</span></span> <span data-ttu-id="69a9d-321">可能な場合は、型パラメーターが推論されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-321">The type parameter will be inferred if possible:</span></span>

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

<span data-ttu-id="69a9d-322">このコンポーネントの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-322">The output of this component looks like this:</span></span>

```html
<h1>My list</h1>
<ul>
    <li><p>The message is: message1</p></li>
    <li><p>The message is: message2</p></li>
<ul>
```

## <a name="code-behind"></a><span data-ttu-id="69a9d-323">分離コード</span><span class="sxs-lookup"><span data-stu-id="69a9d-323">Code-behind</span></span>

<span data-ttu-id="69a9d-324">Blazor コンポーネントは通常、単一の *.razor* ファイルで作成されます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-324">A Blazor component is typically authored in a single *.razor* file.</span></span> <span data-ttu-id="69a9d-325">ただし、分離コード ファイルを使用して、コードとマークアップを分離することもできます。</span><span class="sxs-lookup"><span data-stu-id="69a9d-325">However, it's also possible to separate the code and markup using a code-behind file.</span></span> <span data-ttu-id="69a9d-326">コンポーネント ファイルを使用するには、コンポーネント ファイルのファイル名と一致し、 *.cs* 拡張子を追加した C# ファイルを追加します (*Counter.razor.cs*)。</span><span class="sxs-lookup"><span data-stu-id="69a9d-326">To use a component file, add a C# file that matches the file name of the component file but with a *.cs* extension added (*Counter.razor.cs*).</span></span> <span data-ttu-id="69a9d-327">コンポーネントの基本クラスを定義するには、C# ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="69a9d-327">Use the C# file to define a base class for the component.</span></span> <span data-ttu-id="69a9d-328">基本クラスには任意の名前を付けることができますが、コンポーネント クラスと同じ名前を付けて `Base` 拡張子を追加するのが一般的です (`CounterBase`)。</span><span class="sxs-lookup"><span data-stu-id="69a9d-328">You can name the base class anything you'd like, but it's common to name the class the same as the component class, but with a `Base` extension added (`CounterBase`).</span></span> <span data-ttu-id="69a9d-329">コンポーネント ベースのクラスも、`ComponentBase` から派生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-329">The component-based class must also derive from `ComponentBase`.</span></span> <span data-ttu-id="69a9d-330">次に、Razor コンポーネント ファイルで、`@inherits` ディレクティブを追加してコンポーネントの基本クラスを指定します (`@inherits CounterBase`)。</span><span class="sxs-lookup"><span data-stu-id="69a9d-330">Then, in the Razor component file, add the `@inherits` directive to specify the base class for the component (`@inherits CounterBase`).</span></span>

<span data-ttu-id="69a9d-331">*Counter.razor*</span><span class="sxs-lookup"><span data-stu-id="69a9d-331">*Counter.razor*</span></span>

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

<span data-ttu-id="69a9d-332">*Counter.razor.cs*</span><span class="sxs-lookup"><span data-stu-id="69a9d-332">*Counter.razor.cs*</span></span>

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

<span data-ttu-id="69a9d-333">基本クラスのコンポーネントのメンバーの可視性は、コンポーネント クラスから参照できるように `protected` または `public` である必要があります。</span><span class="sxs-lookup"><span data-stu-id="69a9d-333">The visibility of the component's members in the base class must be `protected` or `public` to be visible to the component class.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="69a9d-334">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="69a9d-334">Additional resources</span></span>

<span data-ttu-id="69a9d-335">上記は、Blazor コンポーネントのすべての側面を網羅するものではありません。</span><span class="sxs-lookup"><span data-stu-id="69a9d-335">The preceding isn't an exhaustive treatment of all aspects of Blazor components.</span></span> <span data-ttu-id="69a9d-336">[ASP.NET Core Razor コンポーネントの作成と使用](/aspnet/core/blazor/components)の方法について詳しくは、Blazor のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="69a9d-336">For more information on how to [Create and use ASP.NET Core Razor components](/aspnet/core/blazor/components), see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="69a9d-337">[前へ](app-startup.md)
>[次へ](pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="69a9d-337">[Previous](app-startup.md)
[Next](pages-routing-layouts.md)</span></span>
