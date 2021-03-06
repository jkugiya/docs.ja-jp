---
title: 適切な .NET Core バージョンを選択する
description: 対象とする .NET Core のバージョンはどのように判断すればよいですか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 401eead986ee8b67ed15be609d0b5d228773312d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "102401270"
---
# <a name="choose-the-right-net-core-version"></a>適切な .NET Core バージョンを選択する

対象とする .NET Core のバージョンを選択する場合、ほとんどの組織にとって最も大きな考慮事項はサポートライフサイクルです。 長期的なサポート (LTS) のリリースは、現在の (非 LTS) リリースよりも頻繁に出荷されることはありませんが、サポート期間は長くなっています。 現時点では、LTS リリースは、他の年ごとに出荷するようにスケジュールされています。 お客様は、ターゲットとするリリースを選択できます。また、.NET Core の異なるリリースを同じコンピューターにサイドバイサイドでインストールできます。 LTS リリースでは、ライフサイクル全体で、重要で互換性のある修正プログラムのみが提供されます。 現在のリリースでは、これらの同じ修正プログラムが提供され、互換性のあるイノベーションと機能によっても更新されます。 LTS リリースは、最初のリリースから3年間サポートされています。 最新リリースは、次の最新リリースまたは LTS リリース後 3 か月間サポートされます。

現在、大規模な .NET Framework アプリを .NET Core に移行しようとしているほとんどのお客様は、以前のバージョンの .NET Core にまだ移行していないことから、安定したコピー先を探していることが考えられます。 この場合、移行の対象となる最適な .NET Core バージョンは、現在の LTS バージョンである .NET Core 3.1 です。 .NET Core 3.1 のサポートは、2022年12月に終了します。 次に予定されている LTS リリースは、2021年11月に出荷予定の .NET 6.0 になります。

.NET Core 3.1 から .net 5.0 (次のバージョン) に更新すると、.NET Framework から .NET Core に移植する場合よりも手間がかかります。 このため、ほとんどのお客様の場合、最初に .NET Core 3.1 にアップグレードすることをお勧めします。 次に、次の更新プログラムを最新の最新リリースにするか (.NET 5.0)、さらにアップグレードする前に次の LTS リリース (.NET 6.0) を待機するかを決定します。

この本は、.NET Framework アプリが .NET Core 3.1 にアップグレードされることを前提としています。

## <a name="references"></a>関連項目

[.NET Core と .NET 5 のサポートポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)

>[!div class="step-by-step"]
>[前へ](migrate-aspnet-core-2-1.md)
>[次へ](incremental-migration-strategies.md)
