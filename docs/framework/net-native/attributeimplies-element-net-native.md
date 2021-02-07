---
description: '詳細情報: <AttributeImplies> 要素 (.NET Native)'
title: <AttributeImplies> 要素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 5af1f60f2c1e556281f2f1d392b1a046e52dd277
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747908"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="19ba7-103">\<AttributeImplies> 要素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="19ba7-103">\<AttributeImplies> Element (.NET Native)</span></span>

<span data-ttu-id="19ba7-104">それを含む属性が適用されるコード要素のポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="19ba7-104">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19ba7-105">構文</span><span class="sxs-lookup"><span data-stu-id="19ba7-105">Syntax</span></span>  
  
```xml  
<AttributeImplies Activate="policy_type"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19ba7-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="19ba7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="19ba7-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="19ba7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19ba7-108">属性</span><span class="sxs-lookup"><span data-stu-id="19ba7-108">Attributes</span></span>  
  
|<span data-ttu-id="19ba7-109">属性</span><span class="sxs-lookup"><span data-stu-id="19ba7-109">Attribute</span></span>|<span data-ttu-id="19ba7-110">属性の型</span><span class="sxs-lookup"><span data-stu-id="19ba7-110">Attribute type</span></span>|<span data-ttu-id="19ba7-111">説明</span><span class="sxs-lookup"><span data-stu-id="19ba7-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="19ba7-112">リフレクション</span><span class="sxs-lookup"><span data-stu-id="19ba7-112">Reflection</span></span>|<span data-ttu-id="19ba7-113">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="19ba7-113">Optional attribute.</span></span> <span data-ttu-id="19ba7-114">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="19ba7-114">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="19ba7-115">リフレクション</span><span class="sxs-lookup"><span data-stu-id="19ba7-115">Reflection</span></span>|<span data-ttu-id="19ba7-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="19ba7-116">Optional attribute.</span></span> <span data-ttu-id="19ba7-117">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="19ba7-117">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="19ba7-118">リフレクション</span><span class="sxs-lookup"><span data-stu-id="19ba7-118">Reflection</span></span>|<span data-ttu-id="19ba7-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="19ba7-119">Optional attribute.</span></span> <span data-ttu-id="19ba7-120">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="19ba7-120">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="19ba7-121">シリアル化</span><span class="sxs-lookup"><span data-stu-id="19ba7-121">Serialization</span></span>|<span data-ttu-id="19ba7-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="19ba7-122">Optional attribute.</span></span> <span data-ttu-id="19ba7-123">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="19ba7-123">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="19ba7-124">シリアル化</span><span class="sxs-lookup"><span data-stu-id="19ba7-124">Serialization</span></span>|<span data-ttu-id="19ba7-125">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="19ba7-125">Optional attribute.</span></span> <span data-ttu-id="19ba7-126"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="19ba7-126">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="19ba7-127">シリアル化</span><span class="sxs-lookup"><span data-stu-id="19ba7-127">Serialization</span></span>|<span data-ttu-id="19ba7-128">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="19ba7-128">Optional attribute.</span></span> <span data-ttu-id="19ba7-129"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="19ba7-129">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="19ba7-130">シリアル化</span><span class="sxs-lookup"><span data-stu-id="19ba7-130">Serialization</span></span>|<span data-ttu-id="19ba7-131">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="19ba7-131">Optional attribute.</span></span> <span data-ttu-id="19ba7-132"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="19ba7-132">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="19ba7-133">Interop</span><span class="sxs-lookup"><span data-stu-id="19ba7-133">Interop</span></span>|<span data-ttu-id="19ba7-134">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="19ba7-134">Optional attribute.</span></span> <span data-ttu-id="19ba7-135">Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="19ba7-135">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="19ba7-136">Interop</span><span class="sxs-lookup"><span data-stu-id="19ba7-136">Interop</span></span>|<span data-ttu-id="19ba7-137">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="19ba7-137">Optional attribute.</span></span> <span data-ttu-id="19ba7-138">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="19ba7-138">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="19ba7-139">Interop</span><span class="sxs-lookup"><span data-stu-id="19ba7-139">Interop</span></span>|<span data-ttu-id="19ba7-140">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="19ba7-140">Optional attribute.</span></span> <span data-ttu-id="19ba7-141">値型をネイティブ コードにマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="19ba7-141">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="19ba7-142">すべての属性</span><span class="sxs-lookup"><span data-stu-id="19ba7-142">All attributes</span></span>  
  
|<span data-ttu-id="19ba7-143">値</span><span class="sxs-lookup"><span data-stu-id="19ba7-143">Value</span></span>|<span data-ttu-id="19ba7-144">説明</span><span class="sxs-lookup"><span data-stu-id="19ba7-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="19ba7-145">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="19ba7-145">*policy_setting*</span></span>|<span data-ttu-id="19ba7-146">このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="19ba7-146">The setting to apply to this policy type.</span></span> <span data-ttu-id="19ba7-147">指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="19ba7-147">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="19ba7-148">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19ba7-148">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19ba7-149">子要素</span><span class="sxs-lookup"><span data-stu-id="19ba7-149">Child Elements</span></span>  

 <span data-ttu-id="19ba7-150">なし。</span><span class="sxs-lookup"><span data-stu-id="19ba7-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19ba7-151">親要素</span><span class="sxs-lookup"><span data-stu-id="19ba7-151">Parent Elements</span></span>  
  
|<span data-ttu-id="19ba7-152">要素</span><span class="sxs-lookup"><span data-stu-id="19ba7-152">Element</span></span>|<span data-ttu-id="19ba7-153">説明</span><span class="sxs-lookup"><span data-stu-id="19ba7-153">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="19ba7-154">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="19ba7-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19ba7-155">解説</span><span class="sxs-lookup"><span data-stu-id="19ba7-155">Remarks</span></span>  

 <span data-ttu-id="19ba7-156">`<AttributeImplies>` 要素は、それを含む型が属性 (つまり、<xref:System.Attribute?displayProperty=nameWithType> から継承されるクラス) である場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="19ba7-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="19ba7-157">特定のプログラム要素に属性が適用される場合、`<AttributeImplies>` 要素によって定義されるポリシーがそのプログラム要素に適用されます。</span><span class="sxs-lookup"><span data-stu-id="19ba7-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="19ba7-158">リフレクション、シリアル化、および相互運用属性はいずれも省略可能ですが、そのうち少なくとも 1 つが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19ba7-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19ba7-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="19ba7-159">See also</span></span>

- [<span data-ttu-id="19ba7-160">\<Type> 要素</span><span class="sxs-lookup"><span data-stu-id="19ba7-160">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="19ba7-161">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="19ba7-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="19ba7-162">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="19ba7-162">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="19ba7-163">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="19ba7-163">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
