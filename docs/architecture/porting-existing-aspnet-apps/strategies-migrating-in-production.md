---
title: 運用環境での実行中に移行するための戦略
description: ASP.NET MVC から MVC ASP.NET Core に大規模なアプリを一度に移行することはできない場合があります。 既存のユーザーに対してアプリケーションを実行し、運用環境に維持しながら、ASP.NET Core にアプリを移行する方法について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 4910984cb281139493aa5424809ba3eedab776e9
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401347"
---
# <a name="strategies-for-migrating-while-running-in-production"></a>運用環境での実行中に移行するための戦略

多くのチームは .NET Core への移行を計画している .NET Framework アプリを持っていますが、このアプリは非常に大きいため、移行には長時間かかることがあります。 移行が1つずつ行われている間、元のアプリはライブで実行する必要があります。 古いバージョンと新しいバージョンのアプリを並行して動作させるためには、古いバージョンを使用する必要があります。また、以前のバージョンは、少なくとも一部の方法では中断せずにインプレースで移行します。 チームは、これらの目標をサポートするためにさまざまな戦略を採用できます。

## <a name="refactor-the-net-framework-solution"></a>.NET Framework ソリューションをリファクターする

.NET Framework アプリを .NET Core に移植する予定の場合は、.NET Core で動作するようにリファクタリングすることをお勧めします。 これは、個々のクラスライブラリを .NET Standard ターゲットに更新し、ASP.NET MVC プロジェクトからこれらのクラスライブラリに対して、より多くのロジックを移行することを意味します。 .NET Standard ライブラリにあるコードは、.NET Framework から .NET Core に比較的簡単に移行できます。

リファクタリングを行うときは、適切なリファクタリングの基礎に従うようにしてください。 たとえば、リファクタリングを開始する前にシステムの動作を確認するテストを作成します。 システムの動作が変更されていないことを確認したら、これらのテストを実行します。 利用できる自動テストの適切なスイートがまだない場合は、システムに特性テストを追加することが必要になる場合があります。

## <a name="extract-front-end-assets-to-a-cdn"></a>CDN へのフロントエンドアセットの抽出

.NET Framework アプリにスクリプト、CSS ファイル、イメージなどの多数の静的資産が含まれている場合は、それらを別の CDN に移行できる可能性があります。 次に、既存のアプリを更新して、これらの資産の CDN リンクを参照します。 アプリケーションを .NET Core に移植すると、これらの静的ファイルは移行の一部にはならず、引き続き ASP.NET Core アプリの CDN からそれらのファイルを参照することになります。

## <a name="extract-and-migrate-individual-microservices"></a>個々のマイクロサービスを抽出して移行する

大規模な .NET Framework アプリは、個別に移行できる個別のフロントエンドシステムで既に構成されている場合があります。 または、マイクロサービスアーキテクチャへの移行の候補である場合もあります。既存の ASP.NET MVC アプリの一部は、新しい ASP.NET Core マイクロサービスの実装に取り込まれます。 マイクロサービスの詳細については、関連付けられている電子ブック「 [.Net マイクロサービス: コンテナー化された .Net アプリケーションのアーキテクチャ](https://aka.ms/microservicesebook)」を参照してください。

たとえば、既存のアプリには、ユーザーのサインインと登録に関連する一連の機能が含まれている場合があります。 これらは別のマイクロサービスに移行することができます。これは、ASP.NET Core を使用して構築およびデプロイし、従来の .NET Framework アプリに統合することができます。 次に、アプリには、個々のユーザーのショッピングカートの追跡専用のページがいくつか含まれている場合があります。 これらのページは、独自の個別のマイクロサービスに取り込まれ、既存のアプリにも統合される可能性があります。 この方法では、元の .NET Framework アプリは運用環境で実行されますが、最新の .NET Core マイクロサービスからの多くの機能が含まれます。

## <a name="deploy-multiple-versions-of-the-app-side-by-side-in-iis"></a>IIS で複数のバージョンのアプリをサイドバイサイドで展開する

ホストヘッダーとリダイレクトの組み合わせを使用して、既存の ASP.NET MVC アプリを同じ IIS サーバー上の ASP.NET Core アプリとサイドバイサイドで実行するように構成することができます。 個々のコントローラーなどの機能の一部が ASP.NET Core に移植されると、そのルートと Url は、ASP.NET Core web サイトまたはサブアプリケーションを対象とするように IIS 内でマップされます (IIS 仮想ディレクトリは ASP.NET Core アプリではサポートされません)。 ASP.NET Core アプリは IIS サブアプリケーション (サブアプリ) としてホスティングできます。 サブアプリのパスは、ルート アプリの URL の一部になります。

## <a name="apply-the-strangler-pattern"></a>ストラングラーパターンを適用する

大規模な ASP.NET MVC アプリは、機能の一部を段階的に移行することにより、新しい ASP.NET Core アプリに段階的に置き換えることができます。 この方法の1つとして、 [ストラングラーパターン](/azure/architecture/patterns/strangler)という名前が付けられています。ストラングラー vines は strangle で、最終的にツリーを破棄します。 この方法は、最初に既存のソリューションの上にファサード層を実装することに依存します。 このファサードは、問題に対する新しいアプローチ、または API ゲートウェイなどの既製のソリューションを使用して構築する必要があります。

ファサードが配置されたら、その一部を新しい ASP.NET Core アプリにルーティングできます。 元の .NET Framework アプリの数を .NET Core に移植するときは、それに応じてファサード層を更新して、façade's の合計機能を新しいシステムに送信します。 図3-5 は、時間の経過に伴うストラングラーパターンの進行を示しています。

## <a name="multi-targeting-approaches"></a>複数のターゲットを設定する方法

.NET Framework を対象とする大規模なアプリは、複数のターゲットを使用し、各フレームワークに個別のコードパスを使用することによって、ASP.NET Core に移行できます。 たとえば、両方の環境で実行する必要があるコードは、異なる機能を実装するために[プリプロセッサ `#if` ](../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)ディレクティブを使用して変更することも、.net Core .NET Framework で実行する場合は異なる依存関係を使用することもできます。 別の方法として、プロジェクトファイルを変更して、対象となるフレームワークに基づいて異なるファイルセットを含めることもできます。 プロジェクトファイル `*.core.cs` では、対象となるフレームワークに応じて、さまざまなグロビングパターン (など) を使用して、さまざまなソースファイルセットを含めることができます。

これらの手法によって、新しい機能が追加されたときに1つの共通コードベースを保持し、.NET Core を使用するようにアプリを移植することができます。

![図3-5](media/Figure3-5.png)

**図 3-5.** 時間の経過に伴うストラングラーパターン。

最終的には、ファサード層全体が、新しい先進の実装に対応します。 この時点で、レガシシステムと face レイヤーの両方を廃止できます。

## <a name="summary"></a>まとめ

多くの場合、大規模な ASP.NET MVC と Web API アプリは、一度に ASP.NET Core に移植されることはありませんが、時間の経過と共に段階的に移行されます。 このセクションでは、この増分移行を実行するためのいくつかの方法について説明します。 組織とアプリに最適なものを1つ選択します。

## <a name="references"></a>関連項目

- [.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ](https://aka.ms/microservicesebook)
- [eShopOnContainers リファレンスマイクロサービスアプリケーション](https://github.com/dotnet-architecture/eShopOnContainers)
- [IIS を使用した Windows での ASP.NET Core のホスト](/aspnet/core/host-and-deploy/iis/)
- [ストラングラー パターン](/azure/architecture/patterns/strangler)

>[!div class="step-by-step"]
>[前へ](understand-update-dependencies.md)
>[次へ](example-migration-eshop.md)
