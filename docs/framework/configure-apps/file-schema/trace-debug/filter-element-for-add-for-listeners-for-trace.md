---
description: 詳細については、のの要素に関するページを参照してください。 <filter> <add> <listeners><trace>
title: <filter>のの <add> 要素 <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: a47903a696fcbf2cd7f4eecda526f93955a31f11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754486"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="57e22-103">\<filter>のの \<add> 要素 \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="57e22-103">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>

<span data-ttu-id="57e22-104">トレースのコレクションのリスナーにフィルターを追加し `Listeners` ます。</span><span class="sxs-lookup"><span data-stu-id="57e22-104">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="57e22-105">構文</span><span class="sxs-lookup"><span data-stu-id="57e22-105">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57e22-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="57e22-106">Attributes and Elements</span></span>  

 <span data-ttu-id="57e22-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="57e22-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57e22-108">属性</span><span class="sxs-lookup"><span data-stu-id="57e22-108">Attributes</span></span>  
  
|<span data-ttu-id="57e22-109">属性</span><span class="sxs-lookup"><span data-stu-id="57e22-109">Attribute</span></span>|<span data-ttu-id="57e22-110">説明</span><span class="sxs-lookup"><span data-stu-id="57e22-110">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="57e22-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="57e22-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="57e22-112">フィルターの種類を指定します。この型はクラスから継承する必要があり <xref:System.Diagnostics.TraceFilter> ます。</span><span class="sxs-lookup"><span data-stu-id="57e22-112">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="57e22-113">型の名前空間で修飾された名前を使用できます。これは、型のプロパティに対応し <xref:System.Type.FullName%2A> ます。または、プロパティに対応するアセンブリ情報を含む完全修飾型名を使用することもでき <xref:System.Type.AssemblyQualifiedName%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="57e22-113">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="57e22-114">完全修飾型名の詳細については、「 [完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57e22-114">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="57e22-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="57e22-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="57e22-116">指定されたフィルタークラスのコンストラクターに渡される文字列。</span><span class="sxs-lookup"><span data-stu-id="57e22-116">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57e22-117">子要素</span><span class="sxs-lookup"><span data-stu-id="57e22-117">Child Elements</span></span>  

 <span data-ttu-id="57e22-118">なし。</span><span class="sxs-lookup"><span data-stu-id="57e22-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57e22-119">親要素</span><span class="sxs-lookup"><span data-stu-id="57e22-119">Parent Elements</span></span>  
  
|<span data-ttu-id="57e22-120">要素</span><span class="sxs-lookup"><span data-stu-id="57e22-120">Element</span></span>|<span data-ttu-id="57e22-121">説明</span><span class="sxs-lookup"><span data-stu-id="57e22-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="57e22-122">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="57e22-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="57e22-123">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="57e22-123">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="57e22-124">トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。</span><span class="sxs-lookup"><span data-stu-id="57e22-124">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="57e22-125">メッセージを収集、格納、およびルーティングするリスナーを格納します。</span><span class="sxs-lookup"><span data-stu-id="57e22-125">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="57e22-126">リスナーは、適切なターゲットにトレース出力を送信します。</span><span class="sxs-lookup"><span data-stu-id="57e22-126">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="57e22-127">`Listeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="57e22-127">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57e22-128">解説</span><span class="sxs-lookup"><span data-stu-id="57e22-128">Remarks</span></span>  

 <span data-ttu-id="57e22-129">`<filter>`要素は `<add>` 、で定義されているリスナーの名前だけでなく、リスナーの種類を指定するトレースリスナーの要素に格納されている必要があり [\<sharedListeners>](sharedlisteners-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="57e22-129">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="57e22-130">リスナーがで定義されている場合は [\<sharedListeners>](sharedlisteners-element.md) 、そのリスナーのフィルターをその要素で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57e22-130">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="57e22-131">この要素は、マシン構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="57e22-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57e22-132">例</span><span class="sxs-lookup"><span data-stu-id="57e22-132">Example</span></span>  

 <span data-ttu-id="57e22-133">次の例では、要素を使用して、フィルター `<filter>` `console` `Listeners` イベントレベルをとして指定し、トレースのコレクション内のリスナーにフィルターを追加する方法を示し `Error` ます。</span><span class="sxs-lookup"><span data-stu-id="57e22-133">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="57e22-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="57e22-134">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="57e22-135">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="57e22-135">Trace and Debug Settings Schema</span></span>](index.md)
