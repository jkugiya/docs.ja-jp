---
description: '詳細情報: 方法:省略可能なパラメーターを受け取るプロシージャをオーバーロードする (Visual Basic)'
title: '方法: 省略可能なパラメーターを受け取るプロシージャをオーバーロードする'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: dccef9d27c08ede2f35edc02c8bd5116aa6969b2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472944"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="8968a-103">方法: 省略可能なパラメーターを受け取るプロシージャをオーバーロードする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8968a-103">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>

<span data-ttu-id="8968a-104">プロシージャに 1 つ以上の [Optional](../../../language-reference/modifiers/optional.md) パラメーターがある場合、暗黙的なオーバーロードのいずれかに一致するオーバーロードされたバージョンを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="8968a-104">If a procedure has one or more [Optional](../../../language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="8968a-105">詳細については、「[プロシージャのオーバーロードに関する注意事項](./considerations-in-overloading-procedures.md)」の「Optional パラメーターの暗黙的なオーバーロード」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8968a-105">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="8968a-106">1 つの省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="8968a-106">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="8968a-107">1 つの省略可能なパラメーターを受け取るプロシージャをオーバーロードするには</span><span class="sxs-lookup"><span data-stu-id="8968a-107">To overload a procedure that takes one optional parameter</span></span>  
  
1. <span data-ttu-id="8968a-108">パラメーター リストに省略可能なパラメーターが含まれた、`Sub` または `Function` 宣言ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="8968a-108">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="8968a-109">このオーバーロードされたバージョンでは、`Optional` キーワードは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="8968a-109">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2. <span data-ttu-id="8968a-110">`Sub` または `Function` キーワードの前に [Overloads](../../../language-reference/modifiers/overloads.md) キーワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="8968a-110">Precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3. <span data-ttu-id="8968a-111">呼び出し元のコードで省略可能な引数が指定されたときに実行する必要があるプロシージャ コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="8968a-111">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4. <span data-ttu-id="8968a-112">プロシージャを、必要に応じて `End Sub` または `End Function` ステートメントで終了します。</span><span class="sxs-lookup"><span data-stu-id="8968a-112">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5. <span data-ttu-id="8968a-113">パラメーター リストに省略可能なパラメーターが含まれていない点を除いて、最初の宣言と同じである 2 番目の宣言ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="8968a-113">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6. <span data-ttu-id="8968a-114">呼び出し元のコードで省略可能な引数が指定されないときに実行する必要があるプロシージャ コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="8968a-114">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="8968a-115">プロシージャを、必要に応じて `End Sub` または `End Function` ステートメントで終了します。</span><span class="sxs-lookup"><span data-stu-id="8968a-115">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="8968a-116">次の例は、省略可能なパラメーターで定義されたプロシージャ、2 つのオーバーロードされたプロシージャの同等のセット、無効および有効なオーバーロードされたバージョンの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="8968a-116">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="8968a-117">複数の省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="8968a-117">Multiple Optional Parameters</span></span>  

 <span data-ttu-id="8968a-118">複数の省略可能なパラメーターがあるプロシージャでは、通常、3 つ以上のオーバーロードされたバージョンが必要です。</span><span class="sxs-lookup"><span data-stu-id="8968a-118">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="8968a-119">たとえば、2 つの省略可能なパラメーターがあり、呼び出し元のコードが各パラメーターを相互に独立して指定または省略できる場合、4 つのオーバーロードされたバージョン (指定された引数の可能な組み合わせごとに 1 つ) が必要です。</span><span class="sxs-lookup"><span data-stu-id="8968a-119">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="8968a-120">省略可能なパラメーターの数が増えると、オーバーロードの複雑さが増します。</span><span class="sxs-lookup"><span data-stu-id="8968a-120">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="8968a-121">指定された引数の一部の組み合わせが許容されない場合を除き、N 個の省略可能なパラメーターには 2 ^ N 個のオーバーロードされたバージョンが必要となります。</span><span class="sxs-lookup"><span data-stu-id="8968a-121">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="8968a-122">プロシージャの性質によっては、オーバーロードされたバージョンをすべて定義することによってロジックが明確になることから、余分な労力をかけるだけの価値がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="8968a-122">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="8968a-123">複数の省略可能なパラメーターを受け取るプロシージャをオーバーロードするには</span><span class="sxs-lookup"><span data-stu-id="8968a-123">To overload a procedure that takes more than one optional parameter</span></span>  
  
1. <span data-ttu-id="8968a-124">プロシージャのロジックで許容される、指定された省略可能な引数の組み合わせを特定します。</span><span class="sxs-lookup"><span data-stu-id="8968a-124">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="8968a-125">ある省略可能なパラメーターが別の省略可能なパラメーターに依存する場合、許容されない組み合わせが生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8968a-125">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="8968a-126">たとえば、あるパラメーターが個人の名前を受け入れ、別のパラメーターがその個人の年齢を受け入れる場合、年齢を指定し、名前を省略する引数の組み合わせは許容されません。</span><span class="sxs-lookup"><span data-stu-id="8968a-126">For example, if one parameter accepts a person's name and another accepts the person's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2. <span data-ttu-id="8968a-127">指定された省略可能な引数の許容される組み合わせごとに、対応するパラメーター リストを定義する、`Sub` または `Function` 宣言ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="8968a-127">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="8968a-128">`Optional` キーワードは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="8968a-128">Do not use the `Optional` keyword.</span></span>  
  
3. <span data-ttu-id="8968a-129">各宣言で、`Sub` または `Function` キーワードの前に [Overloads](../../../language-reference/modifiers/overloads.md) キーワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="8968a-129">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4. <span data-ttu-id="8968a-130">各宣言の後に、呼び出し元のコードでその宣言のパラメーター リストに対応する引数リストが指定されたときに実行する必要があるプロシージャ コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="8968a-130">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5. <span data-ttu-id="8968a-131">各プロシージャを、必要に応じて `End Sub` または `End Function` ステートメントで終了します。</span><span class="sxs-lookup"><span data-stu-id="8968a-131">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8968a-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="8968a-132">See also</span></span>

- [<span data-ttu-id="8968a-133">手順</span><span class="sxs-lookup"><span data-stu-id="8968a-133">Procedures</span></span>](./index.md)
- [<span data-ttu-id="8968a-134">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="8968a-134">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="8968a-135">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="8968a-135">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="8968a-136">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="8968a-136">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="8968a-137">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="8968a-137">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="8968a-138">プロシージャのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="8968a-138">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="8968a-139">方法: プロシージャの複数のバージョンを定義する</span><span class="sxs-lookup"><span data-stu-id="8968a-139">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="8968a-140">方法: オーバーロードされたプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="8968a-140">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="8968a-141">方法: 不特定数のパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="8968a-141">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="8968a-142">オーバーロードの解決</span><span class="sxs-lookup"><span data-stu-id="8968a-142">Overload Resolution</span></span>](./overload-resolution.md)
