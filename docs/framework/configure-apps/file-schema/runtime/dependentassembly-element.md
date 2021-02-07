---
description: '詳細情報: <dependentAssembly> 要素'
title: <dependentAssembly> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
ms.openlocfilehash: c804920de961fc609fd04a0853ecbdbc9202e5be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719085"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="2ce4f-103">\<dependentAssembly> 要素</span><span class="sxs-lookup"><span data-stu-id="2ce4f-103">\<dependentAssembly> Element</span></span>

<span data-ttu-id="2ce4f-104">各アセンブリのバインディング ポリシーとアセンブリの場所をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="2ce4f-104">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="2ce4f-105">`dependentAssembly`アセンブリごとに1つの要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="2ce4f-105">Use one `dependentAssembly` element for each assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="2ce4f-106">構文</span><span class="sxs-lookup"><span data-stu-id="2ce4f-106">Syntax</span></span>  
  
```xml  
<dependentAssembly>
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ce4f-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2ce4f-107">Attributes and Elements</span></span>  

 <span data-ttu-id="2ce4f-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ce4f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ce4f-109">属性</span><span class="sxs-lookup"><span data-stu-id="2ce4f-109">Attributes</span></span>  

 <span data-ttu-id="2ce4f-110">なし。</span><span class="sxs-lookup"><span data-stu-id="2ce4f-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2ce4f-111">子要素</span><span class="sxs-lookup"><span data-stu-id="2ce4f-111">Child Elements</span></span>  
  
|<span data-ttu-id="2ce4f-112">要素</span><span class="sxs-lookup"><span data-stu-id="2ce4f-112">Element</span></span>|<span data-ttu-id="2ce4f-113">説明</span><span class="sxs-lookup"><span data-stu-id="2ce4f-113">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="2ce4f-114">アセンブリに関する識別情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="2ce4f-114">Contains identifying information about the assembly.</span></span> <span data-ttu-id="2ce4f-115">この要素は、各要素に含める必要があり `dependentAssembly` ます。</span><span class="sxs-lookup"><span data-stu-id="2ce4f-115">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="2ce4f-116">ランタイムがコンピューターにインストールされていない場合に、共有アセンブリを見つけることができる場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="2ce4f-116">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="2ce4f-117">1 つのアセンブリ バージョンを別のバージョンにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="2ce4f-117">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="2ce4f-118">ランタイムがこのアセンブリの発行者ポリシーを適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2ce4f-118">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2ce4f-119">親要素</span><span class="sxs-lookup"><span data-stu-id="2ce4f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2ce4f-120">要素</span><span class="sxs-lookup"><span data-stu-id="2ce4f-120">Element</span></span>|<span data-ttu-id="2ce4f-121">説明</span><span class="sxs-lookup"><span data-stu-id="2ce4f-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="2ce4f-122">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2ce4f-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="2ce4f-123">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="2ce4f-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2ce4f-124">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2ce4f-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2ce4f-125">例</span><span class="sxs-lookup"><span data-stu-id="2ce4f-125">Example</span></span>  

 <span data-ttu-id="2ce4f-126">次の例は、2つのアセンブリのアセンブリ情報をカプセル化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2ce4f-126">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ce4f-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ce4f-127">See also</span></span>

- [<span data-ttu-id="2ce4f-128">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="2ce4f-128">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2ce4f-129">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="2ce4f-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2ce4f-130">アセンブリ バージョンのリダイレクト</span><span class="sxs-lookup"><span data-stu-id="2ce4f-130">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
