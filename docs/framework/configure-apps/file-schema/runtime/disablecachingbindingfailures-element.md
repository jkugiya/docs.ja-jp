---
description: '詳細情報: <disableCachingBindingFailures> 要素'
title: <disableCachingBindingFailures> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
ms.openlocfilehash: b1f36f6a8fc7c78a0dc90ecc78ad725b677fdf40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787111"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="7774b-103">\<disableCachingBindingFailures> 要素</span><span class="sxs-lookup"><span data-stu-id="7774b-103">\<disableCachingBindingFailures> Element</span></span>

<span data-ttu-id="7774b-104">プローブによってアセンブリが見つからなかったために発生するバインドエラーのキャッシュを無効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7774b-104">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCachingBindingFailures>**  
  
## <a name="syntax"></a><span data-ttu-id="7774b-105">構文</span><span class="sxs-lookup"><span data-stu-id="7774b-105">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7774b-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7774b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7774b-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7774b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7774b-108">属性</span><span class="sxs-lookup"><span data-stu-id="7774b-108">Attributes</span></span>  
  
|<span data-ttu-id="7774b-109">属性</span><span class="sxs-lookup"><span data-stu-id="7774b-109">Attribute</span></span>|<span data-ttu-id="7774b-110">説明</span><span class="sxs-lookup"><span data-stu-id="7774b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7774b-111">enabled</span><span class="sxs-lookup"><span data-stu-id="7774b-111">enabled</span></span>|<span data-ttu-id="7774b-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="7774b-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="7774b-113">プローブによってアセンブリが見つからなかったために発生するバインドエラーのキャッシュを無効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7774b-113">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7774b-114">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="7774b-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="7774b-115">値</span><span class="sxs-lookup"><span data-stu-id="7774b-115">Value</span></span>|<span data-ttu-id="7774b-116">説明</span><span class="sxs-lookup"><span data-stu-id="7774b-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7774b-117">0</span><span class="sxs-lookup"><span data-stu-id="7774b-117">0</span></span>|<span data-ttu-id="7774b-118">プローブによってアセンブリが見つからなかったために発生するバインドエラーのキャッシュを無効にしないでください。</span><span class="sxs-lookup"><span data-stu-id="7774b-118">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="7774b-119">これは .NET Framework バージョン2.0 以降の既定のバインディング動作です。</span><span class="sxs-lookup"><span data-stu-id="7774b-119">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="7774b-120">1</span><span class="sxs-lookup"><span data-stu-id="7774b-120">1</span></span>|<span data-ttu-id="7774b-121">プローブによってアセンブリが見つからなかったために発生するバインドエラーのキャッシュを無効にします。</span><span class="sxs-lookup"><span data-stu-id="7774b-121">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="7774b-122">この設定は、.NET Framework バージョン1.1 のバインド動作に戻ります。</span><span class="sxs-lookup"><span data-stu-id="7774b-122">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7774b-123">子要素</span><span class="sxs-lookup"><span data-stu-id="7774b-123">Child Elements</span></span>  

 <span data-ttu-id="7774b-124">なし。</span><span class="sxs-lookup"><span data-stu-id="7774b-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7774b-125">親要素</span><span class="sxs-lookup"><span data-stu-id="7774b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="7774b-126">要素</span><span class="sxs-lookup"><span data-stu-id="7774b-126">Element</span></span>|<span data-ttu-id="7774b-127">説明</span><span class="sxs-lookup"><span data-stu-id="7774b-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7774b-128">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="7774b-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7774b-129">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7774b-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7774b-130">解説</span><span class="sxs-lookup"><span data-stu-id="7774b-130">Remarks</span></span>  

 <span data-ttu-id="7774b-131">.NET Framework バージョン2.0 以降では、アセンブリを読み込む既定の動作では、すべてのバインドおよび読み込みエラーがキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="7774b-131">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="7774b-132">つまり、アセンブリの読み込みに失敗した場合、同じアセンブリを読み込むための後続の要求は、アセンブリを特定しなくてもすぐに失敗します。</span><span class="sxs-lookup"><span data-stu-id="7774b-132">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="7774b-133">この要素は、プローブパスにアセンブリが見つからなかったために発生するバインディングエラーの既定の動作を無効にします。</span><span class="sxs-lookup"><span data-stu-id="7774b-133">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="7774b-134">これらのエラーはスロー <xref:System.IO.FileNotFoundException> します。</span><span class="sxs-lookup"><span data-stu-id="7774b-134">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="7774b-135">この要素の影響を受けないバインドと読み込みのエラーもあります。この要素は常にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="7774b-135">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="7774b-136">これらのエラーは、アセンブリが見つかりましたが、読み込むことができなかったことが原因で発生します。</span><span class="sxs-lookup"><span data-stu-id="7774b-136">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="7774b-137"><xref:System.BadImageFormatException>または <xref:System.IO.FileLoadException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="7774b-137">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="7774b-138">このようなエラーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7774b-138">The following list includes some examples of such failures.</span></span>  
  
- <span data-ttu-id="7774b-139">ファイルを読み込もうとしても有効なアセンブリではない場合、不適切なファイルが正しいアセンブリに置き換えられても、その後のアセンブリの読み込み試行は失敗します。</span><span class="sxs-lookup"><span data-stu-id="7774b-139">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
- <span data-ttu-id="7774b-140">ファイルシステムによってロックされているアセンブリを読み込もうとすると、ファイルシステムによってアセンブリが解放された後でも、その後のアセンブリの読み込み試行は失敗します。</span><span class="sxs-lookup"><span data-stu-id="7774b-140">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
- <span data-ttu-id="7774b-141">読み込もうとしているアセンブリの1つまたは複数のバージョンがプローブパスに存在するが、要求している特定のバージョンがそれらの中にない場合は、正しいバージョンがプローブパスに移動されても、そのバージョンを読み込もうとすると失敗します。</span><span class="sxs-lookup"><span data-stu-id="7774b-141">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7774b-142">例</span><span class="sxs-lookup"><span data-stu-id="7774b-142">Example</span></span>  

 <span data-ttu-id="7774b-143">次の例では、プローブによってアセンブリが見つからなかったために発生したアセンブリバインディングエラーのキャッシュを無効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7774b-143">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7774b-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="7774b-144">See also</span></span>

- [<span data-ttu-id="7774b-145">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="7774b-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7774b-146">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="7774b-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7774b-147">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="7774b-147">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
