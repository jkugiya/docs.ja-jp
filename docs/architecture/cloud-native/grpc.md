---
title: gRPC
description: gRPC について、クラウドネイティブ アプリケーションにおけるその役割、HTTP RESTful 通信との違いを説明します。
author: robvet
no-loc:
- Blazor
- Blazor WebAssembly
ms.date: 01/19/2021
ms.openlocfilehash: 8667f2d3a7a19aa6dffdd8ce8bef103eab5cc54f
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505701"
---
# <a name="grpc"></a>gRPC

本書では、これまで [REST ベース](/azure/architecture/best-practices/api-design)の通信に焦点を当ててきました。 REST は、エンティティ リソースに対する CRUD ベースの操作を定義する柔軟なアーキテクチャ スタイルであることを見てきました。 クライアントは、HTTP を介して要求と応答の通信モデルでリソースと対話します。 REST は広く実装されていますが、新しい通信テクノロジである gRPC には、クラウドネイティブ コミュニティ全体で大きな勢いがあります。

## <a name="what-is-grpc"></a>gRPC とは

gRPC は、古い[リモート プロシージャ コール (RPC)](https://en.wikipedia.org/wiki/Remote_procedure_call) プロトコルを進化させる最新のハイパフォーマンス フレームワークです。 アプリケーション レベルでは、gRPC により、クライアントとバックエンド サービス間のメッセージングが合理化されます。 Google から提供されている gRPC はオープンソースであり、クラウドネイティブ オファリングの [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) エコシステムの一部です。 CNCF は、gRPC を [Incubating (発展中) プロジェクト](https://github.com/cncf/toc/blob/master/process/graduation_criteria.adoc)と見なしています。 Incubating とは、エンドユーザーが運用アプリケーションでそのテクノロジを使用しており、プロジェクトには多数の貢献者がいることを意味します。

一般的な gRPC クライアント アプリの場合、ビジネス操作を実装するローカルなインプロセス関数が公開されます。 内部的には、そのローカル関数により、リモート マシン上の別の関数が呼び出されます。 ローカルの呼び出しのように見えますが、本質的には、リモート サービスへの透過的なアウトプロセス呼び出しです。 RPC のプラミングにより、コンピューター間のポイントツーポイント ネットワーク通信、シリアル化、および実行が抽象化されます。

クラウドネイティブ アプリケーションの場合、開発者は複数のプログラミング言語、フレームワーク、テクノロジにまたがって作業することがよくあります。 この "*相互運用性*" により、クロスプラットフォームの通信に必要なメッセージ コントラクトとプラミングが複雑になります。  gRPC には、このような懸案事項を抽象化する "均一な水平レイヤー" が用意されています。 開発者は、ビジネス機能に集中して、ネイティブ プラットフォームでコードを書き、通信のプラミングは gRPC で処理します。

gRPC は、Java、JavaScript、C#、Go、Swift、NodeJS など、ほとんどの一般的な開発スタックを包括的にサポートしています。

## <a name="grpc-benefits"></a>gRPC の利点

gRPC では、トランスポート プロトコルとして HTTP/2 が使用されます。 HTTP/2 は、HTTP 1.1 との互換性を持ちながら、多くの先進的な機能を備えています。

- データ転送のためのバイナリ フレーミング プロトコルです。テキストベースの HTTP 1.1 とは異なります。
- 同じ接続を介して複数の並列要求を送信するための多重化のサポート。HTTP 1.1 の場合、処理が一度に 1 つの要求および応答メッセージに制限されています。
- クライアント要求とサーバー応答の両方を同時に送信するための双方向全二重通信。
- 大規模なデータセットを非同期にストリーミングするための要求と応答を可能にする組み込みのストリーミング。
- ネットワークの使用量を減らすヘッダー圧縮。

gRPC は軽量でハイ パフォーマンスです。 メッセージが 60-80% 小さいので JSON シリアル化よりも最大 8 倍高速になる可能性があります。 Microsoft [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) によると、gRPC のパフォーマンスは、高度に最適化された [NetTCP バインディング](/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8)の速度と効率を上回っています。 Microsoft スタックを優先する NetTCP とは異なり、gRPC はクロスプラットフォームです。

## <a name="protocol-buffers"></a>プロトコル バッファー

gRPC は[プロトコル バッファー](https://developers.google.com/protocol-buffers/docs/overview)というオープンソースのテクノロジを採用しています。 サービスが相互に送信する構造化メッセージをシリアル化するための、非常に効率的でプラットフォームに依存しないシリアル化形式が用意されています。 開発者は、クロスプラットフォームの インターフェイス定義言語 (IDL) を使用して、各マイクロサービスのサービスのサービス コントラクトを定義します。 コントラクトはテキストベースの `.proto` ファイルとして実装され、各サービスのメソッド、入力、出力が記述されます。 同じコントラクト ファイルを、異なる開発プラットフォームで構築された gRPC クライアントやサービスに使用することができます。

proto ファイルを使用すると、Protobuf コンパイラ `protoc` によってターゲット プラットフォーム用のクライアントとサービスの両方のコードが生成されます。 このコードには次のコンポーネントが含まれています。

- クライアントとサービスによって共有される厳密に型指定されたオブジェクト。メッセージのサービス操作とデータ要素を表します。
- リモート gRPC サービスによって継承および拡張できる、必要なネットワーク プラミングを備えた厳密に型指定された基底クラス。
- リモート gRPC サービスを呼び出すための必要なプラミングを含むクライアント スタブ。

ランタイムには、各メッセージは標準的な Protobuf 表現としてシリアル化され、クライアントとリモート サービスの間で交換されます。 JSON や XML とは異なり、Protobuf メッセージはコンパイルされたバイナリ バイトとしてシリアル化されます。

Microsoft アーキテクチャのサイトから入手できるドキュメント「[WCF 開発者向け gRPC](../grpc-for-wcf-developers/index.md)」には、gRPC とプロトコル バッファーについて詳しく説明されています。

## <a name="grpc-support-in-net"></a>.NET での gRPC のサポート

gRPC は、.NET Core 3.0 SDK 以降に統合されています。 次のツールでサポートされています。

- Web 開発ワークロードがインストールされた Visual Studio 2019 (バージョン 16.3 以降)。
- Visual Studio Code
- dotnet CLI

SDK には、エンドポイントのルート指定、組み込みの IoC、およびログのためのツールが含まれています。 オープンソースの Kestrel Web サーバーは、HTTP/2 接続をサポートしています。 図 4-20 は、gRPC サービスのスケルトン プロジェクトをスキャフォールディングした Visual Studio 2019 テンプレートを示しています。 .NET が Windows、Linux、および macOS を完全にサポートしていることに注目してください。

![Visual Studio 2019 での gRPC のサポート](./media/visual-studio-2019-grpc-template.png)

**図 4-20** Visual Studio 2019 での gRPC のサポート
  
図 4-21 は、Visual Studio 2019 に含まれる組み込みのスキャフォールディングから生成されたスケルトン gRPC サービスを示しています。  

![Visual Studio 2019 での gRPC プロジェクト](./media/grpc-project.png  )

**図 4-21** Visual Studio 2019 での gRPC プロジェクト

前の図の proto 記述ファイルとサービス コードに注目してください。 すぐに分かるように、Visual Studio により、Startup クラスと基礎となるプロジェクト ファイルの両方に追加の構成が生成されます。

## <a name="grpc-usage"></a>gRPC の使用

次のようなシナリオでは、gRPC を優先します。

- バックエンドのマイクロサービス間の同期通信で、処理を継続するために即時の応答が必要な場合。
- プログラミング プラットフォームが混在するポリグロット環境。
- パフォーマンスが重要な低待機時間および高スループットの通信。
- ポイントツーポイントのリアルタイム通信。gRPC により、ポーリングを行わずにリアルタイムでメッセージをプッシュすることができ、双方向のストリーミングにも優れた対応をしています。
- ネットワークに制約のある環境。バイナリ gRPC メッセージは、同等のテキストベースの JSON メッセージよりも常に小さくなります。

この記事の執筆時点では、gRPC は主にバックエンド サービスで使用されています。 最新のブラウザーには、フロントエンドの gRPC クライアントをサポートするために必要なレベルの HTTP/2 制御機能がありません。 とはいえ、JavaScript や Blazor WebAssembly テクノロジを使用して構築されたブラウザーベースのアプリからの gRPC 通信を可能にする [gRPC-Web with .NET](https://devblogs.microsoft.com/aspnet/grpc-web-for-net-now-available/) がサポートされています。 [gRPC-Web](https://github.com/grpc/grpc/blob/master/doc/PROTOCOL-WEB.md) を使用すると、ASP.NET Core gRPC アプリがブラウザー アプリで gRPC 機能をサポートできるようになります。

- 厳密に型指定されたコード生成クライアント
- コンパクトな Protobuf メッセージ
- サーバー ストリーミング。

## <a name="grpc-implementation"></a>gRPC の実装

Microsoft のマイクロサービス リファレンス アーキテクチャ [eShop on Containers](https://github.com/dotnet-architecture/eShopOnContainers) は、.NET アプリケーションに gRPC サービスを実装する方法を示しています。 図 4-22 は、バックエンド アーキテクチャを示しています。

![eShop on Containers のバックエンド アーキテクチャ](./media/eshop-with-aggregators.png)

**図 4-22** eShop on Containers のバックエンド アーキテクチャ

前の図では、eShop が、複数の API ゲートウェイを公開することより、[Backend for Frontends パターン](/azure/architecture/patterns/backends-for-frontends) (BFF) を採用していることに注目してください。 BFF パターンについては、この章の前半で説明しました。 Web-Shopping API Gateway とバックエンドのショッピング マイクロサービスの間に位置するアグリゲーター マイクロサービス (灰色) に注目してください。 アグリゲーターによって、クライアントから 1 つの要求が受信され、それがさまざまなマイクロサービスにディスパッチされ、結果が集計され、要求元のクライアントに返送されます。 このような操作には、通常、即時応答を生成するために同期通信が必要です。 eShop では、図 4-23 に示すように、アグリゲーターからのバックエンド呼び出しは、gRPC を使用して実行されます。

![コンテナー上の eShop の gRPC](./media/grpc-implementation.png)

**図 4-23**. コンテナー上の eShop の gRPC

gRPC 通信には、クライアントとサーバーの両方のコンポーネントが必要です。 前の図では、ショッピング アグリゲーターにどのように gRPC クライアントが実装されているかに注目してください。 クライアント側では、バックエンド マイクロサービスへの同期 gRPC 呼び出し (赤色) が行われます。このそれぞれに gRPC サーバーが実装されています。 クライアントとサーバーの両方に、.NET SDK の組み込みの gRPC プラミングが利用されます。 クライアント側の "*スタブ*" には、リモート gRPC 呼び出しを起動するためのプラミングが用意されています。 サーバー側コンポーネントには、カスタム サービス クラスが継承して使用できる gRPC プラミングが用意されています。

RESTful API と gRPC 通信の両方を公開しているマイクロサービスでは、トラフィックを管理するために複数のエンドポイントが必要です。 RESTful 呼び出しのために HTTP トラフィックをリッスンするエンドポイントと、gRPC 呼び出しのための別のエンドポイントを開くことになります。 gRPC エンドポイントは、gRPC 通信に必要な HTTP/2 プロトコル用に構成する必要があります。

Microsoft では非同期通信パターンでマイクロサービスを切り離すように努めていますが、一部の操作には直接呼び出しが必要です。 マイクロサービス間の直接的な同期通信には、gRPC を最優先の選択肢にすべきです。 HTTP/2 とプロトコル バッファーをベースにしたハイ パフォーマンスな通信プロトコルを採用しているため、最適な選択肢です。

## <a name="looking-ahead"></a>今後の予定

クラウドネイティブ システムのために、今後も gRPC の勢いを増していくでしょう。 パフォーマンス上の利点と開発の容易さは魅力的です。 ただし、REST は長い間残る可能性があります。 これは公開されている API と後方互換性の観点から優れています。

>[!div class="step-by-step"]
>[前へ](service-to-service-communication.md)
>[次へ](service-mesh-communication-infrastructure.md)
