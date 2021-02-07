---
description: '詳細情報: 1002-WorkflowApplicationTerminated'
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: 8ceef41515231833767fc7e2095ab3850bf80e41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755629"
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="f1ef0-103">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="f1ef0-103">1002 - WorkflowApplicationTerminated</span></span>

## <a name="properties"></a><span data-ttu-id="f1ef0-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f1ef0-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f1ef0-105">id</span><span class="sxs-lookup"><span data-stu-id="f1ef0-105">ID</span></span>|<span data-ttu-id="f1ef0-106">1002</span><span class="sxs-lookup"><span data-stu-id="f1ef0-106">1002</span></span>|  
|<span data-ttu-id="f1ef0-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="f1ef0-107">Keywords</span></span>|<span data-ttu-id="f1ef0-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f1ef0-108">WFRuntime</span></span>|  
|<span data-ttu-id="f1ef0-109">Level</span><span class="sxs-lookup"><span data-stu-id="f1ef0-109">Level</span></span>|<span data-ttu-id="f1ef0-110">Information</span><span class="sxs-lookup"><span data-stu-id="f1ef0-110">Information</span></span>|  
|<span data-ttu-id="f1ef0-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="f1ef0-111">Channel</span></span>|<span data-ttu-id="f1ef0-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f1ef0-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f1ef0-113">説明</span><span class="sxs-lookup"><span data-stu-id="f1ef0-113">Description</span></span>  

 <span data-ttu-id="f1ef0-114">例外が発生し、ワークフロー アプリケーションが Faulted 状態で終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="f1ef0-114">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f1ef0-115">Message</span><span class="sxs-lookup"><span data-stu-id="f1ef0-115">Message</span></span>  

 <span data-ttu-id="f1ef0-116">WorkflowApplication ID: %1 は中止されました。</span><span class="sxs-lookup"><span data-stu-id="f1ef0-116">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="f1ef0-117">例外により Faulted 状態で完了しました。</span><span class="sxs-lookup"><span data-stu-id="f1ef0-117">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f1ef0-118">詳細</span><span class="sxs-lookup"><span data-stu-id="f1ef0-118">Details</span></span>  
  
|<span data-ttu-id="f1ef0-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="f1ef0-119">Data Item Name</span></span>|<span data-ttu-id="f1ef0-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="f1ef0-120">Data Item Type</span></span>|<span data-ttu-id="f1ef0-121">説明</span><span class="sxs-lookup"><span data-stu-id="f1ef0-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f1ef0-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="f1ef0-122">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="f1ef0-123">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="f1ef0-123">The workflow application id</span></span>|  
|<span data-ttu-id="f1ef0-124">例外</span><span class="sxs-lookup"><span data-stu-id="f1ef0-124">Exception</span></span>|`xs:string`|<span data-ttu-id="f1ef0-125">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="f1ef0-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="f1ef0-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f1ef0-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f1ef0-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="f1ef0-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
