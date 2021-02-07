---
description: '詳細については、次のページを参照してください: <system.web> 要素 (Web 設定)'
title: <system.web> 要素 (Web 設定)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: 2adcd3eba1eb6d67bcb4dc82243cd70d31d64fe9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681904"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="ba0ce-103">\<system.web> 要素 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="ba0ce-103">\<system.web> Element (Web Settings)</span></span>

<span data-ttu-id="ba0ce-104">ASP.NET ホスティングレイヤーがプロセス全体の動作をどのように管理するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ba0ce-104">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
## <a name="syntax"></a><span data-ttu-id="ba0ce-105">構文</span><span class="sxs-lookup"><span data-stu-id="ba0ce-105">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba0ce-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ba0ce-106">Attributes and Elements</span></span>  

<span data-ttu-id="ba0ce-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba0ce-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba0ce-108">属性</span><span class="sxs-lookup"><span data-stu-id="ba0ce-108">Attributes</span></span>  

<span data-ttu-id="ba0ce-109">なし。</span><span class="sxs-lookup"><span data-stu-id="ba0ce-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ba0ce-110">子要素</span><span class="sxs-lookup"><span data-stu-id="ba0ce-110">Child Elements</span></span>  
  
|<span data-ttu-id="ba0ce-111">要素</span><span class="sxs-lookup"><span data-stu-id="ba0ce-111">Element</span></span>|<span data-ttu-id="ba0ce-112">説明</span><span class="sxs-lookup"><span data-stu-id="ba0ce-112">Description</span></span>|  
|-------------|-----------------|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|<span data-ttu-id="ba0ce-113">aspnet.config ファイル内の IIS アプリケーションプールの構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="ba0ce-113">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ba0ce-114">親要素</span><span class="sxs-lookup"><span data-stu-id="ba0ce-114">Parent Elements</span></span>  
  
|<span data-ttu-id="ba0ce-115">要素</span><span class="sxs-lookup"><span data-stu-id="ba0ce-115">Element</span></span>|<span data-ttu-id="ba0ce-116">説明</span><span class="sxs-lookup"><span data-stu-id="ba0ce-116">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="ba0ce-117">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="ba0ce-117">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba0ce-118">解説</span><span class="sxs-lookup"><span data-stu-id="ba0ce-118">Remarks</span></span>  

<span data-ttu-id="ba0ce-119">`system.web`要素とその子 `applicationPool` 要素が .NET FRAMEWORK 3.5 SP1 の .NET Framework に追加されました。</span><span class="sxs-lookup"><span data-stu-id="ba0ce-119">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="ba0ce-120">IIS 7.0 以降のバージョンを統合モードで実行すると、この要素の組み合わせによって、ASP.NET がどのようにスレッドを管理し、ASP.NET が IIS アプリケーションプールでホストされている場合の要求をキューに配置するかを構成できます。</span><span class="sxs-lookup"><span data-stu-id="ba0ce-120">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="ba0ce-121">IIS 7.0 以降のバージョンをクラシックモードまたは ISAPI モードで実行した場合、これらの設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="ba0ce-121">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba0ce-122">例</span><span class="sxs-lookup"><span data-stu-id="ba0ce-122">Example</span></span>  

<span data-ttu-id="ba0ce-123">次の例では、IIS アプリケーションプールで ASP.NET がホストされている場合に、aspnet.config ファイルに ASP.NET プロセス全体の動作を構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ba0ce-123">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="ba0ce-124">この例では、IIS が統合モードで実行されており、アプリケーションが .NET Framework 3.5 SP1 以降のバージョンを使用していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="ba0ce-124">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="ba0ce-125">この動作は、.NET Framework 3.5 SP1 より前のバージョンの .NET Framework では発生しません。</span><span class="sxs-lookup"><span data-stu-id="ba0ce-125">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="ba0ce-126">この例の値は既定値です。</span><span class="sxs-lookup"><span data-stu-id="ba0ce-126">The values in the example are the default values.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool
        maxConcurrentRequestsPerCPU="5000"
        maxConcurrentThreadsPerCPU="0"
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="ba0ce-127">要素情報</span><span class="sxs-lookup"><span data-stu-id="ba0ce-127">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ba0ce-128">名前空間</span><span class="sxs-lookup"><span data-stu-id="ba0ce-128">Namespace</span></span>||  
|<span data-ttu-id="ba0ce-129">スキーマ名</span><span class="sxs-lookup"><span data-stu-id="ba0ce-129">Schema Name</span></span>||  
|<span data-ttu-id="ba0ce-130">検証ファイル</span><span class="sxs-lookup"><span data-stu-id="ba0ce-130">Validation File</span></span>||  
|<span data-ttu-id="ba0ce-131">空にすることができます</span><span class="sxs-lookup"><span data-stu-id="ba0ce-131">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="ba0ce-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba0ce-132">See also</span></span>

- [<span data-ttu-id="ba0ce-133">\<applicationPool> 要素 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="ba0ce-133">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
