---
description: '詳細情報: <TypeParameter> 要素 (.NET Native)'
title: <TypeParameter> 要素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
ms.openlocfilehash: 182cd62dc0584991b8ef0f5757d6005173d6d7a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803647"
---
# <a name="typeparameter-element-net-native"></a><span data-ttu-id="89417-103">\<TypeParameter> 要素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="89417-103">\<TypeParameter> Element (.NET Native)</span></span>

<span data-ttu-id="89417-104">メソッドに渡される型引数により表される型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="89417-104">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89417-105">構文</span><span class="sxs-lookup"><span data-stu-id="89417-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89417-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="89417-106">Attributes and Elements</span></span>  

 <span data-ttu-id="89417-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="89417-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89417-108">属性</span><span class="sxs-lookup"><span data-stu-id="89417-108">Attributes</span></span>  
  
|<span data-ttu-id="89417-109">属性</span><span class="sxs-lookup"><span data-stu-id="89417-109">Attribute</span></span>|<span data-ttu-id="89417-110">属性の型</span><span class="sxs-lookup"><span data-stu-id="89417-110">Attribute type</span></span>|<span data-ttu-id="89417-111">[説明]</span><span class="sxs-lookup"><span data-stu-id="89417-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="89417-112">全般</span><span class="sxs-lookup"><span data-stu-id="89417-112">General</span></span>|<span data-ttu-id="89417-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="89417-113">Required attribute.</span></span> <span data-ttu-id="89417-114"><xref:System.Type> 型のパラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="89417-114">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="89417-115">たとえば、メソッド シグネチャ `Type.GetInterfaceMap(Type interfaceType)` の場合、`Name` 属性の値は "interfaceType" です。</span><span class="sxs-lookup"><span data-stu-id="89417-115">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="89417-116">リフレクション</span><span class="sxs-lookup"><span data-stu-id="89417-116">Reflection</span></span>|<span data-ttu-id="89417-117">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="89417-117">Optional attribute.</span></span> <span data-ttu-id="89417-118">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="89417-118">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="89417-119">リフレクション</span><span class="sxs-lookup"><span data-stu-id="89417-119">Reflection</span></span>|<span data-ttu-id="89417-120">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="89417-120">Optional attribute.</span></span> <span data-ttu-id="89417-121">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="89417-121">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="89417-122">リフレクション</span><span class="sxs-lookup"><span data-stu-id="89417-122">Reflection</span></span>|<span data-ttu-id="89417-123">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="89417-123">Optional attribute.</span></span> <span data-ttu-id="89417-124">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="89417-124">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="89417-125">シリアル化</span><span class="sxs-lookup"><span data-stu-id="89417-125">Serialization</span></span>|<span data-ttu-id="89417-126">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="89417-126">Optional attribute.</span></span> <span data-ttu-id="89417-127">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="89417-127">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="89417-128">シリアル化</span><span class="sxs-lookup"><span data-stu-id="89417-128">Serialization</span></span>|<span data-ttu-id="89417-129">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="89417-129">Optional attribute.</span></span> <span data-ttu-id="89417-130"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="89417-130">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="89417-131">シリアル化</span><span class="sxs-lookup"><span data-stu-id="89417-131">Serialization</span></span>|<span data-ttu-id="89417-132">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="89417-132">Optional attribute.</span></span> <span data-ttu-id="89417-133"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="89417-133">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="89417-134">シリアル化</span><span class="sxs-lookup"><span data-stu-id="89417-134">Serialization</span></span>|<span data-ttu-id="89417-135">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="89417-135">Optional attribute.</span></span> <span data-ttu-id="89417-136"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="89417-136">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="89417-137">Interop</span><span class="sxs-lookup"><span data-stu-id="89417-137">Interop</span></span>|<span data-ttu-id="89417-138">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="89417-138">Optional attribute.</span></span> <span data-ttu-id="89417-139">Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="89417-139">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="89417-140">Interop</span><span class="sxs-lookup"><span data-stu-id="89417-140">Interop</span></span>|<span data-ttu-id="89417-141">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="89417-141">Optional attribute.</span></span> <span data-ttu-id="89417-142">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="89417-142">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="89417-143">Interop</span><span class="sxs-lookup"><span data-stu-id="89417-143">Interop</span></span>|<span data-ttu-id="89417-144">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="89417-144">Optional attribute.</span></span> <span data-ttu-id="89417-145">値型をネイティブ コードにマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="89417-145">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="89417-146">Name 属性</span><span class="sxs-lookup"><span data-stu-id="89417-146">Name attribute</span></span>  
  
|<span data-ttu-id="89417-147">値</span><span class="sxs-lookup"><span data-stu-id="89417-147">Value</span></span>|<span data-ttu-id="89417-148">説明</span><span class="sxs-lookup"><span data-stu-id="89417-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89417-149">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="89417-149">*parameter_name*</span></span>|<span data-ttu-id="89417-150"><xref:System.Type> 型のパラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="89417-150">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="89417-151">たとえば、メソッド シグネチャ `Type.GetInterfaceMap(Type interfaceType)` の場合、`Name` 属性の値は "interfaceType" です。</span><span class="sxs-lookup"><span data-stu-id="89417-151">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="89417-152">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="89417-152">All other attributes</span></span>  
  
|<span data-ttu-id="89417-153">値</span><span class="sxs-lookup"><span data-stu-id="89417-153">Value</span></span>|<span data-ttu-id="89417-154">説明</span><span class="sxs-lookup"><span data-stu-id="89417-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89417-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="89417-155">*policy_setting*</span></span>|<span data-ttu-id="89417-156">このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="89417-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="89417-157">指定できる値は、`All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="89417-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="89417-158">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89417-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89417-159">子要素</span><span class="sxs-lookup"><span data-stu-id="89417-159">Child Elements</span></span>  

 <span data-ttu-id="89417-160">なし。</span><span class="sxs-lookup"><span data-stu-id="89417-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89417-161">親要素</span><span class="sxs-lookup"><span data-stu-id="89417-161">Parent Elements</span></span>  
  
|<span data-ttu-id="89417-162">要素</span><span class="sxs-lookup"><span data-stu-id="89417-162">Element</span></span>|<span data-ttu-id="89417-163">説明</span><span class="sxs-lookup"><span data-stu-id="89417-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="89417-164">コンストラクターまたはメソッドにランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="89417-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89417-165">解説</span><span class="sxs-lookup"><span data-stu-id="89417-165">Remarks</span></span>  

 <span data-ttu-id="89417-166">要素は、 `<TypeParameter>` [\<Parameter>](parameter-element-net-native.md) 型のパラメーターにのみ適用できる点を除いて、要素に似てい <xref:System.Type> ます。</span><span class="sxs-lookup"><span data-stu-id="89417-166">The `<TypeParameter>` element is similar to the [\<Parameter>](parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="89417-167">これは、実行時に `Name` 属性により指定される型引数で表されるすべての型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="89417-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="89417-168">たとえば、NewtonSoft の JSON シリアライザーには静的 `JsonConvert.DeserializeObject(String value, Type type)` メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="89417-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="89417-169">次のリフレクション ディレクティブは、</span><span class="sxs-lookup"><span data-stu-id="89417-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="89417-170">`type` 引数により表されるランタイム型のメタデータをシリアル化で使用できるようにする必要があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="89417-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="89417-171">これらのランタイム ディレクティブが次のソース コードを含むプロジェクトに適用された場合、</span><span class="sxs-lookup"><span data-stu-id="89417-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="89417-172">リフレクション ディレクティブによって、`StockQuote` 型のメタデータが実行時に NewtonSoft の JSON シリアライザーで使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="89417-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89417-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="89417-173">See also</span></span>

- [<span data-ttu-id="89417-174">\<Method> 要素</span><span class="sxs-lookup"><span data-stu-id="89417-174">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="89417-175">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="89417-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="89417-176">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="89417-176">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="89417-177">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="89417-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
