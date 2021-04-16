---
description: '詳細情報: <trace> の <listeners> 要素'
title: <trace> の <listeners> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: 25f6d4b49eeb57b25b4afbbdfdba484d6d7eea3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639628"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="4df83-103">\<trace> の \<listeners> 要素</span><span class="sxs-lookup"><span data-stu-id="4df83-103">\<listeners> Element for \<trace></span></span>

<span data-ttu-id="4df83-104">メッセージを収集、格納、およびルーティングするリスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="4df83-104">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="4df83-105">リスナーにより、トレース出力が適切な場所に送られます。</span><span class="sxs-lookup"><span data-stu-id="4df83-105">Listeners direct the tracing output to an appropriate target.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**

## <a name="syntax"></a><span data-ttu-id="4df83-106">構文</span><span class="sxs-lookup"><span data-stu-id="4df83-106">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4df83-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="4df83-107">Attributes and Elements</span></span>  

 <span data-ttu-id="4df83-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="4df83-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4df83-109">属性</span><span class="sxs-lookup"><span data-stu-id="4df83-109">Attributes</span></span>  

 <span data-ttu-id="4df83-110">なし。</span><span class="sxs-lookup"><span data-stu-id="4df83-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4df83-111">子要素</span><span class="sxs-lookup"><span data-stu-id="4df83-111">Child Elements</span></span>  
  
|<span data-ttu-id="4df83-112">要素</span><span class="sxs-lookup"><span data-stu-id="4df83-112">Element</span></span>|<span data-ttu-id="4df83-113">説明</span><span class="sxs-lookup"><span data-stu-id="4df83-113">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="4df83-114">`Listeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="4df83-114">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="4df83-115">トレースの `Listeners` コレクションを削除します。</span><span class="sxs-lookup"><span data-stu-id="4df83-115">Clears the `Listeners` collection for trace.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="4df83-116">`Listeners` コレクションからリスナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="4df83-116">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4df83-117">親要素</span><span class="sxs-lookup"><span data-stu-id="4df83-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4df83-118">要素</span><span class="sxs-lookup"><span data-stu-id="4df83-118">Element</span></span>|<span data-ttu-id="4df83-119">説明</span><span class="sxs-lookup"><span data-stu-id="4df83-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4df83-120">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="4df83-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4df83-121">ASP.NET 構成セクションのルート要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="4df83-121">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="4df83-122">トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。</span><span class="sxs-lookup"><span data-stu-id="4df83-122">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4df83-123">解説</span><span class="sxs-lookup"><span data-stu-id="4df83-123">Remarks</span></span>  

 <span data-ttu-id="4df83-124"><xref:System.Diagnostics.Debug> クラスと <xref:System.Diagnostics.Trace> クラスでは、同じ **Listeners** コレクションが共有されます。</span><span class="sxs-lookup"><span data-stu-id="4df83-124">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="4df83-125">これらのクラスのいずれかのコレクションにリスナー オブジェクトを追加すると、もう一方のクラスでも同じリスナーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4df83-125">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="4df83-126">.NET Framework に付属しているリスナー クラスは、<xref:System.Diagnostics.TraceListener> クラスから派生したものです。</span><span class="sxs-lookup"><span data-stu-id="4df83-126">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="4df83-127">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="4df83-127">Configuration File</span></span>  

 <span data-ttu-id="4df83-128">この要素は、マシン構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="4df83-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4df83-129">例</span><span class="sxs-lookup"><span data-stu-id="4df83-129">Example</span></span>  

 <span data-ttu-id="4df83-130">次の例は、 **\<listeners>** 要素を使用して、リスナー `MyListener` および `MyEventListener` を **Listeners** コレクションに追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4df83-130">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="4df83-131">`MyListener` では、`MyListener.log` というファイルを作成し、そのファイルに出力を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="4df83-131">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="4df83-132">`MyEventListener` では、イベント ログにエントリを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="4df83-132">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"
          type="System.Diagnostics.TextWriterTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4df83-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="4df83-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="4df83-134">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="4df83-134">Trace and Debug Settings Schema</span></span>](index.md)
