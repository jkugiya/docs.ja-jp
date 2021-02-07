---
description: '詳細情報: <appDomainManagerAssembly> 要素'
title: <appDomainManagerAssembly> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: fcd461a8c8727679df3974028ddbc4b689c73e5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719306"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="a15aa-103">\<appDomainManagerAssembly> 要素</span><span class="sxs-lookup"><span data-stu-id="a15aa-103">\<appDomainManagerAssembly> Element</span></span>

<span data-ttu-id="a15aa-104">プロセスにおける既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーを提供するアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="a15aa-104">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="a15aa-105">構文</span><span class="sxs-lookup"><span data-stu-id="a15aa-105">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a15aa-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a15aa-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a15aa-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a15aa-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a15aa-108">属性</span><span class="sxs-lookup"><span data-stu-id="a15aa-108">Attributes</span></span>  
  
|<span data-ttu-id="a15aa-109">属性</span><span class="sxs-lookup"><span data-stu-id="a15aa-109">Attribute</span></span>|<span data-ttu-id="a15aa-110">説明</span><span class="sxs-lookup"><span data-stu-id="a15aa-110">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="a15aa-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="a15aa-111">Required attribute.</span></span> <span data-ttu-id="a15aa-112">プロセスの既定のアプリケーションドメインのアプリケーションドメインマネージャーを提供するアセンブリの表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a15aa-112">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a15aa-113">子要素</span><span class="sxs-lookup"><span data-stu-id="a15aa-113">Child Elements</span></span>  

 <span data-ttu-id="a15aa-114">なし。</span><span class="sxs-lookup"><span data-stu-id="a15aa-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a15aa-115">親要素</span><span class="sxs-lookup"><span data-stu-id="a15aa-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a15aa-116">要素</span><span class="sxs-lookup"><span data-stu-id="a15aa-116">Element</span></span>|<span data-ttu-id="a15aa-117">説明</span><span class="sxs-lookup"><span data-stu-id="a15aa-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a15aa-118">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="a15aa-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a15aa-119">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a15aa-119">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a15aa-120">解説</span><span class="sxs-lookup"><span data-stu-id="a15aa-120">Remarks</span></span>  

 <span data-ttu-id="a15aa-121">アプリケーションドメインマネージャーの種類を指定するには、この要素と要素の両方を指定する必要があり [\<appDomainManagerType>](appdomainmanagertype-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="a15aa-121">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="a15aa-122">これらの要素のいずれかが指定されていない場合、もう一方は無視されます。</span><span class="sxs-lookup"><span data-stu-id="a15aa-122">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="a15aa-123">既定のアプリケーションドメインが読み込まれると、 <xref:System.TypeLoadException> 指定したアセンブリが存在しない場合、またはアセンブリに要素によって指定された型が含まれていない場合にがスローされ、 [\<appDomainManagerType>](appdomainmanagertype-element.md) プロセスの開始に失敗します。</span><span class="sxs-lookup"><span data-stu-id="a15aa-123">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="a15aa-124">アセンブリが見つかってもバージョン情報が一致しない場合は、 <xref:System.IO.FileLoadException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="a15aa-124">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="a15aa-125">既定のアプリケーションドメインに対してアプリケーションドメインマネージャーの種類を指定すると、既定のアプリケーションドメインから作成された他のアプリケーションドメインは、アプリケーションドメインマネージャーの種類を継承します。</span><span class="sxs-lookup"><span data-stu-id="a15aa-125">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="a15aa-126">プロパティとプロパティを使用して、 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> 新しいアプリケーションドメインに別のアプリケーションドメインマネージャーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="a15aa-126">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="a15aa-127">アプリケーションドメインマネージャーの種類を指定するには、アプリケーションが完全に信頼されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a15aa-127">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="a15aa-128">(たとえば、デスクトップで実行されているアプリケーションには完全な信頼があります)。アプリケーションが完全に信頼されていない場合は、 <xref:System.TypeLoadException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="a15aa-128">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="a15aa-129">アセンブリ表示名の形式については、プロパティを参照してください <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="a15aa-129">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="a15aa-130">この構成要素は、.NET Framework 4 以降でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a15aa-130">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a15aa-131">例</span><span class="sxs-lookup"><span data-stu-id="a15aa-131">Example</span></span>  

 <span data-ttu-id="a15aa-132">次の例は、プロセスの既定のアプリケーションドメインのアプリケーションドメインマネージャーがアセンブリ内の型であることを指定する方法を示してい `MyMgr` `AdMgrExample` ます。</span><span class="sxs-lookup"><span data-stu-id="a15aa-132">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a15aa-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="a15aa-133">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a15aa-134">\<appDomainManagerType> 要素</span><span class="sxs-lookup"><span data-stu-id="a15aa-134">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="a15aa-135">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="a15aa-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a15aa-136">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="a15aa-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a15aa-137">SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="a15aa-137">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
