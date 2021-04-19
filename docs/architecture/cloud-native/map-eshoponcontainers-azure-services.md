---
title: eShopOnContainers を Azure サービスにマッピングする
description: Azure Kubernetes Service、API ゲートウェイ、Azure Service Bus などの Azure サービスへの eShopOnContainers のマッピング。
ms.date: 01/19/2021
ms.openlocfilehash: aa0d5cc3bf6c0226627ce558606f974b0e7ec238
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506254"
---
# <a name="mapping-eshoponcontainers-to-azure-services"></a>eShopOnContainers を Azure サービスにマッピングする

Azure は、必須ではありませんが、eShopOnContainers のサポートに適しています。このプロジェクトがクラウドネイティブ アプリケーションとして構築されたためです。 アプリケーションは .NET でビルドされているため、Docker ホストに応じて Linux または Windows コンテナーで実行できます。 アプリケーションは、それぞれに独自のデータがある複数の自律マイクロサービスで構成されています。 さまざまなマイクロサービスによって、単純な CRUD 操作から複雑な DDD や CQRS パターンまで、さまざまなアプローチが示されます。 マイクロサービスは、HTTP 経由でクライアントと通信し、メッセージベースの通信を介して相互に通信します。 アプリケーションでは、クライアントのために複数のプラットフォームもサポートされます。標準通信プロトコルとして HTTP が採用されており、Android、iOS、および Windows プラットフォームで実行する、ASP.NET Core および Xamarin モバイル アプリが含まれるためです。

アプリケーションのアーキテクチャを図 2-5 に示します。 左側にはクライアント アプリがあり、モバイル、従来の Web、および Web シングル ページ アプリケーション (SPA) という種類に分かれています。 右側には、システムを構成するサーバー側コンポーネントがあり、それぞれを Docker コンテナーおよび Kubernetes クラスターでホストできます。 従来の Web アプリには、黄色で示されている ASP.NET Core MVC アプリケーションが搭載されています。 このアプリおよびモバイル アプリケーションおよび Web SPA アプリケーションは、1 つまたは複数の API ゲートウェイを介して個々のマイクロサービスと通信します。 API ゲートウェイは、"backends for front ends" (BFF) パターンに従います。つまり、各ゲートウェイが所定のフロントエンド クライアントをサポートするように設計されます。 個々のマイクロサービスは、API ゲートウェイの右側に示されています。これには、ビジネス ロジックとなんらかの永続化ストアが含まれます。 さまざまなサービスによって、SQL Server データベース、Redis キャッシュ インスタンス、および MongoDB/CosmosDB ストアが使用されます。 一番右には、マイクロサービス間の通信に使用されるシステムのイベント バスがあります。

![eShopOnContainers アーキテクチャ](./media/eshoponcontainers-architecture.png)
**図 2-5**. eShopOnContainers アーキテクチャ。

このアーキテクチャのサーバー側コンポーネントはすべて、Azure サービスに簡単にマップできます。

## <a name="container-orchestration-and-clustering"></a>コンテナーのオーケストレーションとクラスタリング

ASP.NET Core MVC アプリから、Catalog や Ordering の個々のマイクロサービスまで、アプリケーションのコンテナーでホストされるサービスは、Azure Kubernetes Service (AKS) でホストおよび管理できます。 アプリケーションは Docker および Kubernetes でローカルに実行できます。また、同じコンテナーを、AKS でホストされるステージング環境や運用環境に配置できます。 このプロセスは、次のセクションで説明しますが、自動化することができます。

AKS は、コンテナーの個々のクラスターに管理サービスを提供します。 上のアーキテクチャ図に示すように、アプリケーションによって、AKS クラスター内のマイクロサービスごとに個別のコンテナーが配置されます。 このアプローチのため、各サービスがリソース要求に応じて個別にスケールできます。 各マイクロサービスを個別に配置することもできます。理想は、このような配置によって、システムのダウンタイムをゼロにすることです。

## <a name="api-gateway"></a>API ゲートウェイ

eShopOnContainers アプリケーションには、複数のフロントエンド クライアントと複数の異なるバックエンド サービスがあります。 クライアント アプリケーションとそれらをサポートするマイクロサービスの間に 1 対 1 の対応はありません。 このようなシナリオでは、さまざまなバックエンド サービスへのインターフェイスになるクライアント ソフトウェアを、セキュリティで保護された方法で作成することがきわめて複雑になる可能性があります。 各クライアントが独自にこの複雑さに対処する必要が生じます。その結果、重複が発生し、サービスの変更や新しいポリシーの実装に伴って更新を行うべき箇所が多数発生します。

Azure API Management (APIM) を使用すると、組織は、一貫性があり管理しやすい方法で API を公開することができます。 APIM は、API ゲートウェイ、管理ポータル (Azure portal)、開発者ポータルという 3 つのコンポーネントで構成されます。

API ゲートウェイは API 呼び出しを受け取ると、適切なバックエンド API にルーティングします。 また、API キーまたは JWT トークンの検証や、コードの変更なしで、その場での API 変換 (たとえば、以前のインターフェイスを想定するクライアントに対応する場合) といった、その他のサービスも提供されます。

Azure portal では、API スキーマを定義したり、さまざまな API を製品にパッケージ化したりします。 また、ユーザーのアクセス権を構成したり、レポートを表示したり、クォータや変換のポリシーを構成したりすることもできます。

開発者ポータルは、開発者用の主要リソースとして使用されます。 ここでは、API ドキュメント、対話型のテスト コンソール、および各自の使用状況に関するレポートが開発者に提供されます。 また、開発者は、ポータルを使用して、サブスクリプションや API キーのサポートを含め自身のアカウントの作成や管理を行います。

APIM を使用すると、アプリケーションはさまざまなグループのサービスを公開でき、各サービスによって特定のフロントエンド クライアントにバックエンドが提供されます。 複雑なシナリオでは APIM の使用をお勧めします。 ニーズが単純であれば、軽量の API ゲートウェイ Ocelot を使用できます。 eShopOnContainers アプリが Ocelot を使用するのは、単純であることと、アプリケーションそのものと同じアプリケーション環境に配置できるためです。 [eShopOnContainers、APIM、および Ocelot の詳細については、こちらを参照してください。](../microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md#azure-api-management)

アプリケーションが AKS を使用している場合のもう 1 つのオプションは、Azure ゲートウェイ イングレス コントローラーを AKS クラスターにポッドとして配置することです。 このアプローチにより、クラスターが Azure Application Gateway と統合でき、ゲートウェイが AKS ポッドへのトラフィックを負荷分散できるようになります。 [AKS 用の Azure ゲートウェイ イングレス コントローラーの詳細についてはこちらを参照してください](https://github.com/Azure/application-gateway-kubernetes-ingress)

## <a name="data"></a>Data

eShopOnContainers によって使用される多様なバックエンド サービスには、さまざまなストレージ要件があります。 いくつかのマイクロサービスでは SQL Server データベースが使用されます。 Basket マイクロサービスでは、永続化のために Redis キャッシュが活用されます。 Locations マイクロサービスでは、データのために MongoDB API が必要です。 Azure では、これらの各データ形式がサポートされます。

SQL Server データベースのサポートに関して、Azure には、単一データベースから高度にスケーラブルな SQL Database エラスティック プールまですべてに対応する製品があります。 個々のマイクロサービスが独自の SQL Server データベースと通信するようにすばやく簡単に構成できます。 これらのデータベースはニーズに応じてスケールでき、個々のマイクロサービスをニーズに応じてサポートできます。

eShopOnContainers アプリケーションでは、ユーザーの現在の買い物かごは要求をまたがって保存されます。 この処理は、Redis キャッシュにデータを格納する Basket マイクロサービスによって管理されます。 開発時にはこのキャッシュをコンテナーに配置できますが、運用環境では Azure Cache for Redis を利用できます。 Azure Cache for Redis は、高いパフォーマンスと信頼性を提供する完全な管理サービスです。独自に Redis インスタンスまたはコンテナーを配置して管理する必要はありません。

Locations マイクロサービスでは、永続化のために MongoDB NoSQL データベースが使用されます。 開発時には、データベースをそれ自体のコンテナーに配置できますが、運用環境ではサービスが [Azure Cosmos DB の API for MongoDB](/azure/cosmos-db/mongodb-introduction) を利用できます。 Azure Cosmos DB の利点の 1 つは、SQL API および一般的な NoSQL API (MongoDB、Cassandra、Gremlin、Azure Table Storage など) を含め、さまざまな通信プロトコルを活用できることです。 Azure Cosmos DB によって、完全に管理されグローバルに分散されたデータベースがサービスとして提供されます。このサービスは、それを使用するサービスのニーズに合わせてスケールできます。

クラウドネイティブ アプリケーションの分散データの詳細については、[第 5 章](distributed-data.md)を参照してください。

## <a name="event-bus"></a>イベント バス

アプリケーションは、イベントを使用して異なるサービス間で変更について通信します。 この機能はさまざまな実装を使用して実装できます。ローカルでは、eShopOnContainers アプリケーションによって [RabbitMQ](https://www.rabbitmq.com/) が使用されます。 Azure でホストされるとき、アプリケーションはメッセージングのために [Azure Service Bus](/azure/service-bus/) を活用します。 Azure Service Bus は、完全に管理された統合メッセージ ブローカーであり、分離され信頼性が高い非同期方式で、アプリケーションとサービスが相互に通信できるようになります。 Azure Service Bus では、個々のキューと個別の *トピック* がサポートされ、パブリッシャー サブスクライバー シナリオに対応できます。 eShopOnContainers アプリケーションは、Azure Service Bus のトピックを利用して、1 つのマイクロサービスから、特定のメッセージに反応する必要がある他のマイクロサービスへのメッセージの配布をサポートします。

## <a name="resiliency"></a>回復性

運用環境に配置された eShopOnContainers アプリケーションは、回復性の向上に役立ついくつかの Azure サービスを利用できるようになります。 アプリケーションによって公開される正常性チェックを Application Insights と統合すると、アプリの可用性に基づいたレポートとアラートを提供できます。 Azure リソースによって、バグやパフォーマンスの問題を特定して修正するために使用できる診断ログも提供されます。 リソース ログでは、アプリケーションによって、さまざまな Azure リソースがいつどのように使用されたかという詳しい情報が提供されます。 クラウドネイティブの回復性機能の詳細については、[第 6 章](resiliency.md)を参照してください。

>[!div class="step-by-step"]
>[前へ](introduce-eshoponcontainers-reference-app.md)
>[次へ](deploy-eshoponcontainers-azure.md)
