---
title: ASP.NET MVC と ASP.NET Core のホストの違い
description: ASP.NET MVC アプリがホストされる方法と ASP.NET Core アプリの違いの概要について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 402dd5782cb215545ff2ef13f97ec269b8a2540b
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401382"
---
# <a name="hosting-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="f0d25-103">ASP.NET MVC と ASP.NET Core のホストの違い</span><span class="sxs-lookup"><span data-stu-id="f0d25-103">Hosting differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="f0d25-104">ASP.NET MVC アプリは IIS でホストされ、その動作には IIS 構成に依存する場合があります。</span><span class="sxs-lookup"><span data-stu-id="f0d25-104">ASP.NET MVC apps are hosted in IIS, and may rely on IIS configuration for their behavior.</span></span> <span data-ttu-id="f0d25-105">これには、多くの場合、 [IIS モジュール](/iis/get-started/introduction-to-iis/iis-modules-overview)が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f0d25-105">This often includes [IIS modules](/iis/get-started/introduction-to-iis/iis-modules-overview).</span></span> <span data-ttu-id="f0d25-106">ASP.NET MVC から ASP.NET Core への移植を準備するアプリのレビューの一環として、チームは、サーバーにインストールされている IIS モジュールの一覧から、使用しているモジュール (存在する場合) を特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0d25-106">As part of reviewing an app to prepare to port it from ASP.NET MVC to ASP.NET Core, teams should identify which modules, if any, they're using from the list of IIS Modules installed on their server.</span></span>

<span data-ttu-id="f0d25-107">[ASP.NET Core のアプリは、さまざまなサーバーで実行でき](/aspnet/core/fundamentals/servers/)ます。</span><span class="sxs-lookup"><span data-stu-id="f0d25-107">[ASP.NET Core apps can run on a number of different servers](/aspnet/core/fundamentals/servers/).</span></span> <span data-ttu-id="f0d25-108">既定のクロスプラットフォームサーバーである Kestrel が、既定の選択肢として適しています。</span><span class="sxs-lookup"><span data-stu-id="f0d25-108">The default cross platform server, Kestrel, is a good default choice.</span></span> <span data-ttu-id="f0d25-109">Kestrel で実行されているアプリは、別のプロセスで実行される IIS によってホストできます。</span><span class="sxs-lookup"><span data-stu-id="f0d25-109">Apps running in Kestrel can be hosted by IIS, running in a separate process.</span></span> <span data-ttu-id="f0d25-110">Windows では、アプリは IIS または HTTP.sys を使用してプロセス内で実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0d25-110">On Windows, apps can also run in process on IIS or using HTTP.sys.</span></span> <span data-ttu-id="f0d25-111">最適なパフォーマンスを得るには、通常は Kestrel をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f0d25-111">Kestrel is generally recommended for best performance.</span></span> <span data-ttu-id="f0d25-112">HTTP.sys は、アプリがインターネットに公開されていて、必要な機能が HTTP.sys でサポートされているものの、Kestrel ではサポートされていないシナリオで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0d25-112">HTTP.sys can be used in scenarios where the app is exposed to the Internet and required capabilities are supported by HTTP.sys but not Kestrel.</span></span>

<span data-ttu-id="f0d25-113">Kestrel には、IIS モジュールに相当するものがありません (ただし、IIS でホストされているアプリでも IIS モジュールを利用できます)。</span><span class="sxs-lookup"><span data-stu-id="f0d25-113">Kestrel does not have an equivalent to IIS modules (though apps hosted in IIS can still take advantage of IIS modules).</span></span> <span data-ttu-id="f0d25-114">同等の動作を実現するには、通常、ASP.NET Core アプリ自体で構成されたミドルウェアを使用します。</span><span class="sxs-lookup"><span data-stu-id="f0d25-114">To achieve equivalent behavior, middleware configured in the ASP.NET Core app itself is typically used.</span></span>

## <a name="references"></a><span data-ttu-id="f0d25-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0d25-115">References</span></span>

- [<span data-ttu-id="f0d25-116">IIS モジュール</span><span class="sxs-lookup"><span data-stu-id="f0d25-116">IIS Modules</span></span>](/iis/get-started/introduction-to-iis/iis-modules-overview)
- [<span data-ttu-id="f0d25-117">ASP.NET Core サーバー</span><span class="sxs-lookup"><span data-stu-id="f0d25-117">ASP.NET Core Servers</span></span>](/aspnet/core/fundamentals/servers/)

>[!div class="step-by-step"]
><span data-ttu-id="f0d25-118">[前へ](app-startup-differences.md)
>[次へ](serving-static-files.md)</span><span class="sxs-lookup"><span data-stu-id="f0d25-118">[Previous](app-startup-differences.md)
[Next](serving-static-files.md)</span></span>
