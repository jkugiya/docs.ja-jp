---
description: '詳細情報: オブジェクト初期化子:名前付きの型と匿名型 (Visual Basic)'
title: オブジェクト初期化子:名前付きの型と匿名型
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 47182653e74b16b9911f4b727eb1595bf3eceba6
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455250"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a><span data-ttu-id="9e5c3-103">オブジェクト初期化子:名前付きの型と匿名型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e5c3-103">Object Initializers: Named and Anonymous Types (Visual Basic)</span></span>

<span data-ttu-id="9e5c3-104">オブジェクト初期化子を使用すると、1 つの式を使用して複雑なオブジェクトのプロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-104">Object initializers enable you to specify properties for a complex object by using a single expression.</span></span> <span data-ttu-id="9e5c3-105">それらを使用して、名前付きの型と匿名型のインスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-105">They can be used to create instances of named types and of anonymous types.</span></span>  
  
## <a name="declarations"></a><span data-ttu-id="9e5c3-106">宣言</span><span class="sxs-lookup"><span data-stu-id="9e5c3-106">Declarations</span></span>  

 <span data-ttu-id="9e5c3-107">名前付きの型と匿名型のインスタンスの宣言はほぼ同じように見えますが、それらの効果は同じではありません。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-107">Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same.</span></span> <span data-ttu-id="9e5c3-108">各カテゴリには、独自の機能と制限があります。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-108">Each category has abilities and restrictions of its own.</span></span> <span data-ttu-id="9e5c3-109">次の例は、オブジェクト初期化子リストを使用して、名前付きクラス `Customer` のインスタンスを宣言して初期化する便利な方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-109">The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list.</span></span> <span data-ttu-id="9e5c3-110">クラスの名前がキーワード `New` の後に指定されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-110">Notice that the name of the class is specified after the keyword `New`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 <span data-ttu-id="9e5c3-111">匿名型には使用可能な名前がありません。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-111">An anonymous type has no usable name.</span></span> <span data-ttu-id="9e5c3-112">そのため、匿名型のインスタンス化でクラス名を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-112">Therefore an instantiation of an anonymous type cannot include a class name.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 <span data-ttu-id="9e5c3-113">2 つの宣言の要件と結果は同じではありません。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-113">The requirements and results of the two declarations are not the same.</span></span> <span data-ttu-id="9e5c3-114">`namedCust` の場合、`Name` プロパティを持つ `Customer` クラスが既に存在している必要があり、宣言によってそのクラスのインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-114">For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class.</span></span> <span data-ttu-id="9e5c3-115">`anonymousCust` の場合、コンパイラによって、1 つのプロパティ、`Name` という文字列を持つ新しいクラスが定義され、そのクラスの新しいインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-115">For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.</span></span>  
  
## <a name="named-types"></a><span data-ttu-id="9e5c3-116">名前付きの型</span><span class="sxs-lookup"><span data-stu-id="9e5c3-116">Named Types</span></span>  

 <span data-ttu-id="9e5c3-117">オブジェクト初期化子は、型のコンストラクターを呼び出し、1 つのステートメントで一部またはすべてのプロパティの値を設定するシンプルな方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-117">Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement.</span></span> <span data-ttu-id="9e5c3-118">コンパイラによって、ステートメントの適切なコンストラクターが呼び出されます。引数が指定されていない場合はパラメーターなしのコンストラクター、または 1 つ以上の引数が渡された場合はパラメーター化されたコンストラクターです。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-118">The compiler invokes the appropriate constructor for the statement: the parameterless constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent.</span></span> <span data-ttu-id="9e5c3-119">その後、指定したプロパティが、初期化子リストに提示されている順序で初期化されます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-119">After that, the specified properties are initialized in the order in which they are presented in the initializer list.</span></span>  
  
 <span data-ttu-id="9e5c3-120">初期化子リストの各初期化は、クラスのメンバーへの初期値の代入から構成されます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-120">Each initialization in the initializer list consists of the assignment of an initial value to a member of the class.</span></span> <span data-ttu-id="9e5c3-121">メンバーの名前とデータ型は、クラスを定義するときに決定します。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-121">The names and data types of the members are determined when the class is defined.</span></span> <span data-ttu-id="9e5c3-122">次の例では、`Customer` クラスが存在する必要があり、文字列値を受け入れる `Name` と `City` という名前のメンバーが必要です。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-122">In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 <span data-ttu-id="9e5c3-123">または、次のコードを使用して同じ結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-123">Alternatively, you can obtain the same result by using the following code:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 <span data-ttu-id="9e5c3-124">これらの各宣言は、次の例と同じです。この例では、パラメーターなしのコンストラクターを使用して `Customer` オブジェクトを作成し、次に `With` ステートメントを使用して、`Name` および `City` プロパティの初期値を指定しています。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-124">Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the parameterless constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 <span data-ttu-id="9e5c3-125">`Customer` クラスに、たとえば `Name` の値を渡すことができるパラメーター化されたコンストラクターが含まれている場合、次の方法で `Customer` オブジェクトを宣言して初期化することもできます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-125">If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 <span data-ttu-id="9e5c3-126">次のコードに示すように、すべてのプロパティを初期化する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-126">You do not have to initialize all properties, as the following code shows.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 <span data-ttu-id="9e5c3-127">ただし、初期化リストを空にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-127">However, the initialization list cannot be empty.</span></span> <span data-ttu-id="9e5c3-128">初期化されていないプロパティでは、それらの既定値が保持されます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-128">Uninitialized properties retain their default values.</span></span>  
  
### <a name="type-inference-with-named-types"></a><span data-ttu-id="9e5c3-129">名前付きの型による型の推定</span><span class="sxs-lookup"><span data-stu-id="9e5c3-129">Type Inference with Named Types</span></span>  

 <span data-ttu-id="9e5c3-130">オブジェクト初期化子とローカル型推論を組み合わせて、`cust1` の宣言のコードを短縮できます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-130">You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference.</span></span> <span data-ttu-id="9e5c3-131">これにより、変数宣言で `As` 句を省略できます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-131">This enables you to omit the `As` clause in the variable declaration.</span></span> <span data-ttu-id="9e5c3-132">変数のデータ型は、代入によって作成されたオブジェクトの型から推論されます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-132">The data type of the variable is inferred from the type of the object that is created by the assignment.</span></span> <span data-ttu-id="9e5c3-133">次の例では、`cust6` の型は `Customer` です。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-133">In the following example, the type of `cust6` is `Customer`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a><span data-ttu-id="9e5c3-134">名前付きの型に関する注意</span><span class="sxs-lookup"><span data-stu-id="9e5c3-134">Remarks About Named Types</span></span>  
  
- <span data-ttu-id="9e5c3-135">オブジェクト初期化子リストでクラス メンバーを複数回初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-135">A class member cannot be initialized more than one time in the object initializer list.</span></span> <span data-ttu-id="9e5c3-136">`cust7` の宣言によってエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-136">The declaration of `cust7` causes an error.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- <span data-ttu-id="9e5c3-137">メンバーは、それ自体または別のフィールドを初期化するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-137">A member can be used to initialize itself or another field.</span></span> <span data-ttu-id="9e5c3-138">次の `cust8` の宣言のように、メンバーが初期化される前にアクセスされた場合は、既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-138">If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used.</span></span> <span data-ttu-id="9e5c3-139">オブジェクト初期化子を使用する宣言が処理されるときに最初に行われることは、適切なコンストラクターの呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-139">Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked.</span></span> <span data-ttu-id="9e5c3-140">その後、初期化子リスト内の個々のフィールドが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-140">After that, the individual fields in the initializer list are initialized.</span></span> <span data-ttu-id="9e5c3-141">次の例では、`Name` の既定値が `cust8` に代入され、初期化された値が `cust9` に代入されています。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-141">In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     <span data-ttu-id="9e5c3-142">次の例では、`cust3` と `cust4` のパラメーター化されたコンストラクターを使用して、`cust10` と `cust11` を宣言して初期化しています。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-142">The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- <span data-ttu-id="9e5c3-143">オブジェクト初期化子は入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-143">Object initializers can be nested.</span></span> <span data-ttu-id="9e5c3-144">次の例では、`AddressClass` は `City` と `State` の 2 つのプロパティを持つクラスであり、`Customer` クラスには `Address` のインスタンスである `AddressClass` プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-144">In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- <span data-ttu-id="9e5c3-145">初期化リストは空にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-145">The initialization list cannot be empty.</span></span>  
  
- <span data-ttu-id="9e5c3-146">初期化されるインスタンスはオブジェクト型にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-146">The instance being initialized cannot be of type Object.</span></span>  
  
- <span data-ttu-id="9e5c3-147">初期化されるクラス メンバーは、共有メンバー、読み取り専用のメンバー、定数、またはメソッド呼び出しにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-147">Class members being initialized cannot be shared members, read-only members, constants, or method calls.</span></span>  
  
- <span data-ttu-id="9e5c3-148">初期化されるクラス メンバーにインデックスを作成したり、修飾したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-148">Class members being initialized cannot be indexed or qualified.</span></span> <span data-ttu-id="9e5c3-149">次の例ではコンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-149">The following examples raise compiler errors:</span></span>  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a><span data-ttu-id="9e5c3-150">匿名型</span><span class="sxs-lookup"><span data-stu-id="9e5c3-150">Anonymous Types</span></span>  

 <span data-ttu-id="9e5c3-151">匿名型では、オブジェクト初期化子を使用して、明示的に定義して名前を付けない新しい型のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-151">Anonymous types use object initializers to create instances of new types that you do not explicitly define and name.</span></span> <span data-ttu-id="9e5c3-152">代わりに、コンパイラによって、オブジェクト初期化子リストに指定したプロパティに従って型が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-152">Instead, the compiler generates a type according to the properties you designate in the object initializer list.</span></span> <span data-ttu-id="9e5c3-153">型の名前を指定しないため、*匿名型* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-153">Because the name of the type is not specified, it is referred to as an *anonymous type*.</span></span> <span data-ttu-id="9e5c3-154">たとえば、次の宣言を先述の `cust6` の宣言と比較します。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-154">For example, compare the following declaration to the earlier one for `cust6`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 <span data-ttu-id="9e5c3-155">構文上の違いは、`New` の後に、データ型についての名前が指定されていないことだけです。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-155">The only difference syntactically is that no name is specified after `New` for the data type.</span></span> <span data-ttu-id="9e5c3-156">しかし、何が起こるかはかなり異なります。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-156">However, what happens is quite different.</span></span> <span data-ttu-id="9e5c3-157">コンパイラによって、`Name` と `City` の 2 つのプロパティを持つ新しい匿名型が定義され、指定した値を使用してそのインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-157">The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values.</span></span> <span data-ttu-id="9e5c3-158">型の推定によって、例の `Name` と `City` の型が文字列であると判断されます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-158">Type inference determines the types of `Name` and `City` in the example to be strings.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="9e5c3-159">匿名型の名前はコンパイラによって生成され、コンパイルごとに異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-159">The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation.</span></span> <span data-ttu-id="9e5c3-160">コードでは、匿名型の名前を使用したり、それに依存したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-160">Your code should not use or rely on the name of an anonymous type.</span></span>  
  
 <span data-ttu-id="9e5c3-161">型の名前を使用できないため、`As` 句を使用して `cust13` を宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-161">Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`.</span></span> <span data-ttu-id="9e5c3-162">その型は推論される必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-162">Its type must be inferred.</span></span> <span data-ttu-id="9e5c3-163">遅延バインディングを使用しない場合、これによって、匿名型の使用がローカル変数に限定されます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-163">Without using late binding, this limits the use of anonymous types to local variables.</span></span>  
  
 <span data-ttu-id="9e5c3-164">匿名型は、LINQ クエリのクリティカルなサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-164">Anonymous types provide critical support for LINQ queries.</span></span> <span data-ttu-id="9e5c3-165">クエリでの匿名型の使用の詳細については、「[匿名型](anonymous-types.md)」と「[Visual Basic における LINQ の概要](../linq/introduction-to-linq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-165">For more information about the use of anonymous types in queries, see [Anonymous Types](anonymous-types.md) and [Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md).</span></span>  
  
### <a name="remarks-about-anonymous-types"></a><span data-ttu-id="9e5c3-166">匿名型に関する注意</span><span class="sxs-lookup"><span data-stu-id="9e5c3-166">Remarks About Anonymous Types</span></span>  
  
- <span data-ttu-id="9e5c3-167">一般に、匿名型の宣言に含まれるすべてまたはほとんどのプロパティがキー プロパティになります。これは、プロパティ名の前に `Key` キーワードを入力することによって示されます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-167">Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     <span data-ttu-id="9e5c3-168">キー プロパティの詳細については、「[Key](../../../language-reference/modifiers/key.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-168">For more information about key properties, see [Key](../../../language-reference/modifiers/key.md).</span></span>  
  
- <span data-ttu-id="9e5c3-169">名前付きの型と同様に、匿名型定義の初期化子リストには、少なくとも 1 つのプロパティを宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-169">Like named types, initializer lists for anonymous type definitions must declare at least one property.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- <span data-ttu-id="9e5c3-170">匿名型のインスタンスが宣言されている場合、コンパイラによって、一致する匿名型定義が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-170">When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition.</span></span> <span data-ttu-id="9e5c3-171">プロパティの名前とデータ型が、インスタンス宣言から取得され、コンパイラによって定義に含まれます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-171">The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition.</span></span> <span data-ttu-id="9e5c3-172">名前付きの型の場合と同じように、プロパティには事前に名前が付けられて定義されません。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-172">The properties are not named and defined in advance, as they would be for a named type.</span></span> <span data-ttu-id="9e5c3-173">それらの型は推論されます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-173">Their types are inferred.</span></span> <span data-ttu-id="9e5c3-174">`As` 句を使用してプロパティのデータ型を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-174">You cannot specify the data types of the properties by using an `As` clause.</span></span>  
  
- <span data-ttu-id="9e5c3-175">匿名型では、他のいくつかの方法でプロパティの名前と値を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-175">Anonymous types can also establish the names and values of their properties in several other ways.</span></span> <span data-ttu-id="9e5c3-176">たとえば、匿名型のプロパティは、変数の名前と値の両方、または別のオブジェクトのプロパティの名前と値の両方を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-176">For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     <span data-ttu-id="9e5c3-177">匿名型でプロパティを定義するためのオプションの詳細については、「[方法:匿名型の宣言におけるプロパティ名と型を推論する](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e5c3-177">For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e5c3-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e5c3-178">See also</span></span>

- [<span data-ttu-id="9e5c3-179">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="9e5c3-179">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="9e5c3-180">匿名型</span><span class="sxs-lookup"><span data-stu-id="9e5c3-180">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="9e5c3-181">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="9e5c3-181">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="9e5c3-182">方法: 匿名型の宣言におけるプロパティ名と型を推論する</span><span class="sxs-lookup"><span data-stu-id="9e5c3-182">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="9e5c3-183">Key</span><span class="sxs-lookup"><span data-stu-id="9e5c3-183">Key</span></span>](../../../language-reference/modifiers/key.md)
- [<span data-ttu-id="9e5c3-184">方法: オブジェクト初期化子を使用してオブジェクトを宣言する</span><span class="sxs-lookup"><span data-stu-id="9e5c3-184">How to: Declare an Object by Using an Object Initializer</span></span>](how-to-declare-an-object-by-using-an-object-initializer.md)
