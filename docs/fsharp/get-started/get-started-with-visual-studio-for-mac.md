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
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Visual Studio for Mac での F# の概要

Visual Studio for Mac IDE では F# と Visual F# のツールがサポートされています。 [Visual Studio for Mac がインストールされている](install-fsharp.md#install-f-with-visual-studio-for-mac)ことを確認してください。

## <a name="creating-a-console-application"></a>コンソール アプリケーションの作成

Visual Studio for Mac の最も基本的なプロジェクトの 1 つは、コンソール アプリケーションです。  その方法を次に示します。  Visual Studio for Mac が開いたら:

1. **[ファイル]** メニューの **[新しいソリューション]** をポイントします。

2. [新しいプロジェクト] ダイアログには、コンソール アプリケーション用の 2 つの異なるテンプレートがあります。  1 つは [その他] -> [.NET] の下にあり、.NET Framework を対象としています。  その他のテンプレートは [.NET Core] -> [アプリ] の下にあり、.NET Core を対象としています。  どちらのテンプレートも、この記事の目的に使用できます。

3. コンソール アプリで、必要に応じて C# を F# に変更します。  **[次へ]** ボタンをクリックして先に進みます。  

4. プロジェクトに名前を付け、アプリに必要なオプションを選択します。  画面の端にあるプレビュー ペインに注意してください。ここには、選択したオプションに基づいて作成されるディレクトリ構造が表示されます。  

5. **[作成]** をクリックします。  これでソリューション エクスプローラーに F# プロジェクトが表示されます。

## <a name="writing-your-code"></a>コードを書く

まず、コードをいくつか記述してみましょう。  `Program.fs` ファイルが開いていることを確認し、その内容を以下に置き換えます。

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

前のコード サンプルでは、`x` という名前の入力を受け取り、それをそれ自体で乗算する関数 `square` が定義されています。  F# では[型の推定](../language-reference/type-inference.md)が使用されるため、`x` の型を指定する必要はありません。  F# コンパイラにより、乗算が有効な型が認識され、`square` の呼び出し方法に基づいて型が `x` に割り当てられます。  マウス ポインターを `square` に合わせると、次のように表示されます。

```console
val square: x:int -> int
```

これは、関数の型シグネチャとして知られています。  これは、"Square は、x という整数を受け取り、整数を生成する関数です" のように解釈できます。  コンパイラによって、現段階では `square` に `int` の型が設定されたことに注意してください。これは、乗算が "*すべて*" の型に対してジェネリックではなく、閉じられた型のセット内でジェネリックであるためです。  この時点で F# コンパイラによって `int` が選択されますが、`float` などの別の入力型を使用して `square` を呼び出すと、型シグネチャが調整されます。

`EntryPoint` 属性で装飾された別の関数 `main` が定義されています。これにより、プログラムの実行をそこから開始する必要があることが F# コンパイラに指示されます。  これは、他の [C スタイルのプログラミング言語](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)と同じ規則に従います。コマンドライン引数をこの関数に渡すことができ、整数のコードが返される (通常は `0`) というものです。

これはこの関数内にあり、`12` の引数を指定して `square` 関数を呼び出します。  次に F# コンパイラによって、`int -> int` になるように `square` の型が割り当てられます (つまり、`int` を受け取り、`int` を生成する関数)。  `printfn` の呼び出しは書式設定済みの印刷関数であり、C スタイルのプログラミング言語に似た書式指定文字列と、書式指定文字列で指定されたものに対応するパラメーターを使用し、結果と改行を出力します。

## <a name="running-your-code"></a>コードの実行

トップ レベル メニューの **[実行]** 、続いて **[デバッグなしで開始]** をクリックして、コードを実行し、結果を確認できます。  これにより、プログラムがデバッグなしで実行され、結果を確認できるようになります。

Visual Studio for Mac によって開かれたコンソール ウィンドウに次の出力が表示されます。

```console
12 squared is 144!
```

お疲れさまでした。  最初の F# プロジェクトを Visual Studio for Mac で作成し、その関数を呼び出した結果を出力する F# 関数を記述し、プロジェクトを実行して結果を確認しました。

## <a name="using-f-interactive"></a>F# インタラクティブを使用する

Visual Studio for Mac の Visual F# ツールの最も優れた機能の 1 つは、F# インタラクティブ ウィンドウです。  これを使用すると、コードを呼び出して結果を対話形式で確認できるプロセスにコードを送信できます。

その使用を開始するには、コードで定義されている `square` 関数を強調表示します。  次に、トップ レベル メニューの **[編集]** をクリックします。  次に、 **[選択項目を F# インタラクティブに送信する]** を選択します。  これにより、F# インタラクティブ ウィンドウのコードが実行されます。  または、選択範囲を右クリックし、 **[選択項目を F# インタラクティブに送信する]** を選択します。  F# インタラクティブ ウィンドウが表示され、そこに次のように表示されます。

```console
>

val square : x:int -> int

>
```

これは、前に関数をポイントしたときに表示されたものと同じ `square` 関数の関数シグネチャを示しています。  `square` は現在 F# インタラクティブ プロセスで定義されているため、異なる値を使用して呼び出すことができます。

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

これにより、関数が実行され、結果が新しい名前 `it` にバインドされ、`it` の型と値が表示されます。  各行は、`;;` で終了する必要があることに注意してください。  こうすることで、関数呼び出しがいつ終了するかを F# インタラクティブが認識できます。  F# インタラクティブで新しい関数を定義することもできます。

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

上では新しい関数 `isOdd` が定義されています。これは、`int` を受け取り、それが奇数かどうかを確認するものです。  この関数を呼び出して、さまざまな入力で何が返されるかを確認できます。  関数呼び出しの中で関数を呼び出すことができます。

```console
> isOdd (square 15);;
val it : bool = true
```

[パイプ転送演算子](../language-reference/symbol-and-operator-reference/index.md)を使用して、値を 2 つの関数にパイプライン処理することもできます。

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

パイプ転送演算子などについては、以降のチュートリアルで詳しく説明します。

ここでは、F# インタラクティブを使用してできることを簡単に確認しています。  詳細については、「[F# による対話型プログラミング](../tools/fsharp-interactive/index.md)」をご覧ください。

## <a name="next-steps"></a>次のステップ

まだ行っていない場合は、F# 言語のコア機能の一部を紹介している「[F# のツアー](../tour.md)」をご覧ください。  F# の一部の機能の概要と、Visual Studio for Mac にコピーして実行できる充実したコード サンプルが用意されています。  優れた外部リソースも使用できます。それについては「[F# ガイド](../index.yml)」で紹介しています。

## <a name="see-also"></a>関連項目

- [F# ガイド](../index.yml)
- [F# のツアー](../tour.md)
- [F# 言語リファレンス](../language-reference/index.md)
- [型の推定](../language-reference/type-inference.md)
- [シンボルと演算子のリファレンス](../language-reference/symbol-and-operator-reference/index.md)
