---
description: '詳細情報: 方法:不特定数のパラメーターを受け取るプロシージャをオーバーロードする (Visual Basic)'
title: '方法: 不特定数のパラメーターを受け取るプロシージャをオーバーロードする'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 97e391c2981760e012d56e1f93c24eb60ce3ebfe
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460047"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="f90ba-103">方法: 不特定数のパラメーターを受け取るプロシージャをオーバーロードする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f90ba-103">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>

<span data-ttu-id="f90ba-104">プロシージャに [ParamArray](../../../language-reference/modifiers/paramarray.md) パラメーターが含まれている場合、パラメーター配列に対して 1 次元配列を受け取るオーバーロードされたバージョンを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="f90ba-104">If a procedure has a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="f90ba-105">詳細については、「[プロシージャのオーバーロードに関する注意事項](./considerations-in-overloading-procedures.md)」の「ParamArray パラメーターの暗黙的なオーバーロード」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f90ba-105">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="f90ba-106">可変数のパラメーターを受け取るプロシージャをオーバーロードするには</span><span class="sxs-lookup"><span data-stu-id="f90ba-106">To overload a procedure that takes a variable number of parameters</span></span>  
  
1. <span data-ttu-id="f90ba-107">`ParamArray` パラメーターよりもオーバーロードされたバージョンの方が、プロシージャと呼び出し元のコードのロジックに多くのメリットがもたらされることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f90ba-107">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="f90ba-108">「[プロシージャのオーバーロードに関する注意事項](./considerations-in-overloading-procedures.md)」の「オーバーロードと ParamArray」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f90ba-108">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2. <span data-ttu-id="f90ba-109">プロシージャがパラメーター リストの変数部分で受け入れる必要がある、指定される値の数を決定します。</span><span class="sxs-lookup"><span data-stu-id="f90ba-109">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="f90ba-110">これには、値がないケースが含まれる場合や、単一の 1 次元配列のケースが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f90ba-110">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3. <span data-ttu-id="f90ba-111">指定される値の許容数ごとに、対応するパラメーター リストを定義する `Sub` または `Function` 宣言ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="f90ba-111">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="f90ba-112">このオーバーロードされたバージョンでは、`Optional` または `ParamArray` キーワードは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f90ba-112">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4. <span data-ttu-id="f90ba-113">各宣言で、`Sub` または `Function` キーワードの前に [Overloads](../../../language-reference/modifiers/overloads.md) キーワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="f90ba-113">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5. <span data-ttu-id="f90ba-114">各宣言の後に、呼び出し元のコードでその宣言のパラメーター リストに対応する値が指定されたときに実行する必要があるプロシージャ コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="f90ba-114">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6. <span data-ttu-id="f90ba-115">各プロシージャを、必要に応じて `End Sub` または `End Function` ステートメントで終了します。</span><span class="sxs-lookup"><span data-stu-id="f90ba-115">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f90ba-116">例</span><span class="sxs-lookup"><span data-stu-id="f90ba-116">Example</span></span>  

 <span data-ttu-id="f90ba-117">次の例は、[ParamArray](../../../language-reference/modifiers/paramarray.md) パラメーターを使用して定義されたプロシージャと、これと同等の一連のオーバーロードされたプロシージャを示しています。</span><span class="sxs-lookup"><span data-stu-id="f90ba-117">The following example shows a procedure defined with a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="f90ba-118">パラメーター配列に対して 1 次元配列を受け取るパラメーター リストでそのようなプロシージャをオーバーロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="f90ba-118">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="f90ba-119">ただし、他の暗黙的なオーバーロードのシグネチャを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f90ba-119">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="f90ba-120">次の宣言はこれを示しています。</span><span class="sxs-lookup"><span data-stu-id="f90ba-120">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 <span data-ttu-id="f90ba-121">オーバーロードされたバージョンのコードでは、呼び出し元のコードで `ParamArray` パラメーターに 1 つ以上の値が指定されたかどうかをテストしたり、指定された場合にその数をテストしたりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f90ba-121">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="f90ba-122">Visual Basic は、呼び出し元の引数リストと一致するバージョンに制御を渡します。</span><span class="sxs-lookup"><span data-stu-id="f90ba-122">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="f90ba-123">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="f90ba-123">Compile the code</span></span>  

 <span data-ttu-id="f90ba-124">`ParamArray` パラメーターを使用したプロシージャは、一連のオーバーロードされたバージョンと同等であるため、これらの暗黙的なオーバーロードのいずれかに対応するパラメーター リストでそのようなプロシージャをオーバーロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="f90ba-124">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="f90ba-125">詳細については、「[プロシージャのオーバーロードに関する注意事項](./considerations-in-overloading-procedures.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f90ba-125">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f90ba-126">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f90ba-126">.NET Framework Security</span></span>  

 <span data-ttu-id="f90ba-127">無限に大きくなる可能性がある配列を処理する場合は常に、アプリケーションの何らかの内部容量が超過するリスクがあります。</span><span class="sxs-lookup"><span data-stu-id="f90ba-127">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="f90ba-128">パラメーター配列を受け入れる場合は、呼び出し元のコードから渡された配列の長さをテストし、それがアプリケーションにとって大きすぎる場合は、適切な措置を講じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="f90ba-128">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f90ba-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="f90ba-129">See also</span></span>

- [<span data-ttu-id="f90ba-130">手順</span><span class="sxs-lookup"><span data-stu-id="f90ba-130">Procedures</span></span>](./index.md)
- [<span data-ttu-id="f90ba-131">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="f90ba-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f90ba-132">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="f90ba-132">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="f90ba-133">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="f90ba-133">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="f90ba-134">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="f90ba-134">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="f90ba-135">プロシージャのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="f90ba-135">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="f90ba-136">方法: プロシージャの複数のバージョンを定義する</span><span class="sxs-lookup"><span data-stu-id="f90ba-136">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="f90ba-137">方法: オーバーロードされたプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="f90ba-137">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="f90ba-138">方法: 省略可能なパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="f90ba-138">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="f90ba-139">オーバーロードの解決</span><span class="sxs-lookup"><span data-stu-id="f90ba-139">Overload Resolution</span></span>](./overload-resolution.md)
