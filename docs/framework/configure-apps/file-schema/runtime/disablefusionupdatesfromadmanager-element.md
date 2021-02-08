---
description: '詳細情報: <disableFusionUpdatesFromADManager> 要素'
title: <disableFusionUpdatesFromADManager> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: c3b5758a12fc78c67ec0a4a9631361808724e72a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787085"
---
# <a name="disablefusionupdatesfromadmanager-element"></a><span data-ttu-id="26fc4-103">\<disableFusionUpdatesFromADManager> 要素</span><span class="sxs-lookup"><span data-stu-id="26fc4-103">\<disableFusionUpdatesFromADManager> Element</span></span>

<span data-ttu-id="26fc4-104">アプリケーション ドメインの構成設定をランタイム ホストがオーバーライドする既定の動作を無効化するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="26fc4-104">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**  
  
## <a name="syntax"></a><span data-ttu-id="26fc4-105">構文</span><span class="sxs-lookup"><span data-stu-id="26fc4-105">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26fc4-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="26fc4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="26fc4-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="26fc4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26fc4-108">属性</span><span class="sxs-lookup"><span data-stu-id="26fc4-108">Attributes</span></span>  
  
|<span data-ttu-id="26fc4-109">属性</span><span class="sxs-lookup"><span data-stu-id="26fc4-109">Attribute</span></span>|<span data-ttu-id="26fc4-110">説明</span><span class="sxs-lookup"><span data-stu-id="26fc4-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26fc4-111">enabled</span><span class="sxs-lookup"><span data-stu-id="26fc4-111">enabled</span></span>|<span data-ttu-id="26fc4-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="26fc4-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="26fc4-113">Fusion 設定をオーバーライドする既定の機能が無効になっているかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="26fc4-113">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="26fc4-114">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="26fc4-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="26fc4-115">値</span><span class="sxs-lookup"><span data-stu-id="26fc4-115">Value</span></span>|<span data-ttu-id="26fc4-116">説明</span><span class="sxs-lookup"><span data-stu-id="26fc4-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="26fc4-117">0</span><span class="sxs-lookup"><span data-stu-id="26fc4-117">0</span></span>|<span data-ttu-id="26fc4-118">Fusion の設定をオーバーライドする機能を無効にしないでください。</span><span class="sxs-lookup"><span data-stu-id="26fc4-118">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="26fc4-119">これは、.NET Framework 4 から始まる既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="26fc4-119">This is the default behavior, starting with the .NET Framework 4.</span></span>|  
|<span data-ttu-id="26fc4-120">1</span><span class="sxs-lookup"><span data-stu-id="26fc4-120">1</span></span>|<span data-ttu-id="26fc4-121">Fusion の設定をオーバーライドする機能を無効にします。</span><span class="sxs-lookup"><span data-stu-id="26fc4-121">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="26fc4-122">これにより、.NET Framework の以前のバージョンの動作に戻ります。</span><span class="sxs-lookup"><span data-stu-id="26fc4-122">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26fc4-123">子要素</span><span class="sxs-lookup"><span data-stu-id="26fc4-123">Child Elements</span></span>  

 <span data-ttu-id="26fc4-124">なし。</span><span class="sxs-lookup"><span data-stu-id="26fc4-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="26fc4-125">親要素</span><span class="sxs-lookup"><span data-stu-id="26fc4-125">Parent Elements</span></span>  
  
|<span data-ttu-id="26fc4-126">要素</span><span class="sxs-lookup"><span data-stu-id="26fc4-126">Element</span></span>|<span data-ttu-id="26fc4-127">説明</span><span class="sxs-lookup"><span data-stu-id="26fc4-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="26fc4-128">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="26fc4-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="26fc4-129">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="26fc4-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26fc4-130">解説</span><span class="sxs-lookup"><span data-stu-id="26fc4-130">Remarks</span></span>  

 <span data-ttu-id="26fc4-131">.NET Framework 4 以降の既定の動作では、 <xref:System.AppDomainManager> <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> <xref:System.AppDomainSetup> <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> のサブクラスで、メソッドの実装に渡されるオブジェクトのプロパティまたはメソッドを使用して、オブジェクトが構成設定をオーバーライドできるようにし <xref:System.AppDomainManager> ます。</span><span class="sxs-lookup"><span data-stu-id="26fc4-131">Starting with the .NET Framework 4, the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="26fc4-132">既定のアプリケーションドメインでは、変更した設定によって、アプリケーション構成ファイルで指定された設定が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="26fc4-132">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="26fc4-133">他のアプリケーションドメインで <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> は、メソッドまたはメソッドに渡された構成設定がオーバーライドされ <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="26fc4-133">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="26fc4-134">新しい構成情報を渡すか、null ( `Nothing` Visual Basic) を渡して、渡された構成情報を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="26fc4-134">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="26fc4-135">プロパティとメソッドの両方に構成情報を渡さないでください <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 。</span><span class="sxs-lookup"><span data-stu-id="26fc4-135">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="26fc4-136">構成情報を両方に渡すと、プロパティに渡す情報 <xref:System.AppDomainSetup.ConfigurationFile%2A> は無視されます。これは、メソッドによって <xref:System.AppDomainSetup.SetConfigurationBytes%2A> アプリケーション構成ファイルの構成情報がオーバーライドされるためです。</span><span class="sxs-lookup"><span data-stu-id="26fc4-136">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="26fc4-137">プロパティを使用する場合 <xref:System.AppDomainSetup.ConfigurationFile%2A> は、メソッドに null ( `Nothing` Visual Basic) を渡して、メソッド <xref:System.AppDomainSetup.SetConfigurationBytes%2A> またはメソッドの呼び出しで指定された構成バイトを削除でき <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="26fc4-137">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="26fc4-138">構成情報に加えて、、、、、、、、、、、、、 <xref:System.AppDomainSetup> <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.ApplicationName%2A> <xref:System.AppDomainSetup.CachePath%2A> <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowCodeDownload%2A> <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.LoaderOptimization%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> および <xref:System.AppDomainSetup.ShadowCopyFiles%2A> の各メソッドの実装に渡されるオブジェクトの次の設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="26fc4-138">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="26fc4-139">要素を使用する代わりに `<disableFusionUpdatesFromADManager>` 、レジストリ設定を作成するか、環境変数を設定することによって、既定の動作を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="26fc4-139">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="26fc4-140">レジストリで、またはの下にという名前の DWORD 値を作成 `COMPLUS_disableFusionUpdatesFromADManager` `HKCU\Software\Microsoft\.NETFramework` し、値を `HKLM\Software\Microsoft\.NETFramework` 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="26fc4-140">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="26fc4-141">コマンドラインで、環境変数を `COMPLUS_disableFusionUpdatesFromADManager` 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="26fc4-141">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26fc4-142">例</span><span class="sxs-lookup"><span data-stu-id="26fc4-142">Example</span></span>  

 <span data-ttu-id="26fc4-143">要素を使用して Fusion 設定をオーバーライドする機能を無効にする方法を次の例に示し `<disableFusionUpdatesFromADManager>` ます。</span><span class="sxs-lookup"><span data-stu-id="26fc4-143">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="26fc4-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="26fc4-144">See also</span></span>

- [<span data-ttu-id="26fc4-145">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="26fc4-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="26fc4-146">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="26fc4-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="26fc4-147">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="26fc4-147">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
