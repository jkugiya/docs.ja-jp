---
description: '詳細情報: 方法:拡張メソッドを作成する (Visual Basic)'
title: '方法: 拡張メソッドを作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 4c5d88976e55288ccb350ab82d459db0a23f468e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476190"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="9a3ff-103">方法: 拡張メソッドを作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a3ff-103">How to: Write an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="9a3ff-104">拡張メソッドを使用すると、既存のクラスにメソッドを追加できます。</span><span class="sxs-lookup"><span data-stu-id="9a3ff-104">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="9a3ff-105">拡張メソッドは、そのクラスのインスタンスであるかのように呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="9a3ff-105">The extension method can be called as if it were an instance of that class.</span></span>

### <a name="to-define-an-extension-method"></a><span data-ttu-id="9a3ff-106">拡張メソッドを定義するには</span><span class="sxs-lookup"><span data-stu-id="9a3ff-106">To define an extension method</span></span>

1. <span data-ttu-id="9a3ff-107">Visual Studio で、新規または既存の Visual Basic アプリケーションを開きます。</span><span class="sxs-lookup"><span data-stu-id="9a3ff-107">Open a new or existing Visual Basic application in Visual Studio.</span></span>

2. <span data-ttu-id="9a3ff-108">拡張メソッドを定義するファイルの先頭に、次のインポート ステートメントを含めます。</span><span class="sxs-lookup"><span data-stu-id="9a3ff-108">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. <span data-ttu-id="9a3ff-109">新規または既存のアプリケーションのモジュール内で、メソッド定義を [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) 属性で開始します。</span><span class="sxs-lookup"><span data-stu-id="9a3ff-109">Within a module in your new or existing application, begin the method definition with the [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) attribute:</span></span>

    ```vb
    <Extension()>
    ```

    <span data-ttu-id="9a3ff-110">`Extension` 属性は、Visual Basic の [Module](../../../language-reference/statements/module-statement.md) 内のメソッド (`Sub` または `Function` プロシージャ) にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="9a3ff-110">Note that the `Extension` attribute can only be applied to a method (a `Sub` or `Function` procedure) in a Visual Basic [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="9a3ff-111">`Class` または `Structure` 内のメソッドに適用すると、Visual Basic コンパイラは、エラー [BC36551](../../../misc/bc36551.md) "Extension methods can be defined only in modules\(拡張メソッドはモジュール内でのみ定義できます\)" を生成します。</span><span class="sxs-lookup"><span data-stu-id="9a3ff-111">If you apply it to a method in a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules."</span></span>

4. <span data-ttu-id="9a3ff-112">通常の方法でメソッドを宣言します。ただし、最初のパラメーターの型は、拡張するデータ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a3ff-112">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a><span data-ttu-id="9a3ff-113">例</span><span class="sxs-lookup"><span data-stu-id="9a3ff-113">Example</span></span>

<span data-ttu-id="9a3ff-114">次の例では、モジュール `StringExtensions` で拡張メソッドを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="9a3ff-114">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="9a3ff-115">2 番目のモジュール `Module1` は、`StringExtensions` をインポートし、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9a3ff-115">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="9a3ff-116">拡張メソッドは、呼び出されるときのスコープ内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a3ff-116">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="9a3ff-117">拡張メソッド `PrintAndPunctuate` は、文字列インスタンスを表示し、その後にパラメーターとして送信された句読記号の文字列を表示するメソッドで <xref:System.String> クラスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="9a3ff-117">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>

```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

```vb
' Import the module that holds the extension method you want to use,
' and call it.

Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example = "Hello"
        example.PrintAndPunctuate("?")
        example.PrintAndPunctuate("!!!!")
    End Sub

End Module
```

<span data-ttu-id="9a3ff-118">このメソッドは 2 つのパラメーターで定義され、その 1 つでのみ呼び出されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9a3ff-118">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="9a3ff-119">メソッド定義の最初のパラメーターである `aString` は、メソッドを呼び出す `String` のインスタンスである `example` にバインドされています。</span><span class="sxs-lookup"><span data-stu-id="9a3ff-119">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="9a3ff-120">この例の出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9a3ff-120">The output of the example is as follows:</span></span>

```console
Hello?
Hello!!!!
```

## <a name="see-also"></a><span data-ttu-id="9a3ff-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a3ff-121">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="9a3ff-122">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="9a3ff-122">Extension Methods</span></span>](extension-methods.md)
- [<span data-ttu-id="9a3ff-123">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="9a3ff-123">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="9a3ff-124">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="9a3ff-124">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="9a3ff-125">Visual Basic におけるスコープ</span><span class="sxs-lookup"><span data-stu-id="9a3ff-125">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
