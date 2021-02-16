---
description: '詳細情報: 方法:プロパティ プロシージャを呼び出す (Visual Basic)'
title: '方法: プロパティ プロシージャを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 541768cb6381aa3d2b1bf75267c5b34a82a3d2ab
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466758"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="2cbc7-103">方法: プロパティ プロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cbc7-103">How to: Call a Property Procedure (Visual Basic)</span></span>

<span data-ttu-id="2cbc7-104">プロパティ プロシージャを呼び出すには、プロパティに値を格納するか、その値を取得します。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-104">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="2cbc7-105">プロパティには、変数にアクセスするのと同じ方法でアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-105">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="2cbc7-106">プロパティの `Set` プロシージャによって値が格納され、その `Get` プロシージャによって値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-106">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="2cbc7-107">ただし、これらのプロシージャを名前で明示的に呼び出すことはしません。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-107">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="2cbc7-108">変数の値を格納または取得する場合と同様に、代入ステートメントまたは式でもプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-108">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> <span data-ttu-id="2cbc7-109">Visual Basic によってプロパティのプロシージャが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-109">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="2cbc7-110">プロパティの Get プロシージャを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="2cbc7-110">To call a property's Get procedure</span></span>  
  
1. <span data-ttu-id="2cbc7-111">式内のプロパティ名は、変数名を使用する場合と同じように使用します。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-111">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="2cbc7-112">変数または定数を使用できる場所であればどこでもプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-112">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="2cbc7-113">\- または -</span><span class="sxs-lookup"><span data-stu-id="2cbc7-113">-or-</span></span>  
  
     <span data-ttu-id="2cbc7-114">代入ステートメント内で等号 (`=`) の後にプロパティ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-114">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="2cbc7-115">次の例では、<xref:Microsoft.VisualBasic.DateAndTime.Now%2A> プロパティの値を読み取ることで、その `Get` プロシージャを暗黙的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-115">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="2cbc7-116">プロパティが引数を受け取る場合は、プロパティ名の後にかっこで囲んだ引数リストを指定します。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-116">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="2cbc7-117">引数がない場合は、必要に応じてかっこを省略できます。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-117">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="2cbc7-118">引数リストの引数をコンマで区切ってかっこ内に配置します。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-118">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="2cbc7-119">プロパティで定義されている対応するパラメーターと同じ順序で引数を指定してください。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-119">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="2cbc7-120">プロパティの値は変数または定数の場合と同様に式に含められるか、または代入ステートメントの左辺にある変数またはプロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-120">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="2cbc7-121">プロパティの Set プロシージャを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="2cbc7-121">To call a property's Set procedure</span></span>  
  
1. <span data-ttu-id="2cbc7-122">代入ステートメントの左辺にプロパティ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-122">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="2cbc7-123">次の例では、<xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> プロパティの値を設定して、`Set` プロシージャを暗黙的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-123">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="2cbc7-124">プロパティが引数を受け取る場合は、プロパティ名の後にかっこで囲んだ引数リストを指定します。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-124">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="2cbc7-125">引数がない場合は、必要に応じてかっこを省略できます。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-125">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="2cbc7-126">引数リストの引数をコンマで区切ってかっこ内に配置します。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-126">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="2cbc7-127">プロパティで定義されている対応するパラメーターと同じ順序で引数を指定してください。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-127">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="2cbc7-128">代入ステートメントの右辺で生成された値がプロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="2cbc7-128">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cbc7-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="2cbc7-129">See also</span></span>

- [<span data-ttu-id="2cbc7-130">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2cbc7-130">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="2cbc7-131">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="2cbc7-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="2cbc7-132">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="2cbc7-132">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="2cbc7-133">Visual Basic のプロパティと変数の違い</span><span class="sxs-lookup"><span data-stu-id="2cbc7-133">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="2cbc7-134">方法: プロパティを作成する</span><span class="sxs-lookup"><span data-stu-id="2cbc7-134">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="2cbc7-135">方法: 複数のアクセス レベルを持つプロパティを宣言する</span><span class="sxs-lookup"><span data-stu-id="2cbc7-135">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="2cbc7-136">方法: 既定のプロパティを宣言して呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cbc7-136">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="2cbc7-137">方法: プロパティに値を格納する</span><span class="sxs-lookup"><span data-stu-id="2cbc7-137">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="2cbc7-138">方法: プロパティから値を取得する</span><span class="sxs-lookup"><span data-stu-id="2cbc7-138">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
- [<span data-ttu-id="2cbc7-139">Get ステートメント</span><span class="sxs-lookup"><span data-stu-id="2cbc7-139">Get Statement</span></span>](../../../language-reference/statements/get-statement.md)
- [<span data-ttu-id="2cbc7-140">Set ステートメント</span><span class="sxs-lookup"><span data-stu-id="2cbc7-140">Set Statement</span></span>](../../../language-reference/statements/set-statement.md)
