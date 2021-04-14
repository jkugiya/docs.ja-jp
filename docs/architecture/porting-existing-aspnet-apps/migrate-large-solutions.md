---
title: 大規模なソリューションを ASP.NET Core に移行する
description: 大規模な ASP.NET MVC アプリを ASP.NET Core に移行する方法を見てみましょう。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: d3ebd71213e074ce80dc83fc3230c4e365275ad3
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401359"
---
# <a name="migrate-large-solutions-to-aspnet-core"></a><span data-ttu-id="e3f07-103">大規模なソリューションを ASP.NET Core に移行する</span><span class="sxs-lookup"><span data-stu-id="e3f07-103">Migrate large solutions to ASP.NET Core</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="e3f07-104">大規模なソリューションを .NET Framework から .NET Core に移行するには、いくつかの計画が必要です。</span><span class="sxs-lookup"><span data-stu-id="e3f07-104">Migrating large solutions from .NET Framework to .NET Core requires some planning.</span></span> <span data-ttu-id="e3f07-105">依存関係は、それに依存するプロジェクトよりも前に移行または更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3f07-105">Dependencies must be migrated or updated before the projects that depend on them.</span></span> <span data-ttu-id="e3f07-106">依存関係を特定し、.NET Core への移行を支援するツールがあります。</span><span class="sxs-lookup"><span data-stu-id="e3f07-106">There are tools that can identify dependencies and offer help with migrating to .NET Core.</span></span> <span data-ttu-id="e3f07-107">移行時には、アプリ、そのスコープ、および現在の使用パターンに応じてさまざまな戦略を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e3f07-107">Depending on the app, its scope, and current usage patterns, different strategies may be employed when migrating.</span></span> <span data-ttu-id="e3f07-108">すべてを一度に移行しますか、それとも、現在のシステムとサイドバイサイドで時間をかけて移行しますか?</span><span class="sxs-lookup"><span data-stu-id="e3f07-108">Do you migrate it all at once, or over time, side-by-side with the current system?</span></span> <span data-ttu-id="e3f07-109">現在のシステムを新しいシステム内にラップし、その機能を段階的に置き換えますか?</span><span class="sxs-lookup"><span data-stu-id="e3f07-109">Do you wrap the current system in the new one, and incrementally replace its functionality?</span></span>

<span data-ttu-id="e3f07-110">この章では、大規模なソリューションの移行計画を作成する方法、移行を支援するツールの使用方法、移行自体に関して検討すべきいくつかの戦略について説明します。</span><span class="sxs-lookup"><span data-stu-id="e3f07-110">In this chapter, you'll learn how create a migration plan for a large solution, how to use tools to help with the migration, and some strategies to consider for the migration itself.</span></span>

## <a name="references"></a><span data-ttu-id="e3f07-111">リファレンス</span><span class="sxs-lookup"><span data-stu-id="e3f07-111">References</span></span>

- [<span data-ttu-id="e3f07-112">大規模な MVC アプリおよび Web API アプリを .NET Core に移行するために重要なトピックは何ですか?</span><span class="sxs-lookup"><span data-stu-id="e3f07-112">What topics are important to migrating large MVC and Web API apps to .NET Core?</span></span>](https://twitter.com/ardalis/status/1313669040859217921)
- [<span data-ttu-id="e3f07-113">.NET Framework から .NET Core への移植</span><span class="sxs-lookup"><span data-stu-id="e3f07-113">Porting from .NET Framework to .NET Core</span></span>](../../core/porting/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="e3f07-114">[前へ](testing-differences.md)
>[次へ](identify-migration-sequence.md)</span><span class="sxs-lookup"><span data-stu-id="e3f07-114">[Previous](testing-differences.md)
[Next](identify-migration-sequence.md)</span></span>
