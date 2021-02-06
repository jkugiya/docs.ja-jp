---
description: の詳細については、「」を参照してください。 <add> <listeners><trace>
title: <add> のの <listeners> 要素 <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: ffc0823e0c0ce1dcd9d9f19853929496b3248177
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639784"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="dc10a-103">\<add> のの \<listeners> 要素 \<trace></span><span class="sxs-lookup"><span data-stu-id="dc10a-103">\<add> Element for \<listeners> for \<trace></span></span>

<span data-ttu-id="dc10a-104">リスナーを **リスナー** コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="dc10a-104">Adds a listener to the **Listeners** collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="dc10a-105">構文</span><span class="sxs-lookup"><span data-stu-id="dc10a-105">Syntax</span></span>  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc10a-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="dc10a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="dc10a-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="dc10a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc10a-108">属性</span><span class="sxs-lookup"><span data-stu-id="dc10a-108">Attributes</span></span>  
  
|<span data-ttu-id="dc10a-109">属性</span><span class="sxs-lookup"><span data-stu-id="dc10a-109">Attribute</span></span>|<span data-ttu-id="dc10a-110">説明</span><span class="sxs-lookup"><span data-stu-id="dc10a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dc10a-111">**type**</span><span class="sxs-lookup"><span data-stu-id="dc10a-111">**type**</span></span>|<span data-ttu-id="dc10a-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="dc10a-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="dc10a-113">リスナーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="dc10a-113">Specifies the type of the listener.</span></span> <span data-ttu-id="dc10a-114">[「完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」で指定した要件を満たす文字列を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc10a-114">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="dc10a-115">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="dc10a-115">**initializeData**</span></span>|<span data-ttu-id="dc10a-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="dc10a-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="dc10a-117">指定したクラスのコンストラクターに渡される文字列。</span><span class="sxs-lookup"><span data-stu-id="dc10a-117">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="dc10a-118">**name**</span><span class="sxs-lookup"><span data-stu-id="dc10a-118">**name**</span></span>|<span data-ttu-id="dc10a-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="dc10a-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="dc10a-120">リスナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="dc10a-120">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc10a-121">子要素</span><span class="sxs-lookup"><span data-stu-id="dc10a-121">Child Elements</span></span>  
  
|<span data-ttu-id="dc10a-122">要素</span><span class="sxs-lookup"><span data-stu-id="dc10a-122">Element</span></span>|<span data-ttu-id="dc10a-123">説明</span><span class="sxs-lookup"><span data-stu-id="dc10a-123">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="dc10a-124">トレースのコレクションのリスナーにフィルターを追加し `Listeners` ます。</span><span class="sxs-lookup"><span data-stu-id="dc10a-124">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc10a-125">親要素</span><span class="sxs-lookup"><span data-stu-id="dc10a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="dc10a-126">要素</span><span class="sxs-lookup"><span data-stu-id="dc10a-126">Element</span></span>|<span data-ttu-id="dc10a-127">説明</span><span class="sxs-lookup"><span data-stu-id="dc10a-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="dc10a-128">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="dc10a-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="dc10a-129">メッセージを収集、格納、およびルーティングするリスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="dc10a-129">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="dc10a-130">リスナーは、適切なターゲットにトレース出力を送信します。</span><span class="sxs-lookup"><span data-stu-id="dc10a-130">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="dc10a-131">ASP.NET 構成セクションのルート要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="dc10a-131">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="dc10a-132">トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。</span><span class="sxs-lookup"><span data-stu-id="dc10a-132">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc10a-133">解説</span><span class="sxs-lookup"><span data-stu-id="dc10a-133">Remarks</span></span>  

 <span data-ttu-id="dc10a-134"><xref:System.Diagnostics.Debug>クラスと <xref:System.Diagnostics.Trace> クラスは、同じ **Listeners** コレクションを共有します。</span><span class="sxs-lookup"><span data-stu-id="dc10a-134">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="dc10a-135">これらのクラスのいずれかのコレクションにリスナーオブジェクトを追加すると、他のクラスは同じリスナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="dc10a-135">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="dc10a-136">リスナークラスはから派生し <xref:System.Diagnostics.TraceListener> ます。</span><span class="sxs-lookup"><span data-stu-id="dc10a-136">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="dc10a-137">トレースリスナーの属性を指定しない場合 `name` 、 <xref:System.Diagnostics.TraceListener.Name%2A> トレースリスナーのは既定で空の文字列 ("") になります。</span><span class="sxs-lookup"><span data-stu-id="dc10a-137">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="dc10a-138">アプリケーションにリスナーが1つしかない場合は、名前を指定せずにリスナーを追加し、名前に空の文字列を指定することで削除できます。</span><span class="sxs-lookup"><span data-stu-id="dc10a-138">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="dc10a-139">ただし、アプリケーションに複数のリスナーがある場合は、各トレースリスナーに一意の名前を指定する必要があります。これにより、コレクションとコレクション内の個々のトレースリスナーを識別して管理でき <xref:System.Diagnostics.Debug.Listeners%2A> <xref:System.Diagnostics.Trace.Listeners%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="dc10a-139">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc10a-140">同じ種類の複数のトレースリスナーを同じ名前で追加すると、その型と名前のトレースリスナーは1つだけになり、コレクションに追加され `Listeners` ます。</span><span class="sxs-lookup"><span data-stu-id="dc10a-140">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="dc10a-141">ただし、プログラムを使用して複数の同じリスナーをコレクションに追加することはでき `Listeners` ます。</span><span class="sxs-lookup"><span data-stu-id="dc10a-141">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="dc10a-142">**Initializedata** 属性の値は、作成するリスナーの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="dc10a-142">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="dc10a-143">すべてのトレースリスナーで **Initializedata** を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="dc10a-143">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc10a-144">属性を使用すると、 `initializeData` "initializeData" 属性が宣言されていないことを示すコンパイラの警告が表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="dc10a-144">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="dc10a-145">この警告は、属性を認識しない抽象基本クラスに対して構成設定が検証されるために発生し <xref:System.Diagnostics.TraceListener> `initializeData` ます。</span><span class="sxs-lookup"><span data-stu-id="dc10a-145">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="dc10a-146">通常、パラメーターを受け取るコンストラクターを持つトレースリスナーの実装では、この警告を無視できます。</span><span class="sxs-lookup"><span data-stu-id="dc10a-146">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="dc10a-147">次の表に、.NET Framework に含まれるトレースリスナーと、 **Initializedata** 属性の値について説明します。</span><span class="sxs-lookup"><span data-stu-id="dc10a-147">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="dc10a-148">トレースリスナークラス</span><span class="sxs-lookup"><span data-stu-id="dc10a-148">Trace listener class</span></span>|<span data-ttu-id="dc10a-149">initializeData 属性値</span><span class="sxs-lookup"><span data-stu-id="dc10a-149">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="dc10a-150">`useErrorStream`コンストラクターの値 <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="dc10a-150">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="dc10a-151">属性を `initializeData` "" に設定し、 `true` トレース出力とデバッグ出力をに設定し <xref:System.Console.Error%2A?displayProperty=nameWithType> ます。書き込み先となる " `false` " <xref:System.Console.Out%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="dc10a-151">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="dc10a-152"><xref:System.Diagnostics.DelimitedListTraceListener> が出力を書き込むファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="dc10a-152">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="dc10a-153">既存のイベントログソースの名前。</span><span class="sxs-lookup"><span data-stu-id="dc10a-153">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="dc10a-154">が書き込み先となるファイルの名前 <xref:System.Diagnostics.EventSchemaTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="dc10a-154">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="dc10a-155">が書き込み先となるファイルの名前 <xref:System.Diagnostics.TextWriterTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="dc10a-155">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="dc10a-156">が書き込み先となるファイルの名前 <xref:System.Diagnostics.XmlWriterTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="dc10a-156">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dc10a-157">例</span><span class="sxs-lookup"><span data-stu-id="dc10a-157">Example</span></span>  

 <span data-ttu-id="dc10a-158">次の例は、要素を使用して **\<add>** リスナー `MyListener` と `MyEventListener` **リスナー** コレクションに追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="dc10a-158">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="dc10a-159">`MyListener` という名前のファイルを作成し、その `MyListener.log` 出力をファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="dc10a-159">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="dc10a-160">`MyEventListener` イベントログにエントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="dc10a-160">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc10a-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc10a-161">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="dc10a-162">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="dc10a-162">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="dc10a-163">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="dc10a-163">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
