---
description: '詳細情報: <Application> 要素 (.NET Native)'
title: <Application> 要素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
ms.openlocfilehash: ebbc6292b5936e6b7d54666070b33df2da80f57f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747947"
---
# <a name="application-element-net-native"></a><span data-ttu-id="48e54-103">\<Application> 要素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="48e54-103">\<Application> Element (.NET Native)</span></span>

<span data-ttu-id="48e54-104">実行時にリフレクションに使用可能なメタデータを持つアプリケーション全体の型と型のメンバーのコンテナーとして機能し、アプリ内のすべてのプログラム要素にランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="48e54-104">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time, and applies runtime reflection policy to all the program elements in an app.</span></span>  
  
 <span data-ttu-id="48e54-105">\<Directives> 要素</span><span class="sxs-lookup"><span data-stu-id="48e54-105">\<Directives> Element</span></span>  
<span data-ttu-id="48e54-106">\<Application> 要素 (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="48e54-106">\<Application> Element (rd.xml)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48e54-107">構文</span><span class="sxs-lookup"><span data-stu-id="48e54-107">Syntax</span></span>  
  
```xml  
<Application Activate="policy_setting"  
             Browse="policy_setting"  
             Dynamic="policy_setting"  
             Serialize="policy_setting"  
             DataContractSerializer="policy_setting"  
             DataContractJsonSerializer="policy_setting"  
             XmlSerializer="policy_setting"  
             MarshalObject="policy_setting"  
             MarshalDelegate="policy_setting"  
             MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48e54-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="48e54-108">Attributes and Elements</span></span>  

 <span data-ttu-id="48e54-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="48e54-109">The following sections describe attributes, child elements, and parent elements.</span></span> <span data-ttu-id="48e54-110">「子要素」の表では、ポリシーは実行時に特定のプログラム要素で使用可能になるメタデータの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="48e54-110">In the Child Elements table, policy refers to the kind of metadata that is made available for particular program elements at run time.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48e54-111">属性</span><span class="sxs-lookup"><span data-stu-id="48e54-111">Attributes</span></span>  
  
|<span data-ttu-id="48e54-112">属性</span><span class="sxs-lookup"><span data-stu-id="48e54-112">Attribute</span></span>|<span data-ttu-id="48e54-113">属性の型</span><span class="sxs-lookup"><span data-stu-id="48e54-113">Attribute type</span></span>|<span data-ttu-id="48e54-114">説明</span><span class="sxs-lookup"><span data-stu-id="48e54-114">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="48e54-115">リフレクション</span><span class="sxs-lookup"><span data-stu-id="48e54-115">Reflection</span></span>|<span data-ttu-id="48e54-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="48e54-116">Optional attribute.</span></span> <span data-ttu-id="48e54-117">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="48e54-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="48e54-118">リフレクション</span><span class="sxs-lookup"><span data-stu-id="48e54-118">Reflection</span></span>|<span data-ttu-id="48e54-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="48e54-119">Optional attribute.</span></span> <span data-ttu-id="48e54-120">型に関する情報の照会や型の列挙を制御しますが、実行時の動的アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="48e54-120">Controls querying for information about or enumerating the types, but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="48e54-121">リフレクション</span><span class="sxs-lookup"><span data-stu-id="48e54-121">Reflection</span></span>|<span data-ttu-id="48e54-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="48e54-122">Optional attribute.</span></span> <span data-ttu-id="48e54-123">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="48e54-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="48e54-124">シリアル化</span><span class="sxs-lookup"><span data-stu-id="48e54-124">Serialization</span></span>|<span data-ttu-id="48e54-125">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="48e54-125">Optional attribute.</span></span> <span data-ttu-id="48e54-126">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="48e54-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="48e54-127">シリアル化</span><span class="sxs-lookup"><span data-stu-id="48e54-127">Serialization</span></span>|<span data-ttu-id="48e54-128">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="48e54-128">Optional Attribute.</span></span> <span data-ttu-id="48e54-129"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="48e54-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="48e54-130">シリアル化</span><span class="sxs-lookup"><span data-stu-id="48e54-130">Serialization</span></span>|<span data-ttu-id="48e54-131">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="48e54-131">Optional Attribute.</span></span> <span data-ttu-id="48e54-132"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="48e54-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="48e54-133">シリアル化</span><span class="sxs-lookup"><span data-stu-id="48e54-133">Serialization</span></span>|<span data-ttu-id="48e54-134">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="48e54-134">Optional Attribute.</span></span> <span data-ttu-id="48e54-135"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="48e54-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="48e54-136">Interop</span><span class="sxs-lookup"><span data-stu-id="48e54-136">Interop</span></span>|<span data-ttu-id="48e54-137">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="48e54-137">Optional Attribute.</span></span> <span data-ttu-id="48e54-138">Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="48e54-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="48e54-139">Interop</span><span class="sxs-lookup"><span data-stu-id="48e54-139">Interop</span></span>|<span data-ttu-id="48e54-140">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="48e54-140">Optional Attribute.</span></span> <span data-ttu-id="48e54-141">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="48e54-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="48e54-142">Interop</span><span class="sxs-lookup"><span data-stu-id="48e54-142">Interop</span></span>|<span data-ttu-id="48e54-143">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="48e54-143">Optional Attribute.</span></span> <span data-ttu-id="48e54-144">ネイティブ コードに構造体をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="48e54-144">Controls policy for marshaling structures to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="48e54-145">すべての属性</span><span class="sxs-lookup"><span data-stu-id="48e54-145">All attributes</span></span>  
  
|<span data-ttu-id="48e54-146">値</span><span class="sxs-lookup"><span data-stu-id="48e54-146">Value</span></span>|<span data-ttu-id="48e54-147">説明</span><span class="sxs-lookup"><span data-stu-id="48e54-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="48e54-148">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="48e54-148">*policy_setting*</span></span>|<span data-ttu-id="48e54-149">アプリで型に適用する、このポリシーの設定です。</span><span class="sxs-lookup"><span data-stu-id="48e54-149">The setting for this policy to apply to the types in the app.</span></span> <span data-ttu-id="48e54-150">指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="48e54-150">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="48e54-151">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48e54-151">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48e54-152">子要素</span><span class="sxs-lookup"><span data-stu-id="48e54-152">Child Elements</span></span>  
  
|<span data-ttu-id="48e54-153">要素</span><span class="sxs-lookup"><span data-stu-id="48e54-153">Element</span></span>|<span data-ttu-id="48e54-154">説明</span><span class="sxs-lookup"><span data-stu-id="48e54-154">Description</span></span>|  
|-------------|-----------------|  
|[\<Assembly>](assembly-element-net-native.md)|<span data-ttu-id="48e54-155">特定のアセンブリ内のすべての型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="48e54-155">Applies policy to all the types in a particular assembly.</span></span>|  
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="48e54-156">特定の名前空間内のすべての型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="48e54-156">Applies policy to all the types in a particular namespace.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="48e54-157">クラスや構造体などの特定の型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="48e54-157">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="48e54-158">構築されたジェネリック型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="48e54-158">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="48e54-159">たとえば、要素を [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 使用して、型のポリシーを定義することができ `List<String>` ます。</span><span class="sxs-lookup"><span data-stu-id="48e54-159">For example, a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="48e54-160">特定の型のメソッドにポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="48e54-160">Applies policy to a method on a particular type.</span></span>|  
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|<span data-ttu-id="48e54-161">構築されたジェネリック メソッドにポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="48e54-161">Applies policy to a constructed generic method.</span></span>|  
|[\<Property>](property-element-net-native.md)|<span data-ttu-id="48e54-162">特定の型のプロパティにポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="48e54-162">Applies policy to a property on a particular type.</span></span>|  
|[\<Field>](field-element-net-native.md)|<span data-ttu-id="48e54-163">特定の型のフィールドにポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="48e54-163">Applies policy to a field on a particular type.</span></span>|  
|[\<Event>](event-element-net-native.md)|<span data-ttu-id="48e54-164">特定の型のイベントにポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="48e54-164">Applies policy to an event on a particular type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48e54-165">親要素</span><span class="sxs-lookup"><span data-stu-id="48e54-165">Parent Elements</span></span>  
  
|<span data-ttu-id="48e54-166">要素</span><span class="sxs-lookup"><span data-stu-id="48e54-166">Element</span></span>|<span data-ttu-id="48e54-167">説明</span><span class="sxs-lookup"><span data-stu-id="48e54-167">Description</span></span>|  
|-------------|-----------------|  
|[\<Directives>](directives-element-net-native.md)|<span data-ttu-id="48e54-168">ランタイム ディレクティブ ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="48e54-168">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48e54-169">解説</span><span class="sxs-lookup"><span data-stu-id="48e54-169">Remarks</span></span>  

 <span data-ttu-id="48e54-170">要素には、 [\<Directives>](directives-element-net-native.md) 0 個または1個の要素を含めることができ `<Application>` ます。</span><span class="sxs-lookup"><span data-stu-id="48e54-170">The [\<Directives>](directives-element-net-native.md) element can contain zero or one `<Application>` element.</span></span> <span data-ttu-id="48e54-171">1 つのリフレクション ディレクティブ ファイルに複数の `<Application>` 要素を含めることはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="48e54-171">Multiple `<Application>` elements in a single reflection directives file are not supported.</span></span>  
  
 <span data-ttu-id="48e54-172">`<Application>` 要素は、次の 2 とおりの方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="48e54-172">The `<Application>` element can be used in one of two ways:</span></span>  
  
- <span data-ttu-id="48e54-173">実行時に必要なメタデータを持つプログラム要素を定義するためのコンテナーとして。</span><span class="sxs-lookup"><span data-stu-id="48e54-173">As a container to define the program elements whose metadata is needed at run time.</span></span> <span data-ttu-id="48e54-174">この場合、`<Application>` 要素に属性は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="48e54-174">In this case, the `<Application>` element need not have any attributes.</span></span> <span data-ttu-id="48e54-175">コンパイル時に、コンパイラ ツールは、.NET Framework コア ライブラリを含むすべてのライブラリで、`<Application>` 要素の子要素により示されるプログラム要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="48e54-175">At compile time, compiler tools search all libraries, including .NET Framework core libraries, for program elements identified by child elements of the `<Application>` element.</span></span> <span data-ttu-id="48e54-176">これに対し、コンパイラツールは、要素によって指定されたライブラリのみを検索して、 [\<Library>](library-element-net-native.md) の子要素によって識別されるプログラム要素を検索 [\<Library>](library-element-net-native.md) します。</span><span class="sxs-lookup"><span data-stu-id="48e54-176">In contrast, compiler tools search only the library designated by the [\<Library>](library-element-net-native.md) element for program elements identified by the child elements of [\<Library>](library-element-net-native.md).</span></span>  
  
- <span data-ttu-id="48e54-177">リフレクション、シリアル化、および相互運用に関するアプリケーション全体のポリシーを設定する要素として。</span><span class="sxs-lookup"><span data-stu-id="48e54-177">As an element that sets application-wide policy for reflection, serialization, and interop.</span></span> <span data-ttu-id="48e54-178">要素の属性は、 `<Application>` アプリケーション全体のポリシーを定義します。これは、 `<Application>` 要素または要素によって定義される子要素によってオーバーライドされる可能性があり [\<Library>](library-element-net-native.md) ます。</span><span class="sxs-lookup"><span data-stu-id="48e54-178">The attributes of the `<Application>` element define application-wide policy, which may be overridden by the child elements defined by the `<Application>` or [\<Library>](library-element-net-native.md) element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e54-179">関連項目</span><span class="sxs-lookup"><span data-stu-id="48e54-179">See also</span></span>

- [<span data-ttu-id="48e54-180">\<Library> 要素</span><span class="sxs-lookup"><span data-stu-id="48e54-180">\<Library> Element</span></span>](library-element-net-native.md)
- [<span data-ttu-id="48e54-181">\<Directives> 要素</span><span class="sxs-lookup"><span data-stu-id="48e54-181">\<Directives> Element</span></span>](directives-element-net-native.md)
- [<span data-ttu-id="48e54-182">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="48e54-182">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="48e54-183">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="48e54-183">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
