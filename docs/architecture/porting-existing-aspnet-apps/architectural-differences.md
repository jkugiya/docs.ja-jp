---
title: ASP.NET MVC と ASP.NET Core のアーキテクチャの相違点
description: ASP.NET と ASP.NET Core のアーキテクチャの違いを確認します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 96477f2393482380eee9891e9b2dbbb6445e15bd
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401418"
---
# <a name="architectural-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="d8a04-103">ASP.NET MVC と ASP.NET Core のアーキテクチャの相違点</span><span class="sxs-lookup"><span data-stu-id="d8a04-103">Architectural differences between ASP.NET MVC and ASP.NET Core</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="d8a04-104">.NET Framework と ASP.NET Core の ASP.NET MVC には、さまざまなアーキテクチャ上の違いがあります。</span><span class="sxs-lookup"><span data-stu-id="d8a04-104">There are many architectural differences between ASP.NET MVC on .NET Framework and ASP.NET Core.</span></span> <span data-ttu-id="d8a04-105">チームは、ASP.NET MVC アプリを ASP.NET Core に移植する際の作業を評価する際に、これらの違いについて幅広く理解しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="d8a04-105">It's important to have a broad understanding of these differences as teams evaluate the work involved in porting their ASP.NET MVC apps to ASP.NET Core.</span></span> <span data-ttu-id="d8a04-106">この章では、ASP.NET MVC と ASP.NET Core が大きく異なる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d8a04-106">This chapter looks at each of the ways in which ASP.NET Core differs substantially from ASP.NET MVC.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="d8a04-107">重大な変更</span><span class="sxs-lookup"><span data-stu-id="d8a04-107">Breaking changes</span></span>

<span data-ttu-id="d8a04-108">.NET Core は、.NET Framework のクロスプラットフォームの書き換えです。</span><span class="sxs-lookup"><span data-stu-id="d8a04-108">.NET Core is a cross-platform rewrite of .NET Framework.</span></span> <span data-ttu-id="d8a04-109">[2 つのフレームワーク間](../../core/compatibility/fx-core.md)には多くの重大な変更があります。</span><span class="sxs-lookup"><span data-stu-id="d8a04-109">There are many [breaking changes between the two frameworks](../../core/compatibility/fx-core.md).</span></span> <span data-ttu-id="d8a04-110">以下のセクションでは、ASP.NET MVC と ASP.NET Core アプリを設計および開発する方法の具体的な違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d8a04-110">The following sections identify specific differences between how ASP.NET MVC and ASP.NET Core apps are designed and developed.</span></span> <span data-ttu-id="d8a04-111">また、ドキュメントを調べて、使用しているフレームワークライブラリを変更する必要があるかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d8a04-111">Take care to also examine the documentation to determine which framework libraries you're using that may need to change.</span></span> <span data-ttu-id="d8a04-112">多くの場合、.NET Framework と .NET Core の間に残されているギャップを埋めるために、代替の NuGet パッケージが存在します。</span><span class="sxs-lookup"><span data-stu-id="d8a04-112">In many cases, a replacement NuGet package exists to fill in any gaps left between .NET Framework and .NET Core.</span></span> <span data-ttu-id="d8a04-113">まれなケースとして、サードパーティのソリューションを見つけたり、非互換性に対処するための新しいカスタムコードを実装したりする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="d8a04-113">In rare cases, you may need to find a third-party solution or implement new custom code to address incompatibilities.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d8a04-114">[前へ](additional-migration-resources.md)
>[次へ](app-startup-differences.md)</span><span class="sxs-lookup"><span data-stu-id="d8a04-114">[Previous](additional-migration-resources.md)
[Next](app-startup-differences.md)</span></span>
