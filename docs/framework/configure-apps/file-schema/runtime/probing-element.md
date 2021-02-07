---
description: '詳細情報: <probing> 要素'
title: <probing> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
ms.openlocfilehash: 404e53f735ce02c2a3d7911216f834d38e309789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726105"
---
# <a name="probing-element"></a><span data-ttu-id="a08e5-103">\<probing> 要素</span><span class="sxs-lookup"><span data-stu-id="a08e5-103">\<probing> Element</span></span>

<span data-ttu-id="a08e5-104">アセンブリの読み込み時に共通言語ランタイムが検索するアプリケーションの基本サブディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="a08e5-104">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**  
  
## <a name="syntax"></a><span data-ttu-id="a08e5-105">構文</span><span class="sxs-lookup"><span data-stu-id="a08e5-105">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a08e5-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a08e5-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a08e5-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a08e5-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a08e5-108">属性</span><span class="sxs-lookup"><span data-stu-id="a08e5-108">Attributes</span></span>  
  
|<span data-ttu-id="a08e5-109">属性</span><span class="sxs-lookup"><span data-stu-id="a08e5-109">Attribute</span></span>|<span data-ttu-id="a08e5-110">説明</span><span class="sxs-lookup"><span data-stu-id="a08e5-110">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="a08e5-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="a08e5-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="a08e5-112">アセンブリを含む可能性のあるアプリケーションのベースディレクトリのサブディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="a08e5-112">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="a08e5-113">各サブディレクトリをセミコロンで区切ります。</span><span class="sxs-lookup"><span data-stu-id="a08e5-113">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a08e5-114">子要素</span><span class="sxs-lookup"><span data-stu-id="a08e5-114">Child Elements</span></span>  

<span data-ttu-id="a08e5-115">なし。</span><span class="sxs-lookup"><span data-stu-id="a08e5-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a08e5-116">親要素</span><span class="sxs-lookup"><span data-stu-id="a08e5-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a08e5-117">要素</span><span class="sxs-lookup"><span data-stu-id="a08e5-117">Element</span></span>|<span data-ttu-id="a08e5-118">説明</span><span class="sxs-lookup"><span data-stu-id="a08e5-118">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="a08e5-119">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a08e5-119">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="a08e5-120">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="a08e5-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a08e5-121">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a08e5-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a08e5-122">例</span><span class="sxs-lookup"><span data-stu-id="a08e5-122">Example</span></span>  

 <span data-ttu-id="a08e5-123">次の例では、ランタイムがアセンブリを検索するアプリケーションベースのサブディレクトリを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a08e5-123">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a08e5-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="a08e5-124">See also</span></span>

- [<span data-ttu-id="a08e5-125">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="a08e5-125">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="a08e5-126">構成ファイルスキーマ</span><span class="sxs-lookup"><span data-stu-id="a08e5-126">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="a08e5-127">アセンブリの場所を指定します</span><span class="sxs-lookup"><span data-stu-id="a08e5-127">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="a08e5-128">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="a08e5-128">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
