---
description: '詳細情報: 方法:プロシージャの複数のバージョンを定義する (Visual Basic)'
title: '方法: プロシージャの複数のバージョンを定義する'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: 4b470e478c22c3a827f71b9b28056e16d6d9b7cd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456030"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="9fa77-103">方法: プロシージャの複数のバージョンを定義する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fa77-103">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>

<span data-ttu-id="9fa77-104">同じ名前を使用し、バージョンごとに異なるパラメーター リストを使用して、"*オーバーロード*" することにより、複数のバージョンのプロシージャを定義できます。</span><span class="sxs-lookup"><span data-stu-id="9fa77-104">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="9fa77-105">オーバーロードの目的は、名前で区別する必要なく、プロシージャの密接に関連する複数のバージョンを定義することです。</span><span class="sxs-lookup"><span data-stu-id="9fa77-105">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="9fa77-106">詳細については、「 [Procedure Overloading](./procedure-overloading.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9fa77-106">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="9fa77-107">プロシージャの複数のバージョンを定義するには</span><span class="sxs-lookup"><span data-stu-id="9fa77-107">To define multiple versions of a procedure</span></span>  
  
1. <span data-ttu-id="9fa77-108">定義するプロシージャのバージョンごとに、`Sub` または `Function` 宣言ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="9fa77-108">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="9fa77-109">すべての宣言で同じプロシージャ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="9fa77-109">Use the same procedure name in every declaration.</span></span>  
  
2. <span data-ttu-id="9fa77-110">各宣言の `Sub` または `Function` キーワードの前に [Overloads](../../../language-reference/modifiers/overloads.md) キーワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="9fa77-110">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="9fa77-111">必要に応じて、宣言で `Overloads` を省略することもできますが、宣言のいずれかに含めた場合は、すべての宣言に含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fa77-111">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3. <span data-ttu-id="9fa77-112">各宣言ステートメントの後に、呼び出し元のコードでそのバージョンのパラメーター リストと一致する引数が指定されたときにそのケースを処理するプロシージャ コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="9fa77-112">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="9fa77-113">呼び出し元のコードでどのパラメーターが指定されているかをテストする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9fa77-113">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="9fa77-114">Visual Basic は、プロシージャの一致するバージョンに制御を渡します。</span><span class="sxs-lookup"><span data-stu-id="9fa77-114">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4. <span data-ttu-id="9fa77-115">プロシージャの各バージョンを、必要に応じて `End Sub` または `End Function` ステートメントで終了します。</span><span class="sxs-lookup"><span data-stu-id="9fa77-115">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fa77-116">例</span><span class="sxs-lookup"><span data-stu-id="9fa77-116">Example</span></span>  

 <span data-ttu-id="9fa77-117">次の例では、顧客の残高に対してトランザクションを転記する `Sub` プロシージャを定義します。</span><span class="sxs-lookup"><span data-stu-id="9fa77-117">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="9fa77-118">`Overloads` キーワードを使用して、プロシージャの 2 つのバージョンを定義します。1 つは顧客を名前で受け入れ、もう 1 つは口座番号で受け入れます。</span><span class="sxs-lookup"><span data-stu-id="9fa77-118">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 <span data-ttu-id="9fa77-119">呼び出し元のコードは、`String` または `Integer` として顧客 ID を取得し、どちらの場合も同じ呼び出しステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9fa77-119">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="9fa77-120">`post` プロシージャのこれらのバージョンを呼び出す方法については、「[How to: Call an Overloaded Procedure (方法: オーバーロードされたプロシージャを呼び出す)](./how-to-call-an-overloaded-procedure.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9fa77-120">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="9fa77-121">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="9fa77-121">Compile the code</span></span>  

 <span data-ttu-id="9fa77-122">オーバーロードされた各バージョンのプロシージャ名が同じであり、パラメーター リストが異なることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9fa77-122">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa77-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="9fa77-123">See also</span></span>

- [<span data-ttu-id="9fa77-124">手順</span><span class="sxs-lookup"><span data-stu-id="9fa77-124">Procedures</span></span>](./index.md)
- [<span data-ttu-id="9fa77-125">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="9fa77-125">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="9fa77-126">プロシージャのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="9fa77-126">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="9fa77-127">方法: 省略可能なパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="9fa77-127">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="9fa77-128">方法: 不特定数のパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="9fa77-128">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="9fa77-129">プロシージャのオーバーロードに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="9fa77-129">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="9fa77-130">オーバーロードの解決</span><span class="sxs-lookup"><span data-stu-id="9fa77-130">Overload Resolution</span></span>](./overload-resolution.md)
