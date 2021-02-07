---
description: '詳細情報: 1001-WorkflowApplicationCompleted'
title: 1001 - WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: d32028bbe582f4a1e31796ed1f75e41c651e6c59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755643"
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="13469-103">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="13469-103">1001 - WorkflowApplicationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="13469-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="13469-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="13469-105">id</span><span class="sxs-lookup"><span data-stu-id="13469-105">ID</span></span>|<span data-ttu-id="13469-106">1001</span><span class="sxs-lookup"><span data-stu-id="13469-106">1001</span></span>|  
|<span data-ttu-id="13469-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="13469-107">Keywords</span></span>|<span data-ttu-id="13469-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="13469-108">WFRuntime</span></span>|  
|<span data-ttu-id="13469-109">Level</span><span class="sxs-lookup"><span data-stu-id="13469-109">Level</span></span>|<span data-ttu-id="13469-110">Information</span><span class="sxs-lookup"><span data-stu-id="13469-110">Information</span></span>|  
|<span data-ttu-id="13469-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="13469-111">Channel</span></span>|<span data-ttu-id="13469-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="13469-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="13469-113">説明</span><span class="sxs-lookup"><span data-stu-id="13469-113">Description</span></span>  

 <span data-ttu-id="13469-114">ワークフロー アプリケーションが Closed 状態で完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="13469-114">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="13469-115">Message</span><span class="sxs-lookup"><span data-stu-id="13469-115">Message</span></span>  

 <span data-ttu-id="13469-116">WorkflowInstance ID: %1 は Closed 状態で完了しました。</span><span class="sxs-lookup"><span data-stu-id="13469-116">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="13469-117">詳細</span><span class="sxs-lookup"><span data-stu-id="13469-117">Details</span></span>  
  
|<span data-ttu-id="13469-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="13469-118">Data Item Name</span></span>|<span data-ttu-id="13469-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="13469-119">Data Item Type</span></span>|<span data-ttu-id="13469-120">説明</span><span class="sxs-lookup"><span data-stu-id="13469-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="13469-121">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="13469-121">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="13469-122">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="13469-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="13469-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="13469-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="13469-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="13469-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
