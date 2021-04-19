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
# <a name="cloud-native-application-bundles"></a>クラウド ネイティブ アプリケーション バンドル

クラウドネイティブ アプリケーションの重要な特性は、クラウドの機能を利用して開発が高速になることです。 多くの場合、この設計は、完成したアプリケーションにさまざまな種類のテクノロジが使用されることを意味します。 アプリケーションは Docker コンテナーでリリースされることがあり、サービスによっては Azure Functions が使用されることがあります。一方で、ハードウェア GPU アクセラレーションを備えた大規模なメタル サーバーに割り当てられた仮想マシン上で直接実行されることもあります。 クラウドネイティブ アプリケーションは 2 つとして同じものはないため、リリースするための 1 つのメカニズムを用意することは困難でした。

Docker コンテナーの場合、Kubernetes 上で実行し、デプロイに Helm Chart を使用することができます。 Azure Functions の場合、Terraform テンプレートを使用して割り当てることができます。 最後に、仮想マシンの場合、Terraform を使用して割り当て、構築には Ansible を使用することができます。 このようにさまざまなテクノロジがありますが、それらをすべてまとめて合理的なパッケージにする方法はありませんでした。 今までは、の話です。

クラウド ネイティブ アプリケーション バンドル (CNAB) は、Microsoft、Docker、HashiCorp などの多くのコミュニティ志向の企業による、分散アプリケーションをパッケージ化するための仕様を開発することを目的とした共同の取り組みです。

この取り組みは 2018 年の 12 月に発表されたものなので、この取り組みをより大きなコミュニティに公開するには、まだかなりの作業が必要です。 ただし、既に[オープン仕様](https://github.com/deislabs/cnab-spec)と、[Duffle](https://duffle.sh/) と呼ばれる参照実装があります。 このツールは Go 言語で作成されており、Docker と Microsoft が共同で開発したものです。

CNAB には、さまざまな種類のインストール テクノロジを含めることができます。 このような側面から、Helm chart、Terraform テンプレート、Ansible プレイブックなどを同じパッケージに共存させることができます。 ビルドされたパッケージは、自己完結型でポータブルであり、USB メモリからでもインストールできます。  パッケージには暗号を使用して署名されており、発行元が正規のものであることを確認できます。

CNAB の核となるのは、`bundle.json` というファイルです。 このファイルには、Terraform やイメージなど、バンドルの内容が定義されています。 図 11-9 は、Terraform を呼び出す CNAB の定義です。 ただし、実際には、Terraform の呼び出しに使用される呼び出しイメージが定義されていることに注意してください。 パッケージ化されると、*cnab* ディレクトリにある Docker ファイルが Docker イメージに組み込まれ、バンドルに含まれることになります。 バンドルの Docker コンテナー内に Terraform がインストールされているので、バンドルを実行するためにユーザーがマシンに Terraform をインストールする必要がありません。

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

**図 10-18** - Terraform ファイルの例

また、`bundle.json` では Terraform に渡すパラメーターを定義しています。 バンドルのパラメーター化により、さまざまな環境へのインストールが可能になります。

また、CNAB 形式には柔軟性もあるため、あらゆるクラウドに対して使用することができます。 [OpenStack](https://www.openstack.org/) のようなオンプレミス ソリューションに対しても使用できます。

## <a name="devops-decisions"></a>DevOps の判断

最近の DevOps 分野には素晴らしいツールがたくさんあり、成功させる方法についての優れた書籍や論文も増えています。 DevOps について学習し始める場合にお勧めの書籍は『[The Phoenix Project (Phoenix プロジェクト)](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/)』です。架空の企業での NoOps から DevOps への変革が描かれています。 1 つ確かなことがあります。複雑なクラウド ネイティブ アプリケーションをデプロイする際に、DevOps はもはや "あるといいね" 程度のものではなくなりました。 これは要件であり、プロジェクトの開始時に計画し、リソースを確保すべきものです。

## <a name="references"></a>リファレンス

- [Azure DevOps](https://azure.microsoft.com/services/devops/)
- [Azure Resource Manager](/azure/azure-resource-manager/management/overview)
- [Terraform](https://www.terraform.io/)
- [Azure CLI](/cli/azure/)

>[!div class="step-by-step"]
>[前へ](infrastructure-as-code.md)
>[次へ](summary.md)
