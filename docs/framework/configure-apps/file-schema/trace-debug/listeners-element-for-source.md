---
description: '詳細情報: <source> の <listeners> 要素'
title: <source> の <listeners> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 6b857d4b114366d268eec1859afc7f33cc5b04a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639642"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="a0979-103">\<source> の \<listeners> 要素</span><span class="sxs-lookup"><span data-stu-id="a0979-103">\<listeners> Element for \<source></span></span>

<span data-ttu-id="a0979-104"><xref:System.Diagnostics.TraceSource> の <xref:System.Diagnostics.TraceSource.Listeners%2A> コレクション内のリスナーを追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="a0979-104">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="a0979-105">リスナーにより、トレース出力が適切な場所 (ログ、ウィンドウ、またはテキスト ファイル) に送られます。</span><span class="sxs-lookup"><span data-stu-id="a0979-105">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**  
  
## <a name="syntax"></a><span data-ttu-id="a0979-106">構文</span><span class="sxs-lookup"><span data-stu-id="a0979-106">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0979-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a0979-107">Attributes and Elements</span></span>  

 <span data-ttu-id="a0979-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a0979-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0979-109">属性</span><span class="sxs-lookup"><span data-stu-id="a0979-109">Attributes</span></span>  

 <span data-ttu-id="a0979-110">なし。</span><span class="sxs-lookup"><span data-stu-id="a0979-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a0979-111">子要素</span><span class="sxs-lookup"><span data-stu-id="a0979-111">Child Elements</span></span>  
  
|<span data-ttu-id="a0979-112">要素</span><span class="sxs-lookup"><span data-stu-id="a0979-112">Element</span></span>|<span data-ttu-id="a0979-113">説明</span><span class="sxs-lookup"><span data-stu-id="a0979-113">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|<span data-ttu-id="a0979-114">`Listeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="a0979-114">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="a0979-115">`Listeners` コレクションからリスナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="a0979-115">Removes a listener from the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="a0979-116">トレース ソースの `Listeners` コレクションを消去します。</span><span class="sxs-lookup"><span data-stu-id="a0979-116">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0979-117">親要素</span><span class="sxs-lookup"><span data-stu-id="a0979-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a0979-118">要素</span><span class="sxs-lookup"><span data-stu-id="a0979-118">Element</span></span>|<span data-ttu-id="a0979-119">説明</span><span class="sxs-lookup"><span data-stu-id="a0979-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a0979-120">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="a0979-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a0979-121">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="a0979-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="a0979-122">トレース メッセージを開始するトレース ソースを保持します。</span><span class="sxs-lookup"><span data-stu-id="a0979-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="a0979-123">トレース メッセージを開始するトレース ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="a0979-123">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0979-124">解説</span><span class="sxs-lookup"><span data-stu-id="a0979-124">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="a0979-125">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="a0979-125">Configuration File</span></span>  

 <span data-ttu-id="a0979-126">この要素は、マシン構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="a0979-126">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0979-127">例</span><span class="sxs-lookup"><span data-stu-id="a0979-127">Example</span></span>  

 <span data-ttu-id="a0979-128">次の例は、`<listeners>` 要素を使用してコンソール トレース リスナーを `mySource` ソースに追加し、既定のトレース リスナーを削除する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a0979-128">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0979-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0979-129">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="a0979-130">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="a0979-130">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a0979-131">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="a0979-131">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
