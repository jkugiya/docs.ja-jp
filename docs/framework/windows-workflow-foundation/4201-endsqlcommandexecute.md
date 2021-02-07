---
description: '詳細情報: 4201-EndSqlCommandExecute'
title: 4201 - EndSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
ms.openlocfilehash: e0b98e8da5a0a284bfa55e97f5dde25a2ce42b42
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755370"
---
# <a name="4201---endsqlcommandexecute"></a><span data-ttu-id="0bb5a-103">4201 - EndSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="0bb5a-103">4201 - EndSqlCommandExecute</span></span>

## <a name="properties"></a><span data-ttu-id="0bb5a-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0bb5a-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0bb5a-105">id</span><span class="sxs-lookup"><span data-stu-id="0bb5a-105">ID</span></span>|<span data-ttu-id="0bb5a-106">4201</span><span class="sxs-lookup"><span data-stu-id="0bb5a-106">4201</span></span>|  
|<span data-ttu-id="0bb5a-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="0bb5a-107">Keywords</span></span>|<span data-ttu-id="0bb5a-108">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="0bb5a-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="0bb5a-109">Level</span><span class="sxs-lookup"><span data-stu-id="0bb5a-109">Level</span></span>|<span data-ttu-id="0bb5a-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="0bb5a-110">Verbose</span></span>|  
|<span data-ttu-id="0bb5a-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="0bb5a-111">Channel</span></span>|<span data-ttu-id="0bb5a-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0bb5a-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0bb5a-113">説明</span><span class="sxs-lookup"><span data-stu-id="0bb5a-113">Description</span></span>  

 <span data-ttu-id="0bb5a-114">SQL コマンドの実行が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="0bb5a-114">Indicates a SQL command has finished executing.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0bb5a-115">Message</span><span class="sxs-lookup"><span data-stu-id="0bb5a-115">Message</span></span>  

 <span data-ttu-id="0bb5a-116">SQL コマンドの実行を終了します: %1</span><span class="sxs-lookup"><span data-stu-id="0bb5a-116">End SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="0bb5a-117">詳細</span><span class="sxs-lookup"><span data-stu-id="0bb5a-117">Details</span></span>  
  
|<span data-ttu-id="0bb5a-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="0bb5a-118">Data Item Name</span></span>|<span data-ttu-id="0bb5a-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="0bb5a-119">Data Item Type</span></span>|<span data-ttu-id="0bb5a-120">説明</span><span class="sxs-lookup"><span data-stu-id="0bb5a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0bb5a-121">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="0bb5a-121">SqlCommand</span></span>|<span data-ttu-id="0bb5a-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="0bb5a-122">xs:string</span></span>|<span data-ttu-id="0bb5a-123">実行された SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="0bb5a-123">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="0bb5a-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0bb5a-124">AppDomain</span></span>|<span data-ttu-id="0bb5a-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="0bb5a-125">xs:string</span></span>|<span data-ttu-id="0bb5a-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="0bb5a-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
