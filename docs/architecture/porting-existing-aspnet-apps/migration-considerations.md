---
title: 移行に関する注意事項
description: ASP.NET MVC から .NET Core に移行するかどうか、およびその方法について適切に判断するために、チームが知っておくべきことは何でしょうか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: c669dc477469c92dfa3acda8209ba7a1fdea5ed5
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122860"
---
# <a name="migration-considerations"></a>移行に関する注意事項

.NET Core へのアプリの移植についてチームが答えなければならない最も基本的な質問は、"そもそもアプリを移植する必要があるのか" です。 ASP.NET MVC または Web API を使用して .NET Framework を維持するのが将来的に最適な方針である場合もあります。 この章では、.NET Core への移行が理にかなっている理由について考察します。 また、.NET Framework を維持するためのシナリオと方法についても考察します。

## <a name="is-migration-to-net-core-appropriate"></a>.NET Core への移行が適切かどうか

まずは .NET Core (または .NET 5) への移行が推奨されるいくつかの理由を確認してみましょう。 このリストに挙げたものは一部であり、他にも多くの理由があります。

### <a name="cross-platform-support"></a>クロスプラットフォームのサポート

.NET Core 上に構築されたアプリは、真のクロスプラットフォームであり、Windows、Linux、macOS で実行できます。 開発者が必要なハードウェアを使用できるだけでなく、ユーザーがアプリをどこででもホストできます。 たとえば、ローカル IIS からクラウド内の Azure まで、または Linux Docker コンテナーから IoT デバイスまで多岐にわたります。

### <a name="performance-and-scalability"></a>パフォーマンスと拡張性

.NET Core で構築されたアプリは、[場所を問わず利用可能な最速の技術スタックの 1 つ](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext)で実行されています。 ASP.NET MVC アプリでは、(.NET Core で利用可能な新機能を利用するよう更新された場合は特に) ASP.NET Core におけるパフォーマンスの向上が多く見られます。

### <a name="cloud-native"></a>クラウドネイティブ

上記のような理由により、.NET Core アプリはクラウド ホスティング環境での実行に適しています。 軽量で高速な .NET Core アプリを Azure App Service またはコンテナーにデプロイし、必要に応じて水平方向にスケーリングして、システムの需要を即座に満たすことができます。

### <a name="maintainable"></a>保守しやすい

多くのアプリは、顧客とビジネスのニーズへの対応を続ける一方で、技術的負債が蓄積され、アプリを保守するためのコストが増加しています。 ASP.NET Core アプリは ASP.NET MVC アプリよりもテストが簡単であるため、リファクタリングが容易になり、自信を持って拡張できます。

### <a name="modular"></a>モジュール式

ASP.NET Core はモジュール式であり、フレームワークのファーストクラスのパーツとして NuGet パッケージが使用されています。 .NET Core 用に構築されたアプリはすべて依存関係の挿入をサポートしているため、特定の環境に必要な任意の実装からソリューションを簡単に作成できます。 .NET Core でのマイクロサービスの構築は、IIS との依存関係を持つ ASP.NET MVC を使用するよりも簡単です。 .NET Core では、大規模なアプリを小さなモジュールに分割するための追加オプションを使用できます。

### <a name="modern"></a>モダン

積極的に開発されたモダンな技術スタックを維持することには多くの利点があります。 新機能と C# 言語の機能は .NET Core にのみ追加されます。 .NET Framework の最新リリースはバージョン 4.8 であり、バージョン 8 以降の C# は .NET Framework を対象としていません。 ASP.NET MVC は長年にわたり Microsoft によるサポートが続けられていますが、優れた .NET ソフトウェア開発者は (前述した一部のみの) 利点を考慮して、よりモダンな .NET Core フレームワークの使用に目を向けています。 ASP.NET MVC アプリを維持するためのスキルを持つ開発者を探すことは、今後のどこかの時点で課題となるでしょう。これは、オンライン トレーニングやトラブルシューティングの支援が必要になるためです。 おそらく ASP.NET MVC 5 に関する新規のブログ投稿はあまり多くありませんが、.NET 5.0 向けの投稿は豊富にあります。

.NET Core への移行を検討すべき説得力のある理由は多数ありますが、おそらくそれが本書を読んでいる理由でしょう。 しかしここで、いくつかの欠点と、.NET Framework を使用し続ける方が賢明である理由についても考えてみましょう。

## <a name="when-is-net-framework-appropriate"></a>.NET Framework が適している場合

.NET Framework を維持する最大の理由は、アプリが積極的に開発されていない状況では前述の利点を十分に活用できないためです。 このような場合は、アプリの移植にコストをかけるべき優れたビジネス ケースではありません。 アプリが .NET Core の利点を活用できる場合であっても、.NET Core で使用できないテクノロジが必要な状況では .NET Framework を維持する必要があります。 [.NET Core で使用できない .NET テクノロジ](../../core/porting/net-framework-tech-unavailable.md)は、アプリケーション ドメイン、リモート処理、コード アクセス セキュリティ (CAS)、セキュリティ透過性、`System.EnterpriseServices` です。 これらのテクノロジとその代替手段の概要については本書で説明します。 詳細なガイダンスについては、ドキュメントを参照してください。

### <a name="application-domains"></a>アプリケーション ドメイン

アプリケーション ドメイン (AppDomains) はアプリを互いに分離します。 AppDomain にはランタイム サポートが必要で、コストがかかる場合もあります。 追加のアプリケーション ドメインの作成はサポートされておらず、今後この機能を .NET Core に追加する予定はありません。 コードの分離のためには、代替方法として別個のプロセスやコンテナーを使用します。 一部のお客様は、アセンブリをアンロードする手段として AppDomain を使用します。 .NET Core [AssemblyLoadContext](https://docs.microsoft.com/dotnet/standard/assembly/unloadability) には、アセンブリをアンロードするための別の方法が用意されています。

### <a name="wcf"></a>WCF

サーバー側 WCF は、.NET Core ではサポートされていません。 .NET Core では WCF クライアントがサポートされますが、WCF ホストはサポートされません。 この機能が必要なアプリは、移行の一環として別の通信テクノロジ (gRPC や REST など) にアップグレードする必要があります。

[WCF クライアント ポートが .NET Foundation から提供されています](../../core/dotnet-five.md#windows-communication-foundation)。 これは、完全にオープンソースであり、クロス プラットフォームで、Microsoft でサポートされています。 また、コミュニティでサポートされている [CoreWCF プロジェクト](https://github.com/CoreWCF/CoreWCF)もあります。これは、Microsoft では正式にサポートされて "*いません*"。

WCF から gRPC への移行の詳細については、[WCF 開発者向け gRPC](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/) に関する電子ブックを参照してください。

### <a name="remoting"></a>リモート処理

.NET リモート処理は、問題のあるアーキテクチャであると判断されました。 AppDomain 間の通信で使用されていますが、今後はサポートされなくなります。 また、リモート処理にはランタイム サポートが必要で、維持するのに高いコストがかかります。 これらの理由から、.NET リモート処理は .NET Core でサポートされておらず、また製品チームによる将来的なサポートの追加も予定されていません。 .NET Core アプリにおけるリモート処理の代替として、複数のメッセージング戦略と実装を使用できます。

### <a name="code-access-security-cas-and-security-transparency"></a>コード アクセス セキュリティ (CAS) とセキュリティ透過性

これらのテクノロジはどちらも .NET Core ではサポートされていません。 代わりに、オペレーティング システムが提供するセキュリティ境界を使用することをお勧めします。 たとえば、仮想化、コンテナー、ユーザー アカウントなどです。 必要最小限の特権のセットでプロセスを実行してください。

## <a name="references"></a>References

[.NET Core で使用できない .NET Framework テクノロジ](../../core/porting/net-framework-tech-unavailable.md)

>[!div class="step-by-step"]
>[前へ](introduction.md)
>[次へ](migrate-aspnet-core-2-1.md)
