---
description: '詳細情報: <legacyImpersonationPolicy> 要素'
title: <legacyImpersonationPolicy> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
ms.openlocfilehash: 36cc3336e8e3c0196ae20fc749fc2239c35c8584
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782365"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="65da8-103">\<legacyImpersonationPolicy> 要素</span><span class="sxs-lookup"><span data-stu-id="65da8-103">\<legacyImpersonationPolicy> Element</span></span>

<span data-ttu-id="65da8-104">Windows ID が、現在のスレッドの実行コンテキストのフロー設定に関係なく、非同期ポイント間でフローしないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="65da8-104">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="65da8-105">構文</span><span class="sxs-lookup"><span data-stu-id="65da8-105">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65da8-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="65da8-106">Attributes and Elements</span></span>  

 <span data-ttu-id="65da8-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="65da8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65da8-108">属性</span><span class="sxs-lookup"><span data-stu-id="65da8-108">Attributes</span></span>  
  
|<span data-ttu-id="65da8-109">属性</span><span class="sxs-lookup"><span data-stu-id="65da8-109">Attribute</span></span>|<span data-ttu-id="65da8-110">説明</span><span class="sxs-lookup"><span data-stu-id="65da8-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="65da8-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="65da8-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="65da8-112"><xref:System.Security.Principal.WindowsIdentity>現在のスレッドのフロー設定に関係なく、が非同期ポイント間でフローしないように指定し <xref:System.Threading.ExecutionContext> ます。</span><span class="sxs-lookup"><span data-stu-id="65da8-112">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="65da8-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="65da8-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="65da8-114">値</span><span class="sxs-lookup"><span data-stu-id="65da8-114">Value</span></span>|<span data-ttu-id="65da8-115">説明</span><span class="sxs-lookup"><span data-stu-id="65da8-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="65da8-116"><xref:System.Security.Principal.WindowsIdentity> 現在のスレッドのフロー設定に応じて、非同期ポイント間 <xref:System.Threading.ExecutionContext> をフローします。</span><span class="sxs-lookup"><span data-stu-id="65da8-116"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="65da8-117">既定値です。</span><span class="sxs-lookup"><span data-stu-id="65da8-117">This is the default.</span></span>|  
|`true`|<span data-ttu-id="65da8-118"><xref:System.Security.Principal.WindowsIdentity> は、現在のスレッドのフロー設定に関係なく、非同期ポイント間ではフローしません <xref:System.Threading.ExecutionContext> 。</span><span class="sxs-lookup"><span data-stu-id="65da8-118"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65da8-119">子要素</span><span class="sxs-lookup"><span data-stu-id="65da8-119">Child Elements</span></span>  

 <span data-ttu-id="65da8-120">なし。</span><span class="sxs-lookup"><span data-stu-id="65da8-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="65da8-121">親要素</span><span class="sxs-lookup"><span data-stu-id="65da8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="65da8-122">要素</span><span class="sxs-lookup"><span data-stu-id="65da8-122">Element</span></span>|<span data-ttu-id="65da8-123">説明</span><span class="sxs-lookup"><span data-stu-id="65da8-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="65da8-124">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="65da8-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="65da8-125">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="65da8-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65da8-126">解説</span><span class="sxs-lookup"><span data-stu-id="65da8-126">Remarks</span></span>  

 <span data-ttu-id="65da8-127">.NET Framework バージョン1.0 および1.1 では、は <xref:System.Security.Principal.WindowsIdentity> ユーザー定義の非同期ポイント間ではフローしません。</span><span class="sxs-lookup"><span data-stu-id="65da8-127">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="65da8-128">.NET Framework バージョン2.0 以降では、 <xref:System.Threading.ExecutionContext> 現在実行中のスレッドに関する情報を格納するオブジェクトが存在し、アプリケーションドメイン内の非同期ポイント間をフローします。</span><span class="sxs-lookup"><span data-stu-id="65da8-128">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="65da8-129">は、 <xref:System.Security.Principal.WindowsIdentity> この実行コンテキストに含まれているため、非同期ポイント間でもフローします。つまり、権限借用コンテキストが存在する場合は、同様にフローが行われます。</span><span class="sxs-lookup"><span data-stu-id="65da8-129">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="65da8-130">.NET Framework 2.0 以降では、要素を使用して、 `<legacyImpersonationPolicy>`  <xref:System.Security.Principal.WindowsIdentity> が非同期ポイント間でフローしないことを指定できます。</span><span class="sxs-lookup"><span data-stu-id="65da8-130">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65da8-131">共通言語ランタイム (CLR) は、マネージコードの外部で実行される偽装操作 (アンマネージコードへのプラットフォーム呼び出し、Win32 関数への直接呼び出しなど) を使用して実行される偽装操作を認識します。</span><span class="sxs-lookup"><span data-stu-id="65da8-131">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="65da8-132"><xref:System.Security.Principal.WindowsIdentity> `alwaysFlowImpersonationPolicy` 要素が true () に設定されていない限り、非同期のポイント間でフローできるのはマネージオブジェクトだけ `<alwaysFlowImpersonationPolicy enabled="true"/>` です。</span><span class="sxs-lookup"><span data-stu-id="65da8-132">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="65da8-133">要素を true に設定すると、 `alwaysFlowImpersonationPolicy` 偽装がどのように実行されたかに関係なく、Windows id が常に非同期のポイントでフローすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="65da8-133">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="65da8-134">非同期ポイント間でアンマネージ偽装をフローする方法の詳細については、「 [ \<alwaysFlowImpersonationPolicy> 要素](alwaysflowimpersonationpolicy-element.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65da8-134">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="65da8-135">この既定の動作は、次の2つの方法で変更できます。</span><span class="sxs-lookup"><span data-stu-id="65da8-135">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="65da8-136">マネージコード内で、スレッド単位で。</span><span class="sxs-lookup"><span data-stu-id="65da8-136">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="65da8-137"><xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> 、、またはメソッドを使用してとの設定を変更することで、スレッド単位でフローを抑制でき <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="65da8-137">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="65da8-138">アンマネージホストインターフェイスを呼び出して、共通言語ランタイム (CLR) を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="65da8-138">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="65da8-139">アンマネージホストインターフェイス (単純なマネージ実行可能ファイルではなく) を使用して CLR を読み込む場合は、 [Corbindtoruntimeex 関数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) 関数の呼び出しで特別なフラグを指定できます。</span><span class="sxs-lookup"><span data-stu-id="65da8-139">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="65da8-140">プロセス全体で互換モードを有効にするには、 `flags` [Corbindtoruntimeex 関数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) のパラメーターを STARTUP_LEGACY_IMPERSONATION に設定します。</span><span class="sxs-lookup"><span data-stu-id="65da8-140">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="65da8-141">詳細については、 [ \<alwaysFlowImpersonationPolicy> 要素](alwaysflowimpersonationpolicy-element.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65da8-141">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="65da8-142">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="65da8-142">Configuration File</span></span>  

 <span data-ttu-id="65da8-143">.NET Framework アプリケーションでは、この要素はアプリケーション構成ファイルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="65da8-143">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="65da8-144">ASP.NET アプリケーションの場合は、\Microsoft.NET\Framework\vx.x.xxxx ディレクトリにある aspnet.config ファイルで偽装フローを構成でき \<Windows Folder> ます。</span><span class="sxs-lookup"><span data-stu-id="65da8-144">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="65da8-145">既定では、ASP.NET は、次の構成設定を使用して、aspnet.config ファイル内の偽装フローを無効にします。</span><span class="sxs-lookup"><span data-stu-id="65da8-145">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="65da8-146">ASP.NET で、代わりに偽装のフローを許可する場合は、次の構成設定を明示的に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65da8-146">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="65da8-147">例</span><span class="sxs-lookup"><span data-stu-id="65da8-147">Example</span></span>  

 <span data-ttu-id="65da8-148">次の例は、非同期ポイント間で Windows id をフローしない従来の動作を指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="65da8-148">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="65da8-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="65da8-149">See also</span></span>

- [<span data-ttu-id="65da8-150">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="65da8-150">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="65da8-151">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="65da8-151">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="65da8-152">\<alwaysFlowImpersonationPolicy> 要素</span><span class="sxs-lookup"><span data-stu-id="65da8-152">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)
