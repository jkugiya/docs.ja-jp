---
title: 移行するプロジェクトの順序を確認する
description: 通常、大規模なアプリは新しいプラットフォームにすべて一度に移行されるのではなく、一連の小規模なステップに分けて移行されます。 ASP.NET MVC アプリを ASP.NET Core に移行するためのステップを計画する方法について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 34bcfbf4ea3941329419ba64253a2177247df7b8
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122912"
---
# <a name="identify-sequence-of-projects-to-migrate"></a>移行するプロジェクトの順序を確認する

複数のフロントエンド アプリを含むソリューションでは、アプリを 1 つずつ移行するのが最善の方法です。 たとえば、1 つのフロントエンド アプリとその依存関係のみを含むソリューションを作成して、必要な作業のスコープを簡単に特定できるようにします。 ソリューションは軽量であり、必要に応じて複数のソリューション内にプロジェクトを含めることができます。 移行時には、ソリューションを整理ツールとして活用できます。

移行する ASP.NET アプリを特定し、それに依存するプロジェクトを (理想的には 1 つのソリューション内に) 一緒に配置したら、次のステップとしてフレームワークと NuGet の依存関係を特定します。 すべての依存関係を特定したら、最もシンプルな移行のアプローチは "ボトムアップ" アプローチです。 このアプローチでは、最下位レベルの依存関係を最初に移行します。 その後、最終的にフロントエンド アプリのみが残るまで、次のレベルの依存関係を移行していきます。 図 3-1 に、1 つのアプリを構成するプロジェクトのセットの例を示します。 下位レベルのクラス ライブラリが一番下に、ASP.NET MVC プロジェクトが一番上にあります。

![プロジェクト依存関係](./media/Figure3-1.png)

**図 3-1.** プロジェクトの依存関係のグラフ。

1 つの特定のフロントエンド アプリ、1 つの ASP.NET MVC 5 / Web API 2 プロジェクトを選択します。 ソリューション内でその依存関係を特定し、完全な一覧ができるまでその依存関係をマップに書き出します。 図 3-1 に示したような図が、プロジェクトの依存関係をマップに書き出すときに役立つでしょう。 Visual Studio では、ご使用のエディションに応じて[ソリューションの依存関係図](/visualstudio/modeling/create-layer-diagrams-from-your-code)を生成できます。 [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) でも、依存関係図を生成できます。

図 3-2 は、[.NET Portability Analyzer の Visual Studio 拡張機能](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)のインストーラを示しています。

![.NET Portability Analyzer の拡張機能のインストール](./media/Figure3-2.png)

**図 3-2** .NET Portability Analyzer のインストーラ。

この拡張機能では、Visual Studio 2017 以降がサポートされています。 インストールしたら、図 3-3 に示すように **[分析]**  >  **[Portability Analyzer Settings]\(Portability Analyzer の設定\)** メニューからそれを構成します。

![.NET Portability Analyzer の拡張機能の構成](./media/Figure3-3.png)

**図 3-3** .NET Portability Analyzer の構成。

アナライザーにより、各アセンブリに関する詳細なレポートが生成されます。 このレポートは、

* 各プロジェクトと特定のターゲット フレームワーク (.NET Core 3.1 や .NET Standard 2.0 など) の互換性の状況を示します。
* 特定のプロジェクトを特定のターゲット フレームワークに移植するために必要な作業量をチームが評価するのに役立ちます。

この分析の詳細については、次のセクションで説明します。

プロジェクトとそれらの相互関係をマップに書き出したら、プロジェクトを移行する順序を決定できます。 最初は、依存関係のないプロジェクトから始めます。 その後は、それらのプロジェクトに依存するプロジェクトへと、ツリーの上に向かって作業を進めます。

図 3-1 に示した例では、*Contoso.Utils* プロジェクトから始めます。これは他のプロジェクトに依存していないからです。 次は *Contoso.Data* です。これは "Utils" にのみ依存しているからです。 続いて "BusinessLogic" ライブラリを移行し、最後にフロントエンドの ASP.NET "Web" プロジェクトを移行します。 この "ボトムアップ" アプローチは、すべてのプロジェクトの移行を完了すれば 1 つのユニットとして移行できる、比較的小規模で整然としたアプリに適しています。 より複雑な、またはコードの量が多い大規模なアプリは移行にもっと時間がかかる可能性があり、より段階的な戦略を検討することが必要な場合があります。

## <a name="unit-tests"></a>単体テスト

前の図には、単体テスト プロジェクトがありませんでした。 おそらくは、少なくとも、移植されるライブラリの既存の動作のいくつかを対象としたテストが存在するでしょう。

単体テストがある場合は、それらのプロジェクトを最初に変換するのが最善です。 今後も作業中のプロジェクトでの変更をテストすることをお勧めします。 .NET Core への移植では、コードベースに大きな変更が加えられるという点に注意してください。

MSTest、xUnit、NUnit はすべて .NET Core で動作します。 現在、アプリ用のテストがない場合は、システムの現在の動作を検証するいくつかの特性テストを構築することを検討してください。 その利点は、移行の完了後に、アプリの動作が変わっていないことを確認できることです。

## <a name="considerations-for-migrating-many-apps"></a>多数のアプリの移行に関する考慮事項

組織によっては、移行するアプリの数が多く、1 つずつ手作業で移行するのは必要なリソースが多すぎて不可能な場合があります。 そのような状況では、ある程度の自動化をお勧めします。 この章で示した手順は自動化が可能です。 プロジェクト ファイルの違いや共通パッケージの更新などの構造的な変更は、スクリプトによって適用することができます。 これらのスクリプトは、より多くのプロジェクトで繰り返し実行する間に改善できます。 実行のたびに、各プロジェクトでどのような手動のステップが必要かを確認します。 それらの手動のステップを可能な限り自動化します。 このアプローチを使用すると、組織は時間の経過と共にアプリの移行をより迅速かつ効率的に行えるようになり、各ステップで自動化のサポートが強化されます。

このアプローチの使用方法の概要を、[Mastercard の Lizzy Gallagher による dotNetConf のプレゼンテーション](https://www.youtube.com/watch?v=C-2haqb60No)でご覧いただけます。 このプレゼンテーションでは、次の 5 つのフェーズが使用されています。

- サードパーティの NuGet の依存関係を移行する
- 新しい *.csproj* ファイル形式を使用するようにアプリを移行する
- 内部の NuGet 依存関係を .NET Standard に更新する
- (.NET Framework をターゲットとする) ASP.NET Core にアプリを移行する
- すべてのアプリを .NET Core 3.1 をターゲットにするように更新する

大規模なアプリのスイートを自動化するときは、それらが一貫したコーディング ガイドラインとプロジェクト編成に従っていると非常に役立ちます。 自動化の作業を効率化できるかどうかは、この一貫性にかかっています。 プロジェクト ファイルの解析と移行に加えて、一般的なコード パターンも自動的に移行できます。 一部のコード パターンの例では、コントローラー アクションの宣言方法やそれらが結果を返す方法に違いがあります。

たとえば、移行スクリプトで、*Controller.cs* に一致するファイルで次のいずれかのパターンに一致するコードの行を検索するとします。

```csharp
   return new HttpStatusCodeResult(200);
   // or
   return new HttpStatusCodeResult(HttpStatusCode.OK);
```

ASP.NET Core では、上記の行のどちらも以下で置き換えることができます。

```csharp
    return Ok();
```

## <a name="summary"></a>まとめ

大規模な .NET Framework アプリを .NET Core に移行するための最善のアプローチは次のとおりです。

1. プロジェクトの依存関係を特定します。
1. 各プロジェクトを移植するために何が必要かを分析します。
1. 下から始めて、上方向へと進めます。

.NET Portability Analyzer を使用して、既存のライブラリとターゲット プラットフォームの互換性の状況を調べることができます。 自動テストを使用すると、アプリの移植時に破壊的変更が行われていないことを確認するのに役立ちます。 このようなテスト プロジェクトは、最初に移植すべきプロジェクトの 1 つです。

## <a name="references"></a>References

- [.NET Framework から .NET Core への移植](../../core/porting/index.md)
- [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md)
- [Channel 9: .NET Portability Analyzer の概要 (動画)](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer)
- [2 年間で 200 のアプリ: .NET Core への大規模な移行 (動画)](https://www.youtube.com/watch?v=C-2haqb60No)

>[!div class="step-by-step"]
>[前へ](migrate-large-solutions.md)
>[次へ](understand-update-dependencies.md)
