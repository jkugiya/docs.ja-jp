---
description: 詳細については、「1005-WorkflowApplicationIdled」を参照してください。
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: ee8d0b7ff2155333213a718a04c3966024fda89d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755604"
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="93a92-103">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="93a92-103">1005 - WorkflowApplicationIdled</span></span>

## <a name="properties"></a><span data-ttu-id="93a92-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="93a92-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="93a92-105">id</span><span class="sxs-lookup"><span data-stu-id="93a92-105">ID</span></span>|<span data-ttu-id="93a92-106">1005</span><span class="sxs-lookup"><span data-stu-id="93a92-106">1005</span></span>|  
|<span data-ttu-id="93a92-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="93a92-107">Keywords</span></span>|<span data-ttu-id="93a92-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="93a92-108">WFRuntime</span></span>|  
|<span data-ttu-id="93a92-109">Level</span><span class="sxs-lookup"><span data-stu-id="93a92-109">Level</span></span>|<span data-ttu-id="93a92-110">Information</span><span class="sxs-lookup"><span data-stu-id="93a92-110">Information</span></span>|  
|<span data-ttu-id="93a92-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="93a92-111">Channel</span></span>|<span data-ttu-id="93a92-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="93a92-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="93a92-113">説明</span><span class="sxs-lookup"><span data-stu-id="93a92-113">Description</span></span>  

 <span data-ttu-id="93a92-114">ワークフロー アプリケーションがアイドル状態になったことを示します。</span><span class="sxs-lookup"><span data-stu-id="93a92-114">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="93a92-115">Message</span><span class="sxs-lookup"><span data-stu-id="93a92-115">Message</span></span>  

 <span data-ttu-id="93a92-116">WorkflowApplication ID: '%1' がアイドル状態になりました。</span><span class="sxs-lookup"><span data-stu-id="93a92-116">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="93a92-117">詳細</span><span class="sxs-lookup"><span data-stu-id="93a92-117">Details</span></span>  
  
|<span data-ttu-id="93a92-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="93a92-118">Data Item Name</span></span>|<span data-ttu-id="93a92-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="93a92-119">Data Item Type</span></span>|<span data-ttu-id="93a92-120">説明</span><span class="sxs-lookup"><span data-stu-id="93a92-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="93a92-121">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="93a92-121">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="93a92-122">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="93a92-122">The workflow application id</span></span>|  
|<span data-ttu-id="93a92-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="93a92-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="93a92-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="93a92-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
