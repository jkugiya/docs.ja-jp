---
description: '詳細情報: 2577-TryCatchExceptionDuringCancelation'
title: 2577 - TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: e02e7722dadfe38b9fc1fbb92e809ae8f80cbd2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778101"
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="92351-103">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="92351-103">2577 - TryCatchExceptionDuringCancelation</span></span>

## <a name="properties"></a><span data-ttu-id="92351-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="92351-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="92351-105">id</span><span class="sxs-lookup"><span data-stu-id="92351-105">ID</span></span>|<span data-ttu-id="92351-106">2577</span><span class="sxs-lookup"><span data-stu-id="92351-106">2577</span></span>|  
|<span data-ttu-id="92351-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="92351-107">Keywords</span></span>|<span data-ttu-id="92351-108">WFActivities</span><span class="sxs-lookup"><span data-stu-id="92351-108">WFActivities</span></span>|  
|<span data-ttu-id="92351-109">Level</span><span class="sxs-lookup"><span data-stu-id="92351-109">Level</span></span>|<span data-ttu-id="92351-110">警告</span><span class="sxs-lookup"><span data-stu-id="92351-110">Warning</span></span>|  
|<span data-ttu-id="92351-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="92351-111">Channel</span></span>|<span data-ttu-id="92351-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="92351-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="92351-113">説明</span><span class="sxs-lookup"><span data-stu-id="92351-113">Description</span></span>  

 <span data-ttu-id="92351-114">TryCatch アクティビティの子アクティビティが取り消し中に例外をスローしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="92351-114">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="92351-115">Message</span><span class="sxs-lookup"><span data-stu-id="92351-115">Message</span></span>  

 <span data-ttu-id="92351-116">TryCatch アクティビティ '%1' の子アクティビティは取り消し中に例外をスローしました。</span><span class="sxs-lookup"><span data-stu-id="92351-116">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="92351-117">詳細</span><span class="sxs-lookup"><span data-stu-id="92351-117">Details</span></span>  
  
|<span data-ttu-id="92351-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="92351-118">Data Item Name</span></span>|<span data-ttu-id="92351-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="92351-119">Data Item Type</span></span>|<span data-ttu-id="92351-120">説明</span><span class="sxs-lookup"><span data-stu-id="92351-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="92351-121">DisplayName</span><span class="sxs-lookup"><span data-stu-id="92351-121">DisplayName</span></span>|<span data-ttu-id="92351-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="92351-122">xs:string</span></span>|<span data-ttu-id="92351-123">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="92351-123">The display name of the activity.</span></span>|  
|<span data-ttu-id="92351-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="92351-124">AppDomain</span></span>|<span data-ttu-id="92351-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="92351-125">xs:string</span></span>|<span data-ttu-id="92351-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="92351-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
