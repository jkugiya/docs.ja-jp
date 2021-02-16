---
description: '詳細情報: 方法:変数のスコープを制御する (Visual Basic)'
title: '方法: 変数のスコープを制御する'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: c6da599f76883cba545efbdf9570aa05770602a2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429872"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="8b614-103">方法: 変数のスコープを制御する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b614-103">How to: Control the Scope of a Variable (Visual Basic)</span></span>

<span data-ttu-id="8b614-104">通常、変数は、*スコープ* 内にあります。つまり、それを宣言した領域全体で可視になり参照できます。</span><span class="sxs-lookup"><span data-stu-id="8b614-104">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="8b614-105">場合によって、変数の *アクセス レベル* がそのスコープに影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="8b614-105">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="8b614-106">詳細については、「 [Scope in Visual Basic](scope.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b614-106">For more information, see [Scope in Visual Basic](scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="8b614-107">ブロック レベルまたはプロシージャ レベルのスコープ</span><span class="sxs-lookup"><span data-stu-id="8b614-107">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="8b614-108">変数をブロック内でのみ可視にするには</span><span class="sxs-lookup"><span data-stu-id="8b614-108">To make a variable visible only within a block</span></span>  
  
- <span data-ttu-id="8b614-109">変数の [Dim ステートメント](../../../language-reference/statements/dim-statement.md)を、そのブロックの開始と終了の宣言ステートメントの間、たとえば `For` ループの `For` ステートメントと `Next` ステートメントの間などに配置します。</span><span class="sxs-lookup"><span data-stu-id="8b614-109">Place the [Dim Statement](../../../language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="8b614-110">変数は、ブロック内からのみ参照できます。</span><span class="sxs-lookup"><span data-stu-id="8b614-110">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="8b614-111">変数をプロシージャ内でのみ可視にするには</span><span class="sxs-lookup"><span data-stu-id="8b614-111">To make a variable visible only within a procedure</span></span>  
  
- <span data-ttu-id="8b614-112">変数の `Dim` ステートメントをプロシージャ内、ただし、ブロック (`With`...`End With` ブロックなど) の外部に配置します。</span><span class="sxs-lookup"><span data-stu-id="8b614-112">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="8b614-113">プロシージャに含まれている任意のブロック内など、プロシージャ内からのみ変数を参照できます。</span><span class="sxs-lookup"><span data-stu-id="8b614-113">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="8b614-114">モジュールまたは名前空間レベルのスコープ</span><span class="sxs-lookup"><span data-stu-id="8b614-114">Scope at Module or Namespace Level</span></span>  

 <span data-ttu-id="8b614-115">便宜上、*モジュール レベル* という 1 つの用語は、モジュール、クラス、および構造体に等しく適用されます。</span><span class="sxs-lookup"><span data-stu-id="8b614-115">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="8b614-116">モジュール レベル変数のアクセスレベルによってそのスコープが決まります。</span><span class="sxs-lookup"><span data-stu-id="8b614-116">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="8b614-117">モジュール、クラス、または構造体を含む名前空間もスコープに影響します。</span><span class="sxs-lookup"><span data-stu-id="8b614-117">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="8b614-118">変数をモジュール、クラス、または構造体全体で可視にするには</span><span class="sxs-lookup"><span data-stu-id="8b614-118">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="8b614-119">モジュール、クラス、または構造体の内部で、ただしプロシージャの外部に、変数の `Dim` ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="8b614-119">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="8b614-120">`Dim` ステートメントに [Private](../../../language-reference/modifiers/private.md) キーワードを含めます。</span><span class="sxs-lookup"><span data-stu-id="8b614-120">Include the [Private](../../../language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="8b614-121">変数は、モジュール、クラス、または構造体内のどこからでも参照できますが、その外部から参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="8b614-121">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="8b614-122">変数を名前空間全体で可視にするには</span><span class="sxs-lookup"><span data-stu-id="8b614-122">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="8b614-123">モジュール、クラス、または構造体の内部で、ただしプロシージャの外部に、変数の `Dim` ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="8b614-123">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="8b614-124">`Dim` ステートメントに [Friend](../../../language-reference/modifiers/friend.md) または [Public](../../../language-reference/modifiers/public.md) キーワードを含めます。</span><span class="sxs-lookup"><span data-stu-id="8b614-124">Include the [Friend](../../../language-reference/modifiers/friend.md) or [Public](../../../language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="8b614-125">変数は、モジュール、クラス、または構造体を含む名前空間内のどこからでも参照できます。</span><span class="sxs-lookup"><span data-stu-id="8b614-125">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b614-126">例</span><span class="sxs-lookup"><span data-stu-id="8b614-126">Example</span></span>  

 <span data-ttu-id="8b614-127">次の例では、モジュール レベルで変数を宣言し、その可視性をモジュール内のコードに制限しています。</span><span class="sxs-lookup"><span data-stu-id="8b614-127">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
```vb  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="8b614-128">前の例では、モジュール `demonstrateScope` に定義されているすべてのプロシージャで、`String` 変数 `strMsg` を参照できます。</span><span class="sxs-lookup"><span data-stu-id="8b614-128">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="8b614-129">`strMsg` プロシージャを呼び出すと、文字列変数 `usePrivateVariable` の内容がダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8b614-129">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="8b614-130">前の例を次のように変更すると、文字列変数 `strMsg` は、その宣言の名前空間内のどこでもコードによって参照できます。</span><span class="sxs-lookup"><span data-stu-id="8b614-130">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="8b614-131">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="8b614-131">Robust Programming</span></span>  

 <span data-ttu-id="8b614-132">変数のスコープを狭めるほど、同じ名前を持つ別の変数の代わりに、誤ってそれを参照してしまう可能性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="8b614-132">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="8b614-133">参照マッチングに関する問題を最小限に抑えることもできます。</span><span class="sxs-lookup"><span data-stu-id="8b614-133">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8b614-134">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="8b614-134">.NET Framework Security</span></span>  

 <span data-ttu-id="8b614-135">変数のスコープを狭めるほど、悪意のあるコードによってそれが不正使用される可能性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="8b614-135">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b614-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b614-136">See also</span></span>

- [<span data-ttu-id="8b614-137">Visual Basic におけるスコープ</span><span class="sxs-lookup"><span data-stu-id="8b614-137">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="8b614-138">Visual Basic における有効期間</span><span class="sxs-lookup"><span data-stu-id="8b614-138">Lifetime in Visual Basic</span></span>](lifetime.md)
- [<span data-ttu-id="8b614-139">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="8b614-139">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="8b614-140">変数</span><span class="sxs-lookup"><span data-stu-id="8b614-140">Variables</span></span>](../variables/index.md)
- [<span data-ttu-id="8b614-141">変数宣言</span><span class="sxs-lookup"><span data-stu-id="8b614-141">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="8b614-142">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="8b614-142">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
