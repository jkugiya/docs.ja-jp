---
title: .NET 5 への移行の例
description: .NET Framework をターゲットとするサンプル アプリケーションを .NET 5 に移行する方法を示します。
ms.date: 01/19/2021
ms.openlocfilehash: 02a45859dfca891598e235e3de1ed968aefb5bf4
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605166"
---
# <a name="example-of-migrating-to-net"></a>.NET への移行の例

この章では、.NET Framework から .NET への既存のアプリケーションの移行を実行する際に役立つ実用的なガイドラインを示します。

従うことができる適切に構成されたプロセスと、各手順で考慮する必要がある最も重要なことを示します。

その後、WinForms と WPF の両方のバージョンからのサンプル デスクトップ アプリケーションのステップバイステップ移行プロセスについて説明します。

## <a name="migration-process-overview"></a>移行プロセスの概要

移行プロセスは次の 4 つの手順で構成されています。

1. **準備**: プロジェクトで先のことを見据えて考える必要がある依存関係について理解します。 この手順では、現在のプロジェクトを、移行の開始点を簡略化する状態にします。

2. **プロジェクト ファイルを移行する:** .NET プロジェクトでは、SDK スタイルの新しいプロジェクト形式を使用します。 この形式で新しいプロジェクト ファイルを作成するか、SDK スタイルを使用する必要があるものを更新します。

3. **コードを修正してビルドする:** .NET でコードをビルドし、.NET Framework と .NET の API レベルの違いに対処します。 必要に応じて、サードパーティのパッケージを、.NET をサポートするものに更新します。

4. **実行してテストする:** 実行時まで現れない違いがある可能性があります。 そのため、必ずアプリケーションを実行し、すべてが期待どおりに動作することをテストしてください。

### <a name="preparation"></a>準備

#### <a name="migrate-packagesconfig-file"></a>packages.config ファイルを移行する

.NET Framework アプリケーションでは、外部パッケージへのすべての参照が *packages.config* ファイルで宣言されます。 .NET では、*packages.config* ファイルを使用する必要がなくなりました。 代わりに、プロジェクト ファイル内で [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) プロパティを使用して、ご利用のアプリの NuGet パッケージを指定します。

そのため、形式間の移行が必要になります。 手動で更新するには、*packages.config* ファイルに含まれている依存関係を取得し、`PackageReference` という形式でプロジェクト ファイルに移行します。 または、Visual Studio で自動的に作業が行われるようにすることができます。その場合は、*packages.config* ファイルを右クリックし、 **[packages.config を PackageReference に移行する]** オプションを選択します。

#### <a name="verify-every-dependency-compatibility-in-net"></a>.NET のすべての依存関係の互換性を確認する

パッケージ参照を移行したら、各参照に互換性があるかどうかを確認する必要があります。 [nuget.org](https://www.nuget.org/) で、アプリケーションによって使用される各 NuGet パッケージの依存関係を調べることができます。そのパッケージに .NET Standard の依存関係がある場合は、.NET 5.0 で機能します。.NET ではすべてのバージョンの .NET Standard が[サポートされる](../../standard/net-standard.md#net-implementation-support)ためです。 次の画像には、`Castle.Windsor` パッケージの依存関係が示されています。

![Castle.Windsor パッケージの NuGet 依存関係のスクリーンショット](./media/example-migration-core/nuget-dependencies.png)

パッケージの互換性を確認するために、バージョンと依存関係に関するより詳細な情報を提供するツール <https://fuget.org> を使用できます。

.NET をサポートしていない古いバージョンのパッケージがプロジェクトで参照されている可能性がありますが、それをサポートする新しいバージョンが見つかる場合があります。 そのため、通常はパッケージを新しいバージョンに更新することをお勧めします。 しかし、パッケージ バージョンを更新すると、コードの更新を強制するいくつかの破壊的変更が発生する場合があることに注意してください。

互換性のあるバージョンが見つからない場合はどうなりますか。 これらの破壊的変更のため、パッケージのバージョンを更新したくない場合はどうすればよいですか。 .NET アプリケーションの .NET Framework パッケージに依存する可能性があるため、心配する必要はありません。 外部パッケージにより .NET で使用できない API が呼び出されると、実行時エラーが発生する可能性があるため、必ずテストしてください。 これは、更新する予定のない古いパッケージを使用しており、.NET で作業するために再ターゲットするだけで済む場合に適しています。

#### <a name="check-for-api-compatibility"></a>API の互換性を確認する

.NET Framework と .NET の API サーフェイスは似ていますが、同一ではないため、.NET で使用できる API とできないものを確認する必要があります。 .NET Portability Analyzer ツールを利用すると、使用されている API のうち、.NET には存在しないものを表示できます。 アプリのバイナリ レベルが確認され、呼び出されたすべての API が抽出されてから、ターゲット フレームワーク (この場合は、.NET 5.0) で使用できない API が一覧表示されます。

このツールの詳細については、以下を参照してください。

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

このツールの興味深い点は、変更できない外部パッケージのコードではなく、独自のコードの違いのみが表示されることです。 .NET で動作するように、これらのパッケージのほとんどを更新しておく必要があることに注意してください。

### <a name="migrate-with-try-convert-tool"></a>Try Convert ツールを使用して移行する

[Try Convert](https://github.com/dotnet/try-convert/releases) ツールは、プロジェクトを移行するための優れた方法です。 これはグローバル ツールであり、古いスタイルから新しい SDK スタイルへのプロジェクト ファイルのアップグレードの試行と、.NET 5 への適用可能なプロジェクトの再ターゲットが行われます。 インストールが完了したら、次のコマンドを実行できます。

```dotnetcli
try-convert -p "<path to your project file>"
```

または:

```dotnetcli
try-convert -w "<path to your solution>"
```

> [!NOTE]
> try-convert ツールは、[.NET Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)の一部として自動的に実行されます。 Try Convert だけでなく、完全な Upgrade Assistant の実行を検討してください。

ツールにより変換が試行された後、Visual Studio にファイルを再度読み込み、実行してテストします。 プロジェクトの仕様によっては、Try Convert で変換を実行できなくなる場合があります。 その場合は、以下の手順を参照できます。

#### <a name="migrate-manually"></a>手動で移行する

1. 新しい .NET プロジェクトを作成する

ほとんどの場合、既存のプロジェクトを新しい .NET 形式に更新したいと考えます。 しかし、古いプロジェクトを維持しながら新しいものを作成することもできます。 古いプロジェクトの更新の主な欠点は、デザイナーのサポートが失われることです。これは、お客様と開発チームにとって重要な場合があります。 引き続きデザイナーを使用する場合は、古い .NET プロジェクトを維持しながら新しいものを作成し、資産を共有する必要があります。 デザイナーで UI 要素を変更する必要がある場合は、古いプロジェクトに切り替えてそれを行うことができます。 また、資産はリンクされているため、.NET プロジェクトでも更新されます。

.NET の [SDK スタイルのプロジェクト](../../core/project-sdk/msbuild-props.md)は、.NET Framework のプロジェクト形式よりもはるかにシンプルです。 前述の `PackageReference` エントリとは別に、それ以上の操作は必要ありません。 新しいプロジェクト形式には、`.cs` および `.xaml` ファイルなど、[既定で特定の拡張子を持つファイルが含まれており](../../core/project-sdk/overview.md#default-includes-and-excludes)、それらをプロジェクト ファイルに明示的に含める必要はありません。

#### <a name="assemblyinfo-considerations"></a>AssemblyInfo に関する考慮事項

属性は .NET プロジェクトで自動生成されます。 そのプロジェクトに *AssemblyInfo.cs* ファイルが含まれている場合は、定義が重複するため、コンパイルの競合が発生します。 .NET プロジェクト ファイルに次のエントリを追加することで、古い *AssemblyInfo.cs* ファイルを削除したり、自動生成を無効にしたりすることができます。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a>リソース

埋め込みリソースは自動的に含まれますが、リソースは含まれないため、そのリソースを新しいプロジェクト ファイルに移行する必要があります。

#### <a name="package-references"></a>パッケージ参照

**[packages.config を PackageReference に移行する]** オプションを使用すると、前述のとおり、外部パッケージの参照を新しい形式に簡単に移動できます。

#### <a name="update-package-references"></a>パッケージ参照の更新

前のセクションで示したように、互換性があることがわかったパッケージのバージョンを更新します。

### <a name="fix-the-code-and-build"></a>コードを修正してビルドする

#### <a name="microsoftwindowscompatibility"></a>Microsoft.Windows.Compatibility

アプリケーションが .NET で使用できない API (レジストリ、ACL、WCF など) に依存している場合は、`Microsoft.Windows.Compatibility` パッケージへの参照を含めて、これらの Windows 固有の API を追加する必要があります。 これらは .NET で動作しますが、クロスプラットフォームではないため含まれていません。

API Analyzer (<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>) というツールがあります。これは、コードと互換性のない API を特定するのに役立ちます。

#### <a name="use-if-directives"></a>\#If ディレクティブを使用する

.NET Framework と .NET をターゲットとする際に異なる実行パスが必要な場合は、コンパイル定数を使用する必要があります。 両方のターゲットに対して同じコード ベースを保持するために、いくつかの \#if ディレクティブをコードに追加します。

#### <a name="technologies-not-available-on-net"></a>.NET で使用できないテクノロジ

次のような一部のテクノロジは .NET では使用できません。

* AppDomain
* リモート処理
* コード アクセス セキュリティ
* WCF サーバー
* Windows Workflow

そのため、これらのテクノロジをアプリケーションで使用する場合は、それらに代わるものを見つける必要があります。 詳細については、「[.NET Core および .NET 5 以降で使用できない .NET Framework テクノロジ](../../core/porting/net-framework-tech-unavailable.md)」の記事を参照してください。

#### <a name="regenerate-autogenerated-clients"></a>自動生成されたクライアントを再生成する

自動生成されたコード (WCF クライアントなど) がアプリケーションによって使用される場合は、.NET をターゲットとするようにこのコードを再生成する必要があることがあります。 場合によっては、欠落している参照がいくつか見つかることがあります。これらは既定の .NET アセンブリ セットの一部として含まれない場合があるためです。 <https://apisof.net/> などのツールを使用すると、欠落している参照が存在するアセンブリを簡単に見つけて、NuGet から追加することができます。

#### <a name="rolling-back-package-versions"></a>パッケージ バージョンのロールバック

前述のとおり、通常はすべてのパッケージ バージョンを .NET と互換性を持つように更新することをお勧めします。 しかし、更新された互換性のあるバージョンのアセンブリをターゲットにするだけでは効果がないことがわかります。 変更のコストを許容できない場合は、パッケージ バージョンをロールバックし、.NET Framework で使用しているものを維持することを検討できます。 .NET をターゲットとしない場合もありますが、一部のサポートされていない API を呼び出す場合を除き、適切に機能します。

### <a name="run-and-test"></a>実行してテストする

エラーが発生することなくアプリケーションがビルドされたら、すべての機能をテストすることで、移行の最後の手順を開始できます。

この最後の手順では、アプリケーションの複雑さ、および使用している依存関係と API に応じて、いくつかの異なる問題を見つけることができます。

たとえば、構成ファイル (*app.config*) を使用する場合、実行時にエラー (構成セクションが存在しないなど) がいくつか見つかることがあります。 `Microsoft.Extensions.Configuration` NuGet パッケージを使用すれば、そのエラーが修正されるはずです。

エラーのもう 1 つの理由は、`BeginInvoke` および `EndInvoke` メソッドの使用です。これらは .NET でサポートされていないためです。 これらは .NET 上に存在しないリモート処理に依存しているため、.NET でサポートされていません。 この問題を解決するために、`await` キーワード (使用可能な場合) または <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> メソッドを使用してみてください。

互換性アナライザーを使用すると、実行時に .NET に関する問題を引き起こす可能性がある API とコード パターンをコード内で特定できます。 <https://github.com/dotnet/platform-compat> に移動し、プロジェクトで .NET API アナライザーを使用します。

## <a name="migrating-a-windows-forms-application"></a>Windows フォーム アプリケーションの移行

Windows フォーム アプリケーションの完全な移行プロセスを示すために、ここでは <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> で入手できる eShop サンプル アプリケーションを移行することにしました。 移行の完全な結果は、<https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> で確認できます。

このアプリケーションにより製品カタログが示され、ユーザーは製品を移動、フィルター処理、および検索することができます。 アーキテクチャの観点から見ると、アプリは、バックエンド データベースに対するファサードとして機能する外部の WCF サービスに依存しています。

メイン アプリケーション ウィンドウは、次の画像のように表示されます。

![メイン アプリケーション ウィンドウ](./media/example-migration-core/main-application-window.png)

*.csproj* プロジェクト ファイルを開くと、このようになっています。

![csproj ファイルの内容のスクリーンショット](./media/example-migration-core/csproj-file.png)

前述のとおり、.NET プロジェクトのスタイルはよりコンパクトなものであり、プロジェクトの構造を新しい .NET SDK スタイルに移行する必要があります。

ソリューション エクスプローラーで Windows フォーム プロジェクトを右クリックし、 **[プロジェクトのアンロード]**  >  **[編集]** の順に選択します。

これで、.csproj ファイルを更新できるようになりました。 内容全体を削除し、次のコードに置き換えます。

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

プロジェクトを保存して再度読み込みます。 これでプロジェクト ファイルの更新が完了し、プロジェクトのターゲットは .NET となります。

この時点でプロジェクトをコンパイルすると、WCF クライアント参照に関するエラーがいくつか見つかります。 このコードは自動生成されるため、.NET をターゲットとするように再生成する必要があります。

![エラーを示す Visual Studio の [エラー一覧]](./media/example-migration-core/winforms-compilation-errors.png)

*Reference.cs* ファイルを削除し、新しいサービス クライアントを生成します。

**[接続済みサービス]** を右クリックし、 **[接続済みサービスの追加]** オプションを選択します。

![[接続済みサービスの追加] オプションが選択されている [接続済みサービス] メニューのスクリーンショット](./media/example-migration-core/add-connected-service.png)

[接続済みサービス] ウィンドウが開きます。 **[Microsoft WCF Web Service]** オプションを選択します。

![[接続済みサービス] ウィンドウのスクリーンショット](./media/example-migration-core/connected-services-window.png)

この例と同じソリューションに WCF サービスがある場合は、サービス URL を指定する代わりに、 **[検出]** オプションを選択できます。

![[WCF Web Service Reference の構成] ウィンドウのスクリーンショット](./media/example-migration-core/configure-wcf-reference.png)

サービスが配置されると、ツールにはサービスによって実装された API コントラクトが反映されます。 次の画像に示されているように、名前空間の名前を `eShopServiceReference` に変更します。

![API コントラクトと変更された名前空間のスクリーンショット](./media/example-migration-core/api-contract-namespace.png)

**[完了]** ボタンを選択します。 しばらくすると、生成されたコードが表示されます。

自動生成された次の 3 つのファイルが表示されるはずです。

1. *はじめに*: WCF に関する情報を提供する GitHub へのリンク。
2. *ConnectedService.js*: サービスに接続するための構成パラメーター。
3. *Reference.cs*: 実際の WCF クライアント コード。

![自動生成された 3 つのファイルがあるソリューション エクスプローラー ウィンドウのスクリーンショット](./media/example-migration-core/autogenerated-files.png)

もう一度コンパイルすると、*Helper* フォルダー内の *.cs* ファイルから発生する多くのエラーが表示されます。 このフォルダーは .NET Framework バージョンに存在しましたが、古い *.csproj* には含まれていませんでした。 しかし、新しい SDK スタイルのプロジェクトでは、プロジェクト ファイルの場所の下にあるすべてのコード ファイルが既定で含まれます。 つまり、新しい .NET Core プロジェクトにより、*Helper* フォルダー内のファイルのコンパイルが試行されます。 そのフォルダーは必要ではないため、安全に削除できます。

プロジェクトをもう一度コンパイルして実行すると、製品イメージが表示されなくなります。 ここでの問題は、ファイルへのパスが少し変更されたことです。 この問題を解決するには、パスに別の深さのレベルを追加し、`CatalogView.cs` ファイル内で次の行を更新する必要があります。

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

to

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

この変更後に、アプリケーションが起動し、.NET Core で想定どおりに実行されることを確認できます。

## <a name="migrating-a-wpf-application"></a>WPF アプリケーションの移行

`Shop.ClassicWPF` サンプル アプリケーションを使用して移行を実行します。 次の画像は、移行前のアプリのスクリーンショットを示しています。

![移行前のサンプル アプリ](./media/example-migration-core/app-before-migration.png)

このアプリケーションでは、ローカルの SQL Server Express データベースを使用して、製品カタログ情報を保持します。 このデータベースには、WPF アプリケーションから直接アクセスします。

最初に、 *.csproj* ファイルを、.NET Core アプリケーションで使用される新しい SDK スタイルに更新する必要があります。 Windows フォームの移行で説明されているのと同じ手順に従います。プロジェクトをアンロードし、 *.csproj* ファイルを開き、その内容を更新して、プロジェクトを再度読み込みます。

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

プロジェクトを再度読み込んでコンパイルすると、次のエラーが表示されます。

![1 つのエラー CS0234 が示されている Visual Studio の [エラー一覧]](./media/example-migration-core/wpf-compilation-error.png)

*.csproj* の内容をすべて削除したため、古いプロジェクトに存在するプロジェクト参照の仕様が失われています。 ここで必要なのは、この行を *.csproj* ファイルに追加し、プロジェクト参照を再度含めることだけです。

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

また、 **[依存関係]** ノードを右クリックし、 **[プロジェクト参照の追加]** を選択することで、Visual Studio で作業を行うこともできます。 ソリューションからプロジェクトを選択し、 **[OK]** をクリックします。

![eShop.SqlProvider プロジェクトが選択されている [参照マネージャー] ダイアログのスクリーンショット](./media/example-migration-core/reference-manager.png)

欠落しているプロジェクト参照を追加すると、アプリケーションは .NET 上で予期したとおりにコンパイルおよび実行されます。

>[!div class="step-by-step"]
>[前へ](windows-migration.md)
>[次へ](deploy-modern-applications.md)
