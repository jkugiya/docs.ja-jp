---
description: '詳細情報: <trace> の <listeners> の <add> 要素'
title: <trace> の <listeners> の <add> 要素
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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639784"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="d380d-103">\<trace> の \<listeners> の \<add> 要素</span><span class="sxs-lookup"><span data-stu-id="d380d-103">\<add> Element for \<listeners> for \<trace></span></span>

<span data-ttu-id="d380d-104">**Listeners** コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="d380d-104">Adds a listener to the **Listeners** collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="d380d-105">構文</span><span class="sxs-lookup"><span data-stu-id="d380d-105">Syntax</span></span>  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d380d-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d380d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d380d-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d380d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d380d-108">属性</span><span class="sxs-lookup"><span data-stu-id="d380d-108">Attributes</span></span>  
  
|<span data-ttu-id="d380d-109">属性</span><span class="sxs-lookup"><span data-stu-id="d380d-109">Attribute</span></span>|<span data-ttu-id="d380d-110">説明</span><span class="sxs-lookup"><span data-stu-id="d380d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d380d-111">**type**</span><span class="sxs-lookup"><span data-stu-id="d380d-111">**type**</span></span>|<span data-ttu-id="d380d-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="d380d-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="d380d-113">リスナーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="d380d-113">Specifies the type of the listener.</span></span> <span data-ttu-id="d380d-114">「[完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」で指定された要件を満たす文字列を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d380d-114">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="d380d-115">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="d380d-115">**initializeData**</span></span>|<span data-ttu-id="d380d-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="d380d-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d380d-117">指定されたクラスのコンストラクターに渡される文字列。</span><span class="sxs-lookup"><span data-stu-id="d380d-117">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="d380d-118">**name**</span><span class="sxs-lookup"><span data-stu-id="d380d-118">**name**</span></span>|<span data-ttu-id="d380d-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="d380d-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d380d-120">リスナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d380d-120">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d380d-121">子要素</span><span class="sxs-lookup"><span data-stu-id="d380d-121">Child Elements</span></span>  
  
|<span data-ttu-id="d380d-122">要素</span><span class="sxs-lookup"><span data-stu-id="d380d-122">Element</span></span>|<span data-ttu-id="d380d-123">説明</span><span class="sxs-lookup"><span data-stu-id="d380d-123">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="d380d-124">トレースの `Listeners` コレクションのリスナーにフィルターに追加します。</span><span class="sxs-lookup"><span data-stu-id="d380d-124">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d380d-125">親要素</span><span class="sxs-lookup"><span data-stu-id="d380d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="d380d-126">要素</span><span class="sxs-lookup"><span data-stu-id="d380d-126">Element</span></span>|<span data-ttu-id="d380d-127">説明</span><span class="sxs-lookup"><span data-stu-id="d380d-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d380d-128">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="d380d-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="d380d-129">メッセージを収集、格納、およびルーティングするリスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="d380d-129">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="d380d-130">リスナーにより、トレース出力が適切な場所に送られます。</span><span class="sxs-lookup"><span data-stu-id="d380d-130">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d380d-131">ASP.NET 構成セクションのルート要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="d380d-131">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="d380d-132">トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。</span><span class="sxs-lookup"><span data-stu-id="d380d-132">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d380d-133">解説</span><span class="sxs-lookup"><span data-stu-id="d380d-133">Remarks</span></span>  

 <span data-ttu-id="d380d-134"><xref:System.Diagnostics.Debug> クラスと <xref:System.Diagnostics.Trace> クラスでは、同じ **Listeners** コレクションが共有されます。</span><span class="sxs-lookup"><span data-stu-id="d380d-134">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="d380d-135">これらのクラスのいずれかのコレクションにリスナー オブジェクトを追加すると、もう一方のクラスでも同じリスナーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d380d-135">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="d380d-136">リスナー クラスは <xref:System.Diagnostics.TraceListener> から派生します。</span><span class="sxs-lookup"><span data-stu-id="d380d-136">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="d380d-137">トレース リスナーの `name` 属性を指定しなかった場合、トレース リスナーの <xref:System.Diagnostics.TraceListener.Name%2A> は既定で空の文字列 ("") になります。</span><span class="sxs-lookup"><span data-stu-id="d380d-137">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="d380d-138">アプリケーションにリスナーが 1 つしかない場合は、名前を指定せずにリスナーを追加でき、名前に空の文字列を指定することでリスナーを削除できます。</span><span class="sxs-lookup"><span data-stu-id="d380d-138">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="d380d-139">ただし、アプリケーションに複数のリスナーがある場合は、各トレース リスナーに一意の名前を指定する必要があります。これにより、<xref:System.Diagnostics.Debug.Listeners%2A> コレクションと <xref:System.Diagnostics.Trace.Listeners%2A> コレクション内の個々のトレース リスナーを識別し、管理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d380d-139">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d380d-140">同じ種類の複数のトレース リスナーを同じ名前で追加すると、その種類と名前のトレース リスナーは 1 つだけになり、`Listeners` コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="d380d-140">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="d380d-141">ただし、複数の同じリスナーをプログラムによって `Listeners` コレクションに追加することはできます。</span><span class="sxs-lookup"><span data-stu-id="d380d-141">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="d380d-142">**initializeData** 属性の値は、作成するリスナーの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="d380d-142">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="d380d-143">すべてのトレース リスナーで **initializeData** を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d380d-143">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d380d-144">`initializeData` 属性を使用すると、"'initializeData' 属性が宣言されていません" というコンパイラ警告が表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="d380d-144">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="d380d-145">この警告が表示されるのは、`initializeData` 属性を認識しない抽象基本クラス <xref:System.Diagnostics.TraceListener> に対して構成設定が検証されるためです。</span><span class="sxs-lookup"><span data-stu-id="d380d-145">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="d380d-146">通常、パラメーターを受け取るコンストラクターを持つトレース リスナーの実装では、この警告を無視できます。</span><span class="sxs-lookup"><span data-stu-id="d380d-146">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="d380d-147">次の表で、.NET Framework に含まれているトレース リスナーを示し、それらの **initializeData** 属性の値について説明します。</span><span class="sxs-lookup"><span data-stu-id="d380d-147">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="d380d-148">トレース リスナー クラス</span><span class="sxs-lookup"><span data-stu-id="d380d-148">Trace listener class</span></span>|<span data-ttu-id="d380d-149">initializeData 属性値</span><span class="sxs-lookup"><span data-stu-id="d380d-149">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="d380d-150"><xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> コンストラクターの `useErrorStream` 値。</span><span class="sxs-lookup"><span data-stu-id="d380d-150">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="d380d-151">トレースおよびデバッグ出力を <xref:System.Console.Error%2A?displayProperty=nameWithType> に書き込むには、`initializeData` 属性を "`true`" に設定します。<xref:System.Console.Out%2A?displayProperty=nameWithType> に書き込むには、"`false`" に設定します。</span><span class="sxs-lookup"><span data-stu-id="d380d-151">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="d380d-152"><xref:System.Diagnostics.DelimitedListTraceListener> が出力を書き込むファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="d380d-152">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="d380d-153">既存のイベント ログ ソースの名前。</span><span class="sxs-lookup"><span data-stu-id="d380d-153">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="d380d-154"><xref:System.Diagnostics.EventSchemaTraceListener> による書き込み先のファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="d380d-154">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="d380d-155"><xref:System.Diagnostics.TextWriterTraceListener> による書き込み先のファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="d380d-155">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="d380d-156"><xref:System.Diagnostics.XmlWriterTraceListener> による書き込み先のファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="d380d-156">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d380d-157">例</span><span class="sxs-lookup"><span data-stu-id="d380d-157">Example</span></span>  

 <span data-ttu-id="d380d-158">次の例は、 **\<add>** 要素を使用して、リスナー `MyListener` および `MyEventListener` を **Listeners** コレクションに追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d380d-158">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="d380d-159">`MyListener` では、`MyListener.log` というファイルを作成し、そのファイルに出力を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="d380d-159">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="d380d-160">`MyEventListener` では、イベント ログにエントリを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="d380d-160">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d380d-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="d380d-161">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="d380d-162">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="d380d-162">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d380d-163">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="d380d-163">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
