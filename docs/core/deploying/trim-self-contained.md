---
title: 自己完結型アプリケーションのトリミング
description: 自己完結型アプリケーションをトリミングしてサイズを縮小する方法について説明します。 .NET Core は、自己完結型で公開されているアプリケーションでランタイムをバンドルし、通常は必要以上のランタイムを含んでいます。
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: b5e2650d8240648aa05eaa9026a57b926f63b4de
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872874"
---
# <a name="trim-self-contained-deployments-and-executables"></a>自己完結型の展開と実行可能ファイルのトリミング

[フレームワークに依存するデプロイ モデル](index.md#publish-framework-dependent)は、.NET の開始以降に最も一般的となったデプロイ モデルです。 このシナリオでは、アプリケーション開発者は、.NET ランタイムおよびフレームワーク ライブラリがクライアント コンピューターで利用できることを見込んで、アプリケーションとサードパーティのアセンブリのみをバンドルします。 このデプロイ モデルは .NET Core でも引き続き主に使用されますが、フレームワークに依存するモデルが最適ではないシナリオもあります。 別の方法としては、[自己完結型アプリケーション](index.md#publish-self-contained)を発行します。この場合、.NET Core ランタイムおよびフレームワークは、アプリケーションとサードパーティのアセンブリと共にバンドルされます。

トリミング自己完結型のデプロイ モデルは、展開のサイズを小さくするために最適化された、自己完結型のデプロイ モデルの特殊なバージョンです。 展開のサイズを最小限に抑えることは、Blazor アプリケーションなどの一部のクライアント側のシナリオでは重要な要件です。 アプリケーションの複雑さによっては、アプリケーションを実行するために、フレームワーク アセンブリのサブセットのみが参照され、各アセンブリ内のコードのサブセットのみが必要となります。 ライブラリの未使用部分は不要であり、パッケージ化されたアプリケーションから削除することができます。

ただし、アプリケーションのビルド時分析によってランタイム エラーが発生しうるというリスクがあります。これは、問題のあるさまざまなコード パターンを確実に分析できないためです (ほとんどの場合、リフレクション使用が中心となります)。 信頼性を保証できないため、このデプロイ モデルはプレビュー機能として提供されます。

ビルド時分析エンジンによって、問題のあるコード パターンの開発者に対して、必要な他のコードを検出するように警告が与えられます。 コードには、他に含めるものをトリマーに指示する属性を使用して注釈が付けられます。 多くのリフレクション パターンは、[ソース ジェネレーター](https://github.com/dotnet/roslyn/blob/main/docs/features/source-generators.md)を使用して、ビルド時コード生成に置き換えることができます。

アプリケーションのトリミング モードは、`TrimMode` 設定で構成されます。 既定値は `copyused` で、参照されるアセンブリがアプリケーションとバンドルされます。 Blazor WebAssembly では、`link` 値が使用され、アセンブリ内の使用されていないコードがトリミングされます。 トリミング分析の警告により、完全な依存関係分析が不可能なコード パターンに関する情報が示されます。 これらの警告は、既定では非表示となり、フラグ `SuppressTrimAnalysisWarnings` を `false` に設定することで有効にすることができます。 使用可能なトリミング オプションの詳細については、「[トリミング オプション](trimming-options.md)」を参照してください。

> [!NOTE]
> トリミングは、.NET Core 3.1 および .NET 5.0 の実験的な機能です。 トリミングは、自己完結型で公開されるアプリケーション "_のみ_" で使用できます。

## <a name="prevent-assemblies-from-being-trimmed"></a>アセンブリがトリミングされないようにする

トリミング機能が参照の検出に失敗するシナリオがあります。 たとえば、アプリケーションまたはアプリケーションによって参照されるライブラリから、ランタイム アセンブリに対してリフレクションが使用されている場合、アセンブリは直接参照されません。 このような間接参照はトリミングに認識されず、ライブラリは発行フォルダーから除外されます。

コードからリフレクションを介して間接的にアセンブリを参照している場合は、`<TrimmerRootAssembly>` 設定を使用してアセンブリがトリミングされないようにすることができます。 次の例は、`System.Security` アセンブリという名前のアセンブリがトリミングされないようにする方法を示しています。

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="support-for-ssl-certificates"></a>SSL 証明書のサポート

ASP.NET Core アプリなどのお使いのアプリで SSL 証明書が読み込まれる場合、トリミング時に、SSL 証明書の読み込みを支援するトリミング アセンブリが確実に使用されないようにする必要があります。

ASP.NET Core 3.1 では、次を含むようにプロジェクト ファイルを更新します。

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>...</PropertyGroup>
  <!--Include the following for .aspnetcore 3.1-->
  <ItemGroup>
    <TrimmerRootAssembly Include="System.Net" />
    <TrimmerRootAssembly Include="System.Net.Security" />
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
  ...
</Project>
```

.Net 5.0 を使用している場合は、次を含むようにプロジェクト ファイルを更新します。

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
 <PropertyGroup>...</PropertyGroup>
 <!--Include the following for .net 5.0-->
 <ItemGroup>
    <TrimmerRootAssembly Include="System.Net.Security" />
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
  ...
</Project>
```

## <a name="trim-your-app---cli"></a>アプリをトリミングする - CLI

[dotnet publish](../tools/dotnet-publish.md) コマンドを使用してアプリケーションをトリミングします。 アプリを発行する場合、次のプロパティを設定します。

- 特定のランタイムの自己完結型アプリとして発行する: `-r win-x64`
- トリミングを有効にする: `/p:PublishTrimmed=true`

次の例では、Windows 用のアプリを自己完結型として発行し、出力をトリミングします。

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

次の例では、アグレッシブなトリミング モードでアプリを発行します。このモードでは、アセンブリ内の使用されていないコードがトリミングされ、トリマー警告が有効になります。

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</PropertyGroup>
```

詳細については、「[.NET Core CLI を使用して .NET Core アプリを発行する](deploy-with-cli.md)」を参照してください。

## <a name="trim-your-app---visual-studio"></a>アプリをトリミングする - Visual Studio

Visual Studio を使用すると、アプリケーションの発行方法を制御する再利用可能な発行プロファイルを作成できます。

01. **[ソリューション エクスプローラー]** ペインで、発行するプロジェクトを右クリックします。 **[発行]** を選択します。

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="右クリック メニューの [発行] オプションが強調表示されたソリューション エクスプローラー。":::

    発行プロファイルがまだない場合は、指示に従って作成し、ターゲットの種類として **[フォルダー]** を選択します。

01. **[編集]** を選択します。

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Visual Studio の発行プロファイルと [編集] ボタン":::

01. **[プロファイル設定]** ダイアログで、次のオプションを設定します。

    - **[配置モード]** を **[自己完結]** に設定します。
    - **[ターゲット ランタイム]** を発行先のプラットフォームに設定します。
    - **[未使用のアセンブリをトリミングする (プレビュー)]** を選択します。

    **[保存]** を選択して設定を保存し、 **[発行]** ダイアログに戻ります。

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="[配置モード]、[ターゲット ランタイム]、[未使用のアセンブリをトリミングする] オプションが強調表示されている [プロファイル設定] ダイアログ。":::

01. **[発行]** を選択してトリミングされたアプリを発行します。

詳細については、[Visual Studio を使用した .NET Core アプリの発行](deploy-with-vs.md)に関するページを参照してください。

## <a name="trim-your-app---visual-studio-for-mac"></a>アプリをトリミングする - Visual Studio for Mac

Visual Studio for Mac には、発行時にアプリをトリミングするオプションがありません。 「[アプリをトリミングする - CLI](#trim-your-app---cli)」セクションの手順に従って手動で発行する必要があります。 詳細については、「[.NET Core CLI を使用して .NET Core アプリを発行する](deploy-with-cli.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [.NET Core アプリケーションの配置](index.md)。
- [.NET Core CLI を使用して .NET Core アプリを発行する](deploy-with-cli.md)。
- [Visual Studio を使用して .NET Core アプリを発行する](deploy-with-vs.md)。
- [dotnet publish コマンド](../tools/dotnet-publish.md)。
