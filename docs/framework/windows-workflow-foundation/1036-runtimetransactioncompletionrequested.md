---
description: '詳細については、次のページを参照してください: 1036-Runtimetransactionを要求'
title: 1036 - RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: e07400902d5c3e08732385ab30e1be0d72d3e997
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667890"
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="f6ad6-103">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="f6ad6-103">1036 - RuntimeTransactionCompletionRequested</span></span>

## <a name="properties"></a><span data-ttu-id="f6ad6-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f6ad6-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f6ad6-105">id</span><span class="sxs-lookup"><span data-stu-id="f6ad6-105">ID</span></span>|<span data-ttu-id="f6ad6-106">1036</span><span class="sxs-lookup"><span data-stu-id="f6ad6-106">1036</span></span>|  
|<span data-ttu-id="f6ad6-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="f6ad6-107">Keywords</span></span>|<span data-ttu-id="f6ad6-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f6ad6-108">WFRuntime</span></span>|  
|<span data-ttu-id="f6ad6-109">Level</span><span class="sxs-lookup"><span data-stu-id="f6ad6-109">Level</span></span>|<span data-ttu-id="f6ad6-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="f6ad6-110">Verbose</span></span>|  
|<span data-ttu-id="f6ad6-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="f6ad6-111">Channel</span></span>|<span data-ttu-id="f6ad6-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f6ad6-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f6ad6-113">説明</span><span class="sxs-lookup"><span data-stu-id="f6ad6-113">Description</span></span>  

 <span data-ttu-id="f6ad6-114">アクティビティがランタイムのトランザクションの完了をスケジュールしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="f6ad6-114">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f6ad6-115">Message</span><span class="sxs-lookup"><span data-stu-id="f6ad6-115">Message</span></span>  

 <span data-ttu-id="f6ad6-116">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' はランタイム トランザクションの完了をスケジュールしました。</span><span class="sxs-lookup"><span data-stu-id="f6ad6-116">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f6ad6-117">詳細</span><span class="sxs-lookup"><span data-stu-id="f6ad6-117">Details</span></span>  
  
|<span data-ttu-id="f6ad6-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="f6ad6-118">Data Item Name</span></span>|<span data-ttu-id="f6ad6-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="f6ad6-119">Data Item Type</span></span>|<span data-ttu-id="f6ad6-120">説明</span><span class="sxs-lookup"><span data-stu-id="f6ad6-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f6ad6-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="f6ad6-121">Activity</span></span>|<span data-ttu-id="f6ad6-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6ad6-122">xs:string</span></span>|<span data-ttu-id="f6ad6-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="f6ad6-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="f6ad6-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f6ad6-124">DisplayName</span></span>|<span data-ttu-id="f6ad6-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6ad6-125">xs:string</span></span>|<span data-ttu-id="f6ad6-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="f6ad6-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="f6ad6-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="f6ad6-127">InstanceId</span></span>|<span data-ttu-id="f6ad6-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6ad6-128">xs:string</span></span>|<span data-ttu-id="f6ad6-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="f6ad6-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="f6ad6-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f6ad6-130">AppDomain</span></span>|<span data-ttu-id="f6ad6-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6ad6-131">xs:string</span></span>|<span data-ttu-id="f6ad6-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="f6ad6-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
