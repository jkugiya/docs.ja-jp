---
description: '詳細情報: 方法:変数内で複数の値を保持する (Visual Basic)'
title: '方法: 変数内で複数の値を保持する'
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: 5248bc29f58cccf3b8ced95d3fba8f0d39033a83
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100484003"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="637d8-103">方法: 変数内で複数の値を保持する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="637d8-103">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>

<span data-ttu-id="637d8-104">変数に複数の値が保持されるのは、"*複合データ型*" として宣言したときです。</span><span class="sxs-lookup"><span data-stu-id="637d8-104">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>

<span data-ttu-id="637d8-105">[複合データ型](composite-data-types.md)には、構造体、配列、およびクラスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="637d8-105">[Composite Data Types](composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="637d8-106">複合データ型の変数は、基本データ型とその他の複合型の組み合わせを保持できます。</span><span class="sxs-lookup"><span data-stu-id="637d8-106">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="637d8-107">構造体とクラスは、データだけでなくコードも保持できます。</span><span class="sxs-lookup"><span data-stu-id="637d8-107">Structures and classes can hold code as well as data.</span></span>

## <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="637d8-108">変数内で複数の値を保持するには</span><span class="sxs-lookup"><span data-stu-id="637d8-108">To hold more than one value in a variable</span></span>

1. <span data-ttu-id="637d8-109">変数でどの複合データ型を使用するかを決定します。</span><span class="sxs-lookup"><span data-stu-id="637d8-109">Determine what composite data type you want to use for your variable.</span></span>

2. <span data-ttu-id="637d8-110">その複合データ型がまだ定義されていない場合、定義すると変数で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="637d8-110">If the composite data type is not already defined, define it so that your variable can use it.</span></span>

    - <span data-ttu-id="637d8-111">[Structure ステートメント](../../../language-reference/statements/structure-statement.md)を使用して構造体を定義します。</span><span class="sxs-lookup"><span data-stu-id="637d8-111">Define a structure with a [Structure Statement](../../../language-reference/statements/structure-statement.md).</span></span>

    - <span data-ttu-id="637d8-112">[Dim ステートメント](../../../language-reference/statements/dim-statement.md)を使用して配列を定義します。</span><span class="sxs-lookup"><span data-stu-id="637d8-112">Define an array with a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span>

    - <span data-ttu-id="637d8-113">[Class ステートメント](../../../language-reference/statements/class-statement.md)を使用してクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="637d8-113">Define a class with a [Class Statement](../../../language-reference/statements/class-statement.md).</span></span>

3. <span data-ttu-id="637d8-114">`Dim` ステートメントを使用して変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="637d8-114">Declare your variable with a `Dim` statement.</span></span>

4. <span data-ttu-id="637d8-115">変数名の後に `As` 句を指定します。</span><span class="sxs-lookup"><span data-stu-id="637d8-115">Follow the variable name with an `As` clause.</span></span>

5. <span data-ttu-id="637d8-116">`As` キーワードに続けて、適切な複合データ型の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="637d8-116">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="637d8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="637d8-117">See also</span></span>

- [<span data-ttu-id="637d8-118">データの種類</span><span class="sxs-lookup"><span data-stu-id="637d8-118">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="637d8-119">型文字</span><span class="sxs-lookup"><span data-stu-id="637d8-119">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="637d8-120">複合データ型</span><span class="sxs-lookup"><span data-stu-id="637d8-120">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="637d8-121">構造体</span><span class="sxs-lookup"><span data-stu-id="637d8-121">Structures</span></span>](structures.md)
- [<span data-ttu-id="637d8-122">配列</span><span class="sxs-lookup"><span data-stu-id="637d8-122">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="637d8-123">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="637d8-123">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="637d8-124">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="637d8-124">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
