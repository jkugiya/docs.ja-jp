---
title: フロントエンドのクライアント通信
description: フロントエンド クライアントがクラウドネイティブ システムと通信する方法について説明します
author: robvet
ms.date: 01/19/2021
ms.openlocfilehash: b28fd05aded652057deecd6814199e0360202a07
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604516"
---
# <a name="front-end-client-communication"></a>フロントエンドのクライアント通信

クラウドネイティブ システムでは、フロントエンド クライアント (モバイル、Web、デスクトップ アプリケーション) に、独立したバックエンド マイクロサービスと対話するための通信チャネルが必要です。  

どのようなオプションがありますか?

図 4-2 では、わかりやすさを考慮して、フロントエンド クライアントがバックエンド マイクロサービスと "*直接通信*" しています。

![クライアントからサービスへの直接通信](./media/direct-client-to-service-communication.png)

**図 4-2** クライアントからサービスへの直接通信

この方法では、フロントエンド クライアントがアクセス可能なパブリックエンド ポイントが各マイクロサービスに用意されています。 運用環境では、マイクロサービスの前にロード バランサーを配置して、トラフィックを適切にルーティングします。

実装は簡単ですが、クライアントの直接通信は、シンプルなマイクロサービス アプリケーションでのみ許容されます。 このパターンは、フロントエンド クライアントをコア バックエンド サービスに密結合し、次のようなさまざまな問題のきっかけとなります。

- バックエンド サービスのリファクタリングに対するクライアントの脆弱性。
- コア バックエンド サービスが直接公開される、より広範な攻撃面。
- 各マイクロサービス間における横断的な問題の繰り返し。
- 過度に複雑なクライアント コード - クライアントは、複数のエンドポイントを追跡し、回復力のある方法でエラーを処理する必要があります。

代わりに広く受け入れられているクラウド設計パターンは、フロントエンド アプリケーションとバックエンド サービスの間に [API ゲートウェイ サービス](../microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)を実装する方法です。 図 4-3 は、このパターンを示しています。

![API ゲートウェイ パターン](./media/api-gateway-pattern.png)

**図 4-3** API ゲートウェイ パターン

上の図では、API ゲートウェイ サービスがバックエンド コア マイクロサービスをどのように抽象化しているかに注目してください。 これは Web API として実装され、"*リバース プロキシ*" として機能し、受信トラフィックを内部マイクロサービスにルーティングします。

このゲートウェイにより、クライアントは内部サービスのパーティション分割とリファクタリングから分離されます。 バックエンド サービスを変更する場合は、クライアントを中断することなく、ゲートウェイでサービスを調整できます。 また、ゲートウェイは ID、キャッシュ、回復性、測定、調整などの横断的な問題に対する防御の第一線でもあります。 これらの横断的な問題の多くは、バックエンド コア サービスからゲートウェイにオフロードすることができます。これにより、バックエンド サービスが簡素化されます。

シンプルかつ高速な API ゲートウェイの維持は慎重に行う必要があります。 通常、ビジネス ロジックはゲートウェイには関与しません。 複雑なゲートウェイはボトルネックになるリスクがあり、最終的にはそれ自体が一枚岩となります。 大規模なシステムでは、多くの場合、クライアントの種類 (モバイル、Web、デスクトップ) またはバックエンドの機能別にセグメント化された複数の API ゲートウェイを公開します。 [フロントエンド用バックエンド](/azure/architecture/patterns/backends-for-frontends)のパターンは、複数のゲートウェイを実装するための方向性を提供します。 図 4-4 は、このパターンを示しています。

![フロントエンド用バックエンドのパターン](./media/backend-for-frontend-pattern.png)

**図 4-4** フロントエンド用バックエンドのパターン

上の図では、クライアントの種類 (Web、モバイル、デスクトップ アプリ) に基づいて、受信トラフィックが特定の API ゲートウェイに送信されることに注目してください。 各デバイスの機能はフォーム ファクター、パフォーマンス、表示の制限事項によって大幅に異なるため、この方法は理にかなっています。 通常、モバイル アプリケーションが公開する機能は、ブラウザーやデスクトップ アプリケーションよりも少なくなっています。 各ゲートウェイは、対応するデバイスの機能に合わせて最適化できます。

最初に、独自の API ゲートウェイ サービスを構築できます。 GitHub のクイック検索には、多くの例が用意されています。 ただし、いくつかのフレームワークや市販のゲートウェイ製品も入手できます。

## <a name="ocelot-gateway"></a>Ocelot ゲートウェイ

シンプルな .NET クラウドネイティブ アプリケーションの場合は、[Ocelot ゲートウェイ](https://github.com/ThreeMammals/Ocelot)を検討してください。 Ocelot は、システムへの統合されたエントリ ポイントを必要とする .NET マイクロサービス向けに作成されたオープンソースの API ゲートウェイです。 これは、軽量、高速、かつスケーラブルです。

API ゲートウェイと同様に、主な機能は受信 HTTP 要求をダウンストリーム サービスに転送することです。 また、.NET ミドルウェア パイプラインで構成できるさまざまな機能をサポートしています。 次の表は、その機能セットを示しています。

|Ocelot の機能  | |
| :-------- | :-------- |
| ルーティング | 認証 |
| 要求の集計 | 承認 |
| サービス検索 (Consul と Eureka を使用) | Throttling |
| 負荷分散 | ログ、トレース |
| キャッシュ | ヘッダー/クエリ文字列の変換 |
| 関連付けのパススルー | カスタム ミドルウェア |
| サービスの品質 (QoS) | 再試行ポリシー |

各 Ocelot ゲートウェイは、アップストリームとダウンストリームのアドレスおよび構成可能な機能を JSON 構成ファイルに指定します。 クライアントは、HTTP 要求を Ocelot ゲートウェイに送信します。 要求を受け取った Ocelot は、そのパイプラインを通じて HttpRequest オブジェクトを渡し、構成で指定された状態にします。 パイプラインの最後で、Ocelot は新しい HTTPResponseObject を作成してダウンストリーム サービスに渡します。 応答の場合、Ocelot はパイプラインを反転して、応答をクライアントに送り返します。

Ocelot は NuGet パッケージとして入手できます。 .NET Standard 2.0 を対象としており、.NET Core 2.0 以降および .NET Framework 4.6.1 以降のランタイムの両方と互換性があります。 Ocelot は、HTTP を話すすべてのものと統合され、.NET Core がサポートするプラットフォーム (Linux、macOS、Windows) で実行されます。 Ocelot は拡張可能であり、Docker コンテナー、Azure Kubernetes Service、その他のパブリック クラウドを含む最新のプラットフォームを多数サポートしています。  Ocelot は、[Consul](https://www.consul.io)、[GraphQL](https://graphql.org)、Netflix の [Eureka](https://github.com/Netflix/eureka) などのオープンソースのパッケージと統合されています。

市販の API ゲートウェイの豊富な機能セットを必要としないシンプルなクラウドネイティブ アプリケーションでは Ocelot を検討してください。

## <a name="azure-application-gateway"></a>Azure Application Gateway

ゲートウェイの要件がシンプルな場合は、[Azure Application Gateway](/azure/application-gateway/overview) を検討してください。 Azure [PaaS サービス](https://azure.microsoft.com/overview/what-is-paas/)として利用できるこのゲートウェイには、URL ルーティング、SSL 終端、Web アプリケーション ファイアウォールなどの基本的なゲートウェイ機能が含まれています。 このサービスでは、[レイヤー 7 の負荷分散](https://www.nginx.com/resources/glossary/layer-7-load-balancing/)機能がサポートされます。 レイヤー 7 では、低レベルの TCP ネットワーク パケットだけでなく、HTTP メッセージの実際のコンテンツに基づいて要求をルーティングできます。

本書では、クラウドネイティブ システムを [Kubernetes](https://www.infoworld.com/article/3268073/what-is-kubernetes-your-next-application-platform.html) でホストするよう推奨しています。 コンテナー オーケストレーターである Kubernetes は、コンテナー化されたワークロードのデプロイ、スケーリング、および運用上の処理を自動化します。 Azure Application Gateway は、[Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) クラスター用の API ゲートウェイとして構成できます。

[Application Gateway イングレス コントローラー](https://azure.github.io/application-gateway-kubernetes-ingress/)を使用すると、Azure Application Gateway が [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) を直接操作できるようになります。 図 4.5 は、このアーキテクチャを示しています。

![Application Gateway イングレス コントローラー](./media/application-gateway-ingress-controller.png)

**図 4-5** Application Gateway イングレス コントローラー

Kubernetes には、[Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/) と呼ばれる HTTP (レベル 7) の負荷分散をサポートする機能が組み込まれています。 Ingress では、AKS 内のマイクロサービス インスタンスを外部に公開する方法に関する一連のルールを定義します。 上の図では、イングレス コントローラーがクラスター用に構成されたイングレス ルールを解釈し、Azure Application Gateway を自動的に構成します。 これらのルールに基づいて、Application Gateway は AKS 内で実行されているマイクロサービスにトラフィックをルーティングします。 イングレス コントローラーは、イングレス ルールに対する変更をリッスンし、Azure Application Gateway に適切な変更を加えます。

## <a name="azure-api-management"></a>Azure API Management

中規模から大規模のクラウドネイティブ システムでは、[Azure API Management](https://azure.microsoft.com/services/api-management/) を検討してください。 これは、API ゲートウェイのニーズを解決するだけでなく、フル機能の開発者および管理エクスペリエンスを提供するクラウドベースのサービスです。 図 4-6 は API Management を示しています。

![Azure API Management](./media/azure-api-management.png)

**図 4-6** Azure API Management

最初に、API Management は構成可能なルールとポリシーに基づいて、バックエンド サービスへのアクセスを制御できるゲートウェイ サーバーを公開します。 これらのサービスは、Azure クラウド、オンプレミスのデータセンター、または他のパブリック クラウドに配置できます。 どのユーザーがどのような処理を実行できるかは、API キーと JWT トークンによって決まります。 すべてのトラフィックは、分析のためにログに記録されます。

API Management には、サービス、ドキュメント、およびそれらを呼び出すためのサンプル コードへのアクセスを提供する開発者ポータルが用意されています。 開発者は、Swagger/OpenAPI を使用してサービス エンドポイントを検査し、その使用状況を分析できます。 このサービスは、.NET、Java、Golang などの主要な開発プラットフォームで動作します。

発行者ポータルでは、管理者が API を公開し、その動作を管理する管理ダッシュボードが公開されます。 サービス アクセスを許可し、サービスの正常性を監視して、サービス テレメトリを収集できます。 管理者は、動作に影響を及ぼすための "*ポリシー*" を各エンドポイントに適用します。 [ポリシー](/azure/api-management/api-management-howto-policies)は、それぞれのサービスの呼び出しに対して順番に実行する構築済みのステートメントです。  ポリシーは、着信呼び出し/発信呼び出し用に、またはエラー発生時に呼び出されるように構成されます。 ポリシーを組み合わせるときに決定論的な順序付けを可能にするために、さまざまなサービス スコープでポリシーを適用できます。 製品には、多数の構築済みの[ポリシー](/azure/api-management/api-management-policies)が付属しています。

次の例は、ポリシーがクラウドネイティブ サービスの動作にどのように影響するかを示したものです。  

- サービス アクセスを制限する。
- 認証を適用する。  
- 必要に応じて、1 つのソースからの呼び出しを調整する。
- キャッシュを有効にする。
- 特定の IP アドレスからの呼び出しをブロックする。
- サービスのフローを制御する。
- 要求を SOAP から REST に、または別のデータ形式 (例: XML から JSON) に変換する。

Azure API Management は、任意の場所 (クラウドやデータセンター内) でホストされているバックエンド サービスを公開できます。 クラウドネイティブ システムで公開できるレガシ サービスについては、REST と SOAP API の両方がサポートされます。 その他の Azure サービスも API Management 経由で公開できます。 マネージド API は、[Azure Service Bus](https://azure.microsoft.com/services/service-bus/) や [Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/) などの Azure バッキング サービスの上に配置できます。 Azure API Management には負荷分散サポートが組み込まれていないため、負荷分散サービスと共に使用する必要があります。

次に示す [4 つのレベル](https://azure.microsoft.com/pricing/details/api-management/)の Azure API Management が提供されています。

- 開発者
- Basic
- Standard
- Premium

Developer レベルは、非運用のワークロードおよび評価用です。 他のレベルでは、より優れた能力、機能、高度なサービス レベル アグリーメント (SLA) が提供されます。 Premium レベルでは、[Azure Virtual Network](/azure/virtual-network/virtual-networks-overview) と[複数リージョンのサポート](/azure/api-management/api-management-howto-deploy-multi-region)が提供されます。 すべてのレベルの価格は、1 時間あたりの固定価格です。

Azure クラウドは、Azure API Management 向けの[サーバーレス レベル](https://azure.microsoft.com/blog/announcing-azure-api-management-for-serverless-architectures/)も提供します。 このサービスは "*従量課金の価格レベル*" とも呼ばれ、サーバーレス コンピューティング モデルを中心に設計された API Management の一種です。 前述の "事前に割り当てられた" 価格レベルとは異なり、従量課金レベルでは迅速なプロビジョニングとアクション課金制の価格が提供されます。

これにより、次のユース ケースで API ゲートウェイの機能が有効になります。

- [Azure Functions](/azure/azure-functions/functions-overview) や [Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/) などのサーバーレス テクノロジを使用して実装されたマイクロサービス。
- Service Bus のキューやトピック、Azure Storage などの Azure バッキング サービスのリソース。
- トラフィックが時折急増するが、ほとんどの時間は少ないままのマイクロサービス。

従量課金レベルは、同じ基のサービスの API Management コンポーネントを使用しますが、動的に割り当てられたリソースに基づいてまったく異なるアーキテクチャを採用しています。 これは、次に示すサーバーレス コンピューティング モデルと完全に整合しています。

- 管理するインフラストラクチャがない。
- アイドル容量がない。
- 高可用性。
- 自動スケーリング。
- コストが実際の使用状況に基づく。
  
新しい従量課金レベルは、サーバーレス リソースを API として公開するクラウドネイティブ システムに適しています。

## <a name="real-time-communication"></a>リアルタイム通信

リアルタイム (プッシュ) 通信は、HTTP 経由でバックエンドのクラウドネイティブ システムと通信するフロントエンド アプリケーション向けのもう 1 つのオプションです。 ティッカー、オンライン教育、ゲーム、ジョブの進行状況の更新などのアプリケーションは、バックエンドから即時かつリアルタイムに応答する必要があります。 通常の HTTP 通信では、新しいデータが利用可能になったことをクライアントが認識する方法がありません。 クライアントは、サーバーに対して継続的に要求を "*ポーリング*" または送信する必要があります。 "*リアルタイム*" 通信では、サーバーはいつでも新しいデータをクライアントにプッシュできます。

多くの場合、リアルタイム システムには、高頻度のデータ フローおよび多数の同時クライアント接続という特徴があります。 リアルタイム接続の手動による実装はすぐに複雑になり、接続されたクライアントに対するスケーラビリティと信頼性の高いメッセージングを実現するために、非単純なインフラストラクチャが必要になります。 Azure Cache for Redis のインスタンスと、クライアント アフィニティ用の固定セッションが構成された一連のロード バランサーを管理できます。

[Azure SignalR Service](https://azure.microsoft.com/services/signalr-service/) は、クラウドネイティブ アプリケーション用にリアルタイム通信を簡素化するフル マネージド Azure サービスです。 容量のプロビジョニング、スケーリング、固定接続などの技術的な実装の詳細は削除されています。 これらは、99.9% のサービス レベル アグリーメントで対処されます。 重視するのはインフラストラクチャの組み込みではなくアプリケーションの機能です。

クラウドベースの HTTP サービスを有効にすると、ブラウザー、モバイル、デスクトップ アプリケーションなど、接続されたクライアントにコンテンツの更新を直接プッシュできます。 クライアントは、サーバーをポーリングすることなく更新されます。 Azure SignalR は、リアルタイム接続を作成する転送テクノロジ (WebSocket、Server-Side Events、Long Polling など) を抽象化します。 開発者は、接続されたクライアントのすべてまたは特定のサブセットに対するメッセージの送信に注力します。

図 4-7 は、Azure SignalR が有効になっているクラウドネイティブ アプリケーションに接続する一連の HTTP クライアントを示しています。

![Azure SignalR](./media/azure-signalr-service.png)

**図 4-7** Azure SignalR

Azure SignalR Service のもう 1 つの利点として、サーバーレス クラウドネイティブ サービスが実装されます。 おそらくコードは、Azure Functions のトリガーを使用してオンデマンドで実行されます。 このシナリオは、コードによってクライアントとの接続が長時間維持されないため、注意が必要になる可能性があります。 Azure SignalR サービスでは、サービスが既に接続を管理しているため、このような状況に対処できます。

Azure SignalR Service は、Azure SQL Database、Service Bus、Azure Cache for Redis などの他の Azure サービスと密接に統合されているため、クラウドネイティブ アプリケーションの多くの可能性がもたらされます。

>[!div class="step-by-step"]
>[前へ](communication-patterns.md)
>[次へ](service-to-service-communication.md)
