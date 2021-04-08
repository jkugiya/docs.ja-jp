---
title: 適切な .NET Core バージョンを選択する
description: ターゲットにする .NET Core のバージョンはどのように決定すればよいでしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 401eead986ee8b67ed15be609d0b5d228773312d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "102401270"
---
# <a name="choose-the-right-net-core-version"></a>適切な .NET Core バージョンを選択する

ほとんどの組織にとって、ターゲットにする .NET Core のバージョンを選択する際の最大の考慮事項は、サポート ライフサイクルです。 長期サポート (LTS) リリースは、(LTS 以外の) 最新リリースよりも出荷頻度は低いですが、サポート期間は長くなっています。 現在、LTS リリースは隔年で出荷されるようにスケジュールされています。 お客様は、どちらのリリースをターゲットにするかを選択できます。また、.NET Core の異なる複数のリリースを同じコンピューター上にサイド バイ サイドでインストールできます。 LTS リリースは、そのライフサイクル全体を通じて、重要で互換性のある修正プログラムのみを受信します。 最新リリースは、それらと同じ修正プログラムを受信するほかに、互換性のある革新的技術や機能によっても更新されます。 LTS リリースは、初回リリース後 3 年間サポートされます。 最新リリースは、次の最新リリースまたは LTS リリース後 3 か月間サポートされます。

現在、大規模な .NET Framework アプリの .NET Core への移行を検討しているお客様のほとんどはおそらく、前のバージョンの .NET Core への移行をまだ行っていないので安定した移行先を求めているでしょう。 その場合、移行のターゲットとして最適な .NET Core のバージョンは、現在の LTS バージョンである .NET Core 3.1 です。 .NET Core 3.1 のサポートは 2022 年 12 月に終了します。 次に予定されている LTS リリースは、2021 年 11 月に出荷予定の .NET 6.0 です。

.NET Core 3.1 から .NET 5.0 (次のバージョン) に更新するために必要な作業量は、.NET Framework から .NET Core に移植する場合よりもかなり少なく済みます。 そのため、ほとんどのお客様に対して推奨されるのは、まず .NET Core 3.1 にアップグレードすることです。 その後、次の更新として最新リリース (.NET 5.0) に更新するか、または次の LTS リリース (.NET 6.0) まで待ってからさらにアップグレードするかを決定します。

本書では、.NET Framework アプリが .NET Core 3.1 にアップグレードされることを前提としています。

## <a name="references"></a>リファレンス

[.NET Core と .NET 5 のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)

>[!div class="step-by-step"]
>[前へ](migrate-aspnet-core-2-1.md)
>[次へ](incremental-migration-strategies.md)
