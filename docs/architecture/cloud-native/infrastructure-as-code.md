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
# <a name="infrastructure-as-code"></a><span data-ttu-id="def36-103">コードとしてのインフラストラクチャ</span><span class="sxs-lookup"><span data-stu-id="def36-103">Infrastructure as code</span></span>

<span data-ttu-id="def36-104">クラウドネイティブ システムでは、スピードと機敏性を実現するために、マイクロサービス、コンテナー、最新のシステム設計が採用されています。</span><span class="sxs-lookup"><span data-stu-id="def36-104">Cloud-native systems embrace microservices, containers, and modern system design to achieve speed and agility.</span></span> <span data-ttu-id="def36-105">一貫性のある高品質なコードを実現するために、自動化されたビルドとリリースのステージが用意されています。</span><span class="sxs-lookup"><span data-stu-id="def36-105">They provide automated build and release stages to ensure consistent and quality code.</span></span> <span data-ttu-id="def36-106">しかしそれは、ストーリーの一部にすぎません。</span><span class="sxs-lookup"><span data-stu-id="def36-106">But, that's only part of the story.</span></span> <span data-ttu-id="def36-107">これらのシステムの実行基盤となるクラウド環境をどのようにプロビジョニングすればよいでしょうか?</span><span class="sxs-lookup"><span data-stu-id="def36-107">How do you provision the cloud environments upon which these systems run?</span></span>

<span data-ttu-id="def36-108">最新のクラウドネイティブ アプリケーションでは、[コードとしてのインフラストラクチャ](/azure/devops/learn/what-is-infrastructure-as-code) (`IaC`) という広く受け入れられているプラクティスが採用されています。</span><span class="sxs-lookup"><span data-stu-id="def36-108">Modern cloud-native applications embrace the widely accepted practice of [Infrastructure as Code](/azure/devops/learn/what-is-infrastructure-as-code), or `IaC`.</span></span>  <span data-ttu-id="def36-109">IaC により、プラットフォームのプロビジョニングを自動化できます。</span><span class="sxs-lookup"><span data-stu-id="def36-109">With IaC, you automate platform provisioning.</span></span> <span data-ttu-id="def36-110">基本的には、テストやバージョン管理などのソフトウェア エンジニアリング プラクティスを、DevOps プラクティスに適用します。</span><span class="sxs-lookup"><span data-stu-id="def36-110">You essentially apply software engineering practices such as testing and versioning to your DevOps practices.</span></span> <span data-ttu-id="def36-111">インフラストラクチャとデプロイは、自動化され、一貫した、反復可能なものになります。</span><span class="sxs-lookup"><span data-stu-id="def36-111">Your infrastructure and deployments are automated, consistent, and repeatable.</span></span> <span data-ttu-id="def36-112">継続的デリバリーが従来の手動デプロイのモデルを自動化したのと同様に、コードとしてのインフラストラクチャ (IaC) はアプリケーション環境の管理方法を進化させます。</span><span class="sxs-lookup"><span data-stu-id="def36-112">Just as continuous delivery automated the traditional model of manual deployments, Infrastructure as Code (IaC) is evolving how application environments are managed.</span></span>

<span data-ttu-id="def36-113">Azure Resource Manager (ARM)、Terraform、Azure コマンド ライン インターフェイス (CLI) などのツールを使用すると、必要なクラウド インフラストラクチャを宣言によってスクリプト化できます。</span><span class="sxs-lookup"><span data-stu-id="def36-113">Tools like Azure Resource Manager (ARM), Terraform, and the Azure Command Line Interface (CLI) enable you to declaratively script the cloud infrastructure you require.</span></span>

## <a name="azure-resource-manager-templates"></a><span data-ttu-id="def36-114">Azure Resource Manager のテンプレート</span><span class="sxs-lookup"><span data-stu-id="def36-114">Azure Resource Manager templates</span></span>

<span data-ttu-id="def36-115">ARM は [Azure Resource Manager](/azure/azure-resource-manager/management/overview) の略称です。</span><span class="sxs-lookup"><span data-stu-id="def36-115">ARM stands for [Azure Resource Manager](/azure/azure-resource-manager/management/overview).</span></span> <span data-ttu-id="def36-116">これは、Azure に組み込まれ、API サービスとして公開される API プロビジョニング エンジンです。</span><span class="sxs-lookup"><span data-stu-id="def36-116">It's an API provisioning engine that is built into Azure and exposed as an API service.</span></span> <span data-ttu-id="def36-117">ARM を使用すると、Azure リソース グループに含まれているリソースを 1 回の連携した操作でデプロイ、更新、削除、管理できます。</span><span class="sxs-lookup"><span data-stu-id="def36-117">ARM enables you to deploy, update, delete, and manage the resources contained in Azure resource group in a single, coordinated operation.</span></span> <span data-ttu-id="def36-118">このエンジンに、必要なリソースとその構成を指定する JSON ベースのテンプレートを提供します。</span><span class="sxs-lookup"><span data-stu-id="def36-118">You provide the engine with a JSON-based template that specifies the resources you require and their configuration.</span></span> <span data-ttu-id="def36-119">ARM により、デプロイが、依存関係を尊重した正しい順序で自動的に調整されます。</span><span class="sxs-lookup"><span data-stu-id="def36-119">ARM automatically orchestrates the deployment in the correct order respecting dependencies.</span></span> <span data-ttu-id="def36-120">このエンジンでは、べき等が保証されます。</span><span class="sxs-lookup"><span data-stu-id="def36-120">The engine ensures idempotency.</span></span> <span data-ttu-id="def36-121">同じ構成を持つ目的のリソースが既に存在する場合、プロビジョニングは無視されます。</span><span class="sxs-lookup"><span data-stu-id="def36-121">If a desired resource already exists with the same configuration, provisioning will be ignored.</span></span>

<span data-ttu-id="def36-122">Azure Resource Manager テンプレートは、Azure でさまざまなリソースを定義するための JSON ベースの言語です。</span><span class="sxs-lookup"><span data-stu-id="def36-122">Azure Resource Manager templates are a JSON-based language for defining various resources in Azure.</span></span> <span data-ttu-id="def36-123">基本的なスキーマは 図 10-14 のようになります。</span><span class="sxs-lookup"><span data-stu-id="def36-123">The basic schema looks something like Figure 10-14.</span></span>

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

<span data-ttu-id="def36-124">**図 10-14** - Resource Manager テンプレートのスキーマ</span><span class="sxs-lookup"><span data-stu-id="def36-124">**Figure 10-14** - The schema for a Resource Manager template</span></span>

<span data-ttu-id="def36-125">このテンプレートでは、次のように resources セクション内でストレージ コンテナーを定義できます。</span><span class="sxs-lookup"><span data-stu-id="def36-125">Within this template, one might define a storage container inside the resources section like so:</span></span>

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

<span data-ttu-id="def36-126">**図 10-15** - Resource Manager テンプレート内で定義されたストレージ アカウントの例</span><span class="sxs-lookup"><span data-stu-id="def36-126">**Figure 10-15** - An example of a storage account defined in a Resource Manager template</span></span>

<span data-ttu-id="def36-127">ARM テンプレートは、動的な環境および構成情報でパラメーター化できます。</span><span class="sxs-lookup"><span data-stu-id="def36-127">An ARM template can be parameterized with dynamic environment and configuration information.</span></span> <span data-ttu-id="def36-128">それにより、開発、QA、運用などのさまざまな環境の定義に再利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="def36-128">Doing so enables it to be reused to define different environments, such as development, QA, or production.</span></span> <span data-ttu-id="def36-129">通常、このテンプレートでは、1 つの Azure リソース グループ内にすべてのリソースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="def36-129">Normally, the template creates all resources within a single Azure resource group.</span></span> <span data-ttu-id="def36-130">必要に応じて、1 つの Resource Manager テンプレート内に複数のリソース グループを定義できます。</span><span class="sxs-lookup"><span data-stu-id="def36-130">It's possible to define multiple resource groups in a single Resource Manager template, if needed.</span></span> <span data-ttu-id="def36-131">リソース グループ自体を削除すると、環境内のすべてのリソースを削除できます。</span><span class="sxs-lookup"><span data-stu-id="def36-131">You can delete all resources in an environment by deleting the resource group itself.</span></span> <span data-ttu-id="def36-132">リソース グループ レベルでコスト分析を実行することもできます。これにより、各環境のコストをすばやく計算できます。</span><span class="sxs-lookup"><span data-stu-id="def36-132">Cost analysis can also be run at the resource group level, allowing for quick accounting of how much each environment is costing.</span></span>

<span data-ttu-id="def36-133">GitHub 上の [Azure クイックスタート テンプレート](https://github.com/Azure/azure-quickstart-templates) プロジェクトには、ARM テンプレートの例が多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="def36-133">There are many examples of ARM templates available in the [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates) project on GitHub.</span></span> <span data-ttu-id="def36-134">それらは新しいテンプレートを作成したり、既存のテンプレートを変更したりするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="def36-134">They can help accelerate creating a new template or modifying an existing one.</span></span>

<span data-ttu-id="def36-135">Resource Manager テンプレートを実行するにはさまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="def36-135">Resource Manager templates can be run in many of ways.</span></span> <span data-ttu-id="def36-136">おそらく最も簡単な方法は、単純に Azure portal に貼り付けることです。</span><span class="sxs-lookup"><span data-stu-id="def36-136">Perhaps the simplest way is to simply paste them into the Azure portal.</span></span> <span data-ttu-id="def36-137">試験的なデプロイでは、この方法が手早いでしょう。</span><span class="sxs-lookup"><span data-stu-id="def36-137">For experimental deployments, this method can be quick.</span></span> <span data-ttu-id="def36-138">Azure DevOps のビルドまたはリリース プロセスの一部として実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="def36-138">They can also be run as part of a build or release process in Azure DevOps.</span></span> <span data-ttu-id="def36-139">Azure への接続を利用してテンプレートを実行するタスクがあります。</span><span class="sxs-lookup"><span data-stu-id="def36-139">There are tasks that will leverage connections into Azure to run the templates.</span></span> <span data-ttu-id="def36-140">Resource Manager テンプレートへの変更は増分的に適用されます。つまり、新しいリソースを追加するには、テンプレートに追加するだけです。</span><span class="sxs-lookup"><span data-stu-id="def36-140">Changes to Resource Manager templates are applied incrementally, meaning that to add a new resource requires just adding it to the template.</span></span> <span data-ttu-id="def36-141">ツールによって、現在のリソースとテンプレートで定義されているリソース間の相違点が調整されます。</span><span class="sxs-lookup"><span data-stu-id="def36-141">The tooling will reconcile differences between the current resources and those defined in the template.</span></span> <span data-ttu-id="def36-142">その後、リソースがテンプレートで定義されているものと一致するように作成または変更されます。</span><span class="sxs-lookup"><span data-stu-id="def36-142">Resources will then be created or altered so they match what is defined in the template.</span></span>  

## <a name="terraform"></a><span data-ttu-id="def36-143">Terraform</span><span class="sxs-lookup"><span data-stu-id="def36-143">Terraform</span></span>

<span data-ttu-id="def36-144">多くの場合、クラウドネイティブ アプリケーションは、`cloud agnostic`ように構築されます。</span><span class="sxs-lookup"><span data-stu-id="def36-144">Cloud-native applications are often constructed to be `cloud agnostic`.</span></span> <span data-ttu-id="def36-145">これはつまり、アプリケーションが特定のクラウド ベンダーと緊密に結び付けられておらず、任意のパブリック クラウドにデプロイできるということです。</span><span class="sxs-lookup"><span data-stu-id="def36-145">Being so means the application isn't tightly coupled to a particular cloud vendor and can be deployed to any public cloud.</span></span>

<span data-ttu-id="def36-146">[Terraform](https://www.terraform.io/) は、Azure、Google Cloud Platform、AWS、AliCloud など、すべての主要なクラウド プレイヤーにわたってクラウドネイティブ アプリケーションをプロビジョニングできる商用テンプレート ツールです。</span><span class="sxs-lookup"><span data-stu-id="def36-146">[Terraform](https://www.terraform.io/) is commercial templating tool that can provision cloud-native applications across all the major cloud players: Azure, Google Cloud Platform, AWS, and AliCloud.</span></span> <span data-ttu-id="def36-147">これは、JSON をテンプレート定義言語として使用する代わりに、やや簡潔な YAML を使用します。</span><span class="sxs-lookup"><span data-stu-id="def36-147">Instead of using JSON as the template definition language, it uses the slightly more terse YAML.</span></span>

<span data-ttu-id="def36-148">図 10-16 に、前の Resource Manager テンプレート (図 10-15) と同じ処理を行う Terraform ファイルの例を示します。</span><span class="sxs-lookup"><span data-stu-id="def36-148">An example Terraform file that does the same as the previous Resource Manager template (Figure 10-15) is shown in Figure 10-16:</span></span>

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

<span data-ttu-id="def36-149">**図 10-16** - Resource Manager テンプレートの例</span><span class="sxs-lookup"><span data-stu-id="def36-149">**Figure 10-16** - An example of a Resource Manager template</span></span>

<span data-ttu-id="def36-150">Terraform でも、問題のあるテンプレートに関する直感的なエラー メッセージが提供されます。</span><span class="sxs-lookup"><span data-stu-id="def36-150">Terraform also provides intuitive error messages for problem templates.</span></span> <span data-ttu-id="def36-151">テンプレート エラーを早期にキャッチするためにビルド フェーズで使用できる、便利な検証タスクもあります。</span><span class="sxs-lookup"><span data-stu-id="def36-151">There's also a handy validate task that can be used in the build phase to catch template errors early.</span></span>

<span data-ttu-id="def36-152">Resource Manager テンプレートと同様に、Terraform テンプレートをデプロイするためのコマンドライン ツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="def36-152">As with Resource Manager templates, command-line tools are available to deploy Terraform templates.</span></span> <span data-ttu-id="def36-153">また、Azure Pipelines には、Terraform テンプレートを検証して適用できる、コミュニティによって作成されたタスクもあります。</span><span class="sxs-lookup"><span data-stu-id="def36-153">There are also community-created tasks in Azure Pipelines that can validate and apply Terraform templates.</span></span>

<span data-ttu-id="def36-154">Terraform テンプレートと ARM テンプレートで、有意な値 (新しく作成されたデータベースへの接続文字列など) が出力されることがあります。</span><span class="sxs-lookup"><span data-stu-id="def36-154">Sometimes Terraform and ARM templates output meaningful values, such as a connection string to a newly created database.</span></span> <span data-ttu-id="def36-155">この情報をビルド パイプラインにキャプチャして、後続のタスクで使用することができます。</span><span class="sxs-lookup"><span data-stu-id="def36-155">This information can be captured in the build pipeline and used in subsequent tasks.</span></span>

## <a name="azure-cli-scripts-and-tasks"></a><span data-ttu-id="def36-156">Azure CLI スクリプトとタスク</span><span class="sxs-lookup"><span data-stu-id="def36-156">Azure CLI Scripts and Tasks</span></span>

<span data-ttu-id="def36-157">最後に、[Azure CLI](/cli/azure/) を利用して、クラウド インフラストラクチャを宣言によってスクリプト化できます。</span><span class="sxs-lookup"><span data-stu-id="def36-157">Finally, you can leverage [Azure CLI](/cli/azure/) to declaratively script your cloud infrastructure.</span></span> <span data-ttu-id="def36-158">Azure CLI のスクリプトを作成、検出、共有して、ほぼすべての Azure リソースをプロビジョニングおよび構成できます。</span><span class="sxs-lookup"><span data-stu-id="def36-158">Azure CLI scripts can be created, found, and shared to provision and configure almost any Azure resource.</span></span> <span data-ttu-id="def36-159">CLI は、緩やかな学習曲線で簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="def36-159">The CLI is simple to use with a gentle learning curve.</span></span> <span data-ttu-id="def36-160">スクリプトは PowerShell または Bash 内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="def36-160">Scripts are executed within either PowerShell or Bash.</span></span> <span data-ttu-id="def36-161">また、特に ARM テンプレートと比べてデバッグが簡単です。</span><span class="sxs-lookup"><span data-stu-id="def36-161">They're also straightforward to debug, especially when compared with ARM templates.</span></span>

<span data-ttu-id="def36-162">Azure CLI スクリプトは、インフラストラクチャを破棄して再デプロイする必要がある場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="def36-162">Azure CLI scripts work well when you need to tear down and redeploy your infrastructure.</span></span> <span data-ttu-id="def36-163">既存の環境を更新することは難しい場合があります。</span><span class="sxs-lookup"><span data-stu-id="def36-163">Updating an existing environment can be tricky.</span></span> <span data-ttu-id="def36-164">多くの CLI コマンドは、べき等ではありません。</span><span class="sxs-lookup"><span data-stu-id="def36-164">Many CLI commands aren't idempotent.</span></span> <span data-ttu-id="def36-165">つまり、リソースが既に存在する場合でも、実行されるたびにリソースを再作成します。</span><span class="sxs-lookup"><span data-stu-id="def36-165">That means they'll recreate the resource each time they're run, even if the resource already exists.</span></span> <span data-ttu-id="def36-166">作成前に各リソースが存在するかどうかを調べるコードを追加することは、いつでも可能です。</span><span class="sxs-lookup"><span data-stu-id="def36-166">It's always possible to add code that checks for the existence of each resource before creating it.</span></span> <span data-ttu-id="def36-167">しかしそうすると、スクリプトが肥大化し、管理が難しくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="def36-167">But, doing so, your script can become bloated and difficult to manage.</span></span>

<span data-ttu-id="def36-168">また、これらのスクリプトを Azure DevOps パイプラインに `Azure CLI tasks`として埋め込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="def36-168">These scripts can also be embedded in Azure DevOps pipelines as `Azure CLI tasks`.</span></span> <span data-ttu-id="def36-169">パイプラインを実行すると、スクリプトが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="def36-169">Executing the pipeline invokes the script.</span></span>

<span data-ttu-id="def36-170">図 10-17 に、Azure CLI のバージョンとサブスクリプションの詳細を一覧表示する YAML スニペットを示します。</span><span class="sxs-lookup"><span data-stu-id="def36-170">Figure 10-17 shows a YAML snippet that lists the version of Azure CLI and the details of the subscription.</span></span> <span data-ttu-id="def36-171">Azure CLI コマンドがインライン スクリプト内にどのように含まれているかに注目してください。</span><span class="sxs-lookup"><span data-stu-id="def36-171">Note how Azure CLI commands are included in an inline script.</span></span>

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

<span data-ttu-id="def36-172">**図 10-17** - Azure CLI スクリプト</span><span class="sxs-lookup"><span data-stu-id="def36-172">**Figure 10-17** - Azure CLI script</span></span>

<span data-ttu-id="def36-173">記事「[コードとしてのインフラストラクチャとは](/azure/devops/learn/what-is-infrastructure-as-code)」の中で、執筆者 Sam Guckenheimer は次のように説明しています。"IaC を導入するチームは、安定した環境を迅速かつ大規模に実現できます。</span><span class="sxs-lookup"><span data-stu-id="def36-173">In the article, [What is Infrastructure as Code](/azure/devops/learn/what-is-infrastructure-as-code), Author Sam Guckenheimer describes how, "Teams who implement IaC can deliver stable environments rapidly and at scale.</span></span> <span data-ttu-id="def36-174">チームは、コードによって環境の望ましい状態を表すことで、環境の手動構成を回避し、一貫性を確保します。</span><span class="sxs-lookup"><span data-stu-id="def36-174">Teams avoid manual configuration of environments and enforce consistency by representing the desired state of their environments via code.</span></span> <span data-ttu-id="def36-175">IaC を使用したインフラストラクチャのデプロイは反復可能であり、構成ドリフトや依存関係の不足によって発生するランタイムの問題を防止します。</span><span class="sxs-lookup"><span data-stu-id="def36-175">Infrastructure deployments with IaC are repeatable and prevent runtime issues caused by configuration drift or missing dependencies.</span></span> <span data-ttu-id="def36-176">DevOps チームは、統合された一連のプラクティスおよびツールを使用して連携し、アプリケーションとそれを支えるインフラストラクチャを迅速、確実、大規模に実現できます。"</span><span class="sxs-lookup"><span data-stu-id="def36-176">DevOps teams can work together with a unified set of practices and tools to deliver applications and their supporting infrastructure rapidly, reliably, and at scale."</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="def36-177">[前へ](feature-flags.md)
>[次へ](application-bundles.md)</span><span class="sxs-lookup"><span data-stu-id="def36-177">[Previous](feature-flags.md)
[Next](application-bundles.md)</span></span>
