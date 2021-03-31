---
title: Visual Studio を使用して .NET コンソール アプリケーションを作成する
description: Visual Studio を使用して、C# または Visual Basic で .NET コンソール アプリケーションを作成する方法について学習します。
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 3986ef4083b964799be33d2876570ac4cf2082b8
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511854"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio"></a><span data-ttu-id="e7eae-103">チュートリアル: Visual Studio を使用して .NET コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="e7eae-103">Tutorial: Create a .NET console application using Visual Studio</span></span>

<span data-ttu-id="e7eae-104">このチュートリアルでは、Visual Studio 2019 で .NET コンソール アプリケーションを作成して実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-104">This tutorial shows how to create and run a .NET console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e7eae-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e7eae-105">Prerequisites</span></span>

- <span data-ttu-id="e7eae-106">**.NET Core クロスプラットフォーム開発** ワークロードがインストールされている [Visual Studio 2019 バージョン 16.8 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="e7eae-106">[Visual Studio 2019 version 16.8 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="e7eae-107">このワークロードを選択すると、.NET 5.0 SDK が自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e7eae-107">The .NET 5.0 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="e7eae-108">詳細については、[Visual Studio を使用した .NET SDK のインストール](../install/windows.md#install-with-visual-studio)に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7eae-108">For more information, see [Install the .NET SDK with Visual Studio](../install/windows.md#install-with-visual-studio).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="e7eae-109">アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="e7eae-109">Create the app</span></span>

<span data-ttu-id="e7eae-110">"HelloWorld" という名前の .NET コンソール アプリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-110">Create a .NET console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="e7eae-111">Visual Studio 2019 を起動します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-111">Start Visual Studio 2019.</span></span>

1. <span data-ttu-id="e7eae-112">**[ツール]**  >  **[オプション]**  >  **[環境]**  >  **[プレビュー機能]** の順に選択してから、 **[[新しいプロジェクト] にすべての .NET Core テンプレートを表示する (再起動が必要)]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="e7eae-112">Select **Tools** > **Options** > **Environment** > **Preview features**, and then select **Show all .NET Core templates in the New project (requires restart)**.</span></span>

   :::image type="content" source="media/with-visual-studio/dotnet-options.png" alt-text="すべての .NET テンプレート オプションを表示する":::

1. <span data-ttu-id="e7eae-114">Visual Studio を閉じて、開き直します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-114">Close and reopen Visual Studio.</span></span>

1. <span data-ttu-id="e7eae-115">スタート ページで、 **[新しいプロジェクトの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-115">On the start page, choose **Create a new project**.</span></span>

   :::image type="content" source="./media/with-visual-studio/start-window.png" alt-text="Visual Studio のスタート ページで [新しいプロジェクトの作成] ボタンが選択されている":::

1. <span data-ttu-id="e7eae-117">**[新しいプロジェクトの作成]** ページで、検索ボックスに「**コンソール**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-117">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="e7eae-118">次に、言語の一覧から **[C#]** または **[Visual Basic]** を選択してから、プラットフォームの一覧から **[すべてのプラットフォーム]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-118">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="e7eae-119">**[コンソール アプリケーション]** テンプレートを選んでから、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-119">Choose the **Console Application** template, and then choose **Next**.</span></span>

   :::image type="content" source="./media/with-visual-studio/create-new-project.png" alt-text="フィルターが選択された状態の [新しいプロジェクトの作成] ウィンドウ":::

   > [!TIP]
   > <span data-ttu-id="e7eae-121">.NET テンプレートが表示されない場合は、必要なワークロードが欠落しているおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="e7eae-121">If you don't see the .NET templates, you're probably missing the required workload.</span></span> <span data-ttu-id="e7eae-122">**[お探しの情報が見つかりませんでしたか?]** メッセージで、 **[さらにツールと機能をインストールする]** リンクを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-122">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="e7eae-123">Visual Studio インストーラーが開きます。</span><span class="sxs-lookup"><span data-stu-id="e7eae-123">The Visual Studio Installer opens.</span></span> <span data-ttu-id="e7eae-124">**.NET Core クロスプラットフォーム開発** ワークロードがインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e7eae-124">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

1. <span data-ttu-id="e7eae-125">**[新しいプロジェクトの構成]** ダイアログで、 **[プロジェクト名]** ボックスに「**HelloWorld**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-125">In the **Configure your new project** dialog,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="e7eae-126">**[次へ]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="e7eae-126">Then choose **Next**.</span></span>

   :::image type="content" source="./media/with-visual-studio/configure-new-project.png" alt-text="プロジェクト名、場所、およびソリューション名のフィールドを使用して新しいプロジェクト ウィンドウを構成します":::

1. <span data-ttu-id="e7eae-128">**[追加情報]** ダイアログで、 **[.NET 5.0 (Current)]** を選んでから、 **[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-128">In the **Additional information** dialog, select **.NET 5.0 (Current)**, and then select **Create**.</span></span>

   :::image type="content" source="media/with-visual-studio/additional-info.png" alt-text="[追加情報] ダイアログ":::

<span data-ttu-id="e7eae-130">このテンプレートでは、シンプルな "Hello World" アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-130">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="e7eae-131"><xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> メソッドを呼び出し、"Hello World!" を</span><span class="sxs-lookup"><span data-stu-id="e7eae-131">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="e7eae-132">コンソール ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-132">in the console window.</span></span>

<span data-ttu-id="e7eae-133">テンプレート コードでは、引数として <xref:System.String> 配列を受け取る単一のメソッド `Main` を含む、`Program` というクラスが定義されます。</span><span class="sxs-lookup"><span data-stu-id="e7eae-133">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="e7eae-134">`Main` はアプリケーションのエントリ ポイントで、アプリケーションを起動するときに、ランタイムによって自動的に呼び出されるメソッドです。</span><span class="sxs-lookup"><span data-stu-id="e7eae-134">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="e7eae-135">アプリケーションが起動されるときに提供されるコマンドライン引数はすべて *args* 配列にあります。</span><span class="sxs-lookup"><span data-stu-id="e7eae-135">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="e7eae-136">使用する言語で表示されていない場合は、ページの上部にある言語セレクターを変更します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-136">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="e7eae-137">アプリを実行する</span><span class="sxs-lookup"><span data-stu-id="e7eae-137">Run the app</span></span>

1. <span data-ttu-id="e7eae-138"><kbd>Ctrl</kbd> + <kbd>F5</kbd> キーを押して、デバッグなしでプログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-138">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

   <span data-ttu-id="e7eae-139">コンソール ウィンドウが開き、"Hello World!" というテキストが</span><span class="sxs-lookup"><span data-stu-id="e7eae-139">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="e7eae-140">画面に出力されます。</span><span class="sxs-lookup"><span data-stu-id="e7eae-140">printed on the screen.</span></span>

   :::image type="content" source="./media/with-visual-studio/hello-world-console.png" alt-text="Hello World Press any key to continue と表示されているコンソール ウィンドウ":::

1. <span data-ttu-id="e7eae-142">任意のキーを押して、コンソール ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e7eae-142">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="e7eae-143">アプリを拡張する</span><span class="sxs-lookup"><span data-stu-id="e7eae-143">Enhance the app</span></span>

<span data-ttu-id="e7eae-144">アプリケーションを拡張し、ユーザーに名前の入力を求め、日付と時刻と共にそれを表示するようにします。</span><span class="sxs-lookup"><span data-stu-id="e7eae-144">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="e7eae-145">*Program.cs* または *Program.vb* で、`Main` メソッドの内容 (`Console.WriteLine` を呼び出す行です) を、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e7eae-145">In *Program.cs* or *Program.vb*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   <span data-ttu-id="e7eae-146">このコードによりコンソール ウィンドウにプロンプトが表示され、ユーザーが文字列を入力して <kbd>Enter</kbd> キーを押すまで待機します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-146">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="e7eae-147">これはこの文字列を `name` という変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-147">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="e7eae-148">さらに現在の現地時刻を含む <xref:System.DateTime.Now?displayProperty=nameWithType> プロパティの値を取得して、それを `date` という変数に代入します (Visual Basic では `currentDate`)。</span><span class="sxs-lookup"><span data-stu-id="e7eae-148">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="e7eae-149">これらの値がコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e7eae-149">And it displays these values in the console window.</span></span> <span data-ttu-id="e7eae-150">最後に、コンソール ウィンドウにプロンプトを表示し、<xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> メソッドを呼び出してユーザーによる入力を待ちます。</span><span class="sxs-lookup"><span data-stu-id="e7eae-150">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="e7eae-151"><xref:System.Environment.NewLine> は、プラットフォームに依存せず、言語に依存せずに、改行を表す方法です。</span><span class="sxs-lookup"><span data-stu-id="e7eae-151"><xref:System.Environment.NewLine> is a platform-independent and language-independent way to represent a line break.</span></span> <span data-ttu-id="e7eae-152">代替手段は、C# では `\n`、Visual Basic では `vbCrLf` です。</span><span class="sxs-lookup"><span data-stu-id="e7eae-152">Alternatives are `\n` in C# and `vbCrLf` in Visual Basic.</span></span>

   <span data-ttu-id="e7eae-153">文字列の前にドル記号 (`$`) を付けると、変数名などの式を文字列で中かっこで囲むことができます。</span><span class="sxs-lookup"><span data-stu-id="e7eae-153">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="e7eae-154">式の値が、式の代わりに文字列に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="e7eae-154">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="e7eae-155">この構文は、[補間された文字列](../../csharp/language-reference/tokens/interpolated.md)と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="e7eae-155">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="e7eae-156"><kbd>Ctrl</kbd> + <kbd>F5</kbd> キーを押して、デバッグなしでプログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-156">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

1. <span data-ttu-id="e7eae-157">プロンプトに対し、名前を入力し、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e7eae-157">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="./media/with-visual-studio/hello-world-update.png" alt-text="プログラムの出力が変更されたコンソール ウィンドウ":::

1. <span data-ttu-id="e7eae-159">任意のキーを押して、コンソール ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e7eae-159">Press any key to close the console window.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e7eae-160">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="e7eae-160">Additional resources</span></span>

- [<span data-ttu-id="e7eae-161">現在のリリースと長期的なサポート リリース</span><span class="sxs-lookup"><span data-stu-id="e7eae-161">Current releases and long-term support releases</span></span>](../releases-and-support.md#net-core-and-net-5-version-lifecycles)

## <a name="next-steps"></a><span data-ttu-id="e7eae-162">次のステップ</span><span class="sxs-lookup"><span data-stu-id="e7eae-162">Next steps</span></span>

<span data-ttu-id="e7eae-163">このチュートリアルでは、.NET コンソール アプリケーションを作成しました。</span><span class="sxs-lookup"><span data-stu-id="e7eae-163">In this tutorial, you created a .NET console application.</span></span> <span data-ttu-id="e7eae-164">次のチュートリアルでは、アプリをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="e7eae-164">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e7eae-165">Visual Studio を使用して .NET コンソール アプリケーションをデバッグする</span><span class="sxs-lookup"><span data-stu-id="e7eae-165">Debug a .NET console application using Visual Studio</span></span>](debugging-with-visual-studio.md)
