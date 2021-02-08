---
description: 詳細については、「3508-TrackingProfileNotFound」を参照してください。
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 3e97af1689a868fb103b06413a0c4f28b0c1f652
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778010"
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="c7b4f-103">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="c7b4f-103">3508 - TrackingProfileNotFound</span></span>

## <a name="properties"></a><span data-ttu-id="c7b4f-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c7b4f-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c7b4f-105">id</span><span class="sxs-lookup"><span data-stu-id="c7b4f-105">ID</span></span>|<span data-ttu-id="c7b4f-106">3508</span><span class="sxs-lookup"><span data-stu-id="c7b4f-106">3508</span></span>|  
|<span data-ttu-id="c7b4f-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="c7b4f-107">Keywords</span></span>|<span data-ttu-id="c7b4f-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="c7b4f-108">WFServices</span></span>|  
|<span data-ttu-id="c7b4f-109">Level</span><span class="sxs-lookup"><span data-stu-id="c7b4f-109">Level</span></span>|<span data-ttu-id="c7b4f-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="c7b4f-110">Verbose</span></span>|  
|<span data-ttu-id="c7b4f-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="c7b4f-111">Channel</span></span>|<span data-ttu-id="c7b4f-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c7b4f-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c7b4f-113">説明</span><span class="sxs-lookup"><span data-stu-id="c7b4f-113">Description</span></span>  

 <span data-ttu-id="c7b4f-114">構成ファイル内に TrackingProfile がないか、または ActivityDefinitionId がプロファイルと一致していないことを示します。</span><span class="sxs-lookup"><span data-stu-id="c7b4f-114">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c7b4f-115">Message</span><span class="sxs-lookup"><span data-stu-id="c7b4f-115">Message</span></span>  

 <span data-ttu-id="c7b4f-116">ActivityDefinitionId '%2' の TrackingProfile '%1' が見つかりません。</span><span class="sxs-lookup"><span data-stu-id="c7b4f-116">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="c7b4f-117">config ファイルに TrackingProfile がないか、ActivityDefinitionId が一致しません。</span><span class="sxs-lookup"><span data-stu-id="c7b4f-117">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c7b4f-118">詳細</span><span class="sxs-lookup"><span data-stu-id="c7b4f-118">Details</span></span>  
  
|<span data-ttu-id="c7b4f-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c7b4f-119">Data Item Name</span></span>|<span data-ttu-id="c7b4f-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c7b4f-120">Data Item Type</span></span>|<span data-ttu-id="c7b4f-121">説明</span><span class="sxs-lookup"><span data-stu-id="c7b4f-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c7b4f-122">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="c7b4f-122">TrackingProfile</span></span>|<span data-ttu-id="c7b4f-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="c7b4f-123">xs:string</span></span>|<span data-ttu-id="c7b4f-124">追跡プロファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="c7b4f-124">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="c7b4f-125">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="c7b4f-125">ActivityDefinitionId</span></span>|<span data-ttu-id="c7b4f-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="c7b4f-126">xs:string</span></span>|<span data-ttu-id="c7b4f-127">アクティビティ定義 ID。</span><span class="sxs-lookup"><span data-stu-id="c7b4f-127">The activity definition id.</span></span>|  
|<span data-ttu-id="c7b4f-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c7b4f-128">AppDomain</span></span>|<span data-ttu-id="c7b4f-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="c7b4f-129">xs:string</span></span>|<span data-ttu-id="c7b4f-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c7b4f-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
