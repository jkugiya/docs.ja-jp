---
description: '詳細情報: <Subtypes> 要素 (.NET Native)'
title: <Subtypes> 要素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
ms.openlocfilehash: d30bb482e784d912d3f5d61f688ed2b824e45f27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801957"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="ed2e8-103">\<Subtypes> 要素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="ed2e8-103">\<Subtypes> Element (.NET Native)</span></span>

<span data-ttu-id="ed2e8-104">それを含む型から継承されたすべてのクラスに実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-104">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed2e8-105">構文</span><span class="sxs-lookup"><span data-stu-id="ed2e8-105">Syntax</span></span>  
  
```xml  
<Subtypes Activate="policy_type"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed2e8-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ed2e8-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ed2e8-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed2e8-108">属性</span><span class="sxs-lookup"><span data-stu-id="ed2e8-108">Attributes</span></span>  
  
|<span data-ttu-id="ed2e8-109">属性</span><span class="sxs-lookup"><span data-stu-id="ed2e8-109">Attribute</span></span>|<span data-ttu-id="ed2e8-110">属性の型</span><span class="sxs-lookup"><span data-stu-id="ed2e8-110">Attribute type</span></span>|<span data-ttu-id="ed2e8-111">説明</span><span class="sxs-lookup"><span data-stu-id="ed2e8-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="ed2e8-112">リフレクション</span><span class="sxs-lookup"><span data-stu-id="ed2e8-112">Reflection</span></span>|<span data-ttu-id="ed2e8-113">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-113">Optional attribute.</span></span> <span data-ttu-id="ed2e8-114">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-114">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="ed2e8-115">リフレクション</span><span class="sxs-lookup"><span data-stu-id="ed2e8-115">Reflection</span></span>|<span data-ttu-id="ed2e8-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-116">Optional attribute.</span></span> <span data-ttu-id="ed2e8-117">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-117">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="ed2e8-118">リフレクション</span><span class="sxs-lookup"><span data-stu-id="ed2e8-118">Reflection</span></span>|<span data-ttu-id="ed2e8-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-119">Optional attribute.</span></span> <span data-ttu-id="ed2e8-120">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-120">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="ed2e8-121">シリアル化</span><span class="sxs-lookup"><span data-stu-id="ed2e8-121">Serialization</span></span>|<span data-ttu-id="ed2e8-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-122">Optional attribute.</span></span> <span data-ttu-id="ed2e8-123">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-123">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="ed2e8-124">シリアル化</span><span class="sxs-lookup"><span data-stu-id="ed2e8-124">Serialization</span></span>|<span data-ttu-id="ed2e8-125">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-125">Optional attribute.</span></span> <span data-ttu-id="ed2e8-126"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-126">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="ed2e8-127">シリアル化</span><span class="sxs-lookup"><span data-stu-id="ed2e8-127">Serialization</span></span>|<span data-ttu-id="ed2e8-128">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-128">Optional attribute.</span></span> <span data-ttu-id="ed2e8-129"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-129">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="ed2e8-130">シリアル化</span><span class="sxs-lookup"><span data-stu-id="ed2e8-130">Serialization</span></span>|<span data-ttu-id="ed2e8-131">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-131">Optional attribute.</span></span> <span data-ttu-id="ed2e8-132"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-132">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="ed2e8-133">Interop</span><span class="sxs-lookup"><span data-stu-id="ed2e8-133">Interop</span></span>|<span data-ttu-id="ed2e8-134">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-134">Optional attribute.</span></span> <span data-ttu-id="ed2e8-135">Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-135">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="ed2e8-136">Interop</span><span class="sxs-lookup"><span data-stu-id="ed2e8-136">Interop</span></span>|<span data-ttu-id="ed2e8-137">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-137">Optional attribute.</span></span> <span data-ttu-id="ed2e8-138">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-138">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="ed2e8-139">Interop</span><span class="sxs-lookup"><span data-stu-id="ed2e8-139">Interop</span></span>|<span data-ttu-id="ed2e8-140">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-140">Optional attribute.</span></span> <span data-ttu-id="ed2e8-141">値型をネイティブ コードにマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-141">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="ed2e8-142">すべての属性</span><span class="sxs-lookup"><span data-stu-id="ed2e8-142">All attributes</span></span>  
  
|<span data-ttu-id="ed2e8-143">値</span><span class="sxs-lookup"><span data-stu-id="ed2e8-143">Value</span></span>|<span data-ttu-id="ed2e8-144">説明</span><span class="sxs-lookup"><span data-stu-id="ed2e8-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ed2e8-145">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="ed2e8-145">*policy_setting*</span></span>|<span data-ttu-id="ed2e8-146">このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-146">The setting to apply to this policy type.</span></span> <span data-ttu-id="ed2e8-147">指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-147">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="ed2e8-148">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-148">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed2e8-149">子要素</span><span class="sxs-lookup"><span data-stu-id="ed2e8-149">Child Elements</span></span>  

 <span data-ttu-id="ed2e8-150">なし。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ed2e8-151">親要素</span><span class="sxs-lookup"><span data-stu-id="ed2e8-151">Parent Elements</span></span>  
  
|<span data-ttu-id="ed2e8-152">要素</span><span class="sxs-lookup"><span data-stu-id="ed2e8-152">Element</span></span>|<span data-ttu-id="ed2e8-153">説明</span><span class="sxs-lookup"><span data-stu-id="ed2e8-153">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="ed2e8-154">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed2e8-155">解説</span><span class="sxs-lookup"><span data-stu-id="ed2e8-155">Remarks</span></span>  

 <span data-ttu-id="ed2e8-156">`<Subtypes>` 要素は、それを含む型のすべてのサブタイプにポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="ed2e8-157">派生型および基底クラスに異なるポリシーを適用する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="ed2e8-158">リフレクション、シリアル化、および相互運用属性はいずれも省略可能ですが、そのうち少なくとも 1 つが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed2e8-159">例</span><span class="sxs-lookup"><span data-stu-id="ed2e8-159">Example</span></span>  

 <span data-ttu-id="ed2e8-160">次の例では、`BaseClass` という名前のクラスと `Derived1` という名前のサブクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="ed2e8-161">次のコードに示すように、ランタイム ディレクティブ ファイルは、`Dynamic` の `Activate` ポリシーと `BaseClass` ポリシーを明示的に `Excluded` に設定します。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="ed2e8-162">このため、`BaseClass` 型のオブジェクトは動的に、または `BaseClass` クラス コンストラクターの呼び出しによってインスタンス化できません。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="ed2e8-163">ただし、`<Subtypes>` 要素では、`BaseClass` から派生されたクラスの動的なおよびクラス コンストラクターの呼び出しによるインスタンス化は行えません。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
```  
  
 <span data-ttu-id="ed2e8-164">`<Subtypes>` ディレクティブによって、`Derived1` インスタンスを <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> メソッドを呼び出すことによって動的にインスタンス化する次のコードが正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="ed2e8-165">ここでブロック変数は、空の Windows ストア アプリの <xref:System.Windows.Controls.TextBlock> オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="ed2e8-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ed2e8-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed2e8-166">See also</span></span>

- [<span data-ttu-id="ed2e8-167">\<Type> 要素</span><span class="sxs-lookup"><span data-stu-id="ed2e8-167">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="ed2e8-168">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="ed2e8-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="ed2e8-169">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="ed2e8-169">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="ed2e8-170">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="ed2e8-170">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
