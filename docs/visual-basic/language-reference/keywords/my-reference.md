---
description: '詳細情報: My の参照 (Visual Basic)'
title: My の参照
ms.date: 07/20/2015
helpviewer_keywords:
- My feature
- My reference
ms.assetid: 6f803bd7-21ff-4569-b1fe-b00a6678b1e3
ms.openlocfilehash: 8a0fb265f98c28b8cf37994d39fa210d63fd43c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774695"
---
# <a name="my-reference-visual-basic"></a><span data-ttu-id="cea62-103">My の参照 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cea62-103">My Reference (Visual Basic)</span></span>

<span data-ttu-id="cea62-104">`My` 機能により、よく使用されるメソッド、プロパティ、およびイベントに直観的にアクセスできることで、プログラミングがより高速かつ簡単になります。</span><span class="sxs-lookup"><span data-stu-id="cea62-104">The `My` feature makes programming faster and easier by giving you intuitive access to commonly used methods, properties, and events.</span></span> <span data-ttu-id="cea62-105">次の表に、`My` に含まれるオブジェクトと、それぞれで実行できるアクションを示します。</span><span class="sxs-lookup"><span data-stu-id="cea62-105">This table lists the objects contained in `My`, and the actions that can be performed with each.</span></span>  
  
|<span data-ttu-id="cea62-106">**動作**</span><span class="sxs-lookup"><span data-stu-id="cea62-106">**Action**</span></span>|<span data-ttu-id="cea62-107">**オブジェクト**</span><span class="sxs-lookup"><span data-stu-id="cea62-107">**Object**</span></span>|  
|----------------|----------------|  
|<span data-ttu-id="cea62-108">アプリケーション情報とサービスへのアクセス。</span><span class="sxs-lookup"><span data-stu-id="cea62-108">Accessing application information and services.</span></span>|<span data-ttu-id="cea62-109">`My.Application` オブジェクトは、次のクラスで構成されています。</span><span class="sxs-lookup"><span data-stu-id="cea62-109">The `My.Application` object consists of the following classes:</span></span><br /><br /> <span data-ttu-id="cea62-110"><xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> は、すべてのプロジェクトで使用可能なメンバーを提供します。</span><span class="sxs-lookup"><span data-stu-id="cea62-110"><xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> provides members that are available in all projects.</span></span><br /><br /> <span data-ttu-id="cea62-111"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> は、Windows フォーム アプリケーションで使用可能なメンバーを提供します。</span><span class="sxs-lookup"><span data-stu-id="cea62-111"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> provides members available in Windows Forms applications.</span></span><br /><br /> <span data-ttu-id="cea62-112"><xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> は、コンソール アプリケーションで使用可能なメンバーを提供します。</span><span class="sxs-lookup"><span data-stu-id="cea62-112"><xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> provides members available in console applications.</span></span>|  
|<span data-ttu-id="cea62-113">ホスト コンピューターとそのリソース、サービス、およびデータへのアクセス。</span><span class="sxs-lookup"><span data-stu-id="cea62-113">Accessing the host computer and its resources, services, and data.</span></span>|<span data-ttu-id="cea62-114">`My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)</span><span class="sxs-lookup"><span data-stu-id="cea62-114">`My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)</span></span>|  
|<span data-ttu-id="cea62-115">現在のプロジェクトのフォームへのアクセス。</span><span class="sxs-lookup"><span data-stu-id="cea62-115">Accessing the forms in the current project.</span></span>|[<span data-ttu-id="cea62-116">My.Forms オブジェクト</span><span class="sxs-lookup"><span data-stu-id="cea62-116">My.Forms Object</span></span>](../objects/my-forms-object.md)|  
|<span data-ttu-id="cea62-117">アプリケーション ログへのアクセス。</span><span class="sxs-lookup"><span data-stu-id="cea62-117">Accessing the application log.</span></span>|<span data-ttu-id="cea62-118">`My.Application.Log` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>)</span><span class="sxs-lookup"><span data-stu-id="cea62-118">`My.Application.Log` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>)</span></span>|  
|<span data-ttu-id="cea62-119">現在の Web 要求へのアクセス。</span><span class="sxs-lookup"><span data-stu-id="cea62-119">Accessing the current web request.</span></span>|[<span data-ttu-id="cea62-120">My.Request オブジェクト</span><span class="sxs-lookup"><span data-stu-id="cea62-120">My.Request Object</span></span>](../objects/my-request-object.md)|  
|<span data-ttu-id="cea62-121">リソース要素へのアクセス。</span><span class="sxs-lookup"><span data-stu-id="cea62-121">Accessing resource elements.</span></span>|[<span data-ttu-id="cea62-122">My.Resources オブジェクト</span><span class="sxs-lookup"><span data-stu-id="cea62-122">My.Resources Object</span></span>](../objects/my-resources-object.md)|  
|<span data-ttu-id="cea62-123">現在の Web 応答へのアクセス。</span><span class="sxs-lookup"><span data-stu-id="cea62-123">Accessing the current web response.</span></span>|[<span data-ttu-id="cea62-124">My.Response オブジェクト</span><span class="sxs-lookup"><span data-stu-id="cea62-124">My.Response Object</span></span>](../objects/my-response-object.md)|  
|<span data-ttu-id="cea62-125">ユーザー レベルとアプリケーション レベルの設定へのアクセス。</span><span class="sxs-lookup"><span data-stu-id="cea62-125">Accessing user and application level settings.</span></span>|[<span data-ttu-id="cea62-126">My.Settings オブジェクト</span><span class="sxs-lookup"><span data-stu-id="cea62-126">My.Settings Object</span></span>](../objects/my-settings-object.md)|  
|<span data-ttu-id="cea62-127">現在のユーザーのセキュリティ コンテキストへのアクセス。</span><span class="sxs-lookup"><span data-stu-id="cea62-127">Accessing the current user's security context.</span></span>|<span data-ttu-id="cea62-128">`My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>)</span><span class="sxs-lookup"><span data-stu-id="cea62-128">`My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>)</span></span>|  
|<span data-ttu-id="cea62-129">現在のプロジェクトによって参照されている XML Web サービスへのアクセス。</span><span class="sxs-lookup"><span data-stu-id="cea62-129">Accessing XML Web services referenced by the current project.</span></span>|[<span data-ttu-id="cea62-130">My.WebServices オブジェクト</span><span class="sxs-lookup"><span data-stu-id="cea62-130">My.WebServices Object</span></span>](../objects/my-webservices-object.md)|  
  
## <a name="see-also"></a><span data-ttu-id="cea62-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="cea62-131">See also</span></span>

- [<span data-ttu-id="cea62-132">Visual Basic アプリケーション モデルの概要</span><span class="sxs-lookup"><span data-stu-id="cea62-132">Overview of the Visual Basic Application Model</span></span>](../../developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
- [<span data-ttu-id="cea62-133">My による開発</span><span class="sxs-lookup"><span data-stu-id="cea62-133">Development with My</span></span>](../../developing-apps/development-with-my/index.md)
