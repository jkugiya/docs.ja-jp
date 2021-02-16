---
description: '詳細情報: AttributeUsage (Visual Basic)'
title: AttributeUsage
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: afb043c1b16da3e134888a38ec73f0b6f4ec5f58
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437814"
---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="cb219-103">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb219-103">AttributeUsage (Visual Basic)</span></span>

<span data-ttu-id="cb219-104">カスタム属性クラスの使用方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="cb219-104">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="cb219-105">`AttributeUsage` は、カスタム属性の定義に適用して新しい属性の適用方法を制御できる属性です。</span><span class="sxs-lookup"><span data-stu-id="cb219-105">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="cb219-106">明示的に適用するときの既定の設定は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="cb219-106">The default settings look like this when applied explicitly:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.All,
                   AllowMultiple:=False,
                   Inherited:=True)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

<span data-ttu-id="cb219-107">この例では、属性にできる任意のコード エンティティに `NewAttribute` クラスを適用できますが、各エンティティに適用できるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="cb219-107">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="cb219-108">基底クラスに適用すると、派生クラスによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="cb219-108">It is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="cb219-109">`AllowMultiple` 引数と `Inherited` 引数は省略できるので、次のコードは同じ効果を持ちます。</span><span class="sxs-lookup"><span data-stu-id="cb219-109">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.All)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

<span data-ttu-id="cb219-110">最初の `AttributeUsage` 引数は、<xref:System.AttributeTargets> 列挙型の 1 つまたは複数の要素でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="cb219-110">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="cb219-111">次のように、複数のターゲット型を OR 演算子で 1 つにまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="cb219-111">Multiple target types can be linked together with the OR operator, like this:</span></span>

```vb
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>
Class NewPropertyOrFieldAttribute
    Inherits Attribute
End Class
```

<span data-ttu-id="cb219-112">`AllowMultiple` 引数を `true` に設定すると、次のように、結果の属性を 1 つのエンティティに複数回適用できます。</span><span class="sxs-lookup"><span data-stu-id="cb219-112">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>

```vb
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>
Class MultiUseAttr
    Inherits Attribute
End Class

<MultiUseAttr(), MultiUseAttr()>
Class Class1
End Class
```

<span data-ttu-id="cb219-113">この例では、`AllowMultiple` が `true` に設定されているので、`MultiUseAttr` を繰り返し適用できます。</span><span class="sxs-lookup"><span data-stu-id="cb219-113">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="cb219-114">示されているどちらの形式でも、複数の属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="cb219-114">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="cb219-115">`Inherited` を `false` に設定すると、属性化されたクラスから派生するクラスは属性を継承しません。</span><span class="sxs-lookup"><span data-stu-id="cb219-115">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="cb219-116">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="cb219-116">For example:</span></span>

```vb
<AttributeUsage(AttributeTargets.Class, Inherited:=False)>
Class Attr1
    Inherits Attribute
End Class

<Attr1()>
Class BClass

End Class

Class DClass
    Inherits BClass
End Class
```

<span data-ttu-id="cb219-117">この例では、`Attr1` は継承によって `DClass` に適用されません。</span><span class="sxs-lookup"><span data-stu-id="cb219-117">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="cb219-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="cb219-118">Remarks</span></span>

<span data-ttu-id="cb219-119">`AttributeUsage` 属性は、1 回だけ使用できる属性です。同じクラスに複数回適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="cb219-119">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="cb219-120">`AttributeUsage` は <xref:System.AttributeUsageAttribute> の別名です。</span><span class="sxs-lookup"><span data-stu-id="cb219-120">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="cb219-121">詳細については、「[リフレクションを使用した属性へのアクセス (Visual Basic)](accessing-attributes-by-using-reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb219-121">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="cb219-122">例</span><span class="sxs-lookup"><span data-stu-id="cb219-122">Example</span></span>

<span data-ttu-id="cb219-123">次の例を見ると、`AttributeUsage` 属性に対する `Inherited` 引数と `AllowMultiple` 引数の効果、およびクラスに適用されているカスタム属性の列挙方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="cb219-123">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

```vb
' Create some custom attributes:
<AttributeUsage(System.AttributeTargets.Class, Inherited:=False)>
Class A1
    Inherits System.Attribute
End Class

<AttributeUsage(System.AttributeTargets.Class)>
Class A2
    Inherits System.Attribute
End Class

<AttributeUsage(System.AttributeTargets.Class, AllowMultiple:=True)>
Class A3
    Inherits System.Attribute
End Class

' Apply custom attributes to classes:
<A1(), A2()>
Class BaseClass

End Class

<A3(), A3()>
Class DerivedClass
    Inherits BaseClass
End Class

Public Class TestAttributeUsage
    Sub Main()
        Dim b As New BaseClass
        Dim d As New DerivedClass
        ' Display custom attributes for each class.
        Console.WriteLine("Attributes on Base Class:")
        Dim attrs() As Object = b.GetType().GetCustomAttributes(True)

        For Each attr In attrs
            Console.WriteLine(attr)
        Next

        Console.WriteLine("Attributes on Derived Class:")
        attrs = d.GetType().GetCustomAttributes(True)
        For Each attr In attrs
            Console.WriteLine(attr)
        Next
    End Sub
End Class
```

## <a name="sample-output"></a><span data-ttu-id="cb219-124">出力例</span><span class="sxs-lookup"><span data-stu-id="cb219-124">Sample Output</span></span>

```console
Attributes on Base Class:
A1
A2
Attributes on Derived Class:
A3
A3
A2
```

## <a name="see-also"></a><span data-ttu-id="cb219-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb219-125">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="cb219-126">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="cb219-126">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="cb219-127">属性</span><span class="sxs-lookup"><span data-stu-id="cb219-127">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="cb219-128">リフレクション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb219-128">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="cb219-129">属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb219-129">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="cb219-130">カスタム属性の作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb219-130">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="cb219-131">リフレクションを使用した属性へのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb219-131">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
