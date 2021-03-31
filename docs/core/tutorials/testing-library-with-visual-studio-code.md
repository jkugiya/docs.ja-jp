---
title: Visual Studio Code を使用して .NET クラス ライブラリをテストする
description: Visual Studio Code と .NET CLI を使用して、.NET クラス ライブラリの単体テスト プロジェクトを作成および実行する方法について学習します。
ms.date: 11/17/2020
ms.openlocfilehash: bc8741e11504f94e54ccc45a5ad93408a3fe9309
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511815"
---
# <a name="tutorial-test-a-net-class-library-using-visual-studio-code"></a><span data-ttu-id="3238e-103">チュートリアル: Visual Studio Code を使用して .NET クラス ライブラリをテストする</span><span class="sxs-lookup"><span data-stu-id="3238e-103">Tutorial: Test a .NET class library using Visual Studio Code</span></span>

<span data-ttu-id="3238e-104">このチュートリアルでは、テスト プロジェクトをソリューションに追加して、単体テストを自動化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3238e-104">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3238e-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="3238e-105">Prerequisites</span></span>

- <span data-ttu-id="3238e-106">このチュートリアルでは、「[Visual Studio Code を使用して .NET クラス ライブラリを作成する](library-with-visual-studio-code.md)」で作成するソリューションを使用します。</span><span class="sxs-lookup"><span data-stu-id="3238e-106">This tutorial works with the solution that you create in [Create a .NET class library using Visual Studio Code](library-with-visual-studio-code.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="3238e-107">単体テスト プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="3238e-107">Create a unit test project</span></span>

<span data-ttu-id="3238e-108">単体テストでは、開発および公開時に自動化されたソフトウェア テストが提供されます。</span><span class="sxs-lookup"><span data-stu-id="3238e-108">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="3238e-109">このチュートリアルで使用するテスト フレームワークは MSTest です。</span><span class="sxs-lookup"><span data-stu-id="3238e-109">The testing framework that you use in this tutorial is MSTest.</span></span> <span data-ttu-id="3238e-110">[MSTest](https://github.com/Microsoft/testfx-docs) は、選択できる 3 つのテスト フレームワークのうちの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="3238e-110">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="3238e-111">これ以外は、[xUnit](https://xunit.net/) と [nUnit](https://nunit.org/) です。</span><span class="sxs-lookup"><span data-stu-id="3238e-111">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="3238e-112">Visual Studio Code を開始します。</span><span class="sxs-lookup"><span data-stu-id="3238e-112">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="3238e-113">「[Visual Studio Code を使用して .NET クラス ライブラリを作成する](library-with-visual-studio-code.md)」で作成した `ClassLibraryProjects` ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="3238e-113">Open the `ClassLibraryProjects` solution you created in [Create a .NET class library using Visual Studio Code](library-with-visual-studio-code.md).</span></span>

1. <span data-ttu-id="3238e-114">「StringLibraryTest」という名前の単体テスト プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3238e-114">Create a unit test project named "StringLibraryTest".</span></span>

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   <span data-ttu-id="3238e-115">プロジェクト テンプレートでは、次のコードを使用して UnitTest1.cs ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3238e-115">The project template creates a UnitTest1.cs file with the following code:</span></span>

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   <span data-ttu-id="3238e-116">単体テストのテンプレートで作成されたソース コードにより、次の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="3238e-116">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="3238e-117">単体テストで使用される型が含まれた <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 名前空間がインポートされます。</span><span class="sxs-lookup"><span data-stu-id="3238e-117">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="3238e-118"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 属性が `UnitTest1` クラスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="3238e-118">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="3238e-119"><xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 属性を適用して `TestMethod1` を定義します。</span><span class="sxs-lookup"><span data-stu-id="3238e-119">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1`.</span></span>

   <span data-ttu-id="3238e-120">[[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute)でタグ付けされたテスト クラスの [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) でタグ付けされた各テスト メソッドが、単体テスト実行時に自動実行されます。</span><span class="sxs-lookup"><span data-stu-id="3238e-120">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

1. <span data-ttu-id="3238e-121">次のように、テスト プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="3238e-121">Add the test project to the solution.</span></span>

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

## <a name="add-a-project-reference"></a><span data-ttu-id="3238e-122">プロジェクト参照を追加する</span><span class="sxs-lookup"><span data-stu-id="3238e-122">Add a project reference</span></span>

<span data-ttu-id="3238e-123">テスト プロジェクトが `StringLibrary` クラスと連動するように、`StringLibraryTest` プロジェクトに `StringLibrary` プロジェクトへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="3238e-123">For the test project to work with the `StringLibrary` class, add a reference in the `StringLibraryTest` project to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="3238e-124">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3238e-124">Run the following command:</span></span>

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="3238e-125">単体テスト メソッドの追加と実行</span><span class="sxs-lookup"><span data-stu-id="3238e-125">Add and run unit test methods</span></span>

<span data-ttu-id="3238e-126">Visual Studio で単体テストを実行すると、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 属性でマークされたクラス内で、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 属性でマークされた各メソッドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="3238e-126">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="3238e-127">テスト メソッドは、最初の失敗が検出されたとき、またはそのメソッドに含まれているすべてのテストが成功したときに終了します。</span><span class="sxs-lookup"><span data-stu-id="3238e-127">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="3238e-128">一般的なテストでは、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> クラスのメンバーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3238e-128">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="3238e-129">多くのアサート メソッドは最低 2 つのパラメーターを含んでいます。1 つは予期されるテスト結果、もう 1 つは実際のテスト結果です。</span><span class="sxs-lookup"><span data-stu-id="3238e-129">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="3238e-130">次の表に、`Assert` クラスの頻繁に呼び出されるメソッドをいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="3238e-130">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="3238e-131">Assert メソッド</span><span class="sxs-lookup"><span data-stu-id="3238e-131">Assert methods</span></span>     | <span data-ttu-id="3238e-132">関数</span><span class="sxs-lookup"><span data-stu-id="3238e-132">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="3238e-133">2 つの値または 2 つのオブジェクトが等しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3238e-133">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="3238e-134">値またはオブジェクトが等しくない場合、アサートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="3238e-134">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="3238e-135">2 つのオブジェクト変数が同じオブジェクトを参照していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3238e-135">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="3238e-136">変数が別々のオブジェクトを参照している場合、アサートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="3238e-136">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="3238e-137">条件が `false` であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3238e-137">Verifies that a condition is `false`.</span></span> <span data-ttu-id="3238e-138">条件が `true` の場合、アサートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="3238e-138">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="3238e-139">オブジェクトが `null` でないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3238e-139">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="3238e-140">オブジェクトが `null` である場合、アサートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="3238e-140">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="3238e-141">また、テスト メソッドで <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> メソッドを使用して、スローすることが期待される例外の種類を示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="3238e-141">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="3238e-142">指定した例外がスローされない場合、テストは失敗します。</span><span class="sxs-lookup"><span data-stu-id="3238e-142">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="3238e-143">`StringLibrary.StartsWithUpper` メソッドのテストでは、大文字で始まる文字列を多く用意します。</span><span class="sxs-lookup"><span data-stu-id="3238e-143">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="3238e-144">これらの場合ではメソッドが `true` を返すと予測されるので、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="3238e-144">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3238e-145">同様に、大文字以外で始まる文字列を多く用意します。</span><span class="sxs-lookup"><span data-stu-id="3238e-145">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="3238e-146">これらの場合ではメソッドが `false` を返すと予測されるので、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="3238e-146">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="3238e-147">ライブラリ メソッドでは文字列を処理するため、[空の文字列 (`String.Empty`)](xref:System.String.Empty) および `null` 文字列を正常に処理することも確認します。</span><span class="sxs-lookup"><span data-stu-id="3238e-147">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty) and a `null` string.</span></span> <span data-ttu-id="3238e-148">空の文字列は、文字を含まない、<xref:System.String.Length> が 0 の文字列です。</span><span class="sxs-lookup"><span data-stu-id="3238e-148">An empty string is one that has no characters and whose <xref:System.String.Length> is 0.</span></span> <span data-ttu-id="3238e-149">`null` 文字列は、初期化されていない文字列です。</span><span class="sxs-lookup"><span data-stu-id="3238e-149">A `null` string is one that hasn't been initialized.</span></span> <span data-ttu-id="3238e-150">しかし、`StartsWithUpper` を静的メソッドとして直接呼び出して、単一の <xref:System.String> 引数を渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="3238e-150">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="3238e-151">または、`null` に割り当てられた `string` 変数の拡張メソッドとして `StartsWithUpper` を呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="3238e-151">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="3238e-152">メソッドを 3 つ定義します。これらのメソッドでは、文字列配列の各要素に対して <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3238e-152">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="3238e-153">メソッドのオーバーロードを呼び出します。これにより、テストが失敗した場合に表示されるエラー メッセージを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3238e-153">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="3238e-154">このメッセージによって、エラーの原因となった文字列が識別されます。</span><span class="sxs-lookup"><span data-stu-id="3238e-154">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="3238e-155">テスト メソッドを作成するには</span><span class="sxs-lookup"><span data-stu-id="3238e-155">To create the test methods:</span></span>

1. <span data-ttu-id="3238e-156">*StringLibraryTest/UnitTest1.cs* を開き、すべてのコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3238e-156">Open *StringLibraryTest/UnitTest1.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="3238e-157">`TestStartsWithUpper` メソッドの大文字のテストには、ギリシャ語の大文字のアルファ (U+0391) とキリル文字の大文字 EM (U+041C) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3238e-157">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="3238e-158">`TestDoesNotStartWithUpper` メソッドの小文字のテストには、ギリシャ語の小文字のアルファ (U+03B1) とキリル文字の小文字 Ghe (U+0433) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3238e-158">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="3238e-159">変更内容を保存します。</span><span class="sxs-lookup"><span data-stu-id="3238e-159">Save your changes.</span></span>

1. <span data-ttu-id="3238e-160">テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="3238e-160">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="3238e-161">次のターミナル出力は、すべてのテストが成功したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="3238e-161">The terminal output shows that all tests passed.</span></span>

   ```output
   Starting test execution, please wait...
   A total of 1 test files matched the specified pattern.

   Passed!  - Failed:     0, Passed:     3, Skipped:     0, Total:     3, Duration: 3 ms - StringLibraryTest.dll (net5.0)
   ```

## <a name="handle-test-failures"></a><span data-ttu-id="3238e-162">テストの失敗の処理</span><span class="sxs-lookup"><span data-stu-id="3238e-162">Handle test failures</span></span>

<span data-ttu-id="3238e-163">テスト駆動開発 (TDD) を行っている場合、最初にテストを作成すると、1 回目のテスト実行は失敗します。</span><span class="sxs-lookup"><span data-stu-id="3238e-163">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="3238e-164">その後、テストを成功させるコードをアプリに追加します。</span><span class="sxs-lookup"><span data-stu-id="3238e-164">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="3238e-165">このチュートリアルでは、検証するアプリ コードを記述した後にテストを作成したため、テストが失敗することはありませんでした。</span><span class="sxs-lookup"><span data-stu-id="3238e-165">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="3238e-166">テストの失敗が予想されるときにテストが失敗することを検証するには、テスト入力に無効な値を追加します。</span><span class="sxs-lookup"><span data-stu-id="3238e-166">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="3238e-167">`TestDoesNotStartWithUpper` メソッドの `words` 配列を変更し、文字列 "Error" を含めます。</span><span class="sxs-lookup"><span data-stu-id="3238e-167">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="3238e-168">テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="3238e-168">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="3238e-169">ターミナルの出力では、1 つのテストが失敗したことが示され、失敗したテストに関するエラー メッセージが表示されます。"Assert.IsFalse failed.</span><span class="sxs-lookup"><span data-stu-id="3238e-169">The terminal output shows that one test fails, and it provides an error message for the failed test: "Assert.IsFalse failed.</span></span> <span data-ttu-id="3238e-170">Expected for 'Error': false; actual:True" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3238e-170">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="3238e-171">エラーのため、配列内の "Error" の後ろの文字列はテストされませんでした。</span><span class="sxs-lookup"><span data-stu-id="3238e-171">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   ```output
   Starting test execution, please wait...
   A total of 1 test files matched the specified pattern.
     Failed TestDoesNotStartWithUpper [28 ms]
     Error Message:
      Assert.IsFalse failed. Expected for 'Error': false; Actual: True
     Stack Trace:
        at StringLibraryTest.UnitTest1.TestDoesNotStartWithUpper() in C:\ClassLibraryProjects\StringLibraryTest\UnitTest1.cs:line 33

   Failed!  - Failed:     1, Passed:     2, Skipped:     0, Total:     3, Duration: 31 ms - StringLibraryTest.dll (net5.0)
   ```

1. <span data-ttu-id="3238e-172">手順 1 で追加した文字列 "Error" を削除します。</span><span class="sxs-lookup"><span data-stu-id="3238e-172">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="3238e-173">テストを再実行すると、テストは成功します。</span><span class="sxs-lookup"><span data-stu-id="3238e-173">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="3238e-174">ライブラリのリリース バージョンのテスト</span><span class="sxs-lookup"><span data-stu-id="3238e-174">Test the Release version of the library</span></span>

<span data-ttu-id="3238e-175">これで、ライブラリのデバッグ ビルドを実行したときにすべてのテストが成功したので、さらにライブラリのリリース ビルドに対してテストを行います。</span><span class="sxs-lookup"><span data-stu-id="3238e-175">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="3238e-176">コンパイラの最適化などのさまざまな要因により、デバッグ ビルドとリリース ビルドとでは動作が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3238e-176">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

1. <span data-ttu-id="3238e-177">リリース ビルド構成を使用してテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="3238e-177">Run the tests with the Release build configuration:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   <span data-ttu-id="3238e-178">テストが成功します。</span><span class="sxs-lookup"><span data-stu-id="3238e-178">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="3238e-179">テストのデバッグ</span><span class="sxs-lookup"><span data-stu-id="3238e-179">Debug tests</span></span>

<span data-ttu-id="3238e-180">IDE として Visual Studio Code を使用する場合は、「[Visual Studio Code を使用して .NET コンソール アプリケーションをデバッグする](debugging-with-visual-studio-code.md)」に示されているのと同じプロセスを使用し、単体テスト プロジェクトを使ってコードをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="3238e-180">If you're using Visual Studio Code as your IDE, you can use the same process shown in [Debug a .NET console application using Visual Studio Code](debugging-with-visual-studio-code.md) to debug code using your unit test project.</span></span> <span data-ttu-id="3238e-181">*ShowCase* アプリ プロジェクトを開始する代わりに、*StringLibraryTest/UnitTest1.cs* を開き、7 行目と 8 行目の間で **[すべてのテストを実行する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3238e-181">Instead of starting the *ShowCase* app project, open *StringLibraryTest/UnitTest1.cs*, and select **Run All Tests** between lines 7 and 8.</span></span> <span data-ttu-id="3238e-182">見つからない場合は、<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> キーを押してコマンド パレットを開き、「**Reload Window**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3238e-182">If you're unable to find it, press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> to open the command palette and enter **Reload Window**.</span></span>

<span data-ttu-id="3238e-183">Visual Studio Code により、デバッガーがアタッチされた状態でテスト プロジェクトが開始されます。</span><span class="sxs-lookup"><span data-stu-id="3238e-183">Visual Studio Code starts the test project with the debugger attached.</span></span> <span data-ttu-id="3238e-184">実行は、テスト プロジェクトまたは基になるライブラリ コードに追加したブレークポイントで停止します。</span><span class="sxs-lookup"><span data-stu-id="3238e-184">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="3238e-185">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="3238e-185">Additional resources</span></span>

* [<span data-ttu-id="3238e-186">.NET での単体テスト</span><span class="sxs-lookup"><span data-stu-id="3238e-186">Unit testing in .NET</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="3238e-187">次の手順</span><span class="sxs-lookup"><span data-stu-id="3238e-187">Next steps</span></span>

<span data-ttu-id="3238e-188">このチュートリアルでは、クラス ライブラリの単体テストを行いました。</span><span class="sxs-lookup"><span data-stu-id="3238e-188">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="3238e-189">ライブラリをパッケージとして [NuGet](https://nuget.org) に発行した場合、他のユーザーもそれを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3238e-189">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="3238e-190">方法については、次の NuGet のチュートリアルに従ってください。</span><span class="sxs-lookup"><span data-stu-id="3238e-190">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3238e-191">dotnet CLI を使用したパッケージの作成と公開</span><span class="sxs-lookup"><span data-stu-id="3238e-191">Create and publish a package using the dotnet CLI</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="3238e-192">ライブラリを NuGet パッケージとして発行した場合、他のユーザーもそれをインストールして使用できます。</span><span class="sxs-lookup"><span data-stu-id="3238e-192">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="3238e-193">方法については、次の NuGet のチュートリアルに従ってください。</span><span class="sxs-lookup"><span data-stu-id="3238e-193">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3238e-194">dotnet CLI を使用してパッケージをインストールし使用する</span><span class="sxs-lookup"><span data-stu-id="3238e-194">Install and use a package using the dotnet CLI</span></span>](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

<span data-ttu-id="3238e-195">ライブラリはパッケージとして配布する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3238e-195">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="3238e-196">それが使用されるコンソール アプリにバンドルすることができます。</span><span class="sxs-lookup"><span data-stu-id="3238e-196">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="3238e-197">コンソール アプリを発行する方法については、このシリーズの前のチュートリアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3238e-197">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3238e-198">Visual Studio Code を使用して .NET コンソール アプリケーションを発行する</span><span class="sxs-lookup"><span data-stu-id="3238e-198">Publish a .NET console application using Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
