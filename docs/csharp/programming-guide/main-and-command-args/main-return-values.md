---
title: Main() の戻り値 - C# プログラミング ガイド
description: Main() の戻り値について説明します。 コード例とコンパイラにより生成されたコードを参照し、使用可能なその他のリソースを確認してください。
ms.date: 03/11/2021
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 6f4001ecd490d5627d3a1ec74ecf7d593451e104
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190360"
---
# <a name="main-return-values-c-programming-guide"></a>Main() の戻り値 (C# プログラミング ガイド)

次のいずれかの方法でメソッドを定義することで、`Main` メソッドから `int` を返すことができます。

| `Main` メソッド コード             | `Main` シグネチャ                             |
|--------------------------------|----------------------------------------------|
| `args` と `await` は使用しない    | `static int Main()`                          |
| `args` を使用し、`await` を使用しない | `static int Main(string[] args)`             |
| `args` を使用せず、`await` を使用する | `static async Task<int> Main()`              |
| `args` と `await` を使用する        | `static async Task<int> Main(string[] args)` |

`Main` からの戻り値を使用しない場合、`void` か `Task` を返すと少し簡単なコードにすることができます。

| `Main` メソッド コード             | `Main` シグネチャ                        |
|--------------------------------|-----------------------------------------|
| `args` と `await` は使用しない    | `static void Main()`                    |
| `args` を使用し、`await` を使用しない | `static void Main(string[] args)`       |
| `args` を使用せず、`await` を使用する | `static async Task Main()`              |
| `args` と `await` を使用する        | `static async Task Main(string[] args)` |

ただし、`int` か `Task<int>` を返すことによって、プログラムが状態の情報を、実行可能ファイルを呼び出す他のプログラムまたはスクリプトに伝達することができます。

次の例からは、プロセスの終了コードにアクセスする方法がわかります。

## <a name="example"></a>例

この例では、[.NET Core](../../../core/introduction.md) コマンドライン ツールを使用します。 .NET Core コマンドライン ツールに慣れていない場合は、この[概要の記事](../../../core/tutorials/with-visual-studio-code.md)を参照してください。

*program.cs* の `Main` メソッドを次のように変更します。

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

プログラムを Windows で実行する場合、`Main` 関数からの戻り値はすべて 1 つの環境変数に格納されます。 この環境変数を取得するには、バッチ ファイルから `ERRORLEVEL` を使用するか、PowerShell から `$LastExitCode` を使用します。

[dotnet CLI](../../../core/tools/dotnet.md) の `dotnet build` コマンドを使用してアプリケーションを構築できます。

次に、アプリケーションを実行して結果を表示する PowerShell スクリプトを作成します。 次のコードをテキスト ファイルに貼り付け、プロジェクトが保存されているフォルダーに `test.ps1` として保存します。 PowerShell プロンプトに「`test.ps1`」と入力して PowerShell スクリプトを実行します。

コードがゼロを返すため、バッチ ファイルで成功が報告されます。 ただし、MainReturnValTest.cs が 0 以外の値を返すように変更して、プログラムを再コンパイルする場合、PowerShell スクリプトの後続の実行では失敗が報告されます。

```dotnetcli
dotnet run
```

```powershell
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a>出力例

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a>非同期 Main の戻り値

非同期 Main の戻り値によって、`Main` 内の非同期メソッドを呼び出すために必要な定型コードを、コンパイラで生成されるコードに移動します。 以前のバージョンでは、このコンストラクトを出力して非同期コードを呼び出し、非同期操作が完了するまでプログラムが実行されるようにする必要がありました。

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

現在のバージョンでは、以下のように書き換えられるようになりました。

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

新しい構文を使用すると、コンパイラから常に正しいコードが生成されるという利点があります。

## <a name="compiler-generated-code"></a>コンパイラで生成されたコード

アプリケーションのエントリ ポイントから `Task` または `Task<int>` が返されると、コンパイラによって、アプリケーション コードで宣言されたエントリ ポイント メソッドを呼び出す新しいエントリ ポイントが生成されます。 このエントリ ポイント名が `$GeneratedMain` だとすると、これらのエントリ ポイントについて次のコードが生成されます。

- `static Task Main()` の結果、`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();` と同等のコードが生成されます。
- `static Task Main(string[])` の結果、`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();` と同等のコードが生成されます。
- `static Task<int> Main()` の結果、`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();` と同等のコードが生成されます。
- `static Task<int> Main(string[])` の結果、`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();` と同等のコードが生成されます。

> [!NOTE]
>この例の `Main` メソッドで `async` 修飾子を使用した場合、同じコードが生成されます。

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [C# リファレンス](../../language-reference/index.md)
- [Main() とコマンドライン引数](index.md)
- [コマンド ライン引数を表示する方法](./how-to-display-command-line-arguments.md)
