---
description: の詳細については、「」を参照してください。 <remove> <listeners><source>
title: <remove> のの <listeners> 要素 <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 2f7a815fe97fda95d71bc2a5a1b8fdda7bc2a0ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750625"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="a7890-103">\<remove> のの \<listeners> 要素 \<source></span><span class="sxs-lookup"><span data-stu-id="a7890-103">\<remove> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="a7890-104">トレース ソースの `Listeners` コレクションからリスナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="a7890-104">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="a7890-105">構文</span><span class="sxs-lookup"><span data-stu-id="a7890-105">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7890-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a7890-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a7890-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a7890-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7890-108">属性</span><span class="sxs-lookup"><span data-stu-id="a7890-108">Attributes</span></span>  
  
|<span data-ttu-id="a7890-109">属性</span><span class="sxs-lookup"><span data-stu-id="a7890-109">Attribute</span></span>|<span data-ttu-id="a7890-110">説明</span><span class="sxs-lookup"><span data-stu-id="a7890-110">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="a7890-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="a7890-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="a7890-112">コレクションから削除するリスナーの名前 `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="a7890-112">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7890-113">子要素</span><span class="sxs-lookup"><span data-stu-id="a7890-113">Child Elements</span></span>  

 <span data-ttu-id="a7890-114">なし。</span><span class="sxs-lookup"><span data-stu-id="a7890-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7890-115">親要素</span><span class="sxs-lookup"><span data-stu-id="a7890-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a7890-116">要素</span><span class="sxs-lookup"><span data-stu-id="a7890-116">Element</span></span>|<span data-ttu-id="a7890-117">説明</span><span class="sxs-lookup"><span data-stu-id="a7890-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a7890-118">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="a7890-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a7890-119">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="a7890-119">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="a7890-120">トレース メッセージを開始するトレース ソースを保持します。</span><span class="sxs-lookup"><span data-stu-id="a7890-120">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="a7890-121">トレース メッセージを開始するトレース ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="a7890-121">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="a7890-122">メッセージを収集、格納、およびルーティングするリスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="a7890-122">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7890-123">解説</span><span class="sxs-lookup"><span data-stu-id="a7890-123">Remarks</span></span>  

 <span data-ttu-id="a7890-124">要素は、 `<remove>` 指定されたリスナーを `Listeners` トレースソースのコレクションから削除します。</span><span class="sxs-lookup"><span data-stu-id="a7890-124">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="a7890-125">`Listeners` <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> インスタンスのプロパティに対してメソッドを呼び出すことによって、プログラムによってトレースソースのコレクションから要素を削除でき <xref:System.Diagnostics.TraceSource.Listeners%2A> <xref:System.Diagnostics.TraceSource> ます。</span><span class="sxs-lookup"><span data-stu-id="a7890-125">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="a7890-126">この要素は、マシン構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="a7890-126">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7890-127">例</span><span class="sxs-lookup"><span data-stu-id="a7890-127">Example</span></span>  

 <span data-ttu-id="a7890-128">次の例では、要素を使用し `<remove>` て、 `<add>` リスナーを `console` `Listeners` トレースソースのコレクションに追加する前に、要素を使用する方法を示し `TraceSourceApp` ます。</span><span class="sxs-lookup"><span data-stu-id="a7890-128">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="a7890-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7890-129">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="a7890-130">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="a7890-130">Trace and Debug Settings Schema</span></span>](index.md)
- [\<clear>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="a7890-131">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="a7890-131">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
