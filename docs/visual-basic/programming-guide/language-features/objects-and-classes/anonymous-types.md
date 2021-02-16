---
description: '詳細情報: 匿名型 (Visual Basic)'
title: 匿名型
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
ms.openlocfilehash: 447ca914726d4b426ad4ba2ec370a4bbe9589b81
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425621"
---
# <a name="anonymous-types-visual-basic"></a><span data-ttu-id="b7a1b-103">匿名型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7a1b-103">Anonymous Types (Visual Basic)</span></span>

<span data-ttu-id="b7a1b-104">Visual Basic では匿名型がサポートされています。これを使用すると、データ型のクラス定義を記述せずにオブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-104">Visual Basic supports anonymous types, which enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="b7a1b-105">クラスは、コンパイラによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-105">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="b7a1b-106">このクラスには使用可能な名前がなく、<xref:System.Object> から直接継承され、オブジェクトの宣言時に指定したプロパティが格納されます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-106">The class has no usable name, inherits directly from <xref:System.Object>, and contains the properties you specify in declaring the object.</span></span> <span data-ttu-id="b7a1b-107">データ型の名前を指定しないため、*匿名型* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-107">Because the name of the data type is not specified, it is referred to as an *anonymous type*.</span></span>  
  
 <span data-ttu-id="b7a1b-108">次の例では、`Name` と `Price` の 2 つのプロパティを持つ匿名型のインスタンスとして、変数 `product` を宣言して作成します。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-108">The following example declares and creates variable `product` as an instance of an anonymous type that has two properties, `Name` and `Price`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 <span data-ttu-id="b7a1b-109">*クエリ式* は、匿名型を使用して、クエリによって選択されたデータの列を結合します。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-109">A *query expression* uses anonymous types to combine columns of data selected by a query.</span></span> <span data-ttu-id="b7a1b-110">特定のクエリによって選択される可能性のある列を予測できないため、結果の型を事前に定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-110">You cannot define the type of the result in advance, because you cannot predict the columns a particular query might select.</span></span> <span data-ttu-id="b7a1b-111">匿名型を使用すると、任意の数の列を任意の順序で選択するクエリを記述できます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-111">Anonymous types enable you to write a query that selects any number of columns, in any order.</span></span> <span data-ttu-id="b7a1b-112">コンパイラは、指定されたプロパティと指定された順序に一致するデータ型を作成します。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-112">The compiler creates a data type that matches the specified properties and the specified order.</span></span>  
  
 <span data-ttu-id="b7a1b-113">次の例では、`products` は Product オブジェクトの一覧であり、それぞれに多くのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-113">In the following examples, `products` is a list of product objects, each of which has many properties.</span></span> <span data-ttu-id="b7a1b-114">変数 `namePriceQuery` は、実行されると `Name` と `Price` の 2 つのプロパティを持つ匿名型のインスタンスのコレクションを返すクエリの定義を保持します。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-114">Variable `namePriceQuery` holds the definition of a query that, when it is executed, returns a collection of instances of an anonymous type that has two properties, `Name` and `Price`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#2)]  
  
 <span data-ttu-id="b7a1b-115">変数 `nameQuantityQuery` は、実行されると `Name` と `OnHand` の 2 つのプロパティを持つ匿名型のインスタンスのコレクションを返すクエリの定義を保持します。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-115">Variable `nameQuantityQuery` holds the definition of a query that, when it is executed, returns a collection of instances of an anonymous type that has two properties, `Name` and `OnHand`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#3)]  
  
 <span data-ttu-id="b7a1b-116">コンパイラによって作成される匿名型のコードの詳細については、「[匿名型の定義](anonymous-type-definition.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-116">For more information about the code created by the compiler for an anonymous type, see [Anonymous Type Definition](anonymous-type-definition.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="b7a1b-117">匿名型の名前はコンパイラによって生成され、コンパイルごとに異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-117">The name of the anonymous type is compiler generated and may vary from compilation to compilation.</span></span> <span data-ttu-id="b7a1b-118">プロジェクトが再コンパイルされるときに名前が変更される可能性があるため、コードでは、匿名型の名前を使用したり、それに依存したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-118">Your code should not use or rely on the name of an anonymous type because the name might change when a project is recompiled.</span></span>  
  
## <a name="declaring-an-anonymous-type"></a><span data-ttu-id="b7a1b-119">匿名型の宣言</span><span class="sxs-lookup"><span data-stu-id="b7a1b-119">Declaring an Anonymous Type</span></span>  

 <span data-ttu-id="b7a1b-120">匿名型のインスタンスの宣言では、初期化子リストを使用して型のプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-120">The declaration of an instance of an anonymous type uses an initializer list to specify the properties of the type.</span></span> <span data-ttu-id="b7a1b-121">メソッドやイベントなどの他のクラス要素ではなく、匿名型を宣言する場合は、プロパティのみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-121">You can specify only properties when you declare an anonymous type, not other class elements such as methods or events.</span></span> <span data-ttu-id="b7a1b-122">次の例では、`product1` は、`Name` と `Price` の 2 つのプロパティを持つ匿名型のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-122">In the following example, `product1` is an instance of an anonymous type that has two properties: `Name` and `Price`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#4)]  
  
 <span data-ttu-id="b7a1b-123">プロパティをキー プロパティとして指定した場合は、これらを使用して、2 つの匿名型インスタンスが等しいかどうかを比較できます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-123">If you designate properties as key properties, you can use them to compare two anonymous type instances for equality.</span></span> <span data-ttu-id="b7a1b-124">ただし、キー プロパティの値は変更できません。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-124">However, the values of key properties cannot be changed.</span></span> <span data-ttu-id="b7a1b-125">詳細については、このトピックで後述する「キー プロパティ」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-125">See the Key Properties section later in this topic for more information.</span></span>  
  
 <span data-ttu-id="b7a1b-126">匿名型のインスタンスの宣言は、オブジェクト初期化子を使用して名前付きの型のインスタンスを宣言するのと似ていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-126">Notice that declaring an instance of an anonymous type is like declaring an instance of a named type by using an object initializer:</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#5)]  
  
 <span data-ttu-id="b7a1b-127">匿名型のプロパティを指定するその他の方法の詳細については、「[方法: 匿名型の宣言におけるプロパティ名と型を推論する](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-127">For more information about other ways to specify anonymous type properties, see [How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="b7a1b-128">キー プロパティ</span><span class="sxs-lookup"><span data-stu-id="b7a1b-128">Key Properties</span></span>  

 <span data-ttu-id="b7a1b-129">キー プロパティは、次のいくつかの基本的な点で、キー以外のプロパティとは異なります。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-129">Key properties differ from non-key properties in several fundamental ways:</span></span>  
  
- <span data-ttu-id="b7a1b-130">2 つのインスタンスが等しいかどうかを確認するためには、キー プロパティの値のみが比較されます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-130">Only the values of key properties are compared in order to determine whether two instances are equal.</span></span>  
  
- <span data-ttu-id="b7a1b-131">キー プロパティの値は読み取り専用であり、変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-131">The values of key properties are read-only and cannot be changed.</span></span>  
  
- <span data-ttu-id="b7a1b-132">コンパイラによって生成された匿名型のハッシュ コード アルゴリズムには、キー プロパティ値のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-132">Only key property values are included in the compiler-generated hash code algorithm for an anonymous type.</span></span>  
  
### <a name="equality"></a><span data-ttu-id="b7a1b-133">等価比較</span><span class="sxs-lookup"><span data-stu-id="b7a1b-133">Equality</span></span>  

 <span data-ttu-id="b7a1b-134">匿名型のインスタンスは、同じ匿名型のインスタンスである場合にのみ等しくすることができます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-134">Instances of anonymous types can be equal only if they are instances of the same anonymous type.</span></span> <span data-ttu-id="b7a1b-135">コンパイラは、次の条件を満たす場合、2 つのインスタンスを同じ型のインスタンスとして扱います。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-135">The compiler treats two instances as instances of the same type if they meet the following conditions:</span></span>  
  
- <span data-ttu-id="b7a1b-136">これらは同じアセンブリ内で宣言されています。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-136">They are declared in the same assembly.</span></span>  
  
- <span data-ttu-id="b7a1b-137">これらのプロパティは同じ名前を持ち、推論される型は同じであり、同じ順序で宣言されています。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-137">Their properties have the same names, the same inferred types, and are declared in the same order.</span></span> <span data-ttu-id="b7a1b-138">名前の比較では、大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-138">Name comparisons are not case-sensitive.</span></span>  
  
- <span data-ttu-id="b7a1b-139">それぞれに含まれる同じプロパティは、キー プロパティとしてマークされます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-139">The same properties in each are marked as key properties.</span></span>  
  
- <span data-ttu-id="b7a1b-140">各宣言の少なくとも 1 つのプロパティがキー プロパティです。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-140">At least one property in each declaration is a key property.</span></span>  
  
 <span data-ttu-id="b7a1b-141">キー プロパティを持たない匿名型のインスタンスは、それ自体とのみ等しくなります。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-141">An instance of an anonymous types that has no key properties is equal only to itself.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#6)]  
  
 <span data-ttu-id="b7a1b-142">同じ匿名型の 2 つのインスタンスは、それらのキー プロパティの値が等しい場合に等しいとされます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-142">Two instances of the same anonymous type are equal if the values of their key properties are equal.</span></span> <span data-ttu-id="b7a1b-143">次の例は、等価性のテスト方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-143">The following examples illustrate how equality is tested.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#7)]  
  
### <a name="read-only-values"></a><span data-ttu-id="b7a1b-144">読み取り専用の値</span><span class="sxs-lookup"><span data-stu-id="b7a1b-144">Read-Only Values</span></span>  

 <span data-ttu-id="b7a1b-145">キー プロパティの値は変更できません。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-145">The values of key properties cannot be changed.</span></span> <span data-ttu-id="b7a1b-146">たとえば、前の例の `prod8` では、`Name` フィールドと `Price` フィールドは `read-only` ですが、`OnHand` は変更できます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-146">For example, in `prod8` in the previous example, the `Name` and `Price` fields are `read-only`, but `OnHand` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#8)]  
  
## <a name="anonymous-types-from-query-expressions"></a><span data-ttu-id="b7a1b-147">クエリ式からの匿名型</span><span class="sxs-lookup"><span data-stu-id="b7a1b-147">Anonymous Types from Query Expressions</span></span>  

 <span data-ttu-id="b7a1b-148">クエリ式では、必ずしも匿名型を作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-148">Query expressions do not always require the creation of anonymous types.</span></span> <span data-ttu-id="b7a1b-149">可能な場合は、既存の型を使用して列データを保持します。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-149">When possible, they use an existing type to hold the column data.</span></span> <span data-ttu-id="b7a1b-150">これは、クエリがデータ ソースからレコード全体を返すか、または各レコードのフィールドを 1 つだけ返す場合に行われます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-150">This occurs when the query returns either whole records from the data source, or only one field from each record.</span></span> <span data-ttu-id="b7a1b-151">次のコード例では、`customers` は `Customer` クラスのオブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-151">In the following code examples, `customers` is a collection of objects of a `Customer` class.</span></span> <span data-ttu-id="b7a1b-152">クラスには多くのプロパティがあり、クエリの結果には、任意の順序で 1 つ以上のプロパティを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-152">The class has many properties, and you can include one or more of them in the query result, in any order.</span></span> <span data-ttu-id="b7a1b-153">最初の 2 つの例では、クエリで名前付きの型の要素が選択されるため、匿名型は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-153">In the first two examples, no anonymous types are required because the queries select elements of named types:</span></span>  
  
- <span data-ttu-id="b7a1b-154">`custs1` には文字列のコレクションが含まれます。`cust.Name` が文字列であるためです。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-154">`custs1` contains a collection of strings, because `cust.Name` is a string.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#30)]  
  
- <span data-ttu-id="b7a1b-155">`custs2` には `Customer` オブジェクトのコレクションが含まれます。`customers` の各要素が `Customer` オブジェクトであり、要素全体がクエリによって選択されるためです。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-155">`custs2` contains a collection of `Customer` objects, because each element of `customers` is a `Customer` object, and the whole element is selected by the query.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#31)]  
  
 <span data-ttu-id="b7a1b-156">ただし、適切な名前付きの型が常に使用可能とは限りません。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-156">However, appropriate named types are not always available.</span></span> <span data-ttu-id="b7a1b-157">ある目的のために顧客の名前と住所を、別の目的のために顧客の ID 番号と場所を、そして 3 つ目の目的のために顧客の名前、住所、および注文履歴を選択することができます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-157">You might want to select customer names and addresses for one purpose, customer ID numbers and locations for another, and customer names, addresses, and order histories for a third.</span></span> <span data-ttu-id="b7a1b-158">匿名型を使用すると、プロパティの任意の組み合わせを任意の順序で選択でき、最初に結果を保持するために新しい名前付きの型を宣言する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-158">Anonymous types enable you to select any combination of properties, in any order, without first declaring a new named type to hold the result.</span></span> <span data-ttu-id="b7a1b-159">代わりに、コンパイラは、プロパティのコンパイルごとに匿名型を作成します。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-159">Instead, the compiler creates an anonymous type for each compilation of properties.</span></span> <span data-ttu-id="b7a1b-160">次のクエリでは、`customers` の各 `Customer` オブジェクトから、顧客の名前と ID 番号のみを選択します。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-160">The following query selects only the customer's name and ID number from each `Customer` object in `customers`.</span></span> <span data-ttu-id="b7a1b-161">そのため、コンパイラは、それら 2 つのプロパティのみが含まれている匿名型を作成します。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-161">Therefore, the compiler creates an anonymous type that contains only those two properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#32)]  
  
 <span data-ttu-id="b7a1b-162">匿名型のプロパティの名前とデータ型は両方とも、`Select`、`cust.Name`、および `cust.ID` の引数から取得されます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-162">Both the names and the data types of the properties in the anonymous type are taken from the arguments to `Select`, `cust.Name` and `cust.ID`.</span></span> <span data-ttu-id="b7a1b-163">クエリによって作成される匿名型のプロパティは、常にキー プロパティです。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-163">The properties in an anonymous type that is created by a query are always key properties.</span></span> <span data-ttu-id="b7a1b-164">次の `For Each` ループで `custs3` を実行すると、結果は `Name` と `ID` の 2 つのキー プロパティを持つ匿名型のインスタンスのコレクションになります。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-164">When `custs3` is executed in the following `For Each` loop, the result is a collection of instances of an anonymous type with two key properties, `Name` and `ID`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#33)]  
  
 <span data-ttu-id="b7a1b-165">`custs3` によって表されるコレクション内の要素は厳密に型指定されます。IntelliSense を使用して、使用可能なプロパティ間を移動したり、その型を検証したりできます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-165">The elements in the collection represented by `custs3` are strongly typed, and you can use IntelliSense to navigate through the available properties and to verify their types.</span></span>  
  
 <span data-ttu-id="b7a1b-166">詳細については、「[Visual Basic における LINQ の概要](../linq/introduction-to-linq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-166">For more information, see [Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md).</span></span>  
  
## <a name="deciding-whether-to-use-anonymous-types"></a><span data-ttu-id="b7a1b-167">匿名型を使用するかどうかの決定</span><span class="sxs-lookup"><span data-stu-id="b7a1b-167">Deciding Whether to Use Anonymous Types</span></span>  

 <span data-ttu-id="b7a1b-168">オブジェクトを匿名クラスのインスタンスとして作成する前に、それが最適な選択肢かどうかを検討してください。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-168">Before you create an object as an instance of an anonymous class, consider whether that is the best option.</span></span> <span data-ttu-id="b7a1b-169">たとえば、関連データを格納する一時オブジェクトを作成する場合に、完全なクラスに含まれる可能性のある他のフィールドやメソッドが不要な場合は、匿名型が適切な解決策です。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-169">For example, if you want to create a temporary object to contain related data, and you have no need for other fields and methods that a complete class might contain, an anonymous type is a good solution.</span></span> <span data-ttu-id="b7a1b-170">匿名型は、宣言ごとに異なるプロパティを選択する場合や、プロパティの順序を変更する場合にも便利です。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-170">Anonymous types are also convenient if you want a different selection of properties for each declaration, or if you want to change the order of the properties.</span></span> <span data-ttu-id="b7a1b-171">ただし、プロジェクトに同じプロパティを持つ複数のオブジェクトが一定の順序で含まれている場合は、クラス コンストラクターを持つ名前付きの型を使用して、より簡単に宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-171">However, if your project includes several objects that have the same properties, in a fixed order, you can declare them more easily by using a named type with a class constructor.</span></span> <span data-ttu-id="b7a1b-172">たとえば、適切なコンストラクターを使用すると、匿名型の複数のインスタンスを宣言するよりも、`Product` クラスの複数のインスタンスを宣言する方が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-172">For example, with an appropriate constructor, it is easier to declare several instances of a `Product` class than it is to declare several instances of an anonymous type.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#9)]  
  
 <span data-ttu-id="b7a1b-173">名前付きの型のもう 1 つの利点は、コンパイラがプロパティ名の誤入力をキャッチできることです。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-173">Another advantage of named types is that the compiler can catch an accidental mistyping of a property name.</span></span> <span data-ttu-id="b7a1b-174">前の例では、`firstProd2`、`secondProd2`、および `thirdProd2` は、同じ匿名型のインスタンスとして意図されています。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-174">In the previous examples, `firstProd2`, `secondProd2`, and `thirdProd2` are intended to be instances of the same anonymous type.</span></span> <span data-ttu-id="b7a1b-175">ただし、次のいずれかの方法で誤って `thirdProd2` を宣言すると、その型が `firstProd2` と `secondProd2` とは異なることになります。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-175">However, if you were to accidentally declare `thirdProd2` in one of the following ways, its type would be different from that of `firstProd2` and `secondProd2`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#10)]  
  
 <span data-ttu-id="b7a1b-176">さらに重要な点として、匿名型の使用には、名前付きの型のインスタンスには適用されない制限があります。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-176">More importantly, there are limitations on the use of anonymous types that do not apply to instances of named types.</span></span> <span data-ttu-id="b7a1b-177">`firstProd2`、`secondProd2`、`thirdProd2` は、同じ匿名型のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-177">`firstProd2`, `secondProd2`, and `thirdProd2` are instances of the same anonymous type.</span></span> <span data-ttu-id="b7a1b-178">ただし、共有されている匿名型の名前は使用できません。また、コードで型名を指定する場所を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-178">However, the name for the shared anonymous type is not available and cannot appear where a type name is expected in your code.</span></span> <span data-ttu-id="b7a1b-179">たとえば、匿名型を使用して、メソッド シグネチャを定義したり、別の変数やフィールドを宣言したり、任意の型宣言で宣言したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-179">For example, an anonymous type cannot be used to define a method signature, to declare another variable or field, or in any type declaration.</span></span> <span data-ttu-id="b7a1b-180">そのため、メソッド間で情報を共有する必要がある場合、匿名型は適切ではありません。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-180">As a result, anonymous types are not appropriate when you have to share information across methods.</span></span>  
  
## <a name="an-anonymous-type-definition"></a><span data-ttu-id="b7a1b-181">匿名型の定義</span><span class="sxs-lookup"><span data-stu-id="b7a1b-181">An Anonymous Type Definition</span></span>  

 <span data-ttu-id="b7a1b-182">匿名型のインスタンスの宣言に応答して、コンパイラは、指定されたプロパティを含む新しいクラス定義を作成します。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-182">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties.</span></span>  
  
 <span data-ttu-id="b7a1b-183">匿名型に少なくとも 1 つのキー プロパティが含まれている場合、<xref:System.Object>: <xref:System.Object.Equals%2A>、<xref:System.Object.GetHashCode%2A>、および <xref:System.Object.ToString%2A> から継承された 3 つのメンバーは、この定義によってオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-183">If the anonymous type contains at least one key property, the definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="b7a1b-184">等価性をテストし、ハッシュ コード値を決定するために生成されたコードは、キー プロパティのみを考慮します。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-184">The code produced for testing equality and determining the hash code value considers only the key properties.</span></span> <span data-ttu-id="b7a1b-185">匿名型にキー プロパティが含まれていない場合は、<xref:System.Object.ToString%2A> のみがオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-185">If the anonymous type contains no key properties, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="b7a1b-186">匿名型の明示的に名前が付けられたプロパティは、生成されたこれらのメソッドと競合しません。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-186">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="b7a1b-187">つまり、`.Equals`、`.GetHashCode`、または `.ToString` を使用してプロパティの名前を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-187">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>  
  
 <span data-ttu-id="b7a1b-188">少なくとも 1 つのキー プロパティを持つ匿名型定義は、<xref:System.IEquatable%601?displayProperty=nameWithType> インターフェイスも実装します。ここで `T` は匿名型の型です。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-188">Anonymous type definitions that have at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>  
  
 <span data-ttu-id="b7a1b-189">コンパイラによって作成される匿名型のコードとオーバーライドされたメソッドの機能の詳細については、「[匿名型の定義](anonymous-type-definition.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7a1b-189">For more information about the code created by the compiler and the functionality of the overridden methods, see [Anonymous Type Definition](anonymous-type-definition.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7a1b-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7a1b-190">See also</span></span>

- [<span data-ttu-id="b7a1b-191">オブジェクト初期化子: 名前付きの型と匿名型</span><span class="sxs-lookup"><span data-stu-id="b7a1b-191">Object Initializers: Named and Anonymous Types</span></span>](object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="b7a1b-192">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="b7a1b-192">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="b7a1b-193">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="b7a1b-193">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="b7a1b-194">方法: 匿名型の宣言におけるプロパティ名と型を推論する</span><span class="sxs-lookup"><span data-stu-id="b7a1b-194">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="b7a1b-195">匿名型の定義</span><span class="sxs-lookup"><span data-stu-id="b7a1b-195">Anonymous Type Definition</span></span>](anonymous-type-definition.md)
- [<span data-ttu-id="b7a1b-196">Key</span><span class="sxs-lookup"><span data-stu-id="b7a1b-196">Key</span></span>](../../../language-reference/modifiers/key.md)
