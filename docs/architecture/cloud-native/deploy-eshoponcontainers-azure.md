---
title: eShopOnContainers を Azure にデプロイする
description: Azure Kubernetes Service、Helm、Dev Spaces を使用した eShopOnContainers アプリケーションのデプロイ。
ms.date: 01/19/2021
ms.openlocfilehash: da68fa1510841b6cef9117b6d84e7ed30c565698
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604568"
---
# <a name="deploying-eshoponcontainers-to-azure"></a>eShopOnContainers を Azure にデプロイする

eShopOnContainers アプリケーションは、さまざまな Azure プラットフォームにデプロイできます。 Azure Kubernetes Services (AKS) にアプリケーションをデプロイする方法をお勧めします。 Kubernetes デプロイ ツールである Helm は、デプロイの複雑さを軽減するために使用できます。 開発者は必要に応じて Kubernetes 用の Azure Dev Spaces を実装し、開発プロセスを効率化できます。

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

AKS で eShop をホストするには、最初に AKS クラスターを作成します。 Azure portal を使用すると、作成に必要な手順を実行できます。 また、Azure CLI からクラスターを作成して、ロールベースのアクセス制御 (RBAC) とアプリケーション ルーティングを有効にすることもできます。 eShopOnContainers のドキュメントでは、独自の AKS クラスターを作成する手順について詳しく説明しています。 作成が完了したら、Kubernetes ダッシュボードからクラスターにアクセスして管理できます。

これで、Helm を使用して eShop アプリケーションをクラスターにデプロイできるようになりました。

## <a name="deploying-to-azure-kubernetes-service-using-helm"></a>Helm を使用した Azure Kubernetes Service へのデプロイ

Helm は、Kubernetes と直接連携するアプリケーション パッケージ マネージャー ツールです。 Kubernetes アプリケーションの定義、インストール、アップグレードに役立ちます。 シンプルなアプリはカスタム CLI スクリプトやシンプルなデプロイ ファイルを使用して AKS にデプロイできますが、複雑なアプリには多数の Kubernetes オブジェクトを含めることができます。また、Helm によるメリットも得られます。

Helm を使用するアプリケーションには、Helm チャートと呼ばれるテキスト ベースの構成ファイルが含まれています。このファイルでは、Helm パッケージ内のアプリケーションと構成が宣言によって記述されます。 チャートでは、標準の YAML 形式のファイルを使用して、関連する Kubernetes リソースのセットを記述します。 これらは、記述されているアプリケーション コードと共にバージョン管理されます。 Helm チャートは、記述されているインストールの要件に応じて、シンプルなものから複雑なものまで多岐にわたります。

Helm はコマンド ライン クライアント ツールで構成されます。このツールは、Helm チャートを使用して、Tiller という名前のサーバー コンポーネントに対するコマンドを起動します。 Tiller は Kubernetes API と通信して、コンテナー化されたワークロードを適切にプロビジョニングします。 Helm は、Cloud Native Computing Foundation で管理されています。

次の yaml ファイルは、Helm テンプレートを示しています。

```yaml
apiVersion: v1
kind: Service
metadata:
  name: {{ .Values.app.svc.marketing }}
  labels:
    app: {{ template "marketing-api.name" . }}
    chart: {{ template "marketing-api.chart" . }}
    release: {{ .Release.Name }}
    heritage: {{ .Release.Service }}
spec:
  type: {{ .Values.service.type }}
  ports:
    - port: {{ .Values.service.port }}
      targetPort: http
      protocol: TCP
      name: http
  selector:
    app: {{ template "marketing-api.name" . }}
    release: {{ .Release.Name }}
```

このテンプレートで、キーと値のペアの動的なセットがどのように記述されているかに注目してください。 テンプレートが呼び出されると、中かっこで囲まれた値が、他の yaml ベースの構成ファイルから取り込まれます。

eShopOnContainers の Helm チャートは、/k8s/helm フォルダーにあります。 図 2-6 は、アプリケーションのさまざまなコンポーネントを、デプロイの定義と管理のために Helm で使用されるフォルダー構造に編成する方法を示しています。

![eShopOnContainers の helm フォルダー](./media/eshoponcontainers-helm-folder.png)
**図 2-6** eShopOnContainers の helm フォルダー。

個々のコンポーネントは、`helm install` コマンドを使用してインストールされます。 eShop には、それぞれの Helm チャートを使用してコンポーネントをループまたはインストールする "すべてをデプロイ" スクリプトが含まれています。 結果として、反復可能なプロセスが生成されます。バージョン管理はソース管理でアプリケーションと共に行われます。これにより、チームのすべてのメンバーが 1 行のスクリプト コマンドを使用して AKS クラスターへのデプロイを行えるようになります。

> Helm のバージョン 3 では Tiller サーバー コンポーネントが正式に不要になったことに注意してください。 この機能拡張の詳細については、[ここ](https://medium.com/better-programming/why-is-tiller-missing-in-helm-3-2347c446714)を参照してください。

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

クラウドネイティブ アプリケーションの規模と複雑さが急速に拡大し、実行のために大量のコンピューティング リソースが必要になる可能性があります。 このようなシナリオでは、アプリケーション全体を開発用コンピューター (特にノート PC) でホストすることはできません。 Azure Dev Spaces は、AKS を使用してこの問題に対処するように設計されています。 開発者は、サービスのローカル バージョンで作業を行いながら、AKS 開発クラスターでアプリケーションの残りの部分をホストできます。

開発者は、コンテナー化されたアプリケーション全体が格納されている AKS クラスターで実行中の (開発) インスタンスを共有します。 ただし、サービスのローカル開発には、自分のコンピューターに設定されている個人用のスペースを使用します。 準備ができたら、依存関係をレプリケートすることなく、AKS クラスターでエンドツーエンドのテストを行います。 Azure Dev Spaces により、ローカル コンピューターのコードと AKS 内のサービスがマージされます。 チーム メンバーは、実際の AKS 環境で変更内容がどのように動作するかを確認できます。 開発者は、Visual Studio 2017 または Visual Studio Code を使用して、Kubernetes 内で直接コードの迅速な反復処理とデバッグを実行できます。

図 2-7 では、Susie という開発者が自身の開発スペースに Bikes マイクロサービスの更新バージョンをデプロイしたことがわかります。 次に彼女は、自分のスペースの名前 (susie.s.dev.myapp.eus.azds.io) で始まるカスタム URL を使用して変更内容をテストできます。

![Bikes マイクロサービスを示す eShopOnContainers アーキテクチャ](./media/azure-devspaces-one.png)
**図 2-7** 開発者 Susie が独自のバージョンの Bikes マイクロサービスをデプロイしてテストする。

同時に、開発者 John は Reservations マイクロサービスをカスタマイズして、変更内容をテストする必要があります。 図 2-8 に示すように、彼は Susie の変更内容と競合することなく、自分の開発スペースに変更内容をデプロイします。 次に John は、自分のスペースの名前 (john.s.dev.myapp.eus.azds.io) を先頭に付加した独自の URL を使用して変更内容をテストします。

![John の Reservations マイクロサービスのバージョンを示す eShopOnContainers アーキテクチャ](./media/azure-devspaces-two.png)
**図 2-8** 開発者 John が独自のバージョンの Reservations マイクロサービスをデプロイし、他の開発者と競合することなくテストする。

Azure Dev Spaces を使用すると、チームは AKS を直接操作し、変更内容の修正、デプロイ、テストを独立して行うことができます。 この方法では、開発者が独自の AKS 環境を効果的に使用できるため、個別の専用ホスト環境の必要性が軽減されます。 開発者は CLI を使用して Azure Dev Spaces を操作したり、Visual Studio から直接 Azure Dev Spaces に対してアプリケーションを起動したりできます。 Azure Dev Spaces のしくみと構成方法の詳細については、[ここ](/azure/dev-spaces/how-dev-spaces-works)を参照してください。

## <a name="azure-functions-and-logic-apps-serverless"></a>Azure Functions と Logic Apps (サーバーレス)

eShopOnContainers サンプルには、オンライン マーケティング キャンペーンの追跡のサポートが含まれています。 特定のキャンペーン ID のマーケティング キャンペーンの詳細を追跡するには、Azure 関数を使用します。 完全なマイクロサービスを作成する代わりに、Azure 関数を 1 つ使用すればシンプルかつ十分です。 Azure Functions には、Kubernetes で実行するように構成されている場合などに適した、シンプルなビルドおよびデプロイ モデルが用意されています。 関数のデプロイは、Azure Resource Manager (ARM) テンプレートと Azure CLI を使用してスクリプト化されます。 このキャンペーン サービスは顧客向けではなく、1 つの操作を呼び出します。この操作は Azure Functions に最適な候補になります。 この関数には、データベース接続文字列データやイメージ ベースの URI 設定などの最小限の構成が必要です。 Azure Functions は Azure portal で構成します。

>[!div class="step-by-step"]
>[前へ](map-eshoponcontainers-azure-services.md)
>[次へ](centralized-configuration.md)
