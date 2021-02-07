---
description: '詳細情報: <GenericParameter> 要素 (.NET Native)'
title: <GenericParameter> 要素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
ms.openlocfilehash: 57cbb3418289d7da4f25577188299acd55ce6c94
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747830"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="880c3-103">\<GenericParameter> 要素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="880c3-103">\<GenericParameter> Element (.NET Native)</span></span>

<span data-ttu-id="880c3-104">ジェネリック型またはメソッドのパラメーターの型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="880c3-104">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="880c3-105">構文</span><span class="sxs-lookup"><span data-stu-id="880c3-105">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="880c3-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="880c3-106">Attributes and Elements</span></span>  

 <span data-ttu-id="880c3-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="880c3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="880c3-108">属性</span><span class="sxs-lookup"><span data-stu-id="880c3-108">Attributes</span></span>  
  
|<span data-ttu-id="880c3-109">属性</span><span class="sxs-lookup"><span data-stu-id="880c3-109">Attribute</span></span>|<span data-ttu-id="880c3-110">属性の型</span><span class="sxs-lookup"><span data-stu-id="880c3-110">Attribute type</span></span>|<span data-ttu-id="880c3-111">[説明]</span><span class="sxs-lookup"><span data-stu-id="880c3-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="880c3-112">全般</span><span class="sxs-lookup"><span data-stu-id="880c3-112">General</span></span>|<span data-ttu-id="880c3-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="880c3-113">Required attribute.</span></span> <span data-ttu-id="880c3-114">ジェネリック パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="880c3-114">The name of the generic parameter.</span></span> <span data-ttu-id="880c3-115">たとえば、ジェネリック デリゲート <xref:System.Func%603> の場合、デリゲートの戻り値に実行時ポリシーを適用するための `Name` 属性の値は "TResult" です。</span><span class="sxs-lookup"><span data-stu-id="880c3-115">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="880c3-116">リフレクション</span><span class="sxs-lookup"><span data-stu-id="880c3-116">Reflection</span></span>|<span data-ttu-id="880c3-117">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="880c3-117">Optional attribute.</span></span> <span data-ttu-id="880c3-118">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="880c3-118">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="880c3-119">リフレクション</span><span class="sxs-lookup"><span data-stu-id="880c3-119">Reflection</span></span>|<span data-ttu-id="880c3-120">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="880c3-120">Optional attribute.</span></span> <span data-ttu-id="880c3-121">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="880c3-121">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="880c3-122">リフレクション</span><span class="sxs-lookup"><span data-stu-id="880c3-122">Reflection</span></span>|<span data-ttu-id="880c3-123">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="880c3-123">Optional attribute.</span></span> <span data-ttu-id="880c3-124">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="880c3-124">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="880c3-125">シリアル化</span><span class="sxs-lookup"><span data-stu-id="880c3-125">Serialization</span></span>|<span data-ttu-id="880c3-126">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="880c3-126">Optional attribute.</span></span> <span data-ttu-id="880c3-127">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="880c3-127">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="880c3-128">シリアル化</span><span class="sxs-lookup"><span data-stu-id="880c3-128">Serialization</span></span>|<span data-ttu-id="880c3-129">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="880c3-129">Optional attribute.</span></span> <span data-ttu-id="880c3-130"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="880c3-130">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="880c3-131">シリアル化</span><span class="sxs-lookup"><span data-stu-id="880c3-131">Serialization</span></span>|<span data-ttu-id="880c3-132">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="880c3-132">Optional attribute.</span></span> <span data-ttu-id="880c3-133"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="880c3-133">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="880c3-134">シリアル化</span><span class="sxs-lookup"><span data-stu-id="880c3-134">Serialization</span></span>|<span data-ttu-id="880c3-135">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="880c3-135">Optional attribute.</span></span> <span data-ttu-id="880c3-136"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="880c3-136">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="880c3-137">Interop</span><span class="sxs-lookup"><span data-stu-id="880c3-137">Interop</span></span>|<span data-ttu-id="880c3-138">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="880c3-138">Optional attribute.</span></span> <span data-ttu-id="880c3-139">Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="880c3-139">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="880c3-140">Interop</span><span class="sxs-lookup"><span data-stu-id="880c3-140">Interop</span></span>|<span data-ttu-id="880c3-141">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="880c3-141">Optional attribute.</span></span> <span data-ttu-id="880c3-142">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="880c3-142">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="880c3-143">Interop</span><span class="sxs-lookup"><span data-stu-id="880c3-143">Interop</span></span>|<span data-ttu-id="880c3-144">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="880c3-144">Optional attribute.</span></span> <span data-ttu-id="880c3-145">値型をネイティブ コードにマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="880c3-145">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="880c3-146">Name 属性</span><span class="sxs-lookup"><span data-stu-id="880c3-146">Name attribute</span></span>  
  
|<span data-ttu-id="880c3-147">値</span><span class="sxs-lookup"><span data-stu-id="880c3-147">Value</span></span>|<span data-ttu-id="880c3-148">説明</span><span class="sxs-lookup"><span data-stu-id="880c3-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="880c3-149">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="880c3-149">*generic_parameter_name*</span></span>|<span data-ttu-id="880c3-150">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="880c3-150">Required attribute.</span></span> <span data-ttu-id="880c3-151">ジェネリック型パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="880c3-151">The name of the generic type parameter.</span></span> <span data-ttu-id="880c3-152">たとえば、ジェネリック デリゲート <xref:System.Func%603> の場合、*generic_parameter_name* の値 "TResult" によって、デリゲートの戻り値に実行時ポリシーが適用されます。</span><span class="sxs-lookup"><span data-stu-id="880c3-152">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="880c3-153">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="880c3-153">All other attributes</span></span>  
  
|<span data-ttu-id="880c3-154">値</span><span class="sxs-lookup"><span data-stu-id="880c3-154">Value</span></span>|<span data-ttu-id="880c3-155">説明</span><span class="sxs-lookup"><span data-stu-id="880c3-155">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="880c3-156">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="880c3-156">*policy_setting*</span></span>|<span data-ttu-id="880c3-157">このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="880c3-157">The setting to apply to this policy type.</span></span> <span data-ttu-id="880c3-158">指定できる値は、`All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="880c3-158">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="880c3-159">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="880c3-159">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="880c3-160">子要素</span><span class="sxs-lookup"><span data-stu-id="880c3-160">Child Elements</span></span>  

 <span data-ttu-id="880c3-161">なし。</span><span class="sxs-lookup"><span data-stu-id="880c3-161">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="880c3-162">親要素</span><span class="sxs-lookup"><span data-stu-id="880c3-162">Parent Elements</span></span>  
  
|<span data-ttu-id="880c3-163">要素</span><span class="sxs-lookup"><span data-stu-id="880c3-163">Element</span></span>|<span data-ttu-id="880c3-164">説明</span><span class="sxs-lookup"><span data-stu-id="880c3-164">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="880c3-165">コンストラクターまたはメソッドにランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="880c3-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="880c3-166">クラスや構造体など、特定の型にランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="880c3-166">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="880c3-167">解説</span><span class="sxs-lookup"><span data-stu-id="880c3-167">Remarks</span></span>  

 <span data-ttu-id="880c3-168">要素は、 `<GenericParameter>` 要素または要素の子であり、 [\<Method>](method-element-net-native.md) [\<Type>](type-element-net-native.md) ジェネリック型またはメソッドシグネチャで名前によって指定される特定のジェネリック型パラメーターにポリシーを適用するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="880c3-168">The `<GenericParameter>` element is a child of either the [\<Method>](method-element-net-native.md) or [\<Type>](type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="880c3-169">`<GenericParameter>` 要素は、シリアライザーで使用する場合に最も役立ちます。</span><span class="sxs-lookup"><span data-stu-id="880c3-169">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="880c3-170">次の例では、要素を使用して、 `<GenericParameter>` `T` NewtonSoft JSON シリアライザーの [jsonconvert \<T> (String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) メソッドオーバーロードの呼び出しで、型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="880c3-170">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="880c3-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="880c3-171">See also</span></span>

- [<span data-ttu-id="880c3-172">\<Method> 要素</span><span class="sxs-lookup"><span data-stu-id="880c3-172">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="880c3-173">\<Type> 要素</span><span class="sxs-lookup"><span data-stu-id="880c3-173">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="880c3-174">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="880c3-174">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="880c3-175">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="880c3-175">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="880c3-176">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="880c3-176">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
