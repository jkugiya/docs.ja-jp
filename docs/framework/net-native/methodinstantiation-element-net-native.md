---
description: '詳細情報: <MethodInstantiation> 要素 (.NET Native)'
title: <MethodInstantiation> 要素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
ms.openlocfilehash: 985d522a559dbbce936a2f29a9983c89ebd18a48
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747492"
---
# <a name="methodinstantiation-element-net-native"></a><span data-ttu-id="de7b8-103">\<MethodInstantiation> 要素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="de7b8-103">\<MethodInstantiation> Element (.NET Native)</span></span>

<span data-ttu-id="de7b8-104">構築されたジェネリック メソッドにランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="de7b8-104">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de7b8-105">構文</span><span class="sxs-lookup"><span data-stu-id="de7b8-105">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de7b8-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="de7b8-106">Attributes and Elements</span></span>  

 <span data-ttu-id="de7b8-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="de7b8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de7b8-108">属性</span><span class="sxs-lookup"><span data-stu-id="de7b8-108">Attributes</span></span>  
  
|<span data-ttu-id="de7b8-109">属性</span><span class="sxs-lookup"><span data-stu-id="de7b8-109">Attribute</span></span>|<span data-ttu-id="de7b8-110">属性の型</span><span class="sxs-lookup"><span data-stu-id="de7b8-110">Attribute type</span></span>|<span data-ttu-id="de7b8-111">[説明]</span><span class="sxs-lookup"><span data-stu-id="de7b8-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="de7b8-112">全般</span><span class="sxs-lookup"><span data-stu-id="de7b8-112">General</span></span>|<span data-ttu-id="de7b8-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="de7b8-113">Required attribute.</span></span> <span data-ttu-id="de7b8-114">メソッド名を指定します。</span><span class="sxs-lookup"><span data-stu-id="de7b8-114">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="de7b8-115">全般</span><span class="sxs-lookup"><span data-stu-id="de7b8-115">General</span></span>|<span data-ttu-id="de7b8-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="de7b8-116">Optional attribute.</span></span> <span data-ttu-id="de7b8-117">メソッドの名前付きパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="de7b8-117">Specifies named parameters of the method.</span></span> <span data-ttu-id="de7b8-118">複数の名前付きパラメーターはコンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="de7b8-118">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="de7b8-119">`Signature` 属性は、オーバー ロードされたメソッドを区別するために使用します。</span><span class="sxs-lookup"><span data-stu-id="de7b8-119">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="de7b8-120">全般</span><span class="sxs-lookup"><span data-stu-id="de7b8-120">General</span></span>|<span data-ttu-id="de7b8-121">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="de7b8-121">Required attribute.</span></span> <span data-ttu-id="de7b8-122">ジェネリック型引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="de7b8-122">Specifies the generic type arguments.</span></span> <span data-ttu-id="de7b8-123">複数の引数が存在する場合は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="de7b8-123">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="de7b8-124">リフレクション</span><span class="sxs-lookup"><span data-stu-id="de7b8-124">Reflection</span></span>|<span data-ttu-id="de7b8-125">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="de7b8-125">Optional attribute.</span></span> <span data-ttu-id="de7b8-126">メソッドに関する情報の照会やメソッドの列挙を制御しますが、実行時の動的呼び出しは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="de7b8-126">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="de7b8-127">リフレクション</span><span class="sxs-lookup"><span data-stu-id="de7b8-127">Reflection</span></span>|<span data-ttu-id="de7b8-128">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="de7b8-128">Optional attribute.</span></span> <span data-ttu-id="de7b8-129">コンストラクターまたはメソッドへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="de7b8-129">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="de7b8-130">このポリシーにより、実行時にメンバーを動的に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="de7b8-130">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="de7b8-131">Name 属性</span><span class="sxs-lookup"><span data-stu-id="de7b8-131">Name attribute</span></span>  
  
|<span data-ttu-id="de7b8-132">値</span><span class="sxs-lookup"><span data-stu-id="de7b8-132">Value</span></span>|<span data-ttu-id="de7b8-133">説明</span><span class="sxs-lookup"><span data-stu-id="de7b8-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="de7b8-134">*method_name*</span><span class="sxs-lookup"><span data-stu-id="de7b8-134">*method_name*</span></span>|<span data-ttu-id="de7b8-135">メソッド名。</span><span class="sxs-lookup"><span data-stu-id="de7b8-135">The method name.</span></span> <span data-ttu-id="de7b8-136">メソッドの型は、親要素または要素によって定義され [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) ます。</span><span class="sxs-lookup"><span data-stu-id="de7b8-136">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="de7b8-137">シグネチャ属性</span><span class="sxs-lookup"><span data-stu-id="de7b8-137">Signature attribute</span></span>  
  
|<span data-ttu-id="de7b8-138">値</span><span class="sxs-lookup"><span data-stu-id="de7b8-138">Value</span></span>|<span data-ttu-id="de7b8-139">説明</span><span class="sxs-lookup"><span data-stu-id="de7b8-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="de7b8-140">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="de7b8-140">*method_signature*</span></span>|<span data-ttu-id="de7b8-141">メソッドの名前付きパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="de7b8-141">Specifies the named parameters of the method.</span></span> <span data-ttu-id="de7b8-142">複数のパラメーターが存在する場合はコンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="de7b8-142">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="de7b8-143">引数属性</span><span class="sxs-lookup"><span data-stu-id="de7b8-143">Arguments attribute</span></span>  
  
|<span data-ttu-id="de7b8-144">値</span><span class="sxs-lookup"><span data-stu-id="de7b8-144">Value</span></span>|<span data-ttu-id="de7b8-145">説明</span><span class="sxs-lookup"><span data-stu-id="de7b8-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="de7b8-146">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="de7b8-146">*method_arguments*</span></span>|<span data-ttu-id="de7b8-147">ジェネリック型引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="de7b8-147">Specifies the generic type arguments.</span></span> <span data-ttu-id="de7b8-148">複数の引数が存在する場合は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="de7b8-148">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="de7b8-149">各引数は、完全修飾型名で構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="de7b8-149">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="de7b8-150">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="de7b8-150">All other attributes</span></span>  
  
|<span data-ttu-id="de7b8-151">値</span><span class="sxs-lookup"><span data-stu-id="de7b8-151">Value</span></span>|<span data-ttu-id="de7b8-152">説明</span><span class="sxs-lookup"><span data-stu-id="de7b8-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="de7b8-153">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="de7b8-153">*policy_setting*</span></span>|<span data-ttu-id="de7b8-154">メソッドのこのポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="de7b8-154">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="de7b8-155">指定できる値は、`Auto`、`Excluded`、`Included`、および `Required` です。</span><span class="sxs-lookup"><span data-stu-id="de7b8-155">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="de7b8-156">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de7b8-156">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de7b8-157">子要素</span><span class="sxs-lookup"><span data-stu-id="de7b8-157">Child Elements</span></span>  

 <span data-ttu-id="de7b8-158">なし。</span><span class="sxs-lookup"><span data-stu-id="de7b8-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de7b8-159">親要素</span><span class="sxs-lookup"><span data-stu-id="de7b8-159">Parent Elements</span></span>  
  
|<span data-ttu-id="de7b8-160">要素</span><span class="sxs-lookup"><span data-stu-id="de7b8-160">Element</span></span>|<span data-ttu-id="de7b8-161">説明</span><span class="sxs-lookup"><span data-stu-id="de7b8-161">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="de7b8-162">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="de7b8-162">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="de7b8-163">構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="de7b8-163">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de7b8-164">解説</span><span class="sxs-lookup"><span data-stu-id="de7b8-164">Remarks</span></span>  

 <span data-ttu-id="de7b8-165">`<MethodInstantiation>` 要素は、対応するオープン ジェネリック メソッドのランタイム リフレクション ポリシーをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="de7b8-165">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de7b8-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="de7b8-166">See also</span></span>

- [<span data-ttu-id="de7b8-167">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="de7b8-167">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="de7b8-168">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="de7b8-168">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="de7b8-169">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="de7b8-169">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="de7b8-170">\<Method> 要素</span><span class="sxs-lookup"><span data-stu-id="de7b8-170">\<Method> Element</span></span>](method-element-net-native.md)
