---
title: 大規模なソリューションを ASP.NET Core に移行する
description: 大規模な ASP.NET MVC アプリを ASP.NET Core に移行する方法を見てみましょう。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: d3ebd71213e074ce80dc83fc3230c4e365275ad3
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401359"
---
# <a name="migrate-large-solutions-to-aspnet-core"></a><span data-ttu-id="31ed8-103">大規模なソリューションを ASP.NET Core に移行する</span><span class="sxs-lookup"><span data-stu-id="31ed8-103">Migrate large solutions to ASP.NET Core</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="31ed8-104">大規模なソリューションを .NET Framework から .NET Core に移行するには、いくつかの計画が必要です。</span><span class="sxs-lookup"><span data-stu-id="31ed8-104">Migrating large solutions from .NET Framework to .NET Core requires some planning.</span></span> <span data-ttu-id="31ed8-105">依存関係は、依存するプロジェクトの前に移行または更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31ed8-105">Dependencies must be migrated or updated before the projects that depend on them.</span></span> <span data-ttu-id="31ed8-106">依存関係を識別し、.NET Core への移行に関するヘルプを提供するツールがあります。</span><span class="sxs-lookup"><span data-stu-id="31ed8-106">There are tools that can identify dependencies and offer help with migrating to .NET Core.</span></span> <span data-ttu-id="31ed8-107">アプリ、そのスコープ、現在の使用パターンに応じて、移行時にさまざまな戦略を採用できます。</span><span class="sxs-lookup"><span data-stu-id="31ed8-107">Depending on the app, its scope, and current usage patterns, different strategies may be employed when migrating.</span></span> <span data-ttu-id="31ed8-108">現在のシステムと並行して、または時間の経過と共に移行しますか。</span><span class="sxs-lookup"><span data-stu-id="31ed8-108">Do you migrate it all at once, or over time, side-by-side with the current system?</span></span> <span data-ttu-id="31ed8-109">新しいシステムを新しいシステムにラップし、その機能を段階的に交換しますか。</span><span class="sxs-lookup"><span data-stu-id="31ed8-109">Do you wrap the current system in the new one, and incrementally replace its functionality?</span></span>

<span data-ttu-id="31ed8-110">この章では、大規模なソリューションの移行計画を作成する方法、移行を支援するツールの使用方法、移行自体について検討する必要があるいくつかの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="31ed8-110">In this chapter, you'll learn how create a migration plan for a large solution, how to use tools to help with the migration, and some strategies to consider for the migration itself.</span></span>

## <a name="references"></a><span data-ttu-id="31ed8-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="31ed8-111">References</span></span>

- [<span data-ttu-id="31ed8-112">大規模な MVC および Web API アプリを .NET Core に移行するには、どのトピックが重要ですか?</span><span class="sxs-lookup"><span data-stu-id="31ed8-112">What topics are important to migrating large MVC and Web API apps to .NET Core?</span></span>](https://twitter.com/ardalis/status/1313669040859217921)
- [<span data-ttu-id="31ed8-113">.NET Framework から .NET Core への移植</span><span class="sxs-lookup"><span data-stu-id="31ed8-113">Porting from .NET Framework to .NET Core</span></span>](../../core/porting/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="31ed8-114">[前へ](testing-differences.md)
>[次へ](identify-migration-sequence.md)</span><span class="sxs-lookup"><span data-stu-id="31ed8-114">[Previous](testing-differences.md)
[Next](identify-migration-sequence.md)</span></span>
