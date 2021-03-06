---
title: 依存関係の把握と更新
description: .NET Framework プロジェクトを .NET Core に移行するには、.NET Core で動作するようにその依存関係を更新する必要があります。 このセクションでは、大規模なアプリの移行を計画するために使用できるツールと方法について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: afad77860099e4737b5270dc32fc20c2025e63dd
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401345"
---
# <a name="understand-and-update-dependencies"></a>依存関係の把握と更新

アプリの個々のプロジェクトを移行する順序を特定したら、次の手順として、各プロジェクトの依存関係を理解し、必要に応じて更新します。 プラットフォームの依存関係については、まず、対象のアセンブリで [.Net 移植性アナライザー](../../standard/analyzers/portability-analyzer.md) を実行し、生成された詳細な結果を確認することをお勧めします。 このツールを構成して、.NET Core 3.1 や .NET Standard 2.0 などの1つ以上のターゲットプラットフォームを指定します。 結果には、対象となる各プラットフォームの詳細が表示されます。 図3-4 は、ツールの出力の例を示しています。

![.NET 移植性アナライザーレポートの詳細](./media/Figure3-4.png)

**図 3-4.** .NET 移植性アナライザーレポートの詳細。

## <a name="update-class-library-dependencies"></a>クラスライブラリの依存関係の更新

通常、大規模なアプリには複数のプロジェクトが含まれており、ASP.NET MVC web プロジェクト以外のほとんどのプロジェクトはクラスライブラリである可能性があります。 クラスライブラリは、.NET プラットフォーム間で最も簡単に移植できる傾向があります。特に、ASP.NET プロジェクトの場合は、最も困難なもの (通常は再作成が必要) です。

チームでは、クラスライブラリを .NET Core に移行するための [変換ツール](https://github.com/dotnet/try-convert) または [.net Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant) を検討できます。 これらのツールは、.NET Framework プロジェクトファイルを分析し、.NET Core プロジェクトファイル形式への移行を試行して、プロセスで安全に実行できるように変更を行います。 これらのツールでは、ASP.NET プロジェクトを操作するために手動の支援が必要になる場合がありますが、通常はクラスライブラリを移行するプロセスの速度を向上させることができます。

Convert および Upgrade Assistant ツールは、.NET Core コマンドラインツールとしてデプロイされています。 これらは、.NET Framework アプリで動作するように設計されているため、Windows 上でのみ動作します。 コマンドプロンプトから次のコマンドを実行して、try 変換をインストールできます。

```dotnetcli
dotnet tool install -g try-convert
```

ツールを正常にインストールしたら、 `try-convert` クラスライブラリのプロジェクトファイルが配置されているフォルダーでを実行できます。

次のコマンドを使用して .NET Upgrade Assistant をインストールします (試し変換をインストールした後)。

```dotnetcli
dotnet tool install -g upgrade-assistant
```

`upgrade-assistant <project>`プロジェクトファイルが配置されているフォルダー内のコマンドを使用して、ツールを実行します。

## <a name="update-nuget-package-dependencies"></a>NuGet パッケージの依存関係の更新

サードパーティの NuGet パッケージの使用を分析し、そのうちのいずれかがまだ .NET Standard をサポートしていないかどうかを判断します (または、新しいバージョンでのみサポートします)。 最上位レベルの依存関係が表示されるように、 [ `<PackageReference>` Visual Studio のコンバーターツールを使用して構文を使用するように NuGet パッケージを更新](/nuget/consume-packages/migrate-packages-config-to-package-reference)すると便利な場合があります。 次に、これらのパッケージの現在またはそれ以降のバージョンで .NET Core または .NET Standard がサポートされているかどうかを確認します。 この情報は、パッケージごとに [nuget.org] または Visual Studio 内で確認できます。

アプリが現在使用しているパッケージのバージョンを使用してサポートが存在する場合は、 そうでない場合は、より新しいバージョンのパッケージがサポートされているかどうかを確認し、アップグレードに関連する内容を調査します。 パッケージに重大な変更が加えられている可能性があります。特に、パッケージのメジャーバージョンが現在使用しているバージョンとアップグレードするバージョンの間で変更されている場合です。

場合によっては、特定のパッケージのバージョンが .NET Core で動作しないことがあります。 その場合、チームにはいくつかのオプションがあります。 .NET Framework のバージョンによっては継続できますが、これには制限があります。 アプリは Windows 上でのみ実行され、チームはパッケージのバイナリで移植性アナライザーを実行して、発生する可能性のある問題があるかどうかを確認することができます。 もちろん、チームは十分にテストする必要があります。 もう1つの方法は、別のパッケージを検索する方法です。必要なパッケージがオープンソースの場合は、それを .NET Standard または .NET Core にアップグレードします。

## <a name="migrate-aspnet-mvc-projects"></a>ASP.NET MVC プロジェクトの移行

`System.Web`名前空間と型は、.Net Core には存在しません。 依存関係を分析したり、などのツールを使用したりする場合 `try-convert` 、ASP.NET MVC プロジェクトの自動移行に関する多くの提案と、を参照するコードが提供されていないことがわかり `System.Web` ます。 これらのプロジェクトでは、最初に新しい ASP.NET Core web プロジェクトを作成し、このプロジェクトにファイルを手動で移行する必要があります。

一般に、アプリのビジネスロジックがユーザーインターフェイスレイヤーに存在する量を最小限に抑えることをお勧めします。 また、コントローラーとビューを小さくしておくことをお勧めします。 このガイダンスに従っているアプリは、ASP.NET web プロジェクトで大量のロジックを使用しているよりも簡単に移植できます。 移植を検討しているものの、まだプロセスを開始していないアプリがある場合は、維持するときにこの点に留意してください。 ASP.NET MVC または Web API プロジェクト内のコードの量を最小限に抑えるために必要な作業は、アプリの移植に時間がかかる場合に、作業が少なくなる可能性があります。

次の章では、調査プロジェクト ASP.NET Core に ASP.NET MVC プロジェクトと Web API プロジェクトを移行する方法の詳細について説明します。 前の章では、アプリ間の最大の違いを説明しました。 基本的なプロジェクトの構造が整ったら、通常、個々のコントローラーとビューを移行するのは簡単です。特に、主に web の役割を重視している場合は、

## <a name="references"></a>関連項目

- [.NET Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)
- [try 変換ツール](https://github.com/dotnet/try-convert)
- [apiport ツール](https://github.com/microsoft/dotnet-apiport)

>[!div class="step-by-step"]
>[前へ](identify-migration-sequence.md)
>[次へ](strategies-migrating-in-production.md)
