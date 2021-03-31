---
title: 最上位レベルのステートメント - C# プログラミング ガイド
description: C# 9 以降の最上位レベルのステートメントについて説明します。
ms.date: 03/08/2021
helpviewer_keywords:
- C# language, top-level statements
- C# language, Main method
ms.openlocfilehash: 31a9d3bba302823015058d59ca79da45754b761f
ms.sourcegitcommit: 5ce37699c2a51ed173171813be68ef7577b1aba5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881055"
---
# <a name="top-level-statements-c-programming-guide"></a>最上位レベルのステートメント (C# プログラミング ガイド)

C# 9 以降は、コンソール アプリケーション プロジェクトに `Main` メソッドを明示的に含める必要はありません。 代わりに、"*最上位レベルのステートメント*" 機能を使用し、記述しなければならないコードを最小限に抑えることができます。 その場合、コンパイラによってアプリケーションに対し、クラスと `Main` メソッド エントリ ポイントが生成されます。

次の *Program.cs* ファイルは、C# 9 の完全な C# プログラムです。

:::code language="csharp" source="snippets/top-level-statements-1/Program.cs":::

最上位レベルのステートメントでは、Azure Functions や GitHub Actions など、小さなユーティリティのために簡単なプログラムを記述できます。 また、C# プログラムを始めたばかりの方にとってコードを習い、書くことがもっと簡単になります。

次のセクションでは、最上位レベルのステートメントでできることとできないことに関する規則について説明します。

## <a name="only-one-top-level-file"></a>最上位レベルのファイルは 1 つだけ

アプリケーションにつき、エントリ ポイントは 1 つだけになります。そのため、プロジェクトには、最上位レベルのステートメントのファイルを 1 つだけ含めることができます。 1 つのプロジェクトで複数のファイルに最上位レベルのステートメントを置くと、次のコンパイラ エラーが発生します。

> CS8802 トップレベルのステートメントを持つことができるのは、1 つのコンパイル ユニットのみです。

1 つのプロジェクトには、最上位レベルのステートメントが含まれていない追加のソース コード ファイルをいくらでも含めることができます。

## <a name="no-other-entry-points"></a>エントリ ポイントは他に用意しない

`Main` メソッドは明示的に記述できますが、エントリ ポイントとして機能させることができません。 コンパイラから次の警告が出ます。

> CS7022 プログラムのエントリ ポイントは、グローバル コードです。エントリ ポイント 'Main()' を無視します。

最上位レベルのステートメントが含まれるプロジェクトでは、そのプロジェクトに `Main` メソッドが複数含まれる場合でも、[-main](../../language-reference/compiler-options/advanced.md#mainentrypoint-or-startupobject) コンパイラ オプションを使用してエントリ ポイントを選択することができません。

## <a name="using-directives"></a>`using` ディレクティブ

using ディレクティブを含める場合、次の例のように、ファイルの先頭に指定する必要があります。

:::code language="csharp" source="snippets/top-level-statements-1/Program.cs":::

## <a name="global-namespace"></a>グローバル名前空間

最上位レベルのステートメントは暗黙的にグローバル名前空間に属します。

## <a name="namespaces-and-type-definitions"></a>名前空間と型の定義

最上位レベルのステートメントが含まれるファイルには、名前空間と型の定義を含めることもできますが、最上位レベルのステートメントの後に指定する必要があります。 次に例を示します。

:::code language="csharp" source="snippets/top-level-statements-2/Program.cs":::

## `args`

最上位レベルのステートメントでは、コマンドライン引数が入力された場合、`args` 変数を参照してそれにアクセスできます。 `args` 変数が null 値になることはありませんが、その `Length` は、コマンドライン引数が指定されなかった場合、ゼロになります。 次に例を示します。

:::code language="csharp" source="snippets/top-level-statements-3/Program.cs":::

## `await`

`await` を使用して非同期メソッドを呼び出すことができます。 次に例を示します。

:::code language="csharp" source="snippets/top-level-statements-4/Program.cs":::

## <a name="exit-code-for-the-process"></a>プロセスの終了コード

アプリケーションの終了時に `int` 値を返すには、`int` を返す `Main` メソッドの場合と同じように、`return` ステートメントを使用します。 次に例を示します。

:::code language="csharp" source="snippets/top-level-statements-5/Program.cs":::

## <a name="implicit-entry-point-method"></a>暗黙的なエントリ ポイント メソッド

最上位レベルのステートメントが含まれるプロジェクトに対して、プログラムのエントリ ポイントとして機能するメソッドがコンパイラによって生成されます。 このメソッドの名前は実際のところ `Main` ではありません。コードで直接参照できない実装の詳細です。 メソッドのシグネチャは、最上位レベルのステートメントに `await` キーワードか `return` ステートメントが含まれるかどうかによって決まります。 メソッド シグネチャがどのように表現されるかを次の表にまとめてあります。便宜上、表ではメソッド名に `Main` を使用しています。

| 最上位レベルのコードに含まれる| 暗黙的 `Main` シグネチャ                    |
|------------------------|----------------------------------------------|
| `await` および `return`   | `static async Task<int> Main(string[] args)` |
| `await`                | `static async Task Main(string[] args)`      |
| `return`               | `static int Main(string[] args)`             |
| `await` も `return` もない | `static void Main(string[] args)`            |

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
[最上位レベルのステートメント](~/_csharplang/proposals/csharp-9.0/top-level-statements.md)

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [メソッド](../classes-and-structs/methods.md)
- [インサイド C# プログラム](../inside-a-program/index.md)
