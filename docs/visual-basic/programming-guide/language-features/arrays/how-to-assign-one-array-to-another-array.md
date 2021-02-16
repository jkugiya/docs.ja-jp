---
description: '詳細情報: 方法:配列を別の配列に代入する (Visual Basic)'
title: '方法: 配列を別の配列に代入する'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: dc86225c1f25c207e793e33a048d948646ac77b6
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434733"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="b3bcf-103">方法: 配列を別の配列に代入する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3bcf-103">How to: Assign One Array to Another Array (Visual Basic)</span></span>

<span data-ttu-id="b3bcf-104">配列はオブジェクトであるため、他のオブジェクト型と同様に代入ステートメントで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-104">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="b3bcf-105">配列変数に保持されるのは、配列要素と、ランクおよび長さの情報で構成されるデータへのポインターで、このポインターのみが代入によってコピーされます。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-105">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>

### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="b3bcf-106">配列を別の配列に代入するには</span><span class="sxs-lookup"><span data-stu-id="b3bcf-106">To assign one array to another array</span></span>

1. <span data-ttu-id="b3bcf-107">2 つの配列両方が同じランク (次元数) であり、互換性のある要素データ型を持つことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-107">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>

2. <span data-ttu-id="b3bcf-108">標準の代入ステートメントを使用して、ソース配列を宛先配列に代入します。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-108">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="b3bcf-109">どちらの配列名も、後ろにかっこをつけないでください。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-109">Do not follow either array name with parentheses.</span></span>

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

<span data-ttu-id="b3bcf-110">配列を別の配列に代入するときは、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-110">When you assign one array to another, the following rules apply:</span></span>

- <span data-ttu-id="b3bcf-111">**ランクが同じ。**</span><span class="sxs-lookup"><span data-stu-id="b3bcf-111">**Equal Ranks.**</span></span> <span data-ttu-id="b3bcf-112">宛先配列のランク (次元数) は、ソース配列のランクと同じでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-112">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>

  <span data-ttu-id="b3bcf-113">2 つの配列のランクが等しいことが必要であって、次元は同じである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-113">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="b3bcf-114">特定の次元の要素の数は、代入時に変更される場合があります。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-114">The number of elements in a given dimension can change during assignment.</span></span>

- <span data-ttu-id="b3bcf-115">**要素型**。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-115">**Element Types.**</span></span> <span data-ttu-id="b3bcf-116">両方の配列が "*参照型*" 要素を持つか、または両方の配列が "*値型*" 要素を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-116">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="b3bcf-117">詳細については、「 [Value Types and Reference Types](../data-types/value-types-and-reference-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-117">For more information, see [Value Types and Reference Types](../data-types/value-types-and-reference-types.md).</span></span>

  - <span data-ttu-id="b3bcf-118">両方の配列が値型の要素を持つ場合、要素のデータ型はまったく同じでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-118">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="b3bcf-119">ただし、`Enum` 要素の配列を、その `Enum` の基本データ型の配列に代入できる場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-119">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>

  - <span data-ttu-id="b3bcf-120">両方の配列が参照型要素を持つ場合、ソース要素の型は、宛先要素型から派生している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-120">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="b3bcf-121">この場合、2 つの配列の継承関係は、その要素と同じです。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-121">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="b3bcf-122">これは "*配列の共変性*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-122">This is called *array covariance*.</span></span>

<span data-ttu-id="b3bcf-123">上記の規則に違反している場合、たとえば、データ型に互換性がなかったり、ランクが等しくなかったりすると、コンパイラによってエラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-123">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="b3bcf-124">コードにエラー処理を追加すると、代入を試みる前に配列に互換性があることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-124">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="b3bcf-125">[TryCast 演算子](../../../language-reference/operators/trycast-operator.md)キーワードを使って、例外がスローされないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b3bcf-125">You can also use the [TryCast Operator](../../../language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3bcf-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3bcf-126">See also</span></span>

- [<span data-ttu-id="b3bcf-127">配列</span><span class="sxs-lookup"><span data-stu-id="b3bcf-127">Arrays</span></span>](index.md)
- [<span data-ttu-id="b3bcf-128">配列のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b3bcf-128">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="b3bcf-129">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="b3bcf-129">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="b3bcf-130">配列変換</span><span class="sxs-lookup"><span data-stu-id="b3bcf-130">Array Conversions</span></span>](../data-types/array-conversions.md)
