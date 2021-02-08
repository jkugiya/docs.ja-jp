---
description: '詳細情報: 4203-RenewLockSystemError'
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 0e62c501391fcaec56f2016631707832170775ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792779"
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="2d00e-103">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="2d00e-103">4203 - RenewLockSystemError</span></span>

## <a name="properties"></a><span data-ttu-id="2d00e-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2d00e-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2d00e-105">id</span><span class="sxs-lookup"><span data-stu-id="2d00e-105">ID</span></span>|<span data-ttu-id="2d00e-106">4203</span><span class="sxs-lookup"><span data-stu-id="2d00e-106">4203</span></span>|  
|<span data-ttu-id="2d00e-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="2d00e-107">Keywords</span></span>|<span data-ttu-id="2d00e-108">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="2d00e-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="2d00e-109">Level</span><span class="sxs-lookup"><span data-stu-id="2d00e-109">Level</span></span>|<span data-ttu-id="2d00e-110">エラー</span><span class="sxs-lookup"><span data-stu-id="2d00e-110">Error</span></span>|  
|<span data-ttu-id="2d00e-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="2d00e-111">Channel</span></span>|<span data-ttu-id="2d00e-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="2d00e-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2d00e-113">説明</span><span class="sxs-lookup"><span data-stu-id="2d00e-113">Description</span></span>  

 <span data-ttu-id="2d00e-114">ロックの有効期限が既に過ぎているか、またはロック所有者が削除されたために、SQL プロバイダーはロックの有効期限を延長できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="2d00e-114">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="2d00e-115">SqlWorkflowInstanceStore は中止されます。</span><span class="sxs-lookup"><span data-stu-id="2d00e-115">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2d00e-116">Message</span><span class="sxs-lookup"><span data-stu-id="2d00e-116">Message</span></span>  

 <span data-ttu-id="2d00e-117">ロックの有効期限を延長できませんでした。ロックの有効期限が既に過ぎているか、ロックの所有者が削除されました。</span><span class="sxs-lookup"><span data-stu-id="2d00e-117">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="2d00e-118">SqlWorkflowInstanceStore を中止します。</span><span class="sxs-lookup"><span data-stu-id="2d00e-118">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2d00e-119">詳細</span><span class="sxs-lookup"><span data-stu-id="2d00e-119">Details</span></span>  
  
|<span data-ttu-id="2d00e-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2d00e-120">Data Item Name</span></span>|<span data-ttu-id="2d00e-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2d00e-121">Data Item Type</span></span>|<span data-ttu-id="2d00e-122">説明</span><span class="sxs-lookup"><span data-stu-id="2d00e-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2d00e-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2d00e-123">AppDomain</span></span>|<span data-ttu-id="2d00e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="2d00e-124">xs:string</span></span>|<span data-ttu-id="2d00e-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2d00e-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
