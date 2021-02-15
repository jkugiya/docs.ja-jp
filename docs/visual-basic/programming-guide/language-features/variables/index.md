---
description: '詳細情報: Visual Basic における変数'
title: 変数
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: d00907e451fa09c6e9b6be990a24a4d39b386622
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481715"
---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="393df-103">Visual Basic における変数</span><span class="sxs-lookup"><span data-stu-id="393df-103">Variables in Visual Basic</span></span>

<span data-ttu-id="393df-104">Visual Basic で計算を行う場合、しばしば値を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="393df-104">You often have to store values when you perform calculations with Visual Basic.</span></span> <span data-ttu-id="393df-105">たとえば、いくつかの値を計算し、比較し、比較の結果に応じて、さまざまな操作を実行する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="393df-105">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="393df-106">比較する場合には、その値を保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="393df-106">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="393df-107">使用方法</span><span class="sxs-lookup"><span data-stu-id="393df-107">Usage</span></span>  

 <span data-ttu-id="393df-108">他のほとんどのプログラミング言語と同じように、Visual Basic では値の格納に変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="393df-108">Visual Basic, just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="393df-109">*変数* には (変数に含まれる値を参照するために使用する語である) 名前があります。</span><span class="sxs-lookup"><span data-stu-id="393df-109">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="393df-110">変数には、(変数に格納できるデータの種類を決定する) データ型もあります。</span><span class="sxs-lookup"><span data-stu-id="393df-110">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="393df-111">密接に関連するデータ項目のインデックス セットを格納する必要がある場合、変数で配列を表現することもできます。</span><span class="sxs-lookup"><span data-stu-id="393df-111">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="393df-112">ローカル型推論では、データ型を明示的に指定せずに変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="393df-112">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="393df-113">代わりに、コンパイラは、初期化式の型から変数の型を推測します。</span><span class="sxs-lookup"><span data-stu-id="393df-113">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="393df-114">詳細については、「[ローカル型の推論](local-type-inference.md)」と「[Option Infer ステートメント](../../../language-reference/statements/option-infer-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="393df-114">For more information, see [Local Type Inference](local-type-inference.md) and [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="393df-115">値の代入</span><span class="sxs-lookup"><span data-stu-id="393df-115">Assigning Values</span></span>  

 <span data-ttu-id="393df-116">次の例のように、計算を実行し、結果を変数に割り当てるために、代入ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="393df-116">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="393df-117">この例の等号 (`=`) は、等値演算子ではなく代入演算子です。</span><span class="sxs-lookup"><span data-stu-id="393df-117">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="393df-118">この値は、変数 `applesSold` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="393df-118">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="393df-119">詳細については、「[方法:変数に値を格納する、および変数から値を取得する](how-to-move-data-into-and-out-of-a-variable.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="393df-119">For more information, see [How to: Move Data Into and Out of a Variable](how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="393df-120">変数とプロパティ</span><span class="sxs-lookup"><span data-stu-id="393df-120">Variables and Properties</span></span>  

 <span data-ttu-id="393df-121">変数と同様に、*プロパティ* はアクセス可能な値です。</span><span class="sxs-lookup"><span data-stu-id="393df-121">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="393df-122">ただし、変数よりも複雑です。</span><span class="sxs-lookup"><span data-stu-id="393df-122">However, it is more complex than a variable.</span></span> <span data-ttu-id="393df-123">プロパティは、その値を設定し取得する方法を制御するコード ブロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="393df-123">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="393df-124">詳細については、「[Visual Basic のプロパティと変数の違い](../procedures/differences-between-properties-and-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="393df-124">For more information, see [Differences Between Properties and Variables in Visual Basic](../procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="393df-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="393df-125">See also</span></span>

- [<span data-ttu-id="393df-126">変数宣言</span><span class="sxs-lookup"><span data-stu-id="393df-126">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="393df-127">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="393df-127">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="393df-128">変数のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="393df-128">Troubleshooting Variables</span></span>](troubleshooting-variables.md)
- [<span data-ttu-id="393df-129">方法: 変数に値を格納する、および変数から値を取得する</span><span class="sxs-lookup"><span data-stu-id="393df-129">How to: Move Data Into and Out of a Variable</span></span>](how-to-move-data-into-and-out-of-a-variable.md)
- [<span data-ttu-id="393df-130">Visual Basic のプロパティと変数の違い</span><span class="sxs-lookup"><span data-stu-id="393df-130">Differences Between Properties and Variables in Visual Basic</span></span>](../procedures/differences-between-properties-and-variables.md)
- [<span data-ttu-id="393df-131">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="393df-131">Local Type Inference</span></span>](local-type-inference.md)
