---
description: '詳細については、次を参照してください: <Crst_DisableSpinWait> 要素'
title: <Crst_DisableSpinWait> 要素
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: fca6fed2dabc3d1319ad030bb13bbb35a561b9aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795106"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="074ea-103">\<Crst_DisableSpinWait> 要素</span><span class="sxs-lookup"><span data-stu-id="074ea-103">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="074ea-104">競合がある場合に、クリティカルセクションのスピン待機を無効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="074ea-104">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**  
  
## <a name="syntax"></a><span data-ttu-id="074ea-105">構文</span><span class="sxs-lookup"><span data-stu-id="074ea-105">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="074ea-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="074ea-106">Attributes and Elements</span></span>

<span data-ttu-id="074ea-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="074ea-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="074ea-108">属性</span><span class="sxs-lookup"><span data-stu-id="074ea-108">Attributes</span></span>  
  
|<span data-ttu-id="074ea-109">属性</span><span class="sxs-lookup"><span data-stu-id="074ea-109">Attribute</span></span>|<span data-ttu-id="074ea-110">説明</span><span class="sxs-lookup"><span data-stu-id="074ea-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="074ea-111">**有効**</span><span class="sxs-lookup"><span data-stu-id="074ea-111">**enabled**</span></span>|<span data-ttu-id="074ea-112">重要なセクションが競合している場合は、スピンを待機するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="074ea-112">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="074ea-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="074ea-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="074ea-114">値</span><span class="sxs-lookup"><span data-stu-id="074ea-114">Value</span></span>|<span data-ttu-id="074ea-115">説明</span><span class="sxs-lookup"><span data-stu-id="074ea-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="074ea-116">1</span><span class="sxs-lookup"><span data-stu-id="074ea-116">1</span></span>|<span data-ttu-id="074ea-117">クリティカルセクションを取得できないときに、スピン待機を無効にします。</span><span class="sxs-lookup"><span data-stu-id="074ea-117">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="074ea-118">0</span><span class="sxs-lookup"><span data-stu-id="074ea-118">0</span></span>|<span data-ttu-id="074ea-119">クリティカルセクションを取得できない場合は、スピン待機を無効にしないでください。</span><span class="sxs-lookup"><span data-stu-id="074ea-119">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="074ea-120">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="074ea-120">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="074ea-121">子要素</span><span class="sxs-lookup"><span data-stu-id="074ea-121">Child Elements</span></span>  

 <span data-ttu-id="074ea-122">なし。</span><span class="sxs-lookup"><span data-stu-id="074ea-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="074ea-123">親要素</span><span class="sxs-lookup"><span data-stu-id="074ea-123">Parent Elements</span></span>  
  
|<span data-ttu-id="074ea-124">要素</span><span class="sxs-lookup"><span data-stu-id="074ea-124">Element</span></span>|<span data-ttu-id="074ea-125">説明</span><span class="sxs-lookup"><span data-stu-id="074ea-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="074ea-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="074ea-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="074ea-127">さまざまなランタイム構成設定に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="074ea-127">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="074ea-128">例</span><span class="sxs-lookup"><span data-stu-id="074ea-128">Example</span></span>  

<span data-ttu-id="074ea-129">次の例では、重要なセクションで、競合がある場合、スピン待機を無効にします。</span><span class="sxs-lookup"><span data-stu-id="074ea-129">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="074ea-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="074ea-130">See also</span></span>

- [<span data-ttu-id="074ea-131">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="074ea-131">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="074ea-132">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="074ea-132">Configuration File Schema</span></span>](../index.md)
