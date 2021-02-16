---
description: '詳細情報: 定数とリテラルのデータ型 (Visual Basic)'
title: 定数とリテラルのデータ型
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: e750b1e5746f935c7878e186d064060d0fa055dc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475436"
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="cf77f-103">定数とリテラルのデータ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf77f-103">Constant and Literal Data Types (Visual Basic)</span></span>

<span data-ttu-id="cf77f-104">リテラルとは、数字の 3 や文字列 "Hello" など、変数値や式の結果ではなく、それ自体として表される値のことです。</span><span class="sxs-lookup"><span data-stu-id="cf77f-104">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="cf77f-105">定数とは、リテラルの代わりとなるわかりやすい名前のことです。プログラム内で値が変わりうる変数とは異なり、プログラム全体で同じ値を保持します。</span><span class="sxs-lookup"><span data-stu-id="cf77f-105">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="cf77f-106">[Option Infer](../../../language-reference/statements/option-infer-statement.md) に `Off` を指定し、[Option Strict](../../../language-reference/statements/option-strict-statement.md) に `On` を指定した場合、すべての定数にデータ型を指定して明示的に宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf77f-106">When [Option Infer](../../../language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="cf77f-107">次の例では、`MyByte` のデータ型をデータ型 `Byte` として明示的に宣言しています。</span><span class="sxs-lookup"><span data-stu-id="cf77f-107">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 <span data-ttu-id="cf77f-108">`Option Infer` に `On` を指定するか、`Option Strict` に `Off` を指定している場合は、`As` 句でデータ型を指定することなく定数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="cf77f-108">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="cf77f-109">コンパイラは、式の型から定数の型を判断します。</span><span class="sxs-lookup"><span data-stu-id="cf77f-109">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="cf77f-110">既定では、数値整数型のリテラルは `Integer` データ型にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="cf77f-110">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="cf77f-111">浮動小数点数の既定のデータ型は `Double` であり、 `Boolean` 定数は `True` と `False` の各キーワードで指定します。</span><span class="sxs-lookup"><span data-stu-id="cf77f-111">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="cf77f-112">リテラルと強制型変換</span><span class="sxs-lookup"><span data-stu-id="cf77f-112">Literals and Type Coercion</span></span>  

 <span data-ttu-id="cf77f-113">`Decimal` 型変数に非常に大きな整数型リテラルの値を割り当てる場合など、リテラルの特定のデータ型への強制変換が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="cf77f-113">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="cf77f-114">次の例ではエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="cf77f-114">The following example produces an error:</span></span>  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="cf77f-115">このエラーの原因は、リテラルの表現にあります。</span><span class="sxs-lookup"><span data-stu-id="cf77f-115">The error results from the representation of the literal.</span></span> <span data-ttu-id="cf77f-116">`Decimal` データ型はこの大きさの値を保持できますが、リテラルは暗黙的に `Long` として表現されるので、値を保持できません。</span><span class="sxs-lookup"><span data-stu-id="cf77f-116">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="cf77f-117">リテラルは、2 つの方法で特定のデータ型に強制的に変換できます。1 つは型文字をリテラルに追加することであり、もう 1 つは囲み文字内にリテラルを配置することです。</span><span class="sxs-lookup"><span data-stu-id="cf77f-117">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="cf77f-118">型文字と囲み文字は、リテラルの直前または直後に、スペースや文字を挟まずに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf77f-118">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="cf77f-119">前述の例を機能させるには、リテラルに `D` 型文字を追加します。これにより、リテラルが `Decimal` として表現されます。</span><span class="sxs-lookup"><span data-stu-id="cf77f-119">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 <span data-ttu-id="cf77f-120">型文字と囲み文字の正しい使用方法を、次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="cf77f-120">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 <span data-ttu-id="cf77f-121">Visual Basic で利用可能な囲み文字と囲み文字を、次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="cf77f-121">The following table shows the enclosing characters and type characters available in Visual Basic.</span></span>  
  
|<span data-ttu-id="cf77f-122">データの種類</span><span class="sxs-lookup"><span data-stu-id="cf77f-122">Data type</span></span>|<span data-ttu-id="cf77f-123">囲み文字</span><span class="sxs-lookup"><span data-stu-id="cf77f-123">Enclosing character</span></span>|<span data-ttu-id="cf77f-124">追加する型文字</span><span class="sxs-lookup"><span data-stu-id="cf77f-124">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="cf77f-125">(なし)</span><span class="sxs-lookup"><span data-stu-id="cf77f-125">(none)</span></span>|<span data-ttu-id="cf77f-126">(なし)</span><span class="sxs-lookup"><span data-stu-id="cf77f-126">(none)</span></span>|  
|`Byte`|<span data-ttu-id="cf77f-127">(なし)</span><span class="sxs-lookup"><span data-stu-id="cf77f-127">(none)</span></span>|<span data-ttu-id="cf77f-128">(なし)</span><span class="sxs-lookup"><span data-stu-id="cf77f-128">(none)</span></span>|  
|`Char`|<span data-ttu-id="cf77f-129">"</span><span class="sxs-lookup"><span data-stu-id="cf77f-129">"</span></span>|<span data-ttu-id="cf77f-130">C</span><span class="sxs-lookup"><span data-stu-id="cf77f-130">C</span></span>|  
|`Date`|#|<span data-ttu-id="cf77f-131">(なし)</span><span class="sxs-lookup"><span data-stu-id="cf77f-131">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="cf77f-132">(なし)</span><span class="sxs-lookup"><span data-stu-id="cf77f-132">(none)</span></span>|<span data-ttu-id="cf77f-133">D または @</span><span class="sxs-lookup"><span data-stu-id="cf77f-133">D or @</span></span>|  
|`Double`|<span data-ttu-id="cf77f-134">(なし)</span><span class="sxs-lookup"><span data-stu-id="cf77f-134">(none)</span></span>|<span data-ttu-id="cf77f-135">R または #</span><span class="sxs-lookup"><span data-stu-id="cf77f-135">R or #</span></span>|  
|`Integer`|<span data-ttu-id="cf77f-136">(なし)</span><span class="sxs-lookup"><span data-stu-id="cf77f-136">(none)</span></span>|<span data-ttu-id="cf77f-137">I または %</span><span class="sxs-lookup"><span data-stu-id="cf77f-137">I or %</span></span>|  
|`Long`|<span data-ttu-id="cf77f-138">(なし)</span><span class="sxs-lookup"><span data-stu-id="cf77f-138">(none)</span></span>|<span data-ttu-id="cf77f-139">L または &</span><span class="sxs-lookup"><span data-stu-id="cf77f-139">L or &</span></span>|  
|`Short`|<span data-ttu-id="cf77f-140">(なし)</span><span class="sxs-lookup"><span data-stu-id="cf77f-140">(none)</span></span>|<span data-ttu-id="cf77f-141">S</span><span class="sxs-lookup"><span data-stu-id="cf77f-141">S</span></span>|  
|`Single`|<span data-ttu-id="cf77f-142">(なし)</span><span class="sxs-lookup"><span data-stu-id="cf77f-142">(none)</span></span>|<span data-ttu-id="cf77f-143">F または !</span><span class="sxs-lookup"><span data-stu-id="cf77f-143">F or !</span></span>|  
|`String`|<span data-ttu-id="cf77f-144">"</span><span class="sxs-lookup"><span data-stu-id="cf77f-144">"</span></span>|<span data-ttu-id="cf77f-145">(なし)</span><span class="sxs-lookup"><span data-stu-id="cf77f-145">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf77f-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf77f-146">See also</span></span>

- [<span data-ttu-id="cf77f-147">ユーザー定義定数</span><span class="sxs-lookup"><span data-stu-id="cf77f-147">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="cf77f-148">方法: 定数を宣言する</span><span class="sxs-lookup"><span data-stu-id="cf77f-148">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="cf77f-149">定数の概要</span><span class="sxs-lookup"><span data-stu-id="cf77f-149">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="cf77f-150">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="cf77f-150">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="cf77f-151">Option Explicit ステートメント</span><span class="sxs-lookup"><span data-stu-id="cf77f-151">Option Explicit Statement</span></span>](../../../language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="cf77f-152">列挙型の概要</span><span class="sxs-lookup"><span data-stu-id="cf77f-152">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="cf77f-153">方法: 列挙型を宣言する</span><span class="sxs-lookup"><span data-stu-id="cf77f-153">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="cf77f-154">列挙型と名前の修飾</span><span class="sxs-lookup"><span data-stu-id="cf77f-154">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="cf77f-155">データの種類</span><span class="sxs-lookup"><span data-stu-id="cf77f-155">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="cf77f-156">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="cf77f-156">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
