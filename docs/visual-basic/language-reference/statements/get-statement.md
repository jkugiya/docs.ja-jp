---
description: '詳細情報: Get ステートメント'
title: Get ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: 1cda485867a941129ab2453d4c0900d1403f4e8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769040"
---
# <a name="get-statement"></a><span data-ttu-id="bc062-103">Get ステートメント</span><span class="sxs-lookup"><span data-stu-id="bc062-103">Get Statement</span></span>

<span data-ttu-id="bc062-104">プロパティの値を取得するために使用する `Get` プロパティ プロシージャを宣言します。</span><span class="sxs-lookup"><span data-stu-id="bc062-104">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc062-105">構文</span><span class="sxs-lookup"><span data-stu-id="bc062-105">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="bc062-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="bc062-106">Parts</span></span>  
  
|<span data-ttu-id="bc062-107">用語</span><span class="sxs-lookup"><span data-stu-id="bc062-107">Term</span></span>|<span data-ttu-id="bc062-108">定義</span><span class="sxs-lookup"><span data-stu-id="bc062-108">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="bc062-109">任意。</span><span class="sxs-lookup"><span data-stu-id="bc062-109">Optional.</span></span> <span data-ttu-id="bc062-110">「[属性リスト](attribute-list.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc062-110">See [Attribute List](attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="bc062-111">このプロパティの `Get` および `Set` ステートメントのいずれかで、省略可能です。</span><span class="sxs-lookup"><span data-stu-id="bc062-111">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="bc062-112">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="bc062-112">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="bc062-113">-   [Protected](../modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="bc062-113">-   [Protected](../modifiers/protected.md)</span></span><br /><span data-ttu-id="bc062-114">-   [Friend](../modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="bc062-114">-   [Friend](../modifiers/friend.md)</span></span><br /><span data-ttu-id="bc062-115">-   [Private](../modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="bc062-115">-   [Private](../modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="bc062-116">「 [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc062-116">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="bc062-117">任意。</span><span class="sxs-lookup"><span data-stu-id="bc062-117">Optional.</span></span> <span data-ttu-id="bc062-118">`Get` プロパティ プロシージャが呼び出されたときに実行される 1 つ以上のステートメント。</span><span class="sxs-lookup"><span data-stu-id="bc062-118">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="bc062-119">必須です。</span><span class="sxs-lookup"><span data-stu-id="bc062-119">Required.</span></span> <span data-ttu-id="bc062-120">`Get` プロパティ プロシージャの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="bc062-120">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc062-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="bc062-121">Remarks</span></span>  

 <span data-ttu-id="bc062-122">プロパティが `WriteOnly` とマークされている場合を除き、すべてのプロパティには `Get` プロパティ プロシージャが必要です。</span><span class="sxs-lookup"><span data-stu-id="bc062-122">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="bc062-123">`Get` プロシージャは、プロパティの現在の値を返すために使用します。</span><span class="sxs-lookup"><span data-stu-id="bc062-123">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="bc062-124">Visual Basic では、式でプロパティの値が要求されると、プロパティの `Get` プロシージャが自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="bc062-124">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="bc062-125">プロパティ宣言の本体には、[Property ステートメント](property-statement.md)と `End Property` ステートメントの間に、プロパティの `Get` と `Set` のプロシージャのみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="bc062-125">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="bc062-126">これらのプロシージャ以外のものを格納することはできません。</span><span class="sxs-lookup"><span data-stu-id="bc062-126">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="bc062-127">特に、プロパティの現在の値を格納することはできません。</span><span class="sxs-lookup"><span data-stu-id="bc062-127">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="bc062-128">この値は、プロパティの外部に格納する必要があります。それをいずれかのプロパティ プロシージャの内部に格納した場合、他のプロパティ プロシージャからアクセスできなくなるためです。</span><span class="sxs-lookup"><span data-stu-id="bc062-128">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="bc062-129">通常の方法は、プロパティと同じレベルで宣言された [Private](../modifiers/private.md) 変数に値を格納することです。</span><span class="sxs-lookup"><span data-stu-id="bc062-129">The usual approach is to store the value in a [Private](../modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="bc062-130">`Get` プロシージャは、適用先のプロパティの内部で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc062-130">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="bc062-131">`Get` ステートメントで `accessmodifier` を使用しない限り、`Get` プロシージャは既定で、それを含んでいるプロパティのアクセス レベルに設定されます。</span><span class="sxs-lookup"><span data-stu-id="bc062-131">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="bc062-132">ルール</span><span class="sxs-lookup"><span data-stu-id="bc062-132">Rules</span></span>  
  
- <span data-ttu-id="bc062-133">**混合アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="bc062-133">**Mixed Access Levels.**</span></span> <span data-ttu-id="bc062-134">読み取り/書き込みプロパティを定義する場合は、必要に応じて、`Get` または `Set` のいずれかのプロシージャに対して異なるアクセス レベルを指定できますが、両方に対して指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="bc062-134">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="bc062-135">この場合、プロシージャのアクセス レベルは、プロパティのアクセス レベルよりも制限されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc062-135">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="bc062-136">たとえば、プロパティが `Friend` として宣言されている場合は、`Get` プロシージャを、`Public` ではなく `Private` として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="bc062-136">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="bc062-137">`ReadOnly` プロパティを定義する場合、`Get` プロシージャはプロパティ全体を表します。</span><span class="sxs-lookup"><span data-stu-id="bc062-137">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="bc062-138">`Get` に対して異なるアクセス レベルを宣言することはできません。それによって、プロパティに 2 つのアクセス レベルが設定されるためです。</span><span class="sxs-lookup"><span data-stu-id="bc062-138">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
- <span data-ttu-id="bc062-139">**戻り値の型。**</span><span class="sxs-lookup"><span data-stu-id="bc062-139">**Return Type.**</span></span> <span data-ttu-id="bc062-140">[Property ステートメント](property-statement.md)では、それによって返される値のデータ型を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="bc062-140">The [Property Statement](property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="bc062-141">`Get` プロシージャでは、そのデータ型が自動的に返されます。</span><span class="sxs-lookup"><span data-stu-id="bc062-141">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="bc062-142">任意のデータ型や、列挙、構造体、クラス、またはインターフェイスの名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bc062-142">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="bc062-143">`Property` ステートメントで `returntype` を指定していない場合、プロシージャによって `Object` が返されます。</span><span class="sxs-lookup"><span data-stu-id="bc062-143">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="bc062-144">動作</span><span class="sxs-lookup"><span data-stu-id="bc062-144">Behavior</span></span>  
  
- <span data-ttu-id="bc062-145">**プロシージャからの復帰。**</span><span class="sxs-lookup"><span data-stu-id="bc062-145">**Returning from a Procedure.**</span></span> <span data-ttu-id="bc062-146">`Get` プロシージャから呼び出し元のコードに戻ると、そのプロパティ値を要求したステートメント内で実行が続行されます。</span><span class="sxs-lookup"><span data-stu-id="bc062-146">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="bc062-147">`Get` プロパティ プロシージャでは、[Return ステートメント](return-statement.md)を使用するか、プロパティ名に戻り値を代入することによって、値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="bc062-147">`Get` property procedures can return a value using either the [Return Statement](return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="bc062-148">詳細については、「[Function ステートメント](function-statement.md)」の "戻り値" に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc062-148">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="bc062-149">`Exit Property` および `Return` ステートメントでは、プロパティ プロシージャがすぐに終了します。</span><span class="sxs-lookup"><span data-stu-id="bc062-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="bc062-150">任意の数の `Exit Property` および `Return` ステートメントをプロシージャ内の任意の場所に記述でき、`Exit Property` ステートメントと `Return` ステートメントを混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="bc062-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
- <span data-ttu-id="bc062-151">**戻り値。**</span><span class="sxs-lookup"><span data-stu-id="bc062-151">**Return Value.**</span></span> <span data-ttu-id="bc062-152">`Get` プロシージャから値を返すには、プロパティ名に値を代入するか、[Return ステートメント](return-statement.md)に値を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="bc062-152">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](return-statement.md).</span></span> <span data-ttu-id="bc062-153">`Return` ステートメントでは、`Get` プロシージャに戻り値を代入すると同時に、プロシージャが終了します。</span><span class="sxs-lookup"><span data-stu-id="bc062-153">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="bc062-154">プロパティ名に値を代入せずに、`Exit Property` を使用すると、`Get` プロシージャからは、プロパティのデータ型の既定値が返されます。</span><span class="sxs-lookup"><span data-stu-id="bc062-154">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="bc062-155">詳細については、「[Function ステートメント](function-statement.md)」の "戻り値" に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc062-155">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="bc062-156">次の例では、読み取り専用プロパティ `quoteForTheDay` で、プライベート変数 `quoteValue` に保持されている値を返すことができる 2 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bc062-156">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="bc062-157">例</span><span class="sxs-lookup"><span data-stu-id="bc062-157">Example</span></span>  

 <span data-ttu-id="bc062-158">次の例では、`Get` ステートメントを使用してプロパティの値を返しています。</span><span class="sxs-lookup"><span data-stu-id="bc062-158">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="bc062-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc062-159">See also</span></span>

- [<span data-ttu-id="bc062-160">Set ステートメント</span><span class="sxs-lookup"><span data-stu-id="bc062-160">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="bc062-161">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="bc062-161">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="bc062-162">Exit ステートメント</span><span class="sxs-lookup"><span data-stu-id="bc062-162">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="bc062-163">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="bc062-163">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="bc062-164">チュートリアル: クラスの定義</span><span class="sxs-lookup"><span data-stu-id="bc062-164">Walkthrough: Defining Classes</span></span>](../../programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
