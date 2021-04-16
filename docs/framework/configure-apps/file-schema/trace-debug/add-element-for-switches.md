---
description: '詳細情報: <switches> の <add> 要素'
title: <switches> の <add> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: fc47a8518aca1e4e6390d9d7eba97d5fb7a7664e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639719"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="cb627-103">\<switches> の \<add> 要素</span><span class="sxs-lookup"><span data-stu-id="cb627-103">\<add> Element for \<switches></span></span>

<span data-ttu-id="cb627-104">トレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="cb627-104">Specifies the level where a trace switch is set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="cb627-105">構文</span><span class="sxs-lookup"><span data-stu-id="cb627-105">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb627-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cb627-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cb627-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb627-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb627-108">属性</span><span class="sxs-lookup"><span data-stu-id="cb627-108">Attributes</span></span>  
  
|<span data-ttu-id="cb627-109">属性</span><span class="sxs-lookup"><span data-stu-id="cb627-109">Attribute</span></span>|<span data-ttu-id="cb627-110">説明</span><span class="sxs-lookup"><span data-stu-id="cb627-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb627-111">**name**</span><span class="sxs-lookup"><span data-stu-id="cb627-111">**name**</span></span>|<span data-ttu-id="cb627-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="cb627-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="cb627-113">スイッチの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb627-113">Specifies the name of the switch.</span></span> <span data-ttu-id="cb627-114">この属性の値は、スイッチ コンストラクターに渡される *displayName* パラメーターに対応します。</span><span class="sxs-lookup"><span data-stu-id="cb627-114">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="cb627-115">**value**</span><span class="sxs-lookup"><span data-stu-id="cb627-115">**value**</span></span>|<span data-ttu-id="cb627-116">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="cb627-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="cb627-117">スイッチのレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="cb627-117">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb627-118">子要素</span><span class="sxs-lookup"><span data-stu-id="cb627-118">Child Elements</span></span>  

 <span data-ttu-id="cb627-119">なし。</span><span class="sxs-lookup"><span data-stu-id="cb627-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb627-120">親要素</span><span class="sxs-lookup"><span data-stu-id="cb627-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cb627-121">要素</span><span class="sxs-lookup"><span data-stu-id="cb627-121">Element</span></span>|<span data-ttu-id="cb627-122">説明</span><span class="sxs-lookup"><span data-stu-id="cb627-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cb627-123">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="cb627-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="cb627-124">トレース スイッチと、トレース スイッチを設定するレベルを保持します。</span><span class="sxs-lookup"><span data-stu-id="cb627-124">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="cb627-125">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="cb627-125">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb627-126">解説</span><span class="sxs-lookup"><span data-stu-id="cb627-126">Remarks</span></span>  

 <span data-ttu-id="cb627-127">トレース スイッチのレベルは、構成ファイルに配置して変更できます。</span><span class="sxs-lookup"><span data-stu-id="cb627-127">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="cb627-128">スイッチが <xref:System.Diagnostics.BooleanSwitch> の場合は、オンまたはオフにすることができます。</span><span class="sxs-lookup"><span data-stu-id="cb627-128">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="cb627-129">スイッチが <xref:System.Diagnostics.TraceSwitch> の場合は、別のレベルを割り当てて、アプリケーションが出力するトレース メッセージまたはデバッグ メッセージの種類を指定できます。</span><span class="sxs-lookup"><span data-stu-id="cb627-129">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb627-130">例</span><span class="sxs-lookup"><span data-stu-id="cb627-130">Example</span></span>  

 <span data-ttu-id="cb627-131">次の例では、 **\<add>** 要素を使用してトレース スイッチ `General` を <xref:System.Diagnostics.TraceLevel> レベルに設定し、ブール型のトレース スイッチ `Data` を有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cb627-131">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb627-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb627-132">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="cb627-133">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="cb627-133">Trace and Debug Settings Schema</span></span>](index.md)
