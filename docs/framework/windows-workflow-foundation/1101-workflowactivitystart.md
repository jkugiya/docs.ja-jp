---
description: 詳細については、「1101-WorkflowActivityStart」を参照してください。
title: 1101 - WorkflowActivityStart
ms.date: 03/30/2017
ms.assetid: 831cd386-b9b5-47a9-9690-aff6292ff348
ms.openlocfilehash: f84a3de405d05e5f4669244577a4a16c1c53f8d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667591"
---
# <a name="1101---workflowactivitystart"></a><span data-ttu-id="8e553-103">1101 - WorkflowActivityStart</span><span class="sxs-lookup"><span data-stu-id="8e553-103">1101 - WorkflowActivityStart</span></span>

## <a name="properties"></a><span data-ttu-id="8e553-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8e553-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8e553-105">id</span><span class="sxs-lookup"><span data-stu-id="8e553-105">ID</span></span>|<span data-ttu-id="8e553-106">1101</span><span class="sxs-lookup"><span data-stu-id="8e553-106">1101</span></span>|  
|<span data-ttu-id="8e553-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="8e553-107">Keywords</span></span>|<span data-ttu-id="8e553-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8e553-108">WFRuntime</span></span>|  
|<span data-ttu-id="8e553-109">Level</span><span class="sxs-lookup"><span data-stu-id="8e553-109">Level</span></span>|<span data-ttu-id="8e553-110">Information</span><span class="sxs-lookup"><span data-stu-id="8e553-110">Information</span></span>|  
|<span data-ttu-id="8e553-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="8e553-111">Channel</span></span>|<span data-ttu-id="8e553-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8e553-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8e553-113">説明</span><span class="sxs-lookup"><span data-stu-id="8e553-113">Description</span></span>  

 <span data-ttu-id="8e553-114">ワークフロー アクティビティが開始されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="8e553-114">Indicates a workflow activity has started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8e553-115">Message</span><span class="sxs-lookup"><span data-stu-id="8e553-115">Message</span></span>  

 <span data-ttu-id="8e553-116">WorkflowInstance ID: '%1' E2E アクティビティ</span><span class="sxs-lookup"><span data-stu-id="8e553-116">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="8e553-117">詳細</span><span class="sxs-lookup"><span data-stu-id="8e553-117">Details</span></span>  
  
|<span data-ttu-id="8e553-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="8e553-118">Data Item Name</span></span>|<span data-ttu-id="8e553-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="8e553-119">Data Item Type</span></span>|<span data-ttu-id="8e553-120">説明</span><span class="sxs-lookup"><span data-stu-id="8e553-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8e553-121">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="8e553-121">WorkflowInstanceId</span></span>|<span data-ttu-id="8e553-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e553-122">xs:string</span></span>|<span data-ttu-id="8e553-123">ワークフロー インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="8e553-123">The workflow instance id.</span></span>|  
|<span data-ttu-id="8e553-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8e553-124">AppDomain</span></span>|<span data-ttu-id="8e553-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e553-125">xs:string</span></span>|<span data-ttu-id="8e553-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="8e553-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
