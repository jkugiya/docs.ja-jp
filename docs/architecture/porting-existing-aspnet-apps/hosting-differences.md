---
title: ASP.NET MVC と ASP.NET Core でのホスティングの相違点
description: ASP.NET MVC アプリと ASP.NET Core アプリでのホスト方法の相違点に関する概要を示します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 9881a40403f8109fa63e25167b753ed4ce8ade17
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122899"
---
# <a name="hosting-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="332a7-103">ASP.NET MVC と ASP.NET Core でのホスティングの相違点</span><span class="sxs-lookup"><span data-stu-id="332a7-103">Hosting differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="332a7-104">ASP.NET MVC アプリは IIS でホストされるため、動作が IIS の構成に依存している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="332a7-104">ASP.NET MVC apps are hosted in IIS, and may rely on IIS configuration for their behavior.</span></span> <span data-ttu-id="332a7-105">これには多くの場合、[IIS モジュール](/iis/get-started/introduction-to-iis/iis-modules-overview)が含まれます。</span><span class="sxs-lookup"><span data-stu-id="332a7-105">This often includes [IIS modules](/iis/get-started/introduction-to-iis/iis-modules-overview).</span></span> <span data-ttu-id="332a7-106">ASP.NET MVC から ASP.NET Core にアプリを移植する準備のための確認の一環として、チームはサーバー上にインストールされている IIS モジュールの一覧の中から、使用中のモジュール (存在する場合) を特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="332a7-106">As part of reviewing an app to prepare to port it from ASP.NET MVC to ASP.NET Core, teams should identify which modules, if any, they're using from the list of IIS Modules installed on their server.</span></span>

<span data-ttu-id="332a7-107">[ASP.NET Core アプリは多数の異なるサーバー上で実行できます](/aspnet/core/fundamentals/servers/)。</span><span class="sxs-lookup"><span data-stu-id="332a7-107">[ASP.NET Core apps can run on a number of different servers](/aspnet/core/fundamentals/servers/).</span></span> <span data-ttu-id="332a7-108">既定の選択肢としては、既定のクロス プラットフォーム サーバーである Kestrel が適しています。</span><span class="sxs-lookup"><span data-stu-id="332a7-108">The default cross platform server, Kestrel, is a good default choice.</span></span> <span data-ttu-id="332a7-109">Kestrel で実行されているアプリは、別のプロセスで実行されている IIS によってホストできます。</span><span class="sxs-lookup"><span data-stu-id="332a7-109">Apps running in Kestrel can be hosted by IIS, running in a separate process.</span></span> <span data-ttu-id="332a7-110">Windows では、アプリを IIS 上のプロセス内で、または HTTP.sys を使用して実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="332a7-110">On Windows, apps can also run in process on IIS or using HTTP.sys.</span></span> <span data-ttu-id="332a7-111">最適なパフォーマンスを得るには、通常は Kestrel をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="332a7-111">Kestrel is generally recommended for best performance.</span></span> <span data-ttu-id="332a7-112">HTTP.sys は、アプリがインターネットに公開されていて、必要な機能が HTTP.sys でサポートされているものの、Kestrel ではサポートされていないシナリオで使用できます。</span><span class="sxs-lookup"><span data-stu-id="332a7-112">HTTP.sys can be used in scenarios where the app is exposed to the Internet and required capabilities are supported by HTTP.sys but not Kestrel.</span></span>

<span data-ttu-id="332a7-113">Kestrel には、IIS モジュールに相当するものはありません (ただし、IIS でホストされているアプリで IIS モジュールを利用することはできます)。</span><span class="sxs-lookup"><span data-stu-id="332a7-113">Kestrel does not have an equivalent to IIS modules (though apps hosted in IIS can still take advantage of IIS modules).</span></span> <span data-ttu-id="332a7-114">同等の動作を実現するために、通常は、ASP.NET Core アプリ自体に構成された[ミドルウェア](/aspnet/core/fundamentals/middleware/)が使用されます。</span><span class="sxs-lookup"><span data-stu-id="332a7-114">To achieve equivalent behavior, [middleware](/aspnet/core/fundamentals/middleware/) configured in the ASP.NET Core app itself is typically used.</span></span>

## <a name="references"></a><span data-ttu-id="332a7-115">References</span><span class="sxs-lookup"><span data-stu-id="332a7-115">References</span></span>

- [<span data-ttu-id="332a7-116">IIS モジュール</span><span class="sxs-lookup"><span data-stu-id="332a7-116">IIS Modules</span></span>](/iis/get-started/introduction-to-iis/iis-modules-overview)
- [<span data-ttu-id="332a7-117">ASP.NET Core のミドルウェア</span><span class="sxs-lookup"><span data-stu-id="332a7-117">ASP.NET Core Middleware</span></span>](/aspnet/core/fundamentals/middleware/)
- [<span data-ttu-id="332a7-118">ASP.NET Core サーバー</span><span class="sxs-lookup"><span data-stu-id="332a7-118">ASP.NET Core Servers</span></span>](/aspnet/core/fundamentals/servers/)

>[!div class="step-by-step"]
><span data-ttu-id="332a7-119">[前へ](app-startup-differences.md)
>[次へ](serving-static-files.md)</span><span class="sxs-lookup"><span data-stu-id="332a7-119">[Previous](app-startup-differences.md)
[Next](serving-static-files.md)</span></span>
