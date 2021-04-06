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
# <a name="tutorial-create-a-net-console-application-using-visual-studio"></a>チュートリアル: Visual Studio を使用して .NET コンソール アプリケーションを作成する

このチュートリアルでは、Visual Studio 2019 で .NET コンソール アプリケーションを作成して実行する方法を示します。

## <a name="prerequisites"></a>必須コンポーネント

- **.NET Core クロスプラットフォーム開発** ワークロードがインストールされている [Visual Studio 2019 バージョン 16.9.2 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。 このワークロードを選択すると、.NET 5.0 SDK が自動的にインストールされます。

  詳細については、[Visual Studio を使用した .NET SDK のインストール](../install/windows.md#install-with-visual-studio)に関する記述を参照してください。

## <a name="create-the-app"></a>アプリを作成する

"HelloWorld" という名前の .NET コンソール アプリ プロジェクトを作成します。

1. Visual Studio 2019 を起動します。

1. スタート ページで、 **[新しいプロジェクトの作成]** を選択します。

   :::image type="content" source="./media/with-visual-studio/start-window.png" alt-text="Visual Studio のスタート ページで [新しいプロジェクトの作成] ボタンが選択されている":::

1. **[新しいプロジェクトの作成]** ページで、検索ボックスに「**コンソール**」と入力します。 次に、言語の一覧から **[C#]** または **[Visual Basic]** を選択してから、プラットフォームの一覧から **[すべてのプラットフォーム]** を選択します。 **[コンソール アプリケーション]** テンプレートを選んでから、 **[次へ]** を選択します。

   :::image type="content" source="./media/with-visual-studio/create-new-project.png" alt-text="フィルターが選択された状態の [新しいプロジェクトの作成] ウィンドウ":::

   > [!TIP]
   > .NET テンプレートが表示されない場合は、必要なワークロードが欠落しているおそれがあります。 **[お探しの情報が見つかりませんでしたか?]** メッセージで、 **[さらにツールと機能をインストールする]** リンクを選択します。 Visual Studio インストーラーが開きます。 **.NET Core クロスプラットフォーム開発** ワークロードがインストールされていることを確認してください。

1. **[新しいプロジェクトの構成]** ダイアログで、 **[プロジェクト名]** ボックスに「**HelloWorld**」と入力します。 **[次へ]** を選びます。

   :::image type="content" source="./media/with-visual-studio/configure-new-project.png" alt-text="プロジェクト名、場所、およびソリューション名のフィールドを使用して新しいプロジェクト ウィンドウを構成します":::

1. **[追加情報]** ダイアログで、 **[.NET 5.0 (Current)]** を選んでから、 **[作成]** を選択します。

   :::image type="content" source="media/with-visual-studio/additional-info.png" alt-text="[追加情報] ダイアログ":::

このテンプレートでは、シンプルな "Hello World" アプリケーションを作成します。 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> メソッドを呼び出し、"Hello World!" を コンソール ウィンドウに表示します。

テンプレート コードでは、引数として <xref:System.String> 配列を受け取る単一のメソッド `Main` を含む、`Program` というクラスが定義されます。

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

`Main` はアプリケーションのエントリ ポイントで、アプリケーションを起動するときに、ランタイムによって自動的に呼び出されるメソッドです。 アプリケーションが起動されるときに提供されるコマンドライン引数はすべて *args* 配列にあります。

使用する言語で表示されていない場合は、ページの上部にある言語セレクターを変更します。

## <a name="run-the-app"></a>アプリを実行する

1. <kbd>Ctrl</kbd> + <kbd>F5</kbd> キーを押して、デバッグなしでプログラムを実行します。

   コンソール ウィンドウが開き、"Hello World!" というテキストが 画面に出力されます。

   :::image type="content" source="./media/with-visual-studio/hello-world-console.png" alt-text="Hello World Press any key to continue と表示されているコンソール ウィンドウ":::

1. 任意のキーを押して、コンソール ウィンドウを閉じます。

## <a name="enhance-the-app"></a>アプリを拡張する

アプリケーションを拡張し、ユーザーに名前の入力を求め、日付と時刻と共にそれを表示するようにします。

1. *Program.cs* または *Program.vb* で、`Main` メソッドの内容 (`Console.WriteLine` を呼び出す行です) を、次のコードに置き換えます。

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   このコードによりコンソール ウィンドウにプロンプトが表示され、ユーザーが文字列を入力して <kbd>Enter</kbd> キーを押すまで待機します。 これはこの文字列を `name` という変数に格納します。 さらに現在の現地時刻を含む <xref:System.DateTime.Now?displayProperty=nameWithType> プロパティの値を取得して、それを `currentDate` という変数に代入します。 これらの値がコンソール ウィンドウに表示されます。 最後に、コンソール ウィンドウにプロンプトを表示し、<xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> メソッドを呼び出してユーザーによる入力を待ちます。

   <xref:System.Environment.NewLine> は、プラットフォームに依存せず、言語に依存せずに、改行を表す方法です。 代替手段は、C# では `\n`、Visual Basic では `vbCrLf` です。

   文字列の前にドル記号 (`$`) を付けると、変数名などの式を文字列で中かっこで囲むことができます。 式の値が、式の代わりに文字列に挿入されます。 この構文は、[補間された文字列](../../csharp/language-reference/tokens/interpolated.md)と呼ばれます。

1. <kbd>Ctrl</kbd> + <kbd>F5</kbd> キーを押して、デバッグなしでプログラムを実行します。

1. プロンプトに対し、名前を入力し、<kbd>Enter</kbd> キーを押します。

   :::image type="content" source="./media/with-visual-studio/hello-world-update.png" alt-text="プログラムの出力が変更されたコンソール ウィンドウ":::

1. 任意のキーを押して、コンソール ウィンドウを閉じます。

## <a name="additional-resources"></a>その他のリソース

- [現在のリリースと長期的なサポート リリース](../releases-and-support.md#net-core-and-net-5-version-lifecycles)

## <a name="next-steps"></a>次のステップ

このチュートリアルでは、.NET コンソール アプリケーションを作成しました。 次のチュートリアルでは、アプリをデバッグします。

> [!div class="nextstepaction"]
> [Visual Studio を使用して .NET コンソール アプリケーションをデバッグする](debugging-with-visual-studio.md)
