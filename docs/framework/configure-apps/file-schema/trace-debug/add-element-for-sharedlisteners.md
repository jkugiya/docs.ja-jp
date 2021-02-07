---
description: '詳細情報: <add> の要素 <sharedListeners>'
title: <sharedListeners> の <add> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: df3348fa0cbb357b2ceeb5d9db940a1ae3ae102c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726079"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="1a6c5-103">\<sharedListeners> の \<add> 要素</span><span class="sxs-lookup"><span data-stu-id="1a6c5-103">\<add> Element for \<sharedListeners></span></span>

<span data-ttu-id="1a6c5-104">`sharedListeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-104">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="1a6c5-105">`sharedListeners`[\<source>](source-element.md)またはが参照できるリスナーのコレクションです [\<trace>](trace-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-105">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="1a6c5-106">既定では、コレクション内のリスナー `sharedListeners` はコレクション内に配置されません `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-106">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="1a6c5-107">これらは、またはに名前で追加する必要があり [\<source>](source-element.md) [\<trace>](trace-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-107">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="1a6c5-108">実行時にコードでコレクション内のリスナーを取得することはできません `sharedListeners` 。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-108">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="1a6c5-109">構文</span><span class="sxs-lookup"><span data-stu-id="1a6c5-109">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a6c5-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1a6c5-110">Attributes and Elements</span></span>  

 <span data-ttu-id="1a6c5-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a6c5-112">属性</span><span class="sxs-lookup"><span data-stu-id="1a6c5-112">Attributes</span></span>  
  
|<span data-ttu-id="1a6c5-113">属性</span><span class="sxs-lookup"><span data-stu-id="1a6c5-113">Attribute</span></span>|<span data-ttu-id="1a6c5-114">説明</span><span class="sxs-lookup"><span data-stu-id="1a6c5-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="1a6c5-115">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="1a6c5-116">共有リスナーをコレクションに追加するために使用されるリスナーの名前を指定し `Listeners` ます。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-116">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="1a6c5-117">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="1a6c5-118">リスナーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-118">Specifies the type of the listener.</span></span> <span data-ttu-id="1a6c5-119">[「完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」で指定した要件を満たす文字列を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-119">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="1a6c5-120">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="1a6c5-121">指定したクラスのコンストラクターに渡される文字列。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-121">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="1a6c5-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-122">Optional attribute.</span></span><br/><br/><span data-ttu-id="1a6c5-123"><xref:System.Diagnostics.TraceOptions>トレース出力に書き込まれるデータを示す1つ以上の列挙メンバーの文字列形式。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-123">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="1a6c5-124">複数の項目は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-124">Multiple items are separated by commas.</span></span> <span data-ttu-id="1a6c5-125">既定値は "None" です。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-125">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1a6c5-126">子要素</span><span class="sxs-lookup"><span data-stu-id="1a6c5-126">Child Elements</span></span>  
  
|<span data-ttu-id="1a6c5-127">要素</span><span class="sxs-lookup"><span data-stu-id="1a6c5-127">Element</span></span>|<span data-ttu-id="1a6c5-128">説明</span><span class="sxs-lookup"><span data-stu-id="1a6c5-128">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="1a6c5-129">`sharedListeners` コレクションのリスナーにフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-129">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1a6c5-130">親要素</span><span class="sxs-lookup"><span data-stu-id="1a6c5-130">Parent Elements</span></span>  
  
|<span data-ttu-id="1a6c5-131">要素</span><span class="sxs-lookup"><span data-stu-id="1a6c5-131">Element</span></span>|<span data-ttu-id="1a6c5-132">説明</span><span class="sxs-lookup"><span data-stu-id="1a6c5-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1a6c5-133">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="1a6c5-134">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-134">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="1a6c5-135">任意のソースまたはトレース要素が参照できるリスナーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-135">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a6c5-136">解説</span><span class="sxs-lookup"><span data-stu-id="1a6c5-136">Remarks</span></span>  

 <span data-ttu-id="1a6c5-137">.NET Framework に付属しているリスナークラスは、クラスから派生し <xref:System.Diagnostics.TraceListener> ます。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-137">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="1a6c5-138">属性の値 `name` は、 `Listeners` トレースまたはトレースソースのコレクションに共有リスナーを追加するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-138">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="1a6c5-139">属性の値は、 `initializeData` 作成するリスナーの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-139">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="1a6c5-140">すべてのトレースリスナーでを指定する必要はありません `initializeData` 。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-140">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a6c5-141">属性を使用すると、 `initializeData` "initializeData" 属性が宣言されていないことを示すコンパイラの警告が表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-141">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="1a6c5-142">この警告は、属性を認識しない抽象基本クラスに対して構成設定が検証されるために発生し <xref:System.Diagnostics.TraceListener> `initializeData` ます。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-142">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="1a6c5-143">通常、パラメーターを受け取るコンストラクターを持つトレースリスナーの実装では、この警告を無視できます。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-143">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="1a6c5-144">次の表に、.NET Framework に含まれているトレースリスナーとその属性の値を示し `initializeData` ます。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-144">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="1a6c5-145">トレースリスナークラス</span><span class="sxs-lookup"><span data-stu-id="1a6c5-145">Trace listener class</span></span>|<span data-ttu-id="1a6c5-146">initializeData 属性値</span><span class="sxs-lookup"><span data-stu-id="1a6c5-146">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="1a6c5-147">`useErrorStream`コンストラクターの値 <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-147">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="1a6c5-148">`initializeData`トレース出力およびデバッグ出力を標準エラーストリームに書き込むには、属性を "" に設定します `true` 。 `false` 標準出力ストリームに書き込むには、"" に設定します。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-148">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="1a6c5-149"><xref:System.Diagnostics.DelimitedListTraceListener> が出力を書き込むファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-149">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="1a6c5-150">既存のイベント ログ ソースの名前。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-150">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="1a6c5-151">が書き込み先となるファイルの名前 <xref:System.Diagnostics.EventSchemaTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-151">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="1a6c5-152">が書き込み先となるファイルの名前 <xref:System.Diagnostics.TextWriterTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-152">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="1a6c5-153">が書き込み先となるファイルの名前 <xref:System.Diagnostics.XmlWriterTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-153">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="1a6c5-154">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="1a6c5-154">Configuration File</span></span>  

 <span data-ttu-id="1a6c5-155">この要素は、マシン構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-155">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a6c5-156">例</span><span class="sxs-lookup"><span data-stu-id="1a6c5-156">Example</span></span>  

 <span data-ttu-id="1a6c5-157">次の例は、要素を使用してをコレクションに追加する方法を示して `<add>` <xref:System.Diagnostics.TextWriterTraceListener> `textListener` `sharedListeners` います。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-157">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="1a6c5-158">`textListener` は、トレースソースのコレクションに名前によって追加され `Listeners` `TraceSourceApp` ます。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-158">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="1a6c5-159">リスナーは、 `textListener` トレース出力をファイル myListener .log に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="1a6c5-159">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1a6c5-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a6c5-160">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="1a6c5-161">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="1a6c5-161">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1a6c5-162">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="1a6c5-162">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
