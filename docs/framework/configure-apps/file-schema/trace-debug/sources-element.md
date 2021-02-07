---
description: '詳細情報: <sources> 要素'
title: <sources> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
ms.openlocfilehash: 8e5bf2af74d80cf7766de0992623d4792f17bf37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750547"
---
# <a name="sources-element"></a><span data-ttu-id="5faf1-103">\<sources> 要素</span><span class="sxs-lookup"><span data-stu-id="5faf1-103">\<sources> Element</span></span>

<span data-ttu-id="5faf1-104">トレースメッセージを開始するトレースソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="5faf1-104">Specifies trace sources that initiate tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**

## <a name="syntax"></a><span data-ttu-id="5faf1-105">構文</span><span class="sxs-lookup"><span data-stu-id="5faf1-105">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5faf1-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5faf1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="5faf1-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5faf1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5faf1-108">属性</span><span class="sxs-lookup"><span data-stu-id="5faf1-108">Attributes</span></span>  

 <span data-ttu-id="5faf1-109">なし。</span><span class="sxs-lookup"><span data-stu-id="5faf1-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5faf1-110">子要素</span><span class="sxs-lookup"><span data-stu-id="5faf1-110">Child Elements</span></span>  
  
|<span data-ttu-id="5faf1-111">要素</span><span class="sxs-lookup"><span data-stu-id="5faf1-111">Element</span></span>|<span data-ttu-id="5faf1-112">説明</span><span class="sxs-lookup"><span data-stu-id="5faf1-112">Description</span></span>|  
|-------------|-----------------|  
|[\<source>](source-element.md)|<span data-ttu-id="5faf1-113">必須の要素です。</span><span class="sxs-lookup"><span data-stu-id="5faf1-113">Required element.</span></span><br /><br /> <span data-ttu-id="5faf1-114">トレース メッセージを開始するトレース ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="5faf1-114">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5faf1-115">親要素</span><span class="sxs-lookup"><span data-stu-id="5faf1-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5faf1-116">要素</span><span class="sxs-lookup"><span data-stu-id="5faf1-116">Element</span></span>|<span data-ttu-id="5faf1-117">説明</span><span class="sxs-lookup"><span data-stu-id="5faf1-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5faf1-118">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="5faf1-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5faf1-119">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="5faf1-119">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5faf1-120">解説</span><span class="sxs-lookup"><span data-stu-id="5faf1-120">Remarks</span></span>  

 <span data-ttu-id="5faf1-121">この要素は、マシン構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="5faf1-121">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5faf1-122">例</span><span class="sxs-lookup"><span data-stu-id="5faf1-122">Example</span></span>  

 <span data-ttu-id="5faf1-123">次の例では、要素を使用してトレースソースを追加し、と `<sources>` `mySource` いう名前のソーススイッチのレベルを設定する方法を示し `sourceSwitch` ます。</span><span class="sxs-lookup"><span data-stu-id="5faf1-123">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="5faf1-124">トレース情報をコンソールに書き込むコンソールトレースリスナーが追加されます。</span><span class="sxs-lookup"><span data-stu-id="5faf1-124">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
         <source name="mySource" switchName="sourceSwitch"
            switchType="System.Diagnostics.SourceSwitch"  >  
            <listeners>  
               <add name="console"
                  type="System.Diagnostics.ConsoleTraceListener" >  
                  <filter type="System.Diagnostics.EventTypeFilter"
                     initializeData="Error" />  
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
  
## <a name="see-also"></a><span data-ttu-id="5faf1-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="5faf1-125">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="5faf1-126">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="5faf1-126">Trace and Debug Settings Schema</span></span>](index.md)
- [\<source>](source-element.md)
