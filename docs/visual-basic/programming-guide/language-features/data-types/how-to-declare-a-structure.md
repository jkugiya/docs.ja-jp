---
description: '詳細情報: 方法:構造体を宣言する (Visual Basic)'
title: '方法: 構造体を宣言する'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 7560f22db70fd5804ca309720d32477bcb9a3782
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436930"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="64b72-103">方法: 構造体を宣言する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64b72-103">How to: Declare a Structure (Visual Basic)</span></span>

<span data-ttu-id="64b72-104">構造体宣言は、[Structure ステートメント](../../../language-reference/statements/structure-statement.md)で始まり、`End Structure` ステートメントで終了します。</span><span class="sxs-lookup"><span data-stu-id="64b72-104">You begin a structure declaration with the [Structure Statement](../../../language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span></span> <span data-ttu-id="64b72-105">これら 2 つのステートメントの間には、少なくとも 1 つの "*要素*" を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64b72-105">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="64b72-106">要素は任意のデータ型にすることができますが、少なくとも 1 つは非共有変数または非共有非カスタム イベントのいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="64b72-106">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="64b72-107">構造体宣言で構造体の要素を初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="64b72-107">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="64b72-108">変数を構造体型として宣言するときは、変数を使用して値にアクセスすることによって、要素に値を代入します。</span><span class="sxs-lookup"><span data-stu-id="64b72-108">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="64b72-109">構造体とクラスの違いについては、「[構造体とクラス](structures-and-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64b72-109">For a discussion of the differences between structures and classes, see [Structures and Classes](structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="64b72-110">デモンストレーションとして、従業員の名前、内線電話番号、給与を追跡するケースについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="64b72-110">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="64b72-111">構造体を使用すると、1 つの変数でこれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="64b72-111">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="64b72-112">構造体を宣言するには</span><span class="sxs-lookup"><span data-stu-id="64b72-112">To declare a structure</span></span>  
  
1. <span data-ttu-id="64b72-113">構造体の開始と終了のステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="64b72-113">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="64b72-114">構造体のアクセス レベルを、[Public](../../../language-reference/modifiers/public.md)、[Protected](../../../language-reference/modifiers/protected.md)、[Friend](../../../language-reference/modifiers/friend.md)、または [Private](../../../language-reference/modifiers/private.md) キーワードを使用して指定できます。あるいは、既定で `Public` にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="64b72-114">You can specify the access level of a structure using the [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), or [Private](../../../language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. <span data-ttu-id="64b72-115">構造体の本体に要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="64b72-115">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="64b72-116">構造体には要素が少なくとも 1 つ必要です。</span><span class="sxs-lookup"><span data-stu-id="64b72-116">A structure must have at least one element.</span></span> <span data-ttu-id="64b72-117">すべての要素を宣言し、そのアクセス レベルを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64b72-117">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="64b72-118">キーワードを指定せずに [Dim ステートメント](../../../language-reference/statements/dim-statement.md)を使用すると、アクセシビリティは既定の `Public` になります。</span><span class="sxs-lookup"><span data-stu-id="64b72-118">If you use the [Dim Statement](../../../language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     <span data-ttu-id="64b72-119">前の例の `salary` フィールドは `Private` です。つまり、構造体の外部からはアクセスできないことを意味します。それが含まれているクラスからでもできません。</span><span class="sxs-lookup"><span data-stu-id="64b72-119">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="64b72-120">ただし、`giveRaise` プロシージャは `Public` であるため、構造体の外部から呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="64b72-120">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="64b72-121">同様に、構造体の外部から `salaryReviewTime` イベントを発生させることもできます。</span><span class="sxs-lookup"><span data-stu-id="64b72-121">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="64b72-122">変数、`Sub` プロシージャ、およびイベントに加えて、構造体に定数、`Function` プロシージャ、およびプロパティを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="64b72-122">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="64b72-123">最大 1 つのプロパティを "*既定プロパティ*" として指定できます (そのプロパティが少なくとも 1 つの引数を取る場合)。</span><span class="sxs-lookup"><span data-stu-id="64b72-123">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="64b72-124">[共有](../../../language-reference/modifiers/shared.md) `Sub` プロシージャを使用してイベントを処理できます。</span><span class="sxs-lookup"><span data-stu-id="64b72-124">You can handle an event with a [Shared](../../../language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="64b72-125">詳細については、「[方法:既定のプロパティを宣言して呼び出す (Visual Basic)](../procedures/how-to-declare-and-call-a-default-property.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64b72-125">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64b72-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="64b72-126">See also</span></span>

- [<span data-ttu-id="64b72-127">データの種類</span><span class="sxs-lookup"><span data-stu-id="64b72-127">Data Types</span></span>](index.md)
- [<span data-ttu-id="64b72-128">基本データ型</span><span class="sxs-lookup"><span data-stu-id="64b72-128">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="64b72-129">複合データ型</span><span class="sxs-lookup"><span data-stu-id="64b72-129">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="64b72-130">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="64b72-130">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="64b72-131">構造体</span><span class="sxs-lookup"><span data-stu-id="64b72-131">Structures</span></span>](structures.md)
- [<span data-ttu-id="64b72-132">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="64b72-132">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="64b72-133">構造体変数</span><span class="sxs-lookup"><span data-stu-id="64b72-133">Structure Variables</span></span>](structure-variables.md)
- [<span data-ttu-id="64b72-134">構造体とその他のプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="64b72-134">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)
- [<span data-ttu-id="64b72-135">構造体とクラス</span><span class="sxs-lookup"><span data-stu-id="64b72-135">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="64b72-136">ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="64b72-136">User-Defined Data Type</span></span>](../../../language-reference/data-types/user-defined-data-type.md)
