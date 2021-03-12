---
title: F# インタラクティブ (dotnet) リファレンス
description: F# インタラクティブ (dotnet fsi) を使用して、コンソールで F# コードを対話形式で実行したり、F# スクリプトを実行したりする方法について説明します。
ms.date: 11/29/2020
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: 200caf6be5977e4a4d11bda8ba57f276cb4f5ff6
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605127"
---
# <a name="interactive-programming-with-f"></a>F\# による対話型プログラミング

F# インタラクティブ (dotnet fsi) は、コンソールで F# コードを対話形式で実行したり、F# スクリプトを実行したりするために使用します。 つまり、F# Interactive は、F# 言語の REPL (Read、Evaluate、Print Loop) を実行します。

コンソールから F# インタラクティブを実行するには、`dotnet fsi` を実行します。 `dotnet fsi` はすべての .NET SDK に備わっています。

使用できるコマンド ライン オプションについては、「[F# Interactive オプション](../../language-reference/fsharp-interactive-options.md)」を参照してください。

## <a name="executing-code-directly-in-f-interactive"></a>F# インタラクティブでコードを直接実行する

F# インタラクティブは REPL (read–eval–print loop) であるため、コードを対話形式で実行できます。 コマンド ラインから `dotnet fsi` を実行した後の対話型セッションの例を次に示します。

```console
Microsoft (R) F# Interactive version 11.0.0.0 for F# 5.0
Copyright (c) Microsoft Corporation. All Rights Reserved.

For help type #help;;

> let square x = x *  x;;
val square : x:int -> int

> square 12;;
val it : int = 144

> printfn "Hello, FSI!"
- ;;
Hello, FSI!
val it : unit = ()
```

次の 2 つの主要な点がわかります。

1. すべてのコードは、評価するために 2 つのセミコロン (`;;`) で終了する必要があります
2. コードは評価され、`it` 値に格納されます。 `it` は対話的に参照できます。

F# インタラクティブでは、複数行の入力もサポートされています。 2 つのセミコロン (`;;`) を使用して、入力を終了する必要があります。 F# インタラクティブに対して貼り付けられ、評価された、次のスニペットを考えてみましょう。

```console
> let getOddSquares xs =
-     xs
-     |> List.filter (fun x -> x % 2 <> 0)
-     |> List.map (fun x -> x * x)
-
- printfn "%A" (getOddSquares [1..10]);;
[1; 9; 25; 49; 81]
val getOddSquares : xs:int list -> int list
val it : unit = ()

>
```

コードの書式設定は保持されており、入力を終了する 2 つのセミコロン (`;;`) があります。 その後 F# インタラクティブによってコードが評価され、結果が出力されています。

## <a name="scripting-with-f"></a>F\# によるスクリプト

F# インタラクティブでの対話的なコードの評価は学習ツールとしては優れていますが、通常のエディターでコードを記述するほど生産的ではないことがすぐにわかります。 通常のコード編集をサポートするために、F# スクリプトを記述することができます。

スクリプトで使用されるファイル拡張子は **.fsx** です。 ソース コードをコンパイルした後でそのコンパイル済みのアセンブリを実行する代わりに、**dotnet fsi** を実行して F# ソース コードのスクリプトのファイル名を指定するだけで、F# インタラクティブによってコードを読み取り、リアルタイムで実行することができます。 たとえば、`Script.fsx` という名前の次のスクリプトを考えてみます。

```fsharp
let getOddSquares xs =
    xs
    |> List.filter (fun x -> x % 2 <> 0)
    |> List.map (fun x -> x * x)

printfn "%A" (getOddSquares [1..10])
```

このファイルをコンピューター上に作成したら、`dotnet fsi` を使用して実行し、ターミナル ウィンドウで直接出力を確認することができます。

```console
dotnet fsi Script.fsx
[1; 9; 25; 49; 81]
```

F# スクリプトは [Visual Studio](../../get-started/get-started-visual-studio.md)、[Visual Studio Code](../../get-started/get-started-vscode.md)、[Visual Studio for Mac](../../get-started/get-started-with-visual-studio-for-mac.md) でネイティブにサポートされています。

## <a name="referencing-packages-in-f-interactive"></a>F# インタラクティブでのパッケージの参照

> [!NOTE]
> パッケージ管理システムは拡張可能です。その他の拡張機能については、[こちら](https://fsharp.github.io/FSharp.Compiler.Service/reference/Microsoft.DotNet.DependencyManager.html)をご覧ください。

F# インタラクティブでは、`#r "nuget:"` 構文と省略可能なバージョンを使用した、NuGet パッケージの参照がサポートされています。

```fsharp
#r "nuget: Newtonsoft.Json"
open Newtonsoft.Json

let data = {| Name = "Don Syme"; Occupation = "F# Creator" |}
JsonConvert.SerializeObject(data)
```

バージョンを指定しない場合は、使用可能な最上位のプレビュー版でないパッケージが取得されます。 特定のバージョンを参照するには、コンマを使用してバージョンを指定します。 これは、パッケージのプレビュー バージョンを参照するときに便利です。 たとえば、プレビュー バージョンの [DiffSharp](https://diffsharp.github.io/) を使用する次のスクリプトを考えてみましょう。

```fsharp
#r "nuget: DiffSharp-lite, 1.0.0-preview-328097867"
open DiffSharp

// A 1D tensor
let t1 = dsharp.tensor [ 0.0 .. 0.2 .. 1.0 ]

// A 2x2 tensor
let t2 = dsharp.tensor [ [ 0; 1 ]; [ 2; 2 ] ]

// Define a scalar-to-scalar function
let f (x: Tensor) = sin (sqrt x)

printfn $"{f (dsharp.tensor 1.2)}"
```

### <a name="specifying-a-package-source"></a>パッケージ ソースの指定

`#i` コマンドを使用してパッケージ ソースを指定することもできます。 次の例では、リモートおよびローカルのソースを指定しています。

```fsharp
#i "nuget:https://my-remote-package-source/index.json"
#i @"path-to-my-local-source"
```

これにより、スクリプトに追加されたリモート、ローカル、またはその両方のソースも考慮に入れるよう内部の解決エンジンに指示されます。

スクリプト内では、必要な数だけパッケージ参照を指定できます。

> [!NOTE]
> 現在、フレームワーク参照 (`Microsoft.NET.Sdk.Web` や `Microsoft.NET.Sdk.WindowsDesktop` など) を使用するスクリプトには制限があります。 Saturn、Giraffe、WinForms などのパッケージは使用できません。 これは、イシュー [#9417](https://github.com/dotnet/fsharp/issues/9417) で追跡されています。

詳細については、[パッケージ管理の機能拡張とその他の拡張機能](https://fsharp.github.io/FSharp.Compiler.Service/reference/Microsoft.DotNet.DependencyManager.html)に関するページを参照してください。

## <a name="referencing-assemblies-on-disk-with-f-interactive"></a>F# インタラクティブでディスク上のアセンブリを参照する

また、ディスク上にアセンブリがあり、それをスクリプト内で参照したい場合は、`#r` 構文を使用してアセンブリを指定できます。 `MyAssembly.dll` にコンパイルされるプロジェクト内の次のコードについて考えてみましょう。

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

コンパイルしたら、`Script.fsx` という名前のファイル内で次のように参照できます。

```fsharp
#r "path/to/MyAssembly.dll"

printfn $"{MyAssembly.myFunction 10 40}"
```

出力は次のようになります。

```console
dotnet fsi Script.fsx
90
```

スクリプト内では、必要な数だけアセンブリ参照を指定できます。

## <a name="loading-other-scripts"></a>他のスクリプトの読み込み

スクリプトを作成する際は、異なるスクリプトを異なるタスク用に使用すると便利なことがよくあります。 場合によっては、あるスクリプトのコードを別のスクリプトで再利用することが必要になることがあります。 その内容をコピーしてファイルに貼り付ける代わりに、`#load` を使用して簡単に読み込んで評価することができます。

次の `Script1.fsx` を考えてみましょう。

```fsharp
let square x = x * x
```

また、これを使用するファイル `Script2.fsx` があります。

```fsharp
#load "Script1.fsx"
open Script1

printfn $"%d{square 12}"
```

`open Script1` 宣言が必要であることに注意してください。 これは、F# スクリプト内のコンストラクトが、それを含むスクリプト ファイルの名前である最上位レベルのモジュールにコンパイルされるためです。

次のように `Script2.fsx` を評価できます。

```console
dotnet fsi Script2.fsx
144
```

スクリプト内では、必要な数だけ `#load` ディレクティブを指定できます。

## <a name="using-the-fsi-object-in-f-code"></a>F# コードでの `fsi` オブジェクトの使用

F# スクリプトでは、F# インタラクティブ セッションを表すカスタム `fsi` オブジェクトにアクセスすることができます。 これにより、出力の書式設定などをカスタマイズできます。 これはコマンド ライン引数にアクセスする方法でもあります。

次の例は、コマンド ライン引数を取得して使用する方法を示しています。

```fsharp
let args = fsi.CommandLineArgs

for arg in args do
    printfn $"{arg}"
```

これを評価すると、すべての引数が出力されます。 最初の引数は、常に評価されるスクリプトの名前になります。

```dotnet
dotnet fsi Script1.fsx hello world from fsi
Script1.fsx
hello
world
from
fsi
```

同じ引数にアクセスするために `System.Environment.GetCommandLineArgs()` を使用することもできます。

## <a name="f-interactive-directive-reference"></a>F# インタラクティブのディレクティブのリファレンス

前述の `#r` および `#load` ディレクティブは、F# インタラクティブでのみ使用できます。 F# インタラクティブでのみ使用できるディレクティブがいくつかあります。

|ディレクティブ|説明|
|---------|-----------|
|`#r "nuget:..."`|NuGet からパッケージを参照します|
|`#r "assembly-name.dll"`|ディスク上のアセンブリを参照します|
|`#load "file-name.fsx"`|ソース ファイルを読み取り、コンパイルして実行します。|
|`#help`|使用できるディレクティブに関する情報を表示します。|
|`#I`|アセンブリ検索パスを引用符で囲んで指定します。|
|`#quit`|F# Interactive セッションを終了します。|
|`#time "on"` または `#time "off"`|`#time` 単独で、パフォーマンス情報を表示するかどうかを切り替えることができます。 `"on"` の場合、解釈および実行されるコードのセクションごとに、実時間、CPU 時間、およびガベージ コレクションの情報が F# インタラクティブによって計測されます。|

F# Interactive でファイルまたはパスを指定するときは、リテラル文字列が想定されます。 したがって、ファイルとパスは引用符で囲む必要があり、通常のエスケープ文字が適用されます。 `@` 文字を使用して、パスを含む文字列が F# インタラクティブで逐語的文字列として解釈されるように指示することもできます。 この場合、F# Interactive はエスケープ文字を無視するようになります。

## <a name="interactive-and-compiled-preprocessor-directives"></a>対話型およびコンパイル済みのプリプロセッサ ディレクティブ

F# インタラクティブでコードをコンパイルすると、対話形式で実行しているかスクリプトを実行しているかにかかわらず、シンボル **INTERACTIVE** が定義されます。 コンパイラでコードをコンパイルすると、シンボル **COMPILED** が定義されます。 したがって、コンパイル モードと対話型モードでコードを別にする必要がある場合は、条件付きコンパイルに対する次のプリプロセッサ ディレクティブを使用して、どちらを使用するか決定することができます。 次に例を示します。

```fsharp
#if INTERACTIVE
// Some code that executes only in FSI
// ...
#endif
```

## <a name="using-f-interactive-in-visual-studio"></a>Visual Studio での F# インタラクティブの使用

Visual Studio で F# Interactive を実行するには、ツール バーの **[F# Interactive]** というボタンをクリックするか、**Ctrl + Alt + F** キーを使用します。 この操作により、対話形式のウィンドウが開きます。このウィンドウは、F# Interactive セッションを実行するツール ウィンドウです 対話形式のウィンドウで実行するコードを選択し、**Alt + Enter** キーの組み合わせを押す方法もあります。 F# インタラクティブが **[F# Interactive]** というツール ウィンドウで開始されます。 このショートカット キーを使用するときは、エディター ウィンドウにフォーカスがあることを確認します。

コンソールと Visual Studio のどちらを使用している場合でも、コマンド プロンプトが表示され、入力待ちの状態になります。 コード ファイルと同じようにコードを入力できます。 コードをコンパイルして実行するには、2 つのセミコロン (**;;**) を入力して、入力行を終了します。

F# Interactive によってコードがコンパイルされ、成功すると、コードが実行され、コンパイルされた型のシグネチャと値が出力されます。 エラーが発生した場合は、エラー メッセージが出力されます。

同じセッションで入力したコードからは、前に入力したどの構成要素にもアクセスできるため、プログラムの構築が可能です。 ツール ウィンドウには十分なバッファーが用意されており、必要に応じてコードをファイルにコピーできます。

Visual Studio で実行する場合、F# Interactive はプロジェクトとは独立して動作します。このため、たとえば、プロジェクトで定義された構成要素を F# Interactive で使用することはできません。使用するには、関数のコードを対話形式のウィンドウにコピーする必要があります。

設定を調整することで、F# インタラクティブのコマンド ライン引数 (省略可能) を制御できます。 **[ツール]** メニューの **[オプション]** をクリックし、**[F# ツール]** を展開します。 変更できる 2 つの設定は、F# Interactive オプションおよび 64 ビット コンピューターで F# Interactive を実行する場合にのみ関連する **64 ビット F# Interactive** 設定です。 この設定によって、専用 64 ビット バージョンの **fsi.exe** を実行するか、コンピューター アーキテクチャを使用して 32 ビットまたは 64 ビットどちらのプロセスで実行するかを判断する **fsianycpu.exe** を実行するかを決定できます。

## <a name="related-articles"></a>関連記事

|Title|説明|
|-----|-----------|
|[F# Interactive オプション](../../language-reference/fsharp-interactive-options.md)|F# インタラクティブ (fsi.exe) のコマンド ライン構文やオプションについて説明します。|
