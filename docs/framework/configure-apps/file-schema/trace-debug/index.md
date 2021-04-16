---
description: '詳細情報: トレースおよびデバッグ設定のスキーマ'
title: トレースおよびデバッグ設定のスキーマ
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [.NET Framework], trace and debug settings schema
- configuration schema [.NET Framework], trace and debug settings
- configuration settings [.NET Framework], tracing
- schema configuration settings
- configuration settings [.NET Framework], debugging
- trace listeners, trace and debug settings schema
- configuration sections [.NET Framework]
- elements [.NET Framework], trace and debug settings
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
ms.openlocfilehash: 2429585c44952d2ee12547dab8f51662295bf02f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639653"
---
# <a name="trace-and-debug-settings-schema"></a><span data-ttu-id="4f30f-103">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="4f30f-103">Trace and Debug Settings Schema</span></span>

<span data-ttu-id="4f30f-104">トレースおよびデバッグの設定により、メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-104">Trace and debug settings specify trace listeners that collect, store, and route messages, and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="4f30f-105">次の表に、トレース設定とデバッグ設定の各要素の機能を示します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-105">The following table describes the function of each trace and debug settings element.</span></span>  
  
|<span data-ttu-id="4f30f-106">要素</span><span class="sxs-lookup"><span data-stu-id="4f30f-106">Element</span></span>|<span data-ttu-id="4f30f-107">説明</span><span class="sxs-lookup"><span data-stu-id="4f30f-107">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|<span data-ttu-id="4f30f-108">トレース ソースの `Listeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-108">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="4f30f-109">`Listeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-109">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<add>](add-element-for-sharedlisteners.md)|<span data-ttu-id="4f30f-110">`sharedListeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-110">Adds a listener to the `sharedListeners` collection.</span></span>|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="4f30f-111">トレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-111">Specifies the level where a trace switch is set.</span></span>|  
|[\<assert>](assert-element.md)|<span data-ttu-id="4f30f-112"><xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> メソッドの呼び出し時にメッセージ ボックスを表示するかどうかを指定し、メッセージの書き込み先のファイルの名前も指定します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-112">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="4f30f-113">トレース ソースの `Listeners` コレクションを消去します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-113">Clears the `Listeners` collection for a trace source.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="4f30f-114">トレースの `Listeners` コレクションを削除します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-114">Clears the `Listeners` collection for trace.</span></span>|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="4f30f-115">トレース ソースの `Listeners` コレクション内のリスナーにフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-115">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="4f30f-116">トレースの `Listeners` コレクションのリスナーにフィルターに追加します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-116">Adds a filter to a listener in the `Listeners` collection for trace.</span></span>|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="4f30f-117">`sharedListeners` コレクションのリスナーにフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-117">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
|[\<listeners>](listeners-element-for-source.md)|<span data-ttu-id="4f30f-118">トレース ソースの `Listeners` コレクションにリスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-118">Specifies listeners for the `Listeners` collection for a trace source.</span></span>|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="4f30f-119">トレースの `Listeners` コレクションにリスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-119">Specifies listeners for the `Listeners` collection for trace.</span></span>|  
|[\<performanceCounters>](performancecounters-element.md)|<span data-ttu-id="4f30f-120">パフォーマンス カウンターが共有するグローバル メモリのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-120">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="4f30f-121">トレースの `Listeners` コレクションからリスナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-121">Removes a listener from the `Listeners` collection for trace.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="4f30f-122">トレース ソースの `Listeners` コレクションからリスナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-122">Removes a listener from the `Listeners` collection for a trace source.</span></span>|  
|[\<sharedListeners>](sharedlisteners-element.md)|<span data-ttu-id="4f30f-123">任意の source 要素または trace 要素が参照できるリスナーを含みます。</span><span class="sxs-lookup"><span data-stu-id="4f30f-123">Contains listeners that any source or trace element can reference.</span></span>|  
|[\<sources>](sources-element.md)|<span data-ttu-id="4f30f-124">トレース メッセージを開始するトレース ソースを保持します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-124">Contains trace sources that initiate tracing messages.</span></span>|  
|[\<source>](source-element.md)|<span data-ttu-id="4f30f-125">トレース メッセージを開始するトレース ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-125">Specifies a trace source that initiates tracing messages.</span></span>|  
|[\<switches>](switches-element.md)|<span data-ttu-id="4f30f-126">トレース スイッチと、トレース スイッチを設定するレベルを保持します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-126">Contains trace switches and the level where the trace switches are set.</span></span>|  
|[\<system.diagnostics>](system-diagnostics-element.md)|<span data-ttu-id="4f30f-127">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-127">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|[\<trace>](trace-element.md)|<span data-ttu-id="4f30f-128">トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。</span><span class="sxs-lookup"><span data-stu-id="4f30f-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f30f-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f30f-129">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="4f30f-130">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="4f30f-130">Configuration File Schema</span></span>](../index.md)
