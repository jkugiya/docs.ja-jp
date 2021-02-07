---
description: '詳細情報: 1007-WorkflowApplicationPersisted 化'
title: 1007 - WorkflowApplicationPersisted
ms.date: 03/30/2017
ms.assetid: f4ea4452-28e3-4e66-93c6-eb12ee29bcb1
ms.openlocfilehash: 6598f4490d20f84abfc95223f9d5a3f4231b4754
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755578"
---
# <a name="1007---workflowapplicationpersisted"></a><span data-ttu-id="9cd85-103">1007 - WorkflowApplicationPersisted</span><span class="sxs-lookup"><span data-stu-id="9cd85-103">1007 - WorkflowApplicationPersisted</span></span>

## <a name="properties"></a><span data-ttu-id="9cd85-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9cd85-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9cd85-105">id</span><span class="sxs-lookup"><span data-stu-id="9cd85-105">ID</span></span>|<span data-ttu-id="9cd85-106">1007</span><span class="sxs-lookup"><span data-stu-id="9cd85-106">1007</span></span>|  
|<span data-ttu-id="9cd85-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="9cd85-107">Keywords</span></span>|<span data-ttu-id="9cd85-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9cd85-108">WFRuntime</span></span>|  
|<span data-ttu-id="9cd85-109">Level</span><span class="sxs-lookup"><span data-stu-id="9cd85-109">Level</span></span>|<span data-ttu-id="9cd85-110">Information</span><span class="sxs-lookup"><span data-stu-id="9cd85-110">Information</span></span>|  
|<span data-ttu-id="9cd85-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="9cd85-111">Channel</span></span>|<span data-ttu-id="9cd85-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9cd85-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9cd85-113">説明</span><span class="sxs-lookup"><span data-stu-id="9cd85-113">Description</span></span>  

 <span data-ttu-id="9cd85-114">ワークフロー アプリケーションが永続化されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="9cd85-114">Indicates a workflow application has persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9cd85-115">Message</span><span class="sxs-lookup"><span data-stu-id="9cd85-115">Message</span></span>  

 <span data-ttu-id="9cd85-116">WorkflowApplication ID: %1 が永続化されました。</span><span class="sxs-lookup"><span data-stu-id="9cd85-116">WorkflowApplication Id: '%1' was Persisted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9cd85-117">詳細</span><span class="sxs-lookup"><span data-stu-id="9cd85-117">Details</span></span>  
  
|<span data-ttu-id="9cd85-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="9cd85-118">Data Item Name</span></span>|<span data-ttu-id="9cd85-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="9cd85-119">Data Item Type</span></span>|<span data-ttu-id="9cd85-120">説明</span><span class="sxs-lookup"><span data-stu-id="9cd85-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9cd85-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="9cd85-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="9cd85-122">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="9cd85-122">The workflow application id</span></span>|  
|<span data-ttu-id="9cd85-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9cd85-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9cd85-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="9cd85-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
