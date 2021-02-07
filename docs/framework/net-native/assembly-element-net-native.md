---
description: '詳細情報: <Assembly> 要素 (.NET Native)'
title: <Assembly> 要素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
ms.openlocfilehash: 567a30a6a77e9de03635a9dfaae6bb28c9d728f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747921"
---
# <a name="assembly-element-net-native"></a><span data-ttu-id="6f474-103">\<Assembly> 要素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="6f474-103">\<Assembly> Element (.NET Native)</span></span>

<span data-ttu-id="6f474-104">指定したアセンブリ内のすべての型にランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="6f474-104">Applies runtime reflection policy to all the types in a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f474-105">構文</span><span class="sxs-lookup"><span data-stu-id="6f474-105">Syntax</span></span>  
  
```xml  
<Assembly Name="assembly_name"
          Activate="policy_setting"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f474-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6f474-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6f474-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6f474-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f474-108">属性</span><span class="sxs-lookup"><span data-stu-id="6f474-108">Attributes</span></span>  
  
|<span data-ttu-id="6f474-109">属性</span><span class="sxs-lookup"><span data-stu-id="6f474-109">Attribute</span></span>|<span data-ttu-id="6f474-110">属性の型</span><span class="sxs-lookup"><span data-stu-id="6f474-110">Attribute type</span></span>|<span data-ttu-id="6f474-111">[説明]</span><span class="sxs-lookup"><span data-stu-id="6f474-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="6f474-112">全般</span><span class="sxs-lookup"><span data-stu-id="6f474-112">General</span></span>|<span data-ttu-id="6f474-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="6f474-113">Required attribute.</span></span> <span data-ttu-id="6f474-114">アセンブリの簡易名を指定します。</span><span class="sxs-lookup"><span data-stu-id="6f474-114">Specifies the simple name of an assembly.</span></span>|  
|`Activate`|<span data-ttu-id="6f474-115">リフレクション</span><span class="sxs-lookup"><span data-stu-id="6f474-115">Reflection</span></span>|<span data-ttu-id="6f474-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="6f474-116">Optional attribute.</span></span> <span data-ttu-id="6f474-117">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="6f474-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="6f474-118">リフレクション</span><span class="sxs-lookup"><span data-stu-id="6f474-118">Reflection</span></span>|<span data-ttu-id="6f474-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="6f474-119">Optional attribute.</span></span> <span data-ttu-id="6f474-120">アセンブリ内の型に関する情報の照会または型の列挙を制御しますが、実行時の動的アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="6f474-120">Controls querying for information about or enumerating the types in the assembly, but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="6f474-121">リフレクション</span><span class="sxs-lookup"><span data-stu-id="6f474-121">Reflection</span></span>|<span data-ttu-id="6f474-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="6f474-122">Optional attribute.</span></span> <span data-ttu-id="6f474-123">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="6f474-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="6f474-124">シリアル化</span><span class="sxs-lookup"><span data-stu-id="6f474-124">Serialization</span></span>|<span data-ttu-id="6f474-125">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="6f474-125">Optional attribute.</span></span> <span data-ttu-id="6f474-126">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="6f474-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="6f474-127">シリアル化</span><span class="sxs-lookup"><span data-stu-id="6f474-127">Serialization</span></span>|<span data-ttu-id="6f474-128">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="6f474-128">Optional attribute.</span></span> <span data-ttu-id="6f474-129"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="6f474-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="6f474-130">シリアル化</span><span class="sxs-lookup"><span data-stu-id="6f474-130">Serialization</span></span>|<span data-ttu-id="6f474-131">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="6f474-131">Optional attribute.</span></span> <span data-ttu-id="6f474-132"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="6f474-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="6f474-133">シリアル化</span><span class="sxs-lookup"><span data-stu-id="6f474-133">Serialization</span></span>|<span data-ttu-id="6f474-134">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="6f474-134">Optional attribute.</span></span> <span data-ttu-id="6f474-135"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="6f474-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="6f474-136">Interop</span><span class="sxs-lookup"><span data-stu-id="6f474-136">Interop</span></span>|<span data-ttu-id="6f474-137">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="6f474-137">Optional attribute.</span></span> <span data-ttu-id="6f474-138">Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="6f474-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="6f474-139">Interop</span><span class="sxs-lookup"><span data-stu-id="6f474-139">Interop</span></span>|<span data-ttu-id="6f474-140">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="6f474-140">Optional attribute.</span></span> <span data-ttu-id="6f474-141">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="6f474-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="6f474-142">Interop</span><span class="sxs-lookup"><span data-stu-id="6f474-142">Interop</span></span>|<span data-ttu-id="6f474-143">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="6f474-143">Optional attribute.</span></span> <span data-ttu-id="6f474-144">ネイティブ コードに構造体をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="6f474-144">Controls policy for marshaling structures to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="6f474-145">Name 属性</span><span class="sxs-lookup"><span data-stu-id="6f474-145">Name attribute</span></span>  
  
|<span data-ttu-id="6f474-146">値</span><span class="sxs-lookup"><span data-stu-id="6f474-146">Value</span></span>|<span data-ttu-id="6f474-147">説明</span><span class="sxs-lookup"><span data-stu-id="6f474-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6f474-148">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="6f474-148">*assembly_name*</span></span>|<span data-ttu-id="6f474-149">ファイル拡張子のないアセンブリの簡易名です。</span><span class="sxs-lookup"><span data-stu-id="6f474-149">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="6f474-150">この属性は、<xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> プロパティに対応します。</span><span class="sxs-lookup"><span data-stu-id="6f474-150">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="6f474-151">たとえば、Extensions.dll というアセンブリの名前は "Extensions" です。</span><span class="sxs-lookup"><span data-stu-id="6f474-151">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span><br /><br /> <span data-ttu-id="6f474-152">リテラル文字列 `*Application*` を指定して、アプリ パッケージ内のすべてのアセンブリに、読み込みの有無に関係なくポリシーを適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="6f474-152">You can also specify the literal string `*Application*` to apply policy to all assemblies in your app package, whether those assemblies are loaded or not.</span></span> <span data-ttu-id="6f474-153">`*Application*` は、.NET Framework アセンブリにポリシーを適用しません。</span><span class="sxs-lookup"><span data-stu-id="6f474-153">`*Application*` never applies policy to .NET Framework assemblies.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="6f474-154">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="6f474-154">All other attributes</span></span>  
  
|<span data-ttu-id="6f474-155">値</span><span class="sxs-lookup"><span data-stu-id="6f474-155">Value</span></span>|<span data-ttu-id="6f474-156">説明</span><span class="sxs-lookup"><span data-stu-id="6f474-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6f474-157">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="6f474-157">*policy_setting*</span></span>|<span data-ttu-id="6f474-158">アセンブリ内のすべての型について、このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="6f474-158">The setting to apply to this policy type for all types in the assembly.</span></span> <span data-ttu-id="6f474-159">指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="6f474-159">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="6f474-160">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f474-160">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f474-161">子要素</span><span class="sxs-lookup"><span data-stu-id="6f474-161">Child Elements</span></span>  
  
|<span data-ttu-id="6f474-162">要素</span><span class="sxs-lookup"><span data-stu-id="6f474-162">Element</span></span>|<span data-ttu-id="6f474-163">説明</span><span class="sxs-lookup"><span data-stu-id="6f474-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="6f474-164">子名前空間内のすべての型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="6f474-164">Applies reflection policy to all types in a child namespace.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="6f474-165">型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="6f474-165">Applies reflection policy to a type.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="6f474-166">構築されたジェネリック型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="6f474-166">Applies reflection policy to a constructed generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6f474-167">親要素</span><span class="sxs-lookup"><span data-stu-id="6f474-167">Parent Elements</span></span>  
  
|<span data-ttu-id="6f474-168">要素</span><span class="sxs-lookup"><span data-stu-id="6f474-168">Element</span></span>|<span data-ttu-id="6f474-169">説明</span><span class="sxs-lookup"><span data-stu-id="6f474-169">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="6f474-170">実行時にリフレクションで使用可能なメタデータを持つ、アプリケーション全体の型と型のメンバーのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="6f474-170">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="6f474-171">要素には、 [\<Application>](application-element-net-native.md) 0 個以上の要素を含めることができ `<Assembly>` ます。</span><span class="sxs-lookup"><span data-stu-id="6f474-171">The [\<Application>](application-element-net-native.md) element can have zero, one, or more `<Assembly>` elements.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="6f474-172">実行時にリフレクションに使用可能なメタデータを持つ型と型のメンバーを含むアセンブリを定義します。</span><span class="sxs-lookup"><span data-stu-id="6f474-172">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="6f474-173">要素には、 [\<Library>](library-element-net-native.md) 0 個または1個の要素を含めることができ `<Assembly>` ます。</span><span class="sxs-lookup"><span data-stu-id="6f474-173">The [\<Library>](library-element-net-native.md) element can have zero or one `<Assembly>` element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f474-174">解説</span><span class="sxs-lookup"><span data-stu-id="6f474-174">Remarks</span></span>  

 <span data-ttu-id="6f474-175">`<Assembly>` 要素は、アセンブリ内のすべての型の実行時ポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="6f474-175">The `<Assembly>` element defines runtime policy for all the types in an assembly.</span></span> <span data-ttu-id="6f474-176">これは、 [\<Library>](library-element-net-native.md) ライブラリを指定する要素とは異なりますが、ランタイムリフレクションポリシーを定義するためにその子要素に依存します。</span><span class="sxs-lookup"><span data-stu-id="6f474-176">It differs from the [\<Library>](library-element-net-native.md) element, which specifies a library but depends on its child elements to define runtime reflection policy.</span></span> <span data-ttu-id="6f474-177">`<Assembly>` 要素は、子要素でオーバーライドされない限り、アセンブリ内のすべての型に適用されます。</span><span class="sxs-lookup"><span data-stu-id="6f474-177">The `<Assembly>` element applies to all the types in an assembly unless they are overridden by a child element.</span></span>  
  
 <span data-ttu-id="6f474-178">次の例では、`Name` 属性に "\*Application\*" という値を割り当てて、アプリ パッケージ内のアセンブリのすべての型に実行時ポリシーを適用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6f474-178">The following example shows how you can apply runtime policy to all the types in assemblies within your app package by assigning the `Name` attribute a value of "\*Application\*".</span></span> <span data-ttu-id="6f474-179">`<Assembly>`要素は要素の子である必要があり [\<Application>](application-element-net-native.md) ます。</span><span class="sxs-lookup"><span data-stu-id="6f474-179">The `<Assembly>` element must be a child of the [\<Application>](application-element-net-native.md) element.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <Assembly Name="*Application*" Dynamic="Required All" />
  </Application>
</Directives>  
```  
  
 <span data-ttu-id="6f474-180">`Activate` 属性、`Browse` 属性、`Dynamic`、および `Serialize` 属性はすべて省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6f474-180">The `Activate`, `Browse`, `Dynamic`, and `Serialize` attributes are all optional.</span></span> <span data-ttu-id="6f474-181">ただし、`<Assembly>` 要素にはこれらの属性のいずれか 1 つ以上を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f474-181">However, the `<Assembly>` element must contain at least one of these attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f474-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f474-182">See also</span></span>

- [<span data-ttu-id="6f474-183">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="6f474-183">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="6f474-184">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="6f474-184">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="6f474-185">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="6f474-185">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
