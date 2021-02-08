---
description: '詳細情報: <etwEnable> 要素'
title: <etwEnable> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 224784f47d15788ded41a5756e1d179a5a25907b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787046"
---
# <a name="etwenable-element"></a><span data-ttu-id="28797-103">\<etwEnable> 要素</span><span class="sxs-lookup"><span data-stu-id="28797-103">\<etwEnable> Element</span></span>

<span data-ttu-id="28797-104">共通言語ランタイム イベントで Windows イベント トレーシング (ETW) を有効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="28797-104">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**  
  
## <a name="syntax"></a><span data-ttu-id="28797-105">構文</span><span class="sxs-lookup"><span data-stu-id="28797-105">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28797-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="28797-106">Attributes and Elements</span></span>  

 <span data-ttu-id="28797-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="28797-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28797-108">属性</span><span class="sxs-lookup"><span data-stu-id="28797-108">Attributes</span></span>  
  
|<span data-ttu-id="28797-109">属性</span><span class="sxs-lookup"><span data-stu-id="28797-109">Attribute</span></span>|<span data-ttu-id="28797-110">説明</span><span class="sxs-lookup"><span data-stu-id="28797-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="28797-111">enabled</span><span class="sxs-lookup"><span data-stu-id="28797-111">enabled</span></span>|<span data-ttu-id="28797-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="28797-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="28797-113">ETW を有効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="28797-113">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="28797-114">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="28797-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="28797-115">値</span><span class="sxs-lookup"><span data-stu-id="28797-115">Value</span></span>|<span data-ttu-id="28797-116">説明</span><span class="sxs-lookup"><span data-stu-id="28797-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="28797-117">true</span><span class="sxs-lookup"><span data-stu-id="28797-117">true</span></span>|<span data-ttu-id="28797-118">ETW を有効にします。</span><span class="sxs-lookup"><span data-stu-id="28797-118">Enable ETW.</span></span> <span data-ttu-id="28797-119">Windows Vista および Windows Server 2008 オペレーティングシステム以降のバージョンの Windows では、これが既定です。</span><span class="sxs-lookup"><span data-stu-id="28797-119">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="28797-120">false</span><span class="sxs-lookup"><span data-stu-id="28797-120">false</span></span>|<span data-ttu-id="28797-121">ETW を無効にします。</span><span class="sxs-lookup"><span data-stu-id="28797-121">Disable ETW.</span></span> <span data-ttu-id="28797-122">これは、以前のバージョンの Windows では既定です。</span><span class="sxs-lookup"><span data-stu-id="28797-122">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28797-123">子要素</span><span class="sxs-lookup"><span data-stu-id="28797-123">Child Elements</span></span>  

 <span data-ttu-id="28797-124">なし。</span><span class="sxs-lookup"><span data-stu-id="28797-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28797-125">親要素</span><span class="sxs-lookup"><span data-stu-id="28797-125">Parent Elements</span></span>  
  
|<span data-ttu-id="28797-126">要素</span><span class="sxs-lookup"><span data-stu-id="28797-126">Element</span></span>|<span data-ttu-id="28797-127">説明</span><span class="sxs-lookup"><span data-stu-id="28797-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="28797-128">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="28797-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="28797-129">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="28797-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28797-130">解説</span><span class="sxs-lookup"><span data-stu-id="28797-130">Remarks</span></span>  

 <span data-ttu-id="28797-131">Windows Vista 以降では、ETW は既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="28797-131">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="28797-132">アプリケーションの ETW を無効にするには、この要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="28797-132">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="28797-133">以前のバージョンの Windows では、この要素を使用して、アプリケーションの ETW を有効にします。</span><span class="sxs-lookup"><span data-stu-id="28797-133">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28797-134">ETW は、レジストリ設定を使用して、サーバー上でグローバルに有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="28797-134">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="28797-135">「 [.NET Framework のログ記録の制御](../../../performance/controlling-logging.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28797-135">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="28797-136">例</span><span class="sxs-lookup"><span data-stu-id="28797-136">Example</span></span>  

 <span data-ttu-id="28797-137">次の例は、アプリケーションの ETW トレースを有効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="28797-137">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="28797-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="28797-138">See also</span></span>

- [<span data-ttu-id="28797-139">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="28797-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="28797-140">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="28797-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="28797-141">.NET Framework のログ記録の制御</span><span class="sxs-lookup"><span data-stu-id="28797-141">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
