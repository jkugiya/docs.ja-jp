---
title: Visual Studio for Mac での F# の概要
description: Visual Studio for Mac で F# を使用する方法について説明します。
ms.date: 07/03/2018
ms.openlocfilehash: d2ad24ad18bb31419b39508f2cf555c82fbe2e0b
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437989"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="3f49f-103">Visual Studio for Mac での F# の概要</span><span class="sxs-lookup"><span data-stu-id="3f49f-103">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="3f49f-104">Visual Studio for Mac IDE では F# と Visual F# のツールがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3f49f-104">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span> <span data-ttu-id="3f49f-105">[Visual Studio for Mac がインストールされている](install-fsharp.md#install-f-with-visual-studio-for-mac)ことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3f49f-105">Ensure that you have [Visual Studio for Mac installed](install-fsharp.md#install-f-with-visual-studio-for-mac).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="3f49f-106">コンソール アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="3f49f-106">Creating a console application</span></span>

<span data-ttu-id="3f49f-107">Visual Studio for Mac の最も基本的なプロジェクトの 1 つは、コンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="3f49f-107">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="3f49f-108">その方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3f49f-108">Here's how to do it.</span></span>  <span data-ttu-id="3f49f-109">Visual Studio for Mac が開いたら:</span><span class="sxs-lookup"><span data-stu-id="3f49f-109">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="3f49f-110">**[ファイル]** メニューの **[新しいソリューション]** をポイントします。</span><span class="sxs-lookup"><span data-stu-id="3f49f-110">On the **File** menu, point to **New Solution**.</span></span>

2. <span data-ttu-id="3f49f-111">[新しいプロジェクト] ダイアログには、コンソール アプリケーション用の 2 つの異なるテンプレートがあります。</span><span class="sxs-lookup"><span data-stu-id="3f49f-111">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="3f49f-112">1 つは [その他] -> [.NET] の下にあり、.NET Framework を対象としています。</span><span class="sxs-lookup"><span data-stu-id="3f49f-112">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="3f49f-113">その他のテンプレートは [.NET Core] -> [アプリ] の下にあり、.NET Core を対象としています。</span><span class="sxs-lookup"><span data-stu-id="3f49f-113">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="3f49f-114">どちらのテンプレートも、この記事の目的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-114">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="3f49f-115">コンソール アプリで、必要に応じて C# を F# に変更します。</span><span class="sxs-lookup"><span data-stu-id="3f49f-115">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="3f49f-116">**[次へ]** ボタンをクリックして先に進みます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-116">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="3f49f-117">プロジェクトに名前を付け、アプリに必要なオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="3f49f-117">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="3f49f-118">画面の端にあるプレビュー ペインに注意してください。ここには、選択したオプションに基づいて作成されるディレクトリ構造が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-118">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="3f49f-119">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f49f-119">Click **Create**.</span></span>  <span data-ttu-id="3f49f-120">これでソリューション エクスプローラーに F# プロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-120">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="3f49f-121">コードを書く</span><span class="sxs-lookup"><span data-stu-id="3f49f-121">Writing your code</span></span>

<span data-ttu-id="3f49f-122">まず、コードをいくつか記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="3f49f-122">Let's get started by writing some code first.</span></span>  <span data-ttu-id="3f49f-123">`Program.fs` ファイルが開いていることを確認し、その内容を以下に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-123">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="3f49f-124">前のコード サンプルでは、`x` という名前の入力を受け取り、それをそれ自体で乗算する関数 `square` が定義されています。</span><span class="sxs-lookup"><span data-stu-id="3f49f-124">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="3f49f-125">F# では[型の推定](../language-reference/type-inference.md)が使用されるため、`x` の型を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3f49f-125">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="3f49f-126">F# コンパイラにより、乗算が有効な型が認識され、`square` の呼び出し方法に基づいて型が `x` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-126">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="3f49f-127">マウス ポインターを `square` に合わせると、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-127">If you hover over `square`, you should see the following:</span></span>

```console
val square: x:int -> int
```

<span data-ttu-id="3f49f-128">これは、関数の型シグネチャとして知られています。</span><span class="sxs-lookup"><span data-stu-id="3f49f-128">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="3f49f-129">これは、"Square は、x という整数を受け取り、整数を生成する関数です" のように解釈できます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-129">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="3f49f-130">コンパイラによって、現段階では `square` に `int` の型が設定されたことに注意してください。これは、乗算が "*すべて*" の型に対してジェネリックではなく、閉じられた型のセット内でジェネリックであるためです。</span><span class="sxs-lookup"><span data-stu-id="3f49f-130">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="3f49f-131">この時点で F# コンパイラによって `int` が選択されますが、`float` などの別の入力型を使用して `square` を呼び出すと、型シグネチャが調整されます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-131">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="3f49f-132">`EntryPoint` 属性で装飾された別の関数 `main` が定義されています。これにより、プログラムの実行をそこから開始する必要があることが F# コンパイラに指示されます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-132">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="3f49f-133">これは、他の [C スタイルのプログラミング言語](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)と同じ規則に従います。コマンドライン引数をこの関数に渡すことができ、整数のコードが返される (通常は `0`) というものです。</span><span class="sxs-lookup"><span data-stu-id="3f49f-133">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="3f49f-134">これはこの関数内にあり、`12` の引数を指定して `square` 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3f49f-134">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="3f49f-135">次に F# コンパイラによって、`int -> int` になるように `square` の型が割り当てられます (つまり、`int` を受け取り、`int` を生成する関数)。</span><span class="sxs-lookup"><span data-stu-id="3f49f-135">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="3f49f-136">`printfn` の呼び出しは書式設定済みの印刷関数であり、C スタイルのプログラミング言語に似た書式指定文字列と、書式指定文字列で指定されたものに対応するパラメーターを使用し、結果と改行を出力します。</span><span class="sxs-lookup"><span data-stu-id="3f49f-136">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="3f49f-137">コードの実行</span><span class="sxs-lookup"><span data-stu-id="3f49f-137">Running your code</span></span>

<span data-ttu-id="3f49f-138">トップ レベル メニューの **[実行]** 、続いて **[デバッグなしで開始]** をクリックして、コードを実行し、結果を確認できます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-138">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="3f49f-139">これにより、プログラムがデバッグなしで実行され、結果を確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3f49f-139">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="3f49f-140">Visual Studio for Mac によって開かれたコンソール ウィンドウに次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-140">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```console
12 squared is 144!
```

<span data-ttu-id="3f49f-141">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="3f49f-141">Congratulations!</span></span>  <span data-ttu-id="3f49f-142">最初の F# プロジェクトを Visual Studio for Mac で作成し、その関数を呼び出した結果を出力する F# 関数を記述し、プロジェクトを実行して結果を確認しました。</span><span class="sxs-lookup"><span data-stu-id="3f49f-142">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="3f49f-143">F# インタラクティブを使用する</span><span class="sxs-lookup"><span data-stu-id="3f49f-143">Using F# Interactive</span></span>

<span data-ttu-id="3f49f-144">Visual Studio for Mac の Visual F# ツールの最も優れた機能の 1 つは、F# インタラクティブ ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="3f49f-144">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="3f49f-145">これを使用すると、コードを呼び出して結果を対話形式で確認できるプロセスにコードを送信できます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-145">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="3f49f-146">その使用を開始するには、コードで定義されている `square` 関数を強調表示します。</span><span class="sxs-lookup"><span data-stu-id="3f49f-146">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="3f49f-147">次に、トップ レベル メニューの **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f49f-147">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="3f49f-148">次に、 **[選択項目を F# インタラクティブに送信する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f49f-148">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="3f49f-149">これにより、F# インタラクティブ ウィンドウのコードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-149">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="3f49f-150">または、選択範囲を右クリックし、 **[選択項目を F# インタラクティブに送信する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f49f-150">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="3f49f-151">F# インタラクティブ ウィンドウが表示され、そこに次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-151">You should see the F# Interactive Window appear with the following in it:</span></span>

```console
>

val square : x:int -> int

>
```

<span data-ttu-id="3f49f-152">これは、前に関数をポイントしたときに表示されたものと同じ `square` 関数の関数シグネチャを示しています。</span><span class="sxs-lookup"><span data-stu-id="3f49f-152">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="3f49f-153">`square` は現在 F# インタラクティブ プロセスで定義されているため、異なる値を使用して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-153">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="3f49f-154">これにより、関数が実行され、結果が新しい名前 `it` にバインドされ、`it` の型と値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-154">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="3f49f-155">各行は、`;;` で終了する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3f49f-155">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="3f49f-156">こうすることで、関数呼び出しがいつ終了するかを F# インタラクティブが認識できます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-156">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="3f49f-157">F# インタラクティブで新しい関数を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-157">You can also define new functions in F# Interactive:</span></span>

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="3f49f-158">上では新しい関数 `isOdd` が定義されています。これは、`int` を受け取り、それが奇数かどうかを確認するものです。</span><span class="sxs-lookup"><span data-stu-id="3f49f-158">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="3f49f-159">この関数を呼び出して、さまざまな入力で何が返されるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-159">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="3f49f-160">関数呼び出しの中で関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-160">You can call functions within function calls:</span></span>

```console
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="3f49f-161">[パイプ転送演算子](../language-reference/symbol-and-operator-reference/index.md)を使用して、値を 2 つの関数にパイプライン処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="3f49f-161">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="3f49f-162">パイプ転送演算子などについては、以降のチュートリアルで詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="3f49f-162">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="3f49f-163">ここでは、F# インタラクティブを使用してできることを簡単に確認しています。</span><span class="sxs-lookup"><span data-stu-id="3f49f-163">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="3f49f-164">詳細については、「[F# による対話型プログラミング](../tools/fsharp-interactive/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3f49f-164">To learn more, check out [Interactive Programming with F#](../tools/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="3f49f-165">次のステップ</span><span class="sxs-lookup"><span data-stu-id="3f49f-165">Next steps</span></span>

<span data-ttu-id="3f49f-166">まだ行っていない場合は、F# 言語のコア機能の一部を紹介している「[F# のツアー](../tour.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3f49f-166">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="3f49f-167">F# の一部の機能の概要と、Visual Studio for Mac にコピーして実行できる充実したコード サンプルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="3f49f-167">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="3f49f-168">優れた外部リソースも使用できます。それについては「[F# ガイド](../index.yml)」で紹介しています。</span><span class="sxs-lookup"><span data-stu-id="3f49f-168">There are also some great external resources you can use, showcased in the [F# Guide](../index.yml).</span></span>

## <a name="see-also"></a><span data-ttu-id="3f49f-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f49f-169">See also</span></span>

- [<span data-ttu-id="3f49f-170">F# ガイド</span><span class="sxs-lookup"><span data-stu-id="3f49f-170">F# guide</span></span>](../index.yml)
- [<span data-ttu-id="3f49f-171">F# のツアー</span><span class="sxs-lookup"><span data-stu-id="3f49f-171">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="3f49f-172">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="3f49f-172">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="3f49f-173">型の推定</span><span class="sxs-lookup"><span data-stu-id="3f49f-173">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="3f49f-174">シンボルと演算子のリファレンス</span><span class="sxs-lookup"><span data-stu-id="3f49f-174">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
