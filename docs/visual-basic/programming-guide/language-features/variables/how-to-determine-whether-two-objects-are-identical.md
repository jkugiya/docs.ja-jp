---
description: '詳細情報: 方法:2 つのオブジェクトが同一であるかどうかを判別する (Visual Basic)'
title: '方法: 2 つのオブジェクトが同一であるかどうかを判別する'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 91f431b5a7e4cf51135c060ca0aebf1b3b968b25
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481897"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="6dd83-103">方法: 2 つのオブジェクトが同一であるかどうかを判別する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6dd83-103">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>

<span data-ttu-id="6dd83-104">Visual Basic において 2 つの変数参照は、それらのポインターが同じである場合、つまり、両方の変数がメモリ内の同じクラス インスタンスを指している場合、同一であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="6dd83-104">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="6dd83-105">たとえば、Windows フォーム アプリケーションでは、現在のインスタンス (`Me`) が `Form2` などの特定のインスタンスと同じであるかどうかを判別するために比較を行いたい場合があります。</span><span class="sxs-lookup"><span data-stu-id="6dd83-105">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="6dd83-106">Visual Basic には、ポインターを比較するための演算子が 2 つ用意されています。</span><span class="sxs-lookup"><span data-stu-id="6dd83-106">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="6dd83-107">オブジェクトが同一である場合には、[Is 演算子](../../../language-reference/operators/is-operator.md) から `True` が返され、そうでない場合には [IsNot 演算子](../../../language-reference/operators/isnot-operator.md) から `True` が返されます。</span><span class="sxs-lookup"><span data-stu-id="6dd83-107">The [Is Operator](../../../language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="6dd83-108">2 つのオブジェクトが同一であるかどうかを判別する</span><span class="sxs-lookup"><span data-stu-id="6dd83-108">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="6dd83-109">2 つのオブジェクトが同一であるかどうかを確認するには</span><span class="sxs-lookup"><span data-stu-id="6dd83-109">To determine if two objects are identical</span></span>  
  
1. <span data-ttu-id="6dd83-110">2 つのオブジェクトをテストするための `Boolean` 式を設定します。</span><span class="sxs-lookup"><span data-stu-id="6dd83-110">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="6dd83-111">テスト式では、2 つのオブジェクトをオペランドとする `Is` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="6dd83-111">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="6dd83-112">各オブジェクトがいずれも同じクラス インスタンスを指している場合は、`Is` から `True` が返されます。</span><span class="sxs-lookup"><span data-stu-id="6dd83-112">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="6dd83-113">2 つのオブジェクトが同一でないかどうかを判別する</span><span class="sxs-lookup"><span data-stu-id="6dd83-113">Determining if Two Objects Are Not Identical</span></span>  

 <span data-ttu-id="6dd83-114">2 つのオブジェクトが同一でない場合にアクションの実行が必要なことがあります。しかし、たとえば、`If Not obj1 Is obj2` のように `Not` と `Is` を組み合わせて使用するのは不便です。</span><span class="sxs-lookup"><span data-stu-id="6dd83-114">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="6dd83-115">そのような場合は、`IsNot` 演算子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6dd83-115">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="6dd83-116">2 つのオブジェクトが同一でないかどうかを調べるには</span><span class="sxs-lookup"><span data-stu-id="6dd83-116">To determine if two objects are not identical</span></span>  
  
1. <span data-ttu-id="6dd83-117">2 つのオブジェクトをテストするための `Boolean` 式を設定します。</span><span class="sxs-lookup"><span data-stu-id="6dd83-117">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="6dd83-118">テスト式では、2 つのオブジェクトをオペランドとする `IsNot` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="6dd83-118">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="6dd83-119">各オブジェクトが指しているクラス インスタンスが同じでない場合は、`IsNot` から `True` が返されます。</span><span class="sxs-lookup"><span data-stu-id="6dd83-119">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dd83-120">例</span><span class="sxs-lookup"><span data-stu-id="6dd83-120">Example</span></span>  

 <span data-ttu-id="6dd83-121">次の例では、`Object` 変数のペアをテストして、それらが同じクラス インスタンスを指しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="6dd83-121">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 <span data-ttu-id="6dd83-122">上記の例では、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6dd83-122">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="6dd83-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="6dd83-123">See also</span></span>

- [<span data-ttu-id="6dd83-124">Object 型</span><span class="sxs-lookup"><span data-stu-id="6dd83-124">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="6dd83-125">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="6dd83-125">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="6dd83-126">オブジェクト変数の値</span><span class="sxs-lookup"><span data-stu-id="6dd83-126">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="6dd83-127">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="6dd83-127">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="6dd83-128">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="6dd83-128">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="6dd83-129">方法: 2 つのオブジェクトが関連しているかどうかを判別する</span><span class="sxs-lookup"><span data-stu-id="6dd83-129">How to: Determine Whether Two Objects Are Related</span></span>](how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="6dd83-130">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="6dd83-130">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
