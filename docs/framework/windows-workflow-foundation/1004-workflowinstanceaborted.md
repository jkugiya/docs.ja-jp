---
description: '詳細情報: 1004-WorkflowInstanceAborted'
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: 4aaa0899da9b0b8510684a13537a8cb8f9117ee1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755619"
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="da925-103">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="da925-103">1004 - WorkflowInstanceAborted</span></span>

## <a name="properties"></a><span data-ttu-id="da925-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="da925-104">Properties</span></span>

|||
|-|-|
|<span data-ttu-id="da925-105">id</span><span class="sxs-lookup"><span data-stu-id="da925-105">ID</span></span>|<span data-ttu-id="da925-106">1004</span><span class="sxs-lookup"><span data-stu-id="da925-106">1004</span></span>|
|<span data-ttu-id="da925-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="da925-107">Keywords</span></span>|<span data-ttu-id="da925-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="da925-108">WFRuntime</span></span>|
|<span data-ttu-id="da925-109">Level</span><span class="sxs-lookup"><span data-stu-id="da925-109">Level</span></span>|<span data-ttu-id="da925-110">Information</span><span class="sxs-lookup"><span data-stu-id="da925-110">Information</span></span>|
|<span data-ttu-id="da925-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="da925-111">Channel</span></span>|<span data-ttu-id="da925-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="da925-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|

## <a name="description"></a><span data-ttu-id="da925-113">説明</span><span class="sxs-lookup"><span data-stu-id="da925-113">Description</span></span>

<span data-ttu-id="da925-114">ワークフローインスタンスが例外で中止されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="da925-114">Indicates a workflow instance has aborted with an exception.</span></span>

## <a name="message"></a><span data-ttu-id="da925-115">Message</span><span class="sxs-lookup"><span data-stu-id="da925-115">Message</span></span>

<span data-ttu-id="da925-116">WorkflowInstance ID: '%1' は例外により中止されました。</span><span class="sxs-lookup"><span data-stu-id="da925-116">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>

## <a name="details"></a><span data-ttu-id="da925-117">詳細</span><span class="sxs-lookup"><span data-stu-id="da925-117">Details</span></span>

|<span data-ttu-id="da925-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="da925-118">Data Item Name</span></span>|<span data-ttu-id="da925-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="da925-119">Data Item Type</span></span>|<span data-ttu-id="da925-120">説明</span><span class="sxs-lookup"><span data-stu-id="da925-120">Description</span></span>|
|--------------------|--------------------|-----------------|
|<span data-ttu-id="da925-121">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="da925-121">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="da925-122">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="da925-122">The instance id for the workflow</span></span>|
|<span data-ttu-id="da925-123">例外</span><span class="sxs-lookup"><span data-stu-id="da925-123">Exception</span></span>|`xs:string`|<span data-ttu-id="da925-124">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="da925-124">The exception details for the exception</span></span>|
|<span data-ttu-id="da925-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="da925-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="da925-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="da925-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
