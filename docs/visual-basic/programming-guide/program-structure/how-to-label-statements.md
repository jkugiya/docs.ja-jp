---
description: '詳細情報: 方法:ステートメントにラベルを付ける (Visual Basic)'
title: '方法: ステートメントへのラベル付け'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 4efb320dad7d52f6e9b94f6e6f81730f94b5966b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433253"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="2cd61-103">方法: ステートメントにラベルを付ける (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cd61-103">How to: Label Statements (Visual Basic)</span></span>

<span data-ttu-id="2cd61-104">ステートメント ブロックは、コロンで区切られたコード行で構成されます。</span><span class="sxs-lookup"><span data-stu-id="2cd61-104">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="2cd61-105">行の前に識別文字列または整数が指定されたコード行は、"*ラベル付けされている*" といいます。</span><span class="sxs-lookup"><span data-stu-id="2cd61-105">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="2cd61-106">`On Error Goto` などのステートメントで使用するために、ステートメント ラベルでコード行をマークして識別します。</span><span class="sxs-lookup"><span data-stu-id="2cd61-106">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>

<span data-ttu-id="2cd61-107">ラベルには、有効な Visual Basic 識別子 (プログラミング要素を識別するものなど) または整数リテラルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2cd61-107">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="2cd61-108">ラベルは、ソース コードの行の先頭に配置する必要があり、その後にコロンを指定する必要があります。同じ行でコロンの後にステートメントが続くかどうかは関係ありません。</span><span class="sxs-lookup"><span data-stu-id="2cd61-108">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>

<span data-ttu-id="2cd61-109">コンパイラは、行の先頭が既に定義されている識別子と一致するかどうかをチェックすることでラベルを識別します。</span><span class="sxs-lookup"><span data-stu-id="2cd61-109">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="2cd61-110">一致しない場合、コンパイラはそれをラベルと見なします。</span><span class="sxs-lookup"><span data-stu-id="2cd61-110">If it does not, the compiler assumes it is a label.</span></span>

<span data-ttu-id="2cd61-111">ラベルには独自の宣言領域があり、他の識別子に干渉することはありません。</span><span class="sxs-lookup"><span data-stu-id="2cd61-111">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="2cd61-112">ラベルのスコープはメソッドの本体です。</span><span class="sxs-lookup"><span data-stu-id="2cd61-112">A label's scope is the body of the method.</span></span> <span data-ttu-id="2cd61-113">あいまいな状況では、ラベルの宣言が優先されます。</span><span class="sxs-lookup"><span data-stu-id="2cd61-113">Label declaration takes precedence in any ambiguous situation.</span></span>

> [!NOTE]
> <span data-ttu-id="2cd61-114">ラベルは、メソッド内の実行可能なステートメントでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="2cd61-114">Labels can be used only on executable statements inside methods.</span></span>

## <a name="to-label-a-line-of-code"></a><span data-ttu-id="2cd61-115">コード行にラベルを付けるには</span><span class="sxs-lookup"><span data-stu-id="2cd61-115">To label a line of code</span></span>

<span data-ttu-id="2cd61-116">ソース コードの行の先頭に識別子を配置し、その後にコロンを配置します。</span><span class="sxs-lookup"><span data-stu-id="2cd61-116">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>

<span data-ttu-id="2cd61-117">たとえば、次のコード行は、それぞれ `Jump` と `120` でラベル付けされています。</span><span class="sxs-lookup"><span data-stu-id="2cd61-117">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>

[!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]

## <a name="see-also"></a><span data-ttu-id="2cd61-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="2cd61-118">See also</span></span>

- [<span data-ttu-id="2cd61-119">ステートメント</span><span class="sxs-lookup"><span data-stu-id="2cd61-119">Statements</span></span>](../language-features/statements.md)
- [<span data-ttu-id="2cd61-120">宣言された要素の名前</span><span class="sxs-lookup"><span data-stu-id="2cd61-120">Declared Element Names</span></span>](../language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="2cd61-121">プログラム構造とコード規則</span><span class="sxs-lookup"><span data-stu-id="2cd61-121">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
