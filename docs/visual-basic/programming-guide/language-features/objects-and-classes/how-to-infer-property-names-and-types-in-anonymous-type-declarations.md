---
description: '詳細情報: 方法:匿名型の宣言におけるプロパティ名と型を推論する (Visual Basic)'
title: '方法: 匿名型の宣言におけるプロパティ名と型を推論する'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: e4bff8cd8dd879b97618a3bc69e1eaf1c7c269b7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483899"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="c815c-103">方法: 匿名型の宣言におけるプロパティ名と型を推論する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c815c-103">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>

<span data-ttu-id="c815c-104">匿名型には、プロパティのデータ型を直接指定する機構はありません。</span><span class="sxs-lookup"><span data-stu-id="c815c-104">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="c815c-105">すべてのプロパティの型は、推論されます。</span><span class="sxs-lookup"><span data-stu-id="c815c-105">Types of all properties are inferred.</span></span> <span data-ttu-id="c815c-106">次の例では、 `Name` と `Price` の型は、それらを初期化するために使われる値から、直接推論されます。</span><span class="sxs-lookup"><span data-stu-id="c815c-106">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>

[!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]

<span data-ttu-id="c815c-107">匿名型は、プロパティの名前と型を、他のソースから推論することもできます。</span><span class="sxs-lookup"><span data-stu-id="c815c-107">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="c815c-108">この後のセクションで、推論が可能な状況の一覧と、推論が行われない状況の例を示します。</span><span class="sxs-lookup"><span data-stu-id="c815c-108">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>

## <a name="successful-inference"></a><span data-ttu-id="c815c-109">正常な推論</span><span class="sxs-lookup"><span data-stu-id="c815c-109">Successful Inference</span></span>

#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="c815c-110">匿名型は、プロパティの名前と型を、次のソースから推論できます:</span><span class="sxs-lookup"><span data-stu-id="c815c-110">Anonymous types can infer property names and types from the following sources:</span></span>

- <span data-ttu-id="c815c-111">変数名から。</span><span class="sxs-lookup"><span data-stu-id="c815c-111">From variable names.</span></span> <span data-ttu-id="c815c-112">匿名型 `anonProduct` には、 `productName` と `productPrice`という 2 つのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="c815c-112">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="c815c-113">それらのプロパティのデータ型は、それぞれ、元の変数のデータ型である `String` と `Double`になります。</span><span class="sxs-lookup"><span data-stu-id="c815c-113">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]

- <span data-ttu-id="c815c-114">他のオブジェクトのプロパティまたはフィールドの名前から。</span><span class="sxs-lookup"><span data-stu-id="c815c-114">From property or field names of other objects.</span></span> <span data-ttu-id="c815c-115">たとえば、 `car` プロパティと `CarClass` プロパティを含む `Name` 型の `ID` オブジェクトがあるとします。</span><span class="sxs-lookup"><span data-stu-id="c815c-115">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="c815c-116">新しい匿名型のインスタンス `car1`を作成し、 `Name` オブジェクトの値を使用して `ID` プロパティと `car` プロパティを初期化するには、次のように記述できます。</span><span class="sxs-lookup"><span data-stu-id="c815c-116">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>

  [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]

  <span data-ttu-id="c815c-117">前の宣言は、匿名型 `car2`を定義する、次の長いコードに相当します。</span><span class="sxs-lookup"><span data-stu-id="c815c-117">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]

- <span data-ttu-id="c815c-118">XML メンバー名から。</span><span class="sxs-lookup"><span data-stu-id="c815c-118">From XML member names.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]

  <span data-ttu-id="c815c-119">推論後の `anon` の型は、 `Book`(Of XElement) 型の 1 つのプロパティ <xref:System.Collections.IEnumerable>を持ちます。</span><span class="sxs-lookup"><span data-stu-id="c815c-119">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>

- <span data-ttu-id="c815c-120">次の例に示す `SomeFunction` など、パラメーターを持たない関数から。</span><span class="sxs-lookup"><span data-stu-id="c815c-120">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>

  ```vb
  Dim sc As New SomeClass
  Dim anon1 = New With {Key sc.SomeFunction()}
  ```

  <span data-ttu-id="c815c-121">次のコードの `anon2` 変数は、 `First`という名前の 1 文字を表すプロパティを 1 つ持つ匿名型です。</span><span class="sxs-lookup"><span data-stu-id="c815c-121">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="c815c-122">このコードでは、文字 "E" が表示されます。これは関数 <xref:System.Linq.Enumerable.First%2A>から返される文字です。</span><span class="sxs-lookup"><span data-stu-id="c815c-122">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]

## <a name="inference-failures"></a><span data-ttu-id="c815c-123">推論の失敗</span><span class="sxs-lookup"><span data-stu-id="c815c-123">Inference Failures</span></span>

#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="c815c-124">名前の推論は、次の状況を含む、さまざまな状況で失敗します:</span><span class="sxs-lookup"><span data-stu-id="c815c-124">Name inference will fail in many circumstances, including the following:</span></span>

- <span data-ttu-id="c815c-125">推論が、引数を必要とするメソッド、コンストラクター、またはパラメーター化されたプロパティの呼び出しから派生する場合。</span><span class="sxs-lookup"><span data-stu-id="c815c-125">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="c815c-126">前の `anon1` の宣言は、 `someFunction` に 1 つ以上の引数があると失敗します。</span><span class="sxs-lookup"><span data-stu-id="c815c-126">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon3 = New With {Key sc.someFunction(someArg)}
  ```

  <span data-ttu-id="c815c-127">この問題は、新しいプロパティ名を割り当てることによって解決できます。</span><span class="sxs-lookup"><span data-stu-id="c815c-127">Assignment to a new property name solves the problem.</span></span>

  ```vb
  ' Valid.
  Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}
  ```

- <span data-ttu-id="c815c-128">推論が、複合式から派生する場合。</span><span class="sxs-lookup"><span data-stu-id="c815c-128">The inference derives from a complex expression.</span></span>

  ```vb
  Dim aString As String = "Act "
  ' Not valid.
  ' Dim label = New With {Key aString & "IV"}
  ```

  <span data-ttu-id="c815c-129">このエラーは、式の結果をプロパティ名に割り当てれば解決できます。</span><span class="sxs-lookup"><span data-stu-id="c815c-129">The error can be resolved by assigning the result of the expression to a property name.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]

- <span data-ttu-id="c815c-130">複数のプロパティの推論で、同じ名前を持つ 2 つ以上のプロパティが生成される場合。</span><span class="sxs-lookup"><span data-stu-id="c815c-130">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="c815c-131">前の例で示した宣言で説明すると、同じ匿名型のプロパティとして `product.Name` と `car1.Name` の両方を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="c815c-131">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="c815c-132">これは、各プロパティの推論された識別子がどちらも `Name`になるためです。</span><span class="sxs-lookup"><span data-stu-id="c815c-132">This is because the inferred identifier for each of these would be `Name`.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon5 = New With {Key product.Name, Key car1.Name}
  ```

  <span data-ttu-id="c815c-133">この問題は、別個のプロパティ名に値を割り当てることで解決できます。</span><span class="sxs-lookup"><span data-stu-id="c815c-133">The problem can be solved by assigning the values to distinct property names.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]

  <span data-ttu-id="c815c-134">大文字と小文字の違いでは、別個の名前にならないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="c815c-134">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>

  ```vb
  Dim price = 0
  ' Not valid, because Price and price are the same name.
  ' Dim anon7 = New With {Key product.Price, Key price}
  ```

- <span data-ttu-id="c815c-135">1 つのプロパティの初期の型と値が、まだ確立されていない別のプロパティに依存している場合。</span><span class="sxs-lookup"><span data-stu-id="c815c-135">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="c815c-136">たとえば、 `.IDName = .LastName` は、 `.LastName` が既に初期化されていない限り、匿名型の宣言では使えません。</span><span class="sxs-lookup"><span data-stu-id="c815c-136">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}
  ```

  <span data-ttu-id="c815c-137">この例では、プロパティを宣言する順序を逆にすることで、問題を修正できます。</span><span class="sxs-lookup"><span data-stu-id="c815c-137">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]

- <span data-ttu-id="c815c-138">匿名型のプロパティの名前が、 <xref:System.Object>のメンバーの名前と同じである場合。</span><span class="sxs-lookup"><span data-stu-id="c815c-138">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="c815c-139">たとえば、次の宣言は、 `Equals` が <xref:System.Object>のメソッドなので失敗します。</span><span class="sxs-lookup"><span data-stu-id="c815c-139">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>

  ```vb
  ' Not valid.
  ' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _
  '                       "greater than", Key .Less = "less than"}
  ```

  <span data-ttu-id="c815c-140">この問題は、プロパティ名を変更することで修正できます。</span><span class="sxs-lookup"><span data-stu-id="c815c-140">You can fix the problem by changing the property name:</span></span>

  [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]

## <a name="see-also"></a><span data-ttu-id="c815c-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="c815c-141">See also</span></span>

- [<span data-ttu-id="c815c-142">オブジェクト初期化子: 名前付きの型と匿名型</span><span class="sxs-lookup"><span data-stu-id="c815c-142">Object Initializers: Named and Anonymous Types</span></span>](object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="c815c-143">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="c815c-143">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="c815c-144">匿名型</span><span class="sxs-lookup"><span data-stu-id="c815c-144">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="c815c-145">Key</span><span class="sxs-lookup"><span data-stu-id="c815c-145">Key</span></span>](../../../language-reference/modifiers/key.md)
