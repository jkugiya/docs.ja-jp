---
description: '詳細情報: <source> の <listeners> の <add> 要素'
title: <source> の <listeners> の <add> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: cb2145738b81574397a8de13f68d0d4e572f20cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639836"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="36635-103">\<source> の \<listeners> の \<add> 要素</span><span class="sxs-lookup"><span data-stu-id="36635-103">\<add> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="36635-104">トレース ソースの `Listeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="36635-104">Adds a listener to the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="36635-105">構文</span><span class="sxs-lookup"><span data-stu-id="36635-105">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36635-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="36635-106">Attributes and Elements</span></span>  

 <span data-ttu-id="36635-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="36635-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36635-108">属性</span><span class="sxs-lookup"><span data-stu-id="36635-108">Attributes</span></span>  
  
|<span data-ttu-id="36635-109">属性</span><span class="sxs-lookup"><span data-stu-id="36635-109">Attribute</span></span>|<span data-ttu-id="36635-110">説明</span><span class="sxs-lookup"><span data-stu-id="36635-110">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="36635-111">必須属性です。ただし、`sharedListeners` コレクション内のリスナーを参照する場合は、名前だけで参照することができます (「[例](#example)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="36635-111">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="36635-112">リスナーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="36635-112">Specifies the type of the listener.</span></span> <span data-ttu-id="36635-113">「[完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」で指定された要件を満たす文字列を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36635-113">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="36635-114">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="36635-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="36635-115">指定されたクラスのコンストラクターに渡される文字列。</span><span class="sxs-lookup"><span data-stu-id="36635-115">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="36635-116">クラスに文字列を受け取るコンストラクターがない場合は、<xref:System.Configuration.ConfigurationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="36635-116">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="36635-117">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="36635-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="36635-118">リスナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="36635-118">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="36635-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="36635-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="36635-120">トレース リスナーの <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> プロパティ値を指定します。</span><span class="sxs-lookup"><span data-stu-id="36635-120">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="36635-121">[カスタム属性]</span><span class="sxs-lookup"><span data-stu-id="36635-121">[custom attributes]</span></span>|<span data-ttu-id="36635-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="36635-122">Optional attributes.</span></span><br /><br /> <span data-ttu-id="36635-123">リスナーの <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> メソッドによって識別される、リスナー固有の属性の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="36635-123">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="36635-124"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> は、<xref:System.Diagnostics.DelimitedListTraceListener> クラスに固有の追加属性の例です。</span><span class="sxs-lookup"><span data-stu-id="36635-124"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36635-125">子要素</span><span class="sxs-lookup"><span data-stu-id="36635-125">Child Elements</span></span>  
  
|<span data-ttu-id="36635-126">要素</span><span class="sxs-lookup"><span data-stu-id="36635-126">Element</span></span>|<span data-ttu-id="36635-127">説明</span><span class="sxs-lookup"><span data-stu-id="36635-127">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="36635-128">トレース ソースの `Listeners` コレクション内のリスナーにフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="36635-128">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36635-129">親要素</span><span class="sxs-lookup"><span data-stu-id="36635-129">Parent Elements</span></span>  
  
|<span data-ttu-id="36635-130">要素</span><span class="sxs-lookup"><span data-stu-id="36635-130">Element</span></span>|<span data-ttu-id="36635-131">説明</span><span class="sxs-lookup"><span data-stu-id="36635-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="36635-132">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="36635-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="36635-133">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="36635-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="36635-134">トレース メッセージを開始するトレース ソースを保持します。</span><span class="sxs-lookup"><span data-stu-id="36635-134">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="36635-135">トレース メッセージを開始するトレース ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="36635-135">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="36635-136">メッセージを収集、格納、およびルーティングするリスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="36635-136">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36635-137">解説</span><span class="sxs-lookup"><span data-stu-id="36635-137">Remarks</span></span>  

 <span data-ttu-id="36635-138">.NET Framework に付属しているリスナー クラスは、<xref:System.Diagnostics.TraceListener> クラスから派生したものです。</span><span class="sxs-lookup"><span data-stu-id="36635-138">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="36635-139">トレース リスナーの `name` 属性を指定しなかった場合、トレース リスナーの <xref:System.Diagnostics.TraceListener.Name%2A> プロパティは既定で空の文字列 ("") になります。</span><span class="sxs-lookup"><span data-stu-id="36635-139">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="36635-140">アプリケーションにリスナーが 1 つしかない場合は、名前を指定せずにリスナーを追加でき、名前に空の文字列を指定することでリスナーを削除できます。</span><span class="sxs-lookup"><span data-stu-id="36635-140">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="36635-141">ただし、アプリケーションに複数のリスナーがある場合は、各トレース リスナーに一意の名前を指定する必要があります。これにより、<xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> コレクション内の個々のトレース リスナーを識別し、管理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="36635-141">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36635-142">同じ種類の複数のトレース リスナーを同じ名前で追加すると、その種類と名前のトレース リスナーは 1 つだけになり、`Listeners` コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="36635-142">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="36635-143">ただし、複数の同じリスナーをプログラムによって `Listeners` コレクションに追加することはできます。</span><span class="sxs-lookup"><span data-stu-id="36635-143">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="36635-144">`initializeData` 属性の値は、作成するリスナーの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="36635-144">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="36635-145">すべてのトレース リスナーで `initializeData` を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="36635-145">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36635-146">`initializeData` 属性を使用すると、"'initializeData' 属性が宣言されていません" というコンパイラ警告が表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="36635-146">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="36635-147">この警告が表示されるのは、`initializeData` 属性を認識しない抽象基本クラス <xref:System.Diagnostics.TraceListener> に対して構成設定が検証されるためです。</span><span class="sxs-lookup"><span data-stu-id="36635-147">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="36635-148">通常、パラメーターを受け取るコンストラクターを持つトレース リスナーの実装では、この警告を無視できます。</span><span class="sxs-lookup"><span data-stu-id="36635-148">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="36635-149">次の表で、.NET Framework に含まれているトレース リスナーを示し、それらの `initializeData` 属性の値について説明します。</span><span class="sxs-lookup"><span data-stu-id="36635-149">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="36635-150">トレース リスナー クラス</span><span class="sxs-lookup"><span data-stu-id="36635-150">Trace listener class</span></span>|<span data-ttu-id="36635-151">initializeData 属性値</span><span class="sxs-lookup"><span data-stu-id="36635-151">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="36635-152"><xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> コンストラクターの `useErrorStream` 値。</span><span class="sxs-lookup"><span data-stu-id="36635-152">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="36635-153">トレースおよびデバッグ出力を標準エラー ストリームに書き込むには、`initializeData` 属性を "`true`" に設定します。標準出力ストリームに書き込むには、"`false`" に設定します。</span><span class="sxs-lookup"><span data-stu-id="36635-153">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="36635-154"><xref:System.Diagnostics.DelimitedListTraceListener> が出力を書き込むファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="36635-154">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="36635-155">既存のイベント ログ ソースの名前。</span><span class="sxs-lookup"><span data-stu-id="36635-155">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="36635-156"><xref:System.Diagnostics.EventSchemaTraceListener> による書き込み先のファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="36635-156">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="36635-157"><xref:System.Diagnostics.TextWriterTraceListener> による書き込み先のファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="36635-157">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="36635-158"><xref:System.Diagnostics.XmlWriterTraceListener> による書き込み先のファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="36635-158">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="36635-159">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="36635-159">Configuration File</span></span>  

 <span data-ttu-id="36635-160">この要素は、マシン構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="36635-160">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36635-161">例</span><span class="sxs-lookup"><span data-stu-id="36635-161">Example</span></span>  

 <span data-ttu-id="36635-162">次の例は、`<add>` 要素を使用して、リスナー `console` および `textListener` を トレース ソース `TraceSourceApp` の `Listeners` コレクションに追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="36635-162">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="36635-163">`textListener` リスナーにより、トレース出力がファイル myListener.log に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="36635-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="36635-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="36635-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="36635-165">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="36635-165">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="36635-166">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="36635-166">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
