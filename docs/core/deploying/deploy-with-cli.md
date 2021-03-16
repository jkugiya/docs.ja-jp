---
title: .NET CLI を使用してアプリを公開する
description: .NET CLI コマンドを使用して .NET アプリケーションを公開する方法について説明します。
author: adegeo
ms.author: adegeo
ms.date: 02/05/2021
dev_langs:
- csharp
- vb
ms.openlocfilehash: d2695b1f271e57bb44ed3f94acbbe17b830fdd60
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255693"
---
# <a name="publish-net-apps-with-the-net-cli"></a>.NET CLI を使用した .NET アプリの発行

この記事では、コマンド ラインから .NET アプリケーションを公開する方法を説明します。 .NET には、アプリケーションを公開する方法が 3 つ用意されています。 フレームワークに依存する展開を使用すると、ローカル環境にインストールされている .NET ランタイムを使用するクロスプラットフォームの .dll ファイルが生成されます。 フレームワークに依存する実行可能ファイルを使用すると、ローカル環境にインストールされている .NET ランタイムを使用するプラットフォーム固有の実行可能ファイルが生成されます。 自己完結型の実行可能ファイルを使用すると、プラットフォーム固有の実行可能ファイルが生成されて、.NET ランタイムのローカル コピーが組み込まれます。

これらの公開モードの概要については、[.NET アプリケーションの展開](index.md)に関するページを参照してください。

CLI の使用方法について簡単にわかるヘルプをお探しですか。 次の表では、アプリの公開方法についての例を示します。 ターゲット フレームワークは、`-f <TFM>` パラメーターを使用するか、プロジェクト ファイルを編集して、指定することができます。 詳細については、「[公開の基礎](#publishing-basics)」をご覧ください。

| 公開モード                   | SDK バージョン | command                                                     |
|--------------------------------|-------------|-------------------------------------------------------------|
| [フレームワークに依存する展開](#framework-dependent-deployment) | 2.1         | `dotnet publish -c Release`                                 |
|                                | 3.1         | `dotnet publish -c Release -p:UseAppHost=false`             |
|                                | 5.0         | `dotnet publish -c Release -p:UseAppHost=false`             |
| [フレームワークに依存する実行可能ファイル](#framework-dependent-executable) | 3.1         | `dotnet publish -c Release -r <RID> --self-contained false`<br>`dotnet publish -c Release` |
|                                | 5.0         | `dotnet publish -c Release -r <RID> --self-contained false`<br>`dotnet publish -c Release` |
| [自己完結型の展開](#self-contained-deployment)      | 2.1         | `dotnet publish -c Release -r <RID> --self-contained true`  |
|                                | 3.1         | `dotnet publish -c Release -r <RID> --self-contained true`  |
|                                | 5.0         | `dotnet publish -c Release -r <RID> --self-contained true`  |

\* **SDK バージョン 3.1** 以降を使用する場合、基本的な `dotnet publish` コマンドを実行するときの既定の公開モードは、フレームワークに依存する実行可能ファイルです。

> [!NOTE]
> `-c Release` パラメーターは必要ありません。 アプリの **リリース** ビルドを公開することを明示するために提供されています。

## <a name="publishing-basics"></a>公開の基礎

アプリを公開するときは、プロジェクト ファイルの設定 `<TargetFramework>` で既定のターゲット フレームワークを指定します。 任意の有効な[ターゲット フレームワーク モニカー (TFM)](../../standard/frameworks.md) にターゲット フレームワークを変更できます。 たとえば、プロジェクトで `<TargetFramework>netcoreapp2.1</TargetFramework>` を使用している場合は、.NET Core 2.1 をターゲットとするバイナリが作成されます。 この設定で指定されている TFM が、[`dotnet publish`](../tools/dotnet-publish.md) コマンドで使用される既定のターゲットになります。

複数のフレームワークをターゲットにしたい場合は、セミコロンで区切ることにより、`<TargetFrameworks>` の設定で複数の TFM 値を設定できます。 アプリをビルドするときは、ターゲット フレームワークごとにビルドが生成されます。 ただし、アプリを公開するときは、`dotnet publish -f <TFM>` コマンドでターゲット フレームワークを指定する必要があります。

他の値を設定しない限り、[`dotnet publish`](../tools/dotnet-publish.md) コマンドの出力ディレクトリは `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` です。 `-c` パラメーターで変更しない限り、**BUILD-CONFIGURATION** の既定のモードは **Debug** です。 たとえば、`dotnet publish -c Release -f netcoreapp2.1` と指定すると、`./bin/Release/netcoreapp2.1/publish/` に公開されます。

.NET Core SDK 3.1 以降を使用している場合、既定の公開モードはフレームワークに依存する "_実行可能ファイル_" です。

.NET Core SDK 2.1 を使用している場合、既定の公開モードはフレームワークに依存する "_展開_" です。

### <a name="native-dependencies"></a>ネイティブの依存関係

アプリにネイティブの依存関係がある場合、別のオペレーティング システムではアプリが実行されない可能性があります。 たとえば、ネイティブの Windows API を使用しているアプリは、macOS または Linux では実行されません。 プラットフォーム固有のコードを提供し、プラットフォームごとに実行可能ファイルをコンパイルする必要があります。

また、参照しているライブラリにネイティブの依存関係がある場合、すべてのプラットフォームではアプリを実行できない可能性があることも考慮してください。 ただし、参照している NuGet パッケージには、必要なネイティブの依存関係を処理するためにプラットフォーム固有のバージョンが含まれている可能性があります。

ネイティブの依存関係があるアプリを配布するときは、`dotnet publish -r <RID>` スイッチを使用して、公開対象のターゲット プラットフォームを指定することが必要な場合があります。 ランタイム識別子の一覧については、[ランタイム識別子 (RID) のカタログ](../rid-catalog.md)に関する記事をご覧ください。

プラットフォーム固有のバイナリの詳細については、「[フレームワークに依存する実行可能ファイル](#framework-dependent-executable)」および「[自己完結型の展開](#self-contained-deployment)」セクションをご覧ください。

## <a name="sample-app"></a>サンプル アプリ

次のアプリを使用して、公開コマンドを確認できます。 ターミナルで次のコマンドを実行すると、アプリが作成されます。

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

コンソール テンプレートによって生成される `Program.cs` または `Program.vb` ファイルを、次のように変更する必要があります。

```csharp
using System;

namespace apptest1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"));
        }
    }
}
```

```vb
Module Program
    Sub Main(args As String())
        Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"))
    End Sub
End Module
```

アプリを実行すると ([`dotnet run`](../tools/dotnet-run.md))、次の出力が表示されます。

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a>フレームワークに依存する展開

.NET Core 2.1 SDK の CLI の場合、フレームワークに依存する展開 (FDD) が、基本的な `dotnet publish` コマンドの既定のモードです。 それより新しい SDK では、[フレームワークに依存する実行可能ファイル](#framework-dependent-executable)が既定値です。

FDD としてアプリを公開すると、`./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` フォルダーに`<PROJECT-NAME>.dll` ファイルが作成されます。 アプリを実行するには、出力フォルダーに移動して、`dotnet <PROJECT-NAME>.dll` コマンドを使用します。

アプリは、特定のバージョンの .NET をターゲットにするように構成されます。 アプリが実行されるすべてのコンピューターには、そのターゲットの .NET ランタイムが存在する必要があります。 たとえば、アプリのターゲットが .NET Core 3.1 である場合、アプリを実行するコンピューターには、.NET Core 3.1 ランタイムがインストールされている必要があります。 「[公開の基礎](#publishing-basics)」セクションで説明したように、プロジェクト ファイルを編集することで、既定のターゲット フレームワークを変更したり、複数のフレームワークをターゲットにしたりできます。

FDD を公開すると、アプリが実行されるシステムで使用できる最新の .NET セキュリティ更新プログラムまで自動的にロールフォワードするアプリが作成されます。 コンパイル時のバージョンのバインドの詳細については、「[使用する .NET のバージョンを選択する](../versions/selection.md#framework-dependent-apps-roll-forward)」を参照してください。

| 公開モード                   | SDK バージョン | コマンド                                                     |
|--------------------------------|-------------|-------------------------------------------------------------|
| フレームワークに依存する展開 | 2.1         | `dotnet publish -c Release`                                 |
|                                | 3.1         | `dotnet publish -c Release -p:UseAppHost=false`             |
|                                | 5.0         | `dotnet publish -c Release -p:UseAppHost=false`             |

## <a name="framework-dependent-executable"></a>フレームワークに依存する実行可能ファイル

.NET 5 (および .NET Core 3.1) SDK の CLI の場合は、フレームワークに依存する実行可能ファイル (FDE) が、基本的な `dotnet publish` コマンドの既定のモードです。 現在のオペレーティング システムをターゲットにする限り、他のパラメーターを指定する必要はありません。

このモードでは、クロスプラットフォーム アプリをホストするために、プラットフォームに固有の実行可能なホストが作成されます。 FDD では `dotnet` コマンドの形式でホストを要求するので、このモードは FDD と似ています。 ホストの実行可能ファイル名はプラットフォームごとに異なり、`<PROJECT-FILE>.exe` のような名前になります。 この実行可能ファイルは、`dotnet <PROJECT-FILE>.dll` を呼び出す (アプリの実行手段として引き続き使用可能) 代わりに、直接実行することができます。

アプリは、特定のバージョンの .NET をターゲットにするように構成されます。 アプリが実行されるすべてのコンピューターには、そのターゲットの .NET ランタイムが存在する必要があります。 たとえば、アプリのターゲットが .NET Core 3.1 である場合、アプリを実行するコンピューターには、.NET Core 3.1 ランタイムがインストールされている必要があります。 「[公開の基礎](#publishing-basics)」セクションで説明したように、プロジェクト ファイルを編集することで、既定のターゲット フレームワークを変更したり、複数のフレームワークをターゲットにしたりできます。

FDE を公開すると、アプリが実行されるシステムで使用できる最新の .NET セキュリティ更新プログラムまで自動的にロールフォワードするアプリが作成されます。 コンパイル時のバージョンのバインドの詳細については、「[使用する .NET のバージョンを選択する](../versions/selection.md#framework-dependent-apps-roll-forward)」を参照してください。

.NET 2.1 の場合は、`dotnet publish` コマンドで次のスイッチを使用して、FDE を公開する必要があります。

- `-r <RID>` このスイッチでは、識別子 (RID) を使用してターゲット プラットフォームを指定します。 ランタイム識別子の一覧については、[ランタイム識別子 (RID) のカタログ](../rid-catalog.md)に関する記事をご覧ください。

- `--self-contained false` このスイッチは、自己完結型の展開 (SCD) を作成する `-r` スイッチの既定の動作を無効にします。 このスイッチは、FDE を作成します。

| 公開モード                   | SDK バージョン | コマンド                                                     |
|--------------------------------|-------------|-------------------------------------------------------------|
| フレームワークに依存する実行可能ファイル | 3.1         | `dotnet publish -c Release -r <RID> --self-contained false`<br>`dotnet publish -c Release` |
|                                | 5.0         | `dotnet publish -c Release -r <RID> --self-contained false`<br>`dotnet publish -c Release` |

`-r` スイッチを使用すると常に、出力フォルダーのパスが `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/` に変わります

[アプリの例](#sample-app)を使用する場合は、`dotnet publish -f net5.0 -r win10-x64 --self-contained false` を実行します。 このコマンドでは、実行可能ファイル `./bin/Debug/net5.0/win10-x64/publish/apptest1.exe` が作成されます

> [!NOTE]
> **グローバリゼーション インバリアント モード** を有効にすることで、展開の合計サイズを小さくすることができます。 このモードは、全世界を意識するものではなく、[インバリアント カルチャ](xref:System.Globalization.CultureInfo.InvariantCulture)の書式設定規則、大文字/小文字の区別規則、文字列比較、並べ替え順序を使用できるアプリケーションにとって便利です。 **グローバリゼーション インバリアント モード** の詳細と、それを有効にする方法については、[.NET のグローバリゼーション インバリアント モード](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)に関するページを参照してください。

## <a name="self-contained-deployment"></a>自己完結型の展開

自己完結型の展開 (SCD) を公開すると、.NET SDK によってプラットフォーム固有の実行可能ファイルが作成されます。 SCD の公開には、アプリの実行に必要なすべての .NET ファイルが含まれますが、[.NET のネイティブの依存関係](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)は含まれません。 これらの依存関係は、アプリを実行する前に、システムに存在している必要があります。

SCD の公開で作成されるアプリでは、使用可能な最新の .NET セキュリティ更新プログラムへのロールフォワードは行われません。 コンパイル時のバージョンのバインドの詳細については、「[使用する .NET のバージョンを選択する](../versions/selection.md#self-contained-deployments-include-the-selected-runtime)」を参照してください。

`dotnet publish` コマンドで次のスイッチを使用して、SCD を公開する必要があります。

- `-r <RID>` このスイッチでは、識別子 (RID) を使用してターゲット プラットフォームを指定します。 ランタイム識別子の一覧については、[ランタイム識別子 (RID) のカタログ](../rid-catalog.md)に関する記事をご覧ください。

- `--self-contained true` このスイッチでは、SCD として実行可能ファイルを作成するよう .NET Core SDK に指示されます。

| 公開モード                   | SDK バージョン | コマンド                                                     |
|--------------------------------|-------------|-------------------------------------------------------------|
| 自己完結型の展開      | 2.1         | `dotnet publish -c Release -r <RID> --self-contained true`  |
|                                | 3.1         | `dotnet publish -c Release -r <RID> --self-contained true`  |
|                                | 5.0         | `dotnet publish -c Release -r <RID> --self-contained true`  |

> [!NOTE]
> **グローバリゼーション インバリアント モード** を有効にすることで、展開の合計サイズを小さくすることができます。 このモードは、全世界を意識するものではなく、[インバリアント カルチャ](xref:System.Globalization.CultureInfo.InvariantCulture)の書式設定規則、大文字/小文字の区別規則、文字列比較、並べ替え順序を使用できるアプリケーションにとって便利です。 **グローバリゼーション インバリアント モード** の詳細と、それを有効にする方法については、「[.NET Core Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)」(.NET Core のグローバリゼーション インバリアント モード) を参照してください。

## <a name="see-also"></a>関連項目

- [.NET アプリケーションの展開の概要](index.md)
- [.NET ランタイム識別子 (RID) カタログ](../rid-catalog.md)
