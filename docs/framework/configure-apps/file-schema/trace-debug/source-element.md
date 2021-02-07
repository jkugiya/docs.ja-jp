---
description: '詳細情報: <source> 要素'
title: <source> 要素
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: acf510dd5813900f36ac431418d55bbc6c2f364a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750586"
---
# <a name="source-element"></a><span data-ttu-id="b02dc-103">\<source> 要素</span><span class="sxs-lookup"><span data-stu-id="b02dc-103">\<source> Element</span></span>

<span data-ttu-id="b02dc-104">トレース メッセージを開始するトレース ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="b02dc-104">Specifies a trace source that initiates tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**

## <a name="syntax"></a><span data-ttu-id="b02dc-105">構文</span><span class="sxs-lookup"><span data-stu-id="b02dc-105">Syntax</span></span>  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b02dc-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b02dc-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b02dc-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b02dc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b02dc-108">属性</span><span class="sxs-lookup"><span data-stu-id="b02dc-108">Attributes</span></span>  
  
|<span data-ttu-id="b02dc-109">属性</span><span class="sxs-lookup"><span data-stu-id="b02dc-109">Attribute</span></span>|<span data-ttu-id="b02dc-110">説明</span><span class="sxs-lookup"><span data-stu-id="b02dc-110">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="b02dc-111">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="b02dc-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b02dc-112">トレースソースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="b02dc-112">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="b02dc-113">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="b02dc-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b02dc-114">アプリケーションのトレーススイッチインスタンスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="b02dc-114">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="b02dc-115">スイッチが要素で識別されない場合は、 `<switches>` スイッチのレベルを値で指定します。</span><span class="sxs-lookup"><span data-stu-id="b02dc-115">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="b02dc-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="b02dc-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b02dc-117">トレーススイッチの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="b02dc-117">Specifies the type of the trace switch.</span></span> <span data-ttu-id="b02dc-118">存在する場合、型は有効なクラス名である必要があり、空の文字列にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b02dc-118">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="b02dc-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="b02dc-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b02dc-120">トレースソースに対してメソッドによって識別される、トレースソース固有の属性の値を指定し <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="b02dc-120">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b02dc-121">子要素</span><span class="sxs-lookup"><span data-stu-id="b02dc-121">Child Elements</span></span>  
  
|<span data-ttu-id="b02dc-122">要素</span><span class="sxs-lookup"><span data-stu-id="b02dc-122">Element</span></span>|<span data-ttu-id="b02dc-123">説明</span><span class="sxs-lookup"><span data-stu-id="b02dc-123">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-source.md)|<span data-ttu-id="b02dc-124">メッセージを収集、格納、およびルーティングするリスナーを格納します。</span><span class="sxs-lookup"><span data-stu-id="b02dc-124">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b02dc-125">親要素</span><span class="sxs-lookup"><span data-stu-id="b02dc-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b02dc-126">要素</span><span class="sxs-lookup"><span data-stu-id="b02dc-126">Element</span></span>|<span data-ttu-id="b02dc-127">説明</span><span class="sxs-lookup"><span data-stu-id="b02dc-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b02dc-128">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="b02dc-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b02dc-129">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="b02dc-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="b02dc-130">トレース メッセージを開始するトレース ソースを保持します。</span><span class="sxs-lookup"><span data-stu-id="b02dc-130">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b02dc-131">解説</span><span class="sxs-lookup"><span data-stu-id="b02dc-131">Remarks</span></span>  

 <span data-ttu-id="b02dc-132">この要素は、マシン構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b02dc-132">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b02dc-133">例</span><span class="sxs-lookup"><span data-stu-id="b02dc-133">Example</span></span>  

 <span data-ttu-id="b02dc-134">次の例では、要素を使用してトレースソースを追加し、と `<source>` `mySource` いう名前のソーススイッチのレベルを設定する方法を示し `sourceSwitch` ます。</span><span class="sxs-lookup"><span data-stu-id="b02dc-134">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="b02dc-135">トレース情報をコンソールに書き込むコンソールトレースリスナーが追加されます。</span><span class="sxs-lookup"><span data-stu-id="b02dc-135">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>
  </system.diagnostics>
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b02dc-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="b02dc-136">See also</span></span>

- [<span data-ttu-id="b02dc-137">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="b02dc-137">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b02dc-138">トレース スイッチ</span><span class="sxs-lookup"><span data-stu-id="b02dc-138">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
