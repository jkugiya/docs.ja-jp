---
title: NETSDK1059:プロジェクトに古い .NET CLI ツールが含まれています
description: プロジェクトに古い .NET CLI ツールが含まれている問題を解決する方法。
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1059
ms.openlocfilehash: cad546ed1636b71be6b77aa00ef2f3a20095daa5
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653037"
---
# <a name="netsdk1059-project-contains-obsolete-net-cli-tool"></a><span data-ttu-id="47f2d-103">NETSDK1059:プロジェクトに古い .NET CLI ツールが含まれています</span><span class="sxs-lookup"><span data-stu-id="47f2d-103">NETSDK1059: Project contains obsolete .NET CLI tool</span></span>

<span data-ttu-id="47f2d-104">**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="47f2d-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="47f2d-105">.NET SDK によって警告 NETSDK1059 が発行される場合、プロジェクトには古い .NET CLI ツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="47f2d-105">When the .NET SDK issues warning NETSDK1059, your project contains an obsolete .NET CLI tool.</span></span> <span data-ttu-id="47f2d-106">.NET Core 2.1 では、これらのツールは .NET SDK に含まれており、プロジェクトによって明示的に参照される必要はありません。</span><span class="sxs-lookup"><span data-stu-id="47f2d-106">As of .NET Core 2.1, these tools are included in the .NET SDK and do not need to be explicitly referenced by the project.</span></span> <span data-ttu-id="47f2d-107">詳細については、「[プロジェクト ツールが SDK に追加されました](../../compatibility/2.1.md#project-tools-now-included-in-sdk)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47f2d-107">For more information, see [Project tools now included in SDK](../../compatibility/2.1.md#project-tools-now-included-in-sdk).</span></span>
