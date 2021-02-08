---
description: '詳細情報: <Type> 要素 (.NET Native)'
title: <Type> 要素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
ms.openlocfilehash: 9a0304049c5b8f97c30a85de1c6ed60cde111df1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801944"
---
# <a name="type-element-net-native"></a><span data-ttu-id="7c84d-103">\<Type> 要素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="7c84d-103">\<Type> Element (.NET Native)</span></span>

<span data-ttu-id="7c84d-104">クラスや構造体などの特定の型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-104">Applies runtime policy to a particular type, such as a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="7c84d-105">構文</span><span class="sxs-lookup"><span data-stu-id="7c84d-105">Syntax</span></span>

```xml
<Type Name="type_name"
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

## <a name="attributes-and-elements"></a><span data-ttu-id="7c84d-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7c84d-106">Attributes and Elements</span></span>

<span data-ttu-id="7c84d-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="7c84d-108">属性</span><span class="sxs-lookup"><span data-stu-id="7c84d-108">Attributes</span></span>

|<span data-ttu-id="7c84d-109">属性</span><span class="sxs-lookup"><span data-stu-id="7c84d-109">Attribute</span></span>|<span data-ttu-id="7c84d-110">属性の型</span><span class="sxs-lookup"><span data-stu-id="7c84d-110">Attribute type</span></span>|<span data-ttu-id="7c84d-111">[説明]</span><span class="sxs-lookup"><span data-stu-id="7c84d-111">Description</span></span>|
|---------------|--------------------|-----------------|
|`Name`|<span data-ttu-id="7c84d-112">全般</span><span class="sxs-lookup"><span data-stu-id="7c84d-112">General</span></span>|<span data-ttu-id="7c84d-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="7c84d-113">Required attribute.</span></span> <span data-ttu-id="7c84d-114">型名を指定します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-114">Specifies the type name.</span></span>|
|`Activate`|<span data-ttu-id="7c84d-115">リフレクション</span><span class="sxs-lookup"><span data-stu-id="7c84d-115">Reflection</span></span>|<span data-ttu-id="7c84d-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7c84d-116">Optional attribute.</span></span> <span data-ttu-id="7c84d-117">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="7c84d-117">Controls runtime access to constructors to enable activation of instances.</span></span>|
|`Browse`|<span data-ttu-id="7c84d-118">リフレクション</span><span class="sxs-lookup"><span data-stu-id="7c84d-118">Reflection</span></span>|<span data-ttu-id="7c84d-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7c84d-119">Optional attribute.</span></span> <span data-ttu-id="7c84d-120">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="7c84d-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|
|`Dynamic`|<span data-ttu-id="7c84d-121">リフレクション</span><span class="sxs-lookup"><span data-stu-id="7c84d-121">Reflection</span></span>|<span data-ttu-id="7c84d-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7c84d-122">Optional attribute.</span></span> <span data-ttu-id="7c84d-123">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="7c84d-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|
|`Serialize`|<span data-ttu-id="7c84d-124">シリアル化</span><span class="sxs-lookup"><span data-stu-id="7c84d-124">Serialization</span></span>|<span data-ttu-id="7c84d-125">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7c84d-125">Optional attribute.</span></span> <span data-ttu-id="7c84d-126">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="7c84d-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|
|`DataContractSerializer`|<span data-ttu-id="7c84d-127">シリアル化</span><span class="sxs-lookup"><span data-stu-id="7c84d-127">Serialization</span></span>|<span data-ttu-id="7c84d-128">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7c84d-128">Optional attribute.</span></span> <span data-ttu-id="7c84d-129"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|
|`DataContractJsonSerializer`|<span data-ttu-id="7c84d-130">シリアル化</span><span class="sxs-lookup"><span data-stu-id="7c84d-130">Serialization</span></span>|<span data-ttu-id="7c84d-131">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7c84d-131">Optional attribute.</span></span> <span data-ttu-id="7c84d-132"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|
|`XmlSerializer`|<span data-ttu-id="7c84d-133">シリアル化</span><span class="sxs-lookup"><span data-stu-id="7c84d-133">Serialization</span></span>|<span data-ttu-id="7c84d-134">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7c84d-134">Optional attribute.</span></span> <span data-ttu-id="7c84d-135"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|
|`MarshalObject`|<span data-ttu-id="7c84d-136">Interop</span><span class="sxs-lookup"><span data-stu-id="7c84d-136">Interop</span></span>|<span data-ttu-id="7c84d-137">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7c84d-137">Optional attribute.</span></span> <span data-ttu-id="7c84d-138">Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|
|`MarshalDelegate`|<span data-ttu-id="7c84d-139">Interop</span><span class="sxs-lookup"><span data-stu-id="7c84d-139">Interop</span></span>|<span data-ttu-id="7c84d-140">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7c84d-140">Optional attribute.</span></span> <span data-ttu-id="7c84d-141">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|
|`MarshalStructure`|<span data-ttu-id="7c84d-142">Interop</span><span class="sxs-lookup"><span data-stu-id="7c84d-142">Interop</span></span>|<span data-ttu-id="7c84d-143">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7c84d-143">Optional attribute.</span></span> <span data-ttu-id="7c84d-144">値型をネイティブ コードにマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-144">Controls policy for marshaling value types to native code.</span></span>|

## <a name="name-attribute"></a><span data-ttu-id="7c84d-145">Name 属性</span><span class="sxs-lookup"><span data-stu-id="7c84d-145">Name attribute</span></span>

|<span data-ttu-id="7c84d-146">値</span><span class="sxs-lookup"><span data-stu-id="7c84d-146">Value</span></span>|<span data-ttu-id="7c84d-147">説明</span><span class="sxs-lookup"><span data-stu-id="7c84d-147">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="7c84d-148">*type_name*</span><span class="sxs-lookup"><span data-stu-id="7c84d-148">*type_name*</span></span>|<span data-ttu-id="7c84d-149">型名。</span><span class="sxs-lookup"><span data-stu-id="7c84d-149">The type name.</span></span> <span data-ttu-id="7c84d-150">この `<Type>` 要素が要素または別の要素のいずれかの子である場合 [\<Namespace>](namespace-element-net-native.md) `<Type>` 、 *type_name* は名前空間なしで型の名前を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7c84d-150">If this `<Type>` element is the child of either a [\<Namespace>](namespace-element-net-native.md) element or another `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="7c84d-151">それ以外の場合は、*type_name* には完全修飾型名を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c84d-151">Otherwise, *type_name* must include the fully qualified type name.</span></span>|

## <a name="all-other-attributes"></a><span data-ttu-id="7c84d-152">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="7c84d-152">All other attributes</span></span>

|<span data-ttu-id="7c84d-153">値</span><span class="sxs-lookup"><span data-stu-id="7c84d-153">Value</span></span>|<span data-ttu-id="7c84d-154">説明</span><span class="sxs-lookup"><span data-stu-id="7c84d-154">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="7c84d-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="7c84d-155">*policy_setting*</span></span>|<span data-ttu-id="7c84d-156">このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="7c84d-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="7c84d-157">指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="7c84d-157">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="7c84d-158">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c84d-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|

### <a name="child-elements"></a><span data-ttu-id="7c84d-159">子要素</span><span class="sxs-lookup"><span data-stu-id="7c84d-159">Child Elements</span></span>

|<span data-ttu-id="7c84d-160">要素</span><span class="sxs-lookup"><span data-stu-id="7c84d-160">Element</span></span>|<span data-ttu-id="7c84d-161">説明</span><span class="sxs-lookup"><span data-stu-id="7c84d-161">Description</span></span>|
|-------------|-----------------|
|[\<AttributeImplies>](attributeimplies-element-net-native.md)|<span data-ttu-id="7c84d-162">含んでいる型が属性の場合は、その属性が適用されるコード要素の実行時ポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-162">If the containing type is an attribute, defines runtime policy for code elements to which the attribute is applied.</span></span>|
|[\<Event>](event-element-net-native.md)|<span data-ttu-id="7c84d-163">この型に属するイベントにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-163">Applies reflection policy to an event belonging to this type.</span></span>|
|[\<Field>](field-element-net-native.md)|<span data-ttu-id="7c84d-164">この型に属するフィールドにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-164">Applies reflection policy to a field belonging to this type.</span></span>|
|[\<GenericParameter>](genericparameter-element-net-native.md)|<span data-ttu-id="7c84d-165">ジェネリック型のパラメーターの型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-165">Applies policy to the parameter type of a generic type.</span></span>|
|[\<ImpliesType>](impliestype-element-net-native.md)|<span data-ttu-id="7c84d-166">型にポリシーを適用します (それを含む `<Type>` 要素により表される型にそのポリシーが適用されている場合)。</span><span class="sxs-lookup"><span data-stu-id="7c84d-166">Applies policy to a type, if that policy has been applied to the type represented by the containing `<Type>` element.</span></span>|
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="7c84d-167">この型に属するメソッドにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-167">Applies reflection policy to a method belonging to this type.</span></span>|
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|<span data-ttu-id="7c84d-168">この型に属する構築されたジェネリック メソッドにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-168">Applies reflection policy to a constructed generic method belonging to this type.</span></span>|
|[\<Property>](property-element-net-native.md)|<span data-ttu-id="7c84d-169">この型に属するプロパティにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-169">Applies reflection policy to a property belonging to this type.</span></span>|
|[\<Subtypes>](subtypes-element-net-native.md)|<span data-ttu-id="7c84d-170">それを含む型から継承されたすべてのクラスに実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-170">Applies runtime policy to all classes inherited from the containing type.</span></span>|
|`<Type>`|<span data-ttu-id="7c84d-171">入れ子になった型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-171">Applies reflection policy to a nested type.</span></span>|
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="7c84d-172">構築されたジェネリック型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-172">Applies reflection policy to a constructed generic type.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7c84d-173">親要素</span><span class="sxs-lookup"><span data-stu-id="7c84d-173">Parent Elements</span></span>

|<span data-ttu-id="7c84d-174">要素</span><span class="sxs-lookup"><span data-stu-id="7c84d-174">Element</span></span>|<span data-ttu-id="7c84d-175">説明</span><span class="sxs-lookup"><span data-stu-id="7c84d-175">Description</span></span>|
|-------------|-----------------|
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="7c84d-176">実行時にリフレクションで使用可能なメタデータを持つ、アプリケーション全体の型と型のメンバーのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-176">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span>|
|[\<Assembly>](assembly-element-net-native.md)|<span data-ttu-id="7c84d-177">指定したアセンブリ内のすべての型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-177">Applies reflection policy to all the types in a specified assembly.</span></span>|
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="7c84d-178">実行時にリフレクションに使用可能なメタデータを持つ型と型のメンバーを含むアセンブリを定義します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-178">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>|
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="7c84d-179">名前空間内のすべての型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-179">Applies reflection policy to all the types in a namespace.</span></span>|
|`<Type>`|<span data-ttu-id="7c84d-180">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-180">Applies reflection policy to a type and all its members.</span></span>|
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="7c84d-181">構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-181">Applies reflection policy to a constructed generic type and all its members.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7c84d-182">解説</span><span class="sxs-lookup"><span data-stu-id="7c84d-182">Remarks</span></span>

<span data-ttu-id="7c84d-183">リフレクション、シリアル化、および相互運用属性はすべて省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7c84d-183">The reflection, serialization, and interop attributes are all optional.</span></span> <span data-ttu-id="7c84d-184">いずれも存在しない場合、`<Type>` 要素は、その子型が個々のメンバーのポリシーを定義するコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-184">If none are present, the `<Type>` element serves as a container whose child types define policy for individual members.</span></span>

<span data-ttu-id="7c84d-185">`<Type>`要素が、、、または要素の子である場合は、 [\<Assembly>](assembly-element-net-native.md) [\<Namespace>](namespace-element-net-native.md) `<Type>` [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 親要素によって定義されたポリシー設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="7c84d-185">If a `<Type>` element is the child of an [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), `<Type>`, or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element, it overrides the policy settings defined by the parent element.</span></span>

<span data-ttu-id="7c84d-186">ジェネリック型の `<Type>` 要素は、独自のポリシーを持たないすべてのインスタンス化にそのポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-186">A `<Type>` element of a generic type applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="7c84d-187">構築されたジェネリック型のポリシーは、要素によって定義され [\<TypeInstantiation>](typeinstantiation-element-net-native.md) ます。</span><span class="sxs-lookup"><span data-stu-id="7c84d-187">The policy of constructed generic types is defined by the [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>

<span data-ttu-id="7c84d-188">型がジェネリック型の場合、アクサン グラーブ記号 (\`) の後ろにジェネリック パラメーターの数を付けたもので名前が修飾されます。</span><span class="sxs-lookup"><span data-stu-id="7c84d-188">If the type is a generic type, its name is decorated by a grave accent symbol (\`) followed by its number of generic parameters.</span></span> <span data-ttu-id="7c84d-189">たとえば、`Name` クラスの `<Type>` 要素の <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 属性は、``Name="System.Collections.Generic.List`1"`` と示されます。</span><span class="sxs-lookup"><span data-stu-id="7c84d-189">For example, the `Name` attribute of a `<Type>` element for the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> class appears as ``Name="System.Collections.Generic.List`1"``.</span></span>

## <a name="example"></a><span data-ttu-id="7c84d-190">例</span><span class="sxs-lookup"><span data-stu-id="7c84d-190">Example</span></span>

<span data-ttu-id="7c84d-191">次の例では、リフレクションを使用して、<xref:System.Collections.Generic.List%601?displayProperty=nameWithType> クラスのフィールド、プロパティ、およびメソッドに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-191">The following example uses reflection to display information about the fields, properties, and methods of the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="7c84d-192">この例の変数 `b` は、 <xref:Windows.UI.Xaml.Controls.TextBlock> コントロールです。</span><span class="sxs-lookup"><span data-stu-id="7c84d-192">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span> <span data-ttu-id="7c84d-193">この例は単に型情報を取得するのみであるため、メタデータの可用性は `Browse` ポリシー設定により制御されます。</span><span class="sxs-lookup"><span data-stu-id="7c84d-193">Because the example simply retrieves type information, the availability of metadata is controlled by the `Browse` policy setting.</span></span>

 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]

 <span data-ttu-id="7c84d-194">クラスのメタデータは <xref:System.Collections.Generic.List%601> .NET Native ツールチェーンによって自動的に含まれないため、この例では、要求されたメンバー情報を実行時に表示できません。</span><span class="sxs-lookup"><span data-stu-id="7c84d-194">Because metadata for the <xref:System.Collections.Generic.List%601> class isn't automatically included by the .NET Native tool chain, the example fails to display the requested member information at run time.</span></span> <span data-ttu-id="7c84d-195">必要なメタデータを提供するには、次の `<Type>` 要素をランタイム ディレクティブ ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-195">To provide the necessary metadata, add the following `<Type>` element to the runtime directives file.</span></span> <span data-ttu-id="7c84d-196">親要素 [<Namespace\>](namespace-element-net-native.md) を指定しているため、`<Type>` 要素で完全修飾型名を指定する必要はないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7c84d-196">Note that, because we've provided a parent [<Namespace\>](namespace-element-net-native.md) element, we don't have to provide a fully qualified type name in the `<Type>` element.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="*Application*" Dynamic="Required All" />
      <Namespace Name ="System.Collections.Generic" >
        <Type Name="List`1" Browse="Required All" />
     </Namespace>
   </Application>
</Directives>
```

## <a name="example"></a><span data-ttu-id="7c84d-197">例</span><span class="sxs-lookup"><span data-stu-id="7c84d-197">Example</span></span>

 <span data-ttu-id="7c84d-198">次の例では、リフレクションを使用して、<xref:System.Reflection.PropertyInfo> プロパティを表す <xref:System.String.Chars%2A?displayProperty=nameWithType> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-198">The following example uses reflection to retrieve a <xref:System.Reflection.PropertyInfo> object that represents the <xref:System.String.Chars%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="7c84d-199">続けて、<xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> メソッドを使用して文字列の 7 番目の文字の値を取得し、文字列のすべての文字を表示します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-199">It then uses the <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> method to retrieve the value of the seventh character in a string, and to display all the characters in the string.</span></span> <span data-ttu-id="7c84d-200">この例の変数 `b` は、 <xref:Windows.UI.Xaml.Controls.TextBlock> コントロールです。</span><span class="sxs-lookup"><span data-stu-id="7c84d-200">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>

 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]

 <span data-ttu-id="7c84d-201">オブジェクトのメタデータは <xref:System.String> 使用できないため、メソッドの呼び出しでは、 <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> <xref:System.NullReferenceException> .NET Native ツールチェーンを使用してコンパイルしたときに、実行時に例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="7c84d-201">Because metadata for the <xref:System.String> object isn't available, the call to the <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> method throws a <xref:System.NullReferenceException> exception at run time when compiled with the .NET Native tool chain.</span></span> <span data-ttu-id="7c84d-202">例外を排除し、必要なメタデータを提供するには、次の `<Type>` 要素をランタイム ディレクティブ ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="7c84d-202">To eliminate the exception and provide the necessary metadata, add the following `<Type>` element to the runtime directives file:</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Assembly Name="*Application*" Dynamic="Required All" />
    <Type Name="System.String" Dynamic="Required Public"/> -->
  </Application>
</Directives>
```

## <a name="see-also"></a><span data-ttu-id="7c84d-203">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c84d-203">See also</span></span>

- [<span data-ttu-id="7c84d-204">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="7c84d-204">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="7c84d-205">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="7c84d-205">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="7c84d-206">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="7c84d-206">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
