---
description: の詳細については、「」を参照してください。 <filter> <add><sharedListeners>
title: <filter> のの <add> 要素 <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: 5d6567ff029dea5ed98054dbc524bb7ed405324c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802373"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="0cb40-103">\<filter> のの \<add> 要素 \<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="0cb40-103">\<filter> Element for \<add> for \<sharedListeners></span></span>

<span data-ttu-id="0cb40-104">`sharedListeners` コレクションのリスナーにフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="0cb40-104">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="0cb40-105">構文</span><span class="sxs-lookup"><span data-stu-id="0cb40-105">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0cb40-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0cb40-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0cb40-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0cb40-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0cb40-108">属性</span><span class="sxs-lookup"><span data-stu-id="0cb40-108">Attributes</span></span>  
  
|<span data-ttu-id="0cb40-109">属性</span><span class="sxs-lookup"><span data-stu-id="0cb40-109">Attribute</span></span>|<span data-ttu-id="0cb40-110">説明</span><span class="sxs-lookup"><span data-stu-id="0cb40-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0cb40-111">**type**</span><span class="sxs-lookup"><span data-stu-id="0cb40-111">**type**</span></span>|<span data-ttu-id="0cb40-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="0cb40-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="0cb40-113">フィルターの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="0cb40-113">Specifies the type of the filter.</span></span> <span data-ttu-id="0cb40-114">型の完全な名前 (プロパティの形式) のみを使用することも、 <xref:System.Type.FullName%2A?displayProperty=nameWithType> アセンブリ情報を含む完全修飾型名 (プロパティの形式) を使用することもでき <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="0cb40-114">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="0cb40-115">完全修飾型名の作成の詳細については、「 [完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cb40-115">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="0cb40-116">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="0cb40-116">**initializeData**</span></span>|<span data-ttu-id="0cb40-117">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="0cb40-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0cb40-118">指定したクラスのコンストラクターに渡される文字列。</span><span class="sxs-lookup"><span data-stu-id="0cb40-118">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0cb40-119">子要素</span><span class="sxs-lookup"><span data-stu-id="0cb40-119">Child Elements</span></span>  

 <span data-ttu-id="0cb40-120">なし。</span><span class="sxs-lookup"><span data-stu-id="0cb40-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0cb40-121">親要素</span><span class="sxs-lookup"><span data-stu-id="0cb40-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0cb40-122">要素</span><span class="sxs-lookup"><span data-stu-id="0cb40-122">Element</span></span>|<span data-ttu-id="0cb40-123">説明</span><span class="sxs-lookup"><span data-stu-id="0cb40-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0cb40-124">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="0cb40-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0cb40-125">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="0cb40-125">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="0cb40-126">任意のソースまたはトレース要素が参照できるリスナーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="0cb40-126">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="0cb40-127">リスナーを **sharedListeners** コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="0cb40-127">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cb40-128">解説</span><span class="sxs-lookup"><span data-stu-id="0cb40-128">Remarks</span></span>  

 <span data-ttu-id="0cb40-129">リスナーが要素の要素で定義されている場合 `<add>` `<sharedListeners>` 、そのリスナーのフィルターは、要素の子である要素で定義されている必要があり `<filter>` `<add>` ます。</span><span class="sxs-lookup"><span data-stu-id="0cb40-129">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="0cb40-130">この要素は、マシン構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="0cb40-130">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cb40-131">例</span><span class="sxs-lookup"><span data-stu-id="0cb40-131">Example</span></span>  

 <span data-ttu-id="0cb40-132">次の例は、要素を使用して、 `<filter>` コレクション内のトレースリスナーにフィルターを追加する方法を示して `console` `sharedListeners` います。</span><span class="sxs-lookup"><span data-stu-id="0cb40-132">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cb40-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cb40-133">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="0cb40-134">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="0cb40-134">Trace and Debug Settings Schema</span></span>](index.md)
