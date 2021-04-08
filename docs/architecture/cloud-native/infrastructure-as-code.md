---
title: コードとしてのインフラストラクチャ
description: クラウドネイティブ アプリケーションでの、コードとしてのインフラストラクチャ (IaC) の導入
ms.date: 05/13/2020
ms.openlocfilehash: 5a7cd3a0b4906b1a4aec9e1015d6128867ae9963
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255445"
---
# <a name="infrastructure-as-code"></a>コードとしてのインフラストラクチャ

クラウドネイティブ システムでは、スピードと機敏性を実現するために、マイクロサービス、コンテナー、最新のシステム設計が採用されています。 一貫性のある高品質なコードを実現するために、自動化されたビルドとリリースのステージが用意されています。 しかしそれは、ストーリーの一部にすぎません。 これらのシステムの実行基盤となるクラウド環境をどのようにプロビジョニングすればよいでしょうか?

最新のクラウドネイティブ アプリケーションでは、[コードとしてのインフラストラクチャ](/azure/devops/learn/what-is-infrastructure-as-code) (`IaC`) という広く受け入れられているプラクティスが採用されています。  IaC により、プラットフォームのプロビジョニングを自動化できます。 基本的には、テストやバージョン管理などのソフトウェア エンジニアリング プラクティスを、DevOps プラクティスに適用します。 インフラストラクチャとデプロイは、自動化され、一貫した、反復可能なものになります。 継続的デリバリーが従来の手動デプロイのモデルを自動化したのと同様に、コードとしてのインフラストラクチャ (IaC) はアプリケーション環境の管理方法を進化させます。

Azure Resource Manager (ARM)、Terraform、Azure コマンド ライン インターフェイス (CLI) などのツールを使用すると、必要なクラウド インフラストラクチャを宣言によってスクリプト化できます。

## <a name="azure-resource-manager-templates"></a>Azure Resource Manager のテンプレート

ARM は [Azure Resource Manager](/azure/azure-resource-manager/management/overview) の略称です。 これは、Azure に組み込まれ、API サービスとして公開される API プロビジョニング エンジンです。 ARM を使用すると、Azure リソース グループに含まれているリソースを 1 回の連携した操作でデプロイ、更新、削除、管理できます。 このエンジンに、必要なリソースとその構成を指定する JSON ベースのテンプレートを提供します。 ARM により、デプロイが、依存関係を尊重した正しい順序で自動的に調整されます。 このエンジンでは、べき等が保証されます。 同じ構成を持つ目的のリソースが既に存在する場合、プロビジョニングは無視されます。

Azure Resource Manager テンプレートは、Azure でさまざまなリソースを定義するための JSON ベースの言語です。 基本的なスキーマは 図 10-14 のようになります。

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
  "contentVersion": "",
  "apiProfile": "",
  "parameters": {  },
  "variables": {  },
  "functions": [  ],
  "resources": [  ],
  "outputs": {  }
}
```

**図 10-14** - Resource Manager テンプレートのスキーマ

このテンプレートでは、次のように resources セクション内でストレージ コンテナーを定義できます。

```json
"resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "name": "[variables('storageAccountName')]",
      "location": "[parameters('location')]",
      "apiVersion": "2018-07-01",
      "sku": {
        "name": "[parameters('storageAccountType')]"
      },
      "kind": "StorageV2",
      "properties": {}
    }
  ],
```

**図 10-15** - Resource Manager テンプレート内で定義されたストレージ アカウントの例

ARM テンプレートは、動的な環境および構成情報でパラメーター化できます。 それにより、開発、QA、運用などのさまざまな環境の定義に再利用できるようになります。 通常、このテンプレートでは、1 つの Azure リソース グループ内にすべてのリソースが作成されます。 必要に応じて、1 つの Resource Manager テンプレート内に複数のリソース グループを定義できます。 リソース グループ自体を削除すると、環境内のすべてのリソースを削除できます。 リソース グループ レベルでコスト分析を実行することもできます。これにより、各環境のコストをすばやく計算できます。

GitHub 上の [Azure クイックスタート テンプレート](https://github.com/Azure/azure-quickstart-templates) プロジェクトには、ARM テンプレートの例が多数用意されています。 それらは新しいテンプレートを作成したり、既存のテンプレートを変更したりするのに役立ちます。

Resource Manager テンプレートを実行するにはさまざまな方法があります。 おそらく最も簡単な方法は、単純に Azure portal に貼り付けることです。 試験的なデプロイでは、この方法が手早いでしょう。 Azure DevOps のビルドまたはリリース プロセスの一部として実行することもできます。 Azure への接続を利用してテンプレートを実行するタスクがあります。 Resource Manager テンプレートへの変更は増分的に適用されます。つまり、新しいリソースを追加するには、テンプレートに追加するだけです。 ツールによって、現在のリソースとテンプレートで定義されているリソース間の相違点が調整されます。 その後、リソースがテンプレートで定義されているものと一致するように作成または変更されます。  

## <a name="terraform"></a>Terraform

多くの場合、クラウドネイティブ アプリケーションは、`cloud agnostic`ように構築されます。 これはつまり、アプリケーションが特定のクラウド ベンダーと緊密に結び付けられておらず、任意のパブリック クラウドにデプロイできるということです。

[Terraform](https://www.terraform.io/) は、Azure、Google Cloud Platform、AWS、AliCloud など、すべての主要なクラウド プレイヤーにわたってクラウドネイティブ アプリケーションをプロビジョニングできる商用テンプレート ツールです。 これは、JSON をテンプレート定義言語として使用する代わりに、やや簡潔な YAML を使用します。

図 10-16 に、前の Resource Manager テンプレート (図 10-15) と同じ処理を行う Terraform ファイルの例を示します。

```terraform
provider "azurerm" {
  version = "=1.28.0"
}

resource "azurerm_resource_group" "test" {
  name     = "production"
  location = "West US"
}

resource "azurerm_storage_account" "testsa" {
  name                     = "${var.storageAccountName}"
  resource_group_name      = "${azurerm_resource_group.testrg.name}"
  location                 = "${var.region}"
  account_tier             = "${var.tier}"
  account_replication_type = "${var.replicationType}"

}
```

**図 10-16** - Resource Manager テンプレートの例

Terraform でも、問題のあるテンプレートに関する直感的なエラー メッセージが提供されます。 テンプレート エラーを早期にキャッチするためにビルド フェーズで使用できる、便利な検証タスクもあります。

Resource Manager テンプレートと同様に、Terraform テンプレートをデプロイするためのコマンドライン ツールが用意されています。 また、Azure Pipelines には、Terraform テンプレートを検証して適用できる、コミュニティによって作成されたタスクもあります。

Terraform テンプレートと ARM テンプレートで、有意な値 (新しく作成されたデータベースへの接続文字列など) が出力されることがあります。 この情報をビルド パイプラインにキャプチャして、後続のタスクで使用することができます。

## <a name="azure-cli-scripts-and-tasks"></a>Azure CLI スクリプトとタスク

最後に、[Azure CLI](/cli/azure/) を利用して、クラウド インフラストラクチャを宣言によってスクリプト化できます。 Azure CLI のスクリプトを作成、検出、共有して、ほぼすべての Azure リソースをプロビジョニングおよび構成できます。 CLI は、緩やかな学習曲線で簡単に使用できます。 スクリプトは PowerShell または Bash 内で実行されます。 また、特に ARM テンプレートと比べてデバッグが簡単です。

Azure CLI スクリプトは、インフラストラクチャを破棄して再デプロイする必要がある場合に適しています。 既存の環境を更新することは難しい場合があります。 多くの CLI コマンドは、べき等ではありません。 つまり、リソースが既に存在する場合でも、実行されるたびにリソースを再作成します。 作成前に各リソースが存在するかどうかを調べるコードを追加することは、いつでも可能です。 しかしそうすると、スクリプトが肥大化し、管理が難しくなる可能性があります。

また、これらのスクリプトを Azure DevOps パイプラインに `Azure CLI tasks`として埋め込むこともできます。 パイプラインを実行すると、スクリプトが呼び出されます。

図 10-17 に、Azure CLI のバージョンとサブスクリプションの詳細を一覧表示する YAML スニペットを示します。 Azure CLI コマンドがインライン スクリプト内にどのように含まれているかに注目してください。

```yaml
- task: AzureCLI@2
  displayName: Azure CLI
  inputs:
    azureSubscription: <Name of the Azure Resource Manager service connection>
    scriptType: ps
    scriptLocation: inlineScript
    inlineScript: |
      az --version
      az account show
```

**図 10-17** - Azure CLI スクリプト

記事「[コードとしてのインフラストラクチャとは](/azure/devops/learn/what-is-infrastructure-as-code)」の中で、執筆者 Sam Guckenheimer は次のように説明しています。"IaC を導入するチームは、安定した環境を迅速かつ大規模に実現できます。 チームは、コードによって環境の望ましい状態を表すことで、環境の手動構成を回避し、一貫性を確保します。 IaC を使用したインフラストラクチャのデプロイは反復可能であり、構成ドリフトや依存関係の不足によって発生するランタイムの問題を防止します。 DevOps チームは、統合された一連のプラクティスおよびツールを使用して連携し、アプリケーションとそれを支えるインフラストラクチャを迅速、確実、大規模に実現できます。"

>[!div class="step-by-step"]
>[前へ](feature-flags.md)
>[次へ](application-bundles.md)
