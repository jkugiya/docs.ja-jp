---
title: .NET 5 への移行の例
description: .NET Framework を対象とするサンプルアプリケーションを .NET 5 に移行する方法を示します。
ms.date: 01/19/2021
ms.openlocfilehash: 5b3743c68ee0426efffda6f999dffea788f493e9
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206543"
---
# <a name="example-of-migrating-to-net"></a>.NET への移行の例

この章では、.NET Framework から .NET への既存のアプリケーションの移行を実行する際に役立つ実用的なガイドラインを示します。

ここでは、適切に構成されたプロセスを紹介し、各ステップで考慮する必要がある最も重要なプロセスを示します。

次に、WinForms と WPF の両方のバージョンから、サンプルデスクトップアプリケーションのステップバイステップ移行プロセスについて説明します。

## <a name="migration-process-overview"></a>移行プロセスの概要

移行プロセスは、次の4つの手順で構成されています。

1. **準備**: プロジェクトにおける依存関係について理解しておく必要があります。 このステップでは、現在のプロジェクトを、移行の開始点を簡略化する状態にします。

2. **プロジェクトファイルの移行:** .net プロジェクトでは、SDK スタイルの新しいプロジェクト形式が使用されます。 この形式で新しいプロジェクトファイルを作成するか、SDK スタイルを使用する必要があるものを更新します。

3. **コードを修正してビルドする:** .NET でコードをビルドし、.NET Framework と .NET の API レベルの違いを解決します。 必要に応じて、サードパーティのパッケージを .NET をサポートするパッケージに更新します。

4. **実行とテスト:** 実行時まで表示されない相違がある可能性があります。 そのため、必ずアプリケーションを実行し、すべてが期待どおりに動作することをテストしてください。

### <a name="preparation"></a>準備

#### <a name="migrate-packagesconfig-file"></a>packages.config ファイルの移行

.NET Framework アプリケーションでは、外部パッケージへのすべての参照が *packages.config* ファイルで宣言されます。 .NET では、 *packages.config* ファイルを使用する必要がなくなりました。 代わりに、プロジェクトファイル内の [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) プロパティを使用して、アプリの NuGet パッケージを指定します。

そのため、1つの形式から別の形式に移行する必要があります。 更新を手動で実行するには、 *packages.config* ファイルに含まれている依存関係を取得し、という形式でプロジェクトファイルに移行し `PackageReference` ます。 または、Visual Studio で作業を実行できるようにするには、 *packages.config* ファイルを右クリックし、[ **packages.config を PackageReference に移行する** ] オプションを選択します。

#### <a name="verify-every-dependency-compatibility-in-net"></a>.NET のすべての依存関係の互換性を確認する

パッケージ参照を移行したら、各参照に互換性があるかどうかを確認する必要があります。 アプリケーションが [nuget.org](https://www.nuget.org/)で使用している各 NuGet パッケージの依存関係を調べることができます。パッケージに .NET Standard 依存関係がある場合、.net では、すべてのバージョンの .NET Standard が [サポート](../../standard/net-standard.md#net-implementation-support) されているため、.net 5.0 で動作します。 次の図は、パッケージの依存関係を示してい `Castle.Windsor` ます。

![Windsor パッケージの NuGet 依存関係のスクリーンショット](./media/example-migration-core/nuget-dependencies.png)

パッケージの互換性を確認するには、 <https://fuget.org> バージョンと依存関係に関するより詳細な情報を提供するツールを使用できます。

.NET をサポートしていない古いバージョンのパッケージがプロジェクトで参照されている可能性がありますが、それをサポートしている新しいバージョンが見つかる場合があります。 そのため、通常は、パッケージを新しいバージョンに更新することをお勧めします。 ただし、パッケージバージョンを更新すると、コードの更新を必要とする重大な変更が発生する場合があることに注意してください。

互換性のあるバージョンが見つからない場合はどうなりますか。 これらの重大な変更のためにパッケージのバージョンを更新したくない場合はどうすればよいですか。 .NET アプリケーションの .NET Framework パッケージに依存する可能性があるため、心配する必要はありません。 外部パッケージが .NET で使用できない API を呼び出す場合は、実行時エラーが発生する可能性があるため、必ずテストしてください。 これは、更新される予定のない古いパッケージを使用している場合に適しています。また、.NET での作業に再ターゲットすることもできます。

#### <a name="check-for-api-compatibility"></a>API の互換性を確認する

.NET Framework と .NET の API サーフェイスは似ていますが、同一ではありません。 .NET で使用可能な Api を確認してください。 .Net 移植性アナライザーツールを使用すると、.NET では使用されていない Api を表示できます。 アプリのバイナリレベルを確認し、呼び出されたすべての Api を抽出して、ターゲットフレームワークで使用できない Api (この場合は .NET 5.0) を一覧表示します。

このツールの詳細については、以下を参照してください。

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

このツールの興味深い点は、外部パッケージからのコードではなく、独自のコードの違いだけを表示し、変更できないことです。 .NET で動作するように、これらのパッケージのほとんどを更新しておく必要があります。

### <a name="migrate-with-try-convert-tool"></a>Try Convert ツールを使用した移行

[ [変換の試行](https://github.com/dotnet/try-convert/releases) ] ツールは、プロジェクトを移行するための優れた方法です。 これは、プロジェクトファイルを古いスタイルから新しい SDK スタイルにアップグレードしようとして、適用可能なプロジェクトを .NET 5 に対象するグローバルツールです。 インストールが完了したら、次のコマンドを実行できます。

```dotnetcli
try-convert -p "<path to your project file>"
```

または:

```dotnetcli
try-convert -w "<path to your solution>"
```

> [!NOTE]
> [変換の試行] ツールは、 [.Net Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)の一部として自動的に実行されます。 完全アップグレードアシスタントを実行することを検討してください。変換を試すだけではありません。

ツールの変換が試行されたら、Visual Studio でファイルを再読み込みして実行し、テストします。 お客様のプロジェクトの内容によっては、変換を実行できない可能性があります。 その場合は、以下の手順を参照できます。

#### <a name="migrate-manually"></a>手動で移行する

1. 新しい .NET プロジェクトを作成する

ほとんどの場合、既存のプロジェクトを新しい .NET 形式に更新する必要があります。 ただし、古いプロジェクトを維持しながら新しいプロジェクトを作成することもできます。 古いプロジェクトを更新することによる主な欠点は、デザイナーのサポートが失われることです。これは、お客様と開発チームにとって重要な場合があります。 デザイナーの使用を継続する場合は、古いものと同時に新しい .NET プロジェクトを作成し、アセットを共有する必要があります。 デザイナーで UI 要素を変更する必要がある場合は、古いプロジェクトに切り替えてそれを行うことができます。 また、資産はリンクされているため、.NET プロジェクトでも更新されます。

.NET 用の [SDK スタイルのプロジェクト](../../core/project-sdk/msbuild-props.md) は、.NET Framework のプロジェクト形式よりもはるかに簡単です。 前に説明したエントリとは別 `PackageReference` に、それ以上の操作は必要ありません。 新しいプロジェクト形式には、ファイルやファイルなど、 [既定で特定の拡張子を持つファイルが含まれ](../../core/project-sdk/overview.md#default-includes-and-excludes)て `.cs` おり、それらを `.xaml` プロジェクトファイルに明示的に含める必要はありません。

#### <a name="assemblyinfo-considerations"></a>AssemblyInfo に関する考慮事項

属性は .NET プロジェクトで自動生成されます。 プロジェクトに *AssemblyInfo.cs* ファイルが含まれている場合は、定義が重複するため、コンパイルの競合が発生します。 .Net プロジェクトファイルに次のエントリを追加することで、古い *AssemblyInfo.cs* ファイルを削除するか、自動生成を無効にすることができます。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a>リソース

埋め込みリソースは自動的にインクルードされますが、リソースは含まれないため、リソースを新しいプロジェクトファイルに移行する必要があります。

#### <a name="package-references"></a>パッケージ参照

**PackageReference への packages.config 移行** オプションを使用すると、前に説明したように、外部パッケージの参照を新しい形式に簡単に移動できます。

#### <a name="update-package-references"></a>パッケージ参照の更新

前のセクションで示したように、互換性のあるものとして見つかったパッケージのバージョンを更新します。

### <a name="fix-the-code-and-build"></a>コードを修正してビルドする

#### <a name="microsoftwindowscompatibility"></a>Microsoft. Windows. 互換性

アプリケーションが .NET で使用できない Api (レジストリ、Acl、WCF など) に依存している場合は、パッケージへの参照を含めて、これらの Windows 固有の Api を追加する必要があり `Microsoft.Windows.Compatibility` ます。 これらは .NET で動作しますが、クロスプラットフォームではないため、含まれていません。

API Analyzer () というツールを使用すると、 <https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer> コードと互換性のない api を識別できます。

#### <a name="use-if-directives"></a>If ディレクティブを使用する \#

.NET Framework と .NET を対象とする場合に異なる実行パスが必要な場合は、コンパイル定数を使用する必要があります。 \#同じコードベースを両方のターゲットに保持するために、いくつかの if ディレクティブをコードに追加します。

#### <a name="technologies-not-available-on-net"></a>.NET で使用できないテクノロジ

次のような一部のテクノロジは .NET では使用できません。

* AppDomain
* リモート処理
* コード アクセス セキュリティ
* WCF サーバー
* Windows Workflow

そのため、これらのテクノロジをアプリケーションで使用している場合は、それらのテクノロジに代わるものを見つける必要があります。 詳細については、「 [.Net Core および .net 5 + で使用できないテクノロジ .NET Framework](../../core/porting/net-framework-tech-unavailable.md) 」を参照してください。

#### <a name="regenerate-autogenerated-clients"></a>自動生成したクライアントの再生成

アプリケーションが自動生成されたコード (WCF クライアントなど) を使用する場合は、.NET を対象とするようにこのコードを再生成する必要がある場合があります。 既定の .NET アセンブリセットの一部として含まれていない可能性があるため、不足している参照がいくつか見つかることがあります。 などのツールを使用 <https://apisof.net/> すると、不足している参照が存在するアセンブリを簡単に見つけて、NuGet から追加することができます。

#### <a name="rolling-back-package-versions"></a>パッケージバージョンのロールバック

一般的なルールとして、1つのパッケージバージョンを .NET と互換性を持つように更新することをお勧めしました。 ただし、アセンブリの更新バージョンと互換性のあるバージョンをターゲットにすると、支払いが行われないことがわかります。 変更のコストが許容できない場合は、.NET Framework で使用しているパッケージのバージョンをロールバックすることを検討してください。 .NET を対象としていない場合もありますが、サポートされていない Api を呼び出す場合を除き、適切に機能します。

### <a name="run-and-test"></a>実行してテストする

エラーを発生させずにアプリケーションを構築した後は、すべての機能をテストすることで、移行の最後の手順を開始できます。

この最後の手順では、アプリケーションの複雑さと使用している依存関係と Api に応じて、いくつかの異なる問題を見つけることができます。

たとえば、構成ファイル (*app.config*) を使用する場合、構成セクションが存在しないなど、実行時にエラーが発生することがあります。 NuGet パッケージを使用する `Microsoft.Extensions.Configuration` と、そのエラーを修正する必要があります。

エラーのもう1つの理由は、 `BeginInvoke` `EndInvoke` .net でサポートされていないメソッドとメソッドを使用することです。 .Net ではサポートされません。これは、.NET 上に存在しないリモート処理に依存しているためです。 この問題を解決するに `await` は、キーワード (使用可能な場合) またはメソッドを使用してください <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> 。

互換性アナライザーを使用すると、.NET で実行時に問題を引き起こす可能性がある Api とコードパターンをコード内で識別できます。 にアクセス <https://github.com/dotnet/platform-compat> し、プロジェクトで .NET API analyzer を使用します。

## <a name="migrating-a-windows-forms-application"></a>Windows フォームアプリケーションの移行

Windows フォームアプリケーションの移行プロセスを完了するには、で入手できる eShop サンプルアプリケーションを移行することを選択しました <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> 。 移行の完全な結果については、「」を参照 <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> してください。

このアプリケーションは、製品カタログを表示し、ユーザーが製品の移動、フィルター処理、および検索を行えるようにします。 アーキテクチャの観点から見ると、アプリは、ファサードとして機能する外部の WCF サービスをバックエンドデータベースに依存しています。

メインアプリケーションウィンドウは、次の図のように表示されます。

![メインアプリケーションウィンドウ](./media/example-migration-core/main-application-window.png)

.Csproj プロジェクトファイルを開くと、次のような内容が表示さ *れ* ます。

![.Csproj ファイルの内容のスクリーンショット](./media/example-migration-core/csproj-file.png)

既に説明したように、.NET プロジェクトはよりコンパクトなスタイルであり、プロジェクトの構造を新しい .NET SDK スタイルに移行する必要があります。

ソリューションエクスプローラーで Windows フォームプロジェクトを右クリックし、[プロジェクトの **アンロード**] [編集] の順に選択し  >  ます。

.Csproj ファイルを更新できるようになりました。 コンテンツ全体を削除し、次のコードに置き換えます。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

プロジェクトを保存して再読み込みします。 これでプロジェクトファイルの更新が完了し、プロジェクトは .NET を対象としています。

この時点でプロジェクトをコンパイルすると、WCF クライアントリファレンスに関連するエラーが表示されます。 このコードは自動生成されるため、.NET を対象とするように再生成する必要があります。

![Visual Studio でのコンパイルエラーのスクリーンショット](./media/example-migration-core/winforms-compilation-errors.png)

*Reference.cs* ファイルを削除し、新しいサービスクライアントを生成します。

**接続済みサービス** を右クリックし、[**接続済みサービスの追加**] オプションを選択します。

![[接続済みサービスの追加] オプションが選択されている接続済みサービスメニューのスクリーンショット](./media/example-migration-core/add-connected-service.png)

[接続済みサービス] ウィンドウが開きます。 [ **MICROSOFT WCF Web サービス** ] オプションを選択します。

![[接続済みサービス] ウィンドウのスクリーンショット](./media/example-migration-core/connected-services-window.png)

この例と同じソリューションに WCF サービスがある場合は、サービス URL を指定する代わりに、 **Discover** オプションを選択できます。

![[WCF Web サービス参照の構成] ウィンドウのスクリーンショット](./media/example-migration-core/configure-wcf-reference.png)

サービスが配置されると、このツールはサービスによって実装されている API コントラクトを反映します。 次の図に示すように、名前空間の名前をに変更し `eShopServiceReference` ます。

![API コントラクトと名前空間が変更されたことを示すスクリーンショット](./media/example-migration-core/api-contract-namespace.png)

[ **完了** ] ボタンを選択します。 しばらくすると、生成されたコードが表示されます。

次の3つの自動生成ファイルが表示できます。

1. *はじめに*: WCF に関する情報を提供する GitHub へのリンク。
2. *ConnectedService.js*: サービスに接続するための構成パラメーター。
3. *Reference.cs*: 実際の WCF クライアントコード。

![自動生成された3つのファイルがある [ソリューションエクスプローラー] ウィンドウのスクリーンショット](./media/example-migration-core/autogenerated-files.png)

もう一度コンパイルすると、*ヘルパー* フォルダー内の *.cs* ファイルから発生する多くのエラーが表示されます。 このフォルダーは .NET Framework バージョンに存在しましたが、古い *.csproj* には含まれていません。 ただし、新しい SDK スタイルのプロジェクトでは、プロジェクトファイルの場所の下にあるすべてのコードファイルが既定で含まれています。 つまり、新しい .NET Core プロジェクトでは、 *ヘルパー* フォルダー内のファイルのコンパイルが試行されます。 このフォルダーは必須ではないため、安全に削除できます。

プロジェクトを再度コンパイルして実行すると、製品イメージは表示されません。 問題は、ファイルへのパスが少し変更されたことです。 この問題を解決するには、パスに別の深さレベルを追加し、ファイル内で次の行を更新する必要があり `CatalogView.cs` ます。

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

to

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

この変更を行った後、アプリケーションが起動され、.NET Core で想定どおりに実行されることを確認できます。

## <a name="migrating-a-wpf-application"></a>WPF アプリケーションの移行

サンプルアプリケーションを使用して `Shop.ClassicWPF` 移行を実行します。 次の図は、移行前のアプリのスクリーンショットを示しています。

![移行前のサンプルアプリ](./media/example-migration-core/app-before-migration.png)

このアプリケーションでは、ローカルの SQL Server Express データベースを使用して、製品カタログ情報を保持します。 このデータベースには、WPF アプリケーションから直接アクセスします。

最初に、 *.csproj* ファイルを .net Core アプリケーションで使用される新しい SDK スタイルに更新する必要があります。 「Windows フォームの移行」で説明されているのと同じ手順に従います。プロジェクトをアンロードし、 *.csproj* ファイルを開き、内容を更新して、プロジェクトを再読み込みします。

この場合は、 *.csproj* ファイルのすべての内容を削除し、次のコードに置き換えます。

```xml
 <Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWpf>true</UseWpf>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

プロジェクトを再読み込みしてコンパイルすると、次のエラーが表示されます。

![Visual Studio でのコンパイルエラーのスクリーンショット](./media/example-migration-core/wpf-compilation-error.png)

*.Csproj* の内容をすべて削除したため、古いプロジェクトに存在するプロジェクト参照の仕様が失われています。 次の行を *.csproj* ファイルに追加して、プロジェクト参照を戻す必要があります。

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

また、[ **依存関係** ] ノードを右クリックし、[ **プロジェクト参照の追加**] を選択して、Visual Studio が役に立ちます。 ソリューションからプロジェクトを選択し、[ **OK]** をクリックします。

![[参照マネージャー] ダイアログのスクリーンショット (eShop. SqlProvider プロジェクトが選択されている場合)](./media/example-migration-core/reference-manager.png)

見つからないプロジェクト参照を追加すると、アプリケーションは .NET 上で期待どおりにコンパイルおよび実行されます。

>[!div class="step-by-step"]
>[前へ](windows-migration.md)
>[次へ](deploy-modern-applications.md)
