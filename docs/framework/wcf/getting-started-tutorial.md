---
title: 'チュートリアル: Windows Communication Foundation アプリケーション入門'
description: これらのチュートリアルでは、WCF アプリケーションの作成の概要について説明します。
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 620a83260f01e27a19b19227165695a621c88e5e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238237"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>チュートリアル: Windows Communication Foundation アプリケーション入門

次の一連のチュートリアルでは、Windows Communication Foundation (WCF) のプログラミング エクスペリエンスを紹介します。 これらのチュートリアルを順番に実行すると、WCF アプリケーションの作成に必要なステップの概要を理解することができます。 終了すると、WCF サービスと、そのサービスを呼び出す WCF クライアントを実行できるようになります。

このチュートリアルでは、開発環境として Visual Studio を使用していることを前提とします。 別の開発環境を使用している場合、Visual Studio 固有の指示は無視してください。

ダウンロードして実行できるサンプル WCF アプリケーションについては、「[Windows Communication Foundation のサンプル](samples/index.md)」を参照してください。 サンプルの概要については、「[入門サンプル](samples/getting-started-sample.md)」を参照してください。

サービスとクライアントの作成について詳しくは、「[基本的な WCF プログラミング](basic-wcf-programming.md)」を参照してください。

## <a name="wcf-tutorials"></a>WCF のチュートリアル

最初の 3 つのチュートリアルでは、WCF サービス コントラクトを定義する方法、それを実装する方法、およびそれをホストする方法について説明します。 作成したサービスは、コンソール アプリケーション内で自己ホストされます。 サービスは、Microsoft インターネット インフォメーション サービス (IIS) でホストすることもできます。 詳細については、「[方法: IIS で WCF サービスをホストする](feature-details/how-to-host-a-wcf-service-in-iis.md)」を参照してください。 このチュートリアルではコードを使用してサービスを構成しますが、[構成ファイル内でサービスを構成](configuring-services-using-configuration-files.md)することもできます。

- [チュートリアル: サービス コントラクトを定義する](how-to-define-a-wcf-service-contract.md)

    WCF コントラクトは、ユーザー定義のインターフェイスを使用して作成します。 このコントラクトでは、サービスによって公開される機能を定義します。

- [チュートリアル: サービス コントラクトを実装する](how-to-implement-a-wcf-contract.md)

    定義したコントラクトは、サービス クラスと共に実装する必要があります。

- [チュートリアル: 基本的なサービスをホストおよび実行する](how-to-host-and-run-a-basic-wcf-service.md)

    サービスのエンドポイントを構成し、コンソール アプリケーション内でサービスをホストします。 サービスをアクティブにするには、それを構成し、ランタイム環境内でホストする必要があります。 このランタイム環境によってサービスが作成され、そのコンテキストと有効期間が制御されます。

次の 2 つのチュートリアルでは、サービスによって公開される操作を呼び出すためにクライアント アプリケーションを作成、構成、および使用する方法について説明します。 サービスは、クライアント アプリケーションがサービスと通信するために必要な情報を定義したメタデータを公開します。 Visual Studio により、このメタデータにアクセスするプロセスが自動化され、それを使って、サービスのクライアント アプリケーションが構築されます。 Visual Studio を使用しない場合は、[ServiceModel メタデータ ユーティリティ ツール (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) を代わりに使用できます。

- [チュートリアル: クライアントを作成する](how-to-create-a-wcf-client.md)

    WCF サービスから WCF クライアント プロキシを作成するためのメタデータを取得します。 メタデータを取得するには、Visual Studio を使用してサービス参照を追加するか、ServiceModel メタデータ ユーティリティ ツールを使用します。 サービスにアクセスするためにクライアントによって使用されるエンドポイントを指定します。

- [チュートリアル: クライアントを使用する](how-to-use-a-wcf-client.md)

    WCF クライアント プロキシを使用して、サービス操作を呼び出します。

## <a name="reference"></a>関連項目

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>関連項目

- [概念の概要](conceptual-overview.md)
- [ドキュメントのガイド](guide-to-the-documentation.md)
- [Windows Communication Foundation とは](whats-wcf.md)
- [WCF 機能の詳細](feature-details/index.md)
- [基本的なプログラミング ライフサイクル](basic-programming-lifecycle.md)
- [クライアントを構築する](building-clients.md)
- [基本的な WCF プログラミング](basic-wcf-programming.md)
- [方法: 双方向コントラクトを作成する](feature-details/how-to-create-a-duplex-contract.md)
- [方法: 双方向コントラクトを使用してサービスにアクセスする](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [方法: Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [方法: 構成ファイルを使用してサービスのメタデータを公開する](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [サービスとクライアントを構成するためのバインディングの使用](using-bindings-to-configure-services-and-clients.md)
- [入門サンプル](samples/getting-started-sample.md)
- [Windows Communication Foundation サンプル](samples/index.md)
- [自己ホスト](samples/self-host.md)
