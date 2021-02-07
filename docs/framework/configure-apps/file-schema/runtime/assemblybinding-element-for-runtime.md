---
description: '詳細情報: <assemblyBinding> の要素 <runtime>'
title: <runtime> の <assemblyBinding> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
ms.openlocfilehash: a797b541f9f13852234872f1eb2fc68a2eac727d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719228"
---
# <a name="assemblybinding-element-for-runtime"></a><span data-ttu-id="f8658-103">\<runtime> の \<assemblyBinding> 要素</span><span class="sxs-lookup"><span data-stu-id="f8658-103">\<assemblyBinding> Element for \<runtime></span></span>

<span data-ttu-id="f8658-104">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f8658-104">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="f8658-105">構文</span><span class="sxs-lookup"><span data-stu-id="f8658-105">Syntax</span></span>  
  
```xml  
      <assemblyBinding
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8658-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f8658-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f8658-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f8658-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8658-108">属性</span><span class="sxs-lookup"><span data-stu-id="f8658-108">Attributes</span></span>  
  
|<span data-ttu-id="f8658-109">属性</span><span class="sxs-lookup"><span data-stu-id="f8658-109">Attribute</span></span>|<span data-ttu-id="f8658-110">説明</span><span class="sxs-lookup"><span data-stu-id="f8658-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f8658-111">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="f8658-111">**xmlns**</span></span>|<span data-ttu-id="f8658-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="f8658-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="f8658-113">アセンブリのバインディングに必要な XML 名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="f8658-113">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="f8658-114">値として、文字列 "urn:schemas-microsoft-com:asm.v1" を使用します。</span><span class="sxs-lookup"><span data-stu-id="f8658-114">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="f8658-115">**appliesTo**</span><span class="sxs-lookup"><span data-stu-id="f8658-115">**appliesTo**</span></span>|<span data-ttu-id="f8658-116">.NET Framework アセンブリのリダイレクトを適用するランタイムのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="f8658-116">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="f8658-117">このオプションの属性では、.NET Framework バージョン番号を使用して、適用するバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="f8658-117">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="f8658-118">**appliesTo** 属性が指定されていない場合、 **\<assemblyBinding>** 要素は、すべてのバージョンの .NET Framework に適用されます。</span><span class="sxs-lookup"><span data-stu-id="f8658-118">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="f8658-119">**AppliesTo** 属性は .NET Framework バージョン1.1 で導入されました。.NET Framework バージョン1.0 では無視されます。</span><span class="sxs-lookup"><span data-stu-id="f8658-119">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="f8658-120">つまり、**appliesTo** 属性が指定されている場合でも、.NET Framework バージョン1.0 を使用しているときは、すべての **\<assemblyBinding>** 要素が適用されます。</span><span class="sxs-lookup"><span data-stu-id="f8658-120">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8658-121">子要素</span><span class="sxs-lookup"><span data-stu-id="f8658-121">Child Elements</span></span>  
  
|<span data-ttu-id="f8658-122">要素</span><span class="sxs-lookup"><span data-stu-id="f8658-122">Element</span></span>|<span data-ttu-id="f8658-123">説明</span><span class="sxs-lookup"><span data-stu-id="f8658-123">Description</span></span>|  
|-------------|-----------------|  
|[\<dependentAssembly>](dependentassembly-element.md)|<span data-ttu-id="f8658-124">アセンブリのバインディング ポリシーとアセンブリの場所をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="f8658-124">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="f8658-125">**\<dependentAssembly>** アセンブリごとに1つのタグを使用します。</span><span class="sxs-lookup"><span data-stu-id="f8658-125">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[\<probing>](probing-element.md)|<span data-ttu-id="f8658-126">アセンブリの読み込み時に共通言語ランタイムが検索するサブディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="f8658-126">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[\<publisherPolicy>](publisherpolicy-element.md)|<span data-ttu-id="f8658-127">ランタイムが発行元ポリシーを適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f8658-127">Specifies whether the runtime applies publisher policy.</span></span>|  
|[\<qualifyAssembly>](qualifyassembly-element.md)|<span data-ttu-id="f8658-128">部分名が使用された場合に動的に読み込む必要があるアセンブリの完全名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f8658-128">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f8658-129">親要素</span><span class="sxs-lookup"><span data-stu-id="f8658-129">Parent Elements</span></span>  
  
|<span data-ttu-id="f8658-130">要素</span><span class="sxs-lookup"><span data-stu-id="f8658-130">Element</span></span>|<span data-ttu-id="f8658-131">説明</span><span class="sxs-lookup"><span data-stu-id="f8658-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f8658-132">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="f8658-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f8658-133">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f8658-133">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f8658-134">例</span><span class="sxs-lookup"><span data-stu-id="f8658-134">Example</span></span>  

 <span data-ttu-id="f8658-135">あるアセンブリ バージョンを別のバージョンにリダイレクトし、コードベースを提供する例を示します。</span><span class="sxs-lookup"><span data-stu-id="f8658-135">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="f8658-136">次の例は、 **appliesTo** 属性を使用して .NET Framework アセンブリのバインドをリダイレクトする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f8658-136">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8658-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8658-137">See also</span></span>

- [<span data-ttu-id="f8658-138">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="f8658-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f8658-139">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="f8658-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f8658-140">アセンブリ バージョンのリダイレクト</span><span class="sxs-lookup"><span data-stu-id="f8658-140">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
