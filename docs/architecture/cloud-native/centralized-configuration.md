---
title: 集中管理構成
description: Azure App Configuration と AzureKey Vault を使用したクラウドネイティブ アプリの構成の一元化。
ms.date: 01/19/2021
ms.openlocfilehash: 770c0c19a6de01250c59a586badb6a4afa2e9ae5
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505714"
---
# <a name="centralized-configuration"></a>集中管理構成

すべてが 1 つのインスタンス内で動作するモノリシック アプリとは異なり、クラウドネイティブ アプリは、仮想マシン、コンテナー、地域に分散された、独立したサービスで構成されています。 相互に依存する何十個ものサービスの構成設定を管理することは困難です。 さまざまな場所に構成設定の重複するコピーがあると、エラーが発生しやすく、管理も困難になります。 一元化された構成は、分散型クラウドネイティブ アプリケーションにとって重要な要件です。

[第 1 章](introduction.md)で説明したように、Twelve-Factor App (12 要素アプリ) の推奨事項では、コードと構成を厳密に分離する必要があります。 構成はアプリケーションの外部に格納し、必要に応じて読み込む必要があります。 構成値を定数やリテラル値としてコードに格納することは違反になります。 同じアプリケーション内の多くのサービスで、同じ構成値が使用されることはよくあります。 さらに、開発、テスト、運用など、複数の環境で同じ値をサポートする必要があります。 ベスト プラクティスは、それらを一元化された構成ストアに格納することです。

Azure クラウドにはいくつかの素晴らしい選択肢があります。

## <a name="azure-app-configuration"></a>Azure App Configuration

[Azure App Configuration](/azure/azure-app-configuration/overview) は、フル マネージド Azure サービスであり、シークレットではない構成設定が安全な一元化された場所に格納されます。 格納された値は、複数のサービスやアプリケーション間で共有できます。

このサービスは使いやすく、いくつかの利点があります。

- 柔軟性に優れたキーと値による表現とマッピング
- Azure ラベルによるタグ付け
- 管理専用の UI
- 機密情報の暗号化
- クエリとバッチ取得

Azure App Configuration により、キー値設定に加えられた変更が 7 日間維持されます。 ポイントインタイム スナップショット機能を使用すると、設定の履歴を再構築し、失敗したデプロイをロールバックすることもできます。

App Configuration では、構成ストアへの呼び出しが多くなりすぎないようにするため、個々の設定が自動的にキャッシュされます。 キャッシュされた設定の値は、構成ストアで変更されたとしても、その有効期限が切れるまで、設定の更新操作は先延ばしされます。 キャッシュの既定の有効期間は 30 秒です。 有効期間はオーバーライドすることができます。

App Configuration により、転送中と保存中のすべての構成値が暗号化されます。 キー名とラベルは、構成データを取得するためのインデックスとして使用され、暗号化されません。

App Configuration は強固なセキュリティを備えていますが、それでもアプリケーション シークレットの保管場所としては Azure Key Vault が最も優れています。 Key Vault では、ハードウェアレベルの暗号化、粒度の細かいアクセス ポリシー、管理操作 (証明書のローテーションなど) が利用できます。 キー コンテナーに格納されているシークレットを参照する App Configuration 値を作成できます。

## <a name="azure-key-vault"></a>Azure Key Vault

Key Vault は、シークレットを安全に保管し、それにアクセスするためのマネージド サービスです。 シークレットは、API キー、パスワード、証明書など、アクセスを厳密に制御する必要がある任意のものです。 コンテナーはシークレットの論理グループです。

Key Vault によって、シークレットが誤って漏洩する可能性が大幅に小さくなります。 Key Vault を使用すると、アプリケーション開発者は、アプリケーションにセキュリティ情報を格納する必要がなくなります。 この手法を使用すると、コード内にこの情報を格納する必要がなくなります。 たとえば、必要に応じてデータベースに接続するアプリケーションがあるとします。 この場合、接続文字列をアプリのコードに格納する代わりに、Key Vault に安全に格納できます。

アプリケーションでは、URI を使用して、必要な情報に安全にアクセスできます。 アプリケーションでは、これらの URI を使用して特定のバージョンのシークレットを取得できます。 Key Vault に格納されているシークレット情報のいずれかを保護するためにカスタム コードを記述する必要はありません。

Key Vault にアクセスするには、適切な呼び出し元の認証と承認が必要です。 通常、クラウドネイティブ マイクロサービスには、ClientId と ClientSecret の組み合わせが使用されます。 このような資格情報は、ソース管理の外部に保持することが重要です。 ベスト プラクティスは、アプリケーションの環境でそれらを設定することです。 AKS から Key Vault に直接アクセスするには、[Key Vault FlexVolume](https://github.com/Azure/kubernetes-keyvault-flexvol) を使用します。

## <a name="configuration-in-eshop"></a>eShop での構成

eShopOnContainers アプリケーションには、各マイクロサービスにローカル アプリケーション設定ファイルが含まれています。 これらのファイルはソース管理にチェックインされていますが、接続文字列や API キーなどの運用シークレットは含まれていません。 運用環境では、個々の設定が、サービスごとの環境変数で上書きされる可能性があります。 環境変数にシークレットを挿入することは、ホステッド アプリケーションに一般的な手法ですが、中央の構成ストアは提供されません。 構成設定の一元管理をサポートするために、各マイクロサービスには、ローカル設定と Azure Key Vault 設定の使用を切り替える設定が含まれています。

## <a name="references"></a>リファレンス

- [eShopOnContainers アーキテクチャ](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Architecture)
- [高いスケーラビリティと可用性のためにマイクロサービスと複数のコンテナー アプリケーションを調整する](../microservices/architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
- [Azure API Management](/azure/api-management/api-management-key-concepts)
- [Azure SQL Database の概要](/azure/sql-database/sql-database-technical-overview)
- [Azure Cache for Redis](https://azure.microsoft.com/services/cache/)
- [Azure Cosmos DB の MongoDB 用 API](/azure/cosmos-db/mongodb-introduction)
- [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview)
- [Azure Monitor の概要](/azure/azure-monitor/overview)
- [eShopOnContainers: AKS での Kubernetes クラスターの作成](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)#create-kubernetes-cluster-in-aks)
- [eShopOnContainers: Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces)
- [Azure Dev Spaces](/azure/dev-spaces/about)

>[!div class="step-by-step"]
>[前へ](deploy-eshoponcontainers-azure.md)
>[次へ](scale-applications.md)
