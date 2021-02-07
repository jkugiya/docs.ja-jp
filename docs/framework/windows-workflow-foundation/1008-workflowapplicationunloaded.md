---
description: '詳細情報: 1008-WorkflowApplicationUnloaded'
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: 5e906c0daae525accc3b8b13c907479d18f2fc8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755565"
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="dd6e8-103">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="dd6e8-103">1008 - WorkflowApplicationUnloaded</span></span>

## <a name="properties"></a><span data-ttu-id="dd6e8-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="dd6e8-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dd6e8-105">id</span><span class="sxs-lookup"><span data-stu-id="dd6e8-105">ID</span></span>|<span data-ttu-id="dd6e8-106">1008</span><span class="sxs-lookup"><span data-stu-id="dd6e8-106">1008</span></span>|  
|<span data-ttu-id="dd6e8-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="dd6e8-107">Keywords</span></span>|<span data-ttu-id="dd6e8-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="dd6e8-108">WFRuntime</span></span>|  
|<span data-ttu-id="dd6e8-109">Level</span><span class="sxs-lookup"><span data-stu-id="dd6e8-109">Level</span></span>|<span data-ttu-id="dd6e8-110">Information</span><span class="sxs-lookup"><span data-stu-id="dd6e8-110">Information</span></span>|  
|<span data-ttu-id="dd6e8-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="dd6e8-111">Channel</span></span>|<span data-ttu-id="dd6e8-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="dd6e8-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dd6e8-113">説明</span><span class="sxs-lookup"><span data-stu-id="dd6e8-113">Description</span></span>  

 <span data-ttu-id="dd6e8-114">ワークフロー アプリケーションがアンロードしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="dd6e8-114">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dd6e8-115">Message</span><span class="sxs-lookup"><span data-stu-id="dd6e8-115">Message</span></span>  

 <span data-ttu-id="dd6e8-116">WorkflowInstance ID: '%1' がアンロードされました。</span><span class="sxs-lookup"><span data-stu-id="dd6e8-116">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dd6e8-117">詳細</span><span class="sxs-lookup"><span data-stu-id="dd6e8-117">Details</span></span>  
  
|<span data-ttu-id="dd6e8-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="dd6e8-118">Data Item Name</span></span>|<span data-ttu-id="dd6e8-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="dd6e8-119">Data Item Type</span></span>|<span data-ttu-id="dd6e8-120">説明</span><span class="sxs-lookup"><span data-stu-id="dd6e8-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dd6e8-121">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="dd6e8-121">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="dd6e8-122">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="dd6e8-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="dd6e8-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="dd6e8-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="dd6e8-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="dd6e8-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
