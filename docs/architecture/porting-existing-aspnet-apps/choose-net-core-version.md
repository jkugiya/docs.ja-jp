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
# <a name="choose-the-right-net-core-version"></a><span data-ttu-id="df506-103">適切な .NET Core バージョンを選択する</span><span class="sxs-lookup"><span data-stu-id="df506-103">Choose the right .NET Core version</span></span>

<span data-ttu-id="df506-104">ほとんどの組織にとって、ターゲットにする .NET Core のバージョンを選択する際の最大の考慮事項は、サポート ライフサイクルです。</span><span class="sxs-lookup"><span data-stu-id="df506-104">The largest consideration for most organizations when choosing a version of .NET Core to target is the support lifecycle.</span></span> <span data-ttu-id="df506-105">長期サポート (LTS) リリースは、(LTS 以外の) 最新リリースよりも出荷頻度は低いですが、サポート期間は長くなっています。</span><span class="sxs-lookup"><span data-stu-id="df506-105">Long Term Support (LTS) releases ship less frequently but have a longer support window than Current (non-LTS) releases.</span></span> <span data-ttu-id="df506-106">現在、LTS リリースは隔年で出荷されるようにスケジュールされています。</span><span class="sxs-lookup"><span data-stu-id="df506-106">Currently, LTS releases are scheduled to ship every other year.</span></span> <span data-ttu-id="df506-107">お客様は、どちらのリリースをターゲットにするかを選択できます。また、.NET Core の異なる複数のリリースを同じコンピューター上にサイド バイ サイドでインストールできます。</span><span class="sxs-lookup"><span data-stu-id="df506-107">Customers can choose which releases to target, and can install different releases of .NET Core side by side on the same machine.</span></span> <span data-ttu-id="df506-108">LTS リリースは、そのライフサイクル全体を通じて、重要で互換性のある修正プログラムのみを受信します。</span><span class="sxs-lookup"><span data-stu-id="df506-108">LTS releases will receive only critical and compatible fixes throughout their lifecycle.</span></span> <span data-ttu-id="df506-109">最新リリースは、それらと同じ修正プログラムを受信するほかに、互換性のある革新的技術や機能によっても更新されます。</span><span class="sxs-lookup"><span data-stu-id="df506-109">Current releases will receive these same fixes and will also be updated with compatible innovations and features.</span></span> <span data-ttu-id="df506-110">LTS リリースは、初回リリース後 3 年間サポートされます。</span><span class="sxs-lookup"><span data-stu-id="df506-110">LTS releases are supported for three years after their initial release.</span></span> <span data-ttu-id="df506-111">最新リリースは、次の最新リリースまたは LTS リリース後 3 か月間サポートされます。</span><span class="sxs-lookup"><span data-stu-id="df506-111">Current releases are supported for three months after a subsequent Current or LTS release.</span></span>

<span data-ttu-id="df506-112">現在、大規模な .NET Framework アプリの .NET Core への移行を検討しているお客様のほとんどはおそらく、前のバージョンの .NET Core への移行をまだ行っていないので安定した移行先を求めているでしょう。</span><span class="sxs-lookup"><span data-stu-id="df506-112">Most customers looking to migrate a large .NET Framework app to .NET Core today are probably looking for a stable destination, given that they haven't already made the move to an earlier version of .NET Core.</span></span> <span data-ttu-id="df506-113">その場合、移行のターゲットとして最適な .NET Core のバージョンは、現在の LTS バージョンである .NET Core 3.1 です。</span><span class="sxs-lookup"><span data-stu-id="df506-113">In this case, the best .NET Core version to target for the migration is .NET Core 3.1, which is the current LTS version.</span></span> <span data-ttu-id="df506-114">.NET Core 3.1 のサポートは 2022 年 12 月に終了します。</span><span class="sxs-lookup"><span data-stu-id="df506-114">Support for .NET Core 3.1 ends in December 2022.</span></span> <span data-ttu-id="df506-115">次に予定されている LTS リリースは、2021 年 11 月に出荷予定の .NET 6.0 です。</span><span class="sxs-lookup"><span data-stu-id="df506-115">The next planned LTS release will be .NET 6.0, slated to ship in November 2021.</span></span>

<span data-ttu-id="df506-116">.NET Core 3.1 から .NET 5.0 (次のバージョン) に更新するために必要な作業量は、.NET Framework から .NET Core に移植する場合よりもかなり少なく済みます。</span><span class="sxs-lookup"><span data-stu-id="df506-116">Updating from .NET Core 3.1 to .NET 5.0 (the next version) requires much less effort than porting from .NET Framework to .NET Core.</span></span> <span data-ttu-id="df506-117">そのため、ほとんどのお客様に対して推奨されるのは、まず .NET Core 3.1 にアップグレードすることです。</span><span class="sxs-lookup"><span data-stu-id="df506-117">For this reason, the recommendation for most customers is to upgrade to .NET Core 3.1 first.</span></span> <span data-ttu-id="df506-118">その後、次の更新として最新リリース (.NET 5.0) に更新するか、または次の LTS リリース (.NET 6.0) まで待ってからさらにアップグレードするかを決定します。</span><span class="sxs-lookup"><span data-stu-id="df506-118">Then decide whether the next update should be to the latest current release (.NET 5.0) or to wait for the next LTS release (.NET 6.0) before upgrading further.</span></span>

<span data-ttu-id="df506-119">本書では、.NET Framework アプリが .NET Core 3.1 にアップグレードされることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="df506-119">This book assumes .NET Framework apps will be upgraded to .NET Core 3.1.</span></span>

## <a name="references"></a><span data-ttu-id="df506-120">リファレンス</span><span class="sxs-lookup"><span data-stu-id="df506-120">References</span></span>

[<span data-ttu-id="df506-121">.NET Core と .NET 5 のサポート ポリシー</span><span class="sxs-lookup"><span data-stu-id="df506-121">.NET Core and .NET 5 Support Policy</span></span>](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)

>[!div class="step-by-step"]
><span data-ttu-id="df506-122">[前へ](migrate-aspnet-core-2-1.md)
>[次へ](incremental-migration-strategies.md)</span><span class="sxs-lookup"><span data-stu-id="df506-122">[Previous](migrate-aspnet-core-2-1.md)
[Next](incremental-migration-strategies.md)</span></span>
