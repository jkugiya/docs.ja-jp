---
description: '詳細情報: <trace> 要素'
title: <trace> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 470bc300911656a9c9951e52e3883ba5c8b01c59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750326"
---
# <a name="trace-element"></a><span data-ttu-id="09f44-103">\<trace> 要素</span><span class="sxs-lookup"><span data-stu-id="09f44-103">\<trace> Element</span></span>

<span data-ttu-id="09f44-104">トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。</span><span class="sxs-lookup"><span data-stu-id="09f44-104">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**  
  
## <a name="syntax"></a><span data-ttu-id="09f44-105">構文</span><span class="sxs-lookup"><span data-stu-id="09f44-105">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09f44-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="09f44-106">Attributes and Elements</span></span>  

 <span data-ttu-id="09f44-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="09f44-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09f44-108">属性</span><span class="sxs-lookup"><span data-stu-id="09f44-108">Attributes</span></span>  
  
|<span data-ttu-id="09f44-109">属性</span><span class="sxs-lookup"><span data-stu-id="09f44-109">Attribute</span></span>|<span data-ttu-id="09f44-110">説明</span><span class="sxs-lookup"><span data-stu-id="09f44-110">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="09f44-111">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="09f44-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="09f44-112">書き込み操作が行われるたびに、トレースリスナーが出力バッファーを自動的にフラッシュするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="09f44-112">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="09f44-113">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="09f44-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="09f44-114">インデントするスペースの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="09f44-114">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="09f44-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="09f44-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="09f44-116">グローバルロックを使用する必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="09f44-116">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="09f44-117">autoflush 属性</span><span class="sxs-lookup"><span data-stu-id="09f44-117">autoflush Attribute</span></span>  
  
|<span data-ttu-id="09f44-118">値</span><span class="sxs-lookup"><span data-stu-id="09f44-118">Value</span></span>|<span data-ttu-id="09f44-119">説明</span><span class="sxs-lookup"><span data-stu-id="09f44-119">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="09f44-120">では、出力バッファーは自動的にはフラッシュされません。</span><span class="sxs-lookup"><span data-stu-id="09f44-120">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="09f44-121">既定値です。</span><span class="sxs-lookup"><span data-stu-id="09f44-121">This is the default.</span></span>|  
|`true`|<span data-ttu-id="09f44-122">出力バッファーを自動的にフラッシュします。</span><span class="sxs-lookup"><span data-stu-id="09f44-122">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="09f44-123">useGlobalLock 属性</span><span class="sxs-lookup"><span data-stu-id="09f44-123">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="09f44-124">値</span><span class="sxs-lookup"><span data-stu-id="09f44-124">Value</span></span>|<span data-ttu-id="09f44-125">説明</span><span class="sxs-lookup"><span data-stu-id="09f44-125">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="09f44-126">リスナーがスレッドセーフである場合、はグローバルロックを使用しません。それ以外の場合、はグローバルロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="09f44-126">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="09f44-127">は、リスナーがスレッドセーフかどうかに関係なく、グローバルロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="09f44-127">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="09f44-128">既定値です。</span><span class="sxs-lookup"><span data-stu-id="09f44-128">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09f44-129">子要素</span><span class="sxs-lookup"><span data-stu-id="09f44-129">Child Elements</span></span>  
  
|<span data-ttu-id="09f44-130">要素</span><span class="sxs-lookup"><span data-stu-id="09f44-130">Element</span></span>|<span data-ttu-id="09f44-131">説明</span><span class="sxs-lookup"><span data-stu-id="09f44-131">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="09f44-132">メッセージを収集、格納、およびルーティングするリスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="09f44-132">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="09f44-133">親要素</span><span class="sxs-lookup"><span data-stu-id="09f44-133">Parent Elements</span></span>  
  
|<span data-ttu-id="09f44-134">要素</span><span class="sxs-lookup"><span data-stu-id="09f44-134">Element</span></span>|<span data-ttu-id="09f44-135">説明</span><span class="sxs-lookup"><span data-stu-id="09f44-135">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="09f44-136">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="09f44-136">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="09f44-137">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="09f44-137">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="09f44-138">例</span><span class="sxs-lookup"><span data-stu-id="09f44-138">Example</span></span>  

 <span data-ttu-id="09f44-139">次の例では、要素を使用して、リスナーをコレクションに追加する方法を示し `<trace>` `MyListener` `Listeners` ます。</span><span class="sxs-lookup"><span data-stu-id="09f44-139">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="09f44-140">`MyListener` という名前のファイルを作成 `MyListener.log` し、出力をファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="09f44-140">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="09f44-141">`useGlobalLock`属性がに設定されてい `false` ます。これにより、トレースリスナーがスレッドセーフである場合は、グローバルロックが使用されません。</span><span class="sxs-lookup"><span data-stu-id="09f44-141">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="09f44-142">`autoflush`属性はに設定されます `true` 。これにより、メソッドが呼び出されているかどうかに関係なく、トレースリスナーはファイルに書き込みを <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> 行います。</span><span class="sxs-lookup"><span data-stu-id="09f44-142">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="09f44-143">`indentsize`属性が 0 (ゼロ) に設定されている場合、メソッドの呼び出し時にリスナーによって0個の空白がインデントされ <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="09f44-143">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="09f44-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="09f44-144">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="09f44-145">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="09f44-145">Trace and Debug Settings Schema</span></span>](index.md)
