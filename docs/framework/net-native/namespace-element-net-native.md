---
description: '詳細情報: <Namespace> 要素 (.NET Native)'
title: <Namespace> 要素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
ms.openlocfilehash: c24f78d8d9fd59258391e9dd5e59988675163b49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738612"
---
# <a name="namespace-element-net-native"></a><span data-ttu-id="86864-103">\<Namespace> 要素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="86864-103">\<Namespace> Element (.NET Native)</span></span>

<span data-ttu-id="86864-104">指定した名前空間内のすべての型にランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="86864-104">Applies runtime reflection policy to all the types in a specified namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86864-105">構文</span><span class="sxs-lookup"><span data-stu-id="86864-105">Syntax</span></span>  
  
```xml  
<Namespace Name="namespace_name"
           Activate="policy_type"
           Browse="policy_type"  
           Dynamic="policy_setting"  
           Serialize="policy_setting"  
           DataContractSerializer="policy_setting"  
           DataContractJsonSerializer="policy_setting"  
           XmlSerializer="policy_setting"  
           MarshalObject="policy_setting"  
           MarshalDelegate="policy_setting"  
           MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86864-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="86864-106">Attributes and Elements</span></span>  

 <span data-ttu-id="86864-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="86864-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86864-108">属性</span><span class="sxs-lookup"><span data-stu-id="86864-108">Attributes</span></span>  
  
|<span data-ttu-id="86864-109">属性</span><span class="sxs-lookup"><span data-stu-id="86864-109">Attribute</span></span>|<span data-ttu-id="86864-110">属性の型</span><span class="sxs-lookup"><span data-stu-id="86864-110">Attribute type</span></span>|<span data-ttu-id="86864-111">[説明]</span><span class="sxs-lookup"><span data-stu-id="86864-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="86864-112">全般</span><span class="sxs-lookup"><span data-stu-id="86864-112">General</span></span>|<span data-ttu-id="86864-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="86864-113">Required attribute.</span></span> <span data-ttu-id="86864-114">名前空間の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="86864-114">Specifies the name of the namespace.</span></span>|  
|`Activate`|<span data-ttu-id="86864-115">リフレクション</span><span class="sxs-lookup"><span data-stu-id="86864-115">Reflection</span></span>|<span data-ttu-id="86864-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="86864-116">Optional attribute.</span></span> <span data-ttu-id="86864-117">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="86864-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="86864-118">リフレクション</span><span class="sxs-lookup"><span data-stu-id="86864-118">Reflection</span></span>|<span data-ttu-id="86864-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="86864-119">Optional attribute.</span></span> <span data-ttu-id="86864-120">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="86864-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="86864-121">リフレクション</span><span class="sxs-lookup"><span data-stu-id="86864-121">Reflection</span></span>|<span data-ttu-id="86864-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="86864-122">Optional attribute.</span></span> <span data-ttu-id="86864-123">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="86864-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="86864-124">シリアル化</span><span class="sxs-lookup"><span data-stu-id="86864-124">Serialization</span></span>|<span data-ttu-id="86864-125">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="86864-125">Optional attribute.</span></span> <span data-ttu-id="86864-126">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="86864-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="86864-127">シリアル化</span><span class="sxs-lookup"><span data-stu-id="86864-127">Serialization</span></span>|<span data-ttu-id="86864-128">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="86864-128">Optional attribute.</span></span> <span data-ttu-id="86864-129"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="86864-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="86864-130">シリアル化</span><span class="sxs-lookup"><span data-stu-id="86864-130">Serialization</span></span>|<span data-ttu-id="86864-131">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="86864-131">Optional attribute.</span></span> <span data-ttu-id="86864-132"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="86864-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="86864-133">シリアル化</span><span class="sxs-lookup"><span data-stu-id="86864-133">Serialization</span></span>|<span data-ttu-id="86864-134">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="86864-134">Optional attribute.</span></span> <span data-ttu-id="86864-135"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="86864-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="86864-136">Interop</span><span class="sxs-lookup"><span data-stu-id="86864-136">Interop</span></span>|<span data-ttu-id="86864-137">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="86864-137">Optional attribute.</span></span> <span data-ttu-id="86864-138">Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="86864-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="86864-139">Interop</span><span class="sxs-lookup"><span data-stu-id="86864-139">Interop</span></span>|<span data-ttu-id="86864-140">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="86864-140">Optional attribute.</span></span> <span data-ttu-id="86864-141">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="86864-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="86864-142">Interop</span><span class="sxs-lookup"><span data-stu-id="86864-142">Interop</span></span>|<span data-ttu-id="86864-143">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="86864-143">Optional attribute.</span></span> <span data-ttu-id="86864-144">ネイティブ コードに構造体をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="86864-144">Controls policy for marshaling structures to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="86864-145">Name 属性</span><span class="sxs-lookup"><span data-stu-id="86864-145">Name attribute</span></span>  
  
|<span data-ttu-id="86864-146">値</span><span class="sxs-lookup"><span data-stu-id="86864-146">Value</span></span>|<span data-ttu-id="86864-147">説明</span><span class="sxs-lookup"><span data-stu-id="86864-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86864-148">*namespace_name*</span><span class="sxs-lookup"><span data-stu-id="86864-148">*namespace_name*</span></span>|<span data-ttu-id="86864-149">名前空間の名前。</span><span class="sxs-lookup"><span data-stu-id="86864-149">The namespace name.</span></span> <span data-ttu-id="86864-150">\<Namespace>要素が、、または要素の子である場合 [\<Application>](application-element-net-native.md) [\<Library>](library-element-net-native.md) [\<Assembly>](assembly-element-net-native.md) 、 *namespace_name* は完全修飾名前空間名である必要があります。</span><span class="sxs-lookup"><span data-stu-id="86864-150">If the \<Namespace> element is a child of an [\<Application>](application-element-net-native.md), [\<Library>](library-element-net-native.md), or [\<Assembly>](assembly-element-net-native.md) element, *namespace_name* must be a fully qualified namespace name.</span></span> <span data-ttu-id="86864-151">\<Namespace>要素が別の要素の子である場合 \<Namespace> 、 *namespace_name* は相対名前空間名である必要があります。</span><span class="sxs-lookup"><span data-stu-id="86864-151">If the \<Namespace> element is a child of another \<Namespace> element, *namespace_name* must be a relative namespace name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="86864-152">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="86864-152">All other attributes</span></span>  
  
|<span data-ttu-id="86864-153">値</span><span class="sxs-lookup"><span data-stu-id="86864-153">Value</span></span>|<span data-ttu-id="86864-154">説明</span><span class="sxs-lookup"><span data-stu-id="86864-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86864-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="86864-155">*policy_setting*</span></span>|<span data-ttu-id="86864-156">名前空間内のすべての型について、このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="86864-156">The setting to apply to this policy type for all types in the namespace.</span></span> <span data-ttu-id="86864-157">指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="86864-157">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="86864-158">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86864-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86864-159">子要素</span><span class="sxs-lookup"><span data-stu-id="86864-159">Child Elements</span></span>  
  
|<span data-ttu-id="86864-160">要素</span><span class="sxs-lookup"><span data-stu-id="86864-160">Element</span></span>|<span data-ttu-id="86864-161">説明</span><span class="sxs-lookup"><span data-stu-id="86864-161">Description</span></span>|  
|-------------|-----------------|  
|`<Namespace>`|<span data-ttu-id="86864-162">親名前空間内のすべての型にランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="86864-162">Applies runtime reflection policy to all types in a parent namespace.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="86864-163">型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="86864-163">Applies reflection policy to a type.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="86864-164">構築されたジェネリック型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="86864-164">Applies reflection policy to a constructed generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="86864-165">親要素</span><span class="sxs-lookup"><span data-stu-id="86864-165">Parent Elements</span></span>  
  
|<span data-ttu-id="86864-166">要素</span><span class="sxs-lookup"><span data-stu-id="86864-166">Element</span></span>|<span data-ttu-id="86864-167">説明</span><span class="sxs-lookup"><span data-stu-id="86864-167">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="86864-168">実行時にリフレクションで使用可能なメタデータを持つ、アプリケーション全体の型と型のメンバーのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="86864-168">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="86864-169">要素には、 [\<Application>](application-element-net-native.md) 0 個以上の要素を含めることができ [\<Assembly>](assembly-element-net-native.md) ます。</span><span class="sxs-lookup"><span data-stu-id="86864-169">The [\<Application>](application-element-net-native.md) element can have zero, one, or more [\<Assembly>](assembly-element-net-native.md) elements.</span></span>|  
|[\<Assembly>](assembly-element-net-native.md)|<span data-ttu-id="86864-170">指定したアセンブリ内のすべての型にランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="86864-170">Applies runtime reflection policy to all the types in a specified assembly.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="86864-171">実行時にリフレクションに使用可能なメタデータを持つ型と型のメンバーを含むアセンブリを定義します。</span><span class="sxs-lookup"><span data-stu-id="86864-171">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="86864-172">要素には、 [\<Library>](library-element-net-native.md) 0 個または1個の要素を含めることができ [\<Assembly>](assembly-element-net-native.md) ます。</span><span class="sxs-lookup"><span data-stu-id="86864-172">The [\<Library>](library-element-net-native.md) element can have zero or one [\<Assembly>](assembly-element-net-native.md) element.</span></span>|  
|`<Namespace>`|<span data-ttu-id="86864-173">親名前空間内のすべての型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="86864-173">Applies reflection policy to all types in a parent namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86864-174">解説</span><span class="sxs-lookup"><span data-stu-id="86864-174">Remarks</span></span>  

 <span data-ttu-id="86864-175">`Activate` 属性、`Browse` 属性、`Dynamic`、および `Serialize` 属性はすべて省略可能です。</span><span class="sxs-lookup"><span data-stu-id="86864-175">The `Activate`, `Browse`, `Dynamic`, and `Serialize` attributes are all optional.</span></span> <span data-ttu-id="86864-176">いずれも存在しない場合、`<Namespace>` 要素は子要素のコンテナーとしてのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="86864-176">If none are present, the `<Namespace>` element serves only as a container for child elements.</span></span> <span data-ttu-id="86864-177">存在する場合は、`<Namespace>` 要素は、指定された名前空間内のすべての型にランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="86864-177">If they are present, the `<Namespace>` element applies runtime reflection policy to all the types in the specified namespace.</span></span>  
  
 <span data-ttu-id="86864-178">要素の子である場合 [\<Assembly>](assembly-element-net-native.md) 、要素は、 `<Namespace>` 要素によって定義されたランタイムリフレクションポリシーをオーバーライドし  [\<Assembly>](assembly-element-net-native.md) ます。</span><span class="sxs-lookup"><span data-stu-id="86864-178">When it is a child of the [\<Assembly>](assembly-element-net-native.md) element, the `<Namespace>` element overrides the runtime reflection policy defined by the  [\<Assembly>](assembly-element-net-native.md) element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86864-179">関連項目</span><span class="sxs-lookup"><span data-stu-id="86864-179">See also</span></span>

- [<span data-ttu-id="86864-180">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="86864-180">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="86864-181">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="86864-181">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="86864-182">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="86864-182">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
