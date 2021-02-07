---
description: '詳細情報: <Parameter> 要素 (.NET Native)'
title: <Parameter> 要素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
ms.openlocfilehash: 53b84027e8393e0a799d9652767d173c2787cd27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662794"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="0a3df-103">\<Parameter> 要素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="0a3df-103">\<Parameter> Element (.NET Native)</span></span>

<span data-ttu-id="0a3df-104">メソッドに渡された引数の型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="0a3df-104">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a3df-105">構文</span><span class="sxs-lookup"><span data-stu-id="0a3df-105">Syntax</span></span>  
  
```xml  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a3df-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0a3df-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0a3df-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a3df-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a3df-108">属性</span><span class="sxs-lookup"><span data-stu-id="0a3df-108">Attributes</span></span>  
  
|<span data-ttu-id="0a3df-109">属性</span><span class="sxs-lookup"><span data-stu-id="0a3df-109">Attribute</span></span>|<span data-ttu-id="0a3df-110">属性の型</span><span class="sxs-lookup"><span data-stu-id="0a3df-110">Attribute type</span></span>|<span data-ttu-id="0a3df-111">[説明]</span><span class="sxs-lookup"><span data-stu-id="0a3df-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="0a3df-112">全般</span><span class="sxs-lookup"><span data-stu-id="0a3df-112">General</span></span>|<span data-ttu-id="0a3df-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="0a3df-113">Required attribute.</span></span> <span data-ttu-id="0a3df-114">パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="0a3df-114">The parameter name.</span></span> <span data-ttu-id="0a3df-115">たとえば、メソッド シグネチャ `String.CompareTo(Object value)` の場合、`Name` 属性の値は "value" です。</span><span class="sxs-lookup"><span data-stu-id="0a3df-115">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="0a3df-116">リフレクション</span><span class="sxs-lookup"><span data-stu-id="0a3df-116">Reflection</span></span>|<span data-ttu-id="0a3df-117">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="0a3df-117">Optional attribute.</span></span> <span data-ttu-id="0a3df-118">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="0a3df-118">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="0a3df-119">リフレクション</span><span class="sxs-lookup"><span data-stu-id="0a3df-119">Reflection</span></span>|<span data-ttu-id="0a3df-120">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="0a3df-120">Optional attribute.</span></span> <span data-ttu-id="0a3df-121">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="0a3df-121">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="0a3df-122">リフレクション</span><span class="sxs-lookup"><span data-stu-id="0a3df-122">Reflection</span></span>|<span data-ttu-id="0a3df-123">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="0a3df-123">Optional attribute.</span></span> <span data-ttu-id="0a3df-124">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="0a3df-124">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="0a3df-125">シリアル化</span><span class="sxs-lookup"><span data-stu-id="0a3df-125">Serialization</span></span>|<span data-ttu-id="0a3df-126">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="0a3df-126">Optional attribute.</span></span> <span data-ttu-id="0a3df-127">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="0a3df-127">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="0a3df-128">シリアル化</span><span class="sxs-lookup"><span data-stu-id="0a3df-128">Serialization</span></span>|<span data-ttu-id="0a3df-129">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="0a3df-129">Optional attribute.</span></span> <span data-ttu-id="0a3df-130"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="0a3df-130">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="0a3df-131">シリアル化</span><span class="sxs-lookup"><span data-stu-id="0a3df-131">Serialization</span></span>|<span data-ttu-id="0a3df-132">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="0a3df-132">Optional attribute.</span></span> <span data-ttu-id="0a3df-133"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="0a3df-133">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="0a3df-134">シリアル化</span><span class="sxs-lookup"><span data-stu-id="0a3df-134">Serialization</span></span>|<span data-ttu-id="0a3df-135">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="0a3df-135">Optional attribute.</span></span> <span data-ttu-id="0a3df-136"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="0a3df-136">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="0a3df-137">Interop</span><span class="sxs-lookup"><span data-stu-id="0a3df-137">Interop</span></span>|<span data-ttu-id="0a3df-138">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="0a3df-138">Optional attribute.</span></span> <span data-ttu-id="0a3df-139">WinRT と COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="0a3df-139">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="0a3df-140">Interop</span><span class="sxs-lookup"><span data-stu-id="0a3df-140">Interop</span></span>|<span data-ttu-id="0a3df-141">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="0a3df-141">Optional attribute.</span></span> <span data-ttu-id="0a3df-142">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="0a3df-142">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="0a3df-143">Interop</span><span class="sxs-lookup"><span data-stu-id="0a3df-143">Interop</span></span>|<span data-ttu-id="0a3df-144">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="0a3df-144">Optional attribute.</span></span> <span data-ttu-id="0a3df-145">値型をネイティブ コードにマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="0a3df-145">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="0a3df-146">Name 属性</span><span class="sxs-lookup"><span data-stu-id="0a3df-146">Name attribute</span></span>  
  
|<span data-ttu-id="0a3df-147">値</span><span class="sxs-lookup"><span data-stu-id="0a3df-147">Value</span></span>|<span data-ttu-id="0a3df-148">説明</span><span class="sxs-lookup"><span data-stu-id="0a3df-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0a3df-149">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="0a3df-149">*parameter_name*</span></span>|<span data-ttu-id="0a3df-150">ポリシーが適用されるメソッド パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="0a3df-150">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="0a3df-151">たとえば、メソッド シグネチャ `String.CompareTo(Object value)` の場合、`Name` 属性の値は "value" です。</span><span class="sxs-lookup"><span data-stu-id="0a3df-151">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="0a3df-152">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="0a3df-152">All other attributes</span></span>  
  
|<span data-ttu-id="0a3df-153">値</span><span class="sxs-lookup"><span data-stu-id="0a3df-153">Value</span></span>|<span data-ttu-id="0a3df-154">説明</span><span class="sxs-lookup"><span data-stu-id="0a3df-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0a3df-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="0a3df-155">*policy_setting*</span></span>|<span data-ttu-id="0a3df-156">このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="0a3df-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="0a3df-157">指定できる値は、`All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="0a3df-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="0a3df-158">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a3df-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a3df-159">子要素</span><span class="sxs-lookup"><span data-stu-id="0a3df-159">Child Elements</span></span>  

 <span data-ttu-id="0a3df-160">なし。</span><span class="sxs-lookup"><span data-stu-id="0a3df-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a3df-161">親要素</span><span class="sxs-lookup"><span data-stu-id="0a3df-161">Parent Elements</span></span>  
  
|<span data-ttu-id="0a3df-162">要素</span><span class="sxs-lookup"><span data-stu-id="0a3df-162">Element</span></span>|<span data-ttu-id="0a3df-163">説明</span><span class="sxs-lookup"><span data-stu-id="0a3df-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="0a3df-164">コンストラクターまたはメソッドにランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="0a3df-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a3df-165">解説</span><span class="sxs-lookup"><span data-stu-id="0a3df-165">Remarks</span></span>  

 <span data-ttu-id="0a3df-166">`<Parameter>`要素は要素の子であり、特定の [\<Method>](method-element-net-native.md) メソッドパラメーターにポリシーを適用するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a3df-166">The `<Parameter>` element is a child of the [\<Method>](method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="0a3df-167">特定のメソッド パラメーターは、型ではなく名前で指定されます。</span><span class="sxs-lookup"><span data-stu-id="0a3df-167">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="0a3df-168">`Activate` や `Dynamic` などのポリシーの種類を表す属性が 1 つ以上必要です。</span><span class="sxs-lookup"><span data-stu-id="0a3df-168">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a3df-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a3df-169">See also</span></span>

- [<span data-ttu-id="0a3df-170">\<Method> 要素</span><span class="sxs-lookup"><span data-stu-id="0a3df-170">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="0a3df-171">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="0a3df-171">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="0a3df-172">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="0a3df-172">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="0a3df-173">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="0a3df-173">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
