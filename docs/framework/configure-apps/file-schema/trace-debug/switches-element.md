---
description: '詳細情報: <switches> 要素'
title: <switches> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: d0ffdf2bdc4dacd157d09d34c40063b687595e3d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750521"
---
# <a name="switches-element"></a><span data-ttu-id="8316d-103">\<switches> 要素</span><span class="sxs-lookup"><span data-stu-id="8316d-103">\<switches> Element</span></span>

<span data-ttu-id="8316d-104">トレース スイッチと、トレース スイッチを設定するレベルを保持します。</span><span class="sxs-lookup"><span data-stu-id="8316d-104">Contains trace switches and the level where the trace switches are set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**

## <a name="syntax"></a><span data-ttu-id="8316d-105">構文</span><span class="sxs-lookup"><span data-stu-id="8316d-105">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8316d-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8316d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="8316d-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8316d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8316d-108">属性</span><span class="sxs-lookup"><span data-stu-id="8316d-108">Attributes</span></span>  

 <span data-ttu-id="8316d-109">なし。</span><span class="sxs-lookup"><span data-stu-id="8316d-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8316d-110">子要素</span><span class="sxs-lookup"><span data-stu-id="8316d-110">Child Elements</span></span>  
  
|<span data-ttu-id="8316d-111">要素</span><span class="sxs-lookup"><span data-stu-id="8316d-111">Element</span></span>|<span data-ttu-id="8316d-112">説明</span><span class="sxs-lookup"><span data-stu-id="8316d-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="8316d-113">トレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="8316d-113">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8316d-114">親要素</span><span class="sxs-lookup"><span data-stu-id="8316d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8316d-115">要素</span><span class="sxs-lookup"><span data-stu-id="8316d-115">Element</span></span>|<span data-ttu-id="8316d-116">説明</span><span class="sxs-lookup"><span data-stu-id="8316d-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8316d-117">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="8316d-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="8316d-118">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="8316d-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8316d-119">解説</span><span class="sxs-lookup"><span data-stu-id="8316d-119">Remarks</span></span>  

 <span data-ttu-id="8316d-120">トレーススイッチのレベルは、構成ファイルに配置することによって変更できます。</span><span class="sxs-lookup"><span data-stu-id="8316d-120">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="8316d-121">スイッチがの場合は <xref:System.Diagnostics.BooleanSwitch> 、オンまたはオフにすることができます。</span><span class="sxs-lookup"><span data-stu-id="8316d-121">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="8316d-122">スイッチがの場合は <xref:System.Diagnostics.TraceSwitch> 、別のレベルを割り当てて、アプリケーションが出力するトレースメッセージまたはデバッグメッセージの種類を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8316d-122">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8316d-123">例</span><span class="sxs-lookup"><span data-stu-id="8316d-123">Example</span></span>  

 <span data-ttu-id="8316d-124">次の例では、要素を使用して **\<switch>** `General` トレーススイッチをレベルに設定 <xref:System.Diagnostics.TraceLevel> し、ブール型のトレーススイッチを有効にする方法を示し `Data` ます。</span><span class="sxs-lookup"><span data-stu-id="8316d-124">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8316d-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="8316d-125">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="8316d-126">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="8316d-126">Trace and Debug Settings Schema</span></span>](index.md)
