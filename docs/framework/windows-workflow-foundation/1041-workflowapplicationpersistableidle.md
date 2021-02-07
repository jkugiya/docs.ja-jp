---
description: '詳細情報: 1041-WorkflowApplicationPersistableIdle'
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: eb004077a36ed3e78229df92a73972ed5feda665
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667760"
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="0d3f5-103">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="0d3f5-103">1041 - WorkflowApplicationPersistableIdle</span></span>

## <a name="properties"></a><span data-ttu-id="0d3f5-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0d3f5-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d3f5-105">id</span><span class="sxs-lookup"><span data-stu-id="0d3f5-105">ID</span></span>|<span data-ttu-id="0d3f5-106">1041</span><span class="sxs-lookup"><span data-stu-id="0d3f5-106">1041</span></span>|  
|<span data-ttu-id="0d3f5-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="0d3f5-107">Keywords</span></span>|<span data-ttu-id="0d3f5-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0d3f5-108">WFRuntime</span></span>|  
|<span data-ttu-id="0d3f5-109">Level</span><span class="sxs-lookup"><span data-stu-id="0d3f5-109">Level</span></span>|<span data-ttu-id="0d3f5-110">Information</span><span class="sxs-lookup"><span data-stu-id="0d3f5-110">Information</span></span>|  
|<span data-ttu-id="0d3f5-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="0d3f5-111">Channel</span></span>|<span data-ttu-id="0d3f5-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0d3f5-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0d3f5-113">説明</span><span class="sxs-lookup"><span data-stu-id="0d3f5-113">Description</span></span>  

 <span data-ttu-id="0d3f5-114">ワークフロー アプリケーションがアイドル状態のままであることを示します。</span><span class="sxs-lookup"><span data-stu-id="0d3f5-114">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="0d3f5-115">ワークフロー アプリケーションはアイドル状態または永続化されます。</span><span class="sxs-lookup"><span data-stu-id="0d3f5-115">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0d3f5-116">Message</span><span class="sxs-lookup"><span data-stu-id="0d3f5-116">Message</span></span>  

 <span data-ttu-id="0d3f5-117">WorkflowApplication Id: ' %1 ' はアイドル状態で、持続可能です。</span><span class="sxs-lookup"><span data-stu-id="0d3f5-117">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="0d3f5-118">次のアクションが実行されます: %2。</span><span class="sxs-lookup"><span data-stu-id="0d3f5-118">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0d3f5-119">詳細</span><span class="sxs-lookup"><span data-stu-id="0d3f5-119">Details</span></span>  
  
|<span data-ttu-id="0d3f5-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="0d3f5-120">Data Item Name</span></span>|<span data-ttu-id="0d3f5-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="0d3f5-121">Data Item Type</span></span>|<span data-ttu-id="0d3f5-122">説明</span><span class="sxs-lookup"><span data-stu-id="0d3f5-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0d3f5-123">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="0d3f5-123">WorkflowApplicationId</span></span>|<span data-ttu-id="0d3f5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="0d3f5-124">xs:string</span></span>|<span data-ttu-id="0d3f5-125">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="0d3f5-125">The workflow application id</span></span>|  
|<span data-ttu-id="0d3f5-126">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="0d3f5-126">ActionTaken</span></span>|<span data-ttu-id="0d3f5-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="0d3f5-127">xs:string</span></span>|<span data-ttu-id="0d3f5-128">ワークフロー アプリケーションで実行されるアクション。</span><span class="sxs-lookup"><span data-stu-id="0d3f5-128">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="0d3f5-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0d3f5-129">AppDomain</span></span>|<span data-ttu-id="0d3f5-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="0d3f5-130">xs:string</span></span>|<span data-ttu-id="0d3f5-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="0d3f5-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
