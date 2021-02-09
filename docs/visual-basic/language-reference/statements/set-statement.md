---
description: '詳細情報: Set ステートメント (Visual Basic)'
title: Set ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: 5ee27b35a4639bc20d5b6634de8332c6ede9bf12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741121"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="2d0b6-103">Set ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d0b6-103">Set Statement (Visual Basic)</span></span>

<span data-ttu-id="2d0b6-104">値をプロパティに割り当てるのに使用する `Set` プロパティ プロシージャを宣言します。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-104">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d0b6-105">構文</span><span class="sxs-lookup"><span data-stu-id="2d0b6-105">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="2d0b6-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="2d0b6-106">Parts</span></span>  

 `attributelist`  
 <span data-ttu-id="2d0b6-107">任意。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-107">Optional.</span></span> <span data-ttu-id="2d0b6-108">「[属性リスト](attribute-list.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-108">See [Attribute List](attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="2d0b6-109">このプロパティの `Get` および `Set` ステートメントのいずれかで、省略可能です。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-109">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="2d0b6-110">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-110">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="2d0b6-111">Protected</span><span class="sxs-lookup"><span data-stu-id="2d0b6-111">Protected</span></span>](../modifiers/protected.md)  
  
- [<span data-ttu-id="2d0b6-112">Friend</span><span class="sxs-lookup"><span data-stu-id="2d0b6-112">Friend</span></span>](../modifiers/friend.md)  
  
- [<span data-ttu-id="2d0b6-113">Private</span><span class="sxs-lookup"><span data-stu-id="2d0b6-113">Private</span></span>](../modifiers/private.md)  
  
- `Protected Friend`  
  
 <span data-ttu-id="2d0b6-114">「 [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-114">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="2d0b6-115">必須です。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-115">Required.</span></span> <span data-ttu-id="2d0b6-116">プロパティの新しい値を含むパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-116">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="2d0b6-117">`Option Strict` が `On` の場合は必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-117">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="2d0b6-118">`value` パラメーターのデータ型。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-118">Data type of the `value` parameter.</span></span> <span data-ttu-id="2d0b6-119">指定するデータ型は、この `Set` ステートメントが宣言されているプロパティのデータ型と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-119">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="2d0b6-120">任意。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-120">Optional.</span></span> <span data-ttu-id="2d0b6-121">`Set` プロパティ プロシージャが呼び出されたときに実行される 1 つ以上のステートメント。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-121">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="2d0b6-122">必須です。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-122">Required.</span></span> <span data-ttu-id="2d0b6-123">`Set` プロパティ プロシージャの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-123">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d0b6-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="2d0b6-124">Remarks</span></span>  

 <span data-ttu-id="2d0b6-125">プロパティが `ReadOnly` とマークされている場合を除き、すべてのプロパティには `Set` プロパティ プロシージャが必要です。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-125">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="2d0b6-126">`Set` プロシージャは、プロパティの値を設定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-126">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="2d0b6-127">Visual Basic は、プロパティに格納される値が代入ステートメントによって提供されるときに、プロパティの `Set` プロシージャを自動的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-127">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="2d0b6-128">Visual Basic は、プロパティの割り当て時に `Set` プロシージャにパラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-128">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="2d0b6-129">`Set` のパラメーターを指定しない場合、統合開発環境 (IDE) では `value` という名前の暗黙的なパラメーターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-129">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="2d0b6-130">このパラメーターは、プロパティに割り当てられる値を保持します。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-130">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="2d0b6-131">通常はこの値をプライベート ローカル変数に格納し、これは `Get` プロシージャが呼び出されるたびに返されます。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-131">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="2d0b6-132">プロパティ宣言の本体には、[Property ステートメント](property-statement.md)と `End Property` ステートメントの間に、プロパティの `Get` と `Set` のプロシージャのみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-132">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="2d0b6-133">これらのプロシージャ以外のものを格納することはできません。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-133">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="2d0b6-134">特に、プロパティの現在の値を格納することはできません。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-134">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="2d0b6-135">この値は、プロパティの外部に格納する必要があります。それをいずれかのプロパティ プロシージャの内部に格納した場合、他のプロパティ プロシージャからアクセスできなくなるためです。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-135">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="2d0b6-136">通常の方法は、プロパティと同じレベルで宣言された [Private](../modifiers/private.md) 変数に値を格納することです。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-136">The usual approach is to store the value in a [Private](../modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="2d0b6-137">`Set` プロシージャは、適用先のプロパティの内部で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-137">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="2d0b6-138">`Set` ステートメントで `accessmodifier` を使用しない限り、`Set` プロシージャは既定で、それを含んでいるプロパティのアクセス レベルに設定されます。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-138">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2d0b6-139">ルール</span><span class="sxs-lookup"><span data-stu-id="2d0b6-139">Rules</span></span>  
  
- <span data-ttu-id="2d0b6-140">**混合アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="2d0b6-140">**Mixed Access Levels.**</span></span> <span data-ttu-id="2d0b6-141">読み取り/書き込みプロパティを定義する場合は、必要に応じて、`Get` または `Set` のいずれかのプロシージャに対して異なるアクセス レベルを指定できますが、両方に対して指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-141">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="2d0b6-142">この場合、プロシージャのアクセス レベルは、プロパティのアクセス レベルよりも制限されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-142">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="2d0b6-143">たとえば、プロパティが `Friend` として宣言されている場合は、`Set` プロシージャを、`Public` ではなく `Private` として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-143">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="2d0b6-144">`WriteOnly` プロパティを定義する場合、`Set` プロシージャはプロパティ全体を表します。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-144">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="2d0b6-145">`Set` に対して異なるアクセス レベルを宣言することはできません。それによって、プロパティに 2 つのアクセス レベルが設定されるためです。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-145">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="2d0b6-146">動作</span><span class="sxs-lookup"><span data-stu-id="2d0b6-146">Behavior</span></span>  
  
- <span data-ttu-id="2d0b6-147">**プロパティ プロシージャからの復帰。**</span><span class="sxs-lookup"><span data-stu-id="2d0b6-147">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="2d0b6-148">`Set` プロシージャから呼び出し元のコードに返されると、実行は、格納される値を指定したステートメントの後のステートメントから続行されます。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-148">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="2d0b6-149">`Set` プロパティ プロシージャは、[Return ステートメント](return-statement.md)または [Exit ステートメント](exit-statement.md)のいずれかを使用して返すことができます。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-149">`Set` property procedures can return using either the [Return Statement](return-statement.md) or the [Exit Statement](exit-statement.md).</span></span>  
  
     <span data-ttu-id="2d0b6-150">`Exit Property` および `Return` ステートメントでは、プロパティ プロシージャがすぐに終了します。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-150">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="2d0b6-151">任意の数の `Exit Property` および `Return` ステートメントをプロシージャ内の任意の場所に記述でき、`Exit Property` ステートメントと `Return` ステートメントを混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-151">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d0b6-152">例</span><span class="sxs-lookup"><span data-stu-id="2d0b6-152">Example</span></span>  

 <span data-ttu-id="2d0b6-153">次の例では、`Set` ステートメントを使用してプロパティの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="2d0b6-153">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="2d0b6-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d0b6-154">See also</span></span>

- [<span data-ttu-id="2d0b6-155">Get ステートメント</span><span class="sxs-lookup"><span data-stu-id="2d0b6-155">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="2d0b6-156">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="2d0b6-156">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="2d0b6-157">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="2d0b6-157">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="2d0b6-158">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2d0b6-158">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
