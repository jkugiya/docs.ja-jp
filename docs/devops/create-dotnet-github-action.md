---
title: 'チュートリアル: .NET を使用して GitHub アクションを作成する'
description: コンテナー化された .NET アプリを使用して GitHub アクションを作成する方法について説明します。
author: IEvangelist
ms.author: dapine
ms.date: 04/01/2021
ms.topic: tutorial
ms.openlocfilehash: dbeb5642ae8964495a10e5025dadf3100a1dd10b
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231160"
---
# <a name="tutorial-create-a-github-action-with-net"></a>チュートリアル: .NET を使用して GitHub アクションを作成する

GitHub アクションとして使用できる .NET アプリを作成する方法について説明します。 [GitHub Actions](https://github.com/features/actions) により、ワークフローの自動化と構成が可能になります。 GitHub Actions を使用すると、GitHub からソース コードをビルド、テスト、デプロイできます。 さらに、アクションによって、プログラムで問題を操作したり、プル要求を作成したり、コード レビューを実行したり、ブランチを管理したりする機能が公開されます。 GitHub Actions を使用した継続的インテグレーションの詳細については、[.NET のビルドとテスト](https://docs.github.com/actions/guides/building-and-testing-net)に関するページを参照してください。

このチュートリアルでは、次の作業を行う方法について説明します。

> [!div class="checklist"]
>
> - .NET アプリを GitHub Actions 用に準備する
> - アクションの入力と出力を定義する
> - ワークフローを構成する

## <a name="prerequisites"></a>前提条件

- [GitHub アカウント](https://github.com/join)
- [.NET 5.0 SDK 以降](https://dotnet.microsoft.com/download/dotnet)
- .NET 統合開発環境 (IDE)
  - [Visual Studio IDE](https://visualstudio.microsoft.com) を自由に使用可能

## <a name="the-intent-of-the-app"></a>アプリの意図

このチュートリアルのアプリでは、次の操作を行うことによってコード メトリック分析を実行します。

- *\*.csproj* および *\*.vbproj* プロジェクト ファイルのスキャンと検出。
- これらのプロジェクト内の検出されたソース コードの次の点に関する分析。

  - サイクロマティック複雑度
  - 保守容易性指数
  - 継承の深さ
  - クラス結合
  - ソース コードの行数
  - 実行可能コードの見積もられた行数

- *CODE_METRICS.md* ファイルの作成 (または更新)。

このアプリは、*CODE_METRICS.md* ファイルの変更によりプル要求を作成する役割を果たし "*ません*"。 これらの変更は、[ワークフローの構成](#workflow-composition)の一部として管理されます。

このチュートリアルでのソース コードの参照には、簡潔にするために省略されたアプリの部分が含まれています。 完全なアプリ コードは、[GitHub で入手できます](https://github.com/dotnet/samples/tree/main/github-actions/DotNet.GitHubAction)。

### <a name="explore-the-app"></a>アプリを探索する

.NET コンソール アプリでは、[`CommandLineParser` NuGet](https://www.nuget.org/packages/CommandLineParser/) パッケージを使用して引数を `ActionInputs` オブジェクトに解析します。

:::code language="csharp" source="snippets/DotNet.GitHubAction/ActionInputs.cs":::

前のアクション入力クラスでは、このアプリを正常に実行するために必要ないくつかの入力を定義します。 コンストラクターでは、`"GREETINGS"` 環境変数の値を書き込みます (この値が現在の実行環境で使用可能な場合)。 `Name` および `Branch` プロパティが解析され、`"/"` で区切られた文字列の最後のセグメントから割り当てられます。

定義されたアクション入力クラスを使用して、*Program.cs* ファイルに焦点を絞ります。

:::code language="csharp" source="snippets/DotNet.GitHubAction/Program.cs":::

`Program` ファイルは、簡潔にするために簡略化されています。完全なサンプル ソースを調べるには、[*Program.cs*](https://github.com/dotnet/samples/blob/main/github-actions/DotNet.GitHubAction/DotNet.GitHubAction/Program.cs) を参照してください。 ここに表示されているしくみは、次のものを使用するために必要な定型コードを示しています。

- [最上位レベルのステートメント](../csharp/whats-new/tutorials/top-level-statements.md)
- [汎用ホスト](../core/extensions/generic-host.md)
- [依存関係の挿入](../core/extensions/dependency-injection.md)

外部のプロジェクトまたはパッケージ参照を使用して、依存関係の挿入に登録できます。 `Get<TService>` は、`IHost` インスタンスを必要とする静的ローカル関数であり、必要なサービスを解決するために使用されます。 `CommandLine.Parser.Default` シングルトンでは、このアプリは `args` から `parser` インスタンスを取得します。 これらの引数を解析できない場合、このアプリは 0 以外の終了コードで終了します。 詳細については、[アクションの終了コードの設定](https://docs.github.com/actions/creating-actions/setting-exit-codes-for-actions)に関するページを参照してください。

引数が正常に解析された場合、このアプリは、必要な入力で正しく呼び出されました。 この場合は、主要な機能 `StartAnalysisAsync` への呼び出しが行われます。

出力値を書き込むには、[GitHub Actions: 出力パラメーターの設定](https://docs.github.com/actions/reference/workflow-commands-for-github-actions#setting-an-output-parameter)によって認識される形式に従う必要があります。

## <a name="prepare-the-net-app-for-github-actions"></a>.NET アプリを GitHub Actions 用に準備する

GitHub Actions では、アプリ開発として次の 2 つのバリエーションをサポートしています。

- JavaScript (オプションで [TypeScript](https://www.typescriptlang.org))
- Docker コンテナー ([Docker](https://docs.github.com/actions/creating-actions/creating-a-docker-container-action) 上で実行される任意のアプリ)

.NET は GitHub Actions でネイティブにサポートされ "*いない*" ため、.NET アプリをコンテナー化する必要があります。 詳細については、[.NET アプリのコンテナー化](../core/docker/build-container.md)に関するページを参照してください。

### <a name="the-dockerfile"></a>Dockerfile

[*Dockerfile*](https://docs.docker.com/engine/reference/builder) は、イメージをビルドするための一連の手順です。 .NET アプリケーションの場合、*Dockerfile* は通常、ソリューション ファイルの隣にあるディレクトリのルートに存在します。

:::code language="dockerfile" source="snippets/Dockerfile" highlight="23":::

> [!NOTE]
> このチュートリアルの .NET アプリは、その機能の一部として .NET SDK に依存しているため、強調表示されている行によって .NET SDK がビルド出力で改めて再階層化されます。 その機能の一部として .NET SDK を必要と "***しない***" アプリケーションの場合は、代わりに .NET ランタイムのみに依存します。 これにより、イメージのサイズが大幅に削減されます。
>
> ```dockerfile
> FROM mcr.microsoft.com/dotnet/runtime:5.0
> ```

前の *Dockerfile* のステップには、次のものが含まれます。

- `mcr.microsoft.com/dotnet/sdk:5.0` の基本イメージのエイリアス `build-env` としての設定。
- コンテンツのコピーと .NET アプリの発行。
  - このアプリは、[`dotnet publish`](../core/tools/dotnet-publish.md) コマンドを使用して発行されます。
- コンテナーへのラベルの適用。
- `mcr.microsoft.com/dotnet/sdk:5.0` の .NET SDK イメージの再階層化。
- 発行されたビルド出力の `build-env` からのコピー。
- [`dotnet /DotNet.GitHubAction.dll`](../core/tools/dotnet.md) に委任されるエントリ ポイントの定義。

> [!TIP]
> `mcr.microsoft.com` の MCR は "Microsoft Container Registry" を表し、公式の Docker Hub の Microsoft のシンジケート化されたコンテナー カタログです。 詳細については、[Microsoft によるコンテナー カタログのシンジケート化](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)に関するページを参照してください。

## <a name="define-action-inputs-and-outputs"></a>アクションの入力と出力を定義する

「[アプリを探索する](#explore-the-app)」のセクションでは、`ActionInputs` クラスについて学習しました。 このオブジェクトは、GitHub アクションの入力を表します。 GitHub でリポジトリが GitHub アクションであることを認識できるようにするには、そのリポジトリのルートに *action.yml* ファイルが存在する必要があります。

:::code language="yml" source="snippets/action.yml":::

前の *action.yml* ファイルでは、次のものを定義します。

- GitHub アクションの `name` と `description`。
- `branding`。これは、アクションをより一意に識別しやすくするために [GitHub Marketplace](https://github.com/marketplace?type=actions) で使用されます。
- `inputs`。これは、`ActionInputs` クラスに 1 対 1 でマップします。
- `outputs`。これは、`Program` で[ワークフローの構成](#workflow-composition)に書き込まれ、その一部として使用されます。
- `runs` ノード。これは、そのアプリが `docker` アプリケーションであり、それにどのような引数を渡すかを GitHub に通知します。

詳細については、「[GitHub Actions のメタデータ構文](https://docs.github.com/actions/creating-actions/metadata-syntax-for-github-actions)」を参照してください。

## <a name="workflow-composition"></a>ワークフローの構成

[.NET アプリがコンテナー化](#prepare-the-net-app-for-github-actions)され、[アクションの入力と出力](#define-action-inputs-and-outputs)が定義されると、アクションを使用する準備が整いました。 GitHub Actions は、使用するために GitHub Marketplace で発行する必要は "*ありません*"。 ワークフローは、リポジトリの *.github/workflows* ディレクトリで YAML ファイルとして定義されます。

:::code language="yml" source="snippets/workflow.yml":::

> [!IMPORTANT]
> コンテナー化された GitHub Actions の場合は、`runs-on: ubuntu-latest` を使用する必要があります。 詳細については、[ワークフロー構文`jobs.<job_id>.runs-on`](https://docs.github.com/actions/reference/workflow-syntax-for-github-actions#jobsjob_idruns-on)に関するページを参照してください。

前のワークフロー YAML ファイルでは、次の 3 つのプライマリ ノードを定義します。

- ワークフローの `name`。 この名前はまた、[ワークフロー状態バッジ](https://docs.github.com/actions/managing-workflow-runs/adding-a-workflow-status-badge)を作成するときに使用される名前でもあります。
- `on` ノードは、アクションがいつ、どのようにトリガーされるかを定義します。
- `jobs` ノードは、さまざまなジョブと、各ジョブ内のステップの概要を示します。 個々のステップで GitHub Actions を使用します。

詳細については、[最初のワークフローの作成](https://docs.github.com/actions/quickstart#creating-your-first-workflow)に関するページを参照してください。

`steps` ノードに焦点を絞ると、構成がよりわかりやすくなります。

:::code language="yml" source="snippets/workflow.yml" range="22-47":::

`jobs/steps` は、*ワークフローの構成* を表します。 ステップは、それがシーケンシャルで、通信機能を持ち、かつ構成可能であるように調整されます。 ステップを表すさまざまな GitHub Actions (それぞれに入力と出力があります) を使用してワークフローを構成できます。

前のステップでは、次のことを観察できます。

1. リポジトリが[チェックアウト](https://github.com/actions/checkout)されます。
1. [手動で実行](https://github.blog/changelog/2020-07-06-github-actions-manual-triggers-with-workflow_dispatch)されると、メッセージがワークフロー ログに出力されます。
1. `dotnet-code-metrics` として識別されたステップ:

    - `uses: dotnet/samples/github-actions/DotNet.GitHubAction@main` は、このチュートリアルのコンテナー化された .NET アプリの場所です。
    - `env` は、このアプリの実行で出力される環境変数 `"GREETING"` を作成します。
    - `with` は、必要な各アクション入力を指定します。

1. `dotnet-code-metrics` ステップで `true` の値を持つ `updated-metrics` の出力パラメーターが指定されると、`Create pull request` という名前の条件付きステップが実行されます。

> [!IMPORTANT]
> GitHub では、[暗号化されたシークレット](https://docs.github.com/actions/reference/encrypted-secrets)の作成が許可されます。 シークレットは、`${{ secrets.SECRET_NAME }}` 構文を使用して、ワークフローの構成内で使用できます。 GitHub アクションのコンテキストには、既定値 `${{ secrets.GITHUB_TOKEN }}` が自動的に設定される GitHub トークンが存在します。 詳細については、[GitHub Actions のコンテキストと式の構文](https://docs.github.com/actions/reference/context-and-expression-syntax-for-github-actions)に関するページを参照してください。

## <a name="put-it-all-together"></a>すべてをまとめた配置

[dotnet/samples](https://github.com/dotnet/samples) GitHub リポジトリには、このチュートリアルのアプリを含む多数の .NET サンプル ソース コード プロジェクトがあります。

- このアプリは、[サンプル ブラウザー](/samples/dotnet/samples/create-dotnet-github-action)で入手できます。
- 生成された [*CODE_METRICS.md*](https://github.com/dotnet/samples/blob/main/github-actions/DotNet.GitHubAction/CODE_METRICS.md) ファイルはナビゲート可能です。

*CODE_METRICS.md* ファイルは、分析されたプロジェクトの階層を表します。 各プロジェクトには最上位のセクションがあり、絵文字は、入れ子になったオブジェクトの最も高いサイクロマティック複雑度の全体的な状態を表します。 ファイル内を移動すると、各セクションでは、各領域の概要と共にドリル ダウンの機会が提供されます。 マークダウンには、利便性の向上として折りたたみ可能なセクションがあります。

この階層は、次のように進行します。

- プロジェクト ファイルからアセンブリへ
- アセンブリから名前空間へ
- 名前空間から名前付き型へ
- 各名前付き型にはテーブルがあり、各テーブルには次のものがあります。
  - フィールド、メソッド、プロパティの行番号へのリンク
  - コード メトリックに関する個々の評価

### <a name="in-action"></a>操作の実例

このワークフローは、`main` ブランチへの `push` に関する `on` 操作によって、アクションの実行がトリガーされることを指定します。 これが実行されると、GitHub の **[アクション]** タブによって、その実行のライブ ログ ストリームが報告されます。 `.NET code metrics` 実行のログの例を次に示します。

:::image type="content" source="media/action-log.png" lightbox="media/action-log.png" border="true" alt-text=".NET のコード メトリック - GitHub アクションのログ":::

## <a name="see-also"></a>関連項目

<!-- TODO: Add DevOps eBook link when published -->

- [.NET での汎用ホスト](../core/extensions/generic-host.md)
- [.NET での依存関係の挿入](../core/extensions/dependency-injection.md)
- [コード メトリック値](/visualstudio/code-quality/code-metrics-values)

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [.NET GitHub アクションのサンプル コード](/samples/dotnet/samples/create-dotnet-github-action)
