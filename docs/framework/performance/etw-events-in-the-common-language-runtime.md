---
title: 共通言語ランタイムの ETW イベント
description: 共通言語ランタイム (CLR) の Windows イベント トレーシング (ETW) イベントに関する概要とリンクをご覧ください。
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
ms.openlocfilehash: ab9cb7c53171ebf1dd0d48dec133464fe4042043
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263633"
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="27c6c-103">共通言語ランタイムの ETW イベント</span><span class="sxs-lookup"><span data-stu-id="27c6c-103">ETW Events in the Common Language Runtime</span></span>

<span data-ttu-id="27c6c-104">共通言語ランタイム (CLR) は、さまざまなデバッグとプロファイリング イベントを通じて、有用な Windows イベント トレーシング (ETW) の診断情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="27c6c-104">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="27c6c-105">CLR ETW イベントは、Windows ETW トレース システムを利用して、共通言語ランタイムによって提供される既存のプロファイリングとデバッグのサポートを拡張します。</span><span class="sxs-lookup"><span data-stu-id="27c6c-105">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="27c6c-106">ETW の詳細については、「[ETW によるデバッグとパフォーマンス チューニングの向上](/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)」の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27c6c-106">More information about ETW is available in the [Improve Debugging and Performance Tuning with ETW](/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) article.</span></span> <span data-ttu-id="27c6c-107">Xperf に関する情報は、NTDebugging のブログ エントリ「[Windows Performance Toolkit - Xperf](/archive/blogs/ntdebugging/windows-performance-toolkit-xperf)」にあります。</span><span class="sxs-lookup"><span data-stu-id="27c6c-107">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="27c6c-108">イベント トピックに記載されているすべてのイベントには、.NET Framework 4 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="27c6c-108">The .NET Framework 4 or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="27c6c-109">Windows Vista オペレーティング システムは、サポートされる最小のクライアントで、Windows Server 2008 は、サポートされる最小のサーバーです。</span><span class="sxs-lookup"><span data-stu-id="27c6c-109">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27c6c-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="27c6c-110">In This Section</span></span>  

 [<span data-ttu-id="27c6c-111">.NET Framework のログ記録の制御</span><span class="sxs-lookup"><span data-stu-id="27c6c-111">Controlling .NET Framework Logging</span></span>](controlling-logging.md)  
 <span data-ttu-id="27c6c-112">ETW イベントをキャプチャおよび表示するためのツールとコマンドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="27c6c-112">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="27c6c-113">CLR ETW プロバイダー</span><span class="sxs-lookup"><span data-stu-id="27c6c-113">CLR ETW Providers</span></span>](clr-etw-providers.md)  
 <span data-ttu-id="27c6c-114">ランタイム プロバイダーとランダウン プロバイダーの情報、およびこれらを使用して ETW データを収集する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="27c6c-114">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="27c6c-115">CLR ETW キーワードおよびレベル</span><span class="sxs-lookup"><span data-stu-id="27c6c-115">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="27c6c-116">イベントをカテゴリ別にフィルタ処理できるランタイム プロバイダーとランダウン プロバイダーのキーワードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="27c6c-116">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="27c6c-117">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="27c6c-117">CLR ETW Events</span></span>](clr-etw-events.md)  
 <span data-ttu-id="27c6c-118">CLR ETW イベント、キーワード、レベル、およびイベント データに関する詳細情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="27c6c-118">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27c6c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="27c6c-119">See also</span></span>

- [<span data-ttu-id="27c6c-120">.NET Framework の ETW イベント</span><span class="sxs-lookup"><span data-stu-id="27c6c-120">ETW Events in the .NET Framework</span></span>](etw-events.md)
