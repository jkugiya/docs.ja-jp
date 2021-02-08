---
description: '詳細情報: <qualifyAssembly> 要素'
title: <qualifyAssembly> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 16891cca40d907d0ca32aea7f610e84305fcd0e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802452"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="ef9b8-103">\<qualifyAssembly> 要素</span><span class="sxs-lookup"><span data-stu-id="ef9b8-103">\<qualifyAssembly> Element</span></span>

<span data-ttu-id="ef9b8-104">部分名が使用された場合に動的に読み込む必要があるアセンブリの完全名を指定します。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-104">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="ef9b8-105">構文</span><span class="sxs-lookup"><span data-stu-id="ef9b8-105">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef9b8-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ef9b8-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ef9b8-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef9b8-108">属性</span><span class="sxs-lookup"><span data-stu-id="ef9b8-108">Attributes</span></span>  
  
|<span data-ttu-id="ef9b8-109">属性</span><span class="sxs-lookup"><span data-stu-id="ef9b8-109">Attribute</span></span>|<span data-ttu-id="ef9b8-110">説明</span><span class="sxs-lookup"><span data-stu-id="ef9b8-110">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="ef9b8-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="ef9b8-112">コードに表示されるアセンブリの名前の一部を指定します。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-112">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="ef9b8-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ef9b8-114">グローバルアセンブリキャッシュに表示されるアセンブリの完全名を指定します。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-114">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef9b8-115">子要素</span><span class="sxs-lookup"><span data-stu-id="ef9b8-115">Child Elements</span></span>  

 <span data-ttu-id="ef9b8-116">なし。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef9b8-117">親要素</span><span class="sxs-lookup"><span data-stu-id="ef9b8-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ef9b8-118">要素</span><span class="sxs-lookup"><span data-stu-id="ef9b8-118">Element</span></span>|<span data-ttu-id="ef9b8-119">説明</span><span class="sxs-lookup"><span data-stu-id="ef9b8-119">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="ef9b8-120">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-120">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="ef9b8-121">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ef9b8-122">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-122">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef9b8-123">解説</span><span class="sxs-lookup"><span data-stu-id="ef9b8-123">Remarks</span></span>  

 <span data-ttu-id="ef9b8-124"><xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>部分的なアセンブリ名を使用してメソッドを呼び出すと、共通言語ランタイムによって、アプリケーションのベースディレクトリでのみアセンブリが検索されます。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-124">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="ef9b8-125">**\<qualifyAssembly>** アプリケーション構成ファイルの要素を使用してアセンブリの完全な情報 (名前、バージョン、公開キートークン、およびカルチャ) を指定すると、共通言語ランタイムによってグローバルアセンブリキャッシュ内のアセンブリが検索されます。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-125">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="ef9b8-126">**FullName** 属性には、アセンブリ id の4つのフィールド (名前、バージョン、公開キートークン、およびカルチャ) を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-126">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="ef9b8-127">**Partialname** 属性は、アセンブリを部分的に参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-127">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="ef9b8-128">少なくともアセンブリのテキスト名 (最も一般的なケース) を指定する必要がありますが、バージョン、公開キートークン、またはカルチャ (または4つすべての4つの組み合わせを含む) を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-128">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="ef9b8-129">**Partialname** は、呼び出しで指定された名前と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-129">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="ef9b8-130">たとえば、 `"math"` 構成ファイルで **partialname** 属性としてを指定し、コードでを呼び出すことはできません `Assembly.Load("math, Version=3.3.3.3")` 。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-130">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef9b8-131">例</span><span class="sxs-lookup"><span data-stu-id="ef9b8-131">Example</span></span>  

 <span data-ttu-id="ef9b8-132">次の例では、呼び出しを論理的 `Assembly.Load("math")` にに変換し `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")` ます。</span><span class="sxs-lookup"><span data-stu-id="ef9b8-132">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef9b8-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef9b8-133">See also</span></span>

- [<span data-ttu-id="ef9b8-134">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="ef9b8-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ef9b8-135">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="ef9b8-135">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="ef9b8-136">[部分アセンブリ参照](/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ef9b8-136">[Partial Assembly References](/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
