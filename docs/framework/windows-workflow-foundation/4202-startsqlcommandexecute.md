---
description: '詳細情報: 4202-StartSqlCommandExecute'
title: 4202 - StartSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
ms.openlocfilehash: 1282f275933eff0effbda75851e33531c55adb36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755335"
---
# <a name="4202---startsqlcommandexecute"></a><span data-ttu-id="5e9c0-103">4202 - StartSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="5e9c0-103">4202 - StartSqlCommandExecute</span></span>

## <a name="properties"></a><span data-ttu-id="5e9c0-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5e9c0-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5e9c0-105">id</span><span class="sxs-lookup"><span data-stu-id="5e9c0-105">ID</span></span>|<span data-ttu-id="5e9c0-106">4202</span><span class="sxs-lookup"><span data-stu-id="5e9c0-106">4202</span></span>|  
|<span data-ttu-id="5e9c0-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="5e9c0-107">Keywords</span></span>|<span data-ttu-id="5e9c0-108">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="5e9c0-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="5e9c0-109">Level</span><span class="sxs-lookup"><span data-stu-id="5e9c0-109">Level</span></span>|<span data-ttu-id="5e9c0-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="5e9c0-110">Verbose</span></span>|  
|<span data-ttu-id="5e9c0-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="5e9c0-111">Channel</span></span>|<span data-ttu-id="5e9c0-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="5e9c0-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5e9c0-113">説明</span><span class="sxs-lookup"><span data-stu-id="5e9c0-113">Description</span></span>  

 <span data-ttu-id="5e9c0-114">SQL コマンドが実行されることを示します。</span><span class="sxs-lookup"><span data-stu-id="5e9c0-114">Indicates a SQL command is being executed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5e9c0-115">Message</span><span class="sxs-lookup"><span data-stu-id="5e9c0-115">Message</span></span>  

 <span data-ttu-id="5e9c0-116">SQL コマンドの実行を開始します: %1</span><span class="sxs-lookup"><span data-stu-id="5e9c0-116">Starting SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="5e9c0-117">詳細</span><span class="sxs-lookup"><span data-stu-id="5e9c0-117">Details</span></span>  
  
|<span data-ttu-id="5e9c0-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="5e9c0-118">Data Item Name</span></span>|<span data-ttu-id="5e9c0-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="5e9c0-119">Data Item Type</span></span>|<span data-ttu-id="5e9c0-120">説明</span><span class="sxs-lookup"><span data-stu-id="5e9c0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5e9c0-121">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="5e9c0-121">SqlCommand</span></span>|<span data-ttu-id="5e9c0-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="5e9c0-122">xs:string</span></span>|<span data-ttu-id="5e9c0-123">実行された SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="5e9c0-123">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="5e9c0-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5e9c0-124">AppDomain</span></span>|<span data-ttu-id="5e9c0-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="5e9c0-125">xs:string</span></span>|<span data-ttu-id="5e9c0-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="5e9c0-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
