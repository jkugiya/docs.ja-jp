---
description: '詳細情報: <bypassTrustedAppStrongNames> 要素'
title: <bypassTrustedAppStrongNames> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: d23b9efa19481027480f2a1c7dab22bc97a05e13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719163"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="5c50b-103">\<bypassTrustedAppStrongNames> 要素</span><span class="sxs-lookup"><span data-stu-id="5c50b-103">\<bypassTrustedAppStrongNames> Element</span></span>

<span data-ttu-id="5c50b-104">完全に信頼されているアセンブリでの厳密な名前の検証をバイパスするかどうかを指定し <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="5c50b-104">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**

## <a name="syntax"></a><span data-ttu-id="5c50b-105">構文</span><span class="sxs-lookup"><span data-stu-id="5c50b-105">Syntax</span></span>

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5c50b-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5c50b-106">Attributes and Elements</span></span>

<span data-ttu-id="5c50b-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5c50b-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5c50b-108">属性</span><span class="sxs-lookup"><span data-stu-id="5c50b-108">Attributes</span></span>

|<span data-ttu-id="5c50b-109">属性</span><span class="sxs-lookup"><span data-stu-id="5c50b-109">Attribute</span></span>|<span data-ttu-id="5c50b-110">説明</span><span class="sxs-lookup"><span data-stu-id="5c50b-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="5c50b-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="5c50b-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="5c50b-112">完全に信頼されたアセンブリの厳密な名前の検証を回避するバイパス機能が有効かどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5c50b-112">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="5c50b-113">この機能が有効になっている場合、アセンブリの読み込み時に厳密な名前が正しいかどうかは検証されません。</span><span class="sxs-lookup"><span data-stu-id="5c50b-113">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="5c50b-114">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="5c50b-114">The default is `true`.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="5c50b-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="5c50b-115">enabled Attribute</span></span>

|<span data-ttu-id="5c50b-116">値</span><span class="sxs-lookup"><span data-stu-id="5c50b-116">Value</span></span>|<span data-ttu-id="5c50b-117">説明</span><span class="sxs-lookup"><span data-stu-id="5c50b-117">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="5c50b-118">完全に信頼されたアセンブリの厳密な名前の署名は、アセンブリが完全に信頼されているときには検証されません <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="5c50b-118">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="5c50b-119">既定値です。</span><span class="sxs-lookup"><span data-stu-id="5c50b-119">This is the default.</span></span>|
|`false`|<span data-ttu-id="5c50b-120">完全に信頼されたアセンブリの厳密な名前の署名は、アセンブリが完全信頼に読み込まれるときに検証され <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="5c50b-120">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="5c50b-121">厳密な名前の署名は、署名が正しいかどうかのみを確認します。一致のために別の厳密な名前と比較されることはありません。</span><span class="sxs-lookup"><span data-stu-id="5c50b-121">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5c50b-122">子要素</span><span class="sxs-lookup"><span data-stu-id="5c50b-122">Child Elements</span></span>

<span data-ttu-id="5c50b-123">なし。</span><span class="sxs-lookup"><span data-stu-id="5c50b-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5c50b-124">親要素</span><span class="sxs-lookup"><span data-stu-id="5c50b-124">Parent Elements</span></span>

|<span data-ttu-id="5c50b-125">要素</span><span class="sxs-lookup"><span data-stu-id="5c50b-125">Element</span></span>|<span data-ttu-id="5c50b-126">説明</span><span class="sxs-lookup"><span data-stu-id="5c50b-126">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="5c50b-127">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="5c50b-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="5c50b-128">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5c50b-128">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5c50b-129">解説</span><span class="sxs-lookup"><span data-stu-id="5c50b-129">Remarks</span></span>

<span data-ttu-id="5c50b-130">厳密な名前のバイパス機能を使用すると、完全に信頼されたアセンブリに対する厳密な名前の署名の検証のオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="5c50b-130">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>

<span data-ttu-id="5c50b-131">バイ パス機能は、厳密な名前で署名されていて、次の特性を持つアセンブリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="5c50b-131">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>

- <span data-ttu-id="5c50b-132">証拠なしで完全 <xref:System.Security.Policy.StrongName> に信頼されている (たとえば、 `MyComputer` ゾーン証拠がある)。</span><span class="sxs-lookup"><span data-stu-id="5c50b-132">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>

- <span data-ttu-id="5c50b-133">完全に信頼された <xref:System.AppDomain> に読み込まれる。</span><span class="sxs-lookup"><span data-stu-id="5c50b-133">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="5c50b-134">その <xref:System.AppDomain> の <xref:System.AppDomainSetup.ApplicationBase%2A> プロパティに基づいた場所から読み込まれる。</span><span class="sxs-lookup"><span data-stu-id="5c50b-134">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="5c50b-135">遅延署名されていない。</span><span class="sxs-lookup"><span data-stu-id="5c50b-135">Not delay-signed.</span></span>

> [!NOTE]
> <span data-ttu-id="5c50b-136">レジストリキーを使用して、コンピューター上のすべてのアプリケーションでバイパス機能が無効になっている場合、この構成ファイルの設定は無効です。</span><span class="sxs-lookup"><span data-stu-id="5c50b-136">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="5c50b-137">詳細については、「 [方法: Strong-Name バイパス機能を無効](../../../../standard/assembly/disable-strong-name-bypass-feature.md)にする」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c50b-137">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span></span>

## <a name="example"></a><span data-ttu-id="5c50b-138">例</span><span class="sxs-lookup"><span data-stu-id="5c50b-138">Example</span></span>

<span data-ttu-id="5c50b-139">次の例は、完全に信頼されたアセンブリの厳密な名前の署名を検証する動作を指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5c50b-139">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5c50b-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c50b-140">See also</span></span>

- [<span data-ttu-id="5c50b-141">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="5c50b-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5c50b-142">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="5c50b-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5c50b-143">方法: 厳密な名前のバイパス機能を無効にする</span><span class="sxs-lookup"><span data-stu-id="5c50b-143">How to: Disable the strong-name bypass feature</span></span>](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
