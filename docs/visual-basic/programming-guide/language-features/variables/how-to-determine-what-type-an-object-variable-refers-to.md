---
description: '詳細情報: 方法:オブジェクト変数で参照している型を確認する (Visual Basic)'
title: '方法: オブジェクト変数で参照している型を確認する'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 699a8c5c075fc923a61a66f617c255f193cd8797
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481923"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="76eb0-103">方法: オブジェクト変数で参照している型を確認する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76eb0-103">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>

<span data-ttu-id="76eb0-104">オブジェクト変数には、他の場所に格納されているデータへのポインターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="76eb0-104">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="76eb0-105">データの種類は、実行時に変更可能です。</span><span class="sxs-lookup"><span data-stu-id="76eb0-105">The type of that data can change during run time.</span></span> <span data-ttu-id="76eb0-106">いつでも、<xref:System.Type.GetTypeCode%2A> メソッドを使用して現在の実行時型を確認できます。[TypeOf 演算子](../../../language-reference/operators/typeof-operator.md) を使用して、現在の実行時型が、指定した型と互換性があるかどうかを調べることもできます。</span><span class="sxs-lookup"><span data-stu-id="76eb0-106">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="76eb0-107">オブジェクト変数で現在参照している正確な型を確認するには</span><span class="sxs-lookup"><span data-stu-id="76eb0-107">To determine the exact type an object variable currently refers to</span></span>

1. <span data-ttu-id="76eb0-108">オブジェクト変数で、<xref:System.Object.GetType%2A> メソッドを呼び出して、<xref:System.Type?displayProperty=nameWithType> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="76eb0-108">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <span data-ttu-id="76eb0-109"><xref:System.Type?displayProperty=nameWithType> クラスで、共有メソッド <xref:System.Type.GetTypeCode%2A> を呼び出して、オブジェクトの型の <xref:System.TypeCode> 列挙値を取得します。</span><span class="sxs-lookup"><span data-stu-id="76eb0-109">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <span data-ttu-id="76eb0-110"><xref:System.TypeCode> 列挙値は、`Double` など、目的の列挙メンバーに対してテストできます。</span><span class="sxs-lookup"><span data-stu-id="76eb0-110">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="76eb0-111">オブジェクト変数の型が、指定した型と互換性があるかどうかを判断するには</span><span class="sxs-lookup"><span data-stu-id="76eb0-111">To determine whether an object variable's type is compatible with a specified type</span></span>

- <span data-ttu-id="76eb0-112">`TypeOf` 演算子を [Is 演算子](../../../language-reference/operators/is-operator.md)と組み合わせて使用して、`TypeOf`...`Is` 式でオブジェクトをテストします。</span><span class="sxs-lookup"><span data-stu-id="76eb0-112">Use the `TypeOf` operator in combination with the [Is Operator](../../../language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    <span data-ttu-id="76eb0-113">`TypeOf`...`Is` 式では、オブジェクトの実行時型が、指定した型と互換性がある場合に `True` が返されます。</span><span class="sxs-lookup"><span data-stu-id="76eb0-113">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>

    <span data-ttu-id="76eb0-114">互換性の基準は、指定した型がクラス、構造体、またはインターフェイスのいずれであるかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="76eb0-114">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="76eb0-115">一般に、オブジェクトが、指定した型と同じ型である、指定した型を継承する、または実装する場合、その型は互換性があります。</span><span class="sxs-lookup"><span data-stu-id="76eb0-115">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="76eb0-116">詳細については、「[TypeOf 演算子](../../../language-reference/operators/typeof-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76eb0-116">For more information, see [TypeOf Operator](../../../language-reference/operators/typeof-operator.md).</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="76eb0-117">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="76eb0-117">Compile the code</span></span>

<span data-ttu-id="76eb0-118">指定する型を変数または式にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="76eb0-118">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="76eb0-119">クラス、構造体、インターフェイスなど、定義済みの型の名前である必要があります。</span><span class="sxs-lookup"><span data-stu-id="76eb0-119">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="76eb0-120">これには、`Integer` や `String` などの組み込み型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="76eb0-120">This includes intrinsic types such as `Integer` and `String`.</span></span>

## <a name="see-also"></a><span data-ttu-id="76eb0-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="76eb0-121">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="76eb0-122">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="76eb0-122">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="76eb0-123">オブジェクト変数の値</span><span class="sxs-lookup"><span data-stu-id="76eb0-123">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="76eb0-124">Object 型</span><span class="sxs-lookup"><span data-stu-id="76eb0-124">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
