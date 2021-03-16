---
title: WPF アプリを .NET 5 にアップグレードする
description: .NET アップグレード アシスタントを使用して、既存の .NET Framework WPF アプリを .NET 5 にアップグレードします。 .NET アップグレード アシスタントは、.NET Framework から .NET 5 にアプリを移行するときに役立つ CLI ツールです。
author: ardalis
ms.date: 02/25/2021
ms.openlocfilehash: e71cdc0ef5b72fcb7ae3985a26672e23ed0c1f12
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102108222"
---
# <a name="upgrade-a-wpf-app-to-net-5-with-the-net-upgrade-assistant"></a>.NET アップグレード アシスタントを使用して WPF アプリを .NET 5 にアップグレードする

[.NET アップグレード アシスタント](upgrade-assistant-overview.md)は、.NET Framework WPF アプリを .NET 5 にアップグレードするときに役立つコマンドライン ツールです。 この記事では、次について説明します。

* .NET Framework WPF アプリに対してツールを実行する方法のデモ
* トラブルシューティングのヒント

## <a name="upgrade-net-framework-wpf-apps"></a>.NET Framework WPF アプリをアップグレードする

このセクションでは、.NET Framework 4.6.1 を対象として新しく作成された WPF アプリに対して .NET アップグレード アシスタントを実行する方法を説明します。 ツールのインストール方法の詳細については、「[.NET アップグレード アシスタントの概要](upgrade-assistant-overview.md)」を参照してください。

### <a name="initial-demo-setup"></a>デモの初期セットアップ

ご自身の .NET Framework アプリに対して .NET アップグレード アシスタントを実行する場合は、このステップを省略できます。 その動作を確認するだけの場合は、このステップを見ると、使用するサンプル .NET WPF プロジェクトを設定する方法がわかります。

Visual Studio で、.NET Framework を使用して新しい WPF アプリを作成します。

:::image type="content" source="media/upgrade-assistant-wpf-framework/new-project.png" alt-text="Visual Studio での新しい WPF プロジェクト":::

プロジェクトに **WpfTest** という名前を付けます。 **.NET Framework 4.6.1** を使用するようにプロジェクトを構成します。

:::image type="content" source="media/upgrade-assistant-wpf-framework/configure-project.png" alt-text="Visual Studio で Windows フォーム プロジェクトを構成する":::

作成したプロジェクトとそのファイル (特にプロジェクト ファイル) を確認します。

### <a name="run-upgrade-assistant"></a>upgrade-assistant の実行

ターミナルを開き、ターゲット プロジェクトまたはソリューションが配置されているフォルダーに移動します。 `upgrade-assistant` コマンドを実行します。このとき、ターゲットとするプロジェクトの名前を渡します (プロジェクト ファイルのパスが有効である限り、任意の場所からコマンドを実行できます)。

```console
upgrade-assistant .\WpfTest.csproj
```

ツールが実行され、行われるステップの一覧が表示されます。

:::image type="content" source="media/upgrade-assistant-wpf-framework/initial-run.png" alt-text=".NET アップグレード アシスタントの初期画面":::

各ステップが完了すると、ツールにコマンドのセットが表示されます。ユーザーはそれらを使用して、次のステップを適用またはスキップすること、詳細を確認すること、ログを構成すること、プロセスを終了することができます。 あるステップで実行するアクションがないことが検出された場合は、そのステップがツールで自動的にスキップされ、実行するアクションを含む次のステップに進みます。 Enter キーを押すと、他に何も選択していない場合は次のステップが実行されます。

この例では、適用ステップを毎回選択しています。 最初のステップは、プロジェクトのバックアップです。

:::image type="content" source="media/upgrade-assistant-wpf-framework/backup-project.png" alt-text=".NET アップグレード アシスタントでのプロジェクトのバックアップ":::

ツールにバックアップのカスタム パスを入力します。または、既定値を使用します。その場合は、`.backup` という拡張子の付いたプロジェクトのバックアップが同じフォルダーに配置されます。 ツールで実行される次のステップは、プロジェクト ファイルを SDK スタイルに変換することです。

:::image type="content" source="media/upgrade-assistant-wpf-framework/convert-project.png" alt-text=".NET アップグレード アシスタントによるプロジェクトの SDK スタイルへの変換":::

プロジェクトの形式が更新されたら、次のステップは、プロジェクトの TFM を更新することです。

:::image type="content" source="media/upgrade-assistant-wpf-framework/update-tfm.png" alt-text=".NET アップグレード アシスタントによるプロジェクトの SDK スタイルへの変換":::

次に、ツールによってプロジェクトの NuGet パッケージが更新されます。

:::image type="content" source="media/upgrade-assistant-wpf-framework/update-nuget-packages.png" alt-text=".NET アップグレード アシスタントによる NuGet パッケージの更新":::

パッケージが更新されたら、次のステップは、テンプレート ファイル (存在する場合) を追加することです。 この場合、追加する必要があるテンプレート ファイルはありません。 このステップでは、次に示すように、アプリ構成ファイルを移行し、C# ソースを更新して修正プログラムを適用します。 このプロジェクトの構成ファイルまたはソース コードを変更する必要はなかったため、これらの手順は自動的に行われました。

:::image type="content" source="media/upgrade-assistant-wpf-framework/add-template-files.png" alt-text=".NET アップグレード アシスタントによってテンプレート ファイルが追加され、構成が移行される":::

これは最後のプロジェクトであるため、次のステップ "Move to next project" では、ソリューション全体の移行プロセスを完了するように求められます。

:::image type="content" source="media/upgrade-assistant-wpf-framework/complete-solution.png" alt-text=".NET アップグレード アシスタントでのソリューションの完了":::

このプロセスが完了すると、移行された WPF プロジェクトは次のようになります。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net5.0-windows</TargetFramework>
    <OutputType>WinExe</OutputType>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <UseWPF>true</UseWPF>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Microsoft.CSharp" Version="4.7.0" />
    <PackageReference Include="Microsoft.DotNet.UpgradeAssistant.Extensions.Default.Analyzers" Version="0.2.211942">
      <PrivateAssets>all</PrivateAssets>
    </PackageReference>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="5.0.2" />
  </ItemGroup>
</Project>
```

.NET アップグレード アシスタントにより、アップグレード プロセスを続けるのに役立つアナライザーもプロジェクトに追加されることにご注意ください。

## <a name="troubleshooting-tips"></a>トラブルシューティングのヒント

.NET アップグレード アシスタントの使用時に発生するおそれがある既知の問題がいくつかあります。 場合によっては、.NET アップグレード アシスタントで内部的に使用される [try-convert ツール](https://github.com/dotnet/try-convert)に問題が発生することがあります。 このツールは、より多くのシナリオに対応するように頻繁に更新されるため、最新のバージョンを使用していることをご確認ください。

- try-convert ツールをインストールして、少なくともバージョン _0.7.21201_ に更新する必要があります。
- 以前のバージョンの try-convert ツールでは、カスタムのターゲットまたは props ファイルがサポートされていませんでした。 最新バージョンにアップグレードできない場合は、これらの問題に手動で対処する必要があります。 ターゲット プロジェクト ファイルにカスタムのターゲットまたは props ファイルへの参照が含まれている場合、.NET アップグレード アシスタントを実行する前に、それらの参照をファイルから手動で削除しなければならない場合があります。

その他のトラブルシューティングのヒントと既知の問題については、[ツールの GitHub リポジトリ](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues)を参照してください。

## <a name="see-also"></a>関連項目

- [.NET アップグレード アシスタントを使用して Windows フォーム アプリを .NET 5 にアップグレードする](upgrade-assistant-winforms-framework.md)
- [.NET アップグレード アシスタントを使用して ASP.NET MVC アプリを .NET 5 にアップグレードする](upgrade-assistant-aspnetmvc.md)
- [.NET アップグレード アシスタントの概要](upgrade-assistant-overview.md)
- [.NET アップグレード アシスタントの GitHub リポジトリ](https://github.com/dotnet/upgrade-assistant)
