---
description: '詳細情報: コード内の要素名としてのキーワード (Visual Basic)'
title: コード内の要素名としてのキーワード
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 4782c0f3ea065e3e140d449575c187cf2254cd08
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433214"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="8d4d8-103">コード内の要素名としてのキーワード (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d4d8-103">Keywords as Element Names in Code (Visual Basic)</span></span>

<span data-ttu-id="8d4d8-104">変数、クラス、メンバーなどのプログラム要素には、制限付きキーワードと同じ名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-104">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="8d4d8-105">たとえば、`Loop` という名前の変数を作成できます。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-105">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="8d4d8-106">ただし、制限付きキーワード `Loop` と同じ名前のバージョンを参照するには、次の例に示すように、名前の前に完全修飾文字列を指定するか、名前を角かっこ (`[ ]`) で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-106">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 <span data-ttu-id="8d4d8-107">次の例のように、これらのいずれも行わない場合、Visual Basic では組み込みキーワード `Loop` が使用されていると見なされ、エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-107">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="8d4d8-108">フォームおよびコントロールを参照するときや、制限付きキーワードと同じ名前で変数を宣言したり、プロシージャを定義したりするときは、角かっこを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-108">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="8d4d8-109">名前を修飾したり、角かっこを含めたりするのを忘れやすいため、コードでエラーが発生し、読みにくくなります。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-109">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="8d4d8-110">そのため、プログラム要素の名前として制限付きキーワードを使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-110">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="8d4d8-111">ただし、Visual Basic の将来のバージョンで、既存のフォームやコントロールの名前と競合する新しいキーワードが定義された場合は、その新しいバージョンで機能するようにコードを更新するときにこの手法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-111">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d4d8-112">また、他の参照アセンブリによって提供される要素名がプログラムに含まれている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-112">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="8d4d8-113">これらの名前が制限付きキーワードと競合する場合は、それらを角かっこで囲むと、定義済みの要素と解釈されます。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-113">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d4d8-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d4d8-114">See also</span></span>

- [<span data-ttu-id="8d4d8-115">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="8d4d8-115">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
- [<span data-ttu-id="8d4d8-116">プログラム構造とコード規則</span><span class="sxs-lookup"><span data-stu-id="8d4d8-116">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="8d4d8-117">キーワード</span><span class="sxs-lookup"><span data-stu-id="8d4d8-117">Keywords</span></span>](../../language-reference/keywords/index.md)
