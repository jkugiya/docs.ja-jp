---
description: '詳細情報: トレースの種類の概要'
title: トレースの種類の概要
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: ebfe9de16766494a6aebe0a8d2501954855dc4df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803218"
---
# <a name="trace-type-summary"></a><span data-ttu-id="b8979-103">トレースの種類の概要</span><span class="sxs-lookup"><span data-stu-id="b8979-103">Trace Type Summary</span></span>

<span data-ttu-id="b8979-104">[ソースレベル](xref:System.Diagnostics.SourceLevels) では、さまざまなトレースレベル (重大、エラー、警告、情報、および詳細) を定義すると共に、 `ActivityTracing` トレース境界とアクティビティ転送イベントの出力を切り替えるフラグの説明を提供します。</span><span class="sxs-lookup"><span data-stu-id="b8979-104">[Source Levels](xref:System.Diagnostics.SourceLevels) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides a description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="b8979-105">また <xref:System.Diagnostics.TraceEventType> 、から出力できるトレースの種類を確認することもでき <xref:System.Diagnostics> ます。</span><span class="sxs-lookup"><span data-stu-id="b8979-105">You can also review <xref:System.Diagnostics.TraceEventType> for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="b8979-106">最も重要な種類を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b8979-106">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="b8979-107">トレースの種類</span><span class="sxs-lookup"><span data-stu-id="b8979-107">Trace Type</span></span>|<span data-ttu-id="b8979-108">説明</span><span class="sxs-lookup"><span data-stu-id="b8979-108">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="b8979-109">重大</span><span class="sxs-lookup"><span data-stu-id="b8979-109">Critical</span></span>|<span data-ttu-id="b8979-110">致命的なエラーまたはアプリケーションのクラッシュ。</span><span class="sxs-lookup"><span data-stu-id="b8979-110">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="b8979-111">エラー</span><span class="sxs-lookup"><span data-stu-id="b8979-111">Error</span></span>|<span data-ttu-id="b8979-112">回復可能なエラー。</span><span class="sxs-lookup"><span data-stu-id="b8979-112">Recoverable error.</span></span>|  
|<span data-ttu-id="b8979-113">警告</span><span class="sxs-lookup"><span data-stu-id="b8979-113">Warning</span></span>|<span data-ttu-id="b8979-114">情報メッセージです。</span><span class="sxs-lookup"><span data-stu-id="b8979-114">Informational message.</span></span>|  
|<span data-ttu-id="b8979-115">Information</span><span class="sxs-lookup"><span data-stu-id="b8979-115">Information</span></span>|<span data-ttu-id="b8979-116">重大ではない問題。</span><span class="sxs-lookup"><span data-stu-id="b8979-116">Non-critical problem.</span></span>|  
|<span data-ttu-id="b8979-117">"詳細"</span><span class="sxs-lookup"><span data-stu-id="b8979-117">Verbose</span></span>|<span data-ttu-id="b8979-118">トレースのデバッグ。</span><span class="sxs-lookup"><span data-stu-id="b8979-118">Debugging trace.</span></span>|  
|<span data-ttu-id="b8979-119">開始</span><span class="sxs-lookup"><span data-stu-id="b8979-119">Start</span></span>|<span data-ttu-id="b8979-120">処理の論理単位の開始。</span><span class="sxs-lookup"><span data-stu-id="b8979-120">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="b8979-121">[中断]</span><span class="sxs-lookup"><span data-stu-id="b8979-121">Suspend</span></span>|<span data-ttu-id="b8979-122">処理の論理単位の中断。</span><span class="sxs-lookup"><span data-stu-id="b8979-122">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="b8979-123">再開</span><span class="sxs-lookup"><span data-stu-id="b8979-123">Resume</span></span>|<span data-ttu-id="b8979-124">処理の論理単位の再開。</span><span class="sxs-lookup"><span data-stu-id="b8979-124">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="b8979-125">Stop</span><span class="sxs-lookup"><span data-stu-id="b8979-125">Stop</span></span>|<span data-ttu-id="b8979-126">処理の論理単位の停止。</span><span class="sxs-lookup"><span data-stu-id="b8979-126">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="b8979-127">転送</span><span class="sxs-lookup"><span data-stu-id="b8979-127">Transfer</span></span>|<span data-ttu-id="b8979-128">相関 ID の変更。</span><span class="sxs-lookup"><span data-stu-id="b8979-128">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="b8979-129">アクティビティは、上記のトレースの種類の組み合わせとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="b8979-129">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="b8979-130">ローカル (トレース ソース) スコープでの典型的なアクティビティを定義する正規表現は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b8979-130">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="b8979-131">これは、アクティビティが次の条件を満たす必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="b8979-131">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="b8979-132">アクティビティは、Start トレースによって開始し、Stop トレースによって停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8979-132">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="b8979-133">Suspend トレースまたは Resume トレースの直前に Transfer トレースが必要です。</span><span class="sxs-lookup"><span data-stu-id="b8979-133">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="b8979-134">Suspend トレースと Resume トレースが存在する場合、これらのトレースの間にトレースが存在することはできません。</span><span class="sxs-lookup"><span data-stu-id="b8979-134">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="b8979-135">上記の条件を満たしている限り、Critical/Error/Warning/Information/Verbose/Transfer の各トレースはいくつでも含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b8979-135">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="b8979-136">グローバル スコープでの典型的なアクティビティを定義する正規表現は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b8979-136">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
`R+`  
  
 <span data-ttu-id="b8979-137">R はローカル スコープのアクティビティを表す正規表現です。</span><span class="sxs-lookup"><span data-stu-id="b8979-137">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="b8979-138">これは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b8979-138">This translates to,</span></span>  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
