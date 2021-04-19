---
title: クラウド ネイティブ向けアプリの候補
description: クラウドネイティブ アプローチが適しているアプリケーションの種類について説明します。
author: robvet
ms.date: 01/19/2021
ms.openlocfilehash: 443a7c1a1aaef078b33f352f597b33b768d989a3
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506189"
---
# <a name="candidate-apps-for-cloud-native"></a>クラウド ネイティブ向けアプリの候補

ポートフォリオ内のアプリを確認します。 そのうち、クラウドネイティブ アーキテクチャに適したアプリはいくつありますか。 全部ですか。 一部でしょうか。

費用便益分析を適用すると、クラウド ネイティブにするために必要な高額なコストに見合わない可能性が高いものがほとんどです。 クラウド ネイティブにするためのコストは、アプリケーションのビジネス価値をはるかに上回ります。

どのようなアプリケーションがクラウド ネイティブの候補になる可能性があるでしょうか。

- ビジネスの機能や特徴を常に進化させる必要がある戦略的なエンタープライズ システム

- 高い信頼性を備え、高いリリース速度を必要とするアプリケーション

- システム全体を完全に再デプロイすること "*なく*"、個々の機能をリリースする必要があるシステム

- さまざまなテクノロジ スタックの専門知識を持つチームによって開発されたアプリケーション

- 独立してスケーリングする必要のあるコンポーネントを持つアプリケーション

また、レガシ システムもあります。 誰もが新しいアプリケーションを構築したいと思うものですが、ビジネスにとって重要なレガシ ワークロードのモダン化を担当することもよくあります。 時間の経過と共に、レガシ アプリケーションはマイクロサービスに分解され、コンテナー化され、最終的にはクラウドネイティブ アーキテクチャへと "プラットフォームの再構築" が行われる可能性があります。

### <a name="modernizing-legacy-apps"></a>レガシ アプリのモダン化

無料の Microsoft の電子書籍「[Azure クラウドおよび Windows コンテナーを使用した既存の .NET アプリケーションのモダン化](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)」には、オンプレミスのワークロードをクラウドに移行するためのガイダンスが説明されています。 図 1-10 は、レガシ アプリケーションをモダン化する際に、1 つの汎用的な戦略はないことを示しています。

![レガシ ワークロードを移行するための戦略](./media/strategies-for-migrating-legacy-workloads.png)

**図 1-10**. レガシ ワークロードを移行するための戦略

重要ではないモノリシック アプリには、迅速なリフト アンド シフト ([クラウド インフラストラクチャ対応](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) による移行が適しています。 この場合、オンプレミスのワークロードは変更なしでクラウドベースの VM に再ホストされます。 このアプローチでは、[IaaS (サービスとしてのインフラストラクチャ)](https://azure.microsoft.com/overview/what-is-iaas/) モデルを使用します。 Azure には、このような移行を容易にするために、[Azure Migrate](https://azure.microsoft.com/services/azure-migrate/)、[Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)、[Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) など、いくつかのツールが用意されています。 この戦略により、ある程度のコストを削減できますが、通常、そのようなアプリケーションは、クラウド コンピューティングの利点を引き出して活用するようには設計されていません。

ビジネスに不可欠なモノリシック アプリは、多くの場合、強化されたリフト アンド シフト (*クラウド最適化型*) による移行が適しています。 このアプローチには、アプリケーションのコア アーキテクチャを変更することなく、主要なクラウド サービスを有効にするデプロイの最適化が含まれています。 たとえば、アプリケーションを[コンテナー化](/virtualization/windowscontainers/about/)して、本書で後述する [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/) などのコンテナー オーケストレーターにデプロイすることができます。 クラウド内では、データベース、メッセージ キュー、監視、分散キャッシュなどの他のクラウド サービスがアプリケーションに使用される可能性があります。

最後に、戦略的なエンタープライズ機能を実行するモノリシック アプリの場合、本書の主題である "*クラウドネイティブ*" アプローチが最適な可能性があります。 このアプローチには機敏性とベロシティがあります。 ただし、プラットフォームの再構築、再設計、コードの書き換えにはコストがかかります。

あなたとチームがクラウドネイティブ アプローチが適切であると考えるなら、その決定について組織に理論的に説明することをお勧めします。 クラウドネイティブ アプローチによって解決するビジネス上の問題とは、正確には何でしょうか。 ビジネス ニーズとどのように調和しますか。

- より高い信頼性で機能を迅速にリリースできますか。

- きめ細かいスケーラビリティを備え、リソースをより効率的に使用していますか。

- システムの回復性は向上しますか。

- システムのパフォーマンスは向上しますか。

- 操作の可視性は向上しますか。

- 開発プラットフォームとデータ ストアを融合させ、仕事に最適なツールを実現できますか。

- 将来を見据えたアプリケーションへの投資ですか。

適切な移行戦略は、組織の優先順位と対象とするシステムによって異なります。 モノリシック アプリケーションをクラウドに最適化するか、n 層アプリに粒度の粗いサービスを追加する方が費用効果が高いことはよくあります。 このような場合でも、Azure App Service によって提供されるようなクラウド PaaS 機能を十分に活用できます。

## <a name="summary"></a>まとめ

この章では、クラウドネイティブ コンピューティングについて紹介しました。 クラウドネイティブ アプリケーションを推進する主要な機能と共に、定義について説明しました。 このような投資と労力を正当化できるようなアプリケーションの種類についても説明しました。

導入部を終えて、これからクラウド ネイティブについてさらに詳しく説明します。

### <a name="references"></a>リファレンス

- [Cloud Native Computing Foundation](https://www.cncf.io/)

- [.NET Microservices: Architecture for Containerized .NET applications (.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ)](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Azure クラウドと Windows コンテナーで既存の .NET アプリケーションを最新式にする](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [Cloud Native Patterns (クラウド ネイティブ パターン) (Cornelia Davis 著)](https://www.manning.com/books/cloud-native-patterns)

- [Beyond the Twelve-Factor Application (Twelve-Factor アプリケーションを超えて)](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [コードとしてのインフラストラクチャとは](/azure/devops/learn/what-is-infrastructure-as-code)

- [Uber Engineering's Micro Deploy: Deploying Daily with Confidence (Uber エンジニアリングのマイクロ デプロイ: 自信を持って毎日デプロイする)](https://eng.uber.com/micro-deploy/)

- [How Netflix Deploys Code (Netflix によるコードのデプロイ方法)](https://www.infoq.com/news/2013/06/netflix/)

- [Overload Control for Scaling WeChat Microservices (WeChat マイクロサービスをスケーリングするためのオーバーロード制御)](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
>[前へ](definition.md)
>[次へ](introduce-eshoponcontainers-reference-app.md)
