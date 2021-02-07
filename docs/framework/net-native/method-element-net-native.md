---
description: '詳細情報: <Method> 要素 (.NET Native)'
title: <Method> 要素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 76c379ed81e721316e4293b20ba89acfbc9d174f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747525"
---
# <a name="method-element-net-native"></a><span data-ttu-id="86932-103">\<Method> 要素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="86932-103">\<Method> Element (.NET Native)</span></span>

<span data-ttu-id="86932-104">コンストラクターまたはメソッドにランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="86932-104">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86932-105">構文</span><span class="sxs-lookup"><span data-stu-id="86932-105">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86932-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="86932-106">Attributes and Elements</span></span>  

 <span data-ttu-id="86932-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="86932-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86932-108">属性</span><span class="sxs-lookup"><span data-stu-id="86932-108">Attributes</span></span>  
  
|<span data-ttu-id="86932-109">属性</span><span class="sxs-lookup"><span data-stu-id="86932-109">Attribute</span></span>|<span data-ttu-id="86932-110">属性の型</span><span class="sxs-lookup"><span data-stu-id="86932-110">Attribute type</span></span>|<span data-ttu-id="86932-111">[説明]</span><span class="sxs-lookup"><span data-stu-id="86932-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="86932-112">全般</span><span class="sxs-lookup"><span data-stu-id="86932-112">General</span></span>|<span data-ttu-id="86932-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="86932-113">Required attribute.</span></span> <span data-ttu-id="86932-114">メソッド名を指定します。</span><span class="sxs-lookup"><span data-stu-id="86932-114">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="86932-115">全般</span><span class="sxs-lookup"><span data-stu-id="86932-115">General</span></span>|<span data-ttu-id="86932-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="86932-116">Optional attribute.</span></span> <span data-ttu-id="86932-117">メソッド シグネチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="86932-117">Specifies the method signature.</span></span> <span data-ttu-id="86932-118">複数のパラメーターが存在する場合はコンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="86932-118">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="86932-119">たとえば、次の `<Method>` 要素は <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> メソッドのポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="86932-119">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="86932-120">属性が存在しない場合、ランタイム ディレクティブは、メソッドのすべてのオーバーロードに適用されます。</span><span class="sxs-lookup"><span data-stu-id="86932-120">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="86932-121">リフレクション</span><span class="sxs-lookup"><span data-stu-id="86932-121">Reflection</span></span>|<span data-ttu-id="86932-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="86932-122">Optional attribute.</span></span> <span data-ttu-id="86932-123">メソッドに関する情報の照会やメソッドの列挙を制御しますが、実行時の動的呼び出しは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="86932-123">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="86932-124">リフレクション</span><span class="sxs-lookup"><span data-stu-id="86932-124">Reflection</span></span>|<span data-ttu-id="86932-125">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="86932-125">Optional attribute.</span></span> <span data-ttu-id="86932-126">コンストラクターまたはメソッドへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="86932-126">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="86932-127">このポリシーにより、実行時にメンバーを動的に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="86932-127">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="86932-128">Name 属性</span><span class="sxs-lookup"><span data-stu-id="86932-128">Name attribute</span></span>  
  
|<span data-ttu-id="86932-129">値</span><span class="sxs-lookup"><span data-stu-id="86932-129">Value</span></span>|<span data-ttu-id="86932-130">説明</span><span class="sxs-lookup"><span data-stu-id="86932-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86932-131">*method_name*</span><span class="sxs-lookup"><span data-stu-id="86932-131">*method_name*</span></span>|<span data-ttu-id="86932-132">メソッド名。</span><span class="sxs-lookup"><span data-stu-id="86932-132">The method name.</span></span> <span data-ttu-id="86932-133">メソッドの型は、親要素または要素によって定義され [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) ます。</span><span class="sxs-lookup"><span data-stu-id="86932-133">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="86932-134">シグネチャ属性</span><span class="sxs-lookup"><span data-stu-id="86932-134">Signature attribute</span></span>  
  
|<span data-ttu-id="86932-135">値</span><span class="sxs-lookup"><span data-stu-id="86932-135">Value</span></span>|<span data-ttu-id="86932-136">説明</span><span class="sxs-lookup"><span data-stu-id="86932-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86932-137">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="86932-137">*method_signature*</span></span>|<span data-ttu-id="86932-138">メソッド シグネチャを形成するパラメーター型です。</span><span class="sxs-lookup"><span data-stu-id="86932-138">The parameter types that form the method signature.</span></span> <span data-ttu-id="86932-139">複数のパラメーターは、`"System.String,System.Int32,System.Int32)"` のようにコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="86932-139">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="86932-140">パラメーターの型名は完全修飾されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="86932-140">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="86932-141">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="86932-141">All other attributes</span></span>  
  
|<span data-ttu-id="86932-142">値</span><span class="sxs-lookup"><span data-stu-id="86932-142">Value</span></span>|<span data-ttu-id="86932-143">説明</span><span class="sxs-lookup"><span data-stu-id="86932-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86932-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="86932-144">*policy_setting*</span></span>|<span data-ttu-id="86932-145">このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="86932-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="86932-146">指定できる値は、`Auto`、`Excluded`、`Included`、および `Required` です。</span><span class="sxs-lookup"><span data-stu-id="86932-146">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="86932-147">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86932-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86932-148">子要素</span><span class="sxs-lookup"><span data-stu-id="86932-148">Child Elements</span></span>  
  
|<span data-ttu-id="86932-149">要素</span><span class="sxs-lookup"><span data-stu-id="86932-149">Element</span></span>|<span data-ttu-id="86932-150">説明</span><span class="sxs-lookup"><span data-stu-id="86932-150">Description</span></span>|  
|-------------|-----------------|  
|[\<Parameter>](parameter-element-net-native.md)|<span data-ttu-id="86932-151">メソッドに渡された引数の型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="86932-151">Applies policy to the type of the argument passed to a method.</span></span>|  
|[\<GenericParameter>](genericparameter-element-net-native.md)|<span data-ttu-id="86932-152">ジェネリック型またはメソッドのパラメーターの型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="86932-152">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[\<ImpliesType>](impliestype-element-net-native.md)|<span data-ttu-id="86932-153">型にポリシーを適用します (含んでいる `<Method>` 要素によって表されるメソッドにそのポリシーが適用されている場合)。</span><span class="sxs-lookup"><span data-stu-id="86932-153">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[\<TypeParameter>](typeparameter-element-net-native.md)|<span data-ttu-id="86932-154">メソッドに渡された <xref:System.Type> 引数によって表される型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="86932-154">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="86932-155">親要素</span><span class="sxs-lookup"><span data-stu-id="86932-155">Parent Elements</span></span>  
  
|<span data-ttu-id="86932-156">要素</span><span class="sxs-lookup"><span data-stu-id="86932-156">Element</span></span>|<span data-ttu-id="86932-157">説明</span><span class="sxs-lookup"><span data-stu-id="86932-157">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="86932-158">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="86932-158">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="86932-159">構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="86932-159">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86932-160">解説</span><span class="sxs-lookup"><span data-stu-id="86932-160">Remarks</span></span>  

 <span data-ttu-id="86932-161">ジェネリック メソッドの `<Method>` 要素は、独自のポリシーを持たないインスタンス化すべてにそのポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="86932-161">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="86932-162">`Signature` 属性を使用して、特定のメソッド オーバーロードのポリシーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="86932-162">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="86932-163">そうしない場合、`Signature` 属性が存在しないと、メソッドのすべてのオーバーロードにランタイム ディレクティブが適用されます。</span><span class="sxs-lookup"><span data-stu-id="86932-163">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="86932-164">`<Method>` 要素を使用してコンストラクターのランタイム リフレクション ポリシーを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="86932-164">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="86932-165">代わりに、、、 `Activate`  [\<Assembly>](assembly-element-net-native.md) [\<Namespace>](namespace-element-net-native.md) [\<Type>](type-element-net-native.md) 、または要素の属性を使用 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) します。</span><span class="sxs-lookup"><span data-stu-id="86932-165">Instead, use the `Activate` attribute of the  [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), [\<Type>](type-element-net-native.md), or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86932-166">例</span><span class="sxs-lookup"><span data-stu-id="86932-166">Example</span></span>  

 <span data-ttu-id="86932-167">次の例の `Stringify` メソッドは、リフレクションを使用してオブジェクトを文字列形式に変換する汎用書式設定メソッドです。</span><span class="sxs-lookup"><span data-stu-id="86932-167">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="86932-168">オブジェクトの既定の `ToString` メソッドを呼び出すことに加えて、このメソッドでは、オブジェクトの `ToString` メソッドに書式文字列、<xref:System.IFormatProvider> 実装、またはその両方を渡して、書式設定された結果文字列を生成できます。</span><span class="sxs-lookup"><span data-stu-id="86932-168">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="86932-169">また、数値をバイナリ、16 進数、または 8 進数形式に変換するいずれかの <xref:System.Convert.ToString%2A?displayProperty=nameWithType> オーバーロードを呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="86932-169">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="86932-170">`Stringify` メソッドは、次のようなコードによって呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="86932-170">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="86932-171">ただし、.NET ネイティブでコンパイルした場合、この例は <xref:System.NullReferenceException> や [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) などの例外を実行時にスローする可能性があります。このことは、`Stringify` メソッドが、主に .NET Framework クラス ライブラリでプリミティブ型の動的な書式設定をサポートするものであるために発生します。</span><span class="sxs-lookup"><span data-stu-id="86932-171">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="86932-172">ただし、既定のディレクティブ ファイルではそのメタデータを使用できません。</span><span class="sxs-lookup"><span data-stu-id="86932-172">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="86932-173">メタデータが使用できたとしても、適切な `ToString` の実装がネイティブ コードに含まれていないため、この例は [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="86932-173">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="86932-174">これらの例外をすべて排除するには、要素を使用して [\<Type>](type-element-net-native.md) メタデータが存在する必要がある型を定義し、要素を追加して `<Method>` 動的に呼び出すことができるメソッドオーバーロードの実装も存在するようにします。</span><span class="sxs-lookup"><span data-stu-id="86932-174">These exceptions can all be eliminated by using the [\<Type>](type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="86932-175">これらの例外を排除し、例をエラーなしで実行できるようにした default.rd.xml ファイルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="86932-175">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <Assembly Name="*Application*" Dynamic="Required All" />  
  
     <Type Name = "System.Convert" Browse="Required Public" Dynamic="Required Public" >  
        <Method Name="ToString"    Dynamic ="Required" />  
     </Type>  
     <Type Name="System.Double" Browse="Required Public">  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int32" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int64" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Namespace Name="System" >  
        <Type Name="Byte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="DateTime" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Decimal" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Guid" Browse ="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Int16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="SByte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Single" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="TimeSpan" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="UInt16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt32" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt64" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
     </Namespace>  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="86932-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="86932-176">See also</span></span>

- [<span data-ttu-id="86932-177">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="86932-177">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="86932-178">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="86932-178">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="86932-179">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="86932-179">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="86932-180">\<MethodInstantiation> 要素</span><span class="sxs-lookup"><span data-stu-id="86932-180">\<MethodInstantiation> Element</span></span>](methodinstantiation-element-net-native.md)
