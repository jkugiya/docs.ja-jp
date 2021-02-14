---
description: '詳細情報: #Const ディレクティブ'
title: '#Const ディレクティブ'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: 9597666ee1320f5dfda226040f93a84eb60a3deb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797277"
---
# <a name="const-directive"></a><span data-ttu-id="b9e02-103">#Const ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="b9e02-103">#Const Directive</span></span>

<span data-ttu-id="b9e02-104">Visual Basic の条件付きコンパイラ定数を定義します。</span><span class="sxs-lookup"><span data-stu-id="b9e02-104">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9e02-105">構文</span><span class="sxs-lookup"><span data-stu-id="b9e02-105">Syntax</span></span>  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="b9e02-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="b9e02-106">Parts</span></span>  

 `constname`  
 <span data-ttu-id="b9e02-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="b9e02-107">Required.</span></span> <span data-ttu-id="b9e02-108">定義している定数の名前。</span><span class="sxs-lookup"><span data-stu-id="b9e02-108">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="b9e02-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="b9e02-109">Required.</span></span> <span data-ttu-id="b9e02-110">リテラル、他の条件付きコンパイラ定数、または、`Is` 以外の算術演算子または論理演算子のいずれか、またはすべてを含む任意の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="b9e02-110">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9e02-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="b9e02-111">Remarks</span></span>  

 <span data-ttu-id="b9e02-112">条件付きコンパイラ定数は、それらが出現するファイルに対して常にプライベートです。</span><span class="sxs-lookup"><span data-stu-id="b9e02-112">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="b9e02-113">`#Const` ディレクティブを使用して、パブリック コンパイラ定数を作成することはできません。これらは、ユーザー インターフェイス内、または `/define` コンパイラ オプションを使用する場合にのみ作成できます。</span><span class="sxs-lookup"><span data-stu-id="b9e02-113">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="b9e02-114">`expression` では、条件付きコンパイラ定数とリテラルのみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b9e02-114">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="b9e02-115">`Const` で定義された標準定数を使用すると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b9e02-115">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="b9e02-116">逆に、`#Const` キーワードによって定義された定数は、条件付きコンパイルにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b9e02-116">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="b9e02-117">定数を未定義にすることもできます。その場合、値は `Nothing` になります。</span><span class="sxs-lookup"><span data-stu-id="b9e02-117">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9e02-118">例</span><span class="sxs-lookup"><span data-stu-id="b9e02-118">Example</span></span>  

 <span data-ttu-id="b9e02-119">`#Const` ディレクティブの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b9e02-119">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b9e02-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9e02-120">See also</span></span>

- [<span data-ttu-id="b9e02-121">-define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9e02-121">-define (Visual Basic)</span></span>](../../reference/command-line-compiler/define.md)
- [<span data-ttu-id="b9e02-122">#If...Then...#Else ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="b9e02-122">#If...Then...#Else Directives</span></span>](if-then-else-directives.md)
- [<span data-ttu-id="b9e02-123">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="b9e02-123">Const Statement</span></span>](../statements/const-statement.md)
- [<span data-ttu-id="b9e02-124">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="b9e02-124">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="b9e02-125">If...Then...Else ステートメント</span><span class="sxs-lookup"><span data-stu-id="b9e02-125">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
