---
title: デプロイ戦略
description: ASP.NET から ASP.NET Core に移行する際にチームが使用できるデプロイ戦略 増分移行により、.NET Framework と .NET Core アプリをサイドバイサイドでデプロイできるため、シームレスなエンドユーザーエクスペリエンスが実現しますか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 6691a4878205d6422cf8b6153353abefd9764d18
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401383"
---
# <a name="deployment-strategies"></a>デプロイ戦略

ASP.NET Core するための大規模な ASP.NET アプリの移行を計画する際の考慮事項の1つは、新しいアプリをデプロイする方法です。 ASP.NET では、配置オプションは Windows 上の IIS に限定されていました。 ASP.NET Core を使用すると、より広範な展開オプションを利用できます。

## <a name="cross-platform-options"></a>クロスプラットフォームオプション

.NET Core は Linux 上で実行されるため、以前は考慮されていなかったホスティングオプションを利用できます。 Linux ベースのホスティングは、次の理由で推奨されます。

* 組織にはインフラストラクチャまたは専門知識があります。
* ホスティングプロバイダーは、Linux ベースのホスティングの優れた機能や価格を提供します。

.NET Core が開き、これらのオプションが表示されます。

## <a name="cloud-native-development"></a>クラウドネイティブ開発

現在、ほとんどの組織は、少なくともそのソフトウェア機能の一部に対してクラウドプラットフォームを使用しています。 .NET Core へのアプリの移行では、クラウドホスティングを考慮してアプリを意図的に記述する必要があるかどうかを検討することをお勧めします。 このような *クラウドネイティブ* アプリでは、サーバーレスのマイクロサービスのようなクラウド機能を適用することができ、デプロイの方法と場所の下位レベルの詳細についてはあまり注意が必要ありません。

クラウドネイティブアプリの開発の詳細については、 [Azure 向けのクラウドネイティブ .Net アプリケーションの設計](../cloud-native/index.md)に関するページを参照してください。

## <a name="leverage-containers"></a>コンテナーを活用する

モダンアプリでは、多くの場合、ホスト環境間の変動を減らす手段としてコンテナーを利用しています。 アプリを特定のコンテナーにデプロイすることによって、コンテナーでホストされるアプリは、開発者のノート pc で実行されているか、運用環境で実行されているかにかかわらず、同じように動作します。 .NET Core への移行の一環として、アプリが完全なモノリスとして、または複数の小さなコンテナー化されたアプリに分割されている場合でも、コンテナーを使用したデプロイによってメリットが得られるかどうかを検討することが理にかなっています。

## <a name="side-by-side-deployment-options"></a>サイドバイサイド展開オプション

多くの場合、大規模な .NET Framework アプリを .NET Core に移行するにはかなりの労力が必要です。 ほとんどの組織では、この作業を何らかの方法で中断できるようにする必要があります。これにより、移行全体が完了する前に、アプリの一部を運用環境に移行して展開することができます。 元の ASP.NET アプリと新しく移行された ASP.NET Core サブアプリの両方をサイドバイサイドで実行することは、よく見られる目標です。 これは、 [5 章](deployment-scenarios.md)で説明されている IIS ルーティングを利用するなど、さまざまなメカニズムによって実現できます。 その他のオプションとしては、アプリゲートウェイを利用したり、 [バックエンドのフロントエンドの](/azure/architecture/patterns/backends-for-frontends) ようなクラウド設計パターンを使用して ASP.NET Web api のセットを管理したり、api エンドポイントを ASP.NET Core できます。

## <a name="iis-on-windows"></a>Windows 上の IIS

Windows で実行されている IIS でアプリのホスティングを続行できます。 これは、現在のデプロイメントモデルを変更せずに ASP.NET Core の機能を利用することを希望するお客様にとっては、この方法が適しています。 ASP.NET Core への移行では、アプリを展開する方法と場所に関してより多くのオプションが提供されますが、Windows で実証済みの IIS の組み合わせを使用している状態から変更する必要はありません。

## <a name="other-options-on-windows"></a>Windows のその他のオプション

必要に応じて、Docker コンテナーに加えて、Kestrel、HTTP.sys、および IIS ホストの任意の組み合わせを使用して、Windows 上でアプリをサイドバイサイドでホストすることができます。 アプリで Windows と Linux のサービスを組み合わせて使用する必要がある場合は、 [Wsl](/windows/wsl/about) および linux Docker コンテナーがある windows server でホストすることで、アプリのすべての部分をホストする単一のサーバーソリューションを提供します。

## <a name="references"></a>関連項目

- [ASP.NET Core のホストと展開](/aspnet/core/host-and-deploy/)
- [IIS を使用した Windows での ASP.NET Core のホスト](/aspnet/core/host-and-deploy/iis/)
- [Azure App Service および IIS での ASP.NET Core のトラブルシューティング](/aspnet/core/test/troubleshoot-azure-iis)

>[!div class="step-by-step"]
>[前へ](migrate-web-forms.md)
>[次へ](additional-migration-resources.md)
