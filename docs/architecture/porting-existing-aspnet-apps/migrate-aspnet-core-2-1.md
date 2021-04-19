---
title: ASP.NET Core 2.1 に移行する
description: .NET Framework ランタイムをターゲットにできる最後の .NET Core のバージョンである .NET Core 2.1 に移行することは、一部のアプリ移行計画での中間段階として理にかなっているでしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: e4db85405edc7e7f51ab6f8b422451cf7acc065e
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122847"
---
# <a name="migrate-to-aspnet-core-21"></a>ASP.NET Core 2.1 に移行する

ASP.NET Core 2.1 は、興味深いリリースです。 .NET Core と .NET Framework の両方のランタイムをサポートする、現在サポートされている唯一の ASP.NET Core リリースだからです。 そのような理由で、アプリによっては、これを使用することでアプリのすべての部分を一度に .NET Core にアップグレードするよりもアップグレード パスが簡単になる可能性があります。 LTS リリースとしては、.NET Core 2.1 のサポートは 2021 年 8 月まで継続されます。 .NET Framework 上で実行される ASP.NET Core 2.1 のサポートは、基になる .NET Framework がサポートされている間は継続されます。

## <a name="should-apps-run-on-net-framework-with-aspnet-core-21"></a>.NET Framework と ASP.NET Core 2.1 上でアプリを実行する必要があるか

ASP.NET Core 2.2 以前では、.NET Core と .NET Framework の両方のランタイムがサポートされていました。 .NET Core に完全に移植する前に、足がかりとしてアプリの一部またはすべてを ASP.NET Core 2.1 に移行することは理にかなっているでしょうか? アプリまたはアプリのサブセットで、ビジネス ロジックとインフラストラクチャの使用に関しては引き続き .NET Framework ライブラリを使用しつつ、フロントエンドの ASP.NET ロジックを ASP.NET Core を使用するように移植することができます。 このアプローチは、あまり多くのビジネス ロジックが含まれない比較的薄い UI レイヤーがあり、はるかに大規模な機能のセットがクラス ライブラリ内にある場合に理にかなっています。

フロントエンドの Web レイヤーのみを ASP.NET Core 2.1 に移植する主な利点は、初期移行中に既存の .NET クラス ライブラリをそのまま維持できることです。 これらは他の .NET アプリによって引き続き使用されていたり、または単に、計画されている .NET Core への完全移行の初期イテレーションのスコープ内に含める必要がない場合もあります。 大規模なアプリの初期移行のスコープを小さくすることは、希望する最終状態 (多くの場合、.NET Core への完全な移植) に向けた足がかりとなる段階的な目標を設定するのに役立ちます。

この戦略を使用できる既存のアプリがある場合、そのプロセスに備えるために今できることは、できる限り多くのビジネス ロジック、データ アクセス、その他の UI 以外のロジックを、ASP.NET プロジェクトから別のクラス ライブラリに移動しておくことです。 これは、移行の前と後とで動作の一貫性が維持されていることを確認できるように、システムのテスト カバレッジを自動化している場合にも役立ちます。

アプリの規模が非常に大きいために Web アプリ全体を一度に移行できず、新しい ASP.NET Core アプリを既存の ASP.NET アプリとサイドバイサイドで展開できるようにする必要がある場合は、それを実現できる展開戦略があります。 それらについては、「[第 5 章: 展開シナリオ](deployment-scenarios.md)」で説明しています。

ASP.NET Core 2.1 は .NET Framework 上での実行と .NET Framework ライブラリの使用がサポートされる .NET Core の最後の LTS リリースであることを念頭に置いてください。 このリリースはまもなくサポートされなくなりますが、.NET Framework 上の ASP.NET Core 2.1 は、その .NET Framework がサポートされている間は (.NET Core 2.1 のサポートが終了した後でも) サポートされます。 詳細については、「[.NET Framework 上の ASP.NET Core 2.1](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」を参照してください。

## <a name="references"></a>References

[ASP.NET から ASP.NET Core 2.1 への移行](/aspnet/core/migration/proper-to-2x/?preserve-view=true&view=aspnetcore-2.1)

>[!div class="step-by-step"]
>[前へ](migration-considerations.md)
>[次へ](choose-net-core-version.md)
