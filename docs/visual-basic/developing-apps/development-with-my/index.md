---
description: '詳細情報: My による開発 (Visual Basic)'
title: My による開発
ms.date: 07/20/2015
f1_keywords:
- My.MyWpfExtension.Windows
helpviewer_keywords:
- My object
- My namespace
- My feature
- Visual Basic, programming in
ms.assetid: f1d04509-5e46-4551-9f9f-94334a121fca
ms.openlocfilehash: f19365471dab5fa30b565a9dd93c40a2f5795118
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666564"
---
# <a name="development-with-my-visual-basic"></a><span data-ttu-id="248aa-103">My による開発 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="248aa-103">Development with My (Visual Basic)</span></span>

<span data-ttu-id="248aa-104">Visual Basic には、多彩な機能を提供する一方で生産性や使いやすさを向上させる、迅速なアプリケーション開発用の新しい機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="248aa-104">Visual Basic provides new features for rapid application development that improve productivity and ease of use while delivering power.</span></span> <span data-ttu-id="248aa-105">こうした機能の 1 つである `My` という機能は、情報へのアクセス、およびアプリケーションやそのランタイム環境に関連する既定のオブジェクト インスタンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="248aa-105">One of these features, called `My`, provides access to information and default object instances that are related to the application and its run-time environment.</span></span> <span data-ttu-id="248aa-106">この情報は、IntelliSense によって検出可能な形式で編成され、用途に応じて論理的に区別されます。</span><span class="sxs-lookup"><span data-stu-id="248aa-106">This information is organized in a format that is discoverable through IntelliSense and logically delineated according to use.</span></span>  
  
 <span data-ttu-id="248aa-107">`My` の最上位メンバーは、オブジェクトとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="248aa-107">Top-level members of `My` are exposed as objects.</span></span> <span data-ttu-id="248aa-108">各オブジェクトは、名前空間でも `Shared` メンバーがあるクラスでも同じように動作し、関連するメンバーのセットを公開します。</span><span class="sxs-lookup"><span data-stu-id="248aa-108">Each object behaves similarly to a namespace or a class with `Shared` members, and it exposes a set of related members.</span></span>  
  
 <span data-ttu-id="248aa-109">次の表は、最上位の `My` オブジェクトと各オブジェクトの相互関係を示しています。</span><span class="sxs-lookup"><span data-stu-id="248aa-109">This table shows the top-level `My` objects and their relationship to each other.</span></span>  
  
 ![My のオブジェクト モデルを示す図。](./media/index/my-object-model-relationships.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="248aa-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="248aa-111">In This Section</span></span>  

 [<span data-ttu-id="248aa-112">My.Application、My.Computer、および My.User でのタスクの実行</span><span class="sxs-lookup"><span data-stu-id="248aa-112">Performing Tasks with My.Application, My.Computer, and My.User</span></span>](performing-tasks-with-my-application-my-computer-and-my-user.md)  
 <span data-ttu-id="248aa-113">`My` の中心となる 3 つのオブジェクト (`My.Application`、`My.Computer`、および `My.User`) について説明します。これらのオブジェクトは、情報と機能へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="248aa-113">Describes the three central `My` objects, `My.Application`, `My.Computer`, and `My.User`, which provide access to information and functionality</span></span>  
  
 [<span data-ttu-id="248aa-114">My.Forms と My.WebServices が提供する既定のオブジェクト インスタンス</span><span class="sxs-lookup"><span data-stu-id="248aa-114">Default Object Instances Provided by My.Forms and My.WebServices</span></span>](default-object-instances-provided-by-my-forms-and-my-webservices.md)  
 <span data-ttu-id="248aa-115">`My.Forms` オブジェクトと `My.WebServices` オブジェクトについて説明します。これらのオブジェクトは、アプリケーションで使用されるフォーム、データ ソース、および XML Web サービスへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="248aa-115">Describes the `My.Forms` and `My.WebServices` objects, which provide access to forms, data sources, and XML Web services used by your application.</span></span>  
  
 [<span data-ttu-id="248aa-116">My.Resources と My.Settings による Rapid Application Development</span><span class="sxs-lookup"><span data-stu-id="248aa-116">Rapid Application Development with My.Resources and My.Settings</span></span>](rapid-application-development-with-my-resources-and-my-settings.md)  
 <span data-ttu-id="248aa-117">`My.Resources` オブジェクトと `My.Settings` オブジェクトについて説明します。これらのオブジェクトは、アプリケーションのリソースと設定へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="248aa-117">Describes the `My.Resources` and `My.Settings` objects, which provide access to an application's resources and settings.</span></span>  
  
 [<span data-ttu-id="248aa-118">Visual Basic アプリケーション モデルの概要</span><span class="sxs-lookup"><span data-stu-id="248aa-118">Overview of the Visual Basic Application Model</span></span>](overview-of-the-visual-basic-application-model.md)  
 <span data-ttu-id="248aa-119">Visual Basic アプリケーションのスタートアップまたはシャットダウン モデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="248aa-119">Describes the Visual Basic Application Startup/Shutdown model.</span></span>  
  
 [<span data-ttu-id="248aa-120">プロジェクトの種類に応じた My の機能</span><span class="sxs-lookup"><span data-stu-id="248aa-120">How My Depends on Project Type</span></span>](how-my-depends-on-project-type.md)  
 <span data-ttu-id="248aa-121">異なる種類のプロジェクトで使用できる `My` 機能の詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="248aa-121">Gives details on which `My` features are available in different project types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="248aa-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="248aa-122">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [<span data-ttu-id="248aa-123">My.Forms オブジェクト</span><span class="sxs-lookup"><span data-stu-id="248aa-123">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="248aa-124">My.WebServices オブジェクト</span><span class="sxs-lookup"><span data-stu-id="248aa-124">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="248aa-125">プロジェクトの種類に応じた My の機能</span><span class="sxs-lookup"><span data-stu-id="248aa-125">How My Depends on Project Type</span></span>](how-my-depends-on-project-type.md)
