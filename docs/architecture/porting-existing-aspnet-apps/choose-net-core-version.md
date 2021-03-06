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
# <a name="choose-the-right-net-core-version"></a><span data-ttu-id="b1637-103">適切な .NET Core バージョンを選択する</span><span class="sxs-lookup"><span data-stu-id="b1637-103">Choose the right .NET Core version</span></span>

<span data-ttu-id="b1637-104">対象とする .NET Core のバージョンを選択する場合、ほとんどの組織にとって最も大きな考慮事項はサポートライフサイクルです。</span><span class="sxs-lookup"><span data-stu-id="b1637-104">The largest consideration for most organizations when choosing a version of .NET Core to target is the support lifecycle.</span></span> <span data-ttu-id="b1637-105">長期的なサポート (LTS) のリリースは、現在の (非 LTS) リリースよりも頻繁に出荷されることはありませんが、サポート期間は長くなっています。</span><span class="sxs-lookup"><span data-stu-id="b1637-105">Long Term Support (LTS) releases ship less frequently but have a longer support window than Current (non-LTS) releases.</span></span> <span data-ttu-id="b1637-106">現時点では、LTS リリースは、他の年ごとに出荷するようにスケジュールされています。</span><span class="sxs-lookup"><span data-stu-id="b1637-106">Currently, LTS releases are scheduled to ship every other year.</span></span> <span data-ttu-id="b1637-107">お客様は、ターゲットとするリリースを選択できます。また、.NET Core の異なるリリースを同じコンピューターにサイドバイサイドでインストールできます。</span><span class="sxs-lookup"><span data-stu-id="b1637-107">Customers can choose which releases to target, and can install different releases of .NET Core side by side on the same machine.</span></span> <span data-ttu-id="b1637-108">LTS リリースでは、ライフサイクル全体で、重要で互換性のある修正プログラムのみが提供されます。</span><span class="sxs-lookup"><span data-stu-id="b1637-108">LTS releases will receive only critical and compatible fixes throughout their lifecycle.</span></span> <span data-ttu-id="b1637-109">現在のリリースでは、これらの同じ修正プログラムが提供され、互換性のあるイノベーションと機能によっても更新されます。</span><span class="sxs-lookup"><span data-stu-id="b1637-109">Current releases will receive these same fixes and will also be updated with compatible innovations and features.</span></span> <span data-ttu-id="b1637-110">LTS リリースは、最初のリリースから3年間サポートされています。</span><span class="sxs-lookup"><span data-stu-id="b1637-110">LTS releases are supported for three years after their initial release.</span></span> <span data-ttu-id="b1637-111">最新リリースは、次の最新リリースまたは LTS リリース後 3 か月間サポートされます。</span><span class="sxs-lookup"><span data-stu-id="b1637-111">Current releases are supported for three months after a subsequent Current or LTS release.</span></span>

<span data-ttu-id="b1637-112">現在、大規模な .NET Framework アプリを .NET Core に移行しようとしているほとんどのお客様は、以前のバージョンの .NET Core にまだ移行していないことから、安定したコピー先を探していることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="b1637-112">Most customers looking to migrate a large .NET Framework app to .NET Core today are probably looking for a stable destination, given that they haven't already made the move to an earlier version of .NET Core.</span></span> <span data-ttu-id="b1637-113">この場合、移行の対象となる最適な .NET Core バージョンは、現在の LTS バージョンである .NET Core 3.1 です。</span><span class="sxs-lookup"><span data-stu-id="b1637-113">In this case, the best .NET Core version to target for the migration is .NET Core 3.1, which is the current LTS version.</span></span> <span data-ttu-id="b1637-114">.NET Core 3.1 のサポートは、2022年12月に終了します。</span><span class="sxs-lookup"><span data-stu-id="b1637-114">Support for .NET Core 3.1 ends in December 2022.</span></span> <span data-ttu-id="b1637-115">次に予定されている LTS リリースは、2021年11月に出荷予定の .NET 6.0 になります。</span><span class="sxs-lookup"><span data-stu-id="b1637-115">The next planned LTS release will be .NET 6.0, slated to ship in November 2021.</span></span>

<span data-ttu-id="b1637-116">.NET Core 3.1 から .net 5.0 (次のバージョン) に更新すると、.NET Framework から .NET Core に移植する場合よりも手間がかかります。</span><span class="sxs-lookup"><span data-stu-id="b1637-116">Updating from .NET Core 3.1 to .NET 5.0 (the next version) requires much less effort than porting from .NET Framework to .NET Core.</span></span> <span data-ttu-id="b1637-117">このため、ほとんどのお客様の場合、最初に .NET Core 3.1 にアップグレードすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b1637-117">For this reason, the recommendation for most customers is to upgrade to .NET Core 3.1 first.</span></span> <span data-ttu-id="b1637-118">次に、次の更新プログラムを最新の最新リリースにするか (.NET 5.0)、さらにアップグレードする前に次の LTS リリース (.NET 6.0) を待機するかを決定します。</span><span class="sxs-lookup"><span data-stu-id="b1637-118">Then decide whether the next update should be to the latest current release (.NET 5.0) or to wait for the next LTS release (.NET 6.0) before upgrading further.</span></span>

<span data-ttu-id="b1637-119">この本は、.NET Framework アプリが .NET Core 3.1 にアップグレードされることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="b1637-119">This book assumes .NET Framework apps will be upgraded to .NET Core 3.1.</span></span>

## <a name="references"></a><span data-ttu-id="b1637-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1637-120">References</span></span>

[<span data-ttu-id="b1637-121">.NET Core と .NET 5 のサポートポリシー</span><span class="sxs-lookup"><span data-stu-id="b1637-121">.NET Core and .NET 5 Support Policy</span></span>](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)

>[!div class="step-by-step"]
><span data-ttu-id="b1637-122">[前へ](migrate-aspnet-core-2-1.md)
>[次へ](incremental-migration-strategies.md)</span><span class="sxs-lookup"><span data-stu-id="b1637-122">[Previous](migrate-aspnet-core-2-1.md)
[Next](incremental-migration-strategies.md)</span></span>
