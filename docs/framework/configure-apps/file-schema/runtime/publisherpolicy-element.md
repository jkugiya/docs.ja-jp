---
description: '詳細情報: <publisherPolicy> 要素'
title: <publisherPolicy> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
ms.openlocfilehash: 35d729d5b195e010a80e7272312f14ac5802001b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802438"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="79365-103">\<publisherPolicy> 要素</span><span class="sxs-lookup"><span data-stu-id="79365-103">\<publisherPolicy> Element</span></span>

<span data-ttu-id="79365-104">ランタイムが発行元ポリシーを適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="79365-104">Specifies whether the runtime applies publisher policy.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="79365-105">構文</span><span class="sxs-lookup"><span data-stu-id="79365-105">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79365-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="79365-106">Attributes and Elements</span></span>  

 <span data-ttu-id="79365-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="79365-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79365-108">属性</span><span class="sxs-lookup"><span data-stu-id="79365-108">Attributes</span></span>  
  
|<span data-ttu-id="79365-109">属性</span><span class="sxs-lookup"><span data-stu-id="79365-109">Attribute</span></span>|<span data-ttu-id="79365-110">説明</span><span class="sxs-lookup"><span data-stu-id="79365-110">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="79365-111">発行者ポリシーを適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="79365-111">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="79365-112">属性の適用</span><span class="sxs-lookup"><span data-stu-id="79365-112">apply Attribute</span></span>  
  
|<span data-ttu-id="79365-113">値</span><span class="sxs-lookup"><span data-stu-id="79365-113">Value</span></span>|<span data-ttu-id="79365-114">説明</span><span class="sxs-lookup"><span data-stu-id="79365-114">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="79365-115">発行者ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="79365-115">Applies publisher policy.</span></span> <span data-ttu-id="79365-116">これは、既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="79365-116">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="79365-117">発行者ポリシーは適用されません。</span><span class="sxs-lookup"><span data-stu-id="79365-117">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79365-118">子要素</span><span class="sxs-lookup"><span data-stu-id="79365-118">Child Elements</span></span>  

<span data-ttu-id="79365-119">なし。</span><span class="sxs-lookup"><span data-stu-id="79365-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79365-120">親要素</span><span class="sxs-lookup"><span data-stu-id="79365-120">Parent Elements</span></span>  
  
|<span data-ttu-id="79365-121">要素</span><span class="sxs-lookup"><span data-stu-id="79365-121">Element</span></span>|<span data-ttu-id="79365-122">説明</span><span class="sxs-lookup"><span data-stu-id="79365-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="79365-123">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="79365-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="79365-124">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="79365-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="79365-125">各アセンブリのバインディング ポリシーとアセンブリの場所をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="79365-125">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="79365-126">`<dependentAssembly>`アセンブリごとに1つの要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="79365-126">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="79365-127">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="79365-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79365-128">解説</span><span class="sxs-lookup"><span data-stu-id="79365-128">Remarks</span></span>  

 <span data-ttu-id="79365-129">コンポーネントベンダーがアセンブリの新しいバージョンをリリースする場合、ベンダーには発行者ポリシーを含めることができるため、以前のバージョンを使用するアプリケーションでは新しいバージョンが使用されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="79365-129">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="79365-130">特定のアセンブリに対して発行者ポリシーを適用するかどうかを指定するには、要素に要素を配置し **\<publisherPolicy>** **\<dependentAssembly>** ます。</span><span class="sxs-lookup"><span data-stu-id="79365-130">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="79365-131">**適用** 属性の既定の設定は **[はい]** です。</span><span class="sxs-lookup"><span data-stu-id="79365-131">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="79365-132">**適用** 属性を [**いいえ** **]** に設定すると、アセンブリの以前のすべての設定がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="79365-132">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="79365-133">アプリケーションが [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) アプリケーション構成ファイルの要素を使用して発行者ポリシーを明示的に無視するためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="79365-133">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="79365-134">権限は、にフラグを設定することによって付与され <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> ます。</span><span class="sxs-lookup"><span data-stu-id="79365-134">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="79365-135">詳細については、「 [アセンブリバインディングリダイレクトのセキュリティアクセス許可](../../assembly-binding-redirection-security-permission.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79365-135">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="79365-136">例</span><span class="sxs-lookup"><span data-stu-id="79365-136">Example</span></span>  

 <span data-ttu-id="79365-137">次の例では、アセンブリの発行者ポリシーをオフにし `myAssembly` ます。</span><span class="sxs-lookup"><span data-stu-id="79365-137">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="79365-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="79365-138">See also</span></span>

- [<span data-ttu-id="79365-139">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="79365-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="79365-140">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="79365-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="79365-141">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="79365-141">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="79365-142">アセンブリ バージョンのリダイレクト</span><span class="sxs-lookup"><span data-stu-id="79365-142">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
