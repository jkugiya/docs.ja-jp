---
title: クラウド ネイティブ アプリケーション バンドル
description: Azure 向けクラウド ネイティブ .NET アプリの設計 | クラウド ネイティブ アプリケーション バンドル
ms.date: 01/19/2021
ms.openlocfilehash: d3427ddf82b65dd274ef253749a9b87864092a0a
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506137"
---
# <a name="cloud-native-application-bundles"></a><span data-ttu-id="26573-103">クラウド ネイティブ アプリケーション バンドル</span><span class="sxs-lookup"><span data-stu-id="26573-103">Cloud Native Application Bundles</span></span>

<span data-ttu-id="26573-104">クラウドネイティブ アプリケーションの重要な特性は、クラウドの機能を利用して開発が高速になることです。</span><span class="sxs-lookup"><span data-stu-id="26573-104">A key property of cloud-native applications is that they leverage the capabilities of the cloud to speed up development.</span></span> <span data-ttu-id="26573-105">多くの場合、この設計は、完成したアプリケーションにさまざまな種類のテクノロジが使用されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="26573-105">This design often means that a full application uses different kinds of technologies.</span></span> <span data-ttu-id="26573-106">アプリケーションは Docker コンテナーでリリースされることがあり、サービスによっては Azure Functions が使用されることがあります。一方で、ハードウェア GPU アクセラレーションを備えた大規模なメタル サーバーに割り当てられた仮想マシン上で直接実行されることもあります。</span><span class="sxs-lookup"><span data-stu-id="26573-106">Applications may be shipped in Docker containers, some services may use Azure Functions, while other parts may run directly on virtual machines allocated on large metal servers with hardware GPU acceleration.</span></span> <span data-ttu-id="26573-107">クラウドネイティブ アプリケーションは 2 つとして同じものはないため、リリースするための 1 つのメカニズムを用意することは困難でした。</span><span class="sxs-lookup"><span data-stu-id="26573-107">No two cloud-native applications are the same, so it's been difficult to provide a single mechanism for shipping them.</span></span>

<span data-ttu-id="26573-108">Docker コンテナーの場合、Kubernetes 上で実行し、デプロイに Helm Chart を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="26573-108">The Docker containers may run on Kubernetes using a Helm Chart for deployment.</span></span> <span data-ttu-id="26573-109">Azure Functions の場合、Terraform テンプレートを使用して割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="26573-109">The Azure Functions may be allocated using Terraform templates.</span></span> <span data-ttu-id="26573-110">最後に、仮想マシンの場合、Terraform を使用して割り当て、構築には Ansible を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="26573-110">Finally, the virtual machines may be allocated using Terraform but built out using Ansible.</span></span> <span data-ttu-id="26573-111">このようにさまざまなテクノロジがありますが、それらをすべてまとめて合理的なパッケージにする方法はありませんでした。</span><span class="sxs-lookup"><span data-stu-id="26573-111">This is a large variety of technologies and there has been no way to package them all together into a reasonable package.</span></span> <span data-ttu-id="26573-112">今までは、の話です。</span><span class="sxs-lookup"><span data-stu-id="26573-112">Until now.</span></span>

<span data-ttu-id="26573-113">クラウド ネイティブ アプリケーション バンドル (CNAB) は、Microsoft、Docker、HashiCorp などの多くのコミュニティ志向の企業による、分散アプリケーションをパッケージ化するための仕様を開発することを目的とした共同の取り組みです。</span><span class="sxs-lookup"><span data-stu-id="26573-113">Cloud Native Application Bundles (CNABs) are a joint effort by many community-minded companies such as Microsoft, Docker, and HashiCorp to develop a specification to package distributed applications.</span></span>

<span data-ttu-id="26573-114">この取り組みは 2018 年の 12 月に発表されたものなので、この取り組みをより大きなコミュニティに公開するには、まだかなりの作業が必要です。</span><span class="sxs-lookup"><span data-stu-id="26573-114">The effort was announced in December of 2018, so there's still a fair bit of work to do to expose the effort to the greater community.</span></span> <span data-ttu-id="26573-115">ただし、既に[オープン仕様](https://github.com/deislabs/cnab-spec)と、[Duffle](https://duffle.sh/) と呼ばれる参照実装があります。</span><span class="sxs-lookup"><span data-stu-id="26573-115">However, there's already an [open specification](https://github.com/deislabs/cnab-spec) and a reference implementation known as [Duffle](https://duffle.sh/).</span></span> <span data-ttu-id="26573-116">このツールは Go 言語で作成されており、Docker と Microsoft が共同で開発したものです。</span><span class="sxs-lookup"><span data-stu-id="26573-116">This tool, which was written in Go, is a joint effort between Docker and Microsoft.</span></span>

<span data-ttu-id="26573-117">CNAB には、さまざまな種類のインストール テクノロジを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="26573-117">The CNABs can contain different kinds of installation technologies.</span></span> <span data-ttu-id="26573-118">このような側面から、Helm chart、Terraform テンプレート、Ansible プレイブックなどを同じパッケージに共存させることができます。</span><span class="sxs-lookup"><span data-stu-id="26573-118">This aspect allows things like Helm Charts, Terraform templates, and Ansible Playbooks to coexist in the same package.</span></span> <span data-ttu-id="26573-119">ビルドされたパッケージは、自己完結型でポータブルであり、USB メモリからでもインストールできます。</span><span class="sxs-lookup"><span data-stu-id="26573-119">Once built, the packages are self-contained and portable; they can be installed from a USB stick.</span></span>  <span data-ttu-id="26573-120">パッケージには暗号を使用して署名されており、発行元が正規のものであることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="26573-120">The packages are cryptographically signed to ensure they originate from the party they claim.</span></span>

<span data-ttu-id="26573-121">CNAB の核となるのは、`bundle.json` というファイルです。</span><span class="sxs-lookup"><span data-stu-id="26573-121">The core of a CNAB is a file called `bundle.json`.</span></span> <span data-ttu-id="26573-122">このファイルには、Terraform やイメージなど、バンドルの内容が定義されています。</span><span class="sxs-lookup"><span data-stu-id="26573-122">This file defines the contents of the bundle, be they Terraform or images or anything else.</span></span> <span data-ttu-id="26573-123">図 11-9 は、Terraform を呼び出す CNAB の定義です。</span><span class="sxs-lookup"><span data-stu-id="26573-123">Figure 11-9 defines a CNAB that invokes some Terraform.</span></span> <span data-ttu-id="26573-124">ただし、実際には、Terraform の呼び出しに使用される呼び出しイメージが定義されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="26573-124">Notice, however, that it actually defines an invocation image that is used to invoke the Terraform.</span></span> <span data-ttu-id="26573-125">パッケージ化されると、*cnab* ディレクトリにある Docker ファイルが Docker イメージに組み込まれ、バンドルに含まれることになります。</span><span class="sxs-lookup"><span data-stu-id="26573-125">When packaged up, the Docker file that is located in the *cnab* directory is built into a Docker image, which will be included in the bundle.</span></span> <span data-ttu-id="26573-126">バンドルの Docker コンテナー内に Terraform がインストールされているので、バンドルを実行するためにユーザーがマシンに Terraform をインストールする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="26573-126">Having Terraform installed inside a Docker container in the bundle means that users don't need to have Terraform installed on their machine to run the bundling.</span></span>

```json
{
    "name": "terraform",
    "version": "0.1.0",
    "schemaVersion": "v1.0.0-WD",
    "parameters": {
        "backend": {
            "type": "boolean",
            "defaultValue": false,
            "destination": {
                "env": "TF_VAR_backend"
            }
        }
    },
    "invocationImages": [
        {
        "imageType": "docker",
        "image": "cnab/terraform:latest"
        }
    ],
    "credentials": {
        "tenant_id": {
            "env": "TF_VAR_tenant_id"
        },
        "client_id": {
            "env": "TF_VAR_client_id"
        },
        "client_secret": {
            "env": "TF_VAR_client_secret"
        },
        "subscription_id": {
            "env": "TF_VAR_subscription_id"
        },
        "ssh_authorized_key": {
            "env": "TF_VAR_ssh_authorized_key"
        }
    },
    "actions": {
        "status": {
            "modifies": true
        }
    }
}
```

<span data-ttu-id="26573-127">**図 10-18** - Terraform ファイルの例</span><span class="sxs-lookup"><span data-stu-id="26573-127">**Figure 10-18** - An example Terraform file</span></span>

<span data-ttu-id="26573-128">また、`bundle.json` では Terraform に渡すパラメーターを定義しています。</span><span class="sxs-lookup"><span data-stu-id="26573-128">The `bundle.json` also defines a set of parameters that are passed down into the Terraform.</span></span> <span data-ttu-id="26573-129">バンドルのパラメーター化により、さまざまな環境へのインストールが可能になります。</span><span class="sxs-lookup"><span data-stu-id="26573-129">Parameterization of the bundle allows for installation in various different environments.</span></span>

<span data-ttu-id="26573-130">また、CNAB 形式には柔軟性もあるため、あらゆるクラウドに対して使用することができます。</span><span class="sxs-lookup"><span data-stu-id="26573-130">The CNAB format is also flexible, allowing it to be used against any cloud.</span></span> <span data-ttu-id="26573-131">[OpenStack](https://www.openstack.org/) のようなオンプレミス ソリューションに対しても使用できます。</span><span class="sxs-lookup"><span data-stu-id="26573-131">It can even be used against on-premises solutions such as [OpenStack](https://www.openstack.org/).</span></span>

## <a name="devops-decisions"></a><span data-ttu-id="26573-132">DevOps の判断</span><span class="sxs-lookup"><span data-stu-id="26573-132">DevOps Decisions</span></span>

<span data-ttu-id="26573-133">最近の DevOps 分野には素晴らしいツールがたくさんあり、成功させる方法についての優れた書籍や論文も増えています。</span><span class="sxs-lookup"><span data-stu-id="26573-133">There are so many great tools in the DevOps space these days and even more fantastic books and papers on how to succeed.</span></span> <span data-ttu-id="26573-134">DevOps について学習し始める場合にお勧めの書籍は『[The Phoenix Project (Phoenix プロジェクト)](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/)』です。架空の企業での NoOps から DevOps への変革が描かれています。</span><span class="sxs-lookup"><span data-stu-id="26573-134">A favorite book to get started on the DevOps journey is [The Phoenix Project](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), which follows the transformation of a fictional company from NoOps to DevOps.</span></span> <span data-ttu-id="26573-135">1 つ確かなことがあります。複雑なクラウド ネイティブ アプリケーションをデプロイする際に、DevOps はもはや "あるといいね" 程度のものではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="26573-135">One thing is for certain: DevOps is no longer a "nice to have" when deploying complex, Cloud Native Applications.</span></span> <span data-ttu-id="26573-136">これは要件であり、プロジェクトの開始時に計画し、リソースを確保すべきものです。</span><span class="sxs-lookup"><span data-stu-id="26573-136">It's a requirement and should be planned for and resourced at the start of any project.</span></span>

## <a name="references"></a><span data-ttu-id="26573-137">リファレンス</span><span class="sxs-lookup"><span data-stu-id="26573-137">References</span></span>

- [<span data-ttu-id="26573-138">Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="26573-138">Azure DevOps</span></span>](https://azure.microsoft.com/services/devops/)
- [<span data-ttu-id="26573-139">Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="26573-139">Azure Resource Manager</span></span>](/azure/azure-resource-manager/management/overview)
- [<span data-ttu-id="26573-140">Terraform</span><span class="sxs-lookup"><span data-stu-id="26573-140">Terraform</span></span>](https://www.terraform.io/)
- [<span data-ttu-id="26573-141">Azure CLI</span><span class="sxs-lookup"><span data-stu-id="26573-141">Azure CLI</span></span>](/cli/azure/)

>[!div class="step-by-step"]
><span data-ttu-id="26573-142">[前へ](infrastructure-as-code.md)
>[次へ](summary.md)</span><span class="sxs-lookup"><span data-stu-id="26573-142">[Previous](infrastructure-as-code.md)
[Next](summary.md)</span></span>
