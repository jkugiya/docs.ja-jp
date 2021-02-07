---
description: '詳細情報: 4208-RetryingSqlCommandDueToSqlError'
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: 11ea2260f6a2ceffc1ffdbfce2cb3e3ce784076d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755305"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="cf345-103">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="cf345-103">4208 - RetryingSqlCommandDueToSqlError</span></span>

## <a name="properties"></a><span data-ttu-id="cf345-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="cf345-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf345-105">id</span><span class="sxs-lookup"><span data-stu-id="cf345-105">ID</span></span>|<span data-ttu-id="cf345-106">4208</span><span class="sxs-lookup"><span data-stu-id="cf345-106">4208</span></span>|  
|<span data-ttu-id="cf345-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="cf345-107">Keywords</span></span>|<span data-ttu-id="cf345-108">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="cf345-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="cf345-109">Level</span><span class="sxs-lookup"><span data-stu-id="cf345-109">Level</span></span>|<span data-ttu-id="cf345-110">Information</span><span class="sxs-lookup"><span data-stu-id="cf345-110">Information</span></span>|  
|<span data-ttu-id="cf345-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="cf345-111">Channel</span></span>|<span data-ttu-id="cf345-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="cf345-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cf345-113">説明</span><span class="sxs-lookup"><span data-stu-id="cf345-113">Description</span></span>  

 <span data-ttu-id="cf345-114">SQL プロバイダーは SQL エラーのために SQL コマンドを再試行していることを示します。</span><span class="sxs-lookup"><span data-stu-id="cf345-114">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cf345-115">Message</span><span class="sxs-lookup"><span data-stu-id="cf345-115">Message</span></span>  

 <span data-ttu-id="cf345-116">SQL エラー番号 %1 のため、SQL コマンドを再試行します。</span><span class="sxs-lookup"><span data-stu-id="cf345-116">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cf345-117">詳細</span><span class="sxs-lookup"><span data-stu-id="cf345-117">Details</span></span>  
  
|<span data-ttu-id="cf345-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="cf345-118">Data Item Name</span></span>|<span data-ttu-id="cf345-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="cf345-119">Data Item Type</span></span>|<span data-ttu-id="cf345-120">説明</span><span class="sxs-lookup"><span data-stu-id="cf345-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cf345-121">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="cf345-121">ErrorNumber</span></span>|<span data-ttu-id="cf345-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="cf345-122">xs:string</span></span>|<span data-ttu-id="cf345-123">SQL エラー番号。</span><span class="sxs-lookup"><span data-stu-id="cf345-123">The SQL error number.</span></span>|  
|<span data-ttu-id="cf345-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cf345-124">AppDomain</span></span>|<span data-ttu-id="cf345-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="cf345-125">xs:string</span></span>|<span data-ttu-id="cf345-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="cf345-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
