---
description: '詳細情報: パラメーターのデザイン'
title: パラメーターのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
ms.openlocfilehash: 9663ef8146054985374fdb3e2974fcd996fd1402
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731826"
---
# <a name="parameter-design"></a><span data-ttu-id="5eedb-103">パラメーターのデザイン</span><span class="sxs-lookup"><span data-stu-id="5eedb-103">Parameter Design</span></span>

<span data-ttu-id="5eedb-104">このセクションでは、引数のチェックに関するガイドラインなど、パラメーターの設計に関する広範なガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="5eedb-104">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="5eedb-105">また、「[パラメーターに名前を付ける](naming-parameters.md)」で説明されているガイドラインも参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-105">In addition, you should refer to the guidelines described in [Naming Parameters](naming-parameters.md).</span></span>

 <span data-ttu-id="5eedb-106">✔️ メンバーで必要とされる機能を提供する最小限の派生のパラメーター型を使用します。</span><span class="sxs-lookup"><span data-stu-id="5eedb-106">✔️ DO use the least derived parameter type that provides the functionality required by the member.</span></span>

 <span data-ttu-id="5eedb-107">たとえば、コレクションを列挙して、各項目をコンソールに出力するメソッドを設計するとします。</span><span class="sxs-lookup"><span data-stu-id="5eedb-107">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="5eedb-108">このようなメソッドは、たとえば <xref:System.Collections.ArrayList> や <xref:System.Collections.IList> ではなく、<xref:System.Collections.IEnumerable> をパラメーターとして受け取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="5eedb-108">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>

 <span data-ttu-id="5eedb-109">❌ 予約済みのパラメーターは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-109">❌ DO NOT use reserved parameters.</span></span>

 <span data-ttu-id="5eedb-110">将来のバージョンでメンバーへの入力を増やす必要がある場合は、新しいオーバーロードを追加できます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-110">If more input to a member is needed in some future version, a new overload can be added.</span></span>

 <span data-ttu-id="5eedb-111">❌ パラメーターとしてポインター、ポインターの配列、または多次元配列を受け取る、パブリックに公開されたメソッドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-111">❌ DO NOT have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>

 <span data-ttu-id="5eedb-112">ポインターと多次元配列は、適切に使用するのが比較的困難です。</span><span class="sxs-lookup"><span data-stu-id="5eedb-112">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="5eedb-113">ほとんどの場合、これらの型をパラメーターとして受け取らないように、API を再設計することができます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-113">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>

 <span data-ttu-id="5eedb-114">✔️ オーバーロードの間でパラメーターの順序に不一致が発生するようになっても (「[メンバーのオーバーロード](member-overloading.md)」を参照)、すべての `out` パラメーターを、値渡しおよび `ref` パラメーターの後に配置します (パラメーター配列を除きます)。</span><span class="sxs-lookup"><span data-stu-id="5eedb-114">✔️ DO place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](member-overloading.md)).</span></span>

 <span data-ttu-id="5eedb-115">`out` パラメーターは、追加の戻り値と考えることができ、これらをまとめてグループ化することで、メソッドのシグネチャがわかりやすくなります。</span><span class="sxs-lookup"><span data-stu-id="5eedb-115">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>

 <span data-ttu-id="5eedb-116">✔️ メンバーをオーバーライドするときや、インターフェイス メンバーを実装するときは、パラメーターに一貫した名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-116">✔️ DO be consistent in naming parameters when overriding members or implementing interface members.</span></span>

 <span data-ttu-id="5eedb-117">これにより、メソッド間の関係をより適切に伝えられます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-117">This better communicates the relationship between the methods.</span></span>

### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="5eedb-118">列挙型パラメーターとブール型パラメーターの選択</span><span class="sxs-lookup"><span data-stu-id="5eedb-118">Choosing Between Enum and Boolean Parameters</span></span>  

 <span data-ttu-id="5eedb-119">✔️ そうしないとメンバーに複数のブール型パラメーターが含まれるようになる場合は、列挙型を使用ます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-119">✔️ DO use enums if a member would otherwise have two or more Boolean parameters.</span></span>

 <span data-ttu-id="5eedb-120">❌ 3 つ以上の値が必要にならないことが絶対に確実である場合を除き、ブール型は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-120">❌ DO NOT use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>

 <span data-ttu-id="5eedb-121">列挙型を使用すると、後で値を追加できるようになりますが、列挙型に値を追加することによるすべての影響を把握しておく必要があります。これについては「[列挙型のデザイン](enum.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-121">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](enum.md).</span></span>

 <span data-ttu-id="5eedb-122">✔️ コンストラクターのパラメーターが間違いなく 2 つの状態の値であり、ブール型プロパティの初期化だけに使用される場合は、ブール型を使用することを検討します。</span><span class="sxs-lookup"><span data-stu-id="5eedb-122">✔️ CONSIDER using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>

### <a name="validating-arguments"></a><span data-ttu-id="5eedb-123">引数の検証</span><span class="sxs-lookup"><span data-stu-id="5eedb-123">Validating Arguments</span></span>

 <span data-ttu-id="5eedb-124">✔️ パブリック、プロテクト、または明示的に実装されるメンバーに渡される引数については、検証を行います。</span><span class="sxs-lookup"><span data-stu-id="5eedb-124">✔️ DO validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="5eedb-125">検証が失敗した場合は、<xref:System.ArgumentException?displayProperty=nameWithType> またはそのサブクラスのいずれかをスローします。</span><span class="sxs-lookup"><span data-stu-id="5eedb-125">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>

 <span data-ttu-id="5eedb-126">パブリックまたはプロテクトのメンバー自体では、実際の検証を必ずしも行う必要がないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-126">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="5eedb-127">これは、一部のプライベートまたは内部のルーチンの下位レベルで発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5eedb-127">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="5eedb-128">主要なポイントは、エンド ユーザーに公開されている領域全体で、引数をチェックすることです。</span><span class="sxs-lookup"><span data-stu-id="5eedb-128">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>

 <span data-ttu-id="5eedb-129">✔️ null 引数が渡され、メンバーが null 引数をサポートしていない場合は、<xref:System.ArgumentNullException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="5eedb-129">✔️ DO throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>

 <span data-ttu-id="5eedb-130">✔️ 列挙型パラメーターの検証を行います。</span><span class="sxs-lookup"><span data-stu-id="5eedb-130">✔️ DO validate enum parameters.</span></span>

 <span data-ttu-id="5eedb-131">列挙型引数はその列挙型によって定義されている範囲内であると仮定しないでください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-131">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="5eedb-132">CLR では、値が列挙型で定義されていない場合であっても、任意の整数値を列挙値にキャストできます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-132">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>

 <span data-ttu-id="5eedb-133">❌ 列挙範囲のチェックには <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-133">❌ DO NOT use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>

 <span data-ttu-id="5eedb-134">✔️ 変更可能な引数は検証後に変更される可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-134">✔️ DO be aware that mutable arguments might have changed after they were validated.</span></span>

 <span data-ttu-id="5eedb-135">メンバーのセキュリティが重要な場合は、コピーを作成してから、引数を検証して処理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5eedb-135">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>

### <a name="parameter-passing"></a><span data-ttu-id="5eedb-136">パラメーターの引き渡し</span><span class="sxs-lookup"><span data-stu-id="5eedb-136">Parameter Passing</span></span>

 <span data-ttu-id="5eedb-137">フレームワーク デザイナーの観点から見ると、パラメーターの主なグループには、値渡しパラメーター、`ref` パラメーター、`out` パラメーターの 3 つがあります。</span><span class="sxs-lookup"><span data-stu-id="5eedb-137">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>

 <span data-ttu-id="5eedb-138">値渡しパラメーターによって引数が渡されると、メンバーは渡された実際の引数のコピーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="5eedb-138">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="5eedb-139">引数が値型の場合は、引数のコピーがスタックに格納されます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-139">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="5eedb-140">引数が参照型の場合は、参照のコピーがスタックに格納されます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-140">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="5eedb-141">C#、VB.NET、C++ などのほとんどの一般的な CLR 言語では、値渡しのパラメーターが既定です。</span><span class="sxs-lookup"><span data-stu-id="5eedb-141">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>

 <span data-ttu-id="5eedb-142">引数が `ref` パラメーターによって渡されると、メンバーは渡された実際の引数への参照を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="5eedb-142">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="5eedb-143">引数が値型の場合は、引数への参照がスタックに格納されます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-143">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="5eedb-144">引数が参照型の場合は、参照への参照がスタックに格納されます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-144">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="5eedb-145">`Ref` パラメーターを使用すると、呼び出し元によって渡された引数を、メンバーが変更できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-145">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>

 <span data-ttu-id="5eedb-146">`Out` パラメーターは `ref` パラメーターに似ていますが、いくつか小さな違いがあります。</span><span class="sxs-lookup"><span data-stu-id="5eedb-146">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="5eedb-147">パラメーターは、最初は未割り当てと見なされ、何らかの値が割り当てられるまで、メンバー本体で読み取ることはできません。</span><span class="sxs-lookup"><span data-stu-id="5eedb-147">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="5eedb-148">また、メンバーから戻る前に、パラメーターに何らかの値を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="5eedb-148">Also, the parameter has to be assigned some value before the member returns.</span></span>

 <span data-ttu-id="5eedb-149">❌ `out` または `ref` パラメーターは使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-149">❌ AVOID using `out` or `ref` parameters.</span></span>

 <span data-ttu-id="5eedb-150">`out` または `ref` パラメーターを使用するには、ポインターの使用経験、値型と参照型の違いの理解、および複数の戻り値を持つメソッドの処理が必要になります。</span><span class="sxs-lookup"><span data-stu-id="5eedb-150">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="5eedb-151">また、`out` パラメーターと `ref` パラメーターの違いはあまり理解されていません。</span><span class="sxs-lookup"><span data-stu-id="5eedb-151">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="5eedb-152">一般的な開発者を対象にフレームワークを設計する場合、ユーザーが `out` または `ref` パラメーターの処理を習得していることは期待しないでください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-152">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>

 <span data-ttu-id="5eedb-153">❌ 参照型を参照で渡さないでください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-153">❌ DO NOT pass reference types by reference.</span></span>

 <span data-ttu-id="5eedb-154">参照のスワップに使用できるメソッドなど、ルールにはいくつかの限られた例外があります。</span><span class="sxs-lookup"><span data-stu-id="5eedb-154">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>

### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="5eedb-155">パラメーターの数が可変のメンバー</span><span class="sxs-lookup"><span data-stu-id="5eedb-155">Members with Variable Number of Parameters</span></span>

 <span data-ttu-id="5eedb-156">可変個の引数を受け取ることができるメンバーは、配列パラメーターを指定することによって表されれます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-156">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="5eedb-157">たとえば、<xref:System.String> には次のようなメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="5eedb-157">For example, <xref:System.String> provides the following method:</span></span>

```csharp
public class String {
    public static string Format(string format, object[] parameters);
}
```

 <span data-ttu-id="5eedb-158">ユーザーは、次のようにして <xref:System.String.Format%2A?displayProperty=nameWithType> メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-158">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>

 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`

 <span data-ttu-id="5eedb-159">C# の params キーワードを配列パラメーターに追加すると、パラメーターはいわゆる params 配列パラメーターに変わり、一時配列を作成するためのショートカットが提供されます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-159">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>

```csharp
public class String {
    public static string Format(string format, params object[] parameters);
}
```

 <span data-ttu-id="5eedb-160">これにより、ユーザーは配列要素を引数リストで直接渡すことによって、メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-160">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>

 `String.Format("File {0} not found in {1}",filename,directory);`

 <span data-ttu-id="5eedb-161">params キーワードは、パラメーター リストの最後のパラメーターにだけ追加できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-161">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>

 <span data-ttu-id="5eedb-162">✔️ エンド ユーザーが少数の要素を含む配列を渡すことが予想される場合は、params キーワードを配列パラメーターに追加することを検討します。</span><span class="sxs-lookup"><span data-stu-id="5eedb-162">✔️ CONSIDER adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="5eedb-163">一般的なシナリオで多くの要素が渡されることが予想される場合は、おそらくユーザーはこれらの要素をインラインで渡すことはないため、params キーワードは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="5eedb-163">If it's expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>

 <span data-ttu-id="5eedb-164">❌ 通常、呼び出し元で配列に既に入力が格納されている場合は、params 配列を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-164">❌ AVOID using params arrays if the caller would almost always have the input already in an array.</span></span>

 <span data-ttu-id="5eedb-165">たとえば、バイト配列のパラメーターを持つメンバーは、個々のバイトを渡すことで呼び出されることはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="5eedb-165">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="5eedb-166">このため、.NET Framework のバイト配列パラメーターでは、params キーワードは使用されません。</span><span class="sxs-lookup"><span data-stu-id="5eedb-166">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>

 <span data-ttu-id="5eedb-167">❌ params 配列パラメーターを受け取るメンバーによって配列が変更される場合は、params 配列を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-167">❌ DO NOT use params arrays if the array is modified by the member taking the params array parameter.</span></span>

 <span data-ttu-id="5eedb-168">多くのコンパイラでは、メンバーへの引数が呼び出しサイトで一時配列に変換され、その配列は一時オブジェクトである可能性があるため、配列に対する変更はすべて失われます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-168">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>

 <span data-ttu-id="5eedb-169">✔️ より複雑なオーバーロードでは使用できない場合でも、単純なオーバーロードでは params キーワードの使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="5eedb-169">✔️ CONSIDER using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>

 <span data-ttu-id="5eedb-170">すべてのオーバーロードではなくたとえ 1 つのオーバーロードであっても、params 配列を使用するとユーザーにとって価値があるかどうかを考えてください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-170">Ask yourself if users would value having the params array in one overload even if it wasn't in all overloads.</span></span>

 <span data-ttu-id="5eedb-171">✔️ params キーワードを使用できるように、パラメーターを並べ替えてみます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-171">✔️ DO try to order parameters to make it possible to use the params keyword.</span></span>

 <span data-ttu-id="5eedb-172">✔️ 非常にパフォーマンスが重要な API では、少数の引数を使用する呼び出しに対して、特別なオーバーロードとコード パスを提供することを検討します。</span><span class="sxs-lookup"><span data-stu-id="5eedb-172">✔️ CONSIDER providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>

 <span data-ttu-id="5eedb-173">このようにすると、API が少数の引数で呼び出される場合、配列オブジェクトを作成しなくて済むようになります。</span><span class="sxs-lookup"><span data-stu-id="5eedb-173">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="5eedb-174">配列パラメーターの単数形を使用し、数値のサフィックスを追加することによって、パラメーターの名前を作成します。</span><span class="sxs-lookup"><span data-stu-id="5eedb-174">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>

 <span data-ttu-id="5eedb-175">これは、単に配列を作成してより一般的なメソッドを呼び出すだけでなく、コードパス全体を特殊なケースにする場合にのみ実行してください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-175">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>

 <span data-ttu-id="5eedb-176">✔️ params 配列引数として null が渡される場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-176">✔️ DO be aware that null could be passed as a params array argument.</span></span>

 <span data-ttu-id="5eedb-177">処理する前に、配列が null でないことを検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5eedb-177">You should validate that the array is not null before processing.</span></span>

 <span data-ttu-id="5eedb-178">❌ `varargs` メソッドを使用しないでください。そうしないと、省略として認識されます。</span><span class="sxs-lookup"><span data-stu-id="5eedb-178">❌ DO NOT use the `varargs` methods, otherwise known as the ellipsis.</span></span>

 <span data-ttu-id="5eedb-179">C++ などの一部の CLR 言語では、`varargs` メソッドと呼ばれる変数パラメーター リストを渡すための代替規則がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5eedb-179">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="5eedb-180">この規則は、CLS に準拠していないため、フレームワークでは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-180">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>

### <a name="pointer-parameters"></a><span data-ttu-id="5eedb-181">ポインター パラメーター</span><span class="sxs-lookup"><span data-stu-id="5eedb-181">Pointer Parameters</span></span>

 <span data-ttu-id="5eedb-182">一般に、適切に設計されたマネージド コード フレームワークの公開領域で、ポインターを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="5eedb-182">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="5eedb-183">ほとんどの場合、ポインターはカプセル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5eedb-183">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="5eedb-184">ただし、相互運用性の理由からポインターが必要になることがあり、そのような場合にポインターを使用するのは適切です。</span><span class="sxs-lookup"><span data-stu-id="5eedb-184">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>

 <span data-ttu-id="5eedb-185">✔️ ポインターは CLS に準拠していないため、ポインター引数を受け取るメンバーには代替手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="5eedb-185">✔️ DO provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>

 <span data-ttu-id="5eedb-186">❌ ポインター引数の負荷の高い引数チェックは行わないでください。</span><span class="sxs-lookup"><span data-stu-id="5eedb-186">❌ AVOID doing expensive argument checking of pointer arguments.</span></span>

 <span data-ttu-id="5eedb-187">✔️ ポインターを使用するメンバーを設計するときは、ポインター関連の一般的な規則に従います。</span><span class="sxs-lookup"><span data-stu-id="5eedb-187">✔️ DO follow common pointer-related conventions when designing members with pointers.</span></span>

 <span data-ttu-id="5eedb-188">たとえば、簡単なポインター演算を使用して同じ結果を得ることができるため、開始インデックスを渡す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5eedb-188">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>

 <span data-ttu-id="5eedb-189">*Portions &copy; 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="5eedb-189">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="5eedb-190">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="5eedb-190">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="5eedb-191">関連項目</span><span class="sxs-lookup"><span data-stu-id="5eedb-191">See also</span></span>

- [<span data-ttu-id="5eedb-192">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="5eedb-192">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="5eedb-193">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="5eedb-193">Framework Design Guidelines</span></span>](index.md)
