---
description: '詳細情報: <Field> 要素 (.NET Native)'
title: <Field> 要素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
ms.openlocfilehash: 1f8c8b6720fb90bdc5855da7b17694253bbb7629
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747843"
---
# <a name="field-element-net-native"></a><span data-ttu-id="53489-103">\<Field> 要素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="53489-103">\<Field> Element (.NET Native)</span></span>

<span data-ttu-id="53489-104">フィールドにランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="53489-104">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53489-105">構文</span><span class="sxs-lookup"><span data-stu-id="53489-105">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53489-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="53489-106">Attributes and Elements</span></span>  

 <span data-ttu-id="53489-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="53489-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53489-108">属性</span><span class="sxs-lookup"><span data-stu-id="53489-108">Attributes</span></span>  
  
|<span data-ttu-id="53489-109">属性</span><span class="sxs-lookup"><span data-stu-id="53489-109">Attribute</span></span>|<span data-ttu-id="53489-110">属性の型</span><span class="sxs-lookup"><span data-stu-id="53489-110">Attribute type</span></span>|<span data-ttu-id="53489-111">[説明]</span><span class="sxs-lookup"><span data-stu-id="53489-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="53489-112">全般</span><span class="sxs-lookup"><span data-stu-id="53489-112">General</span></span>|<span data-ttu-id="53489-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="53489-113">Required attribute.</span></span> <span data-ttu-id="53489-114">フィールド名を指定します。</span><span class="sxs-lookup"><span data-stu-id="53489-114">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="53489-115">リフレクション</span><span class="sxs-lookup"><span data-stu-id="53489-115">Reflection</span></span>|<span data-ttu-id="53489-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="53489-116">Optional attribute.</span></span> <span data-ttu-id="53489-117">フィールドに関する情報の照会やフィールドの列挙を制御しますが、実行時の動的アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="53489-117">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="53489-118">リフレクション</span><span class="sxs-lookup"><span data-stu-id="53489-118">Reflection</span></span>|<span data-ttu-id="53489-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="53489-119">Optional attribute.</span></span> <span data-ttu-id="53489-120">フィールドへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="53489-120">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="53489-121">このポリシーにより、実行時にフィールドを動的に設定または取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="53489-121">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="53489-122">シリアル化</span><span class="sxs-lookup"><span data-stu-id="53489-122">Serialization</span></span>|<span data-ttu-id="53489-123">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="53489-123">Optional attribute.</span></span> <span data-ttu-id="53489-124">フィールドへの実行時アクセスを制御して、型インスタンスを Newtonsoft の JSON シリアライザーなどのライブラリによってシリアル化できるようにしたり、データ バインディングで使用できるようにしたりします。</span><span class="sxs-lookup"><span data-stu-id="53489-124">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="53489-125">Name 属性</span><span class="sxs-lookup"><span data-stu-id="53489-125">Name attribute</span></span>  
  
|<span data-ttu-id="53489-126">値</span><span class="sxs-lookup"><span data-stu-id="53489-126">Value</span></span>|<span data-ttu-id="53489-127">説明</span><span class="sxs-lookup"><span data-stu-id="53489-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="53489-128">*method_name*</span><span class="sxs-lookup"><span data-stu-id="53489-128">*method_name*</span></span>|<span data-ttu-id="53489-129">フィールド名。</span><span class="sxs-lookup"><span data-stu-id="53489-129">The field name.</span></span> <span data-ttu-id="53489-130">フィールドの型は、親要素または要素によって定義され [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) ます。</span><span class="sxs-lookup"><span data-stu-id="53489-130">The type of the field is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="53489-131">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="53489-131">All other attributes</span></span>  
  
|<span data-ttu-id="53489-132">値</span><span class="sxs-lookup"><span data-stu-id="53489-132">Value</span></span>|<span data-ttu-id="53489-133">説明</span><span class="sxs-lookup"><span data-stu-id="53489-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="53489-134">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="53489-134">*policy_setting*</span></span>|<span data-ttu-id="53489-135">フィールドのこのポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="53489-135">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="53489-136">指定できる値は、`Auto`、`Excluded`、`Included`、および `Required` です。</span><span class="sxs-lookup"><span data-stu-id="53489-136">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="53489-137">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53489-137">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53489-138">子要素</span><span class="sxs-lookup"><span data-stu-id="53489-138">Child Elements</span></span>  

 <span data-ttu-id="53489-139">なし。</span><span class="sxs-lookup"><span data-stu-id="53489-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53489-140">親要素</span><span class="sxs-lookup"><span data-stu-id="53489-140">Parent Elements</span></span>  
  
|<span data-ttu-id="53489-141">要素</span><span class="sxs-lookup"><span data-stu-id="53489-141">Element</span></span>|<span data-ttu-id="53489-142">説明</span><span class="sxs-lookup"><span data-stu-id="53489-142">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="53489-143">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="53489-143">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="53489-144">構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="53489-144">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53489-145">解説</span><span class="sxs-lookup"><span data-stu-id="53489-145">Remarks</span></span>  

 <span data-ttu-id="53489-146">フィールドのポリシーが明示的に定義されていない場合は、その親要素の実行時ポリシーを継承します。</span><span class="sxs-lookup"><span data-stu-id="53489-146">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53489-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="53489-147">See also</span></span>

- [<span data-ttu-id="53489-148">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="53489-148">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="53489-149">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="53489-149">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="53489-150">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="53489-150">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
