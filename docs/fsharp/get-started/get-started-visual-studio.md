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
# <a name="get-started-with-f-in-visual-studio"></a>Visual Studio での F+ の概要

F# と Visual F# のツールが Visual Studio 統合開発環境 (IDE) でサポートされています。

開始するには、[Visual Studio が F# のサポート付きでインストールされていること](install-fsharp.md#install-f-with-visual-studio)を確認します。

## <a name="create-a-console-application"></a>コンソール アプリケーションの作成

Visual Studio の最も基本的なプロジェクトの 1 つは、コンソール アプリです。 作成手順は次のとおりです。

1. Visual Studio 2019 を開きます。

2. スタート ウィンドウで、 **[新しいプロジェクトの作成]** を選択します。

3. **[新しいプロジェクトの作成]** ページで、言語の一覧から **[F#]** を選択します。

4. **[コンソール アプリ (.NET Core)]** テンプレートを選択し、 **[次へ]** を選択します。

5. **[新しいプロジェクトの構成]** ページで、 **[プロジェクト名]** ボックスに名前を入力します。 次に、 **[作成]** を選択します。

   Visual Studio によって新しい F# プロジェクトが作成されます。 これはソリューション エクスプローラー ウィンドウで確認できます。

## <a name="write-the-code"></a>コードを作成する

まず、コードをいくつか記述してみましょう。 `Program.fs` ファイルが開いていることを確認し、その内容を次の内容に置き換えます。

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

前のコード サンプルでは、`x` という名前の入力を受け取り、それをそれ自体で乗算する `square` という関数を定義しています。 F# では[型の推定](../language-reference/type-inference.md)が使用されるため、`x` の型を指定する必要はありません。 F# コンパイラでは、乗算が有効な型を認識し、`square` の呼び出し方法に基づいて型を `x` に割り当てます。 マウスポインターを `square` に合わせると、次のように表示されます。

```fsharp
val square: x:int -> int
```

これは、関数の型シグネチャとして知られています。 これは、次のように解釈できます。"Square は、x という整数を受け取り、整数を生成する関数です。" コンパイラによって、現段階では、`square` に `int` の型が設定されました。これは、乗算が *すべて* の型ではなく、閉じられた型のセットでジェネリックであるためです。 `float` などの別の入力型を使用して `square` を呼び出すと、F# コンパイラによって型シグネチャが調整されます。

`EntryPoint` 属性で装飾された別の関数 `main` が定義されています。 この属性により、プログラムの実行をそこから開始する必要があることが F# コンパイラに指示されます。 これは、他の [C スタイルのプログラミング言語](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)と同じ規則に従います。コマンドライン引数をこの関数に渡すことができ、整数のコードが返される (通常は `0`) というものです。

エントリ ポイント関数 `main` の中において、`12` の引数を使用して `square` 関数を呼び出します。 次に F# コンパイラは、`int -> int` になるように `square` の型を割り当てます (つまり、`int` を受け取り、`int` を生成する関数)。 `printfn` の呼び出しは、書式指定文字列を使用して結果 (と改行) を出力する書式設定済みの印刷関数です。 書式指定文字列には、C スタイルのプログラミング言語と同様に、渡される引数 (この場合は `12` と `(square 12)`) に対応するパラメーター (`%d`) があります。

## <a name="run-the-code"></a>コードの実行

**Ctrl** + **F5** を押してコードを実行し、結果を確認することができます。 または、最上部のメニュー バーから **[デバッグ]**  >  **[デバッグなしで開始]** を選択することもできます。 これにより、デバッグなしでプログラムが実行されます。

Visual Studio によって開かれたコンソール ウィンドウに以下の出力が表示されます。

```console
12 squared is: 144!
```

お疲れさまでした。 Visual Studio で最初の F# プロジェクトを作成し、値を計算して出力する F# 関数を記述し、プロジェクトを実行して結果を確認しました。

## <a name="next-steps"></a>次のステップ

まだの方は、F# 言語のコア機能の一部をご紹介している「[F# のツアー](../tour.md)」をご覧ください。 F# の一部の機能の概要と、Visual Studio にコピーして実行できる充実したコード サンプルが用意されています。

> [!div class="nextstepaction"]
> [F# のツアー](../tour.md)

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](../language-reference/index.md)
- [型の推定](../language-reference/type-inference.md)
- [シンボルと演算子のリファレンス](../language-reference/symbol-and-operator-reference/index.md)
