---
description: '詳細情報: 1003-WorkflowInstanceCanceled'
title: 1003 - WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: ef7b7c6849e96866204fe53deadce8302d18e0d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703368"
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="3a31e-103">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="3a31e-103">1003 - WorkflowInstanceCanceled</span></span>

## <a name="properties"></a><span data-ttu-id="3a31e-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3a31e-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3a31e-105">id</span><span class="sxs-lookup"><span data-stu-id="3a31e-105">ID</span></span>|<span data-ttu-id="3a31e-106">1003</span><span class="sxs-lookup"><span data-stu-id="3a31e-106">1003</span></span>|  
|<span data-ttu-id="3a31e-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="3a31e-107">Keywords</span></span>|<span data-ttu-id="3a31e-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3a31e-108">WFRuntime</span></span>|  
|<span data-ttu-id="3a31e-109">Level</span><span class="sxs-lookup"><span data-stu-id="3a31e-109">Level</span></span>|<span data-ttu-id="3a31e-110">Information</span><span class="sxs-lookup"><span data-stu-id="3a31e-110">Information</span></span>|  
|<span data-ttu-id="3a31e-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="3a31e-111">Channel</span></span>|<span data-ttu-id="3a31e-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3a31e-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3a31e-113">説明</span><span class="sxs-lookup"><span data-stu-id="3a31e-113">Description</span></span>  

 <span data-ttu-id="3a31e-114">ワークフロー インスタンスが Canceled 状態で完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="3a31e-114">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3a31e-115">Message</span><span class="sxs-lookup"><span data-stu-id="3a31e-115">Message</span></span>  

 <span data-ttu-id="3a31e-116">WorkflowInstance ID: %1 は Canceled 状態で完了しました。</span><span class="sxs-lookup"><span data-stu-id="3a31e-116">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3a31e-117">詳細</span><span class="sxs-lookup"><span data-stu-id="3a31e-117">Details</span></span>  
  
|<span data-ttu-id="3a31e-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="3a31e-118">Data Item Name</span></span>|<span data-ttu-id="3a31e-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="3a31e-119">Data Item Type</span></span>|<span data-ttu-id="3a31e-120">説明</span><span class="sxs-lookup"><span data-stu-id="3a31e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3a31e-121">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="3a31e-121">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="3a31e-122">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="3a31e-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="3a31e-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3a31e-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3a31e-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="3a31e-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
