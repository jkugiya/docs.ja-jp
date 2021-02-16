---
description: '詳細情報: 拡張メソッド (Visual Basic)'
title: 拡張メソッド
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: 5a1482502b144524c0be90e1c83a38f49b4a4d26
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434356"
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="7fd51-103">拡張メソッド (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fd51-103">Extension Methods (Visual Basic)</span></span>

<span data-ttu-id="7fd51-104">拡張メソッドを使用すると、新しい派生型を作成しなくても、既に定義されているデータ型にカスタム機能を追加することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="7fd51-104">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="7fd51-105">拡張メソッドの機能によって、既存の型のインスタンス メソッドを呼び出す場合と同じ要領で呼び出せるメソッドを作成できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="7fd51-105">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>

## <a name="remarks"></a><span data-ttu-id="7fd51-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="7fd51-106">Remarks</span></span>

<span data-ttu-id="7fd51-107">拡張メソッドになるのは、`Sub` プロシージャと `Function` プロシージャだけです。</span><span class="sxs-lookup"><span data-stu-id="7fd51-107">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="7fd51-108">拡張プロパティ、拡張フィールド、拡張イベントを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="7fd51-108">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="7fd51-109">すべての拡張メソッドは <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 名前空間の拡張属性 `<Extension>` を使用してマークし、[Module](../../../language-reference/statements/module-statement.md) 内で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7fd51-109">All extension methods must be marked with the extension attribute `<Extension>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace and must be defined in a [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="7fd51-110">拡張メソッドが module の外部で定義されている場合、Visual Basic コンパイラからはエラー [BC36551](../../../misc/bc36551.md)、"拡張メソッドはモジュール内でのみ定義できます" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-110">If an extension method is defined outside a module, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules".</span></span>

<span data-ttu-id="7fd51-111">拡張メソッド定義の最初のパラメーターでは、そのメソッドが拡張するデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="7fd51-111">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="7fd51-112">メソッドが実行されると、最初のパラメーターは、そのメソッドを呼び出すデータ型のインスタンスにバインディングされます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-112">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>

<span data-ttu-id="7fd51-113">`Extension` 属性は、Visual Basic の [`Module`](../../../language-reference/statements/module-statement.md)、[`Sub`](../../../language-reference/statements/sub-statement.md)、または [`Function`](../../../language-reference/statements/function-statement.md) にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-113">The `Extension` attribute can only be applied to a Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md), or [`Function`](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="7fd51-114">これを `Class` または `Structure` に適用すると、Visual Basic コンパイラによってエラー [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md)、"'Extension' 属性は 'Module'、'Sub'、または 'Function' の各宣言にのみ適用できます" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-114">If you apply it to a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), "'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations".</span></span>

## <a name="example"></a><span data-ttu-id="7fd51-115">例</span><span class="sxs-lookup"><span data-stu-id="7fd51-115">Example</span></span>

<span data-ttu-id="7fd51-116">`Print` データ型の <xref:System.String> 拡張を定義する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7fd51-116">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="7fd51-117">このメソッドでは、`Console.WriteLine` を使用して文字列を表示します。</span><span class="sxs-lookup"><span data-stu-id="7fd51-117">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="7fd51-118">`Print` メソッドのパラメーター `aString` では、このメソッドによって <xref:System.String> クラスを拡張することを指定します。</span><span class="sxs-lookup"><span data-stu-id="7fd51-118">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>

[!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]

<span data-ttu-id="7fd51-119">拡張メソッド定義に拡張属性 `<Extension()>` を設定している点に注目してください。</span><span class="sxs-lookup"><span data-stu-id="7fd51-119">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="7fd51-120">メソッドが定義されているモジュールに拡張属性を設定するかどうかは任意ですが、それぞれの拡張メソッドにはこの設定が必要です。</span><span class="sxs-lookup"><span data-stu-id="7fd51-120">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="7fd51-121">拡張属性にアクセスするためには、<xref:System.Runtime.CompilerServices> をインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7fd51-121"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>

<span data-ttu-id="7fd51-122">拡張メソッドはモジュール内でのみ宣言できます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-122">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="7fd51-123">通常、拡張メソッドを定義するモジュールと拡張メソッドを呼び出すモジュールは、別々になります。</span><span class="sxs-lookup"><span data-stu-id="7fd51-123">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="7fd51-124">必要に応じて、拡張メソッドが含まれているモジュールをインポートすることによって、そのモジュールをスコープの中に入れます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-124">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="7fd51-125">`Print` が含まれているモジュールをスコープの中に入れたら、引数を使用しない通常のインスタンス メソッド (`ToUpper` など) の場合と同じ要領でそのメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-125">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>

[!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]

<span data-ttu-id="7fd51-126">次に取り上げる `PrintAndPunctuate` の例も <xref:System.String> の拡張ですが、今回は 2 つのパラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="7fd51-126">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="7fd51-127">最初のパラメーター `aString` では、この拡張メソッドによって <xref:System.String> を拡張することを指定します。</span><span class="sxs-lookup"><span data-stu-id="7fd51-127">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="7fd51-128">2 番目のパラメーター `punc` では、メソッドの呼び出し時に引数として渡す区切り記号の文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="7fd51-128">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="7fd51-129">このメソッドでは、文字列の後にその区切り記号を表示します。</span><span class="sxs-lookup"><span data-stu-id="7fd51-129">The method displays the string followed by the punctuation marks.</span></span>

[!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]

<span data-ttu-id="7fd51-130">このメソッドを呼び出すときには、`punc` の引数として `example.PrintAndPunctuate(".")` を渡します。</span><span class="sxs-lookup"><span data-stu-id="7fd51-130">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>

<span data-ttu-id="7fd51-131">`Print` と `PrintAndPunctuate` を定義して呼び出す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7fd51-131">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="7fd51-132">拡張属性にアクセスできるようにするために、<xref:System.Runtime.CompilerServices> が定義モジュールにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-132"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions

    <Extension()>
    Public Sub Print(aString As String)
        Console.WriteLine(aString)
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module
```

<span data-ttu-id="7fd51-133">次に、拡張メソッドをスコープの中に取り込んで呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7fd51-133">Next, the extension methods are brought into scope and called:</span></span>

```vb
Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example As String = "Example string"
        example.Print()

        example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")
    End Sub
End Module
```

<span data-ttu-id="7fd51-134">このような拡張メソッドを実行するための唯一の要件は、その拡張メソッドをスコープの中に組み入れておくことです。</span><span class="sxs-lookup"><span data-stu-id="7fd51-134">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="7fd51-135">拡張メソッドが含まれているモジュールがスコープの中に入っていれば、その拡張メソッドは IntelliSense からアクセスできるということであり、通常のインスタンス メソッドの場合と同じ要領で呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-135">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>

<span data-ttu-id="7fd51-136">メソッドを呼び出すときに、最初のパラメーターの引数を渡していない点に注目してください。</span><span class="sxs-lookup"><span data-stu-id="7fd51-136">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="7fd51-137">前のメソッド定義のパラメーター `aString` が、メソッドを呼び出す `example` のインスタンスである `String` にバインディングされています。</span><span class="sxs-lookup"><span data-stu-id="7fd51-137">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="7fd51-138">コンパイラは、最初のパラメーターに渡す引数としてその `example` を使用します。</span><span class="sxs-lookup"><span data-stu-id="7fd51-138">The compiler will use `example` as the argument sent to the first parameter.</span></span>

<span data-ttu-id="7fd51-139">`Nothing` に設定されたオブジェクトに対して拡張メソッドが呼び出された場合、その拡張メソッドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-139">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="7fd51-140">これは、通常のインスタンス メソッドには適用されません。</span><span class="sxs-lookup"><span data-stu-id="7fd51-140">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="7fd51-141">拡張メソッドの `Nothing` は明示的にチェックできます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-141">You can explicitly check for `Nothing` in the extension method.</span></span>

## <a name="types-that-can-be-extended"></a><span data-ttu-id="7fd51-142">拡張可能な型</span><span class="sxs-lookup"><span data-stu-id="7fd51-142">Types that can be extended</span></span>

<span data-ttu-id="7fd51-143">拡張メソッドは、Visual Basic のパラメーター リストで記述できるほとんどの型で定義できます。以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="7fd51-143">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>

- <span data-ttu-id="7fd51-144">クラス (参照型)</span><span class="sxs-lookup"><span data-stu-id="7fd51-144">Classes (reference types)</span></span>
- <span data-ttu-id="7fd51-145">構造体 (値型)</span><span class="sxs-lookup"><span data-stu-id="7fd51-145">Structures (value types)</span></span>
- <span data-ttu-id="7fd51-146">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7fd51-146">Interfaces</span></span>
- <span data-ttu-id="7fd51-147">デリゲート</span><span class="sxs-lookup"><span data-stu-id="7fd51-147">Delegates</span></span>
- <span data-ttu-id="7fd51-148">ByRef 引数と ByVal 引数</span><span class="sxs-lookup"><span data-stu-id="7fd51-148">ByRef and ByVal arguments</span></span>
- <span data-ttu-id="7fd51-149">ジェネリック メソッド パラメーター</span><span class="sxs-lookup"><span data-stu-id="7fd51-149">Generic method parameters</span></span>
- <span data-ttu-id="7fd51-150">配列</span><span class="sxs-lookup"><span data-stu-id="7fd51-150">Arrays</span></span>

<span data-ttu-id="7fd51-151">最初のパラメーターでは、メソッドによって拡張するデータ型を指定するので、最初のパラメーターは必須であり、任意指定にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="7fd51-151">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="7fd51-152">したがって、パラメーター リストの最初のパラメーターとして、`Optional` パラメーターと `ParamArray` パラメーターを記述することはできません。</span><span class="sxs-lookup"><span data-stu-id="7fd51-152">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>

<span data-ttu-id="7fd51-153">拡張メソッドは遅延バインディングでは考慮されません。</span><span class="sxs-lookup"><span data-stu-id="7fd51-153">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="7fd51-154">次の例では、`anObject.PrintMe()` ステートメントで <xref:System.MissingMemberException> 例外が発生します。これは、2 番目の `PrintMe` 拡張メソッド定義を削除した場合に発生する例外と同じです。</span><span class="sxs-lookup"><span data-stu-id="7fd51-154">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>

[!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]

## <a name="best-practices"></a><span data-ttu-id="7fd51-155">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="7fd51-155">Best practices</span></span>

<span data-ttu-id="7fd51-156">拡張メソッドは、既存の型を拡張するための便利で強力な手段になります。</span><span class="sxs-lookup"><span data-stu-id="7fd51-156">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="7fd51-157">それでも、適切に使用するにはいくつかの注意点があります。</span><span class="sxs-lookup"><span data-stu-id="7fd51-157">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="7fd51-158">ここで取り上げる注意点は、主にクラス ライブラリを作成するときに当てはまりますが、拡張メソッドを使用するアプリケーションであればどんなアプリケーションにも影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7fd51-158">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>

<span data-ttu-id="7fd51-159">一般的に、自分で所有していない型に追加した拡張メソッドは、自分で制御できる型に追加した拡張メソッドよりも脆弱になります。</span><span class="sxs-lookup"><span data-stu-id="7fd51-159">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="7fd51-160">自分で所有していないクラスでは、拡張メソッドの動作に影響を及ぼしかねない事柄がいくつか発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7fd51-160">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>

- <span data-ttu-id="7fd51-161">呼び出し元ステートメントの引数との互換性があるシグネチャを持ったアクセス可能なインスタンス メンバーが存在し、引数からパラメーターへの縮小変換が不要な場合は、拡張メソッドよりもそのインスタンス メソッドの方が優先的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-161">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="7fd51-162">したがって、該当するインスタンス メソッドがいずれかの時点でクラスに追加されると、使用しなければならない既存の拡張メソッドにアクセスできなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7fd51-162">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>

- <span data-ttu-id="7fd51-163">拡張メソッドの作成者の側では、その拡張メソッドよりも優先的に使用される可能性がある別の拡張メソッドを他のプログラマが作成する、という事態を防止できません。</span><span class="sxs-lookup"><span data-stu-id="7fd51-163">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>

- <span data-ttu-id="7fd51-164">拡張メソッドをそれ自身の名前空間に入れておけば、拡張メソッドの信頼性が向上します。</span><span class="sxs-lookup"><span data-stu-id="7fd51-164">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="7fd51-165">ライブラリを利用する側では、ライブラリの名前空間とそれ以外の部分を分けて、名前空間を組み込んだり除外したり取捨選択したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-165">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>

- <span data-ttu-id="7fd51-166">クラスを拡張するよりもインターフェイスを拡張する方が安全です。インターフェイスまたはクラスを自分で所有していない場合は特にそういえます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-166">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="7fd51-167">インターフェイスが変更されると、そのインターフェイスを実装するすべてのクラスが影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-167">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="7fd51-168">したがって、インターフェイスでメソッドが追加されたり変更されたりする可能性の方が低いといえます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-168">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="7fd51-169">ただし、クラスが同じシグニチャの拡張メソッドを持つ 2 つのインターフェイスを実装する場合、どちらの拡張メソッドにもアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="7fd51-169">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>

- <span data-ttu-id="7fd51-170">できるだけ具体性の高い型を拡張するようにします。</span><span class="sxs-lookup"><span data-stu-id="7fd51-170">Extend the most specific type you can.</span></span> <span data-ttu-id="7fd51-171">型の階層の中で他の多くの型の派生元になっている型で拡張メソッドを選択すると、その拡張メソッドの動作に影響を及ぼしかねないインスタンス メソッドや他の拡張メソッドが組み込まれる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="7fd51-171">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>

## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="7fd51-172">拡張メソッド、インスタンス メソッド、およびプロパティ</span><span class="sxs-lookup"><span data-stu-id="7fd51-172">Extension methods, instance methods, and properties</span></span>

<span data-ttu-id="7fd51-173">スコープ内のインスタンス メソッドが、呼び出し元ステートメントの引数と互換性があるシグネチャを持っている場合、拡張メソッドよりもそのインスタンス メソッドの方が優先的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-173">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="7fd51-174">この場合、より適合する拡張メソッドがあっても、インスタンス メソッドの方が優先されます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-174">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="7fd51-175">次の例では、`ExampleClass` に、`ExampleMethod` 型のパラメーターを 1 つ持つ `Integer` という名前のインスタンス メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7fd51-175">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="7fd51-176">拡張メソッド `ExampleMethod` は `ExampleClass` を拡張し、`Long` 型のパラメーターを 1 つ持ちます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-176">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>

[!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]

<span data-ttu-id="7fd51-177">次のコードでは、`ExampleMethod` の最初の呼び出しで、拡張メソッドが呼び出されます。これは、`arg1` が `Long` であり、拡張メソッドの `Long` パラメーターとのみ互換性があるためです。</span><span class="sxs-lookup"><span data-stu-id="7fd51-177">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="7fd51-178">`ExampleMethod` の 2 回目の呼び出しでは、`Integer` 引数 `arg2` があるため、インスタンス メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-178">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>

[!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]

<span data-ttu-id="7fd51-179">次は、2 つのメソッド間でパラメーターのデータ型が逆になっています。</span><span class="sxs-lookup"><span data-stu-id="7fd51-179">Now reverse the data types of the parameters in the two methods:</span></span>

[!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]

<span data-ttu-id="7fd51-180">今回は、`Main` 内のコードはどちらの場合でもインスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7fd51-180">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="7fd51-181">これは、`arg1` と `arg2` は `Long` へ拡大変換され、どちらの場合でも拡張メソッドよりインスタンス メソッドの方が優先されるためです。</span><span class="sxs-lookup"><span data-stu-id="7fd51-181">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>

[!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]

<span data-ttu-id="7fd51-182">つまり、既存のインスタンス メソッドの代わりに拡張メソッドを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="7fd51-182">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="7fd51-183">ただし、拡張メソッドとインスタンス メソッドの名前が同じでもシグネチャが競合しない場合は、両方のメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-183">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="7fd51-184">たとえば、クラス `ExampleClass` に引数を使用しない `ExampleMethod` という名前のメソッドがあるとします。拡張メソッドの名前がそのメソッドと同じでもシグネチャが違えば、その拡張メソッドを使用することは可能です。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="7fd51-184">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>

[!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]

<span data-ttu-id="7fd51-185">このコードの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7fd51-185">The output from this code is as follows:</span></span>

```console
Extension method
Instance method
```

<span data-ttu-id="7fd51-186">プロパティの場合、状況はより単純です。拡張メソッドの名前がそのクラスのプロパティと同じである場合、その拡張メソッドは非表示になり、アクセスできません。</span><span class="sxs-lookup"><span data-stu-id="7fd51-186">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>

## <a name="extension-method-precedence"></a><span data-ttu-id="7fd51-187">拡張メソッドの優先順位</span><span class="sxs-lookup"><span data-stu-id="7fd51-187">Extension method precedence</span></span>

<span data-ttu-id="7fd51-188">2 つの拡張メソッドのシグネチャが同じで、そのいずれもスコープに入っていてアクセスが可能な場合は、優先順位の高い方が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-188">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="7fd51-189">拡張メソッドの優先順位は、メソッドをスコープに組み入れる方法に基づいています。</span><span class="sxs-lookup"><span data-stu-id="7fd51-189">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="7fd51-190">優先順位の高い方から低い方へと並べると、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7fd51-190">The following list shows the precedence hierarchy, from highest to lowest.</span></span>

1. <span data-ttu-id="7fd51-191">現在のモジュールの中で定義されている拡張メソッド。</span><span class="sxs-lookup"><span data-stu-id="7fd51-191">Extension methods defined inside the current module.</span></span>

2. <span data-ttu-id="7fd51-192">現在の名前空間の方がその親に相当する名前空間よりも優先順位が高ければ、現在の名前空間またはそのいずれかの親に相当する名前空間にあるデータ型の中で定義されている拡張メソッド。</span><span class="sxs-lookup"><span data-stu-id="7fd51-192">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>

3. <span data-ttu-id="7fd51-193">現在のファイルの型インポートの中で定義されている拡張メソッド。</span><span class="sxs-lookup"><span data-stu-id="7fd51-193">Extension methods defined inside any type imports in the current file.</span></span>

4. <span data-ttu-id="7fd51-194">現在のファイルの名前空間インポートの中で定義されている拡張メソッド。</span><span class="sxs-lookup"><span data-stu-id="7fd51-194">Extension methods defined inside any namespace imports in the current file.</span></span>

5. <span data-ttu-id="7fd51-195">プロジェクト レベルの型インポートの中で定義されている拡張メソッド。</span><span class="sxs-lookup"><span data-stu-id="7fd51-195">Extension methods defined inside any project-level type imports.</span></span>

6. <span data-ttu-id="7fd51-196">プロジェクト レベルの名前空間インポートの中で定義されている拡張メソッド。</span><span class="sxs-lookup"><span data-stu-id="7fd51-196">Extension methods defined inside any project-level namespace imports.</span></span>

<span data-ttu-id="7fd51-197">優先順位を適用してもあいまいさが残る場合は、完全修飾名を使用して、呼び出すメソッドを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7fd51-197">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="7fd51-198">先ほどの例の `Print` メソッドが `StringExtensions` という名前のモジュールで定義されていれば、完全修飾名は `StringExtensions.Print(example)` ではなく `example.Print()` になります。</span><span class="sxs-lookup"><span data-stu-id="7fd51-198">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>

## <a name="see-also"></a><span data-ttu-id="7fd51-199">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fd51-199">See also</span></span>

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="7fd51-200">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="7fd51-200">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="7fd51-201">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="7fd51-201">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="7fd51-202">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="7fd51-202">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="7fd51-203">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="7fd51-203">Optional Parameters</span></span>](optional-parameters.md)
- [<span data-ttu-id="7fd51-204">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="7fd51-204">Parameter Arrays</span></span>](parameter-arrays.md)
- [<span data-ttu-id="7fd51-205">属性の概要</span><span class="sxs-lookup"><span data-stu-id="7fd51-205">Attributes overview</span></span>](../../concepts/attributes/index.md)
- [<span data-ttu-id="7fd51-206">Visual Basic におけるスコープ</span><span class="sxs-lookup"><span data-stu-id="7fd51-206">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
