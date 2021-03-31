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
# <a name="tutorial-test-a-net-class-library-using-visual-studio-code"></a>チュートリアル: Visual Studio Code を使用して .NET クラス ライブラリをテストする

このチュートリアルでは、テスト プロジェクトをソリューションに追加して、単体テストを自動化する方法について説明します。

## <a name="prerequisites"></a>必須コンポーネント

- このチュートリアルでは、「[Visual Studio Code を使用して .NET クラス ライブラリを作成する](library-with-visual-studio-code.md)」で作成するソリューションを使用します。

## <a name="create-a-unit-test-project"></a>単体テスト プロジェクトを作成する

単体テストでは、開発および公開時に自動化されたソフトウェア テストが提供されます。 このチュートリアルで使用するテスト フレームワークは MSTest です。 [MSTest](https://github.com/Microsoft/testfx-docs) は、選択できる 3 つのテスト フレームワークのうちの 1 つです。 これ以外は、[xUnit](https://xunit.net/) と [nUnit](https://nunit.org/) です。

1. Visual Studio Code を開始します。

1. 「[Visual Studio Code を使用して .NET クラス ライブラリを作成する](library-with-visual-studio-code.md)」で作成した `ClassLibraryProjects` ソリューションを開きます。

1. 「StringLibraryTest」という名前の単体テスト プロジェクトを作成します。

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   プロジェクト テンプレートでは、次のコードを使用して UnitTest1.cs ファイルを作成します。

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

   単体テストのテンプレートで作成されたソース コードにより、次の処理が行われます。

   - 単体テストで使用される型が含まれた <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 名前空間がインポートされます。
   - <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 属性が `UnitTest1` クラスに適用されます。
   - <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 属性を適用して `TestMethod1` を定義します。

   [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute)でタグ付けされたテスト クラスの [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) でタグ付けされた各テスト メソッドが、単体テスト実行時に自動実行されます。

1. 次のように、テスト プロジェクトをソリューションに追加します。

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

## <a name="add-a-project-reference"></a>プロジェクト参照を追加する

テスト プロジェクトが `StringLibrary` クラスと連動するように、`StringLibraryTest` プロジェクトに `StringLibrary` プロジェクトへの参照を追加します。

1. 次のコマンドを実行します。

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

## <a name="add-and-run-unit-test-methods"></a>単体テスト メソッドの追加と実行

Visual Studio で単体テストを実行すると、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 属性でマークされたクラス内で、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 属性でマークされた各メソッドが実行されます。 テスト メソッドは、最初の失敗が検出されたとき、またはそのメソッドに含まれているすべてのテストが成功したときに終了します。

一般的なテストでは、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> クラスのメンバーが呼び出されます。 多くのアサート メソッドは最低 2 つのパラメーターを含んでいます。1 つは予期されるテスト結果、もう 1 つは実際のテスト結果です。 次の表に、`Assert` クラスの頻繁に呼び出されるメソッドをいくつか示します。

| Assert メソッド     | 関数 |
| ------------------ | -------- |
| `Assert.AreEqual`  | 2 つの値または 2 つのオブジェクトが等しいことを確認します。 値またはオブジェクトが等しくない場合、アサートは失敗します。 |
| `Assert.AreSame`   | 2 つのオブジェクト変数が同じオブジェクトを参照していることを確認します。 変数が別々のオブジェクトを参照している場合、アサートは失敗します。 |
| `Assert.IsFalse`   | 条件が `false` であることを確認します。 条件が `true` の場合、アサートは失敗します。 |
| `Assert.IsNotNull` | オブジェクトが `null` でないことを確認します。 オブジェクトが `null` である場合、アサートは失敗します。 |

また、テスト メソッドで <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> メソッドを使用して、スローすることが期待される例外の種類を示すこともできます。 指定した例外がスローされない場合、テストは失敗します。

`StringLibrary.StartsWithUpper` メソッドのテストでは、大文字で始まる文字列を多く用意します。 これらの場合ではメソッドが `true` を返すと予測されるので、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> メソッドを呼び出すことができます。 同様に、大文字以外で始まる文字列を多く用意します。 これらの場合ではメソッドが `false` を返すと予測されるので、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> メソッドを呼び出すことができます。

ライブラリ メソッドでは文字列を処理するため、[空の文字列 (`String.Empty`)](xref:System.String.Empty) および `null` 文字列を正常に処理することも確認します。 空の文字列は、文字を含まない、<xref:System.String.Length> が 0 の文字列です。 `null` 文字列は、初期化されていない文字列です。 しかし、`StartsWithUpper` を静的メソッドとして直接呼び出して、単一の <xref:System.String> 引数を渡すこともできます。 または、`null` に割り当てられた `string` 変数の拡張メソッドとして `StartsWithUpper` を呼び出すこともできます。

メソッドを 3 つ定義します。これらのメソッドでは、文字列配列の各要素に対して <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> メソッドが呼び出されます。 メソッドのオーバーロードを呼び出します。これにより、テストが失敗した場合に表示されるエラー メッセージを指定できます。 このメッセージによって、エラーの原因となった文字列が識別されます。

テスト メソッドを作成するには

1. *StringLibraryTest/UnitTest1.cs* を開き、すべてのコードを次のコードに置き換えます。

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   `TestStartsWithUpper` メソッドの大文字のテストには、ギリシャ語の大文字のアルファ (U+0391) とキリル文字の大文字 EM (U+041C) が含まれています。 `TestDoesNotStartWithUpper` メソッドの小文字のテストには、ギリシャ語の小文字のアルファ (U+03B1) とキリル文字の小文字 Ghe (U+0433) が含まれています。

1. 変更内容を保存します。

1. テストを実行します。

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   次のターミナル出力は、すべてのテストが成功したことを示しています。

   ```output
   Starting test execution, please wait...
   A total of 1 test files matched the specified pattern.

   Passed!  - Failed:     0, Passed:     3, Skipped:     0, Total:     3, Duration: 3 ms - StringLibraryTest.dll (net5.0)
   ```

## <a name="handle-test-failures"></a>テストの失敗の処理

テスト駆動開発 (TDD) を行っている場合、最初にテストを作成すると、1 回目のテスト実行は失敗します。 その後、テストを成功させるコードをアプリに追加します。 このチュートリアルでは、検証するアプリ コードを記述した後にテストを作成したため、テストが失敗することはありませんでした。 テストの失敗が予想されるときにテストが失敗することを検証するには、テスト入力に無効な値を追加します。

1. `TestDoesNotStartWithUpper` メソッドの `words` 配列を変更し、文字列 "Error" を含めます。

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. テストを実行します。

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   ターミナルの出力では、1 つのテストが失敗したことが示され、失敗したテストに関するエラー メッセージが表示されます。"Assert.IsFalse failed. Expected for 'Error': false; actual:True" が表示されます。 エラーのため、配列内の "Error" の後ろの文字列はテストされませんでした。

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

1. 手順 1 で追加した文字列 "Error" を削除します。 テストを再実行すると、テストは成功します。

## <a name="test-the-release-version-of-the-library"></a>ライブラリのリリース バージョンのテスト

これで、ライブラリのデバッグ ビルドを実行したときにすべてのテストが成功したので、さらにライブラリのリリース ビルドに対してテストを行います。 コンパイラの最適化などのさまざまな要因により、デバッグ ビルドとリリース ビルドとでは動作が異なる場合があります。

1. リリース ビルド構成を使用してテストを実行します。

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   テストが成功します。

## <a name="debug-tests"></a>テストのデバッグ

IDE として Visual Studio Code を使用する場合は、「[Visual Studio Code を使用して .NET コンソール アプリケーションをデバッグする](debugging-with-visual-studio-code.md)」に示されているのと同じプロセスを使用し、単体テスト プロジェクトを使ってコードをデバッグできます。 *ShowCase* アプリ プロジェクトを開始する代わりに、*StringLibraryTest/UnitTest1.cs* を開き、7 行目と 8 行目の間で **[すべてのテストを実行する]** を選択します。 見つからない場合は、<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> キーを押してコマンド パレットを開き、「**Reload Window**」と入力します。

Visual Studio Code により、デバッガーがアタッチされた状態でテスト プロジェクトが開始されます。 実行は、テスト プロジェクトまたは基になるライブラリ コードに追加したブレークポイントで停止します。

## <a name="additional-resources"></a>その他の技術情報

* [.NET での単体テスト](../testing/index.md)

## <a name="next-steps"></a>次の手順

このチュートリアルでは、クラス ライブラリの単体テストを行いました。 ライブラリをパッケージとして [NuGet](https://nuget.org) に発行した場合、他のユーザーもそれを使用できます。 方法については、次の NuGet のチュートリアルに従ってください。

> [!div class="nextstepaction"]
> [dotnet CLI を使用したパッケージの作成と公開](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

ライブラリを NuGet パッケージとして発行した場合、他のユーザーもそれをインストールして使用できます。 方法については、次の NuGet のチュートリアルに従ってください。

> [!div class="nextstepaction"]
> [dotnet CLI を使用してパッケージをインストールし使用する](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

ライブラリはパッケージとして配布する必要はありません。 それが使用されるコンソール アプリにバンドルすることができます。 コンソール アプリを発行する方法については、このシリーズの前のチュートリアルを参照してください。

> [!div class="nextstepaction"]
> [Visual Studio Code を使用して .NET コンソール アプリケーションを発行する](publishing-with-visual-studio-code.md)
