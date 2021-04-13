---
title: ASP.NET Core への eShop の移行例
description: サンプルのオンライン ストア アプリを参照として使用して、既存の ASP.NET MVC アプリを ASP.NET Core に移行するためのチュートリアルです。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 498eb3b11c44381ff6d261b37caed15a2698b166
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605257"
---
# <a name="example-migration-of-eshop-to-aspnet-core"></a>ASP.NET Core への eShop の移行例

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

この章では、.NET Framework アプリを .NET Core に移行する方法について説明します。 この章では、ASP.NET 5.0 用に作成されたサンプルのオンライン ストア アプリについて確認します。 このアプリでは、本書で既に説明した多くの概念とツールが使用されます。 出発点となるアプリは [*eShopModernizing* GitHub リポジトリ](https://github.com/dotnet-architecture/eShopModernizing)にあります。 出発点となるアプリは複数あります。 この章では、*eShopLegacyMVCSolution* に焦点を当てます。

図 4-1 は、プロジェクトの初期バージョンを示しています。 これは、ごく標準的な ASP.NET MVC 5 アプリです。

![図 4-1](media/Figure4-1.png)

**図 4-1** *eShopModernizing* MVC サンプル プロジェクトの構造。

この章では、アップグレード手順の多くを手動で実行する方法について説明します。 または、[.NET Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)を使用して、プロジェクト ファイルの変換、ターゲット フレームワークの変更、NuGet パッケージの更新など、初期手順の多くを実行することもできます。

## <a name="run-apiport-to-identify-problematic-apis"></a>*ApiPort* を実行して問題のある API を特定する

移行準備の最初の手順は、*ApiPort* ツールを実行することです。 このツールでは、アプリが呼び出す .NET Framework API の数と、それに相当する .NET Standard または .NET Core の API の数を特定します。 サードパーティの依存関係ではなく独自のアプリのロジックを重視し、移植する必要のある `System.Web` の依存関係に注意してください。 ApiPort ツールは、前の[依存関係の把握と更新](understand-update-dependencies.md)に関する章で導入されました。

[*ApiPort* ツールをインストールおよび構成](../../standard/analyzers/portability-analyzer.md)したら、図 4-2 に示すように Visual Studio 内から分析を実行します。

![図 4-2](media/Figure4-2.png)

**図 4-2** Visual Studio でアセンブリの移植性を分析する。

図 4-3 に示すように、プロジェクトの *bin* フォルダーから Web プロジェクトのアセンブリを選択します。

![図 4-3](media/Figure4-3.png)

**図 4-3** プロジェクトの Web アセンブリを選択する。

ソリューションに複数のプロジェクトが含まれている場合は、すべてを選択できます。 *eShop* サンプルに含まれている MVC プロジェクトは 1 つだけです。

レポートが生成されたら、ファイルを開いて結果を確認します。 概要では、アプリが実行する .NET Framework 呼び出しのうち、互換性のあるバージョンを持つ呼び出しの割合が示されます。 図 4-4 は、*eShop* MVC プロジェクトの概要を示しています。

![図 4-4](media/Figure4-4.png)

**図 4-4** ApiPort の概要。

このアプリの場合、約 80% の .NET Framework の呼び出しに互換性があります。 20% の呼び出しは、移植プロセス中に対処する必要があります。 詳細を表示すると、互換性のないすべての呼び出しが `System.Web` に含まれていることがわかります。これは、想定された非互換性です。 `System.Web` の呼び出しへの依存関係は、後の手順でアプリのコントローラーと関連するクラスが移行されるときに対処されます。 図 4-5 は、ツールで検出された型の一部を示しています。

![図 4-5](media/Figure4-5.png)

**図 4-5** *ApiPort* の互換性のない型の詳細。

互換性のない型のほとんどは、`Controller` および ASP.NET Core に同等の属性を持つさまざまな関連属性を参照します。

## <a name="update-project-files-and-nuget-reference-syntax"></a>プロジェクト ファイルと NuGet 参照構文を更新する

次に、古い *.csproj* ファイル構造を、.NET Core で導入されたより新しくシンプルな構造に移行します。 その場合、NuGet 参照用の *packages.config* ファイルの使用が、プロジェクト ファイル内の `<PackageReference>` 要素の使用に移行されます。

元のプロジェクトの *eShopLegacyMVC.csproj* ファイルの長さは 418 行です。 図 4-6 は、プロジェクト ファイルのサンプルを示しています。 全体のサイズと複雑さを把握できるように、画像の右側にはファイル全体が縮小表示されています。

![図 4-6](media/Figure4-6.png)

**図 4-6** *eShopLegacyMVC.csproj* ファイルの構造。

既存の ASP.NET プロジェクト用の新しいプロジェクト ファイルを作成する一般的な方法としては、`dotnet new` または Visual Studio の **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を使用して新しい ASP.NET Core アプリを作成します。 次に、古いプロジェクトから新しいプロジェクトにファイルをコピーして、移行を完了できます。

図 4-7 に示すように、C# プロジェクト ファイルに加えて、NuGet の依存関係が個別の 45 行の *packages.config* ファイルに格納されます。

![図 4-7](media/Figure4-7.png)

**図 4-7** *packages.config* ファイル。

新しい *.csproj* ファイル形式にアップグレードした後で、Visual Studio を使用してクラス ライブラリ プロジェクト内の *packages.config* を移行できます。 ただし、この機能は ASP.NET プロジェクトでは使用できません。 [Visual Studio で *packages.config* を `<PackageReference>` に移行する方法](/nuget/consume-packages/migrate-packages-config-to-package-reference)を参照してください。 多数のプロジェクトを移行する場合は、[このコミュニティ ツール](https://github.com/MarkKharitonov/NuGetPCToPRMigrator)が役立ちます。

## <a name="create-new-aspnet-core-project"></a>新しい ASP.NET Core プロジェクトを作成する

新しい ASP.NET Core プロジェクトを既存のアプリのソリューションに追加して、ファイルを簡単に移動できるようにします。ほとんどの作業は Visual Studio の **ソリューション エクスプローラー** 内から実行できます。 Visual Studio で、アプリのソリューションを右クリックし、 **[新しいプロジェクトの追加]** を選択します。 **[ASP.NET Core Web アプリケーション]** を選択し、図 4-8 に示すように、新しいプロジェクトに名前を付けます。

![図 4-8](media/Figure4-8.png)

**図 4-8** 新しい ASP.NET Core Web アプリケーションを追加する。

次のダイアログでは、使用するテンプレートの選択を求められます。 **[空]** テンプレートを選択します。 また、ドロップダウンを **.Net Core** から **.NET Framework** に変更します。 図 4-9 に示すように、 **[ASP.NET Core 2.2]** を選択します。

![図 4-9](media/Figure4-9.png)

**図 4-9** .NET Framework と ASP.NET Core 2.2 をターゲットとする空のプロジェクト テンプレートを選択する。

### <a name="migrating-nuget-packages"></a>NuGet パッケージの移行

*packages.config* を `<PackageReference>` に移行するための組み込みの移行ツールは ASP.NET プロジェクトでは機能しないため、代わりにコミュニティ ツールを使用するか、手動で移行を実行することができます。 [私が使用したコミュニティ ツール](https://gist.github.com/tomkuijsten/2d75074d9a3c19c04ee8ea19a6289ddf)では、XSL ファイルを使用して形式を変換します。 これを使用するには、まず、新しく作成した ASP.NET Core プロジェクト フォルダーに *packages.config* ファイルをコピーします。 ファイルのバックアップを作成します。このスクリプトでは、スクリプトの実行場所にあるすべてのフォルダーから *packages.config* ファイルが削除されます。 次に、プロジェクト フォルダーから (または、必要に応じてソリューション全体に対して) 次のコマンドを実行します。

```powershell
iwr https://git.io/vdKaV -OutFile Convert-ToPackageReference.ps1
iwr https://git.io/vdKar -OutFile  Convert-ToPackageReference.xsl
./Convert-ToPackageReference.ps1 | Out-Null
```

最初の 2 つのコマンドは、ファイルをダウンロードしてローカルに配置します。 最後の行でスクリプトが実行されます。 実行後、新しいプロジェクトのビルドを試してください。 おそらく何らかのエラーが発生します。 これらを解決するには、一部の参照 (たとえば、`Microsoft.AspNet` パッケージと `System` パッケージのほとんど) を削除します。また、一部の `xmlns` 属性を削除しなければならない場合があります。

ほとんどの ASP.NET MVC アプリでは、Bootstrap や jQuery などの多くのクライアント側の依存関係が NuGet パッケージを使用してデプロイされていました。 ASP.NET Core では、NuGet パッケージはサーバー側の機能にのみ使用されます。 クライアント ファイルは、他の方法で管理する必要があります。 追加された `<PackageReference>` 要素のリストを確認し、次に示すクライアント ライブラリ用の要素をすべてメモして削除します。

- ブートストラップ
- jQuery
- jQuery.Validation
- Modernizr
- popper.js
- 対応

NuGet によってインストールされたこれらのパッケージ用の静的クライアント ファイルは、新しいプロジェクトの *wwwroot* フォルダーにコピーされ、その場所からホストされます。 これらのファイルがアプリで引き続き必要かどうか、およびこれらのファイルを引き続きホストする方法と、代わりにコンテンツ配信ネットワーク (CDN) を使用する方法のどちらが妥当かを検討してください。 これらのライブラリ バージョンは、[LibMan](/aspnet/core/client-side/libman/) や [npm](https://www.npmjs.com/) などのツールを使用してビルド時に管理できます。 図 4-10 は、変換ツールを使用してパッケージ参照を移行し、不要なパッケージを削除した後の完全な *eShopPorted.csproj* ファイルを示しています。

![図 4-10](media/Figure4-10.png)

**図 4-10** *eShopPorted.csproj* ファイル内のパッケージ参照。

`<PackageReference>` で `<Version>1.0.0.0</Version>` 要素を `Version=1.0.0.0` 属性にすることで、パッケージ参照をさらに圧縮できます。

### <a name="migrate-static-files"></a>静的ファイルを移行する

アプリが使用するすべての静的ファイル (サードパーティのスクリプトやフレームワークだけでなく、カスタム画像やスタイルシートも含む) を古いプロジェクトから新しいプロジェクトにコピーする必要があります。 ASP.NET MVC アプリでは、ファイルへのアクセスは通常、プロジェクト フォルダー内のファイルの場所に基づいて行われていました。 ASP.NET Core アプリでは、このような静的ファイルへのアクセスは、*wwwroot* フォルダー内のファイルの場所に基づいて行われます。 *eShop* プロジェクトの場合、静的ファイルは次のフォルダーにあります。

* *コンテンツ*
* *fonts*
* *イメージ*
* *Pics*
* *スクリプト*

前の手順で使用した **空** のプロジェクト テンプレートには、既定ではこのフォルダーが含まれていません。また、このフォルダーが動作するために必要なミドルウェアもありません。 これらを追加する必要があります。

プロジェクトのルートに *wwwroot* フォルダーを追加します。

バージョン 2.2.0 の `Microsoft.AspNetCore.StaticFiles` NuGet パッケージを追加します。

*Startup.cs* で、`Configure` メソッドに `app.UseStaticFiles()` の呼び出しを追加します。

```csharp
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseStaticFiles();

    // ...
}
```

ASP.NET MVC アプリから新しいプロジェクトの *wwwroot* フォルダーに *Content* フォルダーをコピーします。

アプリを実行し、その */Content/base.css* フォルダーに移動して、必要なパスから静的ファイルが正しく提供されていることを確認します。 静的ファイルが格納されている残りのフォルダーを新しいプロジェクトに続けてコピーします。 また、必要に応じて、プロジェクトのルートから *wwwroot* フォルダーに *favicon.ico* ファイルをコピーします。 図 4-11 は、これらのファイルとフォルダーがすべてコピーされた後の結果を示しています。

![図 4-11](media/Figure4-11.png)

**図 4-11** *wwwroot* フォルダーにコピーされた静的フォルダー。

### <a name="migrate-c-files"></a>C# ファイルを移行する

次に、アプリで使用される C# ファイルをコピーします。これには、標準の MVC フォルダーとそのコンテンツ (*Controllers*、*Models*、*ViewModel*、*Services* など) が含まれます。 多くの場合、これらのファイルにはいくつかの変更を加える必要があります。 一度に 1 つのフォルダー (またはサブフォルダー) をコピーしてコンパイルし、対処する必要のあるエラーを確認することをお勧めします。

*eShop* サンプルの場合、移行対象として最初に選択したフォルダーは、C# エンティティと Entity Framework クラスを含む *Models* フォルダーです。 このフォルダーのクラスは他のほとんどのクラスで使用されるので、これらのクラスがコピーされるまでは他のクラスが機能しません。 フォルダーをコピーしてビルドを実行した後で、見つからない名前空間 `System.Web.Hosting` に関連するエラー、`HostingEnvironment` に関連するアクセス、および `ConfigurationManager.AppSettings` への参照をコンパイラが検出しました。 このような問題の解決策として、必要なパス データを渡します。現時点では、問題のある行をコメント アウトし、各行に `TODO:` コメントを追加して追跡します。 5 つの行を変更すると、**タスク一覧** に 5 つの項目とプロジェクト ビルドが表示されます。

次に、1 つのクラスを含む *ViewModel* フォルダーがコピーされます。 これは簡単な処理であり、即座にビルドが実行されます。

*Services* フォルダーがコピーされます。 このフォルダーのクラスは、*Models* フォルダーの Entity Framework クラスに依存しているため、そのフォルダーの後にコピーする必要があります。 さいわいなことに、ビルド時にエラーは発生しません。

これで、残りは *Controllers* フォルダーとその 2 つの `Controller` クラスになりました。 このフォルダーを新しいプロジェクトにコピーしてビルドを実行すると、7 つのビルド エラーが発生します。 このうちの 4 つは `ViewBag` アクセスに関連するもので、次のようなエラーが報告されます。

> `Missing compiler required member 'Microsoft.CSharp.RuntimeBinder.CSharpArgumentInfo.Create'`

このエラーを解決するには、NuGet パッケージ参照を C# に追加します。

```xml
<PackageReference Include="Microsoft.CSharp" Version="4.7.0" />
```

残りの 3 つのエラーは、参照されていないアセンブリで定義されている型を示します。 具体的には次の型です。

- `HttpServerUtilityBase`
- `RouteValueDictionary`
- `HttpRequestBase`

エラーを 1 つずつ確認してみましょう。 最初のエラーは、既に存在しない `Controller` の `Server` プロパティを参照しようとすると発生します。 この操作の目的は、アプリ内の画像ファイルへのパスを取得することです。

```csharp
if (item != null)
{
    var webRoot = Server.MapPath("~/Pics"); // compiler error on this line
    var path = Path.Combine(webRoot, item.PictureFileName);

    string imageFileExtension = Path.GetExtension(item.PictureFileName);
    string mimetype = GetImageMimeTypeFromImageFileExtension(imageFileExtension);

    var buffer = System.IO.File.ReadAllBytes(path);

    return File(buffer, mimetype);
}
```

この問題には 2 つの解決策があります。 1 つ目は、機能をそのまま維持する方法です。 この場合、`Server.MapPath` を使用するのではなく、*wwwroot* 内の画像ファイルの場所を参照する修正されたパスを使用する必要があります。 または、このアクション メソッドの唯一の目的は静的な画像ファイルを返すことであるため、ビュー ファイル内のこのアクションへの参照を更新して静的ファイルを直接参照することができます。これにより、実行時のパフォーマンスが向上します。 このアクションの一部としては何の処理も行われないため、ファイルを直接提供しない理由はありません。 このアクションへのすべての参照を更新できない場合は、アクションを書き換えて、静的ファイルの場所へのリダイレクトを生成できます。

次の 2 つのエラーは、どちらも同じコード行の同じプライベート メソッドで発生します。

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    item.PictureUri = this.Url.RouteUrl(PicController.GetPicRouteName, new { catalogItemId = item.Id }, this.Request.Url.Scheme);
}
```

`this.Url` と `this.Request` の両方が原因でコンパイラ エラーが発生します。 このコードの使用方法によると、これは画像ファイルをレンダリングする `PicController` アクションへのリンクを作成することを目的としたコードです。 先ほど検出されたのと同じものが、*wwwroot* にある静的ファイルへの直接リンクに置き換えられる可能性があります。 現時点では、このコードをコメント アウトして、別の方法で Pics を参照する `TODO:` コメントを追加します。

注目すべき点は、このコードが表示されている `CatalogController` クラスで使用される基底クラス `Controller` が引き続き `System.Web.Mvc.Controller` を参照していることです。 ASP.NET Core を使用するようにこれを更新すると、修正が必要なエラーの数は間違いなく増加します。 最初に、`CatalogController` の `using` ステートメントのリストから `using System.Web.Mvc;` 行を削除します。 次に、NuGet パッケージ `Microsoft.AspNetCore.Mvc` を追加します。 最後に、`using Microsoft.AspNetCore.Mvc;` ステートメントを追加して、アプリをもう一度ビルドします。

今回は 16 個のエラーがあります。

- `Include` が有効な名前付き属性引数ではありません (2)
- `HttpStatusCodeResult` が見つかりません (3)
- `HttpNotFound` が存在しません (3)
- `SelectList` が見つかりません (8)

再び、これらのエラーを 1 つずつ確認してみましょう。 最初に、`using Microsoft.AspNetCore.Mvc.Rendering;` を追加して `SelectList` を修正できます。これで、半分のエラーが解消します。

`return HttpNotFound();` へのすべての参照を `return NotFound();` に置き換える必要があります。

`return new HttpStatusCodeResult(HttpStatusCode.BadRequest);` へのすべての参照を `return BadRequest();` に置き換える必要があります。

これで、次に示すようないくつかのアクション メソッドにおける `[Bind]` 属性を指定した `Include` の使用が残ります。

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind(Include = "Id,Name,Description,Price,PictureFileName,CatalogTypeId,CatalogBrandId,AvailableStock,RestockThreshold,MaxStockThreshold,OnReorder")] CatalogItem catalogItem)
{
```

上のコードでは、モデル バインドを `Include` 文字列に示されているプロパティに制限しています。 ASP.NET Core MVC では、`[Bind]` 属性は引き続き存在しますが、`Include =` 引数は必要ありません。 `[Bind]` 属性にプロパティのリストを直接渡します。

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind("Id,Name,Description,Price,PictureFileName,CatalogTypeId,CatalogBrandId,AvailableStock,RestockThreshold,MaxStockThreshold,OnReorder")] CatalogItem catalogItem)
{
```

これらの変更により、プロジェクトがもう一度コンパイルされます。 通常は、ドメイン モデルまたはデータ モデルの型に対して直接モデル バインドを使用するのではなく、コントローラーの入力に個別のモデルの型を使用することをお勧めします。

## <a name="migrate-views"></a>ビューを移行する

ビューに関連する ASP.NET Core MVC の 2 つの最大の機能は、[Razor Pages](/aspnet/core/razor-pages/) と[タグ ヘルパー](/aspnet/core/mvc/views/tag-helpers/built-in/)です。 最初の移行では、どちらの機能も使用しません。 ただし、移行後もアプリのサポートを継続する場合は、これらの機能を記憶に留めておいてください。 次の手順では、*Views* フォルダーを元のプロジェクトから新しいプロジェクトにコピーします。 ビルド後は次に示す 9 つのエラーが発生します。

- HttpContext が存在しません (2)
- スクリプトが存在しません (5)
- スタイルが存在しません (1)
- HtmlString が見つかりませんでした (1)

これらのエラーを調べると、ほとんどがメインの *_Layout.cshtml* で発生していることがわかります。エラーには、スクリプトとスタイルのタグのレンダリングに関連するものと、アプリをホストしているサーバーが最後に再起動されたときの表示に関連するものがあります。 次のコード リストは、 *_Layout.cshtml* ファイル内で問題が発生している部分を示しています。

```razor
// other lines omitted; only errors shown
@Styles.Render("~/Content/css")
@Scripts.Render("~/bundles/modernizr")

@{ var sessionInfo = new HtmlString($"{HttpContext.Current.Session["MachineName"]}, {HttpContext.Current.Session["SessionStartTime"]}");}

@Scripts.Render("~/bundles/jquery")
@Scripts.Render("~/bundles/bootstrap")
```

Modernizr への参照は削除できます。 Bootstrap と jQuery への参照は、適切なバージョンへの CDN リンクに置き換えることができます。

`@Styles.Render` 行を次のように置き換えます。

```html
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
```

最後の 2 つの `Scripts.Render` 行を次のように置き換えます。

```html
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
```

最後は、Bootstrap `<link>` の後に、アプリで使用するローカル スタイルの `<link>` 要素を追加します。 *eShop* の場合、結果は次のようになります。

```html
<link rel="stylesheet" href="~/Content/custom.css" />
<link rel="stylesheet" href="~/Content/base.css" />
<link rel="stylesheet" href="~/Content/Site.css" />
```

`<link>` 要素の表示順序を決定するには、元のアプリのレンダリングされた HTML を確認します。 または、*BundleConfig.cs* を確認します。*eShop* サンプルの場合、このファイルには、適切なシーケンスを示す次のコードが含まれています。

```csharp
bundles.Add(new StyleBundle("~/Content/css").Include(
          "~/Content/bootstrap.css",
          "~/Content/custom.css",
          "~/Content/base.css",
          "~/Content/site.css"));
```

再度ビルドすると、"*作成*" ビューと "*編集*" ビューにおける jQuery Validation の読み込みエラーがもう 1 つ発生します。 これを次のスクリプトに置き換えます。

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-validate/1.17.0/jquery.validate.min.js" integrity="sha512-O/nUTF5mdFkhEoQHFn9N5wmgYyW323JO6v8kr6ltSRKriZyTr/8417taVWeabVS4iONGk2V444QD0P2cwhuTkg==" crossorigin="anonymous"></script>
```

ビューで最後に修正するのは、アプリが実行されている時間とマシンを表示する `Session` への参照です。 このデータを `Startup` で静的変数として収集し、レイアウト ページに変数を表示できます。 次のプロパティを *Startup.cs* に追加します。

```csharp
public static DateTime StartTime { get; } = DateTime.UtcNow;
public static string MachineName { get; } = Environment.MachineName;
```

次に、レイアウトのフッターの内容を次のコードに置き換えます。

```razor
<section class="col-sm-6">
    <img class="esh-app-footer-text hidden-xs" src="~/images/main_footer_text.png" width="335" height="26" alt="footer text image" />
    <br />
<small>@eShopPorted.Startup.MachineName - @eShopPorted.Startup.StartTime.ToString() UTC</small>
</section>
```

この時点で、再度アプリがビルドされ、正常に完了します。 ただし、それを実行しようとすると *Hello World!* が中断します。 これは、**空** の ASP.NET Core テンプレートが要求に応じてそのプログラムを表示するようにのみ構成されているためです。 次のセクションでは、ASP.NET Core MVC を使用するようにアプリを構成して移行を完了します。これには、依存関係の挿入や構成が含まれます。 準備が整ったら、アプリを実行する必要があります。 その後で、以前に作成された `TODO:` タスクを修正します。

## <a name="migrate-app-startup-components"></a>アプリのスタートアップ コンポーネントを移行する

最後の移行手順では、*Global.asax* からアプリのスタートアップ タスクを実行し、そのアプリが呼び出すクラスを ASP.NET Core のクラスに移行します。 これらのタスクには、MVC 自体の構成、依存関係の挿入の設定、新しい構成システムの操作が含まれます。 ASP.NET Core では、これらのタスクは *Startup.cs* ファイルで処理されます。

### <a name="configure-mvc"></a>MVC を構成する

元の ASP.NET MVC アプリでは、*Global.asax* の `Application_Start` に次のコードが含まれています。このコードはアプリの起動時に実行されます。

```csharp
protected void Application_Start()
{
    container = RegisterContainer();
    AreaRegistration.RegisterAllAreas();
    FilterConfig.RegisterGlobalFilters(GlobalFilters.Filters);
    RouteConfig.RegisterRoutes(RouteTable.Routes);
    BundleConfig.RegisterBundles(BundleTable.Bundles);
    ConfigDataBase();
}
```

これらを 1 行ずつ確認すると、`RegisterContainer` メソッドは依存関係の挿入を設定します。これは以下に示すように移植されます。 次の 3 行は、MVC のさまざまなパーツ (区分、フィルター、ルート) を構成します。 バンドルは、移植されたアプリ内の静的ファイルに置き換えられます。 最後の行は、アプリのデータ アクセスを設定します。これについては後述します。

このアプリは実際には区分を使用していないため、区分登録の呼び出しを移行するために必要な作業はありません。 アプリで区分を移行する必要がある場合は、[ASP.NET Core における区分の構成方法がドキュメントで指定されています](/aspnet/core/mvc/controllers/areas)。

グローバル フィルターの登録のための呼び出しでは、アプリの *App_Start* フォルダー内の `FilterConfig` クラスでヘルパーが起動されます。

```csharp
public static void RegisterGlobalFilters(GlobalFilterCollection filters)
{
    filters.Add(new HandleErrorAttribute());
}
```

アプリに追加される属性は、ASP.NET MVC フィルター `HandleErrorAttribute` のみです。 このフィルターにより、要求の一部として例外が発生したときに、例外の詳細ではなく既定のアクションとビューが表示されます。 ASP.NET Core では、この同じ機能が `UseExceptionHandler` ミドルウェアによって実行されます。 詳細なエラー メッセージは、既定では有効になっていません。 `UseDeveloperExceptionPage` ミドルウェアを使用して構成する必要があります。 元のアプリと一致するようにこの動作を構成するには、*Startup.cs* の `Configure` メソッドの先頭に次のコードを追加する必要があります。

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
    }
    // ...
}
```

これは、eShop アプリで使用される唯一のフィルターを処理します。ここでは、組み込みのミドルウェアを使用して実行されました。 グローバル フィルターをアプリで構成する必要がある場合は、MVC が `ConfigureServices` メソッドで追加されるときにこの処理が行われます。これについては、本章で後述します。

移行が必要な MVC 関連のロジックの最後の部分は、アプリの既定のルートです。 `RouteConfig.RegisterRoutes(RouteTable.Routes)` の呼び出しにより、MVC ルート テーブルが `RegisterRoutes` ヘルパー メソッドに渡されます。このメソッドでは、アプリの起動時に次のコードが実行されます。

```csharp
public static void RegisterRoutes(RouteCollection routes)
{
    routes.MapMvcAttributeRoutes();
    routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

    routes.MapRoute(
        name: "Default",
        url: "{controller}/{action}/{id}",
        defaults: new { controller = "Catalog", action = "Index", id = UrlParameter.Optional }
    );
}
```

このコードを 1 行ずつ確認すると、最初の行では属性ルートのサポートが設定されます。 これは ASP.NET Core に組み込まれているため、個別に構成する必要はありません。 同様に、 *{resource}.axd* ファイルは ASP.NET Core では使用されないため、このようなルートを無視する必要はありません。 `MapRoute` メソッドは、一般的な `{controller}/{action}/{id}` ルート テンプレートを使用する MVC の既定値を構成します。 また、`CatalogController` が使用される既定のコントローラー、`Index` メソッドが既定のアクションになるように、このテンプレートの既定値も指定します。 大規模なアプリには、追加のルートを設定するために `MapRoute` の呼び出しが多く含まれていることがよくあります。

ASP.NET Core MVC では、[従来のルーティングと属性ルーティング](/aspnet/core/mvc/controllers/routing?preserve-view=true&view=aspnetcore-2.2)がサポートされます。 従来のルーティングは、前述の `RegisterRoutes` メソッドでルート テーブルを構成する方法に似ています。 既定のルート (*eShop* アプリで使用されるものなど) を使用して従来のルーティングを設定するには、*Startup.cs* の `Configure` メソッドの末尾に次のコードを追加します。

```csharp
app.UseMvc(routes =>
{
   routes.MapRoute("default", "{controller=Catalog}/{action=Index}/{id?}");
});
```

> [!NOTE]
> ASP.NET Core 3.0 以降では、これがエンドポイントを使用するように変更されます。 ASP.NET Core 2.2 への最初の移植では、これが従来のルートのマッピングに適した構文です。

これらの変更が適用されると、`Configure` メソッドはほぼ完了です。 *Hello World!* を出力する元のテンプレートの `app.Run` メソッド は削除する必要があります。 この時点で、メソッドは次のようになります。

```csharp
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }
    else
    {
        app.UseExceptionHandler("/Home/Error");
    }

    app.UseStaticFiles();

    app.UseMvc(routes =>
    {
        routes.MapRoute("default", "{controller=Catalog}/{action=Index}/{id?}");
    });
}
```

次に、MVC サービスを構成し、続いてアプリによる依存関係の挿入 (DI) のサポートを指定します。 ここまでは、*eShopPorted* プロジェクトの `ConfigureServices` メソッドは空のままです。 ここで読み込みを開始します。

まず、ASP.NET Core MVC を適切に動作させるために、次のように追加する必要があります。

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
}
```

上のコードは、MVC の機能を使用するために必要な最小限の構成です。 この呼び出しから構成できる追加の機能は多数ありますが、アプリのビルドにはこれで十分です。 これを実行すると、既定の要求が適切にルーティングされるようになりましたが、DI をまだ構成していないため、`CatalogController` をアクティブ化する際にエラーが発生します。これは、`ICatalogService` 型の実装がまだ指定されていないためです。 MVC の追加の構成については後述します。 ここでは、アプリの依存関係の挿入を移行してみましょう。

#### <a name="migrate-dependency-injection-configuration"></a>依存関係の挿入の構成を移行する

元のアプリの *Global.asax* ファイルでは、アプリの起動時に呼び出される次のメソッドを定義します。

```csharp
protected IContainer RegisterContainer()
{
  var builder = new ContainerBuilder();

  builder.RegisterControllers(typeof(MvcApplication).Assembly);

  var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
  builder.RegisterModule(new ApplicationModule(mockData));

  var container = builder.Build();
  DependencyResolver.SetResolver(new AutofacDependencyResolver(container));

  return container;
}
```

このコードは、[Autofac](https://autofac.org/) コンテナーを構成し、構成設定を読み取って、実際のデータとモック データのどちらを使用する必要があるかを判断し、この設定を (アプリの */Modules* ディレクトリにある) Autofac モジュールに渡します。 さいわいなことに、Autofac では .NET Core がサポートされるので、モジュールを直接移行できます。 フォルダーを新しいプロジェクトにコピーし、クラスの名前空間を更新して、コンパイルする必要があります。

ASP.NET Core には依存関係の挿入のサポートが組み込まれていますが、必要に応じて、Autofac などのサードパーティのコンテナーを簡単に関連付けることができます。 この場合、アプリは Autofac を使用するように既に構成されているので、その使用を維持することが最も簡単な解決策です。 そのためには、`ConfigureServices` メソッド シグネチャを変更して `IServiceProvider` を返す必要があります。また、Autofac コンテナー インスタンスを構成してメソッドから返す必要があります。

**注:** .NET Core 3.0 以降では、サードパーティの DI コンテナーを統合するためのプロセスが変更されました。

Autofac の構成の一部では、`builder.Populate(services)` を呼び出す必要があります。 この拡張機能は、`Autofac.Extensions.DependencyInjection` NuGet パッケージに含まれています。このパッケージは、コードをコンパイルする前にインストールする必要があります。

Autofac コンテナーを構成するために `ConfigureServices` を変更した後、新しいメソッドは次のようになります。

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    services.AddMvc();

    // Create Autofac container builder
    var builder = new ContainerBuilder();
    builder.Populate(services);
    bool useMockData = true; // TODO: read from config
    builder.RegisterModule(new ApplicationModule(useMockData));

    ILifetimeScope container = builder.Build();

    return new AutofacServiceProvider(container);
}
```

ここでは、`useMockData` は `true` に設定されています。 この設定はすぐに構成から読み取られます。 図 4-12 に示すように、この時点でアプリがコンパイルされ、実行時に正常に読み込まれます。

![図 4-12](media/Figure4-12.png)

**図 4-12** 移植された *eShop* アプリ (モック データを使用してローカルで実行)。

#### <a name="migrate-app-settings"></a>アプリの設定を移行する

ASP.NET Core は新しい [構成システム](/aspnet/core/fundamentals/configuration/?preserve-view=true&view=aspnetcore-2.2)を使用します。既定では、*appsettings.json* ファイルが活用されます。 *Program.cs* の `CreateDefaultBuilder` を使用して、既定の構成がアプリで既に設定されています。 構成にアクセスするには、クラスのコンストラクターで構成を要求する必要があります。 `Startup` クラスは例外ではありません。 `Startup` の構成と残りのアプリへのアクセスを開始するには、そのコンストラクターから `IConfiguration` のインスタンスを要求します。

```csharp
public Startup(IConfiguration configuration)
{
    Configuration = configuration;
}

public IConfiguration Configuration { get; }
```

元のアプリでは、`ConfigurationManager.AppSettings` を使用してその設定を参照していました。 この条件のすべての参照のクイック検索を実行すると、新しいアプリに必要な一連の設定が生成されます。 生成されるのは次の 2 つだけです。

- `UseMockData`
- `UseCustomizationData`

アプリの構成が複雑な場合 (特にカスタム構成セクションを使用している場合) は、オブジェクトを作成して、アプリの構成のさまざまな部分にバインドすることをお勧めします。 [オプション パターン](../../core/extensions/options.md)を使用してこれらの型にアクセスできます。 ただし、参照先のドキュメントで示されているように、このパターンを `ConfigureServices` で使用することはできません。 代わりに、移植されたアプリは `UseMockData` 構成値を直接参照します。

まず、移植されたアプリの `appsettings.json` ファイルを変更して、ルートに 2 つの設定を追加します。

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "AllowedHosts": "*",
  "UseMockData": "true",
  "UseCustomizationData" :  "true"
}
```

次に、`Configuration` プロパティから `UseMockData` 設定 (以前に値を `true` に設定) にアクセスするように `ConfigureServices` を変更します。

```csharp
  bool useMockData = Configuration.GetValue<bool>("UseMockData");
```

この時点で、構成から設定がプルされます。 もう 1 つの設定である `UseCustomizationData` は `CatalogDBInitializer` クラスで使用されます。 このクラスを最初に移植したときに、`ConfigurationManager.AppSettings["UseCustomizationData"]` へのアクセスをコメント アウトしています。 次に、ASP.NET Core 構成を使用するように変更します。 `CatalogDBInitializer` のコンストラクターを次のように変更します。

```csharp
  // add using Microsoft.Extensions.Configuration
  public CatalogDBInitializer(CatalogItemHiLoGenerator indexGenerator,
      IConfiguration configuration)
  {
      this.indexGenerator = indexGenerator;
      useCustomizationData = configuration.GetValue<bool>("UseCustomizationData");
  }
```

新しい `IConfiguration` 型を使用するには、Web アプリ内の構成へのすべてのアクセスをこの方法で変更する必要があります。 .NET Framework 構成へのアクセスを必要とする依存関係では、Web プロジェクトに追加された *app.config* ファイルにこのような設定を含めることができます。 依存プロジェクトは、`ConfigurationManager` を使用して設定にアクセスできます。また、この方法を既に使用している場合、変更は不要です。 ただし、ASP.NET Core アプリは独自の実行可能ファイルとして実行されるため、*web.config* ではなく *app.config* を参照します。レガシ アプリの *web.config* ファイルから ASP.NET Core アプリ内の新しい *app.config* ファイルに設定を移行することで、`ConfigurationManager` を使用して設定にアクセスするコンポーネントは引き続き適切に機能します。

アプリの移行はほぼ完了です。 残りのタスクはデータ アクセスの構成のみです。
  
## <a name="data-access-considerations"></a>データ アクセスに関する考慮事項

.NET Framework で実行されている ASP.NET Core アプリは Entity Framework (EF) を引き続き活用できます。 増分移行を実行する場合は、EF Core を使用するためにデータ アクセス移植する前に、アプリが EF 6 を使用するように設定することをお勧めします。 これにより、別のブロックの移行作業が開始される前に、アプリの移行に関する問題を特定して対処することができます。

この作業は Autofac の `ApplicationModule` で実行されたため、eShop サンプルの移行で EF 6 を構成する場合、特別な作業は必要ありません。 唯一の問題は、現時点で `CatalogDBContext` クラスが *web.config* から接続文字列の読み取りを試行することです。この問題に対処するために、接続の詳細を *appsettings.json* に追加する必要があります。 次に、接続文字列の作成時に、その文字列を `CatalogDBContext` に渡す必要があります。

*appsettings.json* を更新して、接続文字列を含めます。 ファイル全体は次のようになります。

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=eShopPorted;Trusted_Connection=True;MultipleActiveResultSets=true"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "AllowedHosts": "*",
  "UseMockData": "false",
  "UseCustomizationData": "true"
}
```

`DbContext` の作成時に、接続文字列をコンストラクターに渡す必要があります。 インスタンスは Autofac で作成されるため、`ApplicationModule` で変更を行う必要があります。 モジュールを変更し、`connectionString` をコンストラクターに取り込んでフィールドに割り当てます。 次に、`CatalogDBContext` の登録を変更して、接続文字列をパラメーターとして追加します。

```csharp
builder.RegisterType<CatalogDBContext>()
  .WithParameter("connectionString", _connectionString)
  .InstancePerLifetimeScope();
```

このパラメーターは、`CatalogDBContext` 自体の新しいコンストラクターのオーバーロードにも追加する必要があります。

```csharp
public CatalogDBContext(string connectionString) : base(connectionString)
{
}
```

最後に、`ConfigureServices` が `Config` から接続文字列を読み取り、そのインスタンスを作成するときに `ApplicationModule` に渡す必要があります。

```csharp
bool useMockData = Configuration.GetValue<bool>("UseMockData");
string connectionString = Configuration.GetConnectionString("DefaultConnection");
builder.RegisterModule(new ApplicationModule(useMockData, connectionString));
```

このコードにより、アプリは以前と同じように実行され、`UseMockData` が `false` のときに SQL Server データベースに接続します。

この時点で、アプリを運用環境にデプロイして実行できます。アプリは ASP.NET Core に変換されますが、引き続き .NET Framework と EF 6 で実行されます。 必要に応じて、.NET Core と Entity Framework Core で実行するためにアプリを移行できます。これにより、前の章で説明した追加の利点が得られます。 Entity Framework については、[このドキュメントで EF Core と EF 6 を比較](/ef/efcore-and-ef6/)しています。また、個別のさまざまな機能がサポートされるライブラリを示す表も含まれています。

### <a name="migrate-to-entity-framework-core"></a>Entity Framework Core に移行する

EF Core への移行を決定したと仮定すると、特に元のアプリでコード ベース モデルのアプローチを使用していた場合は、手順が非常に簡単になります。 [EF 6 から EF Core への移植の準備](/ef/efcore-and-ef6/porting/)の際、移植先のバージョンの EF Core で機能が使用可能かどうかを確認します。 [EDMX ベース モデルからの移植](/ef/efcore-and-ef6/porting/port-edmx)および[コード ベース モデルからの移植](/ef/efcore-and-ef6/porting/port-code)に関するドキュメントを確認してください。

EF Core 2.2 にアップグレードする場合の基本的な手順として、適切な NuGet パッケージを追加し、名前空間を更新します。 次に、接続文字列を `DbContext` 型に渡す方法と、依存関係の挿入用にそれらを関連付ける方法を調整します。

EF Core は、パッケージ参照としてプロジェクトに追加されます。

```xml
<PackageReference Include="Microsoft.EntityFrameworkCore" Version="2.2.6" />
```

EF 6 への参照は削除されます。

```xml
<PackageReference Include="EntityFramework" Version="6.2.0" />
```

コンパイラは、`CatalogDBContext` と `CatalogDBInitializer` でエラーを報告します。 `CatalogDbContext` では、古い名前空間を削除して `Microsoft.EntityFrameworkCore` に置き換える必要があります。 そのコンストラクターは削除できます。 `DbModelBuilder` は `ModelBuilder` に置き換える必要があります。 型を構成するためのヘルパー メソッドは、`IEntityTypeConfiguration<T>` を実装する別のクラスに移動されます。 これで、`CatalogDBContext` クラスの `OnModelCreating` メソッドは次のようになります。

```csharp
protected override void OnModelCreating(ModelBuilder builder)
{
    builder.ApplyConfigurationsFromAssembly(Assembly.GetExecutingAssembly());

    base.OnModelCreating(builder);
}
```

関連するその他の変更点は次のとおりです。

- `HasDatabaseGeneratedOption(DatabaseGeneratedOption.None)` が `ValueGeneratedNever()` に置き換えられる
- `HasRequired<T>` が `HasOne<T>` に置き換えられる
- `Microsoft.EntityFrameworkCore.Relational` パッケージがインストールされる
- コンストラクターを `CatalogDBContext` に追加し、`DbContextOptions` を取得して基底コンストラクターに渡す

`CatalogType` の構成クラスの例を次に示します。

```csharp
using Microsoft.EntityFrameworkCore;
using Microsoft.EntityFrameworkCore.Metadata.Builders;

namespace eShopPorted.Models.Config
{
    public class CatalogTypeConfig : IEntityTypeConfiguration<CatalogType>
    {
        public void Configure(EntityTypeBuilder<CatalogType> builder)
        {
            builder.ToTable(nameof(CatalogType));

            builder.HasKey(ci => ci.Id);

            builder.Property(ci => ci.Id)
               .IsRequired();

            builder.Property(cb => cb.Type)
                .IsRequired()
                .HasMaxLength(100);
        }
    }
}
```

`CatalogDBInitializer` とその基底クラス `CreateDatabaseIfNotExists<T>` には、EF Core との互換性がありません。 このクラスの目的は、データベースを作成してシードすることです。 EF Core では、次のメソッドを使用して、[`DbContext` の関連データベースが作成および削除](/ef/core/managing-schemas/ensure-created)されます。

```csharp
dbContext.Database.EnsureDeleted();
dbContext.Database.EnsureCreated();
```

EF Core におけるデータのシードは、手動のスクリプトを使用するか、型構成の一部として行うことができます。 他のエンティティ プロパティと共に、`builder.HasData()` を使用して、`IEntityTypeConfiguration` クラスでシード データを構成できます。 元のアプリは、*Setup* ディレクトリ内の CSV ファイルからシード データを読み込みました。 項目数が少ない場合は、代わりにこれらのデータ レコードをエンティティ構成の一部として追加できます。 この方法は、変更頻度の低いテーブル内のデータの検索に適しています。 次のコードを `CatalogTypeConfig` の `Configure` メソッドに追加すると、データベースの作成時に、関連付けられている行が確実に表示されるようになります。

```csharp
builder.HasData(
    new CatalogType { Id = 1, Type = "Mug" },
    new CatalogType { Id = 2, Type = "T-Shirt" },
    new CatalogType { Id = 3, Type = "Sheet" },
    new CatalogType { Id = 4, Type = "USB Memory Stick" }
);
```

初期のアプリには `CatalogBrand` と `CatalogType` のデータを含む `PreconfiguredData` クラスが含まれているため、このメソッドを使用すると、`HasData` の呼び出しが次のように少なくなります。

```csharp
builder.HasData(
    PreconfiguredData.GetPreconfiguredCatalogBrands()
);
```

また、`CatalogItem` データを `PreconfiguredData` からプルすることもできます。関連付けられている画像がソース管理で保持されると仮定すると、これはアプリが機能するために必要な最後のテーブルです。 `CatalogDBInitializer` クラスは、そのクラスへの参照と共に削除できます。 `CatalogItemHiLoGenerator` クラスと `Infrastructure` ディレクトリ内の SQL ファイルも、それらへの参照 (`CatalogService`、`ApplicationModule` 内) と共に削除されます。

`CatalogItem` の特殊なキー ジェネレーター クラスを削除することで、このコードは `CatalogItemConfig` から削除されました。

```csharp
builder.Property(ci => ci.Id)
    .ValueGeneratedNever()
    .IsRequired();
```

このような変更により、ASP.NET Core アプリはビルドされますが、まだ EF Core を使用できません。依存関係の挿入用の構成をアプリで実行する必要があります。 EF Core では、`ConfigureServices` でアプリを構成するのが最も簡単な方法です。

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    bool useMockData = Configuration.GetValue<bool>("UseMockData");
    if (!useMockData)
    {
        string connectionString = Configuration.GetConnectionString("DefaultConnection");

        services.AddDbContext<CatalogDBContext>(options =>
            options.UseSqlServer(connectionString)
        );
    }

    // Create Autofac container builder
    var builder = new ContainerBuilder();
    builder.Populate(services);
    builder.RegisterModule(new ApplicationModule(useMockData));

    ILifetimeScope container = builder.Build();

    return new AutofacServiceProvider(container);
}
```

Autofac の `ApplicationModule` の最終バージョンでは、アプリがモック データを使用するように構成されているかどうかに応じて、1 つの型だけを構成します。

```csharp
public class ApplicationModule : Module
{
    private bool _useMockData;

    public ApplicationModule(bool useMockData)
    {
        _useMockData = useMockData;
    }

    protected override void Load(ContainerBuilder builder)
    {
        if (_useMockData)
        {
            builder.RegisterType<CatalogServiceMock>()
                .As<ICatalogService>()
                .SingleInstance();
        }
        else
        {
            builder.RegisterType<CatalogService>()
                .As<ICatalogService>()
                .InstancePerLifetimeScope();
        }
    }
}
```

移植されたアプリは実行されますが、モック以外のデータを使用するように構成されている場合はデータが表示されません。 `HasData` によって追加されたシード データは、移行が適用されるときにのみ挿入されます。 ソース アプリでは移行を使用していませんでしたが、使用していた場合でも、現状のような移行は行われません。 新しい移行スクリプトで作業を開始するのが最適な方法です。 そのためには、`Microsoft.EntityFrameworkCore.Design` のパッケージ参照を追加し、プロジェクト ルートでターミナル ウィンドウを開きます。 次に、次のコマンドを実行します。

```dotnetcli
dotnet ef migrations add Initial
```

既存の *eShopPorted* データベースが存在する場合は削除して、次のコードを実行します。

```dotnetcli
dotnet ef database update
```

これにより、データベースが作成され、シードされます。 これで実行の準備が整いました。ただし、対処が必要となる小さな更新がいくつか残されています。

## <a name="fix-all-todo-tasks"></a>すべての TODO タスクを修正する

移植されたアプリをこの時点で実行すると、ページに画像が表示されないことがわかります。 これは、`CatalogItem` の `PictureUri` プロパティが設定されていないためです。 Visual Studio の **タスク一覧** を使用して作成した `TODO` 項目の一覧を確認すると、残っているのは "Reference pic from wwwroot" というメモの付いた、`CatalogController` 内の項目のみです。 対象のコードは次のとおりです。

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    //TODO: Reference pic from wwwroot
    //item.PictureUri = this.Url.RouteUrl(PicController.GetPicRouteName, new { catalogItemId = item.Id }, this.Request.Url.Scheme);
}
```

最も簡単な修正方法は、サイトのパブリック ディレクトリである *wwwroot/Pics* 内の公開されている画像ファイルを参照することです。 このタスクを実行するには、メソッドを次のコードに置き換えます。

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    item.PictureUri = $"/Pics/{item.Id}.png";
}
```

この変更により、アプリを実行すると、画像が以前と同じように表示されることがわかります。

## <a name="additional-mvc-customizations"></a>MVC の追加のカスタマイズ

*eShopLegacyMVC* アプリは非常にシンプルなので、既定の MVC の動作に関する構成作業はあまり多くはありません。 ただし、追加の MVC コンポーネント (CORS、フィルター、ルート制約など) を構成する必要がある場合、通常はこの情報を `Startup.ConfigureServices` で提供します。ここでは `UseMvc` が呼び出されます。 たとえば、次のコード リストでは、[CORS](/aspnet/core/security/cors?preserve-view=true&view=aspnetcore-2.2) を構成し、グローバル アクション フィルターを設定します。

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddCors(options =>
    {
        options.AddPolicy(MyAllowSpecificOrigins,
            builder =>
                builder.WithOrigins("http://example.com", "http://www.contoso.com")
                    .AllowAnyHeader()
                    .AllowAnyMethod());
    });

    services.AddMvc(options =>
    {
      options.Filters.Add(new SampleGlobalActionFilter());
    }).SetCompatibilityVersion(CompatibilityVersion.Version_2_2);
}
```

> [!Note]
> CORS の構成を完了するには、`app.UseCors()` を `Configure` で呼び出す必要もあります。

[カスタム モデル バインダー](/aspnet/core/mvc/advanced/custom-model-binding?preserve-view=true&view=aspnetcore-2.2)やフォーマッタの追加など、その他の高度なシナリオについては、ASP.NET Core の詳細なドキュメントを参照してください。これらは通常、個々のコントローラーやアクション単位で、または前述のコード リストに示されているのと同じオプションを使用してグローバルに適用できます。

## <a name="other-dependencies"></a>その他の依存関係

WCF クライアントの型やトレース コードなど、レガシ構成モデルに依存していた .NET Framework 機能を使用する依存関係は、移植時に変更する必要があります。 このような型によって構成情報を直接取り込むのではなく、コードで構成する必要があります。 たとえば、ASP.NET アプリの *web.config* で `basicHttpBinding` を使用するように構成された WCF サービスへの接続は、次のコードを使用してプログラムで構成できます。

```csharp
var binding = new BasicHttpBinding();
binding.MaxReceivedMessageSize = 2_000_000;

var endpointAddress = new EndpointAddress("http://localhost:9200/ExampleService");

var myClient = new MyServiceClient(binding, endpointAddress);
```

WCF クライアントおよびその他の .NET Framework 型の設定は、設定の構成ファイルに依存するのではなく、コードで指定する必要があります。 この方法で構成すると、これらの型は ASP.NET Core 2.2 アプリで引き続き機能します。

## <a name="references"></a>リファレンス

- [eShopModernizing GitHub リポジトリ](https://github.com/dotnet-architecture/eShopModernizing)
- [.NET Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)
- [Your API and ViewModels Should Not Reference Domain Models (API と ViewModels でドメイン モデルを参照できない)](https://ardalis.com/your-api-and-view-models-should-not-reference-domain-models/)
- [開発者例外ページ ミドルウェア](/aspnet/core/fundamentals/error-handling#developer-exception-page)
- [EF Core の HasData の詳細情報](/archive/msdn-magazine/2018/august/data-points-deep-dive-into-ef-core-hasdata-seeding)

>[!div class="step-by-step"]
>[前へ](more-migration-scenarios.md)
>[次へ](deployment-scenarios.md)
