---
description: '詳細情報: <ImpliesType> 要素 (.NET Native)'
title: <ImpliesType> 要素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 6476876f335788a276907fd2aef02d5623382699
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747687"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="24c6c-103">\<ImpliesType> 要素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="24c6c-103">\<ImpliesType> Element (.NET Native)</span></span>

<span data-ttu-id="24c6c-104">型にポリシーを適用します (含んでいる型またはメソッドにそのポリシーが適用されている場合)。</span><span class="sxs-lookup"><span data-stu-id="24c6c-104">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24c6c-105">構文</span><span class="sxs-lookup"><span data-stu-id="24c6c-105">Syntax</span></span>  
  
```xml
<ImpliesType Name="type_name"  
             Activate="policy_type"  
             Browse="policy_type"  
             Dynamic="policy_type"  
             Serialize="policy_type"
             DataContractSerializer="policy_setting"  
             DataContractJsonSerializer="policy_setting"  
             XmlSerializer="policy_setting"  
             MarshalObject="policy_setting"  
             MarshalDelegate="policy_setting"  
             MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24c6c-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="24c6c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="24c6c-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="24c6c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24c6c-108">属性</span><span class="sxs-lookup"><span data-stu-id="24c6c-108">Attributes</span></span>  
  
|<span data-ttu-id="24c6c-109">属性</span><span class="sxs-lookup"><span data-stu-id="24c6c-109">Attribute</span></span>|<span data-ttu-id="24c6c-110">属性の型</span><span class="sxs-lookup"><span data-stu-id="24c6c-110">Attribute type</span></span>|<span data-ttu-id="24c6c-111">[説明]</span><span class="sxs-lookup"><span data-stu-id="24c6c-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="24c6c-112">全般</span><span class="sxs-lookup"><span data-stu-id="24c6c-112">General</span></span>|<span data-ttu-id="24c6c-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="24c6c-113">Required attribute.</span></span> <span data-ttu-id="24c6c-114">型名を指定します。</span><span class="sxs-lookup"><span data-stu-id="24c6c-114">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="24c6c-115">リフレクション</span><span class="sxs-lookup"><span data-stu-id="24c6c-115">Reflection</span></span>|<span data-ttu-id="24c6c-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="24c6c-116">Optional attribute.</span></span> <span data-ttu-id="24c6c-117">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="24c6c-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="24c6c-118">リフレクション</span><span class="sxs-lookup"><span data-stu-id="24c6c-118">Reflection</span></span>|<span data-ttu-id="24c6c-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="24c6c-119">Optional attribute.</span></span> <span data-ttu-id="24c6c-120">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="24c6c-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="24c6c-121">リフレクション</span><span class="sxs-lookup"><span data-stu-id="24c6c-121">Reflection</span></span>|<span data-ttu-id="24c6c-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="24c6c-122">Optional attribute.</span></span> <span data-ttu-id="24c6c-123">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="24c6c-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="24c6c-124">シリアル化</span><span class="sxs-lookup"><span data-stu-id="24c6c-124">Serialization</span></span>|<span data-ttu-id="24c6c-125">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="24c6c-125">Optional attribute.</span></span> <span data-ttu-id="24c6c-126">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="24c6c-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="24c6c-127">シリアル化</span><span class="sxs-lookup"><span data-stu-id="24c6c-127">Serialization</span></span>|<span data-ttu-id="24c6c-128">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="24c6c-128">Optional attribute.</span></span> <span data-ttu-id="24c6c-129"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="24c6c-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="24c6c-130">シリアル化</span><span class="sxs-lookup"><span data-stu-id="24c6c-130">Serialization</span></span>|<span data-ttu-id="24c6c-131">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="24c6c-131">Optional attribute.</span></span> <span data-ttu-id="24c6c-132"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="24c6c-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="24c6c-133">シリアル化</span><span class="sxs-lookup"><span data-stu-id="24c6c-133">Serialization</span></span>|<span data-ttu-id="24c6c-134">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="24c6c-134">Optional attribute.</span></span> <span data-ttu-id="24c6c-135"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="24c6c-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="24c6c-136">Interop</span><span class="sxs-lookup"><span data-stu-id="24c6c-136">Interop</span></span>|<span data-ttu-id="24c6c-137">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="24c6c-137">Optional attribute.</span></span> <span data-ttu-id="24c6c-138">Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="24c6c-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="24c6c-139">Interop</span><span class="sxs-lookup"><span data-stu-id="24c6c-139">Interop</span></span>|<span data-ttu-id="24c6c-140">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="24c6c-140">Optional attribute.</span></span> <span data-ttu-id="24c6c-141">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="24c6c-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="24c6c-142">Interop</span><span class="sxs-lookup"><span data-stu-id="24c6c-142">Interop</span></span>|<span data-ttu-id="24c6c-143">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="24c6c-143">Optional attribute.</span></span> <span data-ttu-id="24c6c-144">値型をネイティブ コードにマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="24c6c-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="24c6c-145">Name 属性</span><span class="sxs-lookup"><span data-stu-id="24c6c-145">Name attribute</span></span>  
  
|<span data-ttu-id="24c6c-146">値</span><span class="sxs-lookup"><span data-stu-id="24c6c-146">Value</span></span>|<span data-ttu-id="24c6c-147">説明</span><span class="sxs-lookup"><span data-stu-id="24c6c-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="24c6c-148">*type_name*</span><span class="sxs-lookup"><span data-stu-id="24c6c-148">*type_name*</span></span>|<span data-ttu-id="24c6c-149">型名。</span><span class="sxs-lookup"><span data-stu-id="24c6c-149">The type name.</span></span> <span data-ttu-id="24c6c-150">この `<ImpliesType>` 要素により表される型がそれを含んでいる `<Type>` 要素と同じ名前空間にある場合、*type_name* には名前空間なしで型の名前を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="24c6c-150">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="24c6c-151">それ以外の場合は、*type_name* には完全修飾型名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="24c6c-151">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="24c6c-152">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="24c6c-152">All other attributes</span></span>  
  
|<span data-ttu-id="24c6c-153">値</span><span class="sxs-lookup"><span data-stu-id="24c6c-153">Value</span></span>|<span data-ttu-id="24c6c-154">説明</span><span class="sxs-lookup"><span data-stu-id="24c6c-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="24c6c-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="24c6c-155">*policy_setting*</span></span>|<span data-ttu-id="24c6c-156">このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="24c6c-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="24c6c-157">指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="24c6c-157">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="24c6c-158">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24c6c-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24c6c-159">子要素</span><span class="sxs-lookup"><span data-stu-id="24c6c-159">Child Elements</span></span>  

 <span data-ttu-id="24c6c-160">なし。</span><span class="sxs-lookup"><span data-stu-id="24c6c-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24c6c-161">親要素</span><span class="sxs-lookup"><span data-stu-id="24c6c-161">Parent Elements</span></span>  
  
|<span data-ttu-id="24c6c-162">要素</span><span class="sxs-lookup"><span data-stu-id="24c6c-162">Element</span></span>|<span data-ttu-id="24c6c-163">説明</span><span class="sxs-lookup"><span data-stu-id="24c6c-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="24c6c-164">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="24c6c-164">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="24c6c-165">構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="24c6c-165">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="24c6c-166">メソッドにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="24c6c-166">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24c6c-167">解説</span><span class="sxs-lookup"><span data-stu-id="24c6c-167">Remarks</span></span>  

 <span data-ttu-id="24c6c-168">`<ImpliesType>` 要素は主にライブラリによる使用を想定しています。</span><span class="sxs-lookup"><span data-stu-id="24c6c-168">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="24c6c-169">これは、次のシナリオに対応します。</span><span class="sxs-lookup"><span data-stu-id="24c6c-169">It addresses the following scenario:</span></span>  
  
- <span data-ttu-id="24c6c-170">ルーチンを 1 つの型にリフレクションする必要がある場合、2 番目の型にもリフレクションする必要がある。</span><span class="sxs-lookup"><span data-stu-id="24c6c-170">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
- <span data-ttu-id="24c6c-171">スタティック分析で必要であると示されないため、2 番目の型の暗黙的なインスタンス化のメタデータをそれ以外の方法で使用できない。</span><span class="sxs-lookup"><span data-stu-id="24c6c-171">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="24c6c-172">最も一般的には、2 つの型は共有型引数を持つジェネリックなインスタンス化です。</span><span class="sxs-lookup"><span data-stu-id="24c6c-172">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="24c6c-173">`<ImpliesType>` 要素は、その親要素により指定される型へのリフレクションが必要な場合、`<ImpliesType>` 要素によって指定される型へのリフレクションも暗黙的に必要になるという前提により定義されました。</span><span class="sxs-lookup"><span data-stu-id="24c6c-173">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="24c6c-174">たとえば、次のリフレクション ディレクティブは、`Explicit<T>` と `Implicit<T>` の 2 つの型に適用されます。</span><span class="sxs-lookup"><span data-stu-id="24c6c-174">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="24c6c-175">このディレクティブは、`Explicit` のインスタンス化に `Dynamic` ポリシー設定が定義されていない場合は効果がありません。</span><span class="sxs-lookup"><span data-stu-id="24c6c-175">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="24c6c-176">たとえば、`Explicit<Int32>` の場合、`Implicit<Int32>` はそのパブリック メンバーをルートとしてインスタンス化され、そのメタデータが動的プログラミングで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="24c6c-176">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="24c6c-177">1 つ以上のシリアライザーに適用される、実際の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="24c6c-177">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="24c6c-178">ディレクティブは、 `IList<`  `>` アプリケーションごとの注釈を必要とせずに、対応する何らかの型に対してリフレクション `List<` を行う必要があるという要件を記述し `>` ます。</span><span class="sxs-lookup"><span data-stu-id="24c6c-178">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="24c6c-179">`<ImpliesType>` 要素は `<Method>` 要素内にも配置できます。これは、ジェネリック メソッドのインスタンス化が型のインスタンス化へのリフレクションを暗黙的に決定する場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="24c6c-179">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="24c6c-180">たとえば、関連付けられている  型と  型と共に、特定のライブラリが動的にアクセスするジェネリック メソッド `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)`<xref:System.Collections.Generic.List%601><xref:System.Array> を考えます。</span><span class="sxs-lookup"><span data-stu-id="24c6c-180">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="24c6c-181">これは次のように表すことができます。</span><span class="sxs-lookup"><span data-stu-id="24c6c-181">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="24c6c-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="24c6c-182">See also</span></span>

- [<span data-ttu-id="24c6c-183">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="24c6c-183">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="24c6c-184">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="24c6c-184">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="24c6c-185">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="24c6c-185">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
