---
title: コードとしてのインフラストラクチャ
description: クラウドネイティブアプリケーションでのインフラストラクチャとしてのインフラストラクチャの導入 (IaC)
ms.date: 05/13/2020
ms.openlocfilehash: 5a7cd3a0b4906b1a4aec9e1015d6128867ae9963
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255445"
---
# <a name="infrastructure-as-code"></a><span data-ttu-id="04dfb-103">コードとしてのインフラストラクチャ</span><span class="sxs-lookup"><span data-stu-id="04dfb-103">Infrastructure as code</span></span>

<span data-ttu-id="04dfb-104">クラウドネイティブシステムは、マイクロサービス、コンテナー、および最新のシステム設計を採用して、速度と機敏性を実現します。</span><span class="sxs-lookup"><span data-stu-id="04dfb-104">Cloud-native systems embrace microservices, containers, and modern system design to achieve speed and agility.</span></span> <span data-ttu-id="04dfb-105">一貫性のある品質のコードを確保するために、自動化されたビルドとリリースのステージを提供します。</span><span class="sxs-lookup"><span data-stu-id="04dfb-105">They provide automated build and release stages to ensure consistent and quality code.</span></span> <span data-ttu-id="04dfb-106">しかし、これはストーリーの一部にすぎません。</span><span class="sxs-lookup"><span data-stu-id="04dfb-106">But, that's only part of the story.</span></span> <span data-ttu-id="04dfb-107">これらのシステムを実行するクラウド環境をプロビジョニングするにはどうすればよいですか。</span><span class="sxs-lookup"><span data-stu-id="04dfb-107">How do you provision the cloud environments upon which these systems run?</span></span>

<span data-ttu-id="04dfb-108">最新のクラウドネイティブアプリケーションは、広く受け入れられ [ているインフラストラクチャをコードとして](/azure/devops/learn/what-is-infrastructure-as-code)、またはとして採用して `IaC` います。</span><span class="sxs-lookup"><span data-stu-id="04dfb-108">Modern cloud-native applications embrace the widely accepted practice of [Infrastructure as Code](/azure/devops/learn/what-is-infrastructure-as-code), or `IaC`.</span></span>  <span data-ttu-id="04dfb-109">IaC を使用すると、プラットフォームのプロビジョニングを自動化できます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-109">With IaC, you automate platform provisioning.</span></span> <span data-ttu-id="04dfb-110">基本的に、テストやバージョン管理などのソフトウェアエンジニアリングプラクティスを DevOps プラクティスに適用します。</span><span class="sxs-lookup"><span data-stu-id="04dfb-110">You essentially apply software engineering practices such as testing and versioning to your DevOps practices.</span></span> <span data-ttu-id="04dfb-111">インフラストラクチャとデプロイは、自動化され、一貫性があり、反復可能です。</span><span class="sxs-lookup"><span data-stu-id="04dfb-111">Your infrastructure and deployments are automated, consistent, and repeatable.</span></span> <span data-ttu-id="04dfb-112">継続的デリバリーと同様に、手動デプロイの従来のモデルを自動化するのと同じように、Infrastructure as Code (IaC) は、アプリケーション環境の管理方法を進化させるものです。</span><span class="sxs-lookup"><span data-stu-id="04dfb-112">Just as continuous delivery automated the traditional model of manual deployments, Infrastructure as Code (IaC) is evolving how application environments are managed.</span></span>

<span data-ttu-id="04dfb-113">Azure Resource Manager (ARM)、Terraform、Azure コマンドラインインターフェイス (CLI) などのツールを使用すると、必要なクラウドインフラストラクチャを宣言によってスクリプト化することができます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-113">Tools like Azure Resource Manager (ARM), Terraform, and the Azure Command Line Interface (CLI) enable you to declaratively script the cloud infrastructure you require.</span></span>

## <a name="azure-resource-manager-templates"></a><span data-ttu-id="04dfb-114">Azure Resource Manager のテンプレート</span><span class="sxs-lookup"><span data-stu-id="04dfb-114">Azure Resource Manager templates</span></span>

<span data-ttu-id="04dfb-115">ARM は [Azure Resource Manager](/azure/azure-resource-manager/management/overview)を表します。</span><span class="sxs-lookup"><span data-stu-id="04dfb-115">ARM stands for [Azure Resource Manager](/azure/azure-resource-manager/management/overview).</span></span> <span data-ttu-id="04dfb-116">これは、Azure に組み込まれ、API サービスとして公開される API プロビジョニングエンジンです。</span><span class="sxs-lookup"><span data-stu-id="04dfb-116">It's an API provisioning engine that is built into Azure and exposed as an API service.</span></span> <span data-ttu-id="04dfb-117">ARM では、Azure リソースグループに含まれるリソースを1回の連携した操作でデプロイ、更新、削除、管理することができます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-117">ARM enables you to deploy, update, delete, and manage the resources contained in Azure resource group in a single, coordinated operation.</span></span> <span data-ttu-id="04dfb-118">このエンジンには、必要なリソースとその構成を指定する JSON ベースのテンプレートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="04dfb-118">You provide the engine with a JSON-based template that specifies the resources you require and their configuration.</span></span> <span data-ttu-id="04dfb-119">ARM は、依存関係を尊重する正しい順序で展開を自動的に調整します。</span><span class="sxs-lookup"><span data-stu-id="04dfb-119">ARM automatically orchestrates the deployment in the correct order respecting dependencies.</span></span> <span data-ttu-id="04dfb-120">エンジンはべき等を保証します。</span><span class="sxs-lookup"><span data-stu-id="04dfb-120">The engine ensures idempotency.</span></span> <span data-ttu-id="04dfb-121">同じ構成の目的のリソースが既に存在する場合、プロビジョニングは無視されます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-121">If a desired resource already exists with the same configuration, provisioning will be ignored.</span></span>

<span data-ttu-id="04dfb-122">Azure Resource Manager テンプレートは、Azure でさまざまなリソースを定義するための JSON ベースの言語です。</span><span class="sxs-lookup"><span data-stu-id="04dfb-122">Azure Resource Manager templates are a JSON-based language for defining various resources in Azure.</span></span> <span data-ttu-id="04dfb-123">基本的なスキーマは、図10-14 のようになります。</span><span class="sxs-lookup"><span data-stu-id="04dfb-123">The basic schema looks something like Figure 10-14.</span></span>

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

<span data-ttu-id="04dfb-124">**図 10-14** -Resource Manager テンプレートのスキーマ</span><span class="sxs-lookup"><span data-stu-id="04dfb-124">**Figure 10-14** - The schema for a Resource Manager template</span></span>

<span data-ttu-id="04dfb-125">このテンプレート内では、次のように resources セクション内にストレージコンテナーを定義できます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-125">Within this template, one might define a storage container inside the resources section like so:</span></span>

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

<span data-ttu-id="04dfb-126">**図 10-15** -Resource Manager テンプレートで定義されたストレージアカウントの例</span><span class="sxs-lookup"><span data-stu-id="04dfb-126">**Figure 10-15** - An example of a storage account defined in a Resource Manager template</span></span>

<span data-ttu-id="04dfb-127">ARM テンプレートは、動的な環境と構成情報を使用してパラメーター化できます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-127">An ARM template can be parameterized with dynamic environment and configuration information.</span></span> <span data-ttu-id="04dfb-128">これにより、開発、QA、実稼働などのさまざまな環境を定義するために再利用できます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-128">Doing so enables it to be reused to define different environments, such as development, QA, or production.</span></span> <span data-ttu-id="04dfb-129">通常、このテンプレートでは、1つの Azure リソースグループ内のすべてのリソースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-129">Normally, the template creates all resources within a single Azure resource group.</span></span> <span data-ttu-id="04dfb-130">必要に応じて、1つの Resource Manager テンプレートに複数のリソースグループを定義できます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-130">It's possible to define multiple resource groups in a single Resource Manager template, if needed.</span></span> <span data-ttu-id="04dfb-131">リソースグループ自体を削除することで、環境内のすべてのリソースを削除できます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-131">You can delete all resources in an environment by deleting the resource group itself.</span></span> <span data-ttu-id="04dfb-132">コスト分析は、リソースグループレベルで実行することもできます。これにより、各環境のコストをすばやく計算できます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-132">Cost analysis can also be run at the resource group level, allowing for quick accounting of how much each environment is costing.</span></span>

<span data-ttu-id="04dfb-133">GitHub の [Azure クイックスタートテンプレート](https://github.com/Azure/azure-quickstart-templates) プロジェクトで使用できる ARM テンプレートには、多くの例が用意されています。</span><span class="sxs-lookup"><span data-stu-id="04dfb-133">There are many examples of ARM templates available in the [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates) project on GitHub.</span></span> <span data-ttu-id="04dfb-134">新しいテンプレートを作成したり、既存のテンプレートを変更したりするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-134">They can help accelerate creating a new template or modifying an existing one.</span></span>

<span data-ttu-id="04dfb-135">Resource Manager テンプレートは、さまざまな方法で実行できます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-135">Resource Manager templates can be run in many of ways.</span></span> <span data-ttu-id="04dfb-136">おそらく、簡単な方法は、単に Azure portal に貼り付けることです。</span><span class="sxs-lookup"><span data-stu-id="04dfb-136">Perhaps the simplest way is to simply paste them into the Azure portal.</span></span> <span data-ttu-id="04dfb-137">試験的なデプロイでは、この方法を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-137">For experimental deployments, this method can be quick.</span></span> <span data-ttu-id="04dfb-138">また、Azure DevOps のビルドプロセスまたはリリースプロセスの一部として実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-138">They can also be run as part of a build or release process in Azure DevOps.</span></span> <span data-ttu-id="04dfb-139">Azure への接続を活用してテンプレートを実行するタスクがあります。</span><span class="sxs-lookup"><span data-stu-id="04dfb-139">There are tasks that will leverage connections into Azure to run the templates.</span></span> <span data-ttu-id="04dfb-140">Resource Manager テンプレートへの変更は段階的に適用されます。つまり、新しいリソースを追加するには、テンプレートに追加するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-140">Changes to Resource Manager templates are applied incrementally, meaning that to add a new resource requires just adding it to the template.</span></span> <span data-ttu-id="04dfb-141">ツールは、現在のリソースと、テンプレートで定義されているリソースとの違いを調整します。</span><span class="sxs-lookup"><span data-stu-id="04dfb-141">The tooling will reconcile differences between the current resources and those defined in the template.</span></span> <span data-ttu-id="04dfb-142">リソースは、テンプレートで定義されている内容と一致するように作成または変更されます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-142">Resources will then be created or altered so they match what is defined in the template.</span></span>  

## <a name="terraform"></a><span data-ttu-id="04dfb-143">Terraform</span><span class="sxs-lookup"><span data-stu-id="04dfb-143">Terraform</span></span>

<span data-ttu-id="04dfb-144">クラウドネイティブアプリケーションは、多くの場合、として構築され `cloud agnostic` ます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-144">Cloud-native applications are often constructed to be `cloud agnostic`.</span></span> <span data-ttu-id="04dfb-145">そのため、アプリケーションは特定のクラウドベンダーと緊密に結合されていないため、任意のパブリッククラウドにデプロイできます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-145">Being so means the application isn't tightly coupled to a particular cloud vendor and can be deployed to any public cloud.</span></span>

<span data-ttu-id="04dfb-146">[Terraform](https://www.terraform.io/) は、すべての主要なクラウドプレーヤー (Azure、GOOGLE CLOUD PLATFORM、AWS、alicloud) でクラウドネイティブアプリケーションをプロビジョニングできる商用テンプレートツールです。</span><span class="sxs-lookup"><span data-stu-id="04dfb-146">[Terraform](https://www.terraform.io/) is commercial templating tool that can provision cloud-native applications across all the major cloud players: Azure, Google Cloud Platform, AWS, and AliCloud.</span></span> <span data-ttu-id="04dfb-147">JSON をテンプレート定義言語として使用する代わりに、やや簡潔な YAML を使用します。</span><span class="sxs-lookup"><span data-stu-id="04dfb-147">Instead of using JSON as the template definition language, it uses the slightly more terse YAML.</span></span>

<span data-ttu-id="04dfb-148">前の Resource Manager テンプレートと同様の Terraform ファイルの例 (図 10-15) を図10-16 に示します。</span><span class="sxs-lookup"><span data-stu-id="04dfb-148">An example Terraform file that does the same as the previous Resource Manager template (Figure 10-15) is shown in Figure 10-16:</span></span>

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

<span data-ttu-id="04dfb-149">**図 10-16** -Resource Manager テンプレートの例</span><span class="sxs-lookup"><span data-stu-id="04dfb-149">**Figure 10-16** - An example of a Resource Manager template</span></span>

<span data-ttu-id="04dfb-150">Terraform は、問題のあるテンプレートに対して直感的なエラーメッセージも提供します。</span><span class="sxs-lookup"><span data-stu-id="04dfb-150">Terraform also provides intuitive error messages for problem templates.</span></span> <span data-ttu-id="04dfb-151">また、テンプレートエラーを早期にキャッチするためにビルドフェーズで使用できる、便利な検証タスクもあります。</span><span class="sxs-lookup"><span data-stu-id="04dfb-151">There's also a handy validate task that can be used in the build phase to catch template errors early.</span></span>

<span data-ttu-id="04dfb-152">Resource Manager テンプレートと同様に、コマンドラインツールを使用して Terraform テンプレートをデプロイできます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-152">As with Resource Manager templates, command-line tools are available to deploy Terraform templates.</span></span> <span data-ttu-id="04dfb-153">また、Azure Pipelines には、Terraform テンプレートを検証して適用できるコミュニティによって作成されたタスクもあります。</span><span class="sxs-lookup"><span data-stu-id="04dfb-153">There are also community-created tasks in Azure Pipelines that can validate and apply Terraform templates.</span></span>

<span data-ttu-id="04dfb-154">Terraform と ARM テンプレートは、新しく作成されたデータベースへの接続文字列など、意味のある値を出力する場合があります。</span><span class="sxs-lookup"><span data-stu-id="04dfb-154">Sometimes Terraform and ARM templates output meaningful values, such as a connection string to a newly created database.</span></span> <span data-ttu-id="04dfb-155">この情報は、ビルドパイプラインでキャプチャし、後続のタスクで使用できます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-155">This information can be captured in the build pipeline and used in subsequent tasks.</span></span>

## <a name="azure-cli-scripts-and-tasks"></a><span data-ttu-id="04dfb-156">Azure CLI のスクリプトとタスク</span><span class="sxs-lookup"><span data-stu-id="04dfb-156">Azure CLI Scripts and Tasks</span></span>

<span data-ttu-id="04dfb-157">最後に、 [Azure CLI](/cli/azure/) を利用して、クラウドインフラストラクチャの宣言によるスクリプト作成を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-157">Finally, you can leverage [Azure CLI](/cli/azure/) to declaratively script your cloud infrastructure.</span></span> <span data-ttu-id="04dfb-158">Azure CLI スクリプトを作成、検出、および共有して、ほぼすべての Azure リソースをプロビジョニングして構成することができます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-158">Azure CLI scripts can be created, found, and shared to provision and configure almost any Azure resource.</span></span> <span data-ttu-id="04dfb-159">CLI は、非常に簡単な学習曲線で簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-159">The CLI is simple to use with a gentle learning curve.</span></span> <span data-ttu-id="04dfb-160">スクリプトは、PowerShell または Bash 内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-160">Scripts are executed within either PowerShell or Bash.</span></span> <span data-ttu-id="04dfb-161">また、特に ARM テンプレートと比較してデバッグするのも簡単です。</span><span class="sxs-lookup"><span data-stu-id="04dfb-161">They're also straightforward to debug, especially when compared with ARM templates.</span></span>

<span data-ttu-id="04dfb-162">Azure CLI スクリプトは、インフラストラクチャを破棄して再展開する必要がある場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="04dfb-162">Azure CLI scripts work well when you need to tear down and redeploy your infrastructure.</span></span> <span data-ttu-id="04dfb-163">既存の環境を更新することは、難しい場合があります。</span><span class="sxs-lookup"><span data-stu-id="04dfb-163">Updating an existing environment can be tricky.</span></span> <span data-ttu-id="04dfb-164">多くの CLI コマンドはべき等ではありません。</span><span class="sxs-lookup"><span data-stu-id="04dfb-164">Many CLI commands aren't idempotent.</span></span> <span data-ttu-id="04dfb-165">つまり、リソースが既に存在する場合でも、実行されるたびにリソースが再作成されます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-165">That means they'll recreate the resource each time they're run, even if the resource already exists.</span></span> <span data-ttu-id="04dfb-166">各リソースが作成される前に存在するかどうかをチェックするコードを追加することは常に可能です。</span><span class="sxs-lookup"><span data-stu-id="04dfb-166">It's always possible to add code that checks for the existence of each resource before creating it.</span></span> <span data-ttu-id="04dfb-167">しかし、そうすると、スクリプトが肥大化し、管理が困難になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="04dfb-167">But, doing so, your script can become bloated and difficult to manage.</span></span>

<span data-ttu-id="04dfb-168">これらのスクリプトは、Azure DevOps パイプラインにとして埋め込むこともでき `Azure CLI tasks` ます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-168">These scripts can also be embedded in Azure DevOps pipelines as `Azure CLI tasks`.</span></span> <span data-ttu-id="04dfb-169">パイプラインを実行すると、スクリプトが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-169">Executing the pipeline invokes the script.</span></span>

<span data-ttu-id="04dfb-170">図10-17 は、Azure CLI のバージョンとサブスクリプションの詳細を一覧表示する YAML スニペットを示しています。</span><span class="sxs-lookup"><span data-stu-id="04dfb-170">Figure 10-17 shows a YAML snippet that lists the version of Azure CLI and the details of the subscription.</span></span> <span data-ttu-id="04dfb-171">インラインスクリプトに Azure CLI コマンドが含まれていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="04dfb-171">Note how Azure CLI commands are included in an inline script.</span></span>

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

<span data-ttu-id="04dfb-172">**図 10-17** -Azure CLI スクリプト</span><span class="sxs-lookup"><span data-stu-id="04dfb-172">**Figure 10-17** - Azure CLI script</span></span>

<span data-ttu-id="04dfb-173">「 [コードとしてのインフラストラクチャとは](/azure/devops/learn/what-is-infrastructure-as-code)」の記事では、作成者 Sam Guckenheimer は、"IaC を実装するチームは、安定した環境を迅速かつ大規模に提供する方法を説明しています。</span><span class="sxs-lookup"><span data-stu-id="04dfb-173">In the article, [What is Infrastructure as Code](/azure/devops/learn/what-is-infrastructure-as-code), Author Sam Guckenheimer describes how, "Teams who implement IaC can deliver stable environments rapidly and at scale.</span></span> <span data-ttu-id="04dfb-174">チームは環境の手動構成を回避し、コードを使用して環境の望ましい状態を表すことによって一貫性を適用します。</span><span class="sxs-lookup"><span data-stu-id="04dfb-174">Teams avoid manual configuration of environments and enforce consistency by representing the desired state of their environments via code.</span></span> <span data-ttu-id="04dfb-175">IaC を使用したインフラストラクチャのデプロイは反復可能であり、構成のずれや依存関係の不足によって発生するランタイムの問題を回避できます。</span><span class="sxs-lookup"><span data-stu-id="04dfb-175">Infrastructure deployments with IaC are repeatable and prevent runtime issues caused by configuration drift or missing dependencies.</span></span> <span data-ttu-id="04dfb-176">DevOps チームは、統合された一連のプラクティスとツールを一緒に使用して、アプリケーションとそのサポートインフラストラクチャを迅速かつ確実に、かつ大規模に配信できます。 "</span><span class="sxs-lookup"><span data-stu-id="04dfb-176">DevOps teams can work together with a unified set of practices and tools to deliver applications and their supporting infrastructure rapidly, reliably, and at scale."</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="04dfb-177">[前へ](feature-flags.md)
>[次へ](application-bundles.md)</span><span class="sxs-lookup"><span data-stu-id="04dfb-177">[Previous](feature-flags.md)
[Next](application-bundles.md)</span></span>
