---
description: '詳細情報: プロシージャのパラメーターと引数 (Visual Basic)'
title: プロシージャのパラメーターと引数
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: c2239c76450f503e74dbf5f191cd212e05d11600
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100423161"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="018da-103">プロシージャのパラメーターと引数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="018da-103">Procedure Parameters and Arguments (Visual Basic)</span></span>

<span data-ttu-id="018da-104">ほとんどの場合、プロシージャには呼び出された状況に関する情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="018da-104">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="018da-105">反復的なタスクや共有タスクを実行するプロシージャでは、呼び出しごとに異なる情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="018da-105">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="018da-106">この情報は、呼び出し時にプロシージャに渡す変数、定数、式で構成されます。</span><span class="sxs-lookup"><span data-stu-id="018da-106">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="018da-107">"*パラメーター*" は、プロシージャを呼び出すときに指定する必要がある値を表します。</span><span class="sxs-lookup"><span data-stu-id="018da-107">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="018da-108">プロシージャの宣言でパラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="018da-108">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="018da-109">パラメーターなし、1 つのパラメーター、または複数のパラメーターでプロシージャを定義できます。</span><span class="sxs-lookup"><span data-stu-id="018da-109">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="018da-110">プロシージャ定義の、パラメーターを指定する部分は、"*パラメーター リスト*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="018da-110">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="018da-111">"*引数*" は、プロシージャを呼び出すときにプロシージャ パラメーターに指定する値を表します。</span><span class="sxs-lookup"><span data-stu-id="018da-111">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="018da-112">呼び出し元のコードは、プロシージャを呼び出すときに引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="018da-112">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="018da-113">プロシージャ呼び出しの、引数を指定する部分は、"*引数リスト*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="018da-113">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="018da-114">次の図は、2 つの異なる場所から `safeSquareRoot` プロシージャを呼び出すコードを示しています。</span><span class="sxs-lookup"><span data-stu-id="018da-114">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="018da-115">最初の呼び出しでは、変数 `x` の値 (4.0) を `number` パラメーターに渡し、`root` の戻り値 (2.0) が変数 `y` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="018da-115">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="018da-116">2 番目の呼び出しでは、リテラル値 9.0 を `number` に渡し、戻り値 (3.0) を変数 `z` に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="018da-116">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![パラメーターへの引数の引渡しを示す図](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="018da-118">詳細については、「[Differences Between Parameters and Arguments (パラメーターと引数の違い)](./differences-between-parameters-and-arguments.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="018da-118">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="018da-119">パラメーターのデータ型</span><span class="sxs-lookup"><span data-stu-id="018da-119">Parameter Data Type</span></span>  

 <span data-ttu-id="018da-120">パラメーターのデータ型を定義するには、宣言で `As` 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="018da-120">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="018da-121">たとえば、次の関数は文字列と整数を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="018da-121">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="018da-122">型チェック スイッチ ([Option Strict ステートメント](../../../language-reference/statements/option-strict-statement.md)) が `Off,` の場合、`As` 句は省略可能です。ただし、いずれか 1 つのパラメーターで使用する場合は、すべてのパラメーターで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="018da-122">If the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="018da-123">型チェックが `On` の場合は、すべてのプロシージャ パラメーターで `As` 句が必須となります。</span><span class="sxs-lookup"><span data-stu-id="018da-123">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="018da-124">呼び出し元のコードが、対応するパラメーターのデータ型とは異なるデータ型の引数 (`String` パラメーターに対する `Byte` など) を指定することを要求している場合、次のいずれかを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="018da-124">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
- <span data-ttu-id="018da-125">パラメーターのデータ型に拡大変換するデータ型の引数のみを指定する。</span><span class="sxs-lookup"><span data-stu-id="018da-125">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
- <span data-ttu-id="018da-126">`Option Strict Off` を設定して、暗黙的な縮小変換を許可する。または、</span><span class="sxs-lookup"><span data-stu-id="018da-126">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
- <span data-ttu-id="018da-127">変換キーワードを使用して、データ型を明示的に変換する。</span><span class="sxs-lookup"><span data-stu-id="018da-127">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="018da-128">型パラメーター</span><span class="sxs-lookup"><span data-stu-id="018da-128">Type Parameters</span></span>  

 <span data-ttu-id="018da-129">"*ジェネリック プロシージャ*" では、通常のパラメーターに加え、1 つ以上の "*型パラメーター*" も定義します。</span><span class="sxs-lookup"><span data-stu-id="018da-129">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="018da-130">ジェネリック プロシージャを使用すると、呼び出し元のコードは、プロシージャを呼び出すたびに異なるデータ型を渡すことができるため、個々の呼び出しの要件に合わせてデータ型を調整できます。</span><span class="sxs-lookup"><span data-stu-id="018da-130">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="018da-131">「 [Generic Procedures in Visual Basic](../data-types/generic-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="018da-131">See [Generic Procedures in Visual Basic](../data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="018da-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="018da-132">See also</span></span>

- [<span data-ttu-id="018da-133">手順</span><span class="sxs-lookup"><span data-stu-id="018da-133">Procedures</span></span>](./index.md)
- [<span data-ttu-id="018da-134">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="018da-134">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="018da-135">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="018da-135">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="018da-136">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="018da-136">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="018da-137">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="018da-137">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="018da-138">方法: プロシージャのパラメーターを定義する</span><span class="sxs-lookup"><span data-stu-id="018da-138">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="018da-139">方法: プロシージャに引数を渡す</span><span class="sxs-lookup"><span data-stu-id="018da-139">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="018da-140">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="018da-140">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="018da-141">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="018da-141">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="018da-142">Visual Basic における型変換</span><span class="sxs-lookup"><span data-stu-id="018da-142">Type Conversions in Visual Basic</span></span>](../data-types/type-conversions.md)
