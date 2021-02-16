---
description: '詳細情報: オーバーロードされたプロパティとメソッド (Visual Basic)'
title: オーバーロードされたプロパティとメソッド
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: fb46876d346ad5f391241aee0b07175df290e656
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438776"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="9309f-103">オーバーロードされたプロパティとメソッド (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9309f-103">Overloaded properties and methods (Visual Basic)</span></span>

<span data-ttu-id="9309f-104">オーバーロードとは、名前が同じで引数の型が異なる複数のプロシージャ、インスタンスのコンストラクター、またはプロパティをクラスに作成することです。</span><span class="sxs-lookup"><span data-stu-id="9309f-104">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>

## <a name="overloading-usage"></a><span data-ttu-id="9309f-105">オーバーロードの使用法</span><span class="sxs-lookup"><span data-stu-id="9309f-105">Overloading usage</span></span>

<span data-ttu-id="9309f-106">オーバーロードは、さまざまなデータ型を操作するプロシージャに同じ名前を使用するようにオブジェクト モデルで指示された場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="9309f-106">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="9309f-107">たとえば、各種のデータ型を表示できるクラスには、次のような `Display` プロシージャがある場合があります。</span><span class="sxs-lookup"><span data-stu-id="9309f-107">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

<span data-ttu-id="9309f-108">オーバーロードを使用しない場合は、実行する処理は同じでも、次に示すようにプロシージャごとに個別の名前を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9309f-108">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

<span data-ttu-id="9309f-109">オーバーロードを使用すると、使用可能なデータ型を選択できるため、プロパティやメソッドを簡単に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9309f-109">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="9309f-110">たとえば、前に説明したオーバーロードされた `Display` メソッドは、次のいずれかのコード行を使用して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="9309f-110">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

<span data-ttu-id="9309f-111">実行時に、Visual Basic は、指定されたパラメーターのデータ型に基づいて正しいプロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9309f-111">At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="9309f-112">オーバーロードのルール</span><span class="sxs-lookup"><span data-stu-id="9309f-112">Overloading rules</span></span>

 <span data-ttu-id="9309f-113">オーバーロードされたメンバーをクラスに作成するには、同じ名前を持つ 2 つ以上のプロパティまたはメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="9309f-113">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="9309f-114">オーバーロードされた派生メンバーを除き、オーバーロードされた各メンバーは異なるパラメーター リストを持つ必要があります。また、プロパティまたはプロシージャをオーバーロードするときに、区別するための特性として次の項目を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="9309f-114">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>

- <span data-ttu-id="9309f-115">メンバーまたはメンバーのパラメーターに適用される、`ByVal` や `ByRef` などの修飾子。</span><span class="sxs-lookup"><span data-stu-id="9309f-115">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>

- <span data-ttu-id="9309f-116">パラメーターの名前</span><span class="sxs-lookup"><span data-stu-id="9309f-116">Names of parameters</span></span>

- <span data-ttu-id="9309f-117">プロシージャの戻り値の型</span><span class="sxs-lookup"><span data-stu-id="9309f-117">Return types of procedures</span></span>

<span data-ttu-id="9309f-118">`Overloads` キーワードはオーバーロード時には省略可能ですが、オーバーロードされたメンバーが `Overloads` キーワードを使用している場合は、同じ名前の他のすべてのオーバーロードされたメンバーにもこのキーワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9309f-118">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>

<span data-ttu-id="9309f-119">派生クラスでは、継承されたメンバーを同じパラメーターとパラメーターの型を持つメンバーでオーバーロードすることができます。これは、*名前とシグネチャによるシャドウ* と呼ばれる処理です。</span><span class="sxs-lookup"><span data-stu-id="9309f-119">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="9309f-120">名前とシグネチャによるシャドウを行うときに `Overloads` キーワードを使用すると、基底クラスの実装ではなく、派生クラスのメンバーの実装が使用され、そのメンバーの他のすべてのオーバーロードが派生クラスのインスタンスで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9309f-120">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>

<span data-ttu-id="9309f-121">同じパラメーターとパラメーターの型を持つメンバーで継承されたメンバーをオーバーロードするときに `Overloads` キーワードを省略した場合、そのオーバーロードは *名前によるシャドウ* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="9309f-121">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="9309f-122">名前によるシャドウでは、メンバーの継承された実装が置き換えられます。これにより、派生クラスとその子孫のインスタンスで他のすべてのオーバーロードが使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="9309f-122">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>

<span data-ttu-id="9309f-123">`Overloads` と `Shadows` の両方の修飾子を同じプロパティまたはメソッドで使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="9309f-123">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>

### <a name="example"></a><span data-ttu-id="9309f-124">例</span><span class="sxs-lookup"><span data-stu-id="9309f-124">Example</span></span>

<span data-ttu-id="9309f-125">次の例では、`String` または `Decimal` で表現されたドル額を受け取り、売上税を含む文字列を返すオーバーロードされたメソッドを作成しています。</span><span class="sxs-lookup"><span data-stu-id="9309f-125">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="9309f-126">この例を使用して、オーバーロードされたメソッドを作成するには</span><span class="sxs-lookup"><span data-stu-id="9309f-126">To use this example to create an overloaded method</span></span>

1. <span data-ttu-id="9309f-127">新しいプロジェクトを開いて、`TaxClass` という名前のクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="9309f-127">Open a new project and add a class named `TaxClass`.</span></span>

2. <span data-ttu-id="9309f-128">`TaxClass` クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="9309f-128">Add the following code to the `TaxClass` class.</span></span>

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. <span data-ttu-id="9309f-129">次のプロシージャをフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="9309f-129">Add the following procedure to your form.</span></span>

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. <span data-ttu-id="9309f-130">フォームにボタンを追加し、ボタンの `Button1_Click` イベントから `ShowTax` プロシージャが呼び出されるようにします。</span><span class="sxs-lookup"><span data-stu-id="9309f-130">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>

5. <span data-ttu-id="9309f-131">プロジェクトを実行し、フォームのボタンをクリックして、オーバーロードされた `ShowTax` プロシージャをテストします。</span><span class="sxs-lookup"><span data-stu-id="9309f-131">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>

<span data-ttu-id="9309f-132">実行時に、コンパイラは、使用されているパラメーターに一致するオーバーロードされた適切な関数を選択します。</span><span class="sxs-lookup"><span data-stu-id="9309f-132">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="9309f-133">このボタンをクリックすると、最初に、文字列である `Price` パラメーターを使用して、オーバーロードされたメソッドが呼び出され、"Price is a String.</span><span class="sxs-lookup"><span data-stu-id="9309f-133">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="9309f-134">Tax is $5.12" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9309f-134">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="9309f-135">2 回目は、`Decimal` 値を使用して `TaxAmount` が呼び出され、"Price is a Decimal.</span><span class="sxs-lookup"><span data-stu-id="9309f-135">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="9309f-136">Tax is $5.12" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9309f-136">Tax is $5.12" is displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="9309f-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="9309f-137">See also</span></span>

- [<span data-ttu-id="9309f-138">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="9309f-138">Objects and Classes</span></span>](index.md)
- [<span data-ttu-id="9309f-139">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="9309f-139">Shadowing in Visual Basic</span></span>](../declared-elements/shadowing.md)
- [<span data-ttu-id="9309f-140">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="9309f-140">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="9309f-141">継承の基本</span><span class="sxs-lookup"><span data-stu-id="9309f-141">Inheritance Basics</span></span>](inheritance-basics.md)
- [<span data-ttu-id="9309f-142">Shadows</span><span class="sxs-lookup"><span data-stu-id="9309f-142">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="9309f-143">ByVal</span><span class="sxs-lookup"><span data-stu-id="9309f-143">ByVal</span></span>](../../../language-reference/modifiers/byval.md)
- [<span data-ttu-id="9309f-144">ByRef</span><span class="sxs-lookup"><span data-stu-id="9309f-144">ByRef</span></span>](../../../language-reference/modifiers/byref.md)
- [<span data-ttu-id="9309f-145">Overloads</span><span class="sxs-lookup"><span data-stu-id="9309f-145">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="9309f-146">Shadows</span><span class="sxs-lookup"><span data-stu-id="9309f-146">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
