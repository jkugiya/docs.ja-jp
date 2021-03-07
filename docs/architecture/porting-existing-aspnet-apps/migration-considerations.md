---
title: 移行に関する考慮事項
description: ASP.NET MVC から .NET Core に移行するかどうか、およびその方法を適切に判断するために、チームは何を知る必要がありますか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: efa1efc99cbe46ef289cfd6b53ba83b3bc1b56b1
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102401479"
---
# <a name="migration-considerations"></a>移行に関する考慮事項

アプリケーションを .NET Core に移植する場合は、最も基本的な質問に答える必要があります。 場合によっては、ASP.NET MVC または Web API を使用して .NET Framework のままにしておくことをお勧めします。 この章では、.NET Core への移行が理にかなっている理由を検討します。 この章では、.NET Framework を維持するためのシナリオと方法についても検討します。

## <a name="is-migration-to-net-core-appropriate"></a>.NET Core への移行は適切ですか?

.NET Core (または .NET 5) に移行する理由のいくつかから始めましょう。 非常に多くのことがあるため、この一覧を完全に考慮しないでください。

### <a name="cross-platform-support"></a>クロスプラットフォームのサポート

.NET Core 上に構築されたアプリは、完全にクロスプラットフォームであり、Windows、Linux、macOS で実行できます。 開発者は必要なハードウェアをどれでも使用できますが、アプリをどこでもホストできます。 例として、ローカル IIS からクラウド内の Azure、または Linux Docker コンテナーから IoT デバイスまでの範囲があります。

### <a name="performance-and-scalability"></a>パフォーマンスと拡張性

.NET Core でビルドされたアプリは [、どこからでも利用できる最速の技術スタックの1つ](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext)で実行されています。 ASP.NET MVC アプリでは、多くの場合、ASP.NET Core のパフォーマンスが向上しています。 .NET Core で利用可能な新機能を利用するために更新された場合は特にそうです。

### <a name="cloud-native"></a>クラウドネイティブ

上記の理由により、.NET Core アプリはクラウドホスティング環境での実行に適しています。 軽量で高速な .NET Core アプリを Azure アプリサービスまたはコンテナーにデプロイし、必要に応じて水平方向に拡張して、システムの需要を即座に満たすことができます。

### <a name="maintainable"></a>保持

多くのアプリでは、顧客とビジネスのニーズに対応しつつ、技術的な負債が蓄積され、アプリのコストが高くなりました。 ASP.NET Core のアプリは、ASP.NET MVC アプリよりも簡単にテストできます。これにより、リファクタリングが容易になり、自信を持って拡張することができます。

### <a name="modular"></a>モジュール式

ASP.NET Core は、フレームワークのファーストクラスの部分として NuGet パッケージを使用してモジュール化されています。 .NET Core 用に構築されたアプリはすべて、依存関係の注入をサポートしているため、特定の環境に必要な任意の実装からソリューションを簡単に作成できます。 .NET Core でのマイクロサービスの構築は、ASP.NET MVC を使用するよりも簡単です。 IIS に依存しているため、大規模なアプリを小さなモジュールに分割するための追加オプションが表示されます。

### <a name="modern"></a>モダン

積極的に開発されたテクノロジスタックを最新の状態に保つことには、利点があります。 新機能と C# 言語機能は、.NET Core にのみ追加されます。 .NET Framework にはバージョン4.8 の最新リリースがあり、8を超えるバージョンの C# では .NET Framework が対象になりません。 ASP.NET MVC は長年にわたってマイクロソフトによってサポートされていますが、最も優れている .NET ソフトウェア開発者は、より最新の .NET Core フレームワークを使用することを検討しています (上記の一部のみを紹介します)。 ASP.NET MVC アプリを維持するためのスキルを持つ開発者を見つけることは、オンライントレーニングとトラブルシューティングのサポートを見つけるために、ある時点での課題になり始めます。 多くの場合、ASP.NET MVC 5 については新しいブログ投稿が作成されていませんが、.NET 5.0 向けには十分に記述されています。

.NET Core への移行を検討すべき説得力のある理由は多数ありますが、この書籍を読むのはなぜでしょうか。 しかし、いくつかの欠点と、.NET Framework に残しておくと意味がある理由について考えてみましょう。

## <a name="when-is-net-framework-appropriate"></a>が .NET Framework 適切な場合

.NET Framework を維持する最大の理由は、アプリがアクティブに開発されていないときに、上記の利点を最大限に活用できないことです。 このような場合は、アプリの移植にかかるコストを発生させるという優れたビジネスケースではありません。 アプリが .NET Core の特典の利点を活用できる場合は、.NET Core で使用できない特定のテクノロジが必要な場合は .NET Framework に続ける必要があります。 [.Net Core で使用できない .net テクノロジ](../../core/porting/net-framework-tech-unavailable.md)がいくつかあります。これには、AppDomains、リモート処理、コードアクセスセキュリティ (CAS)、透過的セキュリティ、およびが含まれ `System.EnterpriseServices` ます。 これらのテクノロジとその代替方法の概要については、こちらを参照してください。 詳細なガイダンスについては、のドキュメントを参照してください。

### <a name="application-domains"></a>アプリケーション ドメイン

アプリケーション ドメイン (AppDomains) はアプリを互いに分離します。 AppDomains ではランタイムサポートが必要であり、負荷が高くなる可能性があります。 追加のアプリドメインの作成はサポートされておらず、今後 .NET Core にこの機能を追加する予定はありません。 コードの分離のためには、代替方法として別個のプロセスやコンテナーを使用します。

### <a name="wcf"></a>WCF

サーバー側 WCF は、.NET Core ではサポートされていません。 .NET Core は wcf クライアントをサポートしますが、WCF ホストはサポートしません。 この機能を必要とするアプリは、移行の一環として別の通信テクノロジ (gRPC や REST など) にアップグレードする必要があります。

[.Net Foundation で使用可能な WCF クライアントポート](../../core/dotnet-five.md#windows-communication-foundation)があります。 これは、完全にオープンソースであり、クロスプラットフォームで、Microsoft によってサポートされています。 また、マイクロソフトによって正式にサポートされて *いない* コミュニティでサポートされている [corewcf プロジェクト](https://github.com/CoreWCF/CoreWCF)もあります。

### <a name="remoting"></a>リモート処理

.NET リモート処理は、問題のあるアーキテクチャであると判断されました。 AppDomain 間の通信で使用されていますが、今後はサポートされなくなります。 また、リモート処理にはランタイム サポートが必要で、維持するのに高いコストがかかります。 このような理由から、.net リモート処理は .NET Core ではサポートされておらず、製品チームは将来のサポートの追加を計画していません。 .NET Core アプリのリモート処理を置き換えるために使用できる、いくつかの代替メッセージング戦略と実装があります。

### <a name="code-access-security-cas-and-security-transparency"></a>コードアクセスセキュリティ (CAS) とセキュリティの透過性

これらのテクノロジはどちらも .NET Core ではサポートされていません。 代わりに、オペレーティングシステムによって提供されるセキュリティ境界を使用することをお勧めします。 たとえば、仮想化、コンテナー、ユーザーアカウントなどです。 必要最小限の特権セットでプロセスを実行します。

## <a name="references"></a>関連項目

[.NET Core で使用できない .NET Framework テクノロジ](../../core/porting/net-framework-tech-unavailable.md)

>[!div class="step-by-step"]
>[前へ](introduction.md)
>[次へ](migrate-aspnet-core-2-1.md)
