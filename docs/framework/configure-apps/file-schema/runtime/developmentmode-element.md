---
description: '詳細情報: <developmentMode> 要素'
title: <developmentMode> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
ms.openlocfilehash: 668461d13c8a1767268692804e9783bb6d4b9a56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787124"
---
# <a name="developmentmode-element"></a><span data-ttu-id="7464d-103">\<developmentMode> 要素</span><span class="sxs-lookup"><span data-stu-id="7464d-103">\<developmentMode> Element</span></span>

<span data-ttu-id="7464d-104">DEVPATH 環境変数によって指定されたディレクトリで、ランタイムがアセンブリの検索を行うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7464d-104">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**  
  
## <a name="syntax"></a><span data-ttu-id="7464d-105">構文</span><span class="sxs-lookup"><span data-stu-id="7464d-105">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7464d-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7464d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7464d-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7464d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7464d-108">属性</span><span class="sxs-lookup"><span data-stu-id="7464d-108">Attributes</span></span>  
  
|<span data-ttu-id="7464d-109">属性</span><span class="sxs-lookup"><span data-stu-id="7464d-109">Attribute</span></span>|<span data-ttu-id="7464d-110">説明</span><span class="sxs-lookup"><span data-stu-id="7464d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7464d-111">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="7464d-111">**developerInstallation**</span></span>|<span data-ttu-id="7464d-112">DEVPATH 環境変数によって指定されたディレクトリで、ランタイムがアセンブリの検索を行うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7464d-112">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="7464d-113">developerInstallation 属性</span><span class="sxs-lookup"><span data-stu-id="7464d-113">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="7464d-114">値</span><span class="sxs-lookup"><span data-stu-id="7464d-114">Value</span></span>|<span data-ttu-id="7464d-115">説明</span><span class="sxs-lookup"><span data-stu-id="7464d-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7464d-116">**true**</span><span class="sxs-lookup"><span data-stu-id="7464d-116">**true**</span></span>|<span data-ttu-id="7464d-117">DEVPATH 環境変数によって指定されたディレクトリ内のアセンブリを検索します。</span><span class="sxs-lookup"><span data-stu-id="7464d-117">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="7464d-118">**false**</span><span class="sxs-lookup"><span data-stu-id="7464d-118">**false**</span></span>|<span data-ttu-id="7464d-119">は、DEVPATH 環境変数によって指定されたディレクトリ内のアセンブリを検索しません。</span><span class="sxs-lookup"><span data-stu-id="7464d-119">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="7464d-120">これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="7464d-120">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7464d-121">子要素</span><span class="sxs-lookup"><span data-stu-id="7464d-121">Child Elements</span></span>  

 <span data-ttu-id="7464d-122">なし。</span><span class="sxs-lookup"><span data-stu-id="7464d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7464d-123">親要素</span><span class="sxs-lookup"><span data-stu-id="7464d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7464d-124">要素</span><span class="sxs-lookup"><span data-stu-id="7464d-124">Element</span></span>|<span data-ttu-id="7464d-125">説明</span><span class="sxs-lookup"><span data-stu-id="7464d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7464d-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="7464d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7464d-127">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7464d-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7464d-128">解説</span><span class="sxs-lookup"><span data-stu-id="7464d-128">Remarks</span></span>  

 <span data-ttu-id="7464d-129">この設定は、開発時にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="7464d-129">Use this setting only at development time.</span></span> <span data-ttu-id="7464d-130">ランタイムは、DEVPATH で見つかった厳密な名前のアセンブリのバージョンをチェックしません。</span><span class="sxs-lookup"><span data-stu-id="7464d-130">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="7464d-131">単純に、最初に見つかったアセンブリを使用します。</span><span class="sxs-lookup"><span data-stu-id="7464d-131">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7464d-132">例</span><span class="sxs-lookup"><span data-stu-id="7464d-132">Example</span></span>  

 <span data-ttu-id="7464d-133">次の例は、DEVPATH 環境変数によって指定されたディレクトリ内のアセンブリをランタイムが検索する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7464d-133">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7464d-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="7464d-134">See also</span></span>

- [<span data-ttu-id="7464d-135">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="7464d-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7464d-136">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="7464d-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7464d-137">方法: DEVPATH を使用してアセンブリを指定する</span><span class="sxs-lookup"><span data-stu-id="7464d-137">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
