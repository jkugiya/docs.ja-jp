---
description: 詳細については、「<> 要素」を参照してください。
title: <diagnostics> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: ac5b1feaa6c8e7ab25a5210999040835322ac7a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750456"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="266b8-103">\<system.diagnostics> 要素</span><span class="sxs-lookup"><span data-stu-id="266b8-103">\<system.diagnostics> Element</span></span>

<span data-ttu-id="266b8-104">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="266b8-104">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="266b8-105">構文</span><span class="sxs-lookup"><span data-stu-id="266b8-105">Syntax</span></span>  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="266b8-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="266b8-106">Attributes and Elements</span></span>  

 <span data-ttu-id="266b8-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="266b8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="266b8-108">属性</span><span class="sxs-lookup"><span data-stu-id="266b8-108">Attributes</span></span>  

 <span data-ttu-id="266b8-109">なし。</span><span class="sxs-lookup"><span data-stu-id="266b8-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="266b8-110">子要素</span><span class="sxs-lookup"><span data-stu-id="266b8-110">Child Elements</span></span>  
  
|<span data-ttu-id="266b8-111">要素</span><span class="sxs-lookup"><span data-stu-id="266b8-111">Element</span></span>|<span data-ttu-id="266b8-112">説明</span><span class="sxs-lookup"><span data-stu-id="266b8-112">Description</span></span>|  
|-------------|-----------------|  
|[\<assert>](assert-element.md)|<span data-ttu-id="266b8-113"><xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> メソッドの呼び出し時にメッセージ ボックスを表示するかどうかを指定し、メッセージの書き込み先のファイルの名前も指定します。</span><span class="sxs-lookup"><span data-stu-id="266b8-113">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[\<performanceCounters>](performancecounters-element.md)|<span data-ttu-id="266b8-114">パフォーマンス カウンターが共有するグローバル メモリのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="266b8-114">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[\<sharedListeners>](sharedlisteners-element.md)|<span data-ttu-id="266b8-115">任意の source 要素または trace 要素が参照できるリスナーを含みます。</span><span class="sxs-lookup"><span data-stu-id="266b8-115">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="266b8-116">共有リスナーとして識別されるリスナーは、名前を指定してソースまたはトレースに追加できます。</span><span class="sxs-lookup"><span data-stu-id="266b8-116">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[\<sources>](sources-element.md)|<span data-ttu-id="266b8-117">トレースメッセージを開始するトレースソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="266b8-117">Specifies trace sources that initiate tracing messages.</span></span>|  
|[\<switches>](switches-element.md)|<span data-ttu-id="266b8-118">トレーススイッチと、トレーススイッチが設定されているレベルを格納します。</span><span class="sxs-lookup"><span data-stu-id="266b8-118">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[\<trace>](trace-element.md)|<span data-ttu-id="266b8-119">トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。</span><span class="sxs-lookup"><span data-stu-id="266b8-119">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="266b8-120">親要素</span><span class="sxs-lookup"><span data-stu-id="266b8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="266b8-121">要素</span><span class="sxs-lookup"><span data-stu-id="266b8-121">Element</span></span>|<span data-ttu-id="266b8-122">説明</span><span class="sxs-lookup"><span data-stu-id="266b8-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="266b8-123">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="266b8-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="266b8-124">例</span><span class="sxs-lookup"><span data-stu-id="266b8-124">Example</span></span>  

 <span data-ttu-id="266b8-125">次の例は、トレーススイッチとトレースリスナーを要素内に埋め込む方法を示して **\<system.diagnostics>** います。</span><span class="sxs-lookup"><span data-stu-id="266b8-125">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="266b8-126">`General`トレーススイッチがレベルに設定されてい <xref:System.Diagnostics.TraceLevel> ます。</span><span class="sxs-lookup"><span data-stu-id="266b8-126">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="266b8-127">トレースリスナーは、と `myListener` いうファイルを作成 `MyListener.log` し、ファイルに出力を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="266b8-127">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="266b8-128">.NET Framework バージョン 2.0 では、スイッチの値を指定するためにテキストを使用できます。</span><span class="sxs-lookup"><span data-stu-id="266b8-128">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="266b8-129">たとえば、に対してを指定したり、の `true` <xref:System.Diagnostics.BooleanSwitch> ような列挙値を表すテキストを使用したりでき `Error` <xref:System.Diagnostics.TraceSwitch> ます。</span><span class="sxs-lookup"><span data-stu-id="266b8-129">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="266b8-130">`<add name="myTraceSwitch" value="Error" />` という行は、`<add name="myTraceSwitch" value="1" />` と同じです。</span><span class="sxs-lookup"><span data-stu-id="266b8-130">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="266b8-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="266b8-131">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="266b8-132">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="266b8-132">Trace and Debug Settings Schema</span></span>](index.md)
