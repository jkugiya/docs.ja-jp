---
description: '詳細情報: #If...Then...#Else ディレクティブ'
title: '#If...Then...#Else ディレクティブ'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
ms.openlocfilehash: fd95d259315e0bd6fd6ab2a3f222288bb4726ce6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797251"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="41299-103">#If...Then...#Else ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="41299-103">#If...Then...#Else Directives</span></span>

<span data-ttu-id="41299-104">選択された Visual Basic コード ブロックを条件付きでコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="41299-104">Conditionally compiles selected blocks of Visual Basic code.</span></span>

## <a name="syntax"></a><span data-ttu-id="41299-105">構文</span><span class="sxs-lookup"><span data-stu-id="41299-105">Syntax</span></span>

```vb
#If expression Then
   statements
[ #ElseIf expression Then
   [ statements ]
...
#ElseIf expression Then
   [ statements ] ]
[ #Else
   [ statements ] ]
#End If
```

## <a name="parts"></a><span data-ttu-id="41299-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="41299-106">Parts</span></span>

`expression`  
<span data-ttu-id="41299-107">`#If` および `#ElseIf` ステートメントでは必須、その他の場所では省略可能です。</span><span class="sxs-lookup"><span data-stu-id="41299-107">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="41299-108">1 つ以上の条件付きコンパイラ定数、リテラル、演算子のみで構成され、`True` または `False` に評価される式です。</span><span class="sxs-lookup"><span data-stu-id="41299-108">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>

`statements`  
<span data-ttu-id="41299-109">`#If` ステートメント ブロックでは必須、その他の場所では省略可能です。</span><span class="sxs-lookup"><span data-stu-id="41299-109">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="41299-110">関連する式が `True` に評価された場合にコンパイルされる、Visual Basic のプログラム行またはコンパイラ ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="41299-110">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>

`#End If`  
<span data-ttu-id="41299-111">`#If` ステートメント ブロックを終了します。</span><span class="sxs-lookup"><span data-stu-id="41299-111">Terminates the `#If` statement block.</span></span>

## <a name="remarks"></a><span data-ttu-id="41299-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="41299-112">Remarks</span></span>

<span data-ttu-id="41299-113">表面上、`#If...Then...#Else` ディレクティブの動作は `If...Then...Else` ステートメントの動作と同じように見えます。</span><span class="sxs-lookup"><span data-stu-id="41299-113">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="41299-114">ただし、`#If...Then...#Else` ディレクティブではコンパイラによってコンパイルされる内容が評価されるのに対し、`If...Then...Else` ステートメントでは実行時に条件が評価されます。</span><span class="sxs-lookup"><span data-stu-id="41299-114">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>

<span data-ttu-id="41299-115">通常、条件付きコンパイルは、異なるプラットフォームで同じプログラムをコンパイルする場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="41299-115">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="41299-116">また、デバッグ コードが実行可能ファイルに現れないようにするためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="41299-116">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="41299-117">条件付きコンパイルで除外されたコードは、最終的な実行可能ファイルから完全に削除されるため、サイズやパフォーマンスに影響しません。</span><span class="sxs-lookup"><span data-stu-id="41299-117">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>

<span data-ttu-id="41299-118">評価の結果に関係なく、すべての式は `Option Compare Binary` を使用して評価されます。</span><span class="sxs-lookup"><span data-stu-id="41299-118">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="41299-119">`Option Compare` ステートメントは、`#If` および `#ElseIf` ステートメントの式には作用しません。</span><span class="sxs-lookup"><span data-stu-id="41299-119">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>

> [!NOTE]
> <span data-ttu-id="41299-120">1 行形式の `#If`、`#Else`、`#ElseIf`、`#End If` ディレクティブは存在しません。</span><span class="sxs-lookup"><span data-stu-id="41299-120">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="41299-121">この各ディレクティブと同じ行に他のコードを記述することはできません。</span><span class="sxs-lookup"><span data-stu-id="41299-121">No other code can appear on the same line as any of the directives.</span></span>

<span data-ttu-id="41299-122">条件付きコンパイル ブロック内のステートメントは、完全な論理ステートメントでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="41299-122">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="41299-123">たとえば、関数の属性のみを条件付きでコンパイルすることはできませんが、次のように関数をその属性ととも条件付きで宣言することはできます。</span><span class="sxs-lookup"><span data-stu-id="41299-123">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
#If DEBUG Then
<WebMethod()>
Public Function SomeFunction() As String
#Else
<WebMethod(CacheDuration:=86400)>
Public Function SomeFunction() As String
#End If
```

## <a name="example"></a><span data-ttu-id="41299-124">例</span><span class="sxs-lookup"><span data-stu-id="41299-124">Example</span></span>

<span data-ttu-id="41299-125">この例では、`#If...Then...#Else` コンストラクトを使用して、特定のステートメントをコンパイルするかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="41299-125">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="41299-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="41299-126">See also</span></span>

- [<span data-ttu-id="41299-127">#Const ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="41299-127">#Const Directive</span></span>](const-directive.md)
- [<span data-ttu-id="41299-128">If...Then...Else ステートメント</span><span class="sxs-lookup"><span data-stu-id="41299-128">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="41299-129">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="41299-129">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
