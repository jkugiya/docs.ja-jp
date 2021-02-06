---
description: の詳細については、「」を参照してください。 <clear> <listeners><source>
title: <clear> のの <listeners> 要素 <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 731c23c73b6d149bd37672e91eca1d70431b2789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639706"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="7bb51-103">\<clear> のの \<listeners> 要素 \<source></span><span class="sxs-lookup"><span data-stu-id="7bb51-103">\<clear> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="7bb51-104">トレース ソースの `Listeners` コレクションを消去します。</span><span class="sxs-lookup"><span data-stu-id="7bb51-104">Clears the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="7bb51-105">構文</span><span class="sxs-lookup"><span data-stu-id="7bb51-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bb51-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7bb51-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7bb51-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7bb51-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bb51-108">属性</span><span class="sxs-lookup"><span data-stu-id="7bb51-108">Attributes</span></span>  

 <span data-ttu-id="7bb51-109">なし。</span><span class="sxs-lookup"><span data-stu-id="7bb51-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7bb51-110">子要素</span><span class="sxs-lookup"><span data-stu-id="7bb51-110">Child Elements</span></span>  

 <span data-ttu-id="7bb51-111">なし。</span><span class="sxs-lookup"><span data-stu-id="7bb51-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bb51-112">親要素</span><span class="sxs-lookup"><span data-stu-id="7bb51-112">Parent Elements</span></span>  
  
|<span data-ttu-id="7bb51-113">要素</span><span class="sxs-lookup"><span data-stu-id="7bb51-113">Element</span></span>|<span data-ttu-id="7bb51-114">説明</span><span class="sxs-lookup"><span data-stu-id="7bb51-114">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7bb51-115">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="7bb51-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="7bb51-116">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7bb51-116">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="7bb51-117">トレース メッセージを開始するトレース ソースを保持します。</span><span class="sxs-lookup"><span data-stu-id="7bb51-117">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="7bb51-118">トレース メッセージを開始するトレース ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="7bb51-118">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="7bb51-119">メッセージを収集、格納、およびルーティングするリスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="7bb51-119">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bb51-120">解説</span><span class="sxs-lookup"><span data-stu-id="7bb51-120">Remarks</span></span>  

 <span data-ttu-id="7bb51-121">`<clear>`要素は、を含む、 `Listeners` トレースソースのコレクションからすべてのリスナーを削除し <xref:System.Diagnostics.DefaultTraceListener> ます。</span><span class="sxs-lookup"><span data-stu-id="7bb51-121">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="7bb51-122">要素を使用 `<clear>` して、 `<add>` コレクション内に他のアクティブなリスナーが存在しないことを特定することができます。</span><span class="sxs-lookup"><span data-stu-id="7bb51-122">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="7bb51-123">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="7bb51-123">Configuration File</span></span>  

 <span data-ttu-id="7bb51-124">この要素は、マシン構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="7bb51-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bb51-125">例</span><span class="sxs-lookup"><span data-stu-id="7bb51-125">Example</span></span>  

 <span data-ttu-id="7bb51-126">次の例では、要素を使用し `<clear>` てリスナーを追加してから、 `<add>` `console` `textListener` `Listeners` トレースソースのコレクションに追加 `TraceSourceApp` する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7bb51-126">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
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
  
## <a name="see-also"></a><span data-ttu-id="7bb51-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="7bb51-127">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="7bb51-128">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="7bb51-128">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7bb51-129">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="7bb51-129">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
