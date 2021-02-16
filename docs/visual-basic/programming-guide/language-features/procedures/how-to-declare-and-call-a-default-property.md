---
description: '詳細情報: 方法:Visual Basic で既定のプロパティを宣言して呼び出す'
title: '方法: 既定のプロパティを宣言して呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: 2a0e82fe89bb89613996f613930ace1aa6e41b7f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472450"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="598b3-103">方法: Visual Basic で既定のプロパティを宣言して呼び出す</span><span class="sxs-lookup"><span data-stu-id="598b3-103">How to: Declare and Call a Default Property in Visual Basic</span></span>

<span data-ttu-id="598b3-104">"*既定のプロパティ*" とは、コードで指定しなくてもアクセスできるクラスまたは構造体のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="598b3-104">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="598b3-105">呼び出し元のコードでクラスまたは構造体の名前を指定し、プロパティ名を指定していないときに、コンテキストでプロパティへのアクセスが許可されている場合、Visual Basic はアクセスをそのクラスまたは構造体の既定のプロパティ (存在する場合) に解決します。</span><span class="sxs-lookup"><span data-stu-id="598b3-105">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="598b3-106">クラスまたは構造体は、最大 1 つの既定のプロパティを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="598b3-106">A class or structure can have at most one default property.</span></span> <span data-ttu-id="598b3-107">ただし、既定のプロパティをオーバーロードし、複数のバージョンを用意することができます。</span><span class="sxs-lookup"><span data-stu-id="598b3-107">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="598b3-108">詳細については、「[Default](../../../language-reference/modifiers/default.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="598b3-108">For more information, see [Default](../../../language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="598b3-109">既定のプロパティを宣言するには</span><span class="sxs-lookup"><span data-stu-id="598b3-109">To declare a default property</span></span>  
  
1. <span data-ttu-id="598b3-110">通常の方法でプロパティを宣言します。</span><span class="sxs-lookup"><span data-stu-id="598b3-110">Declare the property in the normal way.</span></span> <span data-ttu-id="598b3-111">`Shared` または `Private` キーワードは指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="598b3-111">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2. <span data-ttu-id="598b3-112">プロパティ宣言に `Default` キーワードを含めます。</span><span class="sxs-lookup"><span data-stu-id="598b3-112">Include the `Default` keyword in the property declaration.</span></span>  
  
3. <span data-ttu-id="598b3-113">プロパティに少なくとも 1 つのパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="598b3-113">Specify at least one parameter for the property.</span></span> <span data-ttu-id="598b3-114">1 つ以上の引数を受け取らない既定のプロパティを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="598b3-114">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="598b3-115">既定のプロパティを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="598b3-115">To call a default property</span></span>  
  
1. <span data-ttu-id="598b3-116">包含クラスまたは構造体の型の変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="598b3-116">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. <span data-ttu-id="598b3-117">通常はプロパティ名を含める式で変数名のみを使用します。</span><span class="sxs-lookup"><span data-stu-id="598b3-117">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="598b3-118">変数名の後に、かっこで囲んだ引数リストを指定します。</span><span class="sxs-lookup"><span data-stu-id="598b3-118">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="598b3-119">既定のプロパティは、少なくとも 1 つの引数を受け取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="598b3-119">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. <span data-ttu-id="598b3-120">既定のプロパティ値を取得するには、式内または代入ステートメントの等号 (`=`) の後に、変数名と引数リストを使用します。</span><span class="sxs-lookup"><span data-stu-id="598b3-120">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. <span data-ttu-id="598b3-121">既定のプロパティ値を設定するには、代入ステートメントの左辺に変数名と引数リストを使用します。</span><span class="sxs-lookup"><span data-stu-id="598b3-121">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. <span data-ttu-id="598b3-122">他のプロパティにアクセスする場合と同様に、既定のプロパティ名は常に変数名と共に指定できます。</span><span class="sxs-lookup"><span data-stu-id="598b3-122">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="598b3-123">例</span><span class="sxs-lookup"><span data-stu-id="598b3-123">Example</span></span>  

 <span data-ttu-id="598b3-124">次の例では、クラスの既定のプロパティを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="598b3-124">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="598b3-125">例</span><span class="sxs-lookup"><span data-stu-id="598b3-125">Example</span></span>  

 <span data-ttu-id="598b3-126">次の例は、`class1` クラスの既定のプロパティ `myProperty` を呼び出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="598b3-126">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="598b3-127">3 つの代入ステートメントで `myProperty` に値を格納し、<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 呼び出しで値を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="598b3-127">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 <span data-ttu-id="598b3-128">既定のプロパティの最も一般的な用途は、さまざまなコレクション クラスの <xref:Microsoft.VisualBasic.Collection.Item%2A> プロパティです。</span><span class="sxs-lookup"><span data-stu-id="598b3-128">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="598b3-129">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="598b3-129">Robust Programming</span></span>  

 <span data-ttu-id="598b3-130">既定のプロパティを使用すると、ソース コード文字が少し少なくなる可能性がありますが、コードが読みにくくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="598b3-130">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="598b3-131">呼び出し元のコードがクラスまたは構造体をよく理解していない場合は、クラスまたは構造体の名前を参照するときに、その参照がクラスまたは構造体自体、または既定のプロパティにアクセスするかどうかがわかりません。</span><span class="sxs-lookup"><span data-stu-id="598b3-131">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="598b3-132">これにより、コンパイラ エラーや実行時の微妙なロジック エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="598b3-132">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="598b3-133">常に [Option Strict ステートメント](../../../language-reference/statements/option-strict-statement.md)を使用してコンパイラの型チェックを `On` に設定することにより、既定のプロパティ エラーが発生する可能性を多少減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="598b3-133">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="598b3-134">定義済みのクラスまたは構造体をコード内で使用する予定の場合は、既定のプロパティがあるかどうかと、ある場合はその名前を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="598b3-134">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="598b3-135">これらの欠点があるため、既定のプロパティを定義しないことを検討してください。</span><span class="sxs-lookup"><span data-stu-id="598b3-135">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="598b3-136">コードを読みやすくするためには、既定のプロパティを含め、常にすべてのプロパティを明示的に参照することも検討してください。</span><span class="sxs-lookup"><span data-stu-id="598b3-136">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="598b3-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="598b3-137">See also</span></span>

- [<span data-ttu-id="598b3-138">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="598b3-138">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="598b3-139">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="598b3-139">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="598b3-140">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="598b3-140">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="598b3-141">default</span><span class="sxs-lookup"><span data-stu-id="598b3-141">Default</span></span>](../../../language-reference/modifiers/default.md)
- [<span data-ttu-id="598b3-142">Visual Basic のプロパティと変数の違い</span><span class="sxs-lookup"><span data-stu-id="598b3-142">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="598b3-143">方法: プロパティを作成する</span><span class="sxs-lookup"><span data-stu-id="598b3-143">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="598b3-144">方法: 複数のアクセス レベルを持つプロパティを宣言する</span><span class="sxs-lookup"><span data-stu-id="598b3-144">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="598b3-145">方法: プロパティ プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="598b3-145">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="598b3-146">方法: プロパティに値を格納する</span><span class="sxs-lookup"><span data-stu-id="598b3-146">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="598b3-147">方法: プロパティから値を取得する</span><span class="sxs-lookup"><span data-stu-id="598b3-147">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
