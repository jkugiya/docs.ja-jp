---
description: '詳細情報: 3557-TransactedReceiveScopeEndCommitFailed'
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 7865ae27e7ce5b3f13b3567f3f8aeebd6edf3fd4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777984"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="4e792-103">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="4e792-103">3557 - TransactedReceiveScopeEndCommitFailed</span></span>

## <a name="properties"></a><span data-ttu-id="4e792-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4e792-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4e792-105">id</span><span class="sxs-lookup"><span data-stu-id="4e792-105">ID</span></span>|<span data-ttu-id="4e792-106">3557</span><span class="sxs-lookup"><span data-stu-id="4e792-106">3557</span></span>|  
|<span data-ttu-id="4e792-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="4e792-107">Keywords</span></span>|<span data-ttu-id="4e792-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="4e792-108">WFServices</span></span>|  
|<span data-ttu-id="4e792-109">Level</span><span class="sxs-lookup"><span data-stu-id="4e792-109">Level</span></span>|<span data-ttu-id="4e792-110">Information</span><span class="sxs-lookup"><span data-stu-id="4e792-110">Information</span></span>|  
|<span data-ttu-id="4e792-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="4e792-111">Channel</span></span>|<span data-ttu-id="4e792-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="4e792-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4e792-113">説明</span><span class="sxs-lookup"><span data-stu-id="4e792-113">Description</span></span>  

 <span data-ttu-id="4e792-114">CommittableTransaction の EndCommit への呼び出しが TransactionException をスローしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="4e792-114">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4e792-115">Message</span><span class="sxs-lookup"><span data-stu-id="4e792-115">Message</span></span>  

 <span data-ttu-id="4e792-116">id = '%1' の CommittableTransaction に対する EndCommit への呼び出しにより、次のメッセージと共に TransactionException がスローされました: '%2'。</span><span class="sxs-lookup"><span data-stu-id="4e792-116">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4e792-117">詳細</span><span class="sxs-lookup"><span data-stu-id="4e792-117">Details</span></span>  
  
|<span data-ttu-id="4e792-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="4e792-118">Data Item Name</span></span>|<span data-ttu-id="4e792-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="4e792-119">Data Item Type</span></span>|<span data-ttu-id="4e792-120">説明</span><span class="sxs-lookup"><span data-stu-id="4e792-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4e792-121">TransactionId</span><span class="sxs-lookup"><span data-stu-id="4e792-121">TransactionId</span></span>|<span data-ttu-id="4e792-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="4e792-122">xs:string</span></span>|<span data-ttu-id="4e792-123">CommittableTransaction の ID。</span><span class="sxs-lookup"><span data-stu-id="4e792-123">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="4e792-124">例外</span><span class="sxs-lookup"><span data-stu-id="4e792-124">Exception</span></span>|<span data-ttu-id="4e792-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="4e792-125">xs:string</span></span>|<span data-ttu-id="4e792-126">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="4e792-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="4e792-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4e792-127">AppDomain</span></span>|<span data-ttu-id="4e792-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="4e792-128">xs:string</span></span>|<span data-ttu-id="4e792-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="4e792-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
