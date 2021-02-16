---
description: '詳細情報: 方法:演算子を定義するクラスを使用する (Visual Basic)'
title: '方法: 演算子を定義するクラスを使用する'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: 4bf5321fbf1868ad0214d0f4781df30dc8f92ac9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455744"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="4ec53-103">方法: 演算子を定義するクラスを使用する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ec53-103">How to: Use a Class that Defines Operators (Visual Basic)</span></span>

<span data-ttu-id="4ec53-104">独自の演算子が定義されているクラスまたは構造体を使用する場合、Visual Basic からそれらの演算子にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="4ec53-104">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="4ec53-105">クラスまたは構造体での演算子の定義は、演算子の "*オーバーロード*" とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4ec53-105">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ec53-106">例</span><span class="sxs-lookup"><span data-stu-id="4ec53-106">Example</span></span>  

 <span data-ttu-id="4ec53-107">次の例では、SQL 文字列と Visual Basic 文字列の間の双方向の変換演算子 ([CType 関数](../../../language-reference/functions/ctype-function.md)) が定義されている、SQL 構造体 <xref:System.Data.SqlTypes.SqlString> にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="4ec53-107">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="4ec53-108">`CType(`*SQL 文字列式*, `String)` を使用して SQL 文字列を Visual Basic 文字列に変換し、`CType(`*Visual Basic 文字列式*, <xref:System.Data.SqlTypes.SqlString>`)` を使用して逆方向に変換します。</span><span class="sxs-lookup"><span data-stu-id="4ec53-108">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="4ec53-109"><xref:System.Data.SqlTypes.SqlString> 構造体では、`String` から <xref:System.Data.SqlTypes.SqlString> への変換演算子 ([CType 関数](../../../language-reference/functions/ctype-function.md)) と、<xref:System.Data.SqlTypes.SqlString> から `String` への別の変換演算子が定義されています。</span><span class="sxs-lookup"><span data-stu-id="4ec53-109">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="4ec53-110">`title` を `jobTitle` に割り当てるステートメントでは最初の演算子を使用し、<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 関数呼び出しでは 2 番目の演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="4ec53-110">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="4ec53-111">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="4ec53-111">Compile the code</span></span>  

 <span data-ttu-id="4ec53-112">使用しているクラスまたは構造体で、使用する演算子が定義されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4ec53-112">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="4ec53-113">クラスまたは構造体で、オーバーロードに使用できるすべての演算子が定義されていると想定しないでください。</span><span class="sxs-lookup"><span data-stu-id="4ec53-113">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="4ec53-114">使用可能な演算子の一覧については、「[Operator Statement (Operator ステートメント)](../../../language-reference/statements/operator-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4ec53-114">For a list of available operators, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="4ec53-115">ソース ファイルの先頭に、SQL 文字列の適切な `Imports` ステートメントを含めます (この例では <xref:System.Data.SqlTypes>)。</span><span class="sxs-lookup"><span data-stu-id="4ec53-115">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="4ec53-116">プロジェクトには、System.Data および System.XML への参照が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ec53-116">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ec53-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ec53-117">See also</span></span>

- [<span data-ttu-id="4ec53-118">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="4ec53-118">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="4ec53-119">方法: 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="4ec53-119">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="4ec53-120">方法: 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="4ec53-120">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="4ec53-121">方法: 演算子プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="4ec53-121">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="4ec53-122">Widening</span><span class="sxs-lookup"><span data-stu-id="4ec53-122">Widening</span></span>](../../../language-reference/modifiers/widening.md)
- [<span data-ttu-id="4ec53-123">Narrowing</span><span class="sxs-lookup"><span data-stu-id="4ec53-123">Narrowing</span></span>](../../../language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="4ec53-124">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="4ec53-124">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="4ec53-125">方法: 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="4ec53-125">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="4ec53-126">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="4ec53-126">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="4ec53-127">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="4ec53-127">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
