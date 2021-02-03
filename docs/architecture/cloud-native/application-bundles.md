---
title: クラウド ネイティブ アプリケーション バンドル
description: Azure 向けのクラウドネイティブ .NET アプリの設計 |クラウドネイティブアプリケーションバンドル
ms.date: 01/19/2021
ms.openlocfilehash: d3427ddf82b65dd274ef253749a9b87864092a0a
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506137"
---
# <a name="cloud-native-application-bundles"></a><span data-ttu-id="ce6c8-103">クラウド ネイティブ アプリケーション バンドル</span><span class="sxs-lookup"><span data-stu-id="ce6c8-103">Cloud Native Application Bundles</span></span>

<span data-ttu-id="ce6c8-104">クラウドネイティブアプリケーションの重要な特性は、クラウドの機能を活用して開発を高速化できることです。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-104">A key property of cloud-native applications is that they leverage the capabilities of the cloud to speed up development.</span></span> <span data-ttu-id="ce6c8-105">この設計は、多くの場合、アプリケーション全体がさまざまな種類のテクノロジを使用することを意味します。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-105">This design often means that a full application uses different kinds of technologies.</span></span> <span data-ttu-id="ce6c8-106">アプリケーションは、Docker コンテナーに配布される場合があります。一部のサービスでは Azure Functions が使用される場合がありますが、ハードウェア GPU アクセラレーションを使用する大金属サーバー上に割り当てられた仮想マシン上で直接実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-106">Applications may be shipped in Docker containers, some services may use Azure Functions, while other parts may run directly on virtual machines allocated on large metal servers with hardware GPU acceleration.</span></span> <span data-ttu-id="ce6c8-107">2つのクラウドネイティブアプリケーションは同じではありません。そのため、1つのメカニズムを配布することは困難でした。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-107">No two cloud-native applications are the same, so it's been difficult to provide a single mechanism for shipping them.</span></span>

<span data-ttu-id="ce6c8-108">Docker コンテナーは、配置のためのヘルムグラフを使用して、Kubernetes 上で実行できます。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-108">The Docker containers may run on Kubernetes using a Helm Chart for deployment.</span></span> <span data-ttu-id="ce6c8-109">Azure Functions は、Terraform テンプレートを使用して割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-109">The Azure Functions may be allocated using Terraform templates.</span></span> <span data-ttu-id="ce6c8-110">最後に、仮想マシンは Terraform を使用して割り当てられますが、を使用して構築される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-110">Finally, the virtual machines may be allocated using Terraform but built out using Ansible.</span></span> <span data-ttu-id="ce6c8-111">これは、さまざまなテクノロジであり、それらをまとめて適切なパッケージにパッケージ化することはできませんでした。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-111">This is a large variety of technologies and there has been no way to package them all together into a reasonable package.</span></span> <span data-ttu-id="ce6c8-112">これまでは。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-112">Until now.</span></span>

<span data-ttu-id="ce6c8-113">クラウドネイティブアプリケーションバンドル (CNABs) は、Microsoft、Docker、HashiCorp などの多くのコミュニティ志向企業による共同作業で、分散アプリケーションをパッケージ化するための仕様を開発します。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-113">Cloud Native Application Bundles (CNABs) are a joint effort by many community-minded companies such as Microsoft, Docker, and HashiCorp to develop a specification to package distributed applications.</span></span>

<span data-ttu-id="ce6c8-114">この作業は2018年12月に発表されました。そのため、より大きなコミュニティに労力を公開するために、かなりの作業が必要になります。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-114">The effort was announced in December of 2018, so there's still a fair bit of work to do to expose the effort to the greater community.</span></span> <span data-ttu-id="ce6c8-115">ただし、既に開いている [仕様](https://github.com/deislabs/cnab-spec) と、 [ダッフル](https://duffle.sh/)と呼ばれる参照実装があります。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-115">However, there's already an [open specification](https://github.com/deislabs/cnab-spec) and a reference implementation known as [Duffle](https://duffle.sh/).</span></span> <span data-ttu-id="ce6c8-116">このツールは、外出先で作成されたもので、Docker と Microsoft の間の共同作業です。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-116">This tool, which was written in Go, is a joint effort between Docker and Microsoft.</span></span>

<span data-ttu-id="ce6c8-117">CNABs には、さまざまな種類のインストールテクノロジを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-117">The CNABs can contain different kinds of installation technologies.</span></span> <span data-ttu-id="ce6c8-118">この側面では、ヘルムグラフ、Terraform テンプレート、およびその他のプレイブックのようなものを同じパッケージに共存させることができます。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-118">This aspect allows things like Helm Charts, Terraform templates, and Ansible Playbooks to coexist in the same package.</span></span> <span data-ttu-id="ce6c8-119">ビルドされると、パッケージは自己完結型でポータブルになります。USB スティックからインストールできます。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-119">Once built, the packages are self-contained and portable; they can be installed from a USB stick.</span></span>  <span data-ttu-id="ce6c8-120">パッケージは、要求されたパーティからのものであることを確認するために、暗号署名が行われます。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-120">The packages are cryptographically signed to ensure they originate from the party they claim.</span></span>

<span data-ttu-id="ce6c8-121">CNAB の中核となるのは、という名前のファイルです `bundle.json` 。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-121">The core of a CNAB is a file called `bundle.json`.</span></span> <span data-ttu-id="ce6c8-122">このファイルでは、バンドルの内容を定義します。このファイルは、Terraform や images などです。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-122">This file defines the contents of the bundle, be they Terraform or images or anything else.</span></span> <span data-ttu-id="ce6c8-123">図11-9 では、Terraform を呼び出す CNAB を定義しています。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-123">Figure 11-9 defines a CNAB that invokes some Terraform.</span></span> <span data-ttu-id="ce6c8-124">ただし、Terraform を呼び出すために使用される呼び出しイメージを実際に定義することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-124">Notice, however, that it actually defines an invocation image that is used to invoke the Terraform.</span></span> <span data-ttu-id="ce6c8-125">パッケージ化されると、 *cnab* ディレクトリに配置されている docker ファイルは、バンドルに含まれる docker イメージに組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-125">When packaged up, the Docker file that is located in the *cnab* directory is built into a Docker image, which will be included in the bundle.</span></span> <span data-ttu-id="ce6c8-126">バンドル内の Docker コンテナー内に Terraform をインストールすると、バンドルを実行するためにユーザーのコンピューターに Terraform をインストールする必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-126">Having Terraform installed inside a Docker container in the bundle means that users don't need to have Terraform installed on their machine to run the bundling.</span></span>

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

<span data-ttu-id="ce6c8-127">**図 10-18** -Terraform ファイルの例</span><span class="sxs-lookup"><span data-stu-id="ce6c8-127">**Figure 10-18** - An example Terraform file</span></span>

<span data-ttu-id="ce6c8-128">また、は、 `bundle.json` Terraform に渡されるパラメーターのセットも定義します。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-128">The `bundle.json` also defines a set of parameters that are passed down into the Terraform.</span></span> <span data-ttu-id="ce6c8-129">バンドルのパラメーター化により、さまざまな環境でのインストールが可能になります。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-129">Parameterization of the bundle allows for installation in various different environments.</span></span>

<span data-ttu-id="ce6c8-130">また、CNAB 形式は柔軟であり、任意のクラウドに対して使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-130">The CNAB format is also flexible, allowing it to be used against any cloud.</span></span> <span data-ttu-id="ce6c8-131">[Openstack](https://www.openstack.org/)などのオンプレミスソリューションに対しても使用できます。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-131">It can even be used against on-premises solutions such as [OpenStack](https://www.openstack.org/).</span></span>

## <a name="devops-decisions"></a><span data-ttu-id="ce6c8-132">DevOps の意思決定</span><span class="sxs-lookup"><span data-stu-id="ce6c8-132">DevOps Decisions</span></span>

<span data-ttu-id="ce6c8-133">これらの日の DevOps 領域には多くの優れたツールがあり、これを成功させる方法についてはもっとすばらしい書籍や論文もあります。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-133">There are so many great tools in the DevOps space these days and even more fantastic books and papers on how to succeed.</span></span> <span data-ttu-id="ce6c8-134">DevOps の旅を始めるためのお気に入りの書籍は、架空の企業を NoOps から DevOps に変換する、 [フェニックスのプロジェクト](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/)です。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-134">A favorite book to get started on the DevOps journey is [The Phoenix Project](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), which follows the transformation of a fictional company from NoOps to DevOps.</span></span> <span data-ttu-id="ce6c8-135">1つは、複雑なクラウドネイティブアプリケーションをデプロイするときに、DevOps が "優れた" ということです。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-135">One thing is for certain: DevOps is no longer a "nice to have" when deploying complex, Cloud Native Applications.</span></span> <span data-ttu-id="ce6c8-136">これは要件であり、プロジェクトの開始時に、およびに対して計画を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce6c8-136">It's a requirement and should be planned for and resourced at the start of any project.</span></span>

## <a name="references"></a><span data-ttu-id="ce6c8-137">リファレンス</span><span class="sxs-lookup"><span data-stu-id="ce6c8-137">References</span></span>

- [<span data-ttu-id="ce6c8-138">Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="ce6c8-138">Azure DevOps</span></span>](https://azure.microsoft.com/services/devops/)
- [<span data-ttu-id="ce6c8-139">Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="ce6c8-139">Azure Resource Manager</span></span>](/azure/azure-resource-manager/management/overview)
- [<span data-ttu-id="ce6c8-140">Terraform</span><span class="sxs-lookup"><span data-stu-id="ce6c8-140">Terraform</span></span>](https://www.terraform.io/)
- [<span data-ttu-id="ce6c8-141">Azure CLI</span><span class="sxs-lookup"><span data-stu-id="ce6c8-141">Azure CLI</span></span>](/cli/azure/)

>[!div class="step-by-step"]
><span data-ttu-id="ce6c8-142">[前へ](infrastructure-as-code.md)
>[次へ](summary.md)</span><span class="sxs-lookup"><span data-stu-id="ce6c8-142">[Previous](infrastructure-as-code.md)
[Next](summary.md)</span></span>
