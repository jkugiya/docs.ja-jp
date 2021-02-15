---
description: '詳細情報: 属性の概要 (Visual Basic)'
title: 属性の概要
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: f25e69452f0af1c89af667619e673f8906704d1f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437723"
---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="39a2f-103">属性の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39a2f-103">Attributes overview (Visual Basic)</span></span>

<span data-ttu-id="39a2f-104">属性は、メタデータまたは宣言型の情報を、コード (アセンブリ、型、メソッド、プロパティなど) に関連付けるための優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="39a2f-104">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="39a2f-105">属性をプログラム要素に関連付けると、*リフレクション* と呼ばれる手法を使用して、実行時にその属性を照会することができます。</span><span class="sxs-lookup"><span data-stu-id="39a2f-105">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="39a2f-106">詳細については、「[リフレクション (Visual Basic)](../reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39a2f-106">For more information, see [Reflection (Visual Basic)](../reflection.md).</span></span>

<span data-ttu-id="39a2f-107">属性には、次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="39a2f-107">Attributes have the following properties:</span></span>

- <span data-ttu-id="39a2f-108">属性は、プログラムにメタデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-108">Attributes add metadata to your program.</span></span> <span data-ttu-id="39a2f-109">*メタデータ* は、プログラムで定義された型に関する情報です。</span><span class="sxs-lookup"><span data-stu-id="39a2f-109">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="39a2f-110">すべての .NET アセンブリには、アセンブリで定義された型および型のメンバーを記述する、指定されたメタデータのセットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="39a2f-110">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="39a2f-111">カスタム属性を追加して、必要な追加情報を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="39a2f-111">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="39a2f-112">詳細については、「[カスタム属性の作成 (Visual Basic)](creating-custom-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39a2f-112">For more information, see, [Creating Custom Attributes (Visual Basic)](creating-custom-attributes.md).</span></span>

- <span data-ttu-id="39a2f-113">属性は、アセンブリ全体、モジュール、またはクラスやプロパティなどのより小さいプログラム要素に 1 つ以上適用することができます。</span><span class="sxs-lookup"><span data-stu-id="39a2f-113">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>

- <span data-ttu-id="39a2f-114">属性は、メソッドやプロパティと同じ方法で引数を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="39a2f-114">Attributes can accept arguments in the same way as methods and properties.</span></span>

- <span data-ttu-id="39a2f-115">リフレクションを使用して、プログラム自身のメタデータや他のプログラムのメタデータを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="39a2f-115">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="39a2f-116">詳細については、「[リフレクションを使用した属性へのアクセス (Visual Basic)](accessing-attributes-by-using-reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39a2f-116">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="39a2f-117">属性の使用</span><span class="sxs-lookup"><span data-stu-id="39a2f-117">Using Attributes</span></span>

<span data-ttu-id="39a2f-118">属性は、ほぼすべての宣言に配置できますが、属性によっては、有効な宣言の型が制限されている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="39a2f-118">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="39a2f-119">Visual Basic では、属性は山かっこ (\< >) で囲み、</span><span class="sxs-lookup"><span data-stu-id="39a2f-119">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="39a2f-120">同じ行の、適用先の要素の直前に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39a2f-120">It must appear immediately before the element to which it is applied, on the same line.</span></span>

<span data-ttu-id="39a2f-121">この例では、<xref:System.SerializableAttribute> 属性を使用してクラスに特性を適用します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-121">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

```vb
<System.Serializable()> Public Class SampleClass
    ' Objects of this type can be serialized.
End Class
```

 <span data-ttu-id="39a2f-122">属性 <xref:System.Runtime.InteropServices.DllImportAttribute> を持つメソッドは次のように宣言されます。</span><span class="sxs-lookup"><span data-stu-id="39a2f-122">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>

```vb
Imports System.Runtime.InteropServices
```

```vb
<System.Runtime.InteropServices.DllImport("user32.dll")>
Sub SampleMethod()
End Sub
```

<span data-ttu-id="39a2f-123">宣言には、複数の属性を配置できます。</span><span class="sxs-lookup"><span data-stu-id="39a2f-123">More than one attribute can be placed on a declaration:</span></span>

```vb
Imports System.Runtime.InteropServices
```

```vb
Sub MethodA(<[In](), Out()> ByVal x As Double)
End Sub
Sub MethodB(<Out(), [In]()> ByVal x As Double)
End Sub
```

<span data-ttu-id="39a2f-124">特定のエンティティで複数回指定できる属性もあります。</span><span class="sxs-lookup"><span data-stu-id="39a2f-124">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="39a2f-125">このような複数回指定できる属性の例として <xref:System.Diagnostics.ConditionalAttribute> があります。</span><span class="sxs-lookup"><span data-stu-id="39a2f-125">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

```vb
<Conditional("DEBUG"), Conditional("TEST1")>
Sub TraceMethod()
End Sub
```

> [!NOTE]
> <span data-ttu-id="39a2f-126">慣例により、属性名はすべて "Attribute" という単語で終わります。これは、.NET Framework の他の項目と区別するためです。</span><span class="sxs-lookup"><span data-stu-id="39a2f-126">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="39a2f-127">ただし、コード内で属性を使用する場合は、attribute サフィックスを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="39a2f-127">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="39a2f-128">たとえば、`[DllImport]` は `[DllImportAttribute]` と同等ですが、.NET Framework では `DllImportAttribute` は属性の実際の名前を表します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-128">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="39a2f-129">属性のパラメーター</span><span class="sxs-lookup"><span data-stu-id="39a2f-129">Attribute Parameters</span></span>

<span data-ttu-id="39a2f-130">属性の多くは、位置指定パラメーター、名前のないパラメーター、または名前付きパラメーターを持っています。</span><span class="sxs-lookup"><span data-stu-id="39a2f-130">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="39a2f-131">位置指定パラメーターは、特定の順序で指定する必要があり、省略できません。名前付きパラメーターは省略可能で、任意の順序で指定することができます。</span><span class="sxs-lookup"><span data-stu-id="39a2f-131">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="39a2f-132">位置指定パラメーターは、最初に指定します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-132">Positional parameters are specified first.</span></span> <span data-ttu-id="39a2f-133">たとえば、次の 3 つの属性は同等です。</span><span class="sxs-lookup"><span data-stu-id="39a2f-133">For example, these three attributes are equivalent:</span></span>

```vb
<DllImport("user32.dll")>
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>
```

<span data-ttu-id="39a2f-134">最初のパラメーターである DLL 名は位置指定パラメーターであり、常に最初に指定されます。他のパラメーターは名前付きパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="39a2f-134">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="39a2f-135">この例の場合、名前付きパラメーターの既定値はどちらも false なので、省略することができます。</span><span class="sxs-lookup"><span data-stu-id="39a2f-135">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="39a2f-136">パラメーターの既定値については、個々の属性のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39a2f-136">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="39a2f-137">属性の対象</span><span class="sxs-lookup"><span data-stu-id="39a2f-137">Attribute Targets</span></span>

<span data-ttu-id="39a2f-138">属性の *対象* は、属性が適用されるエンティティです。</span><span class="sxs-lookup"><span data-stu-id="39a2f-138">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="39a2f-139">たとえば、属性は、クラス、特定のメソッド、またはアセンブリ全体に適用できます。</span><span class="sxs-lookup"><span data-stu-id="39a2f-139">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="39a2f-140">既定では、属性は後に続く要素に適用されます。</span><span class="sxs-lookup"><span data-stu-id="39a2f-140">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="39a2f-141">ただし、明示的に指定すれば、メソッド、属性のパラメーター、属性の戻り値などにも適用できます。</span><span class="sxs-lookup"><span data-stu-id="39a2f-141">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="39a2f-142">属性の対象を明示的に識別するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-142">To explicitly identify an attribute target, use the following syntax:</span></span>

```vb
<target : attribute-list>
```

<span data-ttu-id="39a2f-143">次の表に、使用可能な `target` の値を示します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-143">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="39a2f-144">対象の値</span><span class="sxs-lookup"><span data-stu-id="39a2f-144">Target value</span></span>|<span data-ttu-id="39a2f-145">対象</span><span class="sxs-lookup"><span data-stu-id="39a2f-145">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="39a2f-146">アセンブリ全体</span><span class="sxs-lookup"><span data-stu-id="39a2f-146">Entire assembly</span></span>|
|`module`|<span data-ttu-id="39a2f-147">現在のアセンブリ モジュール (Visual Basic のモジュールとは異なります)</span><span class="sxs-lookup"><span data-stu-id="39a2f-147">Current assembly module (which is different from a Visual Basic Module)</span></span>|

 <span data-ttu-id="39a2f-148">次の例では、アセンブリとモジュールに属性を適用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-148">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="39a2f-149">詳細については、「[共通の属性 (Visual Basic)](common-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39a2f-149">For more information, see [Common Attributes (Visual Basic)](common-attributes.md).</span></span>

```vb
Imports System.Reflection
<Assembly: AssemblyTitleAttribute("Production assembly 4"),
Module: CLSCompliant(True)>
```

## <a name="common-uses-for-attributes"></a><span data-ttu-id="39a2f-150">属性の一般的な使用法</span><span class="sxs-lookup"><span data-stu-id="39a2f-150">Common Uses for Attributes</span></span>

<span data-ttu-id="39a2f-151">次の表に、コードでの属性の一般的な使用法をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-151">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="39a2f-152">Web サービスの `WebMethod` 属性を使用してメソッドをマークして、メソッドが SOAP プロトコルを介して呼び出されるようにします。</span><span class="sxs-lookup"><span data-stu-id="39a2f-152">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="39a2f-153">詳細については、「<xref:System.Web.Services.WebMethodAttribute>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39a2f-153">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>

- <span data-ttu-id="39a2f-154">ネイティブ コードと相互運用するときにメソッドのパラメーターをマーシャリングする方法を記述します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-154">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="39a2f-155">詳細については、「<xref:System.Runtime.InteropServices.MarshalAsAttribute>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39a2f-155">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

- <span data-ttu-id="39a2f-156">クラス、メソッド、およびインターフェイスの COM プロパティを記述します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-156">Describing the COM properties for classes, methods, and interfaces.</span></span>

- <span data-ttu-id="39a2f-157"><xref:System.Runtime.InteropServices.DllImportAttribute> クラスを使用してアンマネージ コードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-157">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>

- <span data-ttu-id="39a2f-158">タイトル、バージョン、説明、または商標についてのアセンブリを記述します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-158">Describing your assembly in terms of title, version, description, or trademark.</span></span>

- <span data-ttu-id="39a2f-159">永続化のためにシリアル化するクラスのメンバーを記述します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-159">Describing which members of a class to serialize for persistence.</span></span>

- <span data-ttu-id="39a2f-160">XML シリアル化のためにクラス メンバーと XML ノード間をマップする方法を記述します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-160">Describing how to map between class members and XML nodes for XML serialization.</span></span>

- <span data-ttu-id="39a2f-161">メソッドのセキュリティ要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-161">Describing the security requirements for methods.</span></span>

- <span data-ttu-id="39a2f-162">セキュリティを適用するための特性を指定します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-162">Specifying characteristics used to enforce security.</span></span>

- <span data-ttu-id="39a2f-163">コードを容易にデバッグできる状態に保つために、ジャスト イン タイム (JIT) コンパイラによって最適化を制御します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-163">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>

- <span data-ttu-id="39a2f-164">メソッドの呼び出し元に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="39a2f-164">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="39a2f-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="39a2f-165">Related Sections</span></span>

<span data-ttu-id="39a2f-166">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="39a2f-166">For more information, see:</span></span>

- [<span data-ttu-id="39a2f-167">カスタム属性の作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39a2f-167">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)

- [<span data-ttu-id="39a2f-168">リフレクションを使用した属性へのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39a2f-168">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)

- [<span data-ttu-id="39a2f-169">方法: 属性を使用して C/C++ の共用体を作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39a2f-169">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)

- [<span data-ttu-id="39a2f-170">一般的な属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39a2f-170">Common Attributes (Visual Basic)</span></span>](common-attributes.md)

- [<span data-ttu-id="39a2f-171">呼び出し元情報 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39a2f-171">Caller Information (Visual Basic)</span></span>](../caller-information.md)

## <a name="see-also"></a><span data-ttu-id="39a2f-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="39a2f-172">See also</span></span>

- [<span data-ttu-id="39a2f-173">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="39a2f-173">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="39a2f-174">リフレクション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39a2f-174">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="39a2f-175">属性</span><span class="sxs-lookup"><span data-stu-id="39a2f-175">Attributes</span></span>](../../../../standard/attributes/index.md)
