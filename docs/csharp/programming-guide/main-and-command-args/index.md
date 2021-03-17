---
title: Main() とコマンドライン引数 - C# プログラミング ガイド
description: Main() とコマンドライン引数について説明します。 ' Main ' メソッドは、実行可能プログラムのエントリポイントです。
ms.date: 03/08/2021
f1_keywords:
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: 35117642f38885aab08a5c0249d1f65ec76c59f3
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190204"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() とコマンドライン引数 (C# プログラミング ガイド)

`Main` メソッドは、C# アプリケーションのエントリ ポイントです (ライブラリおよびサービスでは、エントリ ポイントとしての `Main` メソッドは必要ありません)。アプリケーションを起動すると、最初に `Main` メソッドが呼び出されます。

C# プログラムのエントリ ポイントは 1 つのみです。 `Main` メソッドを持つクラスが 2 つ以上ある場合、プログラムをコンパイルする際に `-main` コンパイラ オプションを使用して、どの `Main` メソッドをエントリ ポイントとして使用するかを指定する必要があります。 詳細については、「[-main (C# コンパイラ オプション)](../../language-reference/compiler-options/main-compiler-option.md)」を参照してください。

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

C# 9 以降では、次の例のように `Main` メソッドを省略し、`Main` メソッド内にあるかのように C# ステートメントを記述することができます。

:::code language="csharp" source="snippets/top-level-statements-1/Program.cs":::

暗黙的なエントリ ポイント メソッドを使用してアプリケーション コードを記述する方法の詳細については、「[最上位レベルのステートメント](top-level-statements.md)」を参照してください。

## <a name="overview"></a>概要

- `Main` メソッドは実行可能プログラムのエントリ ポイントであり、ここでプログラムの制御を開始および終了します。
- `Main` は、クラスまたは構造体の内部で宣言されます。 `Main` は [static](../../language-reference/keywords/static.md) である必要がありますが、[public](../../language-reference/keywords/public.md) である必要はありません (先ほどの例では、既定の [private](../../language-reference/keywords/private.md) のアクセスを受け取ります)。外側のクラスまたは構造体は、static である必要はありません。
- `Main` の戻り値の型は、`void` または `int` のいずれかになります。C# 7.1 以降では `Task` または `Task<int>` になる場合もあります。
- `Main` で `Task` または `Task<int>` が返される場合に限り、`Main` の宣言に [`async`](../../language-reference/keywords/async.md) 修飾子を含めることができます。 この条件により、`async void Main` メソッドが明確に除外されることに注意してください。
- `Main` メソッドを宣言する際、コマンドライン引数を含む `string[]` パラメーターは指定してもしなくてもかまいません。 Visual Studio を使用して Windows アプリケーションを作成する場合、このパラメーターを手動で追加するか <xref:System.Environment.GetCommandLineArgs> メソッドを使用して、[コマンドライン引数](command-line-arguments.md)を取得できます。 パラメーターは、インデックス 0 のコマンドライン引数として読み取られます。 C や C++ とは異なり、プログラムの名前は、<xref:System.Environment.GetCommandLineArgs> の最初の要素です。`args` 配列の最初のコマンドライン引数として扱われることはありません。

有効な `Main` の署名の一覧を次に示します。

```csharp
public static void Main() { }
public static int Main() { }
public static void Main(string[] args) { }
public static int Main(string[] args) { }
public static async Task Main() { }
public static async Task<int> Main() { }
public static async Task Main(string[] args) { }
public static async Task<int> Main(string[] args) { }
```

前の例ではすべて、public アクセサー修飾子を使用しています。 これは一般的ですが、必須ではありません。

コンソール アプリケーションの `Main` で `await` を使用して非同期操作を開始する必要がある場合、戻り値の型 `async`、`Task`、`Task<int>` を追加することでプログラム コードを簡略化できます。

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [csc.exe を使用したコマンド ラインからのビルド](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [C# プログラミング ガイド](../index.md)
- [メソッド](../classes-and-structs/methods.md)
- [インサイド C# プログラム](../inside-a-program/index.md)
