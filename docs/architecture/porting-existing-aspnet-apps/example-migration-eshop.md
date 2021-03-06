---
title: EShop から ASP.NET Core への移行の例
description: サンプルオンラインストアアプリを参照として使用して、既存の ASP.NET MVC アプリを ASP.NET Core に移行するチュートリアルです。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 83110909632e4eb433e1fabaedf3490ce594e12e
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401387"
---
# <a name="example-migration-of-eshop-to-aspnet-core"></a>EShop から ASP.NET Core への移行の例

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

この章では、.NET Framework アプリを .NET Core に移行する方法について説明します。 この章では、ASP.NET 5.0 用に作成されたオンラインストアアプリのサンプルを調べます。 このアプリでは、このブックで前述した概念とツールの多くを使用します。 [ *EShopModernizing* GitHub リポジトリ](https://github.com/dotnet-architecture/eShopModernizing)に開始ポイントアプリがあります。 いくつかの異なる開始ポイントアプリがあります。 この章では、 *eShopLegacyMVCSolution* を中心に説明します。

プロジェクトの初期バージョンは、図4-1 に示されています。 これは、非常に標準的な ASP.NET MVC 5 アプリです。

![図4-1](media/Figure4-1.png)

**図 4-1** *EShopModernizing* MVC サンプルプロジェクトの構造。

この章では、アップグレードの手順の多くを手動で実行する方法について説明します。 または、 [.Net Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant) を使用して、プロジェクトファイルの変換、ターゲットフレームワークの変更、NuGet パッケージの更新など、初期手順の多くを実行することもできます。

## <a name="run-apiport-to-identify-problematic-apis"></a>*Apiport* を実行して問題のある api を特定する

移行を準備するための最初の手順は、 *Apiport* ツールを実行することです。 このツールでは、アプリが呼び出す .NET Framework Api の数と、それに相当する .NET Standard または .NET Core の数が識別されます。 主に、サードパーティの依存関係ではなく、独自のアプリのロジックに重点を置いて、移植する必要がある依存関係に注意して `System.Web` ください。 ApiPort ツールは、 [依存関係の理解と更新](/understand-update-dependencies.md)に関する最後の章で導入されました。

[ *Apiport* ツールをインストールして構成](../../standard/analyzers/portability-analyzer.md)した後、図4-2 に示すように、Visual Studio 内から分析を実行します。

![図4-2](media/Figure4-2.png)

**図 4-2** Visual Studio でアセンブリの移植性を分析します。

図4-3 に示すように、プロジェクトの *bin* フォルダーから web プロジェクトのアセンブリを選択します。

![図4-3](media/Figure4-3.png)

**図 4-3** プロジェクトの web アセンブリを選択します。

ソリューションに複数のプロジェクトが含まれている場合は、すべてを選択できます。 *EShop* サンプルには、1つの MVC プロジェクトだけが含まれています。

レポートが生成されたら、ファイルを開き、結果を確認します。 概要では、アプリに対する互換性のあるバージョンの .NET Framework 呼び出しの割合が大まかに示されます。 図4-4 は、 *eShop* MVC プロジェクトの概要を示しています。

![図4-4](media/Figure4-4.png)

**図 4-4** ApiPort の概要。

このアプリでは、.NET Framework の呼び出しの約80% に互換性があります。 呼び出しの20% は、移植プロセス中に対処する必要があります。 詳細を表示すると、互換性のないすべての呼び出しがの一部であることがわかり `System.Web` ます。これは、予期しない非互換性です。 呼び出しの依存関係は、 `System.Web` 後の手順でアプリのコントローラーと関連クラスが移行されるときに解決されます。 図4-5 に、ツールによって検出された特定の型の一部を示します。

![図4-5](media/Figure4-5.png)

**図 4-5.** *Apiport* に互換性のない型の詳細があります。

互換性のない型のほとんどは、 `Controller` および ASP.NET Core に相当する関連属性を参照します。

## <a name="update-project-files-and-nuget-reference-syntax"></a>プロジェクトファイルと NuGet 参照構文の更新

次に、古い *.csproj* ファイル構造から、.net Core で導入されたより新しいより単純な構造に移行します。 その場合は、NuGet 参照のために *packages.config* ファイルを使用するから、 `<PackageReference>` プロジェクトファイル内の要素を使用するように移行することもできます。

元のプロジェクトの *eShopLegacyMVC* ファイルの長さは418行です。 図4-6 に、プロジェクトファイルのサンプルを示します。 全体のサイズと複雑さを理解するために、イメージの右側にはファイル全体の小さなビューが含まれています。

![図4-6](media/Figure4-6.png)

**図 4-6** *EShopLegacyMVC* ファイル構造体。

既存の ASP.NET プロジェクト用の新しいプロジェクトファイルを作成する一般的な方法は、 `dotnet new` または  >    >  Visual Studio で新しい **プロジェクト** を使用して新しい ASP.NET Core アプリを作成することです。 その後、古いプロジェクトから新しいプロジェクトにファイルをコピーして、移行を完了できます。

C# プロジェクトファイルに加えて、NuGet の依存関係は、図4-7 に示すように、別の45行 *packages.config* ファイルに格納されます。

![図4-7](media/Figure4-7.png)

**図 4-7** *packages.config* ファイル。

新しい *.csproj* ファイル形式にアップグレードした後、Visual Studio を使用してクラスライブラリプロジェクトの *packages.config* を移行できます。 ただし、この機能は ASP.NET プロジェクトでは機能しません。 [ `<PackageReference>` Visual Studio で *packages.config* をに移行する方法の詳細については、こちらを参照して](/nuget/consume-packages/migrate-packages-config-to-package-reference)ください。 多数のプロジェクトを移行する場合は、 [このコミュニティツールが役に立ち](https://github.com/MarkKharitonov/NuGetPCToPRMigrator)ます。

## <a name="create-new-aspnet-core-project"></a>新しい ASP.NET Core プロジェクトの作成

新しい ASP.NET Core プロジェクトを既存のアプリのソリューションに追加して、ファイルを簡単に移動できるようにします。ほとんどの作業は Visual Studio の **ソリューションエクスプローラー** 内から実行できます。 Visual Studio で、アプリのソリューションを右クリックし、[ **新しいプロジェクトの追加**] を選択します。 [ **ASP.NET Core web アプリケーション**] を選択し、図4-8 に示すように、新しいプロジェクトに名前を付けます。

![図4-8](media/Figure4-8.png)

**図 4-8.** 新しい ASP.NET Core web アプリケーションを追加します。

次のダイアログボックスで、使用するテンプレートを選択するように求めるメッセージが表示されます。 **[空]** テンプレートを選択します。 また、ドロップダウンリストを **.Net Core** から **.NET Framework** に変更します。 図4-9 に示すように、 **ASP.NET Core 2.2** を選択します。

![図4-9](media/Figure4-9.png)

**図 4-9** ASP.NET Core 2.2 で .NET Framework をターゲットとする空のプロジェクトテンプレートを選択します。

### <a name="migrating-nuget-packages"></a>NuGet パッケージの移行

*packages.config* をに移行するための組み込みの移行ツールは `<PackageReference>` ASP.NET プロジェクトでは機能しないため、代わりにコミュニティツールを使用するか、手動で移行することができます。 [私が使用したコミュニティツール](https://gist.github.com/tomkuijsten/2d75074d9a3c19c04ee8ea19a6289ddf)では、XSL ファイルを使用して、ある形式から別の形式に変換します。 これを使用するには、まず、新しく作成した ASP.NET Core プロジェクトフォルダーに *packages.config* ファイルをコピーします。 ファイルのバックアップを作成します。このスクリプトでは、スクリプトの実行場所にあるすべてのフォルダーから *packages.config* ファイルが削除されます。 次に、プロジェクトフォルダー (または、必要に応じてソリューション全体) から次のコマンドを実行します。

```powershell
iwr https://git.io/vdKaV -OutFile Convert-ToPackageReference.ps1
iwr https://git.io/vdKar -OutFile  Convert-ToPackageReference.xsl
./Convert-ToPackageReference.ps1 | Out-Null
```

最初の2つのコマンドは、ファイルがローカルに存在するようにファイルをダウンロードします。 最後の行では、スクリプトが実行されます。 実行後、新しいプロジェクトをビルドしてみてください。 多くの場合、エラーが発生します。 これを解決するには、一部の参照 (およびパッケージのほとんど) を削除し、 `Microsoft.AspNet` 一部の `System` 属性を削除しなければならないことがあり `xmlns` ます。

ほとんどの ASP.NET MVC アプリでは、ブートストラップや jQuery などの多くのクライアント側の依存関係が NuGet パッケージを使用してデプロイされていました。 ASP.NET Core では、NuGet パッケージはサーバー側の機能にのみ使用されます。 クライアントファイルは、他の方法で管理する必要があります。 追加された要素の一覧を確認し、 `<PackageReference>` 次のようなクライアントライブラリのものをすべて削除してメモします。

- ブートストラップ
- jQuery
- jQuery。検証
- Modernizr
- popper.js
- 対応

これらのパッケージの NuGet によってインストールされた静的クライアントファイルは、新しいプロジェクトの *wwwroot* フォルダーにコピーされ、そこからホストされます。 これらのファイルがアプリで依然として必要かどうか、およびそれらのファイルを引き続きホストするか、代わりに content delivery network (CDN) を使用するかを検討してください。 これらのライブラリのバージョンは、 [Libman](/aspnet/core/client-side/libman/) や [npm](https://www.npmjs.com/)などのツールを使用してビルド時に管理できます。 図4-10 に、変換ツールを使用してパッケージ参照を移行し、不要なパッケージを削除した後の完全な *eShopPorted* ファイルを示します。

![図4-10](media/Figure4-10.png)

**図 4-10** *EShopPorted* ファイル内のパッケージ参照。

要素に属性を設定することにより、パッケージ参照をさらに圧縮でき `<Version>1.0.0.0</Version>` `Version=1.0.0.0` `<PackageReference>` ます。

### <a name="migrate-static-files"></a>静的ファイルを移行する

アプリケーションが使用するすべての静的ファイル (サードパーティのスクリプトやフレームワークを含むが、カスタムイメージやスタイルシートも含む) は、古いプロジェクトから新しいプロジェクトにコピーする必要があります。 ASP.NET MVC アプリでは、通常、ファイルはプロジェクトフォルダー内の場所に基づいてアクセスされていました。 ASP.NET Core アプリでは、これらの静的ファイルは *wwwroot* フォルダー内の場所に基づいてアクセスされます。 *EShop* プロジェクトの場合、次のフォルダーに静的ファイルがあります。

* *コンテンツ*
* *フォント*
* *イメージ*
* *写真*
* *スクリプト*

前の手順で使用した **空** のプロジェクトテンプレートには、既定ではこのフォルダーが含まれていません。また、このフォルダーが動作するために必要なミドルウェアもありません。 追加する必要があります。

*Wwwroot* フォルダーをプロジェクトのルートに追加します。

バージョン2.2.0 の `Microsoft.AspNetCore.StaticFiles` NuGet パッケージを追加します。

*Startup.cs* で、メソッドにの呼び出しを追加し `app.UseStaticFiles()` `Configure` ます。

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

ASP.NET MVC アプリから新しいプロジェクトの *wwwroot* フォルダーに *コンテンツ* フォルダーをコピーします。

アプリを実行し、その */Content/base.css* フォルダーに移動して、必要なパスから静的ファイルが正しく提供されていることを確認します。 静的ファイルが格納されている残りのフォルダーを新しいプロジェクトにコピーし続けます。 また、プロジェクトのルートから *wwwroot* フォルダーに *favicon* ファイルをコピーします。 図4-11 は、これらのファイルとそのフォルダーがすべてコピーされた後の結果を示しています。

![図4-11](media/Figure4-11.png)

**図 4-11** 静的フォルダーが *wwwroot* フォルダーにコピーされます。

### <a name="migrate-c-files"></a>C# ファイルを移行する

次に、アプリで使用される C# ファイルをコピーします。これには、標準の MVC フォルダーや、 *コントローラー*、 *モデル*、 *ビュー* モデル、 *サービス* などのコンテンツが含まれます。 多くの場合、これらのファイルにはいくつかの変更が必要です。 一度に1つのフォルダー (またはサブフォルダー) をコピーしてコンパイルし、どのようなエラーに対処する必要があるかを確認することをお勧めします。

*EShop* サンプルの場合、移行対象として最初に選択したフォルダーは、C# エンティティと Entity Framework クラスを含む [*モデル*] フォルダーです。 このフォルダーのクラスは、ほとんどの場合に使用されるので、これらのクラスがコピーされるまでは機能しません。 フォルダーとビルドをコピーした後、コンパイラは、見つからない名前空間 `System.Web.Hosting` 、への関連アクセス `HostingEnvironment` 、およびへの参照に関連するエラーを検出しました `ConfigurationManager.AppSettings` 。 これらの問題の解決策は、必要なパスデータを渡すことです。ここでは、改行をコメントアウトし、 `TODO:` 各行にコメントを追加して追跡します。 5行を変更すると、 **タスク一覧** に5つの項目とプロジェクトビルドが表示されます。

次に、1つのクラスを持つ *ビューモデル* フォルダーがコピーされます。 簡単なものであり、すぐにビルドできます。

*Services* フォルダーがコピーされます。 このフォルダーのクラスは、[ *モデル* ] フォルダーの Entity Framework クラスに依存しているため、そのフォルダーの後にコピーする必要があります。 幸いにも、エラーが発生することなくビルドされます。

これにより、 *Controllers* フォルダーとその2つのクラスが残り `Controller` ます。 フォルダーを新しいプロジェクトにコピーしてビルドすると、7つのビルドエラーが発生します。 これらの4つはアクセスに関連 `ViewBag` しており、次のようなエラーが報告されます。

> `Missing compiler required member 'Microsoft.CSharp.RuntimeBinder.CSharpArgumentInfo.Create'`

このエラーを解決するには、NuGet パッケージ参照を C# に追加します。

```xml
<PackageReference Include="Microsoft.CSharp" Version="4.7.0" />
```

残りの3つのエラーは、参照されていないアセンブリで定義されている型を指定します。 具体的には、次の種類があります。

- `HttpServerUtilityBase`
- `RouteValueDictionary`
- `HttpRequestBase`

各エラーを1つずつ見てみましょう。 最初のエラーは、のプロパティを参照しようとしたときに、存在しなくなった場合に発生し `Server` `Controller` ます。 操作の目的は、アプリ内のイメージファイルへのパスを取得することです。

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

この問題には、2つの解決策が考えられます。 1つ目は、機能をそのまま維持することです。 この場合、を使用するのではなく、 `Server.MapPath` *wwwroot* 内のイメージファイルの場所を参照する固定パスを使用する必要があります。 または、このアクションメソッドの唯一の目的は静的イメージファイルを返すことであるため、ビューファイル内のこのアクションへの参照を更新して静的ファイルを直接参照することができます。これにより、実行時のパフォーマンスが向上します。 この操作の一部として処理は行われないため、ファイルを直接処理するわけではありません。 不都合でこのアクションへのすべての参照を更新しない場合は、静的ファイルの場所へのリダイレクトを生成するためにアクションを書き直すことができます。

次の2つのエラーは、両方とも同じコード行の同じプライベートメソッドで発生します。

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    item.PictureUri = this.Url.RouteUrl(PicController.GetPicRouteName, new { catalogItemId = item.Id }, this.Request.Url.Scheme);
}
```

`this.Url`との両方で `this.Request` コンパイラエラーが発生します。 このコードの使用方法については、 `PicController` イメージファイルをレンダリングするアクションへのリンクを作成することを目的としています。 先ほど見たものと同じものが、 *wwwroot* にある静的ファイルへの直接リンクに置き換えられる可能性があります。 ここでは、このコードをコメントアウトし、別の `TODO:` 方法を参照するコメントを追加する必要があります。

`Controller`このコードが記述されているクラスで使用される基底クラスは、を参照していることに注意 `CatalogController` `System.Web.Mvc.Controller` してください。 ASP.NET Core を使用するように更新した後は、修正が必要なエラーが発生することは間違いありません。 最初に、 `using System.Web.Mvc;` のステートメントのリストから行を削除 `using` `CatalogController` します。 次に、NuGet パッケージを追加し `Microsoft.AspNetCore.Mvc` ます。 最後に、ステートメントを追加 `using Microsoft.AspNetCore.Mvc;` し、アプリをもう一度ビルドします。

今回は、16個のエラーがあります。

- `Include` が有効な名前付き属性引数ではありません (2)
- `HttpStatusCodeResult` 見つかりませんでした (3)
- `HttpNotFound` 存在しません (3)
- `SelectList` 見つかりません (8)

さらに、これらのエラーを1つずつ確認してみましょう。 まず、を `SelectList` 追加して修正でき `using Microsoft.AspNetCore.Mvc.Rendering;` ます。これにより、エラーの半分が解消されます。

へのすべて `return HttpNotFound();` の参照は、に置き換える必要があり `return NotFound();` ます。

へのすべて `return new HttpStatusCodeResult(HttpStatusCode.BadRequest);` の参照は、に置き換える必要があり `return BadRequest();` ます。

これにより、次 `Include` `[Bind]` のようないくつかのアクションメソッドの属性でが使用されるようになります。

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind(Include = "Id,Name,Description,Price,PictureFileName,CatalogTypeId,CatalogBrandId,AvailableStock,RestockThreshold,MaxStockThreshold,OnReorder")] CatalogItem catalogItem)
{
```

上記のコードでは、モデルバインドを文字列に示されているプロパティに限定して `Include` います。 ASP.NET Core MVC では、 `[Bind]` 属性はまだ存在しますが、引数は必要ありません `Include =` 。 属性にプロパティの一覧を直接渡し `[Bind]` ます。

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind("Id,Name,Description,Price,PictureFileName,CatalogTypeId,CatalogBrandId,AvailableStock,RestockThreshold,MaxStockThreshold,OnReorder")] CatalogItem catalogItem)
{
```

これらの変更により、プロジェクトはさらにコンパイルされます。 通常は、ドメインモデルまたはデータモデルの型にモデルバインドを直接使用するのではなく、コントローラー入力に個別のモデルの種類を使用することをお勧めします。

## <a name="migrate-views"></a>ビューの移行

ビューに関連する最大の ASP.NET Core MVC 機能は、 [Razor Pages](/aspnet/core/razor-pages/) と [タグヘルパー](/aspnet/core/mvc/views/tag-helpers/built-in/)の2つです。 最初の移行では、どちらの機能も使用しません。 ただし、移行後にアプリのサポートを継続する場合は、機能を考慮する必要があります。 次の手順では、 *Views* フォルダーを元のプロジェクトから新しいプロジェクトにコピーします。 ビルド後、次の9つのエラーが発生します。

- HttpContext が存在しません (2)
- スクリプトが存在しません (5)
- スタイルが存在しません (1)
- HtmlString が見つかりませんでした (1)

これらのエラーを調査することで、そのほとんどがメイン _Layout に含まれていることがわかります。これには、スクリプトとスタイルタグのレンダリングに関連するものと、アプリをホストしているサーバーが最後に再起動された日時が表示され *ます。* 次のコードリストは、_Layout ファイル内の問題の領域を示して *い* ます。

```razor
// other lines omitted; only errors shown
@Styles.Render("~/Content/css")
@Scripts.Render("~/bundles/modernizr")

@{ var sessionInfo = new HtmlString($"{HttpContext.Current.Session["MachineName"]}, {HttpContext.Current.Session["SessionStartTime"]}");}

@Scripts.Render("~/bundles/jquery")
@Scripts.Render("~/bundles/bootstrap")
```

Modernizr への参照は削除できます。 ブートストラップと jQuery への参照は、適切なバージョンへの CDN リンクに置き換えることができます。

`@Styles.Render`行の置換後の文字列:

```html
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
```

最後の 2 `Scripts.Render` 行を次のコードに置き換えます。

```html
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
```

最後に、ブートストラップの後に、 `<link>` `<link>` アプリで使用するローカルスタイルの要素を追加します。 *EShop* の場合、結果は次のようになります。

```html
<link rel="stylesheet" href="~/Content/custom.css" />
<link rel="stylesheet" href="~/Content/base.css" />
<link rel="stylesheet" href="~/Content/Site.css" />
```

要素の表示順序を決定するには `<link>` 、元のアプリのレンダリングされた HTML を確認します。 または、 *BundleConfig.cs* を確認してください。これには、 *eShop* サンプルに適したシーケンスを示す次のコードが含まれています。

```csharp
bundles.Add(new StyleBundle("~/Content/css").Include(
          "~/Content/bootstrap.css",
          "~/Content/custom.css",
          "~/Content/base.css",
          "~/Content/site.css"));
```

もう一度ビルドすると、 *Create* ビューと *Edit* ビューでの jQuery 検証の読み込みエラーがもう1つ表示されます。 次のスクリプトで置き換えます。

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-validate/1.17.0/jquery.validate.min.js" integrity="sha512-O/nUTF5mdFkhEoQHFn9N5wmgYyW323JO6v8kr6ltSRKriZyTr/8417taVWeabVS4iONGk2V444QD0P2cwhuTkg==" crossorigin="anonymous"></script>
```

ビューで最後に修正することは、 `Session` アプリが実行された時間とコンピューターを表示するためのへの参照です。 このデータをで `Startup` 静的変数として収集し、レイアウトページに変数を表示できます。 次のプロパティを *Startup.cs* に追加します。

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

この時点で、アプリはさらに正常にビルドされます。 ただし、これを実行しようとすると Hello World が生成され *ます。* **空** の ASP.NET Core テンプレートは、要求に応じて表示されるようにのみ構成されているためです。 次のセクションでは、ASP.NET Core MVC を使用するようにアプリを構成して移行を完了します。これには、依存関係の挿入や構成も含まれます。 その後、アプリを実行する必要があります。 その後、前に作成したタスクを修正し `TODO:` ます。

## <a name="migrate-app-startup-components"></a>アプリのスタートアップコンポーネントの移行

最後の移行手順では、 *global.asax* からアプリのスタートアップタスクを実行し、そのタスクが呼び出すクラスを使用して、これらのタスクを同等の ASP.NET Core に移行します。 これらのタスクには、MVC 自体の構成、依存関係の挿入の設定、および新しい構成システムの操作が含まれます。 ASP.NET Core では、これらのタスクは *Startup.cs* ファイルで処理されます。

### <a name="configure-mvc"></a>MVC の構成

元の ASP.NET MVC アプリは、アプリの起動時に実行される global.asax のに次のコードを持ち `Application_Start` ます。 

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

これらの行を1つずつ見ると、 `RegisterContainer` メソッドは依存関係の注入を設定します。これは次のように移植されます。 次の3つの行は、MVC のさまざまな部分 (区分、フィルター、およびルート) を構成します。 バンドルは、移植されたアプリの静的ファイルに置き換えられます。 最後の行では、アプリのデータアクセスを設定します。これは後のセクションで示します。

このアプリは実際には区分を使用していないため、区分登録の呼び出しを移行するために必要な作業はありません。 アプリで領域を移行する必要がある場合、 [ドキュメントでは ASP.NET Core での領域の構成方法を指定](/aspnet/core/mvc/controllers/areas)します。

グローバルフィルターの登録を呼び出すと、 `FilterConfig` アプリの *App_Start* フォルダー内のクラスのヘルパーが呼び出されます。

```csharp
public static void RegisterGlobalFilters(GlobalFilterCollection filters)
{
    filters.Add(new HandleErrorAttribute());
}
```

アプリに追加される属性は、ASP.NET MVC フィルター () のみです `HandleErrorAttribute` 。 このフィルターにより、例外の詳細ではなく、例外が要求の一部として発生したときに、既定のアクションとビューが表示されるようになります。 ASP.NET Core では、この同じ機能がミドルウェアでも実行され `UseExceptionHandler` ます。 詳細なエラーメッセージは、既定では有効になっていません。 ミドルウェアを使用して構成する必要があり `UseDeveloperExceptionPage` ます。 元のアプリに一致するようにこの動作を構成するには、Startup.cs のメソッドの先頭に次のコードを追加する必要があり `Configure` ます。 

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

これは、eShop アプリによって使用される唯一のフィルターを処理します。この場合は、組み込みのミドルウェアを使用して実行されています。 アプリで構成する必要があるグローバルフィルターがある場合は、MVC がメソッドに追加されるときにこの処理が行われます。これについては、 `ConfigureServices` この章で後ほど説明します。

移行が必要な MVC 関連のロジックの最後の部分は、アプリの既定のルートです。 の呼び出しは、 `RouteConfig.RegisterRoutes(RouteTable.Routes)` MVC ルートテーブルを `RegisterRoutes` ヘルパーメソッドに渡します。このメソッドでは、アプリの起動時に次のコードが実行されます。

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

このコードを1行ずつ取得すると、最初の行で属性ルートのサポートが設定されます。 これは ASP.NET Core に組み込まれているため、個別に構成する必要はありません。 同様に、 *{resource} の axd* ファイルは ASP.NET Core では使用されないため、このようなルートを無視する必要はありません。 メソッドは、 `MapRoute` 一般的なルートテンプレートを使用する MVC の既定値を構成し `{controller}/{action}/{id}` ます。 また、 `CatalogController` が既定のコントローラーとして使用され、メソッドが既定のアクションであるように、このテンプレートの既定値も指定し `Index` ます。 大規模なアプリには、追加のルートを設定するために多くの呼び出しが含まれることがよくあり `MapRoute` ます。

MVC ASP.NET Core は [、従来のルーティングと属性ルーティングを](/aspnet/core/mvc/controllers/routing?preserve-view=true&view=aspnetcore-2.2)サポートしています。 従来のルーティングは、前述の方法でルートテーブルを構成する方法に似てい `RegisterRoutes` ます。 既定のルート ( *eShop* アプリで使用されるものなど) を使用して従来のルーティングを設定するには、 `Configure` *Startup.cs* のメソッドの最後に次のコードを追加します。

```csharp
app.UseMvc(routes =>
{
   routes.MapRoute("default", "{controller=Catalog}/{action=Index}/{id?}");
});
```

> [!NOTE]
> ASP.NET Core 3.0 以降では、エンドポイントを使用するように変更されます。 ASP.NET Core 2.2 の初期ポートでは、これは、従来のルートをマッピングするための適切な構文です。

これらの変更が適用されると、 `Configure` メソッドはほぼ完了します。 `app.Run`Hello World を出力する元のテンプレートのメソッド *。* 削除する必要があります。 この時点で、メソッドは次のようになります。

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

次に、MVC サービスを構成してから、残りのアプリの依存関係の挿入 (DI) をサポートします。 これまでは、 *eShopPorted* プロジェクトの `ConfigureServices` メソッドは空のままです。 ここで、作成を開始します。

最初に ASP.NET Core MVC を正常に動作させるには、次のように追加する必要があります。

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
}
```

上記のコードは、MVC 機能を使用するために必要な最小限の構成です。 この呼び出しから構成できる追加機能は多数ありますが、ここではアプリをビルドするのに十分です。 実行すると、既定の要求が適切にルーティングされるようになりましたが、DI をまだ構成していないため、 `CatalogController` 型の実装 `ICatalogService` がまだ提供されていないため、アクティブ化中にエラーが発生します。 MVC の構成については、後で詳しく説明します。 ここでは、アプリの依存関係の挿入を移行してみましょう。

#### <a name="migrate-dependency-injection-configuration"></a>依存関係挿入構成の移行

元のアプリの *global.asax* ファイルは、アプリの起動時に呼び出される次のメソッドを定義します。

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

このコードは、 [Autofac](https://autofac.org/) コンテナーを構成し、構成設定を読み取り、実際のデータまたはモックデータを使用する必要があるかどうかを判断し、この設定を Autofac モジュール (アプリの */Modules* ディレクトリにあります) に渡します。 幸い、Autofac は .NET Core をサポートしているので、モジュールを直接移行することができます。 フォルダーを新しいプロジェクトにコピーし、クラスの名前空間を更新して、コンパイルする必要があります。

ASP.NET Core には依存関係の挿入のサポートが組み込まれていますが、必要に応じて、Autofac などのサードパーティのコンテナーを簡単に接続できます。 この場合、アプリは Autofac を使用するように既に構成されているため、最も簡単な解決策は、その使用を維持することです。 これを行うには、メソッドシグネチャを変更してを `ConfigureServices` 返す必要があり `IServiceProvider` ます。また、Autofac container インスタンスを構成し、メソッドから返す必要があります。

**注:** .NET Core 3.0 以降では、サードパーティの DI コンテナーを統合するためのプロセスが変更されました。

Autofac の構成の一部では、を呼び出す必要があり `builder.Populate(services)` ます。 この拡張機能は、NuGet パッケージに含まれ `Autofac.Extensions.DependencyInjection` ています。このパッケージは、コードをコンパイルする前にインストールする必要があります。

`ConfigureServices`Autofac コンテナーを構成するための変更後、新しいメソッドは次のようになります。

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

現時点では、の設定 `useMockData` はに設定されて `true` います。 この設定はすぐに構成から読み取られます。 この時点で、図4-12 に示すように、アプリはコンパイルされ、実行時に正常に読み込まれます。

![図4-12](media/Figure4-12.png)

**図 4-12** モックデータを使用してローカルで実行されている *eShop* アプリを移植します。

#### <a name="migrate-app-settings"></a>アプリ設定の移行

ASP.NET Core は新しい [構成システム](/aspnet/core/fundamentals/configuration/?preserve-view=true&view=aspnetcore-2.2)を使用します。既定では、ファイル *のappsettings.js* が利用されます。 Program.cs のを使用することにより、 `CreateDefaultBuilder` 既定の構成はアプリで既に設定されています。  構成にアクセスするには、クラスをコンストラクターで要求するだけです。 `Startup`クラスは例外ではありません。 とその他のアプリの構成へのアクセスを開始するには `Startup` 、そのコンストラクターからのインスタンスを要求し `IConfiguration` ます。

```csharp
public Startup(IConfiguration configuration)
{
    Configuration = configuration;
}

public IConfiguration Configuration { get; }
```

元のアプリはを使用してその設定を参照して `ConfigurationManager.AppSettings` います。 この用語のすべての参照をすばやく検索すると、新しいアプリに必要な一連の設定が生成されます。 次の2つしかありません。

- `UseMockData`
- `UseCustomizationData`

アプリの構成が複雑な場合、特にカスタム構成セクションを使用している場合は、アプリケーションの構成のさまざまな部分にオブジェクトを作成し、バインドすることをお勧めします。 これらの型には、 [オプションパターン](../../core/extensions/options.md)を使用してアクセスできます。 ただし、参照されているドキュメントに記載されているように、このパターンはでは使用でき `ConfigureServices` ません。 代わりに、移植されたアプリは `UseMockData` 構成値を直接参照します。

まず、移植されたアプリのファイルを変更 `appsettings.json` し、ルートに次の2つの設定を追加します。

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

次に、を変更して、 `ConfigureServices` `UseMockData` プロパティから設定にアクセスし `Configuration` ます (以前に値をに設定してい `true` ます)。

```csharp
  bool useMockData = Configuration.GetValue<bool>("UseMockData");
```

この時点で、構成から設定がプルされます。 もう1つの設定は、 `UseCustomizationData` クラスによって使用され `CatalogDBInitializer` ます。 このクラスを最初に移植したときに、へのアクセスをコメント化して `ConfigurationManager.AppSettings["UseCustomizationData"]` います。 次に、ASP.NET Core 構成を使用するように変更します。 のコンストラクターを次のように変更 `CatalogDBInitializer` します。

```csharp
  // add using Microsoft.Extensions.Configuration
  public CatalogDBInitializer(CatalogItemHiLoGenerator indexGenerator,
      IConfiguration configuration)
  {
      this.indexGenerator = indexGenerator;
      useCustomizationData = configuration.GetValue<bool>("UseCustomizationData");
  }
```

新しい型を使用するには、web アプリ内の構成へのすべてのアクセスをこの方法で変更する必要があり `IConfiguration` ます。 .NET Framework 構成へのアクセスを必要とする依存関係では、web プロジェクトに追加された *app.config* ファイルにそのような設定を含めることができます。 依存プロジェクトは、を使用して `ConfigurationManager` 設定にアクセスできます。また、この方法を既に使用している場合は、変更を必要としません。 ただし、ASP.NET Core アプリは独自の実行可能ファイルとして実行されるため、 *web.config* を参照するのではなく、 *app.config* します。レガシアプリの *web.config* ファイルから ASP.NET Core アプリの新しい *app.config* ファイルに設定を移行することによって、 `ConfigurationManager` 設定へのアクセスにを使用するコンポーネントは引き続き正常に機能します。

アプリの移行はほぼ完了しています。 残りのタスクは、データアクセス構成のみです。
  
## <a name="data-access-considerations"></a>データアクセスに関する考慮事項

.NET Framework で実行されている ASP.NET Core アプリは Entity Framework (EF) を引き続き利用できます。 増分移行を実行する場合は、データアクセスに EF Core を使用するように移植する前に、EF 6 を使用してアプリを操作することをお勧めします。 これにより、別の移行作業ブロックが開始される前に、アプリの移行に関する問題を特定し、対処することができます。

この作業は Autofac で実行されているため、eShop サンプルの移行で EF 6 を構成する場合、特別な作業は必要ありません `ApplicationModule` 。 唯一の問題は、現在 `CatalogDBContext` クラスが *web.config* から接続文字列を読み取ろうとしていることです。これに対処するには、接続の詳細を *appsettings.js* に追加する必要があります。 次に、接続文字列を作成するときに、その接続文字列をに渡す必要があり `CatalogDBContext` ます。

の *appsettings.js* を更新して、接続文字列を含めます。 完全なファイルを次に示します。

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

の作成時に、接続文字列をコンストラクターに渡す必要があり `DbContext` ます。 インスタンスは Autofac によって作成されるため、で変更を行う必要があり `ApplicationModule` ます。 モジュールを変更して、コンストラクター内のを取得 `connectionString` し、フィールドに割り当てます。 次に、の登録を変更し `CatalogDBContext` て、接続文字列をパラメーターとして追加します。

```csharp
builder.RegisterType<CatalogDBContext>()
  .WithParameter("connectionString", _connectionString)
  .InstancePerLifetimeScope();
```

パラメーターは、それ自体の新しいコンストラクターオーバーロードにも追加する必要があり `CatalogDBContext` ます。

```csharp
public CatalogDBContext(string connectionString) : base(connectionString)
{
}
```

最後に、は `ConfigureServices` から接続文字列を読み取り、それを `Config` インスタンス化するときにに渡す必要があり `ApplicationModule` ます。

```csharp
bool useMockData = Configuration.GetValue<bool>("UseMockData");
string connectionString = Configuration.GetConnectionString("DefaultConnection");
builder.RegisterModule(new ApplicationModule(useMockData, connectionString));
```

このコードを配置すると、アプリは前と同じように実行され、がのときに SQL Server データベースに接続し `UseMockData` `false` ます。

このアプリは、この時点で運用環境でデプロイして実行できます。 ASP.NET Core に変換されますが、.NET Framework および EF 6 で実行されます。 必要に応じて、アプリを .NET Core および Entity Framework Core で実行するように移行できます。これにより、前の章で説明した追加の利点が得られます。 Entity Framework に固有の [このドキュメントでは EF Core と EF 6 を比較](/ef/efcore-and-ef6/) し、さまざまな個別の機能をサポートするライブラリを示すグリッドが含まれています。

### <a name="migrate-to-entity-framework-core"></a>Entity Framework Core への移行

EF Core に移行することを決定した場合、特に元のアプリでコードベースのモデルアプローチを使用した場合は、手順が非常に簡単になります。 [EF 6 から EF Core への移植を準備](/ef/efcore-and-ef6/porting/)するときに、使用する EF Core の移行先バージョンの機能が使用可能かどうかを確認します。 [および EDMX ベースのモデルからの移植と](/ef/efcore-and-ef6/porting/port-edmx)、[コードベースのモデルからの移植](/ef/efcore-and-ef6/porting/port-code)に関するドキュメントを参照してください。

EF Core 2.2 にアップグレードするには、適切な NuGet パッケージを追加し、名前空間を更新するという基本的な手順が必要です。 次に、接続文字列を型に渡す方法 `DbContext` と、依存関係の挿入に使用する方法を調整します。

EF Core は、プロジェクトへのパッケージ参照として追加されます。

```xml
<PackageReference Include="Microsoft.EntityFrameworkCore" Version="2.2.6" />
```

EF 6 への参照は削除されます。

```xml
<PackageReference Include="EntityFramework" Version="6.2.0" />
```

コンパイラは、およびでエラーを報告し `CatalogDBContext` `CatalogDBInitializer` ます。 `CatalogDbContext` 古い名前空間を削除してに置き換える必要があり `Microsoft.EntityFrameworkCore` ます。 そのコンストラクターは削除できます。 `DbModelBuilder` はに置き換える必要があり `ModelBuilder` ます。 型を構成するためのヘルパーメソッドは、を実装する別のクラスに移動され `IEntityTypeConfiguration<T>` ます。 その後、 `CatalogDBContext` クラスの `OnModelCreating` メソッドは次のようになります。

```csharp
protected override void OnModelCreating(ModelBuilder builder)
{
    builder.ApplyConfigurationsFromAssembly(Assembly.GetExecutingAssembly());

    base.OnModelCreating(builder);
}
```

関連するその他の変更点は次のとおりです。

- `HasDatabaseGeneratedOption(DatabaseGeneratedOption.None)` 置換後 `ValueGeneratedNever()`
- `HasRequired<T>` 置換後 `HasOne<T>`
- インストール済み `Microsoft.EntityFrameworkCore.Relational` パッケージ
- `CatalogDBContext`取得 `DbContextOptions` して基本コンストラクターに渡すコンストラクターを追加します。

の構成クラスの例を次 `CatalogType` に示します。

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

`CatalogDBInitializer`とその基本クラスは、 `CreateDatabaseIfNotExists<T>` EF Core と互換性がありません。 このクラスの目的は、データベースを作成およびシードすることです。 EF Core を使用すると、次のメソッドを使用して[、 `DbContext` に関連付けられているデータベースが作成および削除](/ef/core/managing-schemas/ensure-created)されます。

```csharp
dbContext.Database.EnsureDeleted();
dbContext.Database.EnsureCreated();
```

EF Core でのデータのシード処理は、手動スクリプトを使用するか、型構成の一部として行うことができます。 他のエンティティプロパティと共に、を使用して、クラスでシードデータを構成でき `IEntityTypeConfiguration` `builder.HasData()` ます。 元のアプリは、 *セットアップ* ディレクトリの CSV ファイルからシードデータを読み込みました。 項目が少数しかない場合、これらのデータレコードはエンティティ構成の一部として追加できます。 この方法は、頻繁に変更されるテーブル内の参照データに適しています。 次のメソッドをに追加する `CatalogTypeConfig` `Configure` と、データベースの作成時に、関連付けられている行が確実に存在するようになります。

```csharp
builder.HasData(
    new CatalogType { Id = 1, Type = "Mug" },
    new CatalogType { Id = 2, Type = "T-Shirt" },
    new CatalogType { Id = 3, Type = "Sheet" },
    new CatalogType { Id = 4, Type = "USB Memory Stick" }
);
```

初期アプリには、 `PreconfiguredData` とのデータを含むクラスが含まれている `CatalogBrand` `CatalogType` ため、このメソッドを使用すると、 `HasData` 次のようになります。

```csharp
builder.HasData(
    PreconfiguredData.GetPreconfiguredCatalogBrands()
);
```

`CatalogItem`また、データはから取得することもでき `PreconfiguredData` ます。また、関連付けられたイメージがソース管理に保持されることを前提としています。これは、アプリが機能するために必要な最後のテーブルです。 `CatalogDBInitializer`クラスは、そのクラスへの参照と共に削除できます。 `CatalogItemHiLoGenerator`ディレクトリ内のクラスと SQL ファイル `Infrastructure` も、それらへの参照 (、、) と共に削除され `CatalogService` `ApplicationModule` ます。

の特殊なキージェネレータークラスを削除することで `CatalogItem` 、このコードはから削除されました `CatalogItemConfig` 。

```csharp
builder.Property(ci => ci.Id)
    .ValueGeneratedNever()
    .IsRequired();
```

これらの変更により、ASP.NET Core アプリはビルドされますが、まだ EF Core では使用できません。これは、依存関係の挿入のために構成する必要があります。 EF Core では、最も簡単に構成する方法は `ConfigureServices` 次のとおりです。

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

Autofac の最終バージョンでは、 `ApplicationModule` アプリがモックデータを使用するように構成されているかどうかに応じて、1つの型のみを構成します。

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

移植されたアプリは実行されますが、モック以外のデータを使用するように構成されている場合、データは表示されません。 によって追加されたシードデータ `HasData` は、移行が適用されたときにのみ挿入されます。 ソースアプリは移行を使用していませんでしたが、そのような場合は移行できません。 新しい移行スクリプトから始めることをお勧めします。 これを行うには、のパッケージ参照を追加 `Microsoft.EntityFrameworkCore.Design` し、プロジェクトルートでターミナルウィンドウを開きます。 次に、次のコマンドを実行します。

```dotnetcli
dotnet ef migrations add Initial
```

既存の *eShopPorted* データベースが存在する場合は削除し、次のように実行します。

```dotnetcli
dotnet ef database update
```

これにより、データベースが作成され、シードされます。 これで、いくつかの小さな更新プログラムを実行する準備ができました。

## <a name="fix-all-todo-tasks"></a>すべての TODO タスクを修正します

この時点で移植されたアプリを実行すると、ページに画像が表示されなくなります。 これは、 `PictureUri` のプロパティ `CatalogItem` が設定されていないためです。 `TODO`Visual Studio の **タスク一覧** を使用して作成した項目の一覧を見ると、残っているのは `CatalogController` "Wwwroot から pic を参照" というメモが付いているもののみです。 問題のコードは次のとおりです。

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    //TODO: Reference pic from wwwroot
    //item.PictureUri = this.Url.RouteUrl(PicController.GetPicRouteName, new { catalogItemId = item.Id }, this.Request.Url.Scheme);
}
```

最も簡単な解決策は、サイトのパブリック *wwwroot/Pics* ディレクトリにある公開イメージファイルを参照することです。 このタスクを実行するには、メソッドを次のコードに置き換えます。

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    item.PictureUri = $"/Pics/{item.Id}.png";
}
```

この変更により、アプリを実行すると、イメージが以前と同じように動作することがわかります。

## <a name="additional-mvc-customizations"></a>追加の MVC カスタマイズ

*EShopLegacyMVC* アプリはかなり単純なので、既定の MVC の動作に関して構成する必要はありません。 ただし、CORS、フィルター、ルート制約などの追加の MVC コンポーネントを構成する必要がある場合は、通常、この情報をに提供し `Startup.ConfigureServices` ます。ここで、 `UseMvc` はを呼び出します。 たとえば、次のコードリストでは、 [CORS](/aspnet/core/security/cors?preserve-view=true&view=aspnetcore-2.2) を構成し、グローバルアクションフィルターを設定しています。

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
> CORS の構成を完了するには、でもを呼び出す必要があり `app.UseCors()` `Configure` ます。

[カスタムモデルバインダー](/aspnet/core/mvc/advanced/custom-model-binding?preserve-view=true&view=aspnetcore-2.2)やフォーマッタなどの追加の高度なシナリオについては、詳細な ASP.NET Core のドキュメントを参照してください。通常、これらは、個々のコントローラーまたはアクションに適用することも、前のコードリストに示されているのと同じオプションの方法を使用してグローバルに適用することもできます。

## <a name="other-dependencies"></a>その他の依存関係

WCF クライアントの種類やトレースコードなど、レガシ構成モデルに依存している .NET Framework 機能を使用する依存関係は、移植時に変更する必要があります。 これらの型が構成情報を直接取得するのではなく、コードで構成する必要があります。 たとえば、ASP.NET アプリの *web.config* で使用するように構成された WCF サービスへの接続は、 `basicHttpBinding` 次のコードを使用してプログラムで構成できます。

```csharp
var binding = new BasicHttpBinding();
binding.MaxReceivedMessageSize = 2_000_000;

var endpointAddress = new EndpointAddress("http://localhost:9200/ExampleService");

var myClient = new MyServiceClient(binding, endpointAddress);
```

設定の構成ファイルに依存するのではなく、WCF クライアントおよびその他の .NET Framework の種類には、コードで設定を指定する必要があります。 このように構成すると、これらの型は ASP.NET Core 2.2 アプリで引き続き機能します。

## <a name="references"></a>関連項目

- [eShopModernizing GitHub リポジトリ](https://github.com/dotnet-architecture/eShopModernizing)
- [.NET Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)
- [API と Viewmodel がドメインモデルを参照することはできません](https://ardalis.com/your-api-and-view-models-should-not-reference-domain-models/)
- [開発者の例外ページミドルウェア](/aspnet/core/fundamentals/error-handling#developer-exception-page)
- [EF Core HasData の詳細](/archive/msdn-magazine/2018/august/data-points-deep-dive-into-ef-core-hasdata-seeding)

>[!div class="step-by-step"]
>[前へ](more-migration-scenarios.md)
>[次へ](deployment-scenarios.md)
