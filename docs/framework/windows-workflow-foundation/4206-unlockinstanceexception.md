---
description: '詳細情報: 4206-UnlockInstanceException'
title: 4206 - UnlockInstanceException
ms.date: 03/30/2017
ms.assetid: 5a46dc5f-d517-4135-8905-25a42f01206b
ms.openlocfilehash: 7c281b7471869fc2361b1c7fb158559e4c9fae65
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99676275"
---
# <a name="4206---unlockinstanceexception"></a><span data-ttu-id="c6728-103">4206 - UnlockInstanceException</span><span class="sxs-lookup"><span data-stu-id="c6728-103">4206 - UnlockInstanceException</span></span>

## <a name="properties"></a><span data-ttu-id="c6728-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c6728-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c6728-105">id</span><span class="sxs-lookup"><span data-stu-id="c6728-105">ID</span></span>|<span data-ttu-id="c6728-106">4206</span><span class="sxs-lookup"><span data-stu-id="c6728-106">4206</span></span>|  
|<span data-ttu-id="c6728-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="c6728-107">Keywords</span></span>|<span data-ttu-id="c6728-108">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="c6728-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="c6728-109">Level</span><span class="sxs-lookup"><span data-stu-id="c6728-109">Level</span></span>|<span data-ttu-id="c6728-110">エラー</span><span class="sxs-lookup"><span data-stu-id="c6728-110">Error</span></span>|  
|<span data-ttu-id="c6728-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="c6728-111">Channel</span></span>|<span data-ttu-id="c6728-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c6728-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c6728-113">説明</span><span class="sxs-lookup"><span data-stu-id="c6728-113">Description</span></span>  

 <span data-ttu-id="c6728-114">インスタンスのロックを解除しようとしているときに例外が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c6728-114">Indicates an exception was encountered while trying to unlock an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c6728-115">Message</span><span class="sxs-lookup"><span data-stu-id="c6728-115">Message</span></span>  

 <span data-ttu-id="c6728-116">インスタンスのロックを解除しようとして、例外 %1 が発生しました。</span><span class="sxs-lookup"><span data-stu-id="c6728-116">Encountered exception %1 while attempting to unlock instance.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c6728-117">詳細</span><span class="sxs-lookup"><span data-stu-id="c6728-117">Details</span></span>  
  
|<span data-ttu-id="c6728-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c6728-118">Data Item Name</span></span>|<span data-ttu-id="c6728-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c6728-119">Data Item Type</span></span>|<span data-ttu-id="c6728-120">説明</span><span class="sxs-lookup"><span data-stu-id="c6728-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c6728-121">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="c6728-121">ExceptionMessage</span></span>|<span data-ttu-id="c6728-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6728-122">xs:string</span></span>|<span data-ttu-id="c6728-123">SQL 例外からのメッセージ。</span><span class="sxs-lookup"><span data-stu-id="c6728-123">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="c6728-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c6728-124">AppDomain</span></span>|<span data-ttu-id="c6728-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6728-125">xs:string</span></span>|<span data-ttu-id="c6728-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c6728-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
