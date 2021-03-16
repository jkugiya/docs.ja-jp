---
title: ASP.NET MVC アプリを .NET 5 にアップグレードする
description: .NET アップグレード アシスタントを使用して、既存の .NET Framework ASP.NET MVC アプリを .NET 5 にアップグレードします。 .NET アップグレード アシスタントは、.NET Framework から .NET 5 にアプリを移行するときに役立つ CLI ツールです。
author: ardalis
ms.date: 02/25/2021
ms.openlocfilehash: 0c9af9e12b78df7c4a2aaed18155f7ee9f02870d
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102108254"
---
# <a name="upgrade-an-aspnet-mvc-app-to-net-5-with-the-net-upgrade-assistant"></a>.NET アップグレード アシスタントを使用して ASP.NET MVC アプリを .NET 5 にアップグレードする

[.NET アップグレード アシスタント](upgrade-assistant-overview.md)は、.NET Framework ASP.NET MVC アプリを .NET 5 にアップグレードするときに役立つコマンドライン ツールです。 この記事では、次について説明します。

* .NET Framework ASP.NET MVC アプリに対してツールを実行する方法のデモ
* トラブルシューティングのヒント

## <a name="upgrade-net-framework-aspnet-mvc-apps"></a>.NET Framework ASP.NET MVC アプリのアップグレード

このセクションでは、.NET Framework 4.6.1 を対象として新しく作成した ASP.NET MVC アプリに対して .NET アップグレード アシスタントを実行する方法を説明します。 ツールのインストール方法の詳細については、「[.NET アップグレード アシスタントの概要](upgrade-assistant-overview.md)」を参照してください。

### <a name="initial-demo-setup"></a>デモの初期セットアップ

ご自身の .NET Framework アプリに対して .NET アップグレード アシスタントを実行する場合は、このステップを省略できます。 このステップでは、動作を確認するために試してみたい方のために、使用するサンプルの ASP.NET MVC と Web API (.NET Framework) プロジェクトを設定する方法を示します。

Visual Studio を使用して、.NET Framework を使用した新しい ASP.NET Web アプリケーション プロジェクトを作成します。

:::image type="content" source="media/upgrade-assistant-aspnetmvc/new-project.png" alt-text="Visual Studio の新しい ASP.NET Web アプリケーション プロジェクト":::

プロジェクトに **AspNetMvcTest** という名前を付けます。 **.NET Framework 4.6.1** を使用するようにプロジェクトを構成します。

:::image type="content" source="media/upgrade-assistant-aspnetmvc/configure-project.png" alt-text="Visual Studio で ASP.NET プロジェクトを構成する":::

次のダイアログで、**MVC** アプリケーションを選択し、 **[作成]** を選択します。

:::image type="content" source="media/upgrade-assistant-aspnetmvc/create-mvc-webapi.png" alt-text="Visual Studio で ASP.NET MVC プロジェクトを作成する":::

作成したプロジェクトとそのファイル (特にプロジェクト ファイル) を確認します。

### <a name="run-upgrade-assistant"></a>upgrade-assistant の実行

ターミナルを開き、ターゲット プロジェクトまたはソリューションが配置されているフォルダーに移動します。 `upgrade-assistant` コマンドを実行します。このとき、ターゲットとするプロジェクトの名前を渡します (プロジェクト ファイルのパスが有効である限り、任意の場所からコマンドを実行できます)。

```console
upgrade-assistant .\AspNetMvcTest.csproj
```

ツールが実行され、行われるステップの一覧が表示されます。

:::image type="content" source="media/upgrade-assistant-aspnetmvc/initial-run.png" alt-text=".NET アップグレード アシスタントの初期画面":::

各ステップが完了すると、ツールにコマンドのセットが表示されます。ユーザーはそれらを使用して、次のステップを適用またはスキップすること、詳細を確認すること、ログを構成すること、プロセスを終了することができます。 あるステップで実行するアクションがないことが検出された場合は、そのステップがツールで自動的にスキップされ、実行するアクションを含む次のステップに進みます。 <kbd>Enter</kbd> キーを押すと、他に何も選択していない場合は次のステップが実行されます。

この例では、適用ステップを毎回選択しています。 最初のステップは、プロジェクトのバックアップです。

:::image type="content" source="media/upgrade-assistant-aspnetmvc/backup-project.png" alt-text=".NET アップグレード アシスタントでのプロジェクトのバックアップ":::

ツールにバックアップのカスタム パスを入力します。または、既定値を使用します。その場合は、`.backup` という拡張子の付いたプロジェクトのバックアップが同じフォルダーに配置されます。 ツールで実行される次のステップは、プロジェクト ファイルを SDK スタイルに変換することです。

:::image type="content" source="media/upgrade-assistant-aspnetmvc/convert-project.png" alt-text=".NET アップグレード アシスタントによるプロジェクトの SDK スタイルへの変換":::

プロジェクトの形式が更新されたら、次のステップは、プロジェクトの TFM を更新することです。

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-tfm.png" alt-text=".NET アップグレード アシスタントによるプロジェクトの SDK スタイルへの変換":::

次に、ツールによってプロジェクトの NuGet パッケージが更新されます。 複数のパッケージに更新が必要です。さらに、新しいアナライザー パッケージが追加されます。

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-nuget-packages.png" alt-text=".NET アップグレード アシスタントによる NuGet パッケージの更新":::

パッケージが更新されたら、次のステップは、テンプレート ファイル (存在する場合) を追加することです。 必要な 4 つのテンプレート項目がツールに表示され、そして追加されます。 次のファイルが含まれます。

- `Program.cs`
- `Startup.cs`
- `appsettings.json`
- `appsettings.Development.json`

これらのファイルは、[アプリの起動](/aspnet/core/fundamentals/startup)と[構成](/aspnet/core/fundamentals/configuration)のために ASP.NET Core によって使用されます。

:::image type="content" source="media/upgrade-assistant-aspnetmvc/add-template-files.png" alt-text=".NET アップグレード アシスタントによるテンプレート ファイルの追加":::

次に、このツールで構成ファイルを移行します。 ツールでアプリの設定が識別され、サポートされていない構成セクションが無効化されてから、`appSettings` 構成の値が移行されます。

:::image type="content" source="media/upgrade-assistant-aspnetmvc/migrate-config.png" alt-text=".NET アップグレード アシスタントによる構成の移行":::

`system.web.webPages.razor/pages/namespaces` が移行されて、ツールによる構成ファイルの移行が完了します。

:::image type="content" source="media/upgrade-assistant-aspnetmvc/migrate-config2.png" alt-text=".NET アップグレード アシスタントによる構成の移行":::

ツールによって既知の修正プログラムが適用され、C# の参照が新しい対応するものに移行されます。

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-csharp.png" alt-text=".NET アップグレード アシスタントによる C# ソースの更新":::

これは最後のプロジェクトであるため、次のステップ "Move to next project" では、ソリューション全体の移行プロセスを完了するように求められます。

:::image type="content" source="media/upgrade-assistant-aspnetmvc/complete-solution.png" alt-text=".NET アップグレード アシスタントでのソリューションの完了":::

このプロセスが完了したら、プロジェクト ファイルを開いて確認します。 次のような静的ファイルを探します。

```xml
  <ItemGroup>
    <Content Include="fonts\glyphicons-halflings-regular.woff2" />
    <Content Include="fonts\glyphicons-halflings-regular.woff" />
    <Content Include="fonts\glyphicons-halflings-regular.ttf" />
    <Content Include="fonts\glyphicons-halflings-regular.eot" />
    <Content Include="Content\bootstrap.min.css.map" />
    <Content Include="Content\bootstrap.css.map" />
    <Content Include="Content\bootstrap-theme.min.css.map" />
    <Content Include="Content\bootstrap-theme.css.map" />
    <Content Include="Scripts\jquery-3.4.1.slim.min.map" />
    <Content Include="Scripts\jquery-3.4.1.min.map" />
  </ItemGroup>
```

Web サーバーによって提供される静的ファイルは、`wwwroot` というルート レベルのフォルダー内の適切なフォルダーに移動される必要があります。 詳細については、「[ASP.NET Core の静的ファイル](/aspnet/core/fundamentals/static-files?view=aspnetcore-5.0)」を参照してください。 ファイルが移動されたら、プロジェクト ファイル内にある、これらのファイルに対応する `<Content>` 要素を削除できます。 実際、すべての `<Content>` 要素と、それらが含まれるグループを削除することができます。 また、`bootstrap` や `jQuery` のようなクライアント側ライブラリへの `<PackageReference>`があれば、削除する必要があります。

既定では、プロジェクトはクラス ライブラリとして変換されます。 1 行目の `Sdk` 属性を `Microsoft.NET.Sdk.Web` に変更し、`<TargetFramework>` を `net5.0` に設定します。 プロジェクトをコンパイルします。 この時点では、エラーの数はかなり少ないはずです。 新しい ASP.NET 4.6.1 MVC プロジェクトを移植する場合は、残りのエラーで `App_Start` フォルダー内のファイルが参照されます。

- BundleConfig.cs
- FilterConfig.cs
- RouteConfig.cs

これらのファイル、および `App_Start` フォルダー全体を削除できます。 同様に、`Global.asax` および `Global.asax.cs` ファイルも削除できます。

この時点で残っているエラーは、バンドルに関連するものだけです。 [ASP.NET Core でバンドルと縮小を構成するには、いくつかの方法](/aspnet/core/migration/mvc?view=aspnetcore-5.0#configure-bundling-and-minification)があります。 プロジェクトに最も適したものを選択してください。

## <a name="troubleshooting-tips"></a>トラブルシューティングのヒント

.NET アップグレード アシスタントの使用時に発生するおそれがある既知の問題がいくつかあります。 場合によっては、.NET アップグレード アシスタントで内部的に使用される [try-convert ツール](https://github.com/dotnet/try-convert)に問題が発生することがあります。 このツールは、より多くのシナリオに対応するように頻繁に更新されるため、最新のバージョンを使用していることをご確認ください。

- **try-convert** ツールをインストールして、少なくともバージョン _0.7.212201_ に更新する必要があります。
- 以前のバージョンの **try-convert** ツールでは、カスタムのターゲットまたは props ファイルがサポートされていませんでした。 最新バージョンにアップグレードできない場合は、これらの問題に手動で対処する必要があります。 ターゲット プロジェクト ファイルにカスタムのターゲットまたは props ファイルへの参照が含まれている場合、.NET アップグレード アシスタントを実行する前に、それらの参照をファイルから手動で削除しなければならない場合があります。

```xml
<Import Project="packages\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.2.0.1\build\net46\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.props" Condition="Exists('packages\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.2.0.1\build\net46\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.props')" />
```

その他のトラブルシューティングのヒントと既知の問題については、[ツールの GitHub リポジトリ](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues)を参照してください。

## <a name="see-also"></a>関連項目

- [.NET アップグレード アシスタントを使用して WPF アプリを .NET 5 にアップグレードする](upgrade-assistant-wpf-framework.md)
- [.NET アップグレード アシスタントを使用して Windows フォーム アプリを .NET 5 にアップグレードする](upgrade-assistant-winforms-framework.md)
- [.NET アップグレード アシスタントの概要](upgrade-assistant-overview.md)
- [.NET アップグレード アシスタントの GitHub リポジトリ](https://github.com/dotnet/upgrade-assistant)
