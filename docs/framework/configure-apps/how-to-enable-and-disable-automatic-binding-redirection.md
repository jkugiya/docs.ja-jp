---
title: 自動生成されたバインド リダイレクトを有効または無効にする
description: 自動バインド リダイレクトを有効または無効にする方法を説明します。 この機能は、.NET Framework 4.5.1 以降を対象とするデスクトップ アプリと Web アプリに影響します。
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: b099ab4958b1cf41b76884243e252e19a7a951b7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698833"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>方法: 自動バインディング リダイレクトを有効/無効にする

.NET Framework 4.5.1 以降のバージョンを対象とする Visual Studio でアプリをコンパイルすると、アセンブリの統一をオーバーライドするために、バインド リダイレクトがアプリ構成ファイルに自動的に追加される場合があります。 アプリの構成ファイルで手動でバインド リダイレクトを指定している場合でも、アプリまたはそのコンポーネントが同じアセンブリの複数バージョンを参照している場合、バインド リダイレクトが追加されます。 自動バインド リダイレクト機能は、.NET Framework 4.5.1 以降のバージョンを対象とするデスクトップ アプリと Web アプリに影響します。ただし、Web アプリに対する動作は若干異なります。 以前のバージョンの .NET Framework を対象とする既存のアプリがある場合は、自動バインド リダイレクトを有効にできます。また、バインド リダイレクトを手動で作成する場合は、この機能を無効にできます。

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>デスクトップ アプリでの自動バインド リダイレクトの無効化

自動バインド リダイレクトは、.NET Framework 4.5.1 以降のバージョンを対象とする Windows デスクトップ アプリに対して既定で有効になっています。 バインド リダイレクトは、アプリがコンパイルされ、発生する可能性のあるアセンブリの統一をオーバーライドするときに、出力構成ファイル (**app.config**) に追加されます。 ソース **app.config** ファイルは変更されません。 この機能を無効にするには、アプリのプロジェクト ファイルを変更するか、Visual Studio でプロジェクトのプロパティのチェックボックスをオフにします。

### <a name="disable-through-project-properties"></a>プロジェクトのプロパティを通じて無効にする

Visual Studio 2017 バージョン 15.7 以降を使用している場合は、プロジェクトのプロパティ ページで自動生成されたバインド リダイレクトを簡単に無効化できます。

1. **ソリューション エクスプローラー** でプロジェクトを右クリックして、 **[プロパティ]** を選択します。

2. **[アプリケーション]** ページで、 **[バインド リダイレクトの自動生成]** オプションをオフにします。

3. **Ctrl**+**S** キーを押して、変更を保存します。

### <a name="disable-manually-in-the-project-file"></a>プロジェクト ファイル内で手動で無効にする

1. 次のいずれかの方法を使用して、プロジェクト ファイルを編集用に開きます。

   - Visual Studio の **ソリューション エクスプローラー** で、プロジェクトを選択し、ショートカット メニューの **[エクスプローラーでフォルダーを開く]** をクリックします。 エクスプローラーで、プロジェクト ファイル (.csproj または .vbproj) を検索し、メモ帳で開きます。
   - Visual Studio の **ソリューション エクスプローラー** で、プロジェクトを右クリックして **[プロジェクトのアンロード]** を選択します。 アンロードされたプロジェクトをもう一度右クリックし、 **[[projectname.csproj] の編集]** を選択します。

2. プロジェクト ファイルで、次のプロパティ エントリを検索します。

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. 以下のように [`true`] \(SSL 有効) を `false` に変えます。

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a>自動バインド リダイレクトを手動で有効にする

自動バインド リダイレクトは、.NET Framework の旧バージョンを対象とする既存のアプリ内で、またはリダイレクトの追加を確認するメッセージが自動的に表示されない場合に、有効にできます。 新しいバージョンのフレームワークを対象としているが、リダイレクトの追加を確認するメッセージが自動的に表示されない場合は、アセンブリを再マップすることがビルド出力によって推奨されることがあります。

1. 次のいずれかの方法を使用して、プロジェクト ファイルを編集用に開きます。

   - Visual Studio の **ソリューション エクスプローラー** で、プロジェクトを選択し、ショートカット メニューの **[エクスプローラーでフォルダーを開く]** をクリックします。 エクスプローラーで、プロジェクト ファイル (.csproj または .vbproj) を検索し、メモ帳で開きます。
   - Visual Studio の **ソリューション エクスプローラー** で、プロジェクトを右クリックして **[プロジェクトのアンロード]** を選択します。 アンロードされたプロジェクトをもう一度右クリックし、 **[[projectname.csproj] の編集]** を選択します。

2. 最初の構成プロパティ グループ (\<PropertyGroup> タグの下) に次の要素を追加します。

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   要素が挿入されたプロジェクト ファイルの例を次に示します。

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
     <PropertyGroup>
       <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
       <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
       <ProjectGuid>{123334}</ProjectGuid>
       ...
       <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
     </PropertyGroup>
     ...
   </Project>
   ```

3. アプリをコンパイルします。

## <a name="enable-automatic-binding-redirects-in-web-apps"></a>Web アプリ内で自動バインド リダイレクトを有効にする

自動バインド リダイレクトは、Web アプリでは異なる方法で実装されます。 ソースの構成 (**web.config**) ファイルを Web アプリ用に変更する必要があるため、バインド リダイレクトは構成ファイルに自動的に追加されません。 ただし、Visual Studio によってバインドの競合が通知されるため、バインド リダイレクトを追加して競合を解決できます。 バインド リダイレクトを追加するかどうかの確認メッセージは常に表示されるため、Web アプリのこの機能を明示的に無効にする必要はありません。

**web.config** ファイルにバインド リダイレクトを追加するには:

1. Visual Studio で、アプリをコンパイルし、ビルドの警告を確認します。

   ![アセンブリ参照の競合のビルド警告](./media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. アセンブリ バインドの競合がある場合、警告が表示されます。 警告をダブルクリックするか、警告を選択して **Enter** キーを押します。

   ソース **web.config** ファイルに必要なバインド リダイレクトを自動的に追加できるダイアログ ボックスが表示されます。

   ![バインディング リダイレクトのアクセス許可ダイアログ](./media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>関連項目

- [\<bindingRedirect> 要素](./file-schema/runtime/bindingredirect-element.md)
- [アセンブリ バージョンのリダイレクト](redirect-assembly-versions.md)
