---
title: プロパティ - C# プログラミング ガイド
description: C# のプロパティは、プライベート フィールドの値の読み取り、書き込み、または計算を行うアクセサー メソッドを使用した、パブリック データのメンバーとしてのメンバーです。
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: 6079fc5d2611ed1111d39d3f39e4c91817db528f
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103189879"
---
# <a name="properties-c-programming-guide"></a><span data-ttu-id="55c33-103">プロパティ (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="55c33-103">Properties (C# Programming Guide)</span></span>

<span data-ttu-id="55c33-104">プロパティは、プライベート フィールドの値の読み取り、書き込み、または計算を行う、柔軟な機構が用意されたメンバーです。</span><span class="sxs-lookup"><span data-stu-id="55c33-104">A property is a member that provides a flexible mechanism to read, write, or compute the value of a private field.</span></span> <span data-ttu-id="55c33-105">プロパティは、パブリック データのメンバーと同様に使用できますが、実際は *アクセサー* という特殊なメソッドです。</span><span class="sxs-lookup"><span data-stu-id="55c33-105">Properties can be used as if they are public data members, but they are actually special methods called *accessors*.</span></span> <span data-ttu-id="55c33-106">メソッドの安全性と柔軟性を高めながら、簡単にデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="55c33-106">This enables data to be accessed easily and still helps promote the safety and flexibility of methods.</span></span>  

## <a name="properties-overview"></a><span data-ttu-id="55c33-107">プロパティの概要</span><span class="sxs-lookup"><span data-stu-id="55c33-107">Properties overview</span></span>  
  
- <span data-ttu-id="55c33-108">プロパティを使えば、実装や検査コードを隠したままで、値の取得と設定についてパブリックな方法をクラスが公開できます。</span><span class="sxs-lookup"><span data-stu-id="55c33-108">Properties enable a class to expose a public way of getting and setting values, while hiding implementation or verification code.</span></span>  
  
- <span data-ttu-id="55c33-109">[get](../../language-reference/keywords/get.md) プロパティ アクセサーはプロパティ値を取得するために使用し、[set](../../language-reference/keywords/set.md) プロパティ アクセサーは新しい値を割り当てるために使用します。</span><span class="sxs-lookup"><span data-stu-id="55c33-109">A [get](../../language-reference/keywords/get.md) property accessor is used to return the property value, and a [set](../../language-reference/keywords/set.md) property accessor is used to assign a new value.</span></span> <span data-ttu-id="55c33-110">C# 9 以降では、オブジェクトの構築時にのみ、[init](../../language-reference/keywords/init.md) プロパティ アクセサーを使用して新しい値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="55c33-110">In C# 9 and later, an [init](../../language-reference/keywords/init.md) property accessor is used to assign a new value only during object construction.</span></span> <span data-ttu-id="55c33-111">これらのアクセサーには異なるアクセス レベルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="55c33-111">These accessors can have different access levels.</span></span> <span data-ttu-id="55c33-112">詳細については、「[アクセサーのアクセシビリティの制限](./restricting-accessor-accessibility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55c33-112">For more information, see [Restricting Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
- <span data-ttu-id="55c33-113">`set` または `init` アクセサーで割り当てる値は [value](../../language-reference/keywords/value.md) キーワードを使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="55c33-113">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` or `init` accessor.</span></span>  
- <span data-ttu-id="55c33-114">プロパティの種類には、*読み取り/書き込み* (`get` アクセサーと `set` アクセサーの両方を備える)、*読み取り専用* (`get` アクセサーのみで `set` アクセサーはない)、*書き込み専用* (`set` アクセサーのみで `get` アクセサーはない) があります。</span><span class="sxs-lookup"><span data-stu-id="55c33-114">Properties can be *read-write* (they have both a `get` and a `set` accessor), *read-only* (they have a `get` accessor but no `set` accessor), or *write-only* (they have a `set` accessor, but no `get` accessor).</span></span> <span data-ttu-id="55c33-115">書き込み専用のプロパティの使用頻度は低く、ほとんどの場合、機密データへのアクセスを制限するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="55c33-115">Write-only properties are rare and are most commonly used to restrict access to sensitive data.</span></span>

- <span data-ttu-id="55c33-116">カスタムのアクセサー コードを必要としない単純なプロパティは、式本体の定義として、または[自動実装プロパティ](./auto-implemented-properties.md)として実装できます。</span><span class="sxs-lookup"><span data-stu-id="55c33-116">Simple properties that require no custom accessor code can be implemented either as expression body definitions or as [auto-implemented properties](./auto-implemented-properties.md).</span></span>

## <a name="properties-with-backing-fields"></a><span data-ttu-id="55c33-117">バッキング フィールドを持つプロパティ</span><span class="sxs-lookup"><span data-stu-id="55c33-117">Properties with backing fields</span></span>

<span data-ttu-id="55c33-118">プロパティを実装する基本的な手法の 1 つとして、プロパティ値の設定と取得にプライベート バッキング フィールドを使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="55c33-118">One basic pattern for implementing a property involves using a private backing field for setting and retrieving the property value.</span></span> <span data-ttu-id="55c33-119">この方法では、`get` アクセサーはプライベート フィールドの値を返します。`set` アクセサーはプライベート フィールドに値を割り当てる前にデータ検証を実行できます。</span><span class="sxs-lookup"><span data-stu-id="55c33-119">The `get` accessor returns the value of the private field, and the `set` accessor may perform some data validation before assigning a value to the private field.</span></span> <span data-ttu-id="55c33-120">また、どちらのアクセサーも、データの変換や計算を行ってから、データを格納したり返したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="55c33-120">Both accessors may also perform some conversion or computation on the data before it is stored or returned.</span></span>

<span data-ttu-id="55c33-121">このパターンを説明する例を下に示します。</span><span class="sxs-lookup"><span data-stu-id="55c33-121">The following example illustrates this pattern.</span></span> <span data-ttu-id="55c33-122">この例では、`TimePeriod` クラスは時間間隔を表しています。</span><span class="sxs-lookup"><span data-stu-id="55c33-122">In this example, the `TimePeriod` class represents an interval of time.</span></span> <span data-ttu-id="55c33-123">クラスの内部では、`_seconds` という名前のプライベート フィールドに時間間隔が秒単位で格納されます。</span><span class="sxs-lookup"><span data-stu-id="55c33-123">Internally, the class stores the time interval in seconds in a private field named `_seconds`.</span></span> <span data-ttu-id="55c33-124">`Hours` という読み取り/書き込みプロパティでは、ユーザーが時間間隔を時間単位で指定できます。</span><span class="sxs-lookup"><span data-stu-id="55c33-124">A read-write property named `Hours` allows the customer to specify the time interval in hours.</span></span> <span data-ttu-id="55c33-125">`get` アクセサーと `set` アクセサーの両方で、必要に応じて時間と秒の変換が実行されます。</span><span class="sxs-lookup"><span data-stu-id="55c33-125">Both the `get` and the `set` accessors perform the necessary conversion between hours and seconds.</span></span> <span data-ttu-id="55c33-126">また、`set` アクセサーは、データを検証し、時間数が無効である場合に <xref:System.ArgumentOutOfRangeException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="55c33-126">In addition, the `set` accessor validates the data and throws an <xref:System.ArgumentOutOfRangeException> if the number of hours is invalid.</span></span>

 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="55c33-127">式本体の定義</span><span class="sxs-lookup"><span data-stu-id="55c33-127">Expression body definitions</span></span>  

 <span data-ttu-id="55c33-128">プロパティ アクセサーは、通常、式の結果を割り当てるか返すだけの 1 行のステートメントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="55c33-128">Property accessors often consist of single-line statements that just assign or return the result of an expression.</span></span> <span data-ttu-id="55c33-129">プロパティは、本体が式形式のメンバーとして実装できます。</span><span class="sxs-lookup"><span data-stu-id="55c33-129">You can implement these properties as expression-bodied members.</span></span> <span data-ttu-id="55c33-130">式本体の定義は、`=>` 記号の後に、プロパティに割り当てるかプロパティから取得するための式を続けて構成します。</span><span class="sxs-lookup"><span data-stu-id="55c33-130">Expression body definitions consist of the `=>` symbol followed by the expression to assign to or retrieve from the property.</span></span>

 <span data-ttu-id="55c33-131">C# 6 以降では、読み取り専用プロパティに `get` アクセサーを式形式のメンバーとして実装できます。</span><span class="sxs-lookup"><span data-stu-id="55c33-131">Starting with C# 6, read-only properties can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="55c33-132">この場合、`get` アクセサー キーワードと `return` キーワードはどちらも使用しません。</span><span class="sxs-lookup"><span data-stu-id="55c33-132">In this case, neither the `get` accessor keyword nor the `return` keyword is used.</span></span> <span data-ttu-id="55c33-133">次の例では、読み取り専用 `Name` プロパティを式形式のメンバーとして実装しています。</span><span class="sxs-lookup"><span data-stu-id="55c33-133">The following example implements the read-only `Name` property as an expression-bodied member.</span></span>

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 <span data-ttu-id="55c33-134">C# 7.0 以降では、`get` アクセサーと `set` アクセサーのどちらも、式形式のメンバーとして実装できます。</span><span class="sxs-lookup"><span data-stu-id="55c33-134">Starting with C# 7.0, both the `get` and the `set` accessor can be implemented as expression-bodied members.</span></span> <span data-ttu-id="55c33-135">この場合、`get` キーワードと `set` キーワードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55c33-135">In this case, the `get` and `set` keywords must be present.</span></span> <span data-ttu-id="55c33-136">両方のアクセサーに式本体の定義を使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="55c33-136">The following example illustrates the use of expression body definitions for both accessors.</span></span> <span data-ttu-id="55c33-137">`get` アクセサーで `return` キーワードが使用されていない点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="55c33-137">Note that the `return` keyword is not used with the `get` accessor.</span></span>

  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a><span data-ttu-id="55c33-138">自動実装プロパティ</span><span class="sxs-lookup"><span data-stu-id="55c33-138">Auto-implemented properties</span></span>

<span data-ttu-id="55c33-139">ロジックを追加しなくても、プロパティの `get` アクセサーと `set` アクセサーはバッキング フィールドに値を割り当てたりバッキング フィールドから取得したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="55c33-139">In some cases, property `get` and `set` accessors just assign a value to or retrieve a value from a backing field without including any additional logic.</span></span> <span data-ttu-id="55c33-140">この自動実装プロパティを使用すると、C# コンパイラによってバッキング フィールドが透過的に提供されるため、コードを簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="55c33-140">By using auto-implemented properties, you can simplify your code while having the C# compiler transparently provide the backing field for you.</span></span>

<span data-ttu-id="55c33-141">プロパティに `get` と `set` (または `get` と `init`) の両方のアクセサーがある場合は、どちらも自動実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55c33-141">If a property has both a `get` and a `set` (or a `get` and an `init`) accessor, both must be auto-implemented.</span></span> <span data-ttu-id="55c33-142">自動実装プロパティを定義するには、実装を省略して `get` キーワードと `set` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="55c33-142">You define an auto-implemented property by using the `get` and `set` keywords without providing any implementation.</span></span> <span data-ttu-id="55c33-143">次の例は前の例と似ていますが、`Name` と `Price` が自動実装プロパティである点が異なります。</span><span class="sxs-lookup"><span data-stu-id="55c33-143">The following example repeats the previous one, except that `Name` and `Price` are auto-implemented properties.</span></span> <span data-ttu-id="55c33-144">この例では、パラメーター化されたコンストラクターも削除されているため、`SaleItem` オブジェクトがパラメーターなしのコンストラクターの呼び出しと[オブジェクト初期化子](object-and-collection-initializers.md)を使用して初期化されています。</span><span class="sxs-lookup"><span data-stu-id="55c33-144">The example also removes the parameterized constructor, so that `SaleItem` objects are now initialized with a call to the parameterless constructor and an [object initializer](object-and-collection-initializers.md).</span></span>

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a><span data-ttu-id="55c33-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="55c33-145">Related sections</span></span>  
  
- [<span data-ttu-id="55c33-146">プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="55c33-146">Using Properties</span></span>](./using-properties.md)  
  
- [<span data-ttu-id="55c33-147">インターフェイスのプロパティ</span><span class="sxs-lookup"><span data-stu-id="55c33-147">Interface Properties</span></span>](./interface-properties.md)  
  
- [<span data-ttu-id="55c33-148">プロパティとインデクサーの比較</span><span class="sxs-lookup"><span data-stu-id="55c33-148">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="55c33-149">アクセサーのアクセシビリティの制限</span><span class="sxs-lookup"><span data-stu-id="55c33-149">Restricting Accessor Accessibility</span></span>](./restricting-accessor-accessibility.md)  
  
- [<span data-ttu-id="55c33-150">自動実装プロパティ</span><span class="sxs-lookup"><span data-stu-id="55c33-150">Auto-Implemented Properties</span></span>](./auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="55c33-151">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="55c33-151">C# Language Specification</span></span>  

<span data-ttu-id="55c33-152">詳細については、「[C# 言語の仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の[プロパティ](~/_csharplang/spec/classes.md#properties)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="55c33-152">For more information, see [Properties](~/_csharplang/spec/classes.md#properties) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="55c33-153">言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。</span><span class="sxs-lookup"><span data-stu-id="55c33-153">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="55c33-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="55c33-154">See also</span></span>

- [<span data-ttu-id="55c33-155">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="55c33-155">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="55c33-156">プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="55c33-156">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="55c33-157">インデクサー</span><span class="sxs-lookup"><span data-stu-id="55c33-157">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="55c33-158">get キーワード</span><span class="sxs-lookup"><span data-stu-id="55c33-158">get keyword</span></span>](../../language-reference/keywords/get.md)
- [<span data-ttu-id="55c33-159">set キーワード</span><span class="sxs-lookup"><span data-stu-id="55c33-159">set keyword</span></span>](../../language-reference/keywords/set.md)
