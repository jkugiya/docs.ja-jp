---
title: Visual Studio for Mac を使用して .NET コンソール アプリケーションを作成する
description: Visual Studio for Mac を使用して .NET コンソール アプリケーションを作成する方法について説明します。
ms.date: 11/30/2020
ms.openlocfilehash: 4add8309338b8618265a66b9e71dab2df38ca8d0
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511828"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="98674-103">チュートリアル: Visual Studio for Mac を使用して .NET コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="98674-103">Tutorial: Create a .NET console application using Visual Studio for Mac</span></span>

<span data-ttu-id="98674-104">このチュートリアルでは、Visual Studio for Mac を使用して .NET コンソール アプリケーションを作成および実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="98674-104">This tutorial shows how to create and run a .NET console application using Visual Studio for Mac.</span></span>

> [!NOTE]
> <span data-ttu-id="98674-105">お客様のフィードバックは非常に貴重です。</span><span class="sxs-lookup"><span data-stu-id="98674-105">Your feedback is highly valued.</span></span> <span data-ttu-id="98674-106">次の 2 つの方法で Visual Studio for Mac の開発チームにフィードバックを送信できます。</span><span class="sxs-lookup"><span data-stu-id="98674-106">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="98674-107">Visual Studio for Mac で、メニューから **[ヘルプ]**  >  **[問題の報告]** の順に選択するか、ようこそ画面から **[問題の報告]** を選択して、バグ報告を提出するためのウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="98674-107">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="98674-108">お客様のフィードバックは、[開発者コミュニティ](https://aka.ms/feedback/report?space=41) ポータルで追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="98674-108">You can track your feedback in the [Developer Community](https://aka.ms/feedback/report?space=41) portal.</span></span>
> * <span data-ttu-id="98674-109">提案するには、メニューから **[ヘルプ]**  >  **[提案の送信]** の順に選択するか、ようこそ画面から **[提案の送信]** を選択し、[Visual Studio for Mac の開発者コミュニティの Web ページ](https://aka.ms/feedback/suggest?space=41)に移動します。</span><span class="sxs-lookup"><span data-stu-id="98674-109">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://aka.ms/feedback/suggest?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="98674-110">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="98674-110">Prerequisites</span></span>

* <span data-ttu-id="98674-111">[Visual Studio for Mac バージョン 8.8 以降](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。</span><span class="sxs-lookup"><span data-stu-id="98674-111">[Visual Studio for Mac version 8.8 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="98674-112">.NET Core をインストールするオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="98674-112">Select the option to install .NET Core.</span></span> <span data-ttu-id="98674-113">.NET 開発の場合、Xamarin のインストールは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="98674-113">Installing Xamarin is optional for .NET development.</span></span> <span data-ttu-id="98674-114">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="98674-114">For more information, see the following resources:</span></span>

  * <span data-ttu-id="98674-115">[チュートリアル: Visual Studio for Mac をインストールする](/visualstudio/mac/installation)。</span><span class="sxs-lookup"><span data-stu-id="98674-115">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="98674-116">[サポート対象の macOS のバージョン](../install/windows.md)。</span><span class="sxs-lookup"><span data-stu-id="98674-116">[Supported macOS versions](../install/windows.md).</span></span>
  * <span data-ttu-id="98674-117">[Visual Studio for Mac でサポートされている .NET のバージョン](/visualstudio/mac/net-core-support)。</span><span class="sxs-lookup"><span data-stu-id="98674-117">[.NET versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="98674-118">アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="98674-118">Create the app</span></span>

1. <span data-ttu-id="98674-119">Visual Studio for Mac を起動します。</span><span class="sxs-lookup"><span data-stu-id="98674-119">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="98674-120">スタート ウィンドウで **[新規]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="98674-120">Select **New** in the start window.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Visual Studio for Mac のスタート ウィンドウの [新規] ボタン":::

1. <span data-ttu-id="98674-122">**[新しいプロジェクト]** ダイアログで、 **[Web and Console]\(Web とコンソール\)** ノードの下にある **[アプリ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="98674-122">In the **New Project** dialog, select **App** under the **Web and Console** node.</span></span> <span data-ttu-id="98674-123">**[コンソール アプリケーション]** テンプレートを選択し、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="98674-123">Select the **Console Application** template, and select **Next**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-dialog.png" alt-text="新しいプロジェクト テンプレートの一覧":::

1. <span data-ttu-id="98674-125">**[Configure your new Console Application]\(新しいコンソール アプリケーションの構成\)** ダイアログの **[ターゲット フレームワーク]** ドロップダウンで、 **[.NET 5.0]** を選択し、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="98674-125">In the **Target Framework** drop-down of the **Configure your new Console Application** dialog, select **.NET 5.0**, and select **Next**.</span></span>

1. <span data-ttu-id="98674-126">**[プロジェクト名]** に「HelloWorld」と入力し、 **[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="98674-126">Type "HelloWorld" for the **Project Name**, and select **Create**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-options.png" alt-text="[Configure your new Console Application]\(新しいコンソール アプリケーションの構成\) ダイアログ":::

<span data-ttu-id="98674-128">このテンプレートでは、シンプルな "Hello World" アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="98674-128">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="98674-129"><xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> メソッドを呼び出し、"Hello World!" を</span><span class="sxs-lookup"><span data-stu-id="98674-129">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="98674-130">ターミナル ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="98674-130">in the terminal window.</span></span>

<span data-ttu-id="98674-131">テンプレート コードでは、引数として <xref:System.String> 配列を受け取る単一のメソッド `Main` を含む、`Program` というクラスが定義されます。</span><span class="sxs-lookup"><span data-stu-id="98674-131">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="98674-132">`Main` はアプリケーションのエントリ ポイントで、アプリケーションを起動するときに、ランタイムによって自動的に呼び出されるメソッドです。</span><span class="sxs-lookup"><span data-stu-id="98674-132">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="98674-133">アプリケーションの起動時に指定されるコマンドライン引数は、`args` 配列から利用できます。</span><span class="sxs-lookup"><span data-stu-id="98674-133">Any command-line arguments supplied when the application is launched are available in the `args` array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="98674-134">アプリを実行する</span><span class="sxs-lookup"><span data-stu-id="98674-134">Run the app</span></span>

1. <span data-ttu-id="98674-135"><kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>command</kbd> + <kbd>enter</kbd>) キーを押して、デバッグなしでアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="98674-135">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run the app without debugging.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-output.png" alt-text="ターミナルに Hello World! が表示される":::

1. <span data-ttu-id="98674-137">**ターミナル** ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="98674-137">Close the **Terminal** window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="98674-138">アプリを拡張する</span><span class="sxs-lookup"><span data-stu-id="98674-138">Enhance the app</span></span>

<span data-ttu-id="98674-139">アプリケーションを拡張し、ユーザーに名前の入力を求め、日付と時刻と共にそれを表示するようにします。</span><span class="sxs-lookup"><span data-stu-id="98674-139">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="98674-140">*Program.cs* で、`Main` メソッドの内容 (`Console.WriteLine` を呼び出す行) を以下のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="98674-140">In *Program.cs*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   <span data-ttu-id="98674-141">このコードによりコンソール ウィンドウにプロンプトが表示され、ユーザーが文字列を入力して <kbd>Enter</kbd> キーを押すまで待機します。</span><span class="sxs-lookup"><span data-stu-id="98674-141">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>enter</kbd> key.</span></span> <span data-ttu-id="98674-142">これはこの文字列を `name` という変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="98674-142">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="98674-143">さらに現在の現地時刻を含む <xref:System.DateTime.Now?displayProperty=nameWithType> プロパティの値を取得して、それを `date` という変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="98674-143">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="98674-144">これらの値がコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="98674-144">And it displays these values in the console window.</span></span> <span data-ttu-id="98674-145">最後に、コンソール ウィンドウにプロンプトを表示し、<xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> メソッドを呼び出してユーザーによる入力を待ちます。</span><span class="sxs-lookup"><span data-stu-id="98674-145">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="98674-146"><xref:System.Environment.NewLine> は、プラットフォームに依存せず、言語に依存せずに、改行を表す方法です。</span><span class="sxs-lookup"><span data-stu-id="98674-146"><xref:System.Environment.NewLine> is a platform-independent and language-independent way to represent a line break.</span></span> <span data-ttu-id="98674-147">代替手段は、C# では `\n`、Visual Basic では `vbCrLf` です。</span><span class="sxs-lookup"><span data-stu-id="98674-147">Alternatives are `\n` in C# and `vbCrLf` in Visual Basic.</span></span>

   <span data-ttu-id="98674-148">文字列の前にドル記号 (`$`) を付けると、変数名などの式を文字列で中かっこで囲むことができます。</span><span class="sxs-lookup"><span data-stu-id="98674-148">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="98674-149">式の値が、式の代わりに文字列に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="98674-149">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="98674-150">この構文は、[補間された文字列](../../csharp/language-reference/tokens/interpolated.md)と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="98674-150">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="98674-151"><kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>command</kbd> + <kbd>enter</kbd>) キーを押して、アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="98674-151">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run the app.</span></span>

1. <span data-ttu-id="98674-152">名前を入力して <kbd>enter</kbd> キーを押すことで、このプロンプトに応答します。</span><span class="sxs-lookup"><span data-stu-id="98674-152">Respond to the prompt by entering a name and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/hello-world-update.png" alt-text="変更されたプログラムの出力を示すターミナル":::

1. <span data-ttu-id="98674-154">ターミナルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="98674-154">Close the terminal.</span></span>

## <a name="next-steps"></a><span data-ttu-id="98674-155">次の手順</span><span class="sxs-lookup"><span data-stu-id="98674-155">Next steps</span></span>

<span data-ttu-id="98674-156">このチュートリアルでは、.NET コンソール アプリケーションを作成しました。</span><span class="sxs-lookup"><span data-stu-id="98674-156">In this tutorial, you created a .NET console application.</span></span> <span data-ttu-id="98674-157">次のチュートリアルでは、アプリをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="98674-157">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="98674-158">Visual Studio for Mac を使用して .NET コンソール アプリケーションをデバッグする</span><span class="sxs-lookup"><span data-stu-id="98674-158">Debug a .NET console application using Visual Studio for Mac</span></span>](debugging-with-visual-studio-mac.md)
