---
title: 依存関係の把握と更新
description: .NET Framework プロジェクトを .NET Core に移行するためには、その依存関係を .NET Core で機能するように更新する必要があります。 このセクションでは、大規模なアプリの移行を計画するために使用できるツールとアプローチについて説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 484691496d3691151fd3ca83ec776dbb31327c09
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122756"
---
# <a name="understand-and-update-dependencies"></a>依存関係の把握と更新

アプリの個々のプロジェクトを移行する順序を特定したら、次のステップとして、各プロジェクトの依存関係を把握し、必要に応じてそれらを更新します。 プラットフォームの依存関係に関しては、対象のアセンブリ上で [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) を実行し、生成された詳細な結果を調べるのが手始めとして最善の方法です。 このツールを、1 つ以上のターゲット プラットフォーム (.NET Core 3.1 や .NET Standard 2.0 など) を指定するように構成します。 結果では、各ターゲット プラットフォームに関する詳細が示されます。 図 3-4 に、このツールの出力の例を示します。

![.NET Portability Analyzer レポートの詳細](./media/Figure3-4.png)

**図 3-4** .NET Portability Analyzer レポートの詳細。

## <a name="update-class-library-dependencies"></a>クラス ライブラリの依存関係の更新

通常、大規模なアプリには複数のプロジェクトが含まれており、ASP.NET MVC Web プロジェクト以外のほとんどのプロジェクトはクラス ライブラリである可能性があります。 クラス ライブラリは、.NET プラットフォーム間の移植が最も難しい部類に入る (かつ、通常は再作成が必要になる) ASP.NET プロジェクトと比べると特に、移植が非常に簡単な傾向があります。

クラス ライブラリを .NET Core に移行するために、チームは [try-convert ツール](https://github.com/dotnet/try-convert)または [.NET Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)を検討できます。 これらのツールは .NET Framework プロジェクト ファイルを分析し、プロセス内で安全に実行できる変更をすべて行って、.NET Core プロジェクト ファイル形式への移行を試みます。 これらのツールは、ASP.NET プロジェクトで機能させるために手動の支援が必要な場合がありますが、通常はクラス ライブラリの移行のプロセスを迅速化するのに役立ちます。

try-convert ツールと Upgrade Assistant ツールは .NET Core コマンド ライン ツールとして展開されます。 これらは .NET Framework アプリで動作するように設計されているため、Windows 上でのみ実行できます。 try-convert をインストールするには、コマンド プロンプトから次のコマンドを実行します。

```dotnetcli
dotnet tool install -g try-convert
```

ツールを正常にインストールしたら、クラス ライブラリのプロジェクト ファイルが置かれているフォルダー内で `try-convert` を実行できます。

(try-convert のインストール後に) 次のコマンドを使用して、.NET Upgrade Assistant をインストールします。

```dotnetcli
dotnet tool install -g upgrade-assistant
```

プロジェクト ファイルが置かれているフォルダー内でコマンド `upgrade-assistant <project>` を使用して、このツールを実行します。

## <a name="update-nuget-package-dependencies"></a>NuGet パッケージの依存関係の更新

サードパーティの NuGet パッケージの使用状況を分析し、それらの中にまだ .NET Standard をサポートしていない (またはサポートしているが新しいバージョンでのみサポートしている) ものがあるかどうかを調べます。 最上位の依存関係が表示されるように、[Visual Studio のコンバーター ツールを使用して `<PackageReference>` 構文を使用するように NuGet パッケージを更新する](/nuget/consume-packages/migrate-packages-config-to-package-reference)と便利な場合があります。 次に、これらのパッケージの現在またはそれ以降のバージョンで .NET Core または .NET Standard がサポートされているかどうかを調べます。 この情報は、パッケージごとに [nuget.org] または Visual Studio 内で確認できます。

アプリで現在使用されているパッケージのバージョンに対するサポートが存在する場合は、問題ありません。 そうでない場合は、パッケージのより新しいバージョンに対するサポートがあるかどうかを確認し、アップグレードに何が関与するかを調べます。 現在使用しているバージョンとアップグレード先のバージョンとでパッケージのメジャー バージョンが変わる場合は特に、パッケージに重大な変更が含まれている可能性があります。

場合によっては、パッケージのどのバージョンも .NET Core で機能しないことがあります。 その場合、チームにはいくつかの選択肢があります。 引き続きその .NET Framework のバージョンに依存することは可能ですが、これには制限があります。 アプリは Windows 上でのみ実行され、チームは問題が発生する可能性がないかどうかを調べるために、パッケージのバイナリ上で Portability Analyzer を実行する必要があるかもしれません。 .NET Core で使用できない API を参照する .NET Framework パッケージが使用されている場合は、ランタイム例外が発生するため、チームが十分にテストする必要があります。 もう 1 つの選択肢は、別のパッケージを見つけるか、必要なパッケージがオープン ソースであれば .NET Standard または .NET Core 自体にアップグレードすることです。

## <a name="migrate-aspnet-mvc-projects"></a>ASP.NET MVC プロジェクトの移行

`System.Web` 名前空間と型は、.NET Core には存在しません。 依存関係を分析して `try-convert` などのツールを使用していると、ASP.NET MVC プロジェクトとその中の `System.Web` を参照するコードの自動移行に関して、ツールから多くの提案が提供されないことに気付くでしょう。 これらのプロジェクトについては、新しい ASP.NET Core Web プロジェクトで開始して、そのプロジェクトに手動で移行することが必要になります。

一般に、アプリのビジネス ロジックはできる限りそのユーザー インターフェイス レイヤー内に配置しないようにすることをお勧めします。 コントローラーとビューも小さく保つのが最善です。 このガイダンスに従っているアプリは、ASP.NET Web プロジェクト内に大量のロジックを含んでいるアプリよりも移植が簡単になります。 移植を検討しているアプリがあるが、まだそのプロセスを開始していない場合は、管理の際にこの点に留意してください。 ASP.NET MVC または Web API プロジェクトに含まれるコードの量を最小限に抑えるために費やした作業量によって、アプリを移植する際の手間を減らせるでしょう。

次の章では、ASP.NET MVC プロジェクトおよび Web API プロジェクトから ASP.NET Core プロジェクトに移行する方法について詳しく説明します。 前の章では、アプリ間の最大の相違点を列挙しました。 通常、いったん基本的なプロジェクトの構造が整えば、個々のコントローラーとビューを移行することは、特にそれらが主に Web の役割に重点を置いている場合は簡単です。

## <a name="references"></a>References

- [.NET Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)
- [try-convert ツール](https://github.com/dotnet/try-convert)
- [apiport ツール](https://github.com/microsoft/dotnet-apiport)

>[!div class="step-by-step"]
>[前へ](identify-migration-sequence.md)
>[次へ](strategies-migrating-in-production.md)
