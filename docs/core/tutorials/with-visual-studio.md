---
title: Visual Studio を使用して .NET コンソール アプリケーションを作成する
description: Visual Studio を使用して、C# または Visual Basic で .NET コンソール アプリケーションを作成する方法について学習します。
ms.date: 03/26/2021
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet,contperf-fy21q3
ms.openlocfilehash: e55927080ab30e7a24c54656b7f11a94a023bd65
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636806"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio"></a><span data-ttu-id="d4f6e-103">チュートリアル: Visual Studio を使用して .NET コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="d4f6e-103">Tutorial: Create a .NET console application using Visual Studio</span></span>

<span data-ttu-id="d4f6e-104">このチュートリアルでは、Visual Studio 2019 で .NET コンソール アプリケーションを作成して実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-104">This tutorial shows how to create and run a .NET console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d4f6e-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d4f6e-105">Prerequisites</span></span>

- <span data-ttu-id="d4f6e-106">**.NET Core クロスプラットフォーム開発** ワークロードがインストールされている [Visual Studio 2019 バージョン 16.9.2 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-106">[Visual Studio 2019 version 16.9.2 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="d4f6e-107">このワークロードを選択すると、.NET 5.0 SDK が自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-107">The .NET 5.0 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="d4f6e-108">詳細については、[Visual Studio を使用した .NET SDK のインストール](../install/windows.md#install-with-visual-studio)に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-108">For more information, see [Install the .NET SDK with Visual Studio](../install/windows.md#install-with-visual-studio).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="d4f6e-109">アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="d4f6e-109">Create the app</span></span>

<span data-ttu-id="d4f6e-110">"HelloWorld" という名前の .NET コンソール アプリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-110">Create a .NET console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="d4f6e-111">Visual Studio 2019 を起動します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-111">Start Visual Studio 2019.</span></span>

1. <span data-ttu-id="d4f6e-112">スタート ページで、 **[新しいプロジェクトの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-112">On the start page, choose **Create a new project**.</span></span>

   :::image type="content" source="./media/with-visual-studio/start-window.png" alt-text="Visual Studio のスタート ページで [新しいプロジェクトの作成] ボタンが選択されている":::

1. <span data-ttu-id="d4f6e-114">**[新しいプロジェクトの作成]** ページで、検索ボックスに「**コンソール**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-114">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="d4f6e-115">次に、言語の一覧から **[C#]** または **[Visual Basic]** を選択してから、プラットフォームの一覧から **[すべてのプラットフォーム]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-115">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="d4f6e-116">**[コンソール アプリケーション]** テンプレートを選んでから、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-116">Choose the **Console Application** template, and then choose **Next**.</span></span>

   :::image type="content" source="./media/with-visual-studio/create-new-project.png" alt-text="フィルターが選択された状態の [新しいプロジェクトの作成] ウィンドウ":::

   > [!TIP]
   > <span data-ttu-id="d4f6e-118">.NET テンプレートが表示されない場合は、必要なワークロードが欠落しているおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-118">If you don't see the .NET templates, you're probably missing the required workload.</span></span> <span data-ttu-id="d4f6e-119">**[お探しの情報が見つかりませんでしたか?]** メッセージで、 **[さらにツールと機能をインストールする]** リンクを選択します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-119">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="d4f6e-120">Visual Studio インストーラーが開きます。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-120">The Visual Studio Installer opens.</span></span> <span data-ttu-id="d4f6e-121">**.NET Core クロスプラットフォーム開発** ワークロードがインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-121">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

1. <span data-ttu-id="d4f6e-122">**[新しいプロジェクトの構成]** ダイアログで、 **[プロジェクト名]** ボックスに「**HelloWorld**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-122">In the **Configure your new project** dialog,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="d4f6e-123">**[次へ]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-123">Then choose **Next**.</span></span>

   :::image type="content" source="./media/with-visual-studio/configure-new-project.png" alt-text="プロジェクト名、場所、およびソリューション名のフィールドを使用して新しいプロジェクト ウィンドウを構成します":::

1. <span data-ttu-id="d4f6e-125">**[追加情報]** ダイアログで、 **[.NET 5.0 (Current)]** を選んでから、 **[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-125">In the **Additional information** dialog, select **.NET 5.0 (Current)**, and then select **Create**.</span></span>

   :::image type="content" source="media/with-visual-studio/additional-info.png" alt-text="[追加情報] ダイアログ":::

<span data-ttu-id="d4f6e-127">このテンプレートでは、シンプルな "Hello World" アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-127">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="d4f6e-128"><xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> メソッドを呼び出し、"Hello World!" を</span><span class="sxs-lookup"><span data-stu-id="d4f6e-128">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="d4f6e-129">コンソール ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-129">in the console window.</span></span>

<span data-ttu-id="d4f6e-130">テンプレート コードでは、引数として <xref:System.String> 配列を受け取る単一のメソッド `Main` を含む、`Program` というクラスが定義されます。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-130">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

```vb
Imports System

Module Program
    Sub Main(args As String())
        Console.WriteLine("Hello World!")
    End Sub
End Module
```

<span data-ttu-id="d4f6e-131">`Main` はアプリケーションのエントリ ポイントで、アプリケーションを起動するときに、ランタイムによって自動的に呼び出されるメソッドです。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-131">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="d4f6e-132">アプリケーションが起動されるときに提供されるコマンドライン引数はすべて *args* 配列にあります。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-132">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="d4f6e-133">使用する言語で表示されていない場合は、ページの上部にある言語セレクターを変更します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-133">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="d4f6e-134">アプリを実行する</span><span class="sxs-lookup"><span data-stu-id="d4f6e-134">Run the app</span></span>

1. <span data-ttu-id="d4f6e-135"><kbd>Ctrl</kbd> + <kbd>F5</kbd> キーを押して、デバッグなしでプログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-135">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

   <span data-ttu-id="d4f6e-136">コンソール ウィンドウが開き、"Hello World!" というテキストが</span><span class="sxs-lookup"><span data-stu-id="d4f6e-136">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="d4f6e-137">画面に出力されます。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-137">printed on the screen.</span></span>

   :::image type="content" source="./media/with-visual-studio/hello-world-console.png" alt-text="Hello World Press any key to continue と表示されているコンソール ウィンドウ":::

1. <span data-ttu-id="d4f6e-139">任意のキーを押して、コンソール ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-139">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="d4f6e-140">アプリを拡張する</span><span class="sxs-lookup"><span data-stu-id="d4f6e-140">Enhance the app</span></span>

<span data-ttu-id="d4f6e-141">アプリケーションを拡張し、ユーザーに名前の入力を求め、日付と時刻と共にそれを表示するようにします。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-141">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="d4f6e-142">*Program.cs* または *Program.vb* で、`Main` メソッドの内容 (`Console.WriteLine` を呼び出す行です) を、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-142">In *Program.cs* or *Program.vb*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   <span data-ttu-id="d4f6e-143">このコードによりコンソール ウィンドウにプロンプトが表示され、ユーザーが文字列を入力して <kbd>Enter</kbd> キーを押すまで待機します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-143">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="d4f6e-144">これはこの文字列を `name` という変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-144">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="d4f6e-145">さらに現在の現地時刻を含む <xref:System.DateTime.Now?displayProperty=nameWithType> プロパティの値を取得して、それを `currentDate` という変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-145">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `currentDate`.</span></span> <span data-ttu-id="d4f6e-146">これらの値がコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-146">And it displays these values in the console window.</span></span> <span data-ttu-id="d4f6e-147">最後に、コンソール ウィンドウにプロンプトを表示し、<xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> メソッドを呼び出してユーザーによる入力を待ちます。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-147">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="d4f6e-148"><xref:System.Environment.NewLine> は、プラットフォームに依存せず、言語に依存せずに、改行を表す方法です。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-148"><xref:System.Environment.NewLine> is a platform-independent and language-independent way to represent a line break.</span></span> <span data-ttu-id="d4f6e-149">代替手段は、C# では `\n`、Visual Basic では `vbCrLf` です。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-149">Alternatives are `\n` in C# and `vbCrLf` in Visual Basic.</span></span>

   <span data-ttu-id="d4f6e-150">文字列の前にドル記号 (`$`) を付けると、変数名などの式を文字列で中かっこで囲むことができます。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-150">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="d4f6e-151">式の値が、式の代わりに文字列に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-151">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="d4f6e-152">この構文は、[補間された文字列](../../csharp/language-reference/tokens/interpolated.md)と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-152">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="d4f6e-153"><kbd>Ctrl</kbd> + <kbd>F5</kbd> キーを押して、デバッグなしでプログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-153">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

1. <span data-ttu-id="d4f6e-154">プロンプトに対し、名前を入力し、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-154">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="./media/with-visual-studio/hello-world-update.png" alt-text="プログラムの出力が変更されたコンソール ウィンドウ":::

1. <span data-ttu-id="d4f6e-156">任意のキーを押して、コンソール ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-156">Press any key to close the console window.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d4f6e-157">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="d4f6e-157">Additional resources</span></span>

- [<span data-ttu-id="d4f6e-158">現在のリリースと長期的なサポート リリース</span><span class="sxs-lookup"><span data-stu-id="d4f6e-158">Current releases and long-term support releases</span></span>](../releases-and-support.md#net-core-and-net-5-version-lifecycles)

## <a name="next-steps"></a><span data-ttu-id="d4f6e-159">次のステップ</span><span class="sxs-lookup"><span data-stu-id="d4f6e-159">Next steps</span></span>

<span data-ttu-id="d4f6e-160">このチュートリアルでは、.NET コンソール アプリケーションを作成しました。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-160">In this tutorial, you created a .NET console application.</span></span> <span data-ttu-id="d4f6e-161">次のチュートリアルでは、アプリをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="d4f6e-161">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d4f6e-162">Visual Studio を使用して .NET コンソール アプリケーションをデバッグする</span><span class="sxs-lookup"><span data-stu-id="d4f6e-162">Debug a .NET console application using Visual Studio</span></span>](debugging-with-visual-studio.md)
