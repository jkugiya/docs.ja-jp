---
title: ASP.NET MVC および ASP.NET Core で静的ファイルを提供する
description: IIS での ASP.NET MVC と比較して、ASP.NET Core での静的ファイルの提供に関するサポートを構成するための関係
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 02f84a6985835502c24db8cc68db24c8de086b18
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401350"
---
# <a name="serve-static-files-in-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="b206b-103">ASP.NET MVC および ASP.NET Core で静的ファイルを提供する</span><span class="sxs-lookup"><span data-stu-id="b206b-103">Serve static files in ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="b206b-104">ほとんどの web アプリには、サーバー側のロジックと静的ファイルを組み合わせたものが含まれており、そのようにクライアントに送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b206b-104">Most web apps involve a combination of server-side logic and static files that must be sent to the client as-is.</span></span> <span data-ttu-id="b206b-105">ASP.NET MVC から静的ファイルを提供する ASP.NET Core ハンドルに移行するにはどうすればよいですか。</span><span class="sxs-lookup"><span data-stu-id="b206b-105">How should your migration from ASP.NET MVC to ASP.NET Core handle serving static files?</span></span>

## <a name="host-static-files-in-aspnet-mvc"></a><span data-ttu-id="b206b-106">ASP.NET MVC での静的ファイルのホスト</span><span class="sxs-lookup"><span data-stu-id="b206b-106">Host static files in ASP.NET MVC</span></span>

<span data-ttu-id="b206b-107">IIS によってホストされる ASP.NET MVC アプリは、通常、静的ファイルをアプリから直接ホストします。</span><span class="sxs-lookup"><span data-stu-id="b206b-107">ASP.NET MVC apps, hosted by IIS, typically host static files directly from the app.</span></span> <span data-ttu-id="b206b-108">ASP.NET MVC では、静的ファイルを、サーバー上でプライベートに保持する必要があるファイルと同時に配置できます。</span><span class="sxs-lookup"><span data-stu-id="b206b-108">ASP.NET MVC supports placing static files side by side with files that should be kept private on the server.</span></span> <span data-ttu-id="b206b-109">IIS と ASP.NET では、ASP.NET アプリがホストされているフォルダーから、特定のファイルまたはファイル拡張子が明示的に制限されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b206b-109">IIS and ASP.NET require explicitly restricting certain files or file extensions from being served from the folder in which an ASP.NET app is hosted.</span></span>

<span data-ttu-id="b206b-110">多くの静的ファイルでは、コンテンツ配信ネットワーク (CDN) を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b206b-110">For many static files, using a content delivery network (CDN) is a good practice.</span></span> <span data-ttu-id="b206b-111">[静的コンテンツホスティング](/azure/architecture/patterns/static-content-hosting) では、アプリサーバーからの負荷と帯域幅を削減しながら、パフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="b206b-111">[Static content hosting](/azure/architecture/patterns/static-content-hosting) allows better performance while reducing load and bandwidth from app servers.</span></span>

## <a name="host-static-files-in-aspnet-core"></a><span data-ttu-id="b206b-112">ASP.NET Core での静的ファイルのホスト</span><span class="sxs-lookup"><span data-stu-id="b206b-112">Host static files in ASP.NET Core</span></span>

<span data-ttu-id="b206b-113">当然のことですが、ASP.NET Core 静的ファイルのサポートは組み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="b206b-113">It may be surprising, but ASP.NET Core doesn't have built-in support for static files.</span></span> <span data-ttu-id="b206b-114">この機能は、IIS によって有効にされる ASP.NET の一部として常に存在していたものであり、ASP.NET Core またはその Kestrel web サーバーには組み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="b206b-114">This feature that has always existed as just a part of ASP.NET, enabled by IIS, isn't intrinsic to ASP.NET Core or its Kestrel web server.</span></span> <span data-ttu-id="b206b-115">ASP.NET Core アプリから静的ファイルを提供するには、 [静的ファイルミドルウェア](/aspnet/core/fundamentals/static-files)を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b206b-115">To serve static files from an ASP.NET Core app, you must configure [static files middleware](/aspnet/core/fundamentals/static-files).</span></span>

<span data-ttu-id="b206b-116">静的ファイルミドルウェアが構成されている場合、ASP.NET Core アプリは、特定のフォルダー (通常は */wwwroot*) にあるすべてのファイルに対して機能します。</span><span class="sxs-lookup"><span data-stu-id="b206b-116">With static files middleware configured, an ASP.NET Core app will serve all files located in a certain folder (typically */wwwroot*).</span></span> <span data-ttu-id="b206b-117">アプリまたはプロジェクトフォルダー内の他のファイルが、サーバーによって誤って公開される危険性があります。</span><span class="sxs-lookup"><span data-stu-id="b206b-117">No other files in the app or project folder are at risk of being accidentally exposed by the server.</span></span> <span data-ttu-id="b206b-118">IIS の場合と同様に、ファイル名または拡張機能に基づく特別な制限を構成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b206b-118">No special restrictions based on file names or extensions need to be configured, as is the case with IIS.</span></span> <span data-ttu-id="b206b-119">代わりに、開発者は、 *wwwroot* フォルダーにファイルを配置するときに、ファイルを公開するように明示的に選択します。</span><span class="sxs-lookup"><span data-stu-id="b206b-119">Instead, developers explicitly choose to expose files publicly when they place them in the *wwwroot* folder.</span></span> <span data-ttu-id="b206b-120">既定では、このフォルダー以外のファイルは共有されません。</span><span class="sxs-lookup"><span data-stu-id="b206b-120">By default, files outside of this folder aren't shared.</span></span>

<span data-ttu-id="b206b-121">静的ファイルのサポートはミドルウェアを使用するため、その他のミドルウェアは同じ要求パイプラインの一部として適用できます。</span><span class="sxs-lookup"><span data-stu-id="b206b-121">Because support for static files uses middleware, any other middleware can be applied as part of the same request pipeline.</span></span> <span data-ttu-id="b206b-122">ミドルウェアの例としては、認証、キャッシュ、圧縮などがあります。</span><span class="sxs-lookup"><span data-stu-id="b206b-122">Examples of middleware include authentication, caching, and compression.</span></span>

<span data-ttu-id="b206b-123">もちろん、ASP.NET MVC アプリで使用されているのと同じ理由で、CDNs は ASP.NET Core アプリに適しています。</span><span class="sxs-lookup"><span data-stu-id="b206b-123">Of course, CDNs remain a good choice for ASP.NET Core apps for all the same reasons they're used in ASP.NET MVC apps.</span></span> <span data-ttu-id="b206b-124">.NET Core への移行の準備の一環として、CDN を使用してアプリの利点が得られる場合は、.NET Core に移行する前に、静的なファイルを CDN に移動することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b206b-124">As part of preparing to migrate to .NET Core, if there are benefits your app could realize from using a CDN, it would be good to move static files to a CDN before migrating to .NET Core.</span></span> <span data-ttu-id="b206b-125">これにより、静的な資産の移行作業全体の範囲が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="b206b-125">Doing so reduces the migration effort's overall scope for static assets.</span></span>

## <a name="references"></a><span data-ttu-id="b206b-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="b206b-126">References</span></span>

- [<span data-ttu-id="b206b-127">静的コンテンツホスティング</span><span class="sxs-lookup"><span data-stu-id="b206b-127">Static content hosting</span></span>](/azure/architecture/patterns/static-content-hosting)
- [<span data-ttu-id="b206b-128">ASP.NET Core の静的ファイル</span><span class="sxs-lookup"><span data-stu-id="b206b-128">Static files in ASP.NET Core</span></span>](/aspnet/core/fundamentals/static-files)

>[!div class="step-by-step"]
><span data-ttu-id="b206b-129">[前へ](hosting-differences.md)
>[次へ](dependency-injection-differences.md)</span><span class="sxs-lookup"><span data-stu-id="b206b-129">[Previous](hosting-differences.md)
[Next](dependency-injection-differences.md)</span></span>
