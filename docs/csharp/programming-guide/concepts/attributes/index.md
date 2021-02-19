---
title: 属性 (C#)
description: 属性を使用して、メタデータまたは宣言情報を C# のコードに関連付ける方法について説明します。 属性は、実行時にリフレクションを使用してクエリできます。
ms.date: 04/26/2018
ms.openlocfilehash: f468b01d3f7832ed8c127f34e6d4e3c1bcf7901a
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100583673"
---
# <a name="attributes-c"></a><span data-ttu-id="c5731-104">属性 (C#)</span><span class="sxs-lookup"><span data-stu-id="c5731-104">Attributes (C#)</span></span>

<span data-ttu-id="c5731-105">属性は、メタデータまたは宣言型の情報を、コード (アセンブリ、型、メソッド、プロパティなど) に関連付けるための優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="c5731-105">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="c5731-106">属性をプログラム要素に関連付けると、*リフレクション* と呼ばれる手法を使用して、実行時にその属性を照会することができます。</span><span class="sxs-lookup"><span data-stu-id="c5731-106">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="c5731-107">詳細については、「[リフレクション (C#)](../reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5731-107">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="c5731-108">属性には、次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="c5731-108">Attributes have the following properties:</span></span>

- <span data-ttu-id="c5731-109">属性は、プログラムにメタデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="c5731-109">Attributes add metadata to your program.</span></span> <span data-ttu-id="c5731-110">*メタデータ* は、プログラムで定義された型に関する情報です。</span><span class="sxs-lookup"><span data-stu-id="c5731-110">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="c5731-111">すべての .NET アセンブリには、アセンブリで定義された型および型のメンバーを記述する、指定されたメタデータのセットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c5731-111">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="c5731-112">カスタム属性を追加して、必要な追加情報を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="c5731-112">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="c5731-113">詳細については、「[カスタム属性の作成 (C#)](creating-custom-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5731-113">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="c5731-114">属性は、アセンブリ全体、モジュール、またはクラスやプロパティなどのより小さいプログラム要素に 1 つ以上適用することができます。</span><span class="sxs-lookup"><span data-stu-id="c5731-114">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="c5731-115">属性は、メソッドやプロパティと同じ方法で引数を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="c5731-115">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="c5731-116">リフレクションを使用して、プログラム自身のメタデータや他のプログラムのメタデータを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="c5731-116">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="c5731-117">詳しくは、「[リフレクションを使用した属性へのアクセス (C#)](accessing-attributes-by-using-reflection.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c5731-117">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="c5731-118">属性の使用</span><span class="sxs-lookup"><span data-stu-id="c5731-118">Using attributes</span></span>

<span data-ttu-id="c5731-119">属性は、ほぼすべての宣言に配置できますが、属性によっては、有効な宣言の型が制限されている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="c5731-119">Attributes can be placed on almost any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="c5731-120">C# では、角かっこ ([]) で囲んだ属性の名前を、適用先のエンティティの宣言の前に配置して、属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5731-120">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="c5731-121">この例では、<xref:System.SerializableAttribute> 属性を使用してクラスに特性を適用します。</span><span class="sxs-lookup"><span data-stu-id="c5731-121">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="c5731-122">属性 <xref:System.Runtime.InteropServices.DllImportAttribute> を持つメソッドは次の例のように宣言されます。</span><span class="sxs-lookup"><span data-stu-id="c5731-122">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="c5731-123">次の例のように、宣言には、複数の属性を配置できます。</span><span class="sxs-lookup"><span data-stu-id="c5731-123">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="c5731-124">特定のエンティティで複数回指定できる属性もあります。</span><span class="sxs-lookup"><span data-stu-id="c5731-124">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="c5731-125">このような複数回指定できる属性の例として <xref:System.Diagnostics.ConditionalAttribute> があります。</span><span class="sxs-lookup"><span data-stu-id="c5731-125">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="c5731-126">慣例により、属性名はすべて "Attribute" という単語で終わります。これは、.NET ライブラリの他の項目と区別するためです。</span><span class="sxs-lookup"><span data-stu-id="c5731-126">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="c5731-127">ただし、コード内で属性を使用する場合は、attribute サフィックスを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c5731-127">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="c5731-128">たとえば、`[DllImport]` は `[DllImportAttribute]` と同等ですが、.NET クラス ライブラリでは `DllImportAttribute` は属性の実際の名前を表します。</span><span class="sxs-lookup"><span data-stu-id="c5731-128">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="c5731-129">属性のパラメーター</span><span class="sxs-lookup"><span data-stu-id="c5731-129">Attribute parameters</span></span>

<span data-ttu-id="c5731-130">属性の多くは、位置指定パラメーター、名前のないパラメーター、または名前付きパラメーターを持っています。</span><span class="sxs-lookup"><span data-stu-id="c5731-130">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="c5731-131">どの位置指定パラメーターも、特定の順序で指定する必要があり、省略することはできません。</span><span class="sxs-lookup"><span data-stu-id="c5731-131">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="c5731-132">名前付きパラメーターは省略可能で、任意の順序で指定することができます。</span><span class="sxs-lookup"><span data-stu-id="c5731-132">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="c5731-133">位置指定パラメーターは、最初に指定します。</span><span class="sxs-lookup"><span data-stu-id="c5731-133">Positional parameters are specified first.</span></span> <span data-ttu-id="c5731-134">たとえば、次の 3 つの属性は同等です。</span><span class="sxs-lookup"><span data-stu-id="c5731-134">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="c5731-135">最初のパラメーターである DLL 名は位置指定パラメーターであり、常に最初に指定されます。他のパラメーターは名前付きパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="c5731-135">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="c5731-136">この例の場合、名前付きパラメーターの既定値はどちらも false なので、省略することができます。</span><span class="sxs-lookup"><span data-stu-id="c5731-136">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="c5731-137">位置指定パラメーターは、属性コンストラクターのパラメーターに対応します。</span><span class="sxs-lookup"><span data-stu-id="c5731-137">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="c5731-138">名前付きまたは省略可能なパラメーターは、属性のプロパティまたはフィールドのどちらかに対応します。</span><span class="sxs-lookup"><span data-stu-id="c5731-138">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="c5731-139">パラメーターの既定値については、個々の属性のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5731-139">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="c5731-140">属性の対象</span><span class="sxs-lookup"><span data-stu-id="c5731-140">Attribute targets</span></span>

<span data-ttu-id="c5731-141">属性の *対象* は、属性が適用されるエンティティです。</span><span class="sxs-lookup"><span data-stu-id="c5731-141">The *target* of an attribute is the entity which the attribute applies to.</span></span> <span data-ttu-id="c5731-142">たとえば、属性は、クラス、特定のメソッド、またはアセンブリ全体に適用できます。</span><span class="sxs-lookup"><span data-stu-id="c5731-142">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="c5731-143">既定では、属性はその後に続く要素に適用されます。</span><span class="sxs-lookup"><span data-stu-id="c5731-143">By default, an attribute applies to the element that follows it.</span></span> <span data-ttu-id="c5731-144">ただし、明示的に指定すれば、メソッド、属性のパラメーター、属性の戻り値などにも適用できます。</span><span class="sxs-lookup"><span data-stu-id="c5731-144">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="c5731-145">属性の対象を明示的に識別するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5731-145">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="c5731-146">次の表に、使用可能な `target` の値を示します。</span><span class="sxs-lookup"><span data-stu-id="c5731-146">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="c5731-147">対象の値</span><span class="sxs-lookup"><span data-stu-id="c5731-147">Target value</span></span>|<span data-ttu-id="c5731-148">対象</span><span class="sxs-lookup"><span data-stu-id="c5731-148">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="c5731-149">アセンブリ全体</span><span class="sxs-lookup"><span data-stu-id="c5731-149">Entire assembly</span></span>|
|`module`|<span data-ttu-id="c5731-150">現在のアセンブリ モジュール</span><span class="sxs-lookup"><span data-stu-id="c5731-150">Current assembly module</span></span>|
|`field`|<span data-ttu-id="c5731-151">クラスまたは構造体のフィールド</span><span class="sxs-lookup"><span data-stu-id="c5731-151">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="c5731-152">event</span><span class="sxs-lookup"><span data-stu-id="c5731-152">Event</span></span>|
|`method`|<span data-ttu-id="c5731-153">メソッドまたは `get` および `set` プロパティ アクセサー</span><span class="sxs-lookup"><span data-stu-id="c5731-153">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="c5731-154">メソッド パラメーターまたは `set` プロパティ アクセサー パラメーター</span><span class="sxs-lookup"><span data-stu-id="c5731-154">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="c5731-155">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c5731-155">Property</span></span>|
|`return`|<span data-ttu-id="c5731-156">メソッド、プロパティ インデクサー、または `get` プロパティ アクセサーの戻り値</span><span class="sxs-lookup"><span data-stu-id="c5731-156">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="c5731-157">構造体、クラス、インターフェイス、列挙型、またはデリゲート</span><span class="sxs-lookup"><span data-stu-id="c5731-157">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="c5731-158">対象の値 `field` を指定して、[auto-implemented プロパティ](../../../properties.md)に作成されたバッキング フィールドに属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="c5731-158">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="c5731-159">次の例では、アセンブリとモジュールに属性を適用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c5731-159">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="c5731-160">詳細については、「[共通の属性 (C#)](../../../language-reference/attributes/global.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5731-160">For more information, see [Common Attributes (C#)](../../../language-reference/attributes/global.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="c5731-161">C# でメソッド、メソッドのパラメーター、およびメソッドの戻り値に属性を適用する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c5731-161">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="c5731-162">`ValidatedContract` が有効になるように定義されるターゲットが何であっても、`return` は指定する必要があります。これは、`ValidatedContract` が戻り値にのみ適用されるように定義されている場合でも必要です。</span><span class="sxs-lookup"><span data-stu-id="c5731-162">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="c5731-163">つまり、コンパイラは `AttributeUsage` 情報を使用して、あいまいな属性ターゲットを解決しません。</span><span class="sxs-lookup"><span data-stu-id="c5731-163">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="c5731-164">詳細については、「[AttributeUsage (C#)](../../../language-reference/attributes/general.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5731-164">For more information, see [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="c5731-165">属性の一般的な使用法</span><span class="sxs-lookup"><span data-stu-id="c5731-165">Common uses for attributes</span></span>

<span data-ttu-id="c5731-166">次の表に、コードでの属性の一般的な使用法をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="c5731-166">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="c5731-167">Web サービスの `WebMethod` 属性を使用してメソッドをマークして、メソッドが SOAP プロトコルを介して呼び出されるようにします。</span><span class="sxs-lookup"><span data-stu-id="c5731-167">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="c5731-168">詳細については、「<xref:System.Web.Services.WebMethodAttribute>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5731-168">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="c5731-169">ネイティブ コードと相互運用するときにメソッドのパラメーターをマーシャリングする方法を記述します。</span><span class="sxs-lookup"><span data-stu-id="c5731-169">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="c5731-170">詳細については、「<xref:System.Runtime.InteropServices.MarshalAsAttribute>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5731-170">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="c5731-171">クラス、メソッド、およびインターフェイスの COM プロパティを記述します。</span><span class="sxs-lookup"><span data-stu-id="c5731-171">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="c5731-172"><xref:System.Runtime.InteropServices.DllImportAttribute> クラスを使用してアンマネージ コードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c5731-172">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="c5731-173">タイトル、バージョン、説明、または商標についてのアセンブリを記述します。</span><span class="sxs-lookup"><span data-stu-id="c5731-173">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="c5731-174">永続化のためにシリアル化するクラスのメンバーを記述します。</span><span class="sxs-lookup"><span data-stu-id="c5731-174">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="c5731-175">XML シリアル化のためにクラス メンバーと XML ノード間をマップする方法を記述します。</span><span class="sxs-lookup"><span data-stu-id="c5731-175">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="c5731-176">メソッドのセキュリティ要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="c5731-176">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="c5731-177">セキュリティを適用するための特性を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5731-177">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="c5731-178">コードを容易にデバッグできる状態に保つために、ジャスト イン タイム (JIT) コンパイラによって最適化を制御します。</span><span class="sxs-lookup"><span data-stu-id="c5731-178">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="c5731-179">メソッドの呼び出し元に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="c5731-179">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="c5731-180">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5731-180">Related sections</span></span>

<span data-ttu-id="c5731-181">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="c5731-181">For more information, see:</span></span>

- [<span data-ttu-id="c5731-182">カスタム属性の作成 (C#)</span><span class="sxs-lookup"><span data-stu-id="c5731-182">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="c5731-183">リフレクションを使用した属性へのアクセス (C#)</span><span class="sxs-lookup"><span data-stu-id="c5731-183">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="c5731-184">属性を使用して C/C++ の共用体を作成する方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="c5731-184">How to create a C/C++ union by using attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="c5731-185">共通属性 (C#)</span><span class="sxs-lookup"><span data-stu-id="c5731-185">Common Attributes (C#)</span></span>](../../../language-reference/attributes/global.md)  
- [<span data-ttu-id="c5731-186">呼び出し元情報 (C#)</span><span class="sxs-lookup"><span data-stu-id="c5731-186">Caller Information (C#)</span></span>](../../../language-reference/attributes/caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="c5731-187">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5731-187">See also</span></span>

- [<span data-ttu-id="c5731-188">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c5731-188">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="c5731-189">リフレクション (C#)</span><span class="sxs-lookup"><span data-stu-id="c5731-189">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="c5731-190">属性</span><span class="sxs-lookup"><span data-stu-id="c5731-190">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="c5731-191">C# での属性の使用</span><span class="sxs-lookup"><span data-stu-id="c5731-191">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)
