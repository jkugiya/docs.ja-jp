---
title: ASP.NET Core 2.1 に移行する
description: .NET Framework ランタイムを対象とする最新の .NET Core バージョンとして、.NET Core 2.1 への移行は、一部のアプリ移行計画の中間手順として意味がありますか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 0c478ae194c6d9118bfbca73f8933d7623246e2c
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401360"
---
# <a name="migrate-to-aspnet-core-21"></a>ASP.NET Core 2.1 に移行する

ASP.NET Core 2.1 は、.NET Core と .NET Framework の両方のランタイムをサポートするために現在サポートされている .NET Core リリースのみであるため、興味深いリリースです。 そのため、アプリのすべての部分を .NET Core に一度にアップグレードする場合と比較すると、一部のアプリのアップグレードパスが簡単になります。 LTS リリースでは、.NET Core 2.1 のサポートは8月2021まで継続されます。 基になる .NET Framework がサポートされている限り、.NET Framework で実行されている ASP.NET Core 2.1 のサポートは続行されます。

## <a name="should-apps-run-on-net-framework-with-aspnet-core-21"></a>アプリを ASP.NET Core 2.1 で .NET Framework で実行する必要があるか

ASP.NET Core 2.2 以前では、.NET Core と .NET Framework のランタイムの両方がサポートされていました。 .NET Core に完全に移植する前に、アプリの一部またはすべてをステップ実行のストーンとして ASP.NET Core 2.1 に移行することは理にかなっていますか。 アプリ、またはアプリのサブセットによって、ASP.NET Core を使用するようにフロントエンドの ASP.NET ロジックが移植される一方で、ビジネスロジックとインフラストラクチャの消費に .NET Framework ライブラリが引き続き使用される可能性があります。 この方法は、ビジネスロジックを持たない比較的シン UI レイヤーがある場合や、クラスライブラリの機能セットがはるかに大きい場合に意味があります。

フロントエンド web レイヤーのみを ASP.NET Core 2.1 に移植する主な利点は、既存の .NET クラスライブラリを最初の移行時にそのまま残すことができることです。 これらは、他の .NET アプリによって引き続き使用されている場合もあれば、.NET Core への計画的な完全移行の最初のイテレーションの範囲内に存在しない場合もあります。 大規模なアプリの初期移行の範囲を減らすことは、必要な終了状態に対するステップ実行として機能する段階的な目標を実現するのに役立ちます。これは、多くの場合、.NET Core への完全なポートです。

この方法を使用する既存のアプリがある場合は、そのプロセスの準備に役立ついくつかの作業を行うことができます。そのためには、ビジネスロジック、データアクセス、およびその他の UI 以外のロジックを ASP.NET プロジェクトから別のクラスライブラリに移動する必要があります。 また、システムのテストカバレッジが自動化されている場合にも役立ちます。これにより、移行前後の動作が一貫していることを確認できます。

アプリケーション全体を一度に移行することができず、新しい ASP.NET Core アプリを既存の ASP.NET アプリとサイドバイサイドでデプロイできるようにする必要がある場合は、これを実現するために使用できる展開戦略があります。 これらについては、 [「5: 展開シナリオ](deployment-scenarios.md)」で説明しています。

ASP.NET Core 2.1 は、.NET Framework での実行と .NET Framework ライブラリの使用をサポートする .NET Core の最後の LTS リリースであることに注意してください。 このリリースはまもなくサポートされなくなりますが、.NET Framework (.NET Core 2.1 のサポートが終了した後でも) .NET Framework の ASP.NET Core 2.1 がサポートされるようになります。 詳細については、 [.NET Framework の ASP.NET Core 2.1](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)を参照してください。

## <a name="references"></a>関連項目

[ASP.NET から ASP.NET Core 2.1 への移行](/aspnet/core/migration/proper-to-2x/?preserve-view=true&view=aspnetcore-2.1)

>[!div class="step-by-step"]
>[前へ](migration-considerations.md)
>[次へ](choose-net-core-version.md)
