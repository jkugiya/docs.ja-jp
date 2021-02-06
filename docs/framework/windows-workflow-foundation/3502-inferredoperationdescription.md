---
description: '詳細情報: 3502-InferredOperationDescription'
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 5068a3553484b38242951ef985886190f8027035
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631490"
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="42e23-103">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="42e23-103">3502 - InferredOperationDescription</span></span>

## <a name="properties"></a><span data-ttu-id="42e23-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="42e23-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="42e23-105">id</span><span class="sxs-lookup"><span data-stu-id="42e23-105">ID</span></span>|<span data-ttu-id="42e23-106">3502</span><span class="sxs-lookup"><span data-stu-id="42e23-106">3502</span></span>|  
|<span data-ttu-id="42e23-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="42e23-107">Keywords</span></span>|<span data-ttu-id="42e23-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="42e23-108">WFServices</span></span>|  
|<span data-ttu-id="42e23-109">Level</span><span class="sxs-lookup"><span data-stu-id="42e23-109">Level</span></span>|<span data-ttu-id="42e23-110">Information</span><span class="sxs-lookup"><span data-stu-id="42e23-110">Information</span></span>|  
|<span data-ttu-id="42e23-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="42e23-111">Channel</span></span>|<span data-ttu-id="42e23-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="42e23-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="42e23-113">説明</span><span class="sxs-lookup"><span data-stu-id="42e23-113">Description</span></span>  

 <span data-ttu-id="42e23-114">OperationDescription が WorkflowService から推論されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="42e23-114">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="42e23-115">Message</span><span class="sxs-lookup"><span data-stu-id="42e23-115">Message</span></span>  

 <span data-ttu-id="42e23-116">コントラクト '%2' 内の Name='%1' の OperationDescription が WorkflowService から推論されました。</span><span class="sxs-lookup"><span data-stu-id="42e23-116">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="42e23-117">IsOneWay=%3。</span><span class="sxs-lookup"><span data-stu-id="42e23-117">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="42e23-118">詳細</span><span class="sxs-lookup"><span data-stu-id="42e23-118">Details</span></span>  
  
|<span data-ttu-id="42e23-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="42e23-119">Data Item Name</span></span>|<span data-ttu-id="42e23-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="42e23-120">Data Item Type</span></span>|<span data-ttu-id="42e23-121">説明</span><span class="sxs-lookup"><span data-stu-id="42e23-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="42e23-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="42e23-122">OperationName</span></span>|<span data-ttu-id="42e23-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="42e23-123">xs:string</span></span>|<span data-ttu-id="42e23-124">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="42e23-124">The name of the operation.</span></span>|  
|<span data-ttu-id="42e23-125">ContractName</span><span class="sxs-lookup"><span data-stu-id="42e23-125">ContractName</span></span>|<span data-ttu-id="42e23-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="42e23-126">xs:string</span></span>|<span data-ttu-id="42e23-127">コントラクトの名前。</span><span class="sxs-lookup"><span data-stu-id="42e23-127">The name of the contract.</span></span>|  
|<span data-ttu-id="42e23-128">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="42e23-128">IsOneWay</span></span>|<span data-ttu-id="42e23-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="42e23-129">xs:string</span></span>|<span data-ttu-id="42e23-130">True または False はコントラクトが一方向かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="42e23-130">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="42e23-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="42e23-131">AppDomain</span></span>|<span data-ttu-id="42e23-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="42e23-132">xs:string</span></span>|<span data-ttu-id="42e23-133">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="42e23-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
