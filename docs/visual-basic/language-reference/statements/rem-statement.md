---
description: '詳細情報: REM ステートメント (Visual Basic)'
title: REM ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: c82621db98dc66060ae098ee6537ee58b24046a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741316"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="0f783-103">REM ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f783-103">REM Statement (Visual Basic)</span></span>

<span data-ttu-id="0f783-104">プログラムのソース コード内に説明のための注記を含めるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0f783-104">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f783-105">構文</span><span class="sxs-lookup"><span data-stu-id="0f783-105">Syntax</span></span>  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="0f783-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="0f783-106">Parts</span></span>  

 `comment`  
 <span data-ttu-id="0f783-107">任意。</span><span class="sxs-lookup"><span data-stu-id="0f783-107">Optional.</span></span> <span data-ttu-id="0f783-108">含めるコメントのテキストです。</span><span class="sxs-lookup"><span data-stu-id="0f783-108">The text of any comment you want to include.</span></span> <span data-ttu-id="0f783-109">`REM` キーワードと `comment` の間にはスペースが必要です。</span><span class="sxs-lookup"><span data-stu-id="0f783-109">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f783-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="0f783-110">Remarks</span></span>  

 <span data-ttu-id="0f783-111">`REM` ステートメントを 1 行に単独で配置することも、別のステートメントの後の行に配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="0f783-111">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="0f783-112">`REM` ステートメントは行の最後のステートメントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f783-112">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="0f783-113">別のステートメントの後に続く場合、`REM` は、そのステートメントとスペースで区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f783-113">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="0f783-114">`REM` ではなく、単一引用符 (`'`) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0f783-114">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="0f783-115">これは、コメントが同じ行で別のステートメントの後に続くか 1 つの行に単独で存在するかにかかわらず当てはまります。</span><span class="sxs-lookup"><span data-stu-id="0f783-115">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f783-116">行連結シーケンス (`_`) を使用して `REM` ステートメントを継続することはできません。</span><span class="sxs-lookup"><span data-stu-id="0f783-116">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="0f783-117">コメントが開始された後、コンパイラは、文字に特別な意味があるかどうかを調べません。</span><span class="sxs-lookup"><span data-stu-id="0f783-117">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="0f783-118">複数行のコメントでは、各行で別の `REM` ステートメントまたはコメント記号 (`'`) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="0f783-118">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f783-119">例</span><span class="sxs-lookup"><span data-stu-id="0f783-119">Example</span></span>  

 <span data-ttu-id="0f783-120">次の例では、プログラム内に説明のための注記を含めるために使用される `REM` ステートメントを示しています。</span><span class="sxs-lookup"><span data-stu-id="0f783-120">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="0f783-121">また、`REM` ではなく単一引用符文字 (`'`) を使用する別の方法も示しています。</span><span class="sxs-lookup"><span data-stu-id="0f783-121">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="0f783-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f783-122">See also</span></span>

- [<span data-ttu-id="0f783-123">コード内のコメント</span><span class="sxs-lookup"><span data-stu-id="0f783-123">Comments in Code</span></span>](../../programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="0f783-124">方法: コード内でステートメントを分割および連結する</span><span class="sxs-lookup"><span data-stu-id="0f783-124">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
