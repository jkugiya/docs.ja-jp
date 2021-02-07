---
description: '詳細情報: 1006-WorkflowApplicationUnhandledException'
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: bfccd0d12c5dac4caad1e84e95f1cd096a551aa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755591"
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="08bf1-103">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="08bf1-103">1006 - WorkflowApplicationUnhandledException</span></span>

## <a name="properties"></a><span data-ttu-id="08bf1-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="08bf1-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="08bf1-105">id</span><span class="sxs-lookup"><span data-stu-id="08bf1-105">ID</span></span>|<span data-ttu-id="08bf1-106">1006</span><span class="sxs-lookup"><span data-stu-id="08bf1-106">1006</span></span>|  
|<span data-ttu-id="08bf1-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="08bf1-107">Keywords</span></span>|<span data-ttu-id="08bf1-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="08bf1-108">WFRuntime</span></span>|  
|<span data-ttu-id="08bf1-109">Level</span><span class="sxs-lookup"><span data-stu-id="08bf1-109">Level</span></span>|<span data-ttu-id="08bf1-110">エラー</span><span class="sxs-lookup"><span data-stu-id="08bf1-110">Error</span></span>|  
|<span data-ttu-id="08bf1-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="08bf1-111">Channel</span></span>|<span data-ttu-id="08bf1-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="08bf1-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="08bf1-113">説明</span><span class="sxs-lookup"><span data-stu-id="08bf1-113">Description</span></span>  

 <span data-ttu-id="08bf1-114">ワークフロー アプリケーションでハンドルされない例外が検出されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="08bf1-114">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="08bf1-115">Message</span><span class="sxs-lookup"><span data-stu-id="08bf1-115">Message</span></span>  

 <span data-ttu-id="08bf1-116">WorkflowInstance Id: ' %1 ' でハンドルされない例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="08bf1-116">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="08bf1-117">Activity ' %2 '、DisplayName: ' %3 ' から例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="08bf1-117">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="08bf1-118">次のアクションが実行されます: %4。</span><span class="sxs-lookup"><span data-stu-id="08bf1-118">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="08bf1-119">詳細</span><span class="sxs-lookup"><span data-stu-id="08bf1-119">Details</span></span>  
  
|<span data-ttu-id="08bf1-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="08bf1-120">Data Item Name</span></span>|<span data-ttu-id="08bf1-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="08bf1-121">Data Item Type</span></span>|<span data-ttu-id="08bf1-122">説明</span><span class="sxs-lookup"><span data-stu-id="08bf1-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="08bf1-123">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="08bf1-123">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="08bf1-124">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="08bf1-124">The instance id for the workflow</span></span>|  
|<span data-ttu-id="08bf1-125">例外</span><span class="sxs-lookup"><span data-stu-id="08bf1-125">Exception</span></span>|`xs:string`|<span data-ttu-id="08bf1-126">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="08bf1-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="08bf1-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="08bf1-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="08bf1-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="08bf1-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
