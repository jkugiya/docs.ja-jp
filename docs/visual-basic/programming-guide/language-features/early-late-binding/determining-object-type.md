---
description: '詳細情報: オブジェクトの型の決定 (Visual Basic)'
title: オブジェクトの型の決定
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: 0cf64b6dde74b98edaf055537533cb648ed3381a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434408"
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="7f064-103">オブジェクトの型の決定 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f064-103">Determining Object Type (Visual Basic)</span></span>

<span data-ttu-id="7f064-104">汎用オブジェクト変数 (`Object` として宣言する変数) では、あらゆるクラスのオブジェクトを保持できます。</span><span class="sxs-lookup"><span data-stu-id="7f064-104">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="7f064-105">`Object` 型の変数を使用する場合、オブジェクトのクラスによって異なるアクションを実行しなければならないことがあります。たとえば、オブジェクトによっては、特定のプロパティやメソッドがサポートされません。</span><span class="sxs-lookup"><span data-stu-id="7f064-105">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="7f064-106">Visual Basic では、`TypeName` 関数と `TypeOf...Is` 演算子という 2 つの方法によって、オブジェクト変数に格納されているオブジェクトの型を特定できます。</span><span class="sxs-lookup"><span data-stu-id="7f064-106">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="7f064-107">TypeName と TypeOf…Is</span><span class="sxs-lookup"><span data-stu-id="7f064-107">TypeName and TypeOf…Is</span></span>  

 <span data-ttu-id="7f064-108">`TypeName` 関数の戻り値は文字列であり、次のコードで示すように、オブジェクトのクラス名を格納または表示する必要がある場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="7f064-108">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 <span data-ttu-id="7f064-109">`TypeOf...Is` 演算子は、`TypeName` を使用した同等の文字列比較よりもはるかに高速であるため、オブジェクトの型のテストに最も適しています。</span><span class="sxs-lookup"><span data-stu-id="7f064-109">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="7f064-110">次のコードでは、`If...Then...Else` ステートメント内で `TypeOf...Is` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="7f064-110">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 <span data-ttu-id="7f064-111">ここで注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="7f064-111">A word of caution is due here.</span></span> <span data-ttu-id="7f064-112">オブジェクトが特定の型であるか、または特定の型から派生している場合、`TypeOf...Is` 演算子は `True` を返します。</span><span class="sxs-lookup"><span data-stu-id="7f064-112">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="7f064-113">Visual Basic で行うほとんどすべての操作にはオブジェクトが関係しています。これには、文字列や整数など、オブジェクトとは通常見なされない要素も含まれます。</span><span class="sxs-lookup"><span data-stu-id="7f064-113">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="7f064-114">こうしたオブジェクトは、<xref:System.Object> から派生し、そのメソッドを継承しています。</span><span class="sxs-lookup"><span data-stu-id="7f064-114">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="7f064-115">`TypeOf...Is` 演算子に `Integer` を渡して、`Object` かどうかを評価した場合、`True` が返されます。</span><span class="sxs-lookup"><span data-stu-id="7f064-115">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="7f064-116">次の例では、パラメーター `InParam` は `Object` であり、かつ `Integer` でもあると返されます。</span><span class="sxs-lookup"><span data-stu-id="7f064-116">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 <span data-ttu-id="7f064-117">次の例では、`TypeOf...Is` と `TypeName` の両方を使用して、`Ctrl` 引数から渡されたオブジェクトの型を特定します。</span><span class="sxs-lookup"><span data-stu-id="7f064-117">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="7f064-118">`TestObject` プロシージャにより、3 種類のコントロールを使用して `ShowType` を呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="7f064-118">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="7f064-119">例を実行するには</span><span class="sxs-lookup"><span data-stu-id="7f064-119">To run the example</span></span>  
  
1. <span data-ttu-id="7f064-120">新しい Windows アプリケーション プロジェクトを作成して、フォームに <xref:System.Windows.Forms.Button> コントロール、<xref:System.Windows.Forms.CheckBox> コントロール、および <xref:System.Windows.Forms.RadioButton> コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="7f064-120">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2. <span data-ttu-id="7f064-121">フォームのボタンで `TestObject` プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7f064-121">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3. <span data-ttu-id="7f064-122">次のコードをフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="7f064-122">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a><span data-ttu-id="7f064-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f064-123">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [<span data-ttu-id="7f064-124">文字列名によるプロパティまたはメソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="7f064-124">Calling a Property or Method Using a String Name</span></span>](calling-a-property-or-method-using-a-string-name.md)
- [<span data-ttu-id="7f064-125">Object 型</span><span class="sxs-lookup"><span data-stu-id="7f064-125">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="7f064-126">If...Then...Else ステートメント</span><span class="sxs-lookup"><span data-stu-id="7f064-126">If...Then...Else Statement</span></span>](../../../language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="7f064-127">String データ型</span><span class="sxs-lookup"><span data-stu-id="7f064-127">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="7f064-128">Integer データ型</span><span class="sxs-lookup"><span data-stu-id="7f064-128">Integer Data Type</span></span>](../../../language-reference/data-types/integer-data-type.md)
