---
description: '詳細情報: <startup> 要素'
title: <startup> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: 82ece56aaa05376237922b3bd54b6f15967adf8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639823"
---
# <a name="startup-element"></a><span data-ttu-id="ca081-103">\<startup> 要素</span><span class="sxs-lookup"><span data-stu-id="ca081-103">\<startup> element</span></span>

<span data-ttu-id="ca081-104">共通言語ランタイムのスタートアップ情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="ca081-104">Specifies common language runtime startup information.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<startup>**  

## <a name="syntax"></a><span data-ttu-id="ca081-105">構文</span><span class="sxs-lookup"><span data-stu-id="ca081-105">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ca081-106">属性と要素</span><span class="sxs-lookup"><span data-stu-id="ca081-106">Attributes and elements</span></span>

 <span data-ttu-id="ca081-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ca081-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca081-108">属性</span><span class="sxs-lookup"><span data-stu-id="ca081-108">Attributes</span></span>

|<span data-ttu-id="ca081-109">属性</span><span class="sxs-lookup"><span data-stu-id="ca081-109">Attribute</span></span>|<span data-ttu-id="ca081-110">説明</span><span class="sxs-lookup"><span data-stu-id="ca081-110">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="ca081-111">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="ca081-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ca081-112">.NET Framework 2.0 ランタイムアクティブ化ポリシーを有効にするか、.NET Framework 4 のアクティブ化ポリシーを使用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ca081-112">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="ca081-113">useLegacyV2RuntimeActivationPolicy 属性</span><span class="sxs-lookup"><span data-stu-id="ca081-113">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="ca081-114">値</span><span class="sxs-lookup"><span data-stu-id="ca081-114">Value</span></span>|<span data-ttu-id="ca081-115">説明</span><span class="sxs-lookup"><span data-stu-id="ca081-115">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="ca081-116">選択したランタイムの .NET Framework 2.0 ランタイムアクティブ化ポリシーを有効にします。これは、CLR バージョン2.0 ではなく、レガシランタイムアクティブ化手法 ( [Corbindtoruntimeex 関数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)など) を構成ファイルから選択されたランタイムにバインドするためです。</span><span class="sxs-lookup"><span data-stu-id="ca081-116">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="ca081-117">したがって、CLR バージョン4以降が構成ファイルから選択されている場合、以前のバージョンの .NET Framework で作成された混合モードアセンブリは、選択した CLR バージョンで読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="ca081-117">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="ca081-118">この値を設定すると、CLR バージョン1.1 または CLR バージョン2.0 を同じプロセスに読み込むことができなくなり、インプロセスサイドバイサイド機能が実質的に無効になります。</span><span class="sxs-lookup"><span data-stu-id="ca081-118">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="ca081-119">.NET Framework 4 以降の既定のアクティブ化ポリシーを使用します。これは、従来のランタイムアクティブ化手法で CLR バージョン1.1 または2.0 をプロセスに読み込むことができるようにするためです。</span><span class="sxs-lookup"><span data-stu-id="ca081-119">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="ca081-120">この値を設定すると、.NET Framework 4 以降でビルドされた場合を除き、混合モードのアセンブリが .NET Framework 4 以降に読み込まれなくなります。</span><span class="sxs-lookup"><span data-stu-id="ca081-120">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="ca081-121">この値は既定値です。</span><span class="sxs-lookup"><span data-stu-id="ca081-121">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ca081-122">子要素</span><span class="sxs-lookup"><span data-stu-id="ca081-122">Child elements</span></span>

|<span data-ttu-id="ca081-123">要素</span><span class="sxs-lookup"><span data-stu-id="ca081-123">Element</span></span>|<span data-ttu-id="ca081-124">説明</span><span class="sxs-lookup"><span data-stu-id="ca081-124">Description</span></span>|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="ca081-125">バージョン 1.0 の共通言語ランタイムのみがアプリケーションでサポートされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="ca081-125">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="ca081-126">ランタイムバージョン1.1 以降でビルドされたアプリケーションでは、要素を使用する必要があり **\<supportedRuntime>** ます。</span><span class="sxs-lookup"><span data-stu-id="ca081-126">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="ca081-127">アプリケーションでサポートされる共通言語ランタイムのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="ca081-127">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ca081-128">親要素</span><span class="sxs-lookup"><span data-stu-id="ca081-128">Parent elements</span></span>

|<span data-ttu-id="ca081-129">要素</span><span class="sxs-lookup"><span data-stu-id="ca081-129">Element</span></span>|<span data-ttu-id="ca081-130">説明</span><span class="sxs-lookup"><span data-stu-id="ca081-130">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="ca081-131">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="ca081-131">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ca081-132">解説</span><span class="sxs-lookup"><span data-stu-id="ca081-132">Remarks</span></span>

 <span data-ttu-id="ca081-133">要素は、 **\<supportedRuntime>** ランタイムのバージョン1.1 以降を使用してビルドされたすべてのアプリケーションで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca081-133">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="ca081-134">ランタイムのバージョン1.0 のみをサポートするようにビルドされたアプリケーションでは、要素を使用する必要があり **\<requiredRuntime>** ます。</span><span class="sxs-lookup"><span data-stu-id="ca081-134">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="ca081-135">Microsoft Internet Explorer でホストされているアプリケーションのスタートアップコードは、 **\<startup>** 要素とその子要素を無視します。</span><span class="sxs-lookup"><span data-stu-id="ca081-135">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="ca081-136">UseLegacyV2RuntimeActivationPolicy 属性</span><span class="sxs-lookup"><span data-stu-id="ca081-136">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="ca081-137">この属性は、アプリケーションが [Corbindtoruntimeex 関数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)などの従来のアクティブ化パスを使用していて、以前のバージョンではなく CLR のバージョン4をアクティブ化する必要がある場合、またはアプリケーションが .NET Framework 4 でビルドされていて、以前のバージョンの .NET Framework でビルドされた混合モードのアセンブリに依存している場合</span><span class="sxs-lookup"><span data-stu-id="ca081-137">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="ca081-138">これらのシナリオでは、属性をに設定 `true` します。</span><span class="sxs-lookup"><span data-stu-id="ca081-138">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="ca081-139">属性をに設定すると、 `true` clr バージョン1.1 または clr バージョン2.0 が同じプロセスに読み込むことができなくなります。つまり、インプロセスサイドバイサイドの機能が実質的に無効になります (「 [COM 相互運用機能の side-by-side 実行](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="ca081-139">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="ca081-140">例</span><span class="sxs-lookup"><span data-stu-id="ca081-140">Example</span></span>

 <span data-ttu-id="ca081-141">次の例は、構成ファイルでランタイムバージョンを指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ca081-141">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<!-- When used with version 1.0 of the .NET Framework runtime -->
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
<!-- When used with version 1.1 (or later) of the runtime -->
<configuration>
   <startup>
      <supportedRuntime version="v1.1.4322"/>
      <supportedRuntime version="v1.0.3705"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ca081-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca081-142">See also</span></span>

- [<span data-ttu-id="ca081-143">スタートアップ設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="ca081-143">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ca081-144">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="ca081-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ca081-145">方法: .NET Framework 4 以降のバージョンをサポートするアプリを構成する</span><span class="sxs-lookup"><span data-stu-id="ca081-145">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="ca081-146">[COM 相互運用機能の side-by-side 実行](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ca081-146">[Side-by-Side Execution for COM Interop](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="ca081-147">インプロセスの side-by-side 実行</span><span class="sxs-lookup"><span data-stu-id="ca081-147">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
