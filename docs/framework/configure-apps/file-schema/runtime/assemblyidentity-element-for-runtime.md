---
description: '詳細情報: <assemblyIdentity> の要素 <runtime>'
title: <runtime> の <assemblyIdentity> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: d53c4f7f5207fbcf9ad4a8f82667eacc1f57f5e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719189"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="91e49-103">\<runtime> の \<assemblyIdentity> 要素</span><span class="sxs-lookup"><span data-stu-id="91e49-103">\<assemblyIdentity> Element for \<runtime></span></span>

<span data-ttu-id="91e49-104">アセンブリに関する識別情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="91e49-104">Contains identifying information about the assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**  
  
## <a name="syntax"></a><span data-ttu-id="91e49-105">構文</span><span class="sxs-lookup"><span data-stu-id="91e49-105">Syntax</span></span>  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91e49-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="91e49-106">Attributes and Elements</span></span>  

 <span data-ttu-id="91e49-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="91e49-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91e49-108">属性</span><span class="sxs-lookup"><span data-stu-id="91e49-108">Attributes</span></span>  
  
|<span data-ttu-id="91e49-109">属性</span><span class="sxs-lookup"><span data-stu-id="91e49-109">Attribute</span></span>|<span data-ttu-id="91e49-110">説明</span><span class="sxs-lookup"><span data-stu-id="91e49-110">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="91e49-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="91e49-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="91e49-112">アセンブリの名前</span><span class="sxs-lookup"><span data-stu-id="91e49-112">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="91e49-113">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="91e49-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="91e49-114">アセンブリの言語と国/地域を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="91e49-114">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="91e49-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="91e49-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="91e49-116">アセンブリの厳密な名前を指定する16進値。</span><span class="sxs-lookup"><span data-stu-id="91e49-116">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="91e49-117">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="91e49-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="91e49-118">プロセッサ固有のコードを含むアセンブリのプロセッサアーキテクチャを指定する、"x86"、"amd64"、"msil"、または "ia64" のいずれかの値。</span><span class="sxs-lookup"><span data-stu-id="91e49-118">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="91e49-119">値の大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="91e49-119">The values are not case-sensitive.</span></span> <span data-ttu-id="91e49-120">属性に他の値が割り当てられている場合は、 `<assemblyIdentity>` 要素全体が無視されます。</span><span class="sxs-lookup"><span data-stu-id="91e49-120">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="91e49-121">以下を参照してください。<xref:System.Reflection.ProcessorArchitecture></span><span class="sxs-lookup"><span data-stu-id="91e49-121">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="91e49-122">processorArchitecture 属性</span><span class="sxs-lookup"><span data-stu-id="91e49-122">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="91e49-123">値</span><span class="sxs-lookup"><span data-stu-id="91e49-123">Value</span></span>|<span data-ttu-id="91e49-124">説明</span><span class="sxs-lookup"><span data-stu-id="91e49-124">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="91e49-125">AMD x86-64 アーキテクチャのみ。</span><span class="sxs-lookup"><span data-stu-id="91e49-125">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="91e49-126">Intel Itanium アーキテクチャのみ。</span><span class="sxs-lookup"><span data-stu-id="91e49-126">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="91e49-127">プロセッサおよびワードあたりのビット数に関して中立</span><span class="sxs-lookup"><span data-stu-id="91e49-127">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="91e49-128">64ビットプラットフォーム上のネイティブまたは Windows on Windows (WOW) 環境の32ビット x86 プロセッサ。</span><span class="sxs-lookup"><span data-stu-id="91e49-128">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91e49-129">子要素</span><span class="sxs-lookup"><span data-stu-id="91e49-129">Child Elements</span></span>  

 <span data-ttu-id="91e49-130">なし。</span><span class="sxs-lookup"><span data-stu-id="91e49-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91e49-131">親要素</span><span class="sxs-lookup"><span data-stu-id="91e49-131">Parent Elements</span></span>  
  
|<span data-ttu-id="91e49-132">要素</span><span class="sxs-lookup"><span data-stu-id="91e49-132">Element</span></span>|<span data-ttu-id="91e49-133">説明</span><span class="sxs-lookup"><span data-stu-id="91e49-133">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="91e49-134">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="91e49-134">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="91e49-135">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="91e49-135">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="91e49-136">各アセンブリのバインディング ポリシーとアセンブリの場所をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="91e49-136">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="91e49-137">`<dependentAssembly>`アセンブリごとに1つの要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="91e49-137">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="91e49-138">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="91e49-138">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91e49-139">解説</span><span class="sxs-lookup"><span data-stu-id="91e49-139">Remarks</span></span>  

 <span data-ttu-id="91e49-140">すべて **\<dependentAssembly>** の要素には1つ **\<assemblyIdentity>** の子要素が必要です。</span><span class="sxs-lookup"><span data-stu-id="91e49-140">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="91e49-141">`processorArchitecture`属性が存在する場合、要素は、 `<assemblyIdentity>` 対応するプロセッサアーキテクチャを持つアセンブリにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="91e49-141">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="91e49-142">`processorArchitecture`属性が存在しない場合、要素は、 `<assemblyIdentity>` 任意のプロセッサアーキテクチャを持つアセンブリに適用できます。</span><span class="sxs-lookup"><span data-stu-id="91e49-142">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="91e49-143">次の例では、2つの異なる2つのプロセッサアーキテクチャを対象とする同じ名前の2つのアセンブリの構成ファイルを示しています。これらのバージョンは、同期中に保持されていません。X86 プラットフォームでアプリケーションを実行すると、最初の `<assemblyIdentity>` 要素が適用され、もう一方の要素は無視されます。</span><span class="sxs-lookup"><span data-stu-id="91e49-143">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="91e49-144">アプリケーションが x86 または ia64 以外のプラットフォームで実行されている場合は、両方とも無視されます。</span><span class="sxs-lookup"><span data-stu-id="91e49-144">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="91e49-145">属性のない要素が構成ファイルに含まれて `<assemblyIdentity>` `processorArchitecture` おり、プラットフォームに一致する要素が含まれていない場合、属性のない要素 `processorArchitecture` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="91e49-145">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91e49-146">例</span><span class="sxs-lookup"><span data-stu-id="91e49-146">Example</span></span>  

 <span data-ttu-id="91e49-147">次の例は、アセンブリに関する情報を提供する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="91e49-147">The following example shows how to provide information about an assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="91e49-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="91e49-148">See also</span></span>

- [<span data-ttu-id="91e49-149">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="91e49-149">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="91e49-150">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="91e49-150">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="91e49-151">アセンブリ バージョンのリダイレクト</span><span class="sxs-lookup"><span data-stu-id="91e49-151">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
