---
title: dotnet テストと xUnit を使用した .NET Core での単体テスト F#
description: dotnet テストおよび xUnit を使用したサンプル ソリューションを段階的に構築していく対話型エクスペリエンスを通じて、.NET Core における F# の単体テストの概念について説明します。
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: 76386097ebe9b0ec6141abd089b219275d989446
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875032"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="96ef7-103">dotnet テストと xUnit を使用した .NET Core での単体テスト F# ライブラリ</span><span class="sxs-lookup"><span data-stu-id="96ef7-103">Unit testing F# libraries in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="96ef7-104">このチュートリアルでは、単体テストの概念について学習するためにサンプル ソリューションを段階的に構築する対話型のエクスペリエンスを示します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="96ef7-105">構築済みのソリューションを使用してチュートリアルに従う場合は、開始する前に[サンプル コードを参照またはダウンロード](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-with-fsharp/)してください。</span><span class="sxs-lookup"><span data-stu-id="96ef7-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-with-fsharp/) before you begin.</span></span> <span data-ttu-id="96ef7-106">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#view-and-download-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96ef7-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="96ef7-107">ソース プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="96ef7-107">Creating the source project</span></span>

<span data-ttu-id="96ef7-108">シェル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="96ef7-108">Open a shell window.</span></span> <span data-ttu-id="96ef7-109">ソリューションを保存するための *unit-testing-with-fsharp* というディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="96ef7-110">この新しいディレクトリ内で `dotnet new sln` を実行して、ソリューションを新たに作成します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-110">Inside this new directory, run `dotnet new sln` to create a new solution.</span></span> <span data-ttu-id="96ef7-111">こうすることで、クラス ライブラリと単体テスト プロジェクトの両方を管理しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="96ef7-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="96ef7-112">ソリューションのディレクトリ内で、*MathService* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="96ef7-113">現時点のディレクトリとファイルの構造は次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="96ef7-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="96ef7-114">*MathService* を現在のディレクトリにし、`dotnet new classlib -lang "F#"` を実行してソース プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-114">Make *MathService* the current directory, and run `dotnet new classlib -lang "F#"` to create the source project.</span></span> <span data-ttu-id="96ef7-115">計算サービスのエラーが発生する実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="96ef7-116">*unit-testing-with-fsharp* ディレクトリに戻ります。</span><span class="sxs-lookup"><span data-stu-id="96ef7-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="96ef7-117">`dotnet sln add .\MathService\MathService.fsproj` を実行して、クラス ライブラリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-117">Run `dotnet sln add .\MathService\MathService.fsproj` to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="96ef7-118">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="96ef7-118">Creating the test project</span></span>

<span data-ttu-id="96ef7-119">次に、*MathService.Tests* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="96ef7-120">次の一覧はディレクトリ構造を示したものです。</span><span class="sxs-lookup"><span data-stu-id="96ef7-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="96ef7-121">*MathService.Tests* ディレクトリを現在のディレクトリにし、`dotnet new xunit -lang "F#"` を使用して新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-121">Make the *MathService.Tests* directory the current directory and create a new project using `dotnet new xunit -lang "F#"`.</span></span> <span data-ttu-id="96ef7-122">これで、テスト ライブラリとして xUnit を使用するテスト プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="96ef7-122">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="96ef7-123">生成されたテンプレートで、*MathServiceTests.fsproj* のテスト ランナーが構成されます。</span><span class="sxs-lookup"><span data-stu-id="96ef7-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="96ef7-124">テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="96ef7-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="96ef7-125">前の手順の `dotnet new` によって、xUnit と xUnit ランナーが追加されています。</span><span class="sxs-lookup"><span data-stu-id="96ef7-125">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="96ef7-126">ここで、プロジェクトに別の依存関係として `MathService` クラス ライブラリを追加します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="96ef7-127">`dotnet add reference` コマンドを使用する。</span><span class="sxs-lookup"><span data-stu-id="96ef7-127">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="96ef7-128">全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="96ef7-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="96ef7-129">ソリューションの最終的なレイアウトは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="96ef7-129">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathServiceTests.fsproj
```

<span data-ttu-id="96ef7-130">*unit-testing-with-fsharp* ディレクトリで `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` を実行します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-130">Execute `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="96ef7-131">最初のテストの作成</span><span class="sxs-lookup"><span data-stu-id="96ef7-131">Creating the first test</span></span>

<span data-ttu-id="96ef7-132">失敗するテストを 1 つ作成してそれを合格させる、というプロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="96ef7-133">*Tests.fs* を開き、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

<span data-ttu-id="96ef7-134">`[<Fact>]` 属性は、テスト ランナーによって実行されるテスト メソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-134">The `[<Fact>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="96ef7-135">*unit-testing-with-fsharp* で `dotnet test` を実行してテストとクラス ライブラリをビルドし、それからテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-135">From the *unit-testing-with-fsharp*, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="96ef7-136">xUnit テスト ランナーには、テストを実行するためのプログラムのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="96ef7-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="96ef7-137">`dotnet test` を実行すると、作成した単体テスト プロジェクトを使用してテスト ランナーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="96ef7-137">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="96ef7-138">この 2 つのテストは、最も基本的な成功テストと失敗テストです。</span><span class="sxs-lookup"><span data-stu-id="96ef7-138">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="96ef7-139">`My test` は成功し、`Fail every time` は失敗します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-139">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="96ef7-140">今度は `squaresOfOdds` メソッドのテストを作成します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-140">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="96ef7-141">`squaresOfOdds` メソッドは、入力シーケンスに含まれるすべての奇数の整数値を 2 乗した値のシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-141">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="96ef7-142">これらの関数をすべて一度に書き込むのではなく、機能を検証するテストを繰り返し作成することができます。</span><span class="sxs-lookup"><span data-stu-id="96ef7-142">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="96ef7-143">各テストを成功させることで、メソッドに必要な機能を作成することになります。</span><span class="sxs-lookup"><span data-stu-id="96ef7-143">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="96ef7-144">最も簡単に記述できるテストは、すべて偶数である数字を `squaresOfOdds` に渡して呼び出すことです。このテストの結果は、整数の空のシーケンスになります。</span><span class="sxs-lookup"><span data-stu-id="96ef7-144">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="96ef7-145">次に示すのがそのテストです。</span><span class="sxs-lookup"><span data-stu-id="96ef7-145">Here's that test:</span></span>

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="96ef7-146">テストが失敗します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-146">Your test fails.</span></span> <span data-ttu-id="96ef7-147">実装はまだ作成していません。</span><span class="sxs-lookup"><span data-stu-id="96ef7-147">You haven't created the implementation yet.</span></span> <span data-ttu-id="96ef7-148">最も単純な動作のコードを `MathService` クラスに記述して、このテストが成功するようにします。</span><span class="sxs-lookup"><span data-stu-id="96ef7-148">Make this test pass by writing the simplest code in the `MathService` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="96ef7-149">*unit-testing-with-fsharp* ディレクトリで、もう一度 `dotnet test` を実行します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-149">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="96ef7-150">`dotnet test` コマンドは `MathService` プロジェクトのビルドを実行してから、`MathService.Tests` プロジェクトのビルドを実行します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-150">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="96ef7-151">両方のプロジェクトをビルドすると、この単一テストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="96ef7-151">After building both projects, it runs this single test.</span></span> <span data-ttu-id="96ef7-152">成功します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-152">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="96ef7-153">要件の完成</span><span class="sxs-lookup"><span data-stu-id="96ef7-153">Completing the requirements</span></span>

<span data-ttu-id="96ef7-154">テストが成功したので、他のテストも記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="96ef7-154">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="96ef7-155">次の単純な例は、奇数は `1` のみが含まれるシーケンスで機能します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-155">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="96ef7-156">数値の 1 は簡単です。なぜなら 1 の 2 乗は 1 になるためです。</span><span class="sxs-lookup"><span data-stu-id="96ef7-156">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="96ef7-157">次のテストを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-157">Here's that next test:</span></span>

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="96ef7-158">`dotnet test` を実行するとテストが実行され、新しいテストが失敗することがわかります。</span><span class="sxs-lookup"><span data-stu-id="96ef7-158">Executing `dotnet test` runs your tests and shows you that the new test fails.</span></span> <span data-ttu-id="96ef7-159">今度は、新しいテストに対応するために `squaresOfOdds` メソッドを更新します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-159">Now, update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="96ef7-160">このテストを成功させるには、フィルター処理でシーケンスからすべての偶数を除外します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-160">You filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="96ef7-161">小さなフィルター関数を記述し、`Seq.filter` を使用することで実現できます。</span><span class="sxs-lookup"><span data-stu-id="96ef7-161">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="96ef7-162">実施する手順がもう一つあります。各奇数を 2 乗します。</span><span class="sxs-lookup"><span data-stu-id="96ef7-162">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="96ef7-163">テストを新たに記述するところから始めます。</span><span class="sxs-lookup"><span data-stu-id="96ef7-163">Start by writing a new test:</span></span>

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

<span data-ttu-id="96ef7-164">テストを修正するには、フィルター処理したシーケンスをパイプでつなぎ、各奇数の 2 乗を計算するマップ操作をします。</span><span class="sxs-lookup"><span data-stu-id="96ef7-164">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="96ef7-165">これで、小さなライブラリとそのライブラリの単体テストのセットが構築されました。</span><span class="sxs-lookup"><span data-stu-id="96ef7-165">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="96ef7-166">ソリューションを構築したことで、新しいパッケージとテストの追加が通常のワークフローに組み込まれました。</span><span class="sxs-lookup"><span data-stu-id="96ef7-166">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="96ef7-167">アプリケーションの目標を達成することに時間と労力の多くを割き、集中して取り組みました。</span><span class="sxs-lookup"><span data-stu-id="96ef7-167">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="96ef7-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="96ef7-168">See also</span></span>

- [<span data-ttu-id="96ef7-169">dotnet new</span><span class="sxs-lookup"><span data-stu-id="96ef7-169">dotnet new</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="96ef7-170">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="96ef7-170">dotnet sln</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="96ef7-171">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="96ef7-171">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="96ef7-172">dotnet test</span><span class="sxs-lookup"><span data-stu-id="96ef7-172">dotnet test</span></span>](../tools/dotnet-test.md)
