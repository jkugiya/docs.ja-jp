---
title: デプロイ戦略
description: ASP.NET から ASP.NET Core に移行する際に、チームはどのような展開戦略を使用できるでしょうか? 段階的移行を使用すると、.NET Framework アプリと .NET Core アプリをサイドバイサイドで展開してシームレスなエンド ユーザー エクスペリエンスを実現できるでしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 6691a4878205d6422cf8b6153353abefd9764d18
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401383"
---
# <a name="deployment-strategies"></a>デプロイ戦略

大規模な ASP.NET アプリの ASP.NET Core への移行を計画するときの考慮事項の 1 つに、新しいアプリをどのように展開するかという点があります。 ASP.NET では、展開オプションは Windows 上の IIS のみに限られていました。 ASP.NET Core では、はるかに幅広い展開オプションが用意されています。

## <a name="cross-platform-options"></a>クロスプラットフォーム オプション

.NET Core は Linux 上で実行されるため、以前は検討対象になかったホスティング オプションを利用できます。 以下の理由から、Linux ベースのホスティングをお勧めします。

* 組織にインフラストラクチャや専門知識がある。
* Linux ベースのホスティングに関しては、ホスティング プロバイダーから魅力的な機能や価格が提供されている。

.NET Core により、これらのオプションを利用する機会が得られます。

## <a name="cloud-native-development"></a>クラウド ネイティブ開発

今日のほとんどの組織は、少なくともそのソフトウェア機能の一部に対して、クラウド プラットフォームを使用しています。 .NET Core へのアプリの移行に伴い、意図的にクラウド ホスティングを念頭に置いてアプリを記述するべきかどうかを検討することをお勧めします。 このような "*クラウド ネイティブ*" アプリは、サーバーレスやマイクロサービスなどのクラウド機能を適用しやすく、それらの展開方法や展開場所といった下位レベルの詳細についての懸念も少なくなります。

クラウド ネイティブ アプリの開発の詳細については、無料の電子書籍「[Azure 向けクラウド ネイティブ .NET アプリケーションの設計](../cloud-native/index.md)」を参照してください。

## <a name="leverage-containers"></a>コンテナーの利用

最新のアプリでは、多くの場合、ホスト環境間のばらつきを低減する手段としてコンテナーを利用しています。 特定のコンテナーにアプリを展開することにより、そのコンテナーでホストされるアプリを開発者のノート PC 上でも運用環境でも同じように実行できるようになります。 .NET Core への移行の一環として、コンテナーを使用して (1 つの完全なモノリスとして、または複数のより小規模なコンテナー化されたアプリに分割して) 展開することでアプリがベネフィットを得られるかどうかを検討することは理にかなっています。

## <a name="side-by-side-deployment-options"></a>サイドバイサイド展開オプション

多くの場合、大規模な .NET Framework アプリを .NET Core に移行するにはかなりの作業量が必要となります。 ほとんどの組織では、この作業を何らかの方法で分割して、移行全体を完了する前にアプリの一部を移行し、運用環境に展開できるようにしたいと考えることでしょう。 元の ASP.NET アプリとその新しく移行された ASP.NET Core サブアプリをサイドバイサイドで実行することは、よく挙げられる目標です。 これは IIS ルーティングの活用など、さまざまなメカニズムによって実現できます。これについては[第 5 章](deployment-scenarios.md)で説明します。 その他のオプションとしては、アプリ ゲートウェイやクラウド設計パターン ([フロントエンド用バックエンド](/azure/architecture/patterns/backends-for-frontends) など) を利用して一連の ASP.NET Web API と ASP.NET Core API エンドポイントを管理する方法などがあります。

## <a name="iis-on-windows"></a>Windows 上の IIS

Windows で実行されている IIS 上で、引き続きアプリをホストできます。 これは、現在の展開モデルを変更することなく ASP.NET Core の機能を利用したいと考えているお客様に適したオプションです。 ASP.NET Core への移行時には、アプリの展開方法と展開場所に関して幅広いオプションが用意されていますが、Windows 上の IIS という定評のある組み合わせを使用している現状を変えなければならないわけではありません。

## <a name="other-options-on-windows"></a>Windows 上のその他のオプション

必要に応じて、Docker コンテナーに加えて Kestrel、HTTP.sys、および IIS ホストの任意の組み合わせを使用して、アプリを Windows 上でサイドバイサイドでホストすることができます。 アプリで Windows のサービスと Linux のサービスを組み合わせる必要がある場合は、[WSL](/windows/wsl/about) または Linux Docker コンテナー (あるいはその両方) を使用して Windows サーバー上でホストすることで、アプリのすべての部分をホストする単一のソリューションを提供できます。

## <a name="references"></a>リファレンス

- [ASP.NET Core のホストと展開](/aspnet/core/host-and-deploy/)
- [IIS を使用した Windows での ASP.NET Core のホスト](/aspnet/core/host-and-deploy/iis/)
- [Azure App Service および IIS での ASP.NET Core のトラブルシューティング](/aspnet/core/test/troubleshoot-azure-iis)

>[!div class="step-by-step"]
>[前へ](migrate-web-forms.md)
>[次へ](additional-migration-resources.md)
