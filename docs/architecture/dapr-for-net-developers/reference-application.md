---
title: EShopOnDapr reference アプリケーションの概要
description: EShopOnDapr 参照アプリケーションとその履歴の概要。
author: amolenk
ms.date: 02/07/2021
ms.openlocfilehash: d05d47399b9be539597778a4f7856e06d3b16a6c
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401446"
---
# <a name="dapr-reference-application"></a>Dapr 参照アプリケーション

前に、Dapr の基本的な利点について説明しました。 Dapr は、チームが分散アプリケーションを構築するのにどのように役立つかを説明し、アーキテクチャや運用上の複雑さを軽減します。 その過程で、小規模な Dapr アプリを構築する機会がありました。 次に、エンドツーエンドのマイクロサービスアプリケーションを探索します。これは、Dapr の構成要素とコンポーネントを示しています。

しかし、まず少し歴史があります。

## <a name="eshop-on-containers"></a>コンテナーでの eShop

数年前、Microsoft は主要なコミュニティエキスパートと提携しており、広く普及しているガイダンスブックをリリースしました。これには、コンテナー化された [.Net アプリケーション用の .Net マイクロサービス](https://dotnet.microsoft.com/download/e-book/microservices-architecture/pdf)があります。 図3-1 は、次の書籍を示しています。

![コンテナー化されたマイクロサービス .NET アプリケーションの設計。](./media/reference-application/architecting-microservices-book.png)

**図 3-1**. .NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ。

この書籍では、分散アプリケーションを構築するための原則、パターン、およびベストプラクティスに dove を掘り下げています。 これには、アーキテクチャの概念を紹介する完全な機能を備えたマイクロサービス参照アプリケーションが含まれていました。 [EShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)のアプリケーションは、さまざまな .net アイテム (衣料やコーヒーマグを含む) を販売する e コマースショップを示しています。  .NET Core に組み込まれているアプリケーションはクロスプラットフォームで、Linux または Windows コンテナーのいずれかで実行できます。 図3-2 は、元の eShop アーキテクチャを示しています。

![eShopOnContainers リファレンスアプリケーションアーキテクチャ。](./media/reference-application/eshop-on-containers.png)

**図 3-2**. 元 `ShopOnContainers` の参照アプリケーション。

ご覧のように、eShopOnContainers には多くの移動要素が含まれています。

1. 3つの異なるフロントエンドクライアント。
1. フロントエンドからバックエンドを抽象化するアプリケーションゲートウェイ。
1. 複数のバックエンドコアマイクロサービス。
1. 非同期の pub/sub メッセージングを有効にするイベントバスコンポーネント。

EShopOnContainers reference アプリケーションは、.NET コミュニティ全体で広く受け入れられており、多数の大規模な商用マイクロサービスアプリケーションをモデル化するために使用されています。

## <a name="eshop-on-dapr"></a>Dapr の eShop

この書籍には、eShop アプリケーションの代替バージョンが付属しています。 これは [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr)と呼ばれます。 更新されたバージョンは、Dapr のビルディングブロックとコンポーネントを統合することによって、以前の eShopOnContainers アプリケーションを進化させるものです。 図3-3 は、新しい合理化されたソリューションアーキテクチャを示しています。  

![eShopOnDapr リファレンスアプリケーションアーキテクチャ。](./media/reference-application/eshop-on-dapr.png)

**図 3-3**. eShopOnDapr リファレンスアプリケーションアーキテクチャ。

EShopOnDapr 参照アプリケーションのフォーカスが Dapr にあると、元のアプリケーションが更新されています。 アーキテクチャは次の要素で構成されます。

1. 人気のある角 SPA フレームワークで記述された [単一ページアプリケーション](/archive/msdn-magazine/2013/november/asp-net-single-page-applications-build-modern-responsive-web-apps-with-asp-net) のフロントエンド。 API ゲートウェイマイクロサービスにユーザー要求を送信します。

1. API ゲートウェイは、フロントエンドクライアントからバックエンドコアマイクロサービスを抽出します。 これは、高パフォーマンスのオープンソースのサービスプロキシである [エンボイ](https://www.envoyproxy.io/)を使用して実装されます。 エンボイは、着信要求をさまざまなバックエンドマイクロサービスにルーティングします。 ほとんどの要求は単純な CRUD 操作 (カタログからブランドの一覧を取得するなど) であり、バックエンドマイクロサービスへの直接呼び出しによって処理されます。

1. その他の要求は論理的に複雑で、複数のマイクロサービスを連携させる必要があります。 このような場合、eShopOnDapr は、操作を完了するために必要なマイクロサービス間でワークフローを調整する [アグリゲーターマイクロサービス](../cloud-native/service-to-service-communication.md#service-aggregator-pattern) を実装します。

1. 一連のコアバックエンドマイクロサービスには、e コマースストアに必要な機能が含まれています。 各は自己完結型であり、他のユーザーとは独立しています。 広く受け入れられているドメイン分解パターンに従うと、各マイクロサービスは特定の *ビジネス機能* を分離します。

   - バスケットサービスは、お客様のショッピングカートのエクスペリエンスを管理します。
   - カタログサービスは、販売に使用できる製品アイテムを管理します。
   - Id サービスは、認証と id を管理します。
   - 注文サービスでは、注文の配置と管理のすべての側面が処理されます。
   - 支払いサービスは、お客様の支払いを処理します。

   各サービスには、独自の永続的なストレージがあります。 マイクロサービスの [ベストプラクティス](../cloud-native/distributed-data.md#database-per-microservice-why)に準拠しているため、すべてのサービスがやり取りする共有データストアはありません。

   各マイクロサービスの設計は、個々の要件に基づいています。 単純なサービスでは、基本的な CRUD 操作を使用して、基になるデータストアにアクセスします。 順序付けなどの高度なサービスは、Domain-Driven 設計アプローチを使用して、ビジネスの複雑さを管理します。 必要に応じて、.NET Core、Java、ゴー、NodeJS などのさまざまなテクノロジスタックでサービスを構築できます。

1. 最後に、イベントバスは、Dapr のパブリッシュ/サブスクライブコンポーネントをラップします。 マイクロサービス間で非同期の公開/サブスクライブメッセージングを有効にします。 開発者は、任意の Dapr でサポートされているメッセージブローカーをプラグインできます。

### <a name="application-of-dapr-building-blocks"></a>Dapr 構成ブロックの適用

EShopOnDapr codebase は、eShopOnContainers codebase よりも簡素化されています。 Dapr ビルディングブロックは、大量のエラーが発生しやすい組み込みコードを置き換えます。

図3-4 は、eShop 参照アプリケーションにおける Dapr の統合を示しています。

![eShopOnDapr リファレンスアプリケーションのアーキテクチャ](./media/reference-application/eshop-on-dapr-buildingblocks.png)

**図 3-4**. EShopOnDapr での dapr の統合。

前の図では、どのサービスがどの Dapr の構成要素を使用しているかを確認できます。

1. 元の eShopOnContainers アプリケーションは、注文サービスの DDD の概念とパターンを示しています。 更新された eShopOnDapr では、注文サービスは *アクター構成ブロック* を代替の実装として使用します。 アクターのターンベースのアクセスモデルを使用すると、キャンセルをサポートするステートフルな順序付けプロセスを簡単に実装できます。
1. 注文サービスは、 [バインド構成ブロック](bindings.md)を使用して注文確認電子メールを送信します。
1. バックエンドサービスは、 [publish & subscribe ビルディングブロック](publish-subscribe.md)を使用して非同期に通信します。
1. シークレットの管理は、 [シークレットの構成ブロック](secrets.md)によって行われます。
1. API ゲートウェイと web ショッピングアグリゲーターサービスは、 [サービス呼び出しの構成要素](service-invocation.md) を使用して、バックエンドサービスでメソッドを呼び出します。
1. バスケットサービスは、 [state management ビルディングブロック](state-management.md) を使用して、顧客の買い物かごの状態を格納します。

### <a name="benefits-of-applying-dapr-to-eshop"></a>EShop に Dapr を適用する利点

一般に、Dapr 構成ブロックを使用すると、可観測性と柔軟性がアプリケーションに追加されます。

1. 可観測性: Dapr 構成ブロックを使用することにより、コードを記述しなくても、サービス間および Dapr コンポーネントとの両方の呼び出しに対して、豊富な分散トレースを取得できます。 EShopOnContainers では、大量のカスタムログを使用して洞察を得ることができます。
1. 柔軟性: コンポーネント構成ファイルを変更するだけで、インフラストラクチャを *入れ替える* ことができるようになりました。 コードに変更を加える必要はありません。

次に、特定の構成要素で提供される利点の例をいくつか示します。

- **サービスの呼び出し**
  - Dapr が [mTLS](https://blog.cloudflare.com/introducing-tls-client-auth/)をサポートすることで、サービスは暗号化されたチャネルを介して通信できるようになりました。
  - 一時的なエラーが発生すると、サービス呼び出しは自動的に再試行されます。
  - 自動サービス検出を使用すると、サービスが互いを検索するために必要な構成の量を減らすことができます。

- **パブリッシュ/サブスクライブ**
  - eShopOnContainer と RabbitMQ の Azure Service Bus 両方をサポートするための多数のカスタムコードが含まれています。 開発者は、ローカルでの開発とテストのために Azure Service Bus を実稼働用と RabbitMQ に使用していました。 `IEventBus`これらのメッセージブローカー間のスワップを可能にするために、抽象化レイヤーが作成されました。 このレイヤーには *、約700行のエラーが発生しやすいコード* があります。 Dapr を使用した更新された実装には、 *35 行のコード* のみが必要です。 これは、元のコード行の **5%** です。 さらに重要なのは、実装が簡単でわかりやすいことです。
  - eShopOnDapr は、Dapr の豊富な ASP.NET Core 統合を使用して、pub/sub を使用します。 `Topic`ASP.NET Core コントローラーメソッドに属性を追加して、メッセージをサブスクライブします。 したがって、メッセージブローカーごとに個別のメッセージハンドラーループを記述する必要はありません。
  - HTTP 呼び出しとしてサービスにルーティングされたメッセージは、新しい概念や Sdk を導入することなく、ASP.NET Core ミドルウェアを使用して機能を追加することができます。

- **バインド**
  - EShopOnContainers ソリューションには、顧客への注文確認を電子メールで送信 *する to do* 項目が含まれていました。 最終的には、SendGrid などのサードパーティ製の電子メール API を実装することを考えました。 Dapr では、電子メール通知の実装は、リソースバインドを構成するのと同じように簡単でした。 外部 Api または Sdk について学ぶ必要はありませんでした。

> [!NOTE]
> アクターのビルディングブロックは、このブックの最初のバージョンでは説明されていません。 アクターの構成要素と eShopOnDapr との統合についての広範な章は、1.1 更新プログラムに含まれています。

## <a name="summary"></a>まとめ

この章では、eShopOnDapr 参照アプリケーションについて紹介します。 これは、広く普及している eShopOnContainers マイクロサービス参照アプリケーションの進化です。 eShopOnDapr は、大量のカスタム機能を Dapr の構成要素およびコンポーネントに置き換え、マイクロサービスアプリケーションの構築に必要な複雑さを劇的に簡素化します。

### <a name="references"></a>関連項目

- [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr)

- [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)

- [コンテナー化された .NET アプリケーション用の .NET マイクロサービス](https://dotnet.microsoft.com/download/e-book/microservices-architecture/pdf)

- [Azure 向け Cloud-Native .NET アプリの設計](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf)

> [!div class="step-by-step"]
> [前へ](getting-started.md)
> [次へ](state-management.md)
