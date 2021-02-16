---
description: '詳細情報: 方法:引数の値渡しを強制する (Visual Basic)'
title: '方法: 引数の値渡しを強制する'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 471ddbf8993ad671dc4285729a11f5b17a5b19dc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475423"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="982ec-103">方法: 引数の値渡しを強制する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="982ec-103">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>

<span data-ttu-id="982ec-104">プロシージャ宣言によって引渡し方法が決まります。</span><span class="sxs-lookup"><span data-stu-id="982ec-104">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="982ec-105">Visual Basic では、パラメーターが [ByRef](../../../language-reference/modifiers/byref.md) として宣言されている場合、対応する引数は参照渡しになります。</span><span class="sxs-lookup"><span data-stu-id="982ec-105">If a parameter is declared [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="982ec-106">これにより、プロシージャは引数の基になる呼び出し元のコードのプログラミング要素の値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="982ec-106">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="982ec-107">基になる要素をこのような変更から保護する場合は、引数名をかっこで囲むことで、プロシージャ呼び出しの引渡し方法 `ByRef` をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="982ec-107">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="982ec-108">これらのかっこは、呼び出しの引数リストを囲むかっこに追加されます。</span><span class="sxs-lookup"><span data-stu-id="982ec-108">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="982ec-109">呼び出し元のコードでは、引渡し方法 [ByVal](../../../language-reference/modifiers/byval.md) をオーバーライドできません。</span><span class="sxs-lookup"><span data-stu-id="982ec-109">The calling code cannot override a [ByVal](../../../language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="982ec-110">引数の値渡しを強制するには</span><span class="sxs-lookup"><span data-stu-id="982ec-110">To force an argument to be passed by value</span></span>  
  
- <span data-ttu-id="982ec-111">対応するパラメーターがプロシージャで `ByVal` として宣言されている場合は、追加の手順を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="982ec-111">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="982ec-112">引数は既に値渡しになっています。</span><span class="sxs-lookup"><span data-stu-id="982ec-112">Visual Basic already expects to pass the argument by value.</span></span>  
  
- <span data-ttu-id="982ec-113">対応するパラメーターがプロシージャで `ByRef` として宣言されている場合は、プロシージャ呼び出しで引数をかっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="982ec-113">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="982ec-114">例</span><span class="sxs-lookup"><span data-stu-id="982ec-114">Example</span></span>  

 <span data-ttu-id="982ec-115">次の例では、`ByRef` パラメーター宣言をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="982ec-115">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="982ec-116">`ByVal` を強制する呼び出しでは、2 つのレベルのかっこがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="982ec-116">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 <span data-ttu-id="982ec-117">引数リスト内で `str` が追加のかっこで囲まれている場合、`setNewString` プロシージャは呼び出し元のコードの値を変更できず、`MsgBox` に "Cannot be replaced if passed ByVal (ByVal で渡した場合、置き換えることはできません)" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="982ec-117">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="982ec-118">`str` が追加のかっこで囲まれていない場合、プロシージャは値を変更することができ、`MsgBox` に "This is a new value for the inString argument (これは inString 引数の新しい値です)" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="982ec-118">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="982ec-119">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="982ec-119">Compile the code</span></span>  

 <span data-ttu-id="982ec-120">変数を参照渡しにするときは、`ByRef` キーワードを使用してこの方法を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="982ec-120">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="982ec-121">Visual Basic の既定では、引数は値渡しになります。</span><span class="sxs-lookup"><span data-stu-id="982ec-121">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="982ec-122">ただし、宣言されるすべてのパラメーターに、[ByVal](../../../language-reference/modifiers/byval.md) または [ByRef](../../../language-reference/modifiers/byref.md) キーワードを含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="982ec-122">However, it is good programming practice to include either the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="982ec-123">これにより、コードが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="982ec-123">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="982ec-124">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="982ec-124">Robust Programming</span></span>  

 <span data-ttu-id="982ec-125">プロシージャでパラメーターが [ByRef](../../../language-reference/modifiers/byref.md) として宣言されている場合、コードの正しい実行は、呼び出し元のコードの基になる要素を変更できるかどうかに左右されます。</span><span class="sxs-lookup"><span data-stu-id="982ec-125">If a procedure declares a parameter [ByRef](../../../language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="982ec-126">呼び出し元のコードで、引数をかっこで囲んでこの引渡し方法をオーバーライドした場合や、変更不可能な引数を渡した場合、プロシージャは基になる要素を変更できません。</span><span class="sxs-lookup"><span data-stu-id="982ec-126">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="982ec-127">これにより、呼び出し元のコードで予期しない結果が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="982ec-127">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="982ec-128">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="982ec-128">.NET Framework Security</span></span>  

 <span data-ttu-id="982ec-129">プロシージャが呼び出し元のコードの引数の基になる値を変更できるようにする場合、常に潜在的なリスクがあります。</span><span class="sxs-lookup"><span data-stu-id="982ec-129">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="982ec-130">この値が変更されることを想定し、使用前に有効性をチェックする準備をしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="982ec-130">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="982ec-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="982ec-131">See also</span></span>

- [<span data-ttu-id="982ec-132">手順</span><span class="sxs-lookup"><span data-stu-id="982ec-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="982ec-133">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="982ec-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="982ec-134">方法: プロシージャに引数を渡す</span><span class="sxs-lookup"><span data-stu-id="982ec-134">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="982ec-135">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="982ec-135">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="982ec-136">変更できる引数と変更できない引数の違い</span><span class="sxs-lookup"><span data-stu-id="982ec-136">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="982ec-137">引数の値渡しと参照渡しの違い</span><span class="sxs-lookup"><span data-stu-id="982ec-137">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="982ec-138">方法: プロシージャ引数の値を変更する</span><span class="sxs-lookup"><span data-stu-id="982ec-138">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="982ec-139">方法: プロシージャ引数の値が変更されないように保護する</span><span class="sxs-lookup"><span data-stu-id="982ec-139">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="982ec-140">位置と名前による引数渡し</span><span class="sxs-lookup"><span data-stu-id="982ec-140">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="982ec-141">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="982ec-141">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
