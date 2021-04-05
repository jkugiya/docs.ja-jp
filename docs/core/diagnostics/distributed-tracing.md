---
title: 分散トレース - .NET
description: .NET の分散トレースの概要です。
ms.date: 03/15/2021
ms.openlocfilehash: 274a058bf9daf096958813575901e83a3976a3a4
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111115"
---
# <a name="net-distributed-tracing"></a>.NET の分散トレース

分散トレースは、特に複数のコンピューターやプロセスに分散される可能性があるアプリケーション内のエラーとパフォーマンスの問題を、エンジニアがローカライズするのに役立つ診断手法です。 この手法は、アプリケーションを介して要求を追跡し、さまざまなアプリケーション コンポーネントによって実行される作業を相互に関連付けて、アプリケーションが同時要求に対して実行する可能性がある他の作業から分離します。 たとえば、一般的な Web サービスへの要求は、最初にロード バランサーによって受信され、次に Web サーバー プロセスに転送され、その後、データベースに対して複数のクエリが実行されます。 分散トレースを使用すると、エンジニアは、これらのステップのいずれかが失敗したかどうか、各ステップにかかった時間、および実行時に各ステップによって生成されたメッセージをログする可能性を見分けることができます。

## <a name="getting-started-for-net-app-developers"></a>.NET アプリ開発者向けの概要

主要な .NET ライブラリは、分散トレース情報を自動的に生成するためにインストルメント化されますが、後で確認できるように、この情報を収集して保存する必要があります。
通常、アプリ開発者は、このトレース情報を格納するテレメトリ サービスを選択し、対応するライブラリを使用して、選択したサービスに分散トレース テレメトリを送信します。 [OpenTelemetry](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md) は複数のサービスをサポートするベンダー中立ライブラリで、[Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing) は Microsoft が提供する完全な機能を備えたサービスです。また、統合された .NET ソリューションを提供する高品質のサード パーティの APM ベンダーも多数存在します。

- [分散トレースの概念を理解する](distributed-tracing-concepts.md)
- ガイド
  - [Application Insights を使用した分散トレースの収集](distributed-tracing-collection-walkthroughs.md#collect-traces-using-application-insights)
  - [OpenTelemetry を使用した分散トレースの収集](distributed-tracing-collection-walkthroughs.md#collect-traces-using-opentelemetry)
  - [カスタム ロジックを使用した分散トレースの収集](distributed-tracing-collection-walkthroughs.md#collect-traces-using-custom-logic)
  - [カスタム分散トレース インストルメンテーションの追加](distributed-tracing-instrumentation-walkthroughs.md)

サード パーティのテレメトリ収集サービスについては、ベンダーから提供されているセットアップ手順に従います。

## <a name="getting-started-for-net-library-developers"></a>.NET ライブラリ開発者向けの概要

.NET ライブラリでは、テレメトリが最終的にどのように収集されるかを考慮する必要はなく、どのように生成されるかだけを考慮する必要があります。 ライブラリを使用する .NET アプリ開発者が、ライブラリで実行される作業を分散トレースで詳細に確認できると思われる場合は、それをサポートする分散トレース インストルメンテーションを追加する必要があります。

- [分散トレースの概念を理解する](distributed-tracing-concepts.md)
- ガイド
  - [カスタム分散トレース インストルメンテーションの追加](distributed-tracing-instrumentation-walkthroughs.md)
