---
description: 詳細については、「アクティビティ検証の構成」を参照してください。
title: アクティビティ検証の構成
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: 9e40842a18dd2afd9a5ec0104d66e8971d691b5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792753"
---
# <a name="configuring-activity-validation"></a><span data-ttu-id="de44c-103">アクティビティ検証の構成</span><span class="sxs-lookup"><span data-stu-id="de44c-103">Configuring Activity Validation</span></span>

<span data-ttu-id="de44c-104">アクティビティの検証を使用すると、アクティビティの作成者とユーザーは、アクティビティを実行する前に、アクティビティの構成エラーを特定および報告できます。</span><span class="sxs-lookup"><span data-stu-id="de44c-104">Activity validation enables activity authors and users to identify and report errors in an activity’s configuration prior to its execution.</span></span> <span data-ttu-id="de44c-105">Windows Workflow Foundation (WF) には、次の3種類のアクティビティの検証が用意されています。</span><span class="sxs-lookup"><span data-stu-id="de44c-105">Windows Workflow Foundation (WF) provides the following three types of activity validation:</span></span>  
  
- <span data-ttu-id="de44c-106">`RequiredArgument` 属性および `OverloadGroup` 属性。</span><span class="sxs-lookup"><span data-stu-id="de44c-106">`RequiredArgument` and `OverloadGroup` attributes.</span></span>  
  
- <span data-ttu-id="de44c-107">命令型コードに基づく検証。</span><span class="sxs-lookup"><span data-stu-id="de44c-107">Imperative code-based validation.</span></span>  
  
- <span data-ttu-id="de44c-108">宣言の制約。</span><span class="sxs-lookup"><span data-stu-id="de44c-108">Declarative constraints.</span></span>  
  
 <span data-ttu-id="de44c-109">`RequiredArgument` 属性と `OverloadGroup` 属性は、アクティビティにおける特定の引数が必須であることを示します。</span><span class="sxs-lookup"><span data-stu-id="de44c-109">`RequiredArgument` and `OverloadGroup` attributes indicate that certain arguments on an activity are required.</span></span> <span data-ttu-id="de44c-110">命令型コードに基づく検証には、アクティビティが自身に関する検証を提供できる単純な方法が用意されています。また、宣言の制約を使用すると、アクティビティとそれを含むワークフローとの関係に関して検証できます。</span><span class="sxs-lookup"><span data-stu-id="de44c-110">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and declarative constraints enable validation about the activity and its relationship with the containing workflow.</span></span> <span data-ttu-id="de44c-111">検証の要件に従ってアクティビティが正しく構成されていない場合、検証のエラーと警告が返されます。</span><span class="sxs-lookup"><span data-stu-id="de44c-111">If an activity is not configured properly according to the validation requirements, validation errors and warnings are returned.</span></span> <span data-ttu-id="de44c-112">包含するワークフローをワークフロー デザイナーを使用して作成する場合、デザイナーには任意の検証のエラーと警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="de44c-112">If the containing workflow is created using the workflow designer, any validation errors and warnings are displayed in the designer.</span></span> <span data-ttu-id="de44c-113">ワークフローをワークフロー デザイナーを使用せずに作成する場合、ワークフローを呼び出すときに任意の検証エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="de44c-113">If the workflow is created outside of the workflow designer any validation errors are returned when the workflow is invoked.</span></span> <span data-ttu-id="de44c-114">ワークフローの作成方法にかかわらず、検証エラーを含むワークフローは実行できません。</span><span class="sxs-lookup"><span data-stu-id="de44c-114">Regardless of how the workflow was created, a workflow with validation errors is never allowed to execute.</span></span> <span data-ttu-id="de44c-115">ここでは、このようなアクティビティの検証に関する概要と、アクティビティの検証を呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de44c-115">This section provides an overview of these types of activity validation and how activity validation is invoked.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="de44c-116">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="de44c-116">In This Section</span></span>  

 [<span data-ttu-id="de44c-117">必須の引数とオーバーロード グループ</span><span class="sxs-lookup"><span data-stu-id="de44c-117">Required Arguments and Overload Groups</span></span>](required-arguments-and-overload-groups.md)  
 <span data-ttu-id="de44c-118">検証を実現するために、`RequiredArgument` 属性および `OverloadGroup` 属性を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de44c-118">Describes how to use the `RequiredArgument` and `OverloadGroup` attributes to provide validation.</span></span>  
  
 [<span data-ttu-id="de44c-119">命令型コードに基づく検証</span><span class="sxs-lookup"><span data-stu-id="de44c-119">Imperative Code-Based Validation</span></span>](imperative-code-based-validation.md)  
 <span data-ttu-id="de44c-120"><xref:System.Activities.CodeActivity> および <xref:System.Activities.NativeActivity> に基づくアクティビティにコードに基づく検証を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de44c-120">Describes how to use code-based validation for <xref:System.Activities.CodeActivity> and <xref:System.Activities.NativeActivity> based activities.</span></span>  
  
 [<span data-ttu-id="de44c-121">宣言の制約</span><span class="sxs-lookup"><span data-stu-id="de44c-121">Declarative Constraints</span></span>](declarative-constraints.md)  
 <span data-ttu-id="de44c-122">複雑なアクティビティの検証を実現するために宣言の制約を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de44c-122">Describes how to use declarative constraints to provide complex activity validation.</span></span>  
  
 [<span data-ttu-id="de44c-123">アクティビティ検証の呼び出し</span><span class="sxs-lookup"><span data-stu-id="de44c-123">Invoking Activity Validation</span></span>](invoking-activity-validation.md)  
 <span data-ttu-id="de44c-124">アクティビティの検証が自動的に呼び出される場合と、明示的に検証を呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de44c-124">Discusses when activity validation is invoked automatically and how to explicitly invoke validation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="de44c-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="de44c-125">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="de44c-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="de44c-126">Related Sections</span></span>
