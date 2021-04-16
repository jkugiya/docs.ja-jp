---
title: Visual Studio での F+ の概要
description: Visual Studio で F# を使用する方法について説明します。
ms.date: 12/20/2019
ms.openlocfilehash: 9bf47fb08ea3df0aa0d5064043d94f030d45d568
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337341"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="f4509-103">Visual Studio での F+ の概要</span><span class="sxs-lookup"><span data-stu-id="f4509-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="f4509-104">F# と Visual F# のツールが Visual Studio 統合開発環境 (IDE) でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f4509-104">F# and the Visual F# tooling are supported in the Visual Studio integrated development environment (IDE).</span></span>

<span data-ttu-id="f4509-105">開始するには、[Visual Studio が F# のサポート付きでインストールされていること](install-fsharp.md#install-f-with-visual-studio)を確認します。</span><span class="sxs-lookup"><span data-stu-id="f4509-105">To begin, ensure that you have [Visual Studio installed with F# support](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="f4509-106">コンソール アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="f4509-106">Create a console application</span></span>

<span data-ttu-id="f4509-107">Visual Studio の最も基本的なプロジェクトの 1 つは、コンソール アプリです。</span><span class="sxs-lookup"><span data-stu-id="f4509-107">One of the most basic projects in Visual Studio is the console app.</span></span> <span data-ttu-id="f4509-108">作成手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f4509-108">Here's how to create one:</span></span>

1. <span data-ttu-id="f4509-109">Visual Studio 2019 を開きます。</span><span class="sxs-lookup"><span data-stu-id="f4509-109">Open Visual Studio 2019.</span></span>

2. <span data-ttu-id="f4509-110">スタート ウィンドウで、 **[新しいプロジェクトの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f4509-110">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="f4509-111">**[新しいプロジェクトの作成]** ページで、言語の一覧から **[F#]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f4509-111">On the **Create a new project** page, choose **F#** from the Language list.</span></span>

4. <span data-ttu-id="f4509-112">**[コンソール アプリ (.NET Core)]** テンプレートを選択し、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f4509-112">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

5. <span data-ttu-id="f4509-113">**[新しいプロジェクトの構成]** ページで、 **[プロジェクト名]** ボックスに名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f4509-113">On the **Configure your new project** page, enter a name in the **Project name** box.</span></span> <span data-ttu-id="f4509-114">次に、 **[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f4509-114">Then, choose **Create**.</span></span>

   <span data-ttu-id="f4509-115">Visual Studio によって新しい F# プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f4509-115">Visual Studio creates the new F# project.</span></span> <span data-ttu-id="f4509-116">これはソリューション エクスプローラー ウィンドウで確認できます。</span><span class="sxs-lookup"><span data-stu-id="f4509-116">You can see it in the Solution Explorer window.</span></span>

## <a name="write-the-code"></a><span data-ttu-id="f4509-117">コードを作成する</span><span class="sxs-lookup"><span data-stu-id="f4509-117">Write the code</span></span>

<span data-ttu-id="f4509-118">まず、コードをいくつか記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="f4509-118">Let's get started by writing some code.</span></span> <span data-ttu-id="f4509-119">`Program.fs` ファイルが開いていることを確認し、その内容を次の内容に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f4509-119">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="f4509-120">前のコード サンプルでは、`x` という名前の入力を受け取り、それをそれ自体で乗算する `square` という関数を定義しています。</span><span class="sxs-lookup"><span data-stu-id="f4509-120">The previous code sample defines a function called `square` that takes an input named `x` and multiplies it by itself.</span></span> <span data-ttu-id="f4509-121">F# では[型の推定](../language-reference/type-inference.md)が使用されるため、`x` の型を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f4509-121">Because F# uses [Type inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span> <span data-ttu-id="f4509-122">F# コンパイラでは、乗算が有効な型を認識し、`square` の呼び出し方法に基づいて型を `x` に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="f4509-122">The F# compiler understands the types where multiplication is valid and assigns a type to `x` based on how `square` is called.</span></span> <span data-ttu-id="f4509-123">マウスポインターを `square` に合わせると、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4509-123">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="f4509-124">これは、関数の型シグネチャとして知られています。</span><span class="sxs-lookup"><span data-stu-id="f4509-124">This is what is known as the function's type signature.</span></span> <span data-ttu-id="f4509-125">これは、次のように解釈できます。"Square は、x という整数を受け取り、整数を生成する関数です。"</span><span class="sxs-lookup"><span data-stu-id="f4509-125">It can be read like this: "Square is a function that takes an integer named x and produces an integer".</span></span> <span data-ttu-id="f4509-126">コンパイラによって、現段階では、`square` に `int` の型が設定されました。これは、乗算が *すべて* の型ではなく、閉じられた型のセットでジェネリックであるためです。</span><span class="sxs-lookup"><span data-stu-id="f4509-126">The compiler gave `square` the `int` type for now; this is because multiplication is not generic across *all* types but rather a closed set of types.</span></span> <span data-ttu-id="f4509-127">`float` などの別の入力型を使用して `square` を呼び出すと、F# コンパイラによって型シグネチャが調整されます。</span><span class="sxs-lookup"><span data-stu-id="f4509-127">The F# compiler will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="f4509-128">`EntryPoint` 属性で装飾された別の関数 `main` が定義されています。</span><span class="sxs-lookup"><span data-stu-id="f4509-128">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute.</span></span> <span data-ttu-id="f4509-129">この属性により、プログラムの実行をそこから開始する必要があることが F# コンパイラに指示されます。</span><span class="sxs-lookup"><span data-stu-id="f4509-129">This attribute tells the F# compiler that program execution should start there.</span></span> <span data-ttu-id="f4509-130">これは、他の [C スタイルのプログラミング言語](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)と同じ規則に従います。コマンドライン引数をこの関数に渡すことができ、整数のコードが返される (通常は `0`) というものです。</span><span class="sxs-lookup"><span data-stu-id="f4509-130">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="f4509-131">エントリ ポイント関数 `main` の中において、`12` の引数を使用して `square` 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f4509-131">It is in the entry point function, `main`, that you call the `square` function with an argument of `12`.</span></span> <span data-ttu-id="f4509-132">次に F# コンパイラは、`int -> int` になるように `square` の型を割り当てます (つまり、`int` を受け取り、`int` を生成する関数)。</span><span class="sxs-lookup"><span data-stu-id="f4509-132">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function that takes an `int` and produces an `int`).</span></span> <span data-ttu-id="f4509-133">`printfn` の呼び出しは、書式指定文字列を使用して結果 (と改行) を出力する書式設定済みの印刷関数です。</span><span class="sxs-lookup"><span data-stu-id="f4509-133">The call to `printfn` is a formatted printing function that uses a format string and prints the result (and a new line).</span></span> <span data-ttu-id="f4509-134">書式指定文字列には、C スタイルのプログラミング言語と同様に、渡される引数 (この場合は `12` と `(square 12)`) に対応するパラメーター (`%d`) があります。</span><span class="sxs-lookup"><span data-stu-id="f4509-134">The format string, similar to C-style programming languages, has parameters (`%d`) that correspond to the arguments that are passed to it, in this case, `12` and `(square 12)`.</span></span>

## <a name="run-the-code"></a><span data-ttu-id="f4509-135">コードの実行</span><span class="sxs-lookup"><span data-stu-id="f4509-135">Run the code</span></span>

<span data-ttu-id="f4509-136">**Ctrl** + **F5** を押してコードを実行し、結果を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="f4509-136">You can run the code and see the results by pressing **Ctrl**+**F5**.</span></span> <span data-ttu-id="f4509-137">または、最上部のメニュー バーから **[デバッグ]**  >  **[デバッグなしで開始]** を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="f4509-137">Alternatively, you can choose the **Debug** > **Start Without Debugging** from the top-level menu bar.</span></span> <span data-ttu-id="f4509-138">これにより、デバッグなしでプログラムが実行されます。</span><span class="sxs-lookup"><span data-stu-id="f4509-138">This runs the program without debugging.</span></span>

<span data-ttu-id="f4509-139">Visual Studio によって開かれたコンソール ウィンドウに以下の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4509-139">The following output prints to the console window that Visual Studio opened:</span></span>

```console
12 squared is: 144!
```

<span data-ttu-id="f4509-140">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="f4509-140">Congratulations!</span></span> <span data-ttu-id="f4509-141">Visual Studio で最初の F# プロジェクトを作成し、値を計算して出力する F# 関数を記述し、プロジェクトを実行して結果を確認しました。</span><span class="sxs-lookup"><span data-stu-id="f4509-141">You've created your first F# project in Visual Studio, written an F# function that calculates and prints a value, and run the project to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f4509-142">次のステップ</span><span class="sxs-lookup"><span data-stu-id="f4509-142">Next steps</span></span>

<span data-ttu-id="f4509-143">まだの方は、F# 言語のコア機能の一部をご紹介している「[F# のツアー](../tour.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f4509-143">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span> <span data-ttu-id="f4509-144">F# の一部の機能の概要と、Visual Studio にコピーして実行できる充実したコード サンプルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f4509-144">It provides an overview of some of the capabilities of F# and ample code samples that you can copy into Visual Studio and run.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f4509-145">F# のツアー</span><span class="sxs-lookup"><span data-stu-id="f4509-145">Tour of F#</span></span>](../tour.md)

## <a name="see-also"></a><span data-ttu-id="f4509-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4509-146">See also</span></span>

- [<span data-ttu-id="f4509-147">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="f4509-147">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="f4509-148">型の推定</span><span class="sxs-lookup"><span data-stu-id="f4509-148">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="f4509-149">シンボルと演算子のリファレンス</span><span class="sxs-lookup"><span data-stu-id="f4509-149">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
