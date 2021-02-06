---
description: '詳細情報: <requiredRuntime> 要素'
title: <requiredRuntime> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: e9d0a88a65f72ec03f3b2b124920d8265b8bf0c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639849"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="98f1c-103">\<requiredRuntime> 要素</span><span class="sxs-lookup"><span data-stu-id="98f1c-103">\<requiredRuntime> element</span></span>

<span data-ttu-id="98f1c-104">バージョン 1.0 の共通言語ランタイムのみがアプリケーションでサポートされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="98f1c-104">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="98f1c-105">この要素は非推奨とされ、使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="98f1c-105">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="98f1c-106">[`supportedRuntime`](supportedruntime-element.md)代わりに、要素を使用してください。</span><span class="sxs-lookup"><span data-stu-id="98f1c-106">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<startup>**](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**  

## <a name="syntax"></a><span data-ttu-id="98f1c-107">構文</span><span class="sxs-lookup"><span data-stu-id="98f1c-107">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="98f1c-108">属性と要素</span><span class="sxs-lookup"><span data-stu-id="98f1c-108">Attributes and elements</span></span>

<span data-ttu-id="98f1c-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="98f1c-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="98f1c-110">属性</span><span class="sxs-lookup"><span data-stu-id="98f1c-110">Attributes</span></span>

|<span data-ttu-id="98f1c-111">属性</span><span class="sxs-lookup"><span data-stu-id="98f1c-111">Attribute</span></span>|<span data-ttu-id="98f1c-112">説明</span><span class="sxs-lookup"><span data-stu-id="98f1c-112">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="98f1c-113">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="98f1c-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="98f1c-114">このアプリケーションでサポートされている .NET Framework のバージョンを指定する文字列値。</span><span class="sxs-lookup"><span data-stu-id="98f1c-114">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="98f1c-115">文字列値は、.NET Framework のインストールルートの下にあるディレクトリ名と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98f1c-115">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="98f1c-116">文字列値の内容は解析されません。</span><span class="sxs-lookup"><span data-stu-id="98f1c-116">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="98f1c-117">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="98f1c-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="98f1c-118">ランタイムスタートアップコードがレジストリを検索してランタイムバージョンを確認するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="98f1c-118">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="98f1c-119">セーフ属性</span><span class="sxs-lookup"><span data-stu-id="98f1c-119">safemode attribute</span></span>

|<span data-ttu-id="98f1c-120">値</span><span class="sxs-lookup"><span data-stu-id="98f1c-120">Value</span></span>|<span data-ttu-id="98f1c-121">説明</span><span class="sxs-lookup"><span data-stu-id="98f1c-121">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="98f1c-122">ランタイムスタートアップコードによって、レジストリが検索されます。</span><span class="sxs-lookup"><span data-stu-id="98f1c-122">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="98f1c-123">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="98f1c-123">This is the default value.</span></span>|
|`true`|<span data-ttu-id="98f1c-124">ランタイムスタートアップコードでは、レジストリが検索されません。</span><span class="sxs-lookup"><span data-stu-id="98f1c-124">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="98f1c-125">子要素</span><span class="sxs-lookup"><span data-stu-id="98f1c-125">Child elements</span></span>

<span data-ttu-id="98f1c-126">なし。</span><span class="sxs-lookup"><span data-stu-id="98f1c-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="98f1c-127">親要素</span><span class="sxs-lookup"><span data-stu-id="98f1c-127">Parent elements</span></span>

|<span data-ttu-id="98f1c-128">要素</span><span class="sxs-lookup"><span data-stu-id="98f1c-128">Element</span></span>|<span data-ttu-id="98f1c-129">説明</span><span class="sxs-lookup"><span data-stu-id="98f1c-129">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="98f1c-130">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="98f1c-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="98f1c-131">要素が含まれてい `<requiredRuntime>` ます。</span><span class="sxs-lookup"><span data-stu-id="98f1c-131">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="98f1c-132">解説</span><span class="sxs-lookup"><span data-stu-id="98f1c-132">Remarks</span></span>

 <span data-ttu-id="98f1c-133">ランタイムのバージョン1.0 のみをサポートするようにビルドされたアプリケーションでは、要素を使用する必要があり `<requiredRuntime>` ます。</span><span class="sxs-lookup"><span data-stu-id="98f1c-133">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="98f1c-134">ランタイムのバージョン1.1 以降を使用してビルドされたアプリケーションでは、要素を使用する必要があり `<supportedRuntime>` ます。</span><span class="sxs-lookup"><span data-stu-id="98f1c-134">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="98f1c-135">[Corbindtoruntimebycfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)関数を使用して構成ファイルを指定する場合は、すべてのバージョンのランタイムで要素を使用する必要があり `<requiredRuntime>` ます。</span><span class="sxs-lookup"><span data-stu-id="98f1c-135">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="98f1c-136">`<supportedRuntime>` [Corbindtoruntimebycfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)を使用する場合、要素は無視されます。</span><span class="sxs-lookup"><span data-stu-id="98f1c-136">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="98f1c-137">`version`属性文字列は、.NET Framework の指定したバージョンのインストールフォルダー名と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="98f1c-137">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="98f1c-138">この文字列は解釈されません。</span><span class="sxs-lookup"><span data-stu-id="98f1c-138">This string is not interpreted.</span></span> <span data-ttu-id="98f1c-139">ランタイムスタートアップコードが一致するフォルダーを見つけられない場合、ランタイムは読み込まれません。スタートアップコードによってエラーメッセージが表示され、終了します。</span><span class="sxs-lookup"><span data-stu-id="98f1c-139">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="98f1c-140">Microsoft Internet Explorer でホストされているアプリケーションのスタートアップコードは、要素を無視し `<requiredRuntime>` ます。</span><span class="sxs-lookup"><span data-stu-id="98f1c-140">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="98f1c-141">例</span><span class="sxs-lookup"><span data-stu-id="98f1c-141">Example</span></span>

<span data-ttu-id="98f1c-142">次の例は、構成ファイルでランタイムバージョンを指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="98f1c-142">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="98f1c-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="98f1c-143">See also</span></span>

- [<span data-ttu-id="98f1c-144">スタートアップ設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="98f1c-144">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="98f1c-145">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="98f1c-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="98f1c-146">方法: .NET Framework 4 以降のバージョンをサポートするアプリを構成する</span><span class="sxs-lookup"><span data-stu-id="98f1c-146">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
