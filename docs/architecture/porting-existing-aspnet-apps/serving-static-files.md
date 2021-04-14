---
title: ASP.NET MVC と ASP.NET Core での静的ファイルの提供
description: IIS 上の ASP.NET MVC と比較して、ASP.NET Core で静的ファイルを提供するためのサポートを構成するには何が必要でしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 02f84a6985835502c24db8cc68db24c8de086b18
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401350"
---
# <a name="serve-static-files-in-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="b1d50-103">ASP.NET MVC と ASP.NET Core での静的ファイルの提供</span><span class="sxs-lookup"><span data-stu-id="b1d50-103">Serve static files in ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="b1d50-104">ほとんどの Web アプリには、サーバー側のロジックと、クライアントにそのまま送信する必要がある静的ファイルの組み合わせが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b1d50-104">Most web apps involve a combination of server-side logic and static files that must be sent to the client as-is.</span></span> <span data-ttu-id="b1d50-105">ASP.NET MVC から ASP.NET Core への移行では、静的ファイルの提供をどのように処理すればよいでしょうか?</span><span class="sxs-lookup"><span data-stu-id="b1d50-105">How should your migration from ASP.NET MVC to ASP.NET Core handle serving static files?</span></span>

## <a name="host-static-files-in-aspnet-mvc"></a><span data-ttu-id="b1d50-106">ASP.NET MVC での静的ファイルのホスト</span><span class="sxs-lookup"><span data-stu-id="b1d50-106">Host static files in ASP.NET MVC</span></span>

<span data-ttu-id="b1d50-107">通常、IIS によってホストされる ASP.NET MVC アプリは、静的ファイルをアプリから直接ホストします。</span><span class="sxs-lookup"><span data-stu-id="b1d50-107">ASP.NET MVC apps, hosted by IIS, typically host static files directly from the app.</span></span> <span data-ttu-id="b1d50-108">ASP.NET MVC では、静的ファイルを、サーバー上で非公開にする必要があるファイルとサイドバイサイドで配置できます。</span><span class="sxs-lookup"><span data-stu-id="b1d50-108">ASP.NET MVC supports placing static files side by side with files that should be kept private on the server.</span></span> <span data-ttu-id="b1d50-109">IIS および ASP.NET では、ASP.NET アプリがホストされているフォルダーから特定のファイルまたはファイル拡張子が提供されないように明示的に制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1d50-109">IIS and ASP.NET require explicitly restricting certain files or file extensions from being served from the folder in which an ASP.NET app is hosted.</span></span>

<span data-ttu-id="b1d50-110">多くの静的ファイルに対しては、コンテンツ配信ネットワーク (CDN) を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b1d50-110">For many static files, using a content delivery network (CDN) is a good practice.</span></span> <span data-ttu-id="b1d50-111">[静的コンテンツ ホスティング](/azure/architecture/patterns/static-content-hosting)を使用すると、アプリ サーバーからの負荷と帯域幅を抑えつつ、パフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="b1d50-111">[Static content hosting](/azure/architecture/patterns/static-content-hosting) allows better performance while reducing load and bandwidth from app servers.</span></span>

## <a name="host-static-files-in-aspnet-core"></a><span data-ttu-id="b1d50-112">ASP.NET Core での静的ファイルのホスト</span><span class="sxs-lookup"><span data-stu-id="b1d50-112">Host static files in ASP.NET Core</span></span>

<span data-ttu-id="b1d50-113">意外かもしれませんが、ASP.NET Core には静的ファイルのサポートが組み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="b1d50-113">It may be surprising, but ASP.NET Core doesn't have built-in support for static files.</span></span> <span data-ttu-id="b1d50-114">ASP.NET の一部として常に存在し、IIS によって実現されていたこの機能は、ASP.NET Core やその Kestrel Web サーバーには組み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="b1d50-114">This feature that has always existed as just a part of ASP.NET, enabled by IIS, isn't intrinsic to ASP.NET Core or its Kestrel web server.</span></span> <span data-ttu-id="b1d50-115">ASP.NET Core アプリから静的ファイルを提供するには、[静的ファイル ミドルウェア](/aspnet/core/fundamentals/static-files)を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1d50-115">To serve static files from an ASP.NET Core app, you must configure [static files middleware](/aspnet/core/fundamentals/static-files).</span></span>

<span data-ttu-id="b1d50-116">静的ファイル ミドルウェアを構成されると、ASP.NET Core アプリは特定のフォルダー (通常は */wwwroot*) 内にあるすべてのファイルを提供します。</span><span class="sxs-lookup"><span data-stu-id="b1d50-116">With static files middleware configured, an ASP.NET Core app will serve all files located in a certain folder (typically */wwwroot*).</span></span> <span data-ttu-id="b1d50-117">アプリまたはプロジェクト フォルダーに含まれるそれ以外のファイルがサーバーによって誤って公開される危険性はありません。</span><span class="sxs-lookup"><span data-stu-id="b1d50-117">No other files in the app or project folder are at risk of being accidentally exposed by the server.</span></span> <span data-ttu-id="b1d50-118">IIS のように、ファイル名または拡張機能に基づいて特別な制限を構成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b1d50-118">No special restrictions based on file names or extensions need to be configured, as is the case with IIS.</span></span> <span data-ttu-id="b1d50-119">代わりに、開発者はファイルを *wwwroot* フォルダー内に配置することで、そのファイルを公開することを明示的に選択します。</span><span class="sxs-lookup"><span data-stu-id="b1d50-119">Instead, developers explicitly choose to expose files publicly when they place them in the *wwwroot* folder.</span></span> <span data-ttu-id="b1d50-120">既定では、このフォルダー外にあるファイルは共有されません。</span><span class="sxs-lookup"><span data-stu-id="b1d50-120">By default, files outside of this folder aren't shared.</span></span>

<span data-ttu-id="b1d50-121">静的ファイルのサポートではミドルウェアが使用されるため、他の任意のミドルウェアを同じ要求パイプラインの一部として適用できます。</span><span class="sxs-lookup"><span data-stu-id="b1d50-121">Because support for static files uses middleware, any other middleware can be applied as part of the same request pipeline.</span></span> <span data-ttu-id="b1d50-122">ミドルウェアの例としては、認証、キャッシュ、圧縮などがあります。</span><span class="sxs-lookup"><span data-stu-id="b1d50-122">Examples of middleware include authentication, caching, and compression.</span></span>

<span data-ttu-id="b1d50-123">もちろん、CDN は、ASP.NET MVC アプリで使用されているのとまったく同じ理由で、ASP.NET Core アプリでも良い選択であることに変わりありません。</span><span class="sxs-lookup"><span data-stu-id="b1d50-123">Of course, CDNs remain a good choice for ASP.NET Core apps for all the same reasons they're used in ASP.NET MVC apps.</span></span> <span data-ttu-id="b1d50-124">.NET Core への移行の準備の一環として、CDN を使用することでアプリが得られるベネフィットがある場合は、.NET Core に移行する前に静的ファイルを CDN に移動しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b1d50-124">As part of preparing to migrate to .NET Core, if there are benefits your app could realize from using a CDN, it would be good to move static files to a CDN before migrating to .NET Core.</span></span> <span data-ttu-id="b1d50-125">それにより、静的アセットに関する移行作業のスコープ全体を縮小できます。</span><span class="sxs-lookup"><span data-stu-id="b1d50-125">Doing so reduces the migration effort's overall scope for static assets.</span></span>

## <a name="references"></a><span data-ttu-id="b1d50-126">リファレンス</span><span class="sxs-lookup"><span data-stu-id="b1d50-126">References</span></span>

- [<span data-ttu-id="b1d50-127">静的コンテンツ ホスティング</span><span class="sxs-lookup"><span data-stu-id="b1d50-127">Static content hosting</span></span>](/azure/architecture/patterns/static-content-hosting)
- [<span data-ttu-id="b1d50-128">ASP.NET Core の静的ファイル</span><span class="sxs-lookup"><span data-stu-id="b1d50-128">Static files in ASP.NET Core</span></span>](/aspnet/core/fundamentals/static-files)

>[!div class="step-by-step"]
><span data-ttu-id="b1d50-129">[前へ](hosting-differences.md)
>[次へ](dependency-injection-differences.md)</span><span class="sxs-lookup"><span data-stu-id="b1d50-129">[Previous](hosting-differences.md)
[Next](dependency-injection-differences.md)</span></span>
