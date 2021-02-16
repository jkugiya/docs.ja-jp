---
description: '詳細情報: 引数の値渡しと参照渡しの違い (Visual Basic)'
title: 引数の値渡しと参照渡しの違い
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: 632895eae82a20c9bcd773da71f88ebef26d786c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464730"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="bbec1-103">引数の値渡しと参照渡しの違い (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbec1-103">Differences Between Passing an Argument By Value and By Reference (Visual Basic)</span></span>

<span data-ttu-id="bbec1-104">プロシージャに 1 つまたは複数の引数を渡す場合、各引数は、呼び出し元のコード内の基になるプログラミング要素に対応します。</span><span class="sxs-lookup"><span data-stu-id="bbec1-104">When you pass one or more arguments to a procedure, each argument corresponds to an underlying programming element in the calling code.</span></span> <span data-ttu-id="bbec1-105">この基になる要素の値を渡すことも、それへの参照を渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="bbec1-105">You can pass either the value of this underlying element, or a reference to it.</span></span> <span data-ttu-id="bbec1-106">これは "*引渡し方法*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="bbec1-106">This is known as the *passing mechanism*.</span></span>  
  
## <a name="passing-by-value"></a><span data-ttu-id="bbec1-107">値渡し</span><span class="sxs-lookup"><span data-stu-id="bbec1-107">Passing by Value</span></span>  

 <span data-ttu-id="bbec1-108">引数を "*値渡し*" するには、プロシージャ定義内の対応するパラメーターに [ByVal](../../../language-reference/modifiers/byval.md) キーワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="bbec1-108">You pass an argument *by value* by specifying the [ByVal](../../../language-reference/modifiers/byval.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="bbec1-109">この引渡し方法を使用すると、基になるプログラミング要素の値がプロシージャ内のローカル変数に Visual Basic によってコピーされます。</span><span class="sxs-lookup"><span data-stu-id="bbec1-109">When you use this passing mechanism, Visual Basic copies the value of the underlying programming element into a local variable in the procedure.</span></span> <span data-ttu-id="bbec1-110">プロシージャコードには、呼び出し元のコード内の基になる要素へのアクセス権がありません。</span><span class="sxs-lookup"><span data-stu-id="bbec1-110">The procedure code does not have any access to the underlying element in the calling code.</span></span>  
  
## <a name="passing-by-reference"></a><span data-ttu-id="bbec1-111">参照渡し</span><span class="sxs-lookup"><span data-stu-id="bbec1-111">Passing by Reference</span></span>  

 <span data-ttu-id="bbec1-112">引数を "*参照渡し*" するには、プロシージャ定義内の対応するパラメーターに [ByRef](../../../language-reference/modifiers/byref.md) キーワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="bbec1-112">You pass an argument *by reference* by specifying the [ByRef](../../../language-reference/modifiers/byref.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="bbec1-113">この引渡し方法を使用した場合、呼び出し元のコード内の基になるプログラミング要素への直接参照が Visual Basic によってプロシージャに渡されます。</span><span class="sxs-lookup"><span data-stu-id="bbec1-113">When you use this passing mechanism, Visual Basic gives the procedure a direct reference to the underlying programming element in the calling code.</span></span>  
  
## <a name="passing-mechanism-and-element-type"></a><span data-ttu-id="bbec1-114">引渡し方法と要素型</span><span class="sxs-lookup"><span data-stu-id="bbec1-114">Passing Mechanism and Element Type</span></span>  

 <span data-ttu-id="bbec1-115">引渡し方法を選択することは、基になる要素型を分類することと同じではありません。</span><span class="sxs-lookup"><span data-stu-id="bbec1-115">The choice of passing mechanism is not the same as the classification of the underlying element type.</span></span> <span data-ttu-id="bbec1-116">値渡しまたは参照渡しでは、Visual Basic によってプロシージャ コードに提供されるものを示します。</span><span class="sxs-lookup"><span data-stu-id="bbec1-116">Passing by value or by reference refers to what Visual Basic supplies to the procedure code.</span></span> <span data-ttu-id="bbec1-117">値型または参照型では、プログラミング要素がメモリ内に格納される方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bbec1-117">A value type or reference type refers to how a programming element is stored in memory.</span></span>  
  
 <span data-ttu-id="bbec1-118">ただし、引渡し方法と要素型は相互に関連しています。</span><span class="sxs-lookup"><span data-stu-id="bbec1-118">However, the passing mechanism and element type are interrelated.</span></span> <span data-ttu-id="bbec1-119">参照型の値は、メモリ内の別の場所にあるデータを指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="bbec1-119">The value of a reference type is a pointer to the data elsewhere in memory.</span></span> <span data-ttu-id="bbec1-120">つまり、参照型を値渡しすると、プロシージャ コードには、基になる要素自体にアクセスできなくても、基になる要素のデータを指すポインターが用意されます。</span><span class="sxs-lookup"><span data-stu-id="bbec1-120">This means that when you pass a reference type by value, the procedure code has a pointer to the underlying element's data, even though it cannot access the underlying element itself.</span></span> <span data-ttu-id="bbec1-121">たとえば、要素が配列変数である場合、プロシージャ コードから変数自体にアクセスすることはできませんが、配列のメンバーにはアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="bbec1-121">For example, if the element is an array variable, the procedure code does not have access to the variable itself, but it can access the array members.</span></span>  
  
## <a name="ability-to-modify"></a><span data-ttu-id="bbec1-122">変更する機能</span><span class="sxs-lookup"><span data-stu-id="bbec1-122">Ability to Modify</span></span>  

 <span data-ttu-id="bbec1-123">変更できない要素を引数として渡した場合、その要素が `ByVal` または `ByRef` のどちらで渡されたかに関係なく、プロシージャでは呼び出し元のコード内のそれを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="bbec1-123">When you pass a nonmodifiable element as an argument, the procedure can never modify it in the calling code, whether it is passed `ByVal` or `ByRef`.</span></span>  
  
 <span data-ttu-id="bbec1-124">変更可能な要素については、次の表に、要素型と引渡し方法のやり取りをまとめてあります。</span><span class="sxs-lookup"><span data-stu-id="bbec1-124">For a modifiable element, the following table summarizes the interaction between the element type and the passing mechanism.</span></span>  
  
|<span data-ttu-id="bbec1-125">要素型</span><span class="sxs-lookup"><span data-stu-id="bbec1-125">Element type</span></span>|<span data-ttu-id="bbec1-126">`ByVal` で渡した</span><span class="sxs-lookup"><span data-stu-id="bbec1-126">Passed `ByVal`</span></span>|<span data-ttu-id="bbec1-127">`ByRef` で渡した</span><span class="sxs-lookup"><span data-stu-id="bbec1-127">Passed `ByRef`</span></span>|  
|------------------|--------------------|--------------------|  
|<span data-ttu-id="bbec1-128">値型 (値のみを含む)</span><span class="sxs-lookup"><span data-stu-id="bbec1-128">Value type (contains only a value)</span></span>|<span data-ttu-id="bbec1-129">プロシージャでは変数も、そのいずれのメンバーも変更することができません。</span><span class="sxs-lookup"><span data-stu-id="bbec1-129">The procedure cannot change the variable or any of its members.</span></span>|<span data-ttu-id="bbec1-130">プロシージャでは変数とそのメンバーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="bbec1-130">The procedure can change the variable and its members.</span></span>|  
|<span data-ttu-id="bbec1-131">参照型 (クラスまたは構造体のインスタンスを指すポインターを含む)</span><span class="sxs-lookup"><span data-stu-id="bbec1-131">Reference type (contains a pointer to a class or structure instance)</span></span>|<span data-ttu-id="bbec1-132">プロシージャでは変数を変更することはできませんが、それによって参照されているインスタンスのメンバーを変更することはできます。</span><span class="sxs-lookup"><span data-stu-id="bbec1-132">The procedure cannot change the variable but can change members of the instance to which it points.</span></span>|<span data-ttu-id="bbec1-133">プロシージャでは変数と、それによって参照されるインスタンスのメンバーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="bbec1-133">The procedure can change the variable and members of the instance to which it points.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bbec1-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbec1-134">See also</span></span>

- [<span data-ttu-id="bbec1-135">手順</span><span class="sxs-lookup"><span data-stu-id="bbec1-135">Procedures</span></span>](./index.md)
- [<span data-ttu-id="bbec1-136">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="bbec1-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="bbec1-137">方法: プロシージャに引数を渡す</span><span class="sxs-lookup"><span data-stu-id="bbec1-137">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="bbec1-138">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="bbec1-138">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="bbec1-139">変更できる引数と変更できない引数の違い</span><span class="sxs-lookup"><span data-stu-id="bbec1-139">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="bbec1-140">方法: プロシージャ引数の値を変更する</span><span class="sxs-lookup"><span data-stu-id="bbec1-140">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="bbec1-141">方法: プロシージャ引数の値が変更されないように保護する</span><span class="sxs-lookup"><span data-stu-id="bbec1-141">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="bbec1-142">方法: 引数の値渡しを強制する</span><span class="sxs-lookup"><span data-stu-id="bbec1-142">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="bbec1-143">位置と名前による引数渡し</span><span class="sxs-lookup"><span data-stu-id="bbec1-143">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="bbec1-144">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="bbec1-144">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
