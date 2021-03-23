---
title: Docker コンテナー用 .NET Framework を選択するタイミング
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | Docker コンテナー用 .NET Framework を選択するタイミング'
ms.date: 01/13/2021
ms.openlocfilehash: fa644753c3a39f285052aba7a8524ea96442c842
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873134"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Docker コンテナー用 .NET Framework を選択するタイミング

.NET 5 は新しいアプリケーションとアプリケーション パターンには大きな利点がありますが、既存の多くのシナリオでは引き続き .NET Framework が適切な選択肢となります。

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>既存アプリケーションを Windows Server コンテナーに直接移行する

マイクロサービスを作成していない場合は、デプロイメントを簡略にするためだけでも Docker コンテナーを使用できます。 たとえば、Docker に対する DevOps ワークフローを改善したいとします。コンテナーを使用すると、適切に分離されたテスト環境を確保でき、運用環境に移行したときに依存関係が失われて生じるデプロイメントの問題も解消できます。 このようなケースでは、単体のアプリケーションをデプロイする場合でも、現在の .NET Framework アプリケーションのために Docker および Windows コンテナーを使用するメリットがあります。

このシナリオのほとんどのケースでは、既存のアプリケーションを .NET 5 に移行する必要はありません。従来の .NET Framework を含む Docker コンテナーを使用できます。 しかし、ASP.NET Core で新しいサービスを作成するなど、既存のアプリケーションを拡張するときには .NET 5 を使用することをお勧めします。

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-5"></a>NET 5 で使用できないサードパーティ製の .NET ライブラリや NuGet パッケージの使用

サードパーティ製のライブラリでは [.NET Standard](../../../standard/net-standard.md) の採用が迅速に進められています。これにより、.NET 5 を含むすべての種類の .NET でコードを共有できるようになります。 .NET Standard 2.0 以降、異なるフレームワーク間での API サーフェスの互換性はかなり高くなっています。 さらに、.NET Core 2.x と新しいアプリケーションでは、既存の .NET Framework ライブラリを直接参照することもできます ([.NET Standard 2.0 をサポートする .NET Framework 4.6.1](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20) に関するページを参照してください)。

さらに、[Windows 互換機能パック](../../../core/porting/windows-compat-pack.md)では、Windows の .NET Standard 2.0 で利用可能な API サーフェスが拡張されています。 このパックでは、最小限の変更か、または変更を伴わずに、.NET Standard 2.x のほとんどの既存コードを再コンパイルして、Windows 上で実行できます。

しかし、.NET Standard 2.0 および .NET Core 2.1 以降の進歩が並外れているとしても、特定の NuGet パッケージの実行には Windows が必要であり、.NET Core 以降がサポートされていないケースはあります。 これらのパッケージがアプリケーションに不可欠な場合は、Windows コンテナー上で .NET Framework を使用する必要があります。

## <a name="using-net-technologies-not-available-for-net-5"></a>.NET 5 で利用できない .NET テクノロジの使用

一部の .NET Framework テクノロジは、現在の .NET バージョン (このドキュメント作成時点ではバージョン 5.0) では利用できません。 今後のリリースで使用可能になるものもありますが、それ以外は .NET Core の対象となる新しいアプリケーション パターンには適合せず、使用可能にならない可能性があります。

以下の一覧には、.NET 5 で利用できないテクノロジのほとんどが示されています。

- ASP.NET Web フォーム。 このテクノロジは .NET Framework のみで利用できます。 現時点では、ASP.NET Web Forms を .NET 以降に含める予定はありません。

- WCF サービス。 .NET 5 から WCF サービスを使用する [WCF クライアント ライブラリ](https://github.com/dotnet/wcf)が利用可能な場合でも、2021 年 1 月の時点では、WCF サーバーの実装は .NET Framework でのみ可能です。

- ワークフロー関連サービス。 Windows Workflow Foundation (WF)、ワークフロー サービス (1 つのサービスに WCF と WF) および WCF Data Services (旧称: ADO.NET Data Services) は、NET Framework でのみ使用できます。 現在、これらを .NET 5 に含める予定はありません。

公式の [.NET ロードマップ](https://github.com/dotnet/core/blob/main/roadmap.md)に一覧表示されているテクノロジに加え、他の機能が新しい[統合 .NET プラットフォーム](https://devblogs.microsoft.com/dotnet/introducing-net-5/)に移植される可能性があります。 GitHub でのディスカッションに参加して意見を述べることを検討してください。 また、何か足りないと感じた場合は、[dotnet/runtime](https://github.com/dotnet/runtime/issues/new) GitHub リポジトリで新しい案件を作成してください。

## <a name="using-a-platform-or-api-that-doesnt-support-net-5"></a>.NET 5 をサポートしていないプラットフォームまたは API の使用

Microsoft とサードパーティ製のプラットフォームの中には、.NET 5 をサポートしないものがあります。 たとえば、一部の Azure サービスでは、.NET 5 ではまだ使用できない SDK が提供されています。 ほとんどの Azure SDK は最終的に .NET 5/Standard に移植されるはずですが、いくつかはさまざまな理由で移植されない場合があります。 使用可能な Azure SDK については、[Azure SDK の最新リリース](https://azure.github.io/azure-sdk/releases/latest/index.html) ページを参照してください。

この間、Azure のプラットフォームまたはサービスがそのクライアント API で .NET 5 をまだサポートしていない場合は、Azure サービスまたはクライアント SDK の同等の REST API を .NET Framework で使用できます。

### <a name="additional-resources"></a>その他のリソース

- **.NET の基礎** \
  [https://docs.microsoft.com/dotnet/fundamentals](../../../fundamentals/index.yml)

- **.NET 5 へのプロジェクトの移植** \
  [https://channel9.msdn.com/Events/dotnetConf/2020/Porting-Projects-to-NET-5](https://channel9.msdn.com/Events/dotnetConf/2020/Porting-Projects-to-NET-5)

- **Docker 上の .NET のガイド** \
  [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **.NET コンポーネントの概要** \
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[前へ](net-core-container-scenarios.md)
>[次へ](container-framework-choice-factors.md)
