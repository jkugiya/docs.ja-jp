---
description: 条件付きコンパイル、警告、null 許容分析などを制御するさまざまな C# プリプロセッサ ディレクティブについて学習します
title: C# プリプロセッサ ディレクティブ
ms.date: 03/17/2021
f1_keywords:
- cs.preprocessor
- '#nullable'
- '#if'
- '#else'
- '#elif'
- '#endif'
- '#define'
- '#undef'
- '#warning'
- '#error'
- '#line'
- '#region'
- '#endregion'
- '#pragma'
- '#pragma warning'
- '#pragma checksum'
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
- '#nullable directive [C#]'
- '#if directive [C#]'
- '#else directive [C#]'
- '#elif directive [C#]'
- '#endif directive [C#]'
- '#define directive [C#]'
- '#undef directive [C#]'
- '#warning directive [C#]'
- '#error directive [C#]'
- '#line directive [C#]'
- '#region directive [C#]'
- '#endregion directive [C#]'
- '#pragma directive [C#]'
- '#pragma warning [C#]'
- '#pragma checksum [C#]'
ms.openlocfilehash: 373952282a684da25414af9853e18b7bc4874108
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637658"
---
# <a name="c-preprocessor-directives"></a>C# プリプロセッサ ディレクティブ

コンパイラに個別のプリプロセッサはありませんが、このセクションに示すディレクティブは、ある場合と同じように処理されます。 これらを使用すると、条件付きコンパイルに役立ちます。 C や C++ のディレクティブとは異なり、マクロを作成するのにこれらのディレクティブを使用することはできません。 プリプロセッサ ディレクティブは、行の唯一の命令である必要があります。

## <a name="nullable-context"></a>Null 許容コンテキスト

`#nullable` プリプロセッサ ディレクティブは、"*Null 許容注釈コンテキスト*" と "*Null 許容警告コンテキスト*" を設定します。 このディレクティブでは、Null 許容注釈の効果があるかどうか、および NULL 値の許容の警告が与えられるかどうかが制御されます。 各コンテキストは "*無効*" または "*有効*" になります。

どちらのコンテキストもプロジェクト レベル (C# ソース コードの外部) で指定することができます。 `#nullable` ディレクティブは、注釈と警告のコンテキストを制御し、プロジェクト レベルの設定よりも優先されます。 ディレクティブは、別のディレクティブがそれをオーバーライドするか、ソース ファイルの末尾に達するまで、制御するコンテキストを設定します。

ディレクティブの効果は次のとおりです。

- `#nullable disable`: Null 許容注釈および警告コンテキストを "*無効*" に設定します。
- `#nullable enable`: Null 許容注釈および警告コンテキストを "*有効*" に設定します。
- `#nullable restore`: Null 許容注釈および警告コンテキストを、プロジェクト設定に復元します。
- `#nullable disable annotations`: Null 許容注釈コンテキストを "*無効*" に設定します。
- `#nullable enable annotations`: Null 許容注釈コンテキストを "*有効*" に設定します。
- `#nullable restore annotations`: Null 許容注釈コンテキストを、プロジェクト設定に復元します。
- `#nullable disable warnings`: Null 許容警告コンテキストを "*無効*" に設定します。
- `#nullable enable warnings`: Null 許容警告コンテキストを "*有効*" に設定します。
- `#nullable restore warnings`: Null 許容警告コンテキストをプロジェクト設定に復元します。

## <a name="conditional-compilation"></a>条件付きコンパイル

次の 4 つのプリプロセッサ ディレクティブを使用して、条件付きコンパイルを制御します。

- `#if`: 条件付きコンパイルを開きます。コードは、指定されたシンボルが定義されている場合にのみコンパイルされます。
- `#elif`: 前の条件付きコンパイルを閉じ、指定されたシンボルが定義されているかどうかに基づいて、新しい条件付きコンパイルを開きます。
- `#else`: 前の条件付きコンパイルを閉じ、前に指定されたシンボルが定義されていない場合は、新しい条件付きコンパイルを開きます。
- `#endif`: 前の条件付きコンパイルを閉じます。

C# コンパイラによって、`#if` ディレクティブ、次いで `#endif` ディレクティブが検出されると、指定されたシンボルが定義されている場合にのみ、これらのディレクティブ間のコードがコンパイルされます。 C や C++ とは異なり、シンボルに数値を代入することはできません。 C# の `#if` ステートメントはブール値で、シンボルが定義されているかどうかのみをテストします。 次に例を示します。

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

[`bool`](builtin-types/bool.md) 値 `true` または `false` をテストするために、演算子 [`==` (等式)](operators/equality-operators.md#equality-operator-) および [`!=` (不等式)](operators/equality-operators.md#inequality-operator-) を使用することができます。 `true` は、シンボルが定義されていることを意味します。 ステートメント `#if DEBUG` と `#if (DEBUG == true)` の意味は同じです。 [`&&` (かつ)](operators/boolean-logical-operators.md#conditional-logical-and-operator-)、[`||` (または)](operators/boolean-logical-operators.md#conditional-logical-or-operator-)、[`!` (否定)](operators/boolean-logical-operators.md#logical-negation-operator-) の各演算子を使用すると、複数のシンボルが定義されているかどうかを評価することができます。 シンボルと演算子は、かっこを使用してグループ化できます。

`#if` と `#else`、`#elif`、`#endif`、`#define`、`#undef` の各ディレクティブを組み合わせると、1 つ以上のシンボルが存在するかどうかに応じてコードを含めたり除外したりできます。 条件付きコンパイルは、デバッグ ビルドのコードをコンパイルする場合や、特定の構成用にコンパイルを行う場合に役立ちます。

`#if` ディレクティブで始まる条件付きディレクティブは、`#endif` ディレクティブで明示的に終了させる必要があります。 `#define` を使用するとシンボルを定義できます。 シンボルを `#if` ディレクティブに渡す式として使用すると、この式は `true` と評価されます。 シンボルは、[**DefineConstants**](compiler-options/language.md#defineconstants) コンパイラ オプションでも定義できます。 `#undef` を使うと、シンボルを未定義状態にできます。 `#define` を使用して作成したシンボルのスコープは、そのシンボルが定義されているファイルです。 **DefineConstants** または `#define` で定義したシンボルは、同じ名前の変数とは競合しません。 つまり、変数名をプリプロセッサ ディレクティブに渡すことはできません。シンボルはプリプロセッサ ディレクティブによってのみ評価できます。

`#elif` を使用すると、複合条件付きディレクティブを作成できます。 `#elif` 式が評価されるのは、前の `#if` および前の省略可能な `#elif` ディレクティブ式がいずれも `true` と評価されなかった場合です。 `#elif` 式が `true` と評価された場合は、`#elif` と次の条件付きディレクティブの間にあるすべてのコードが、コンパイラによって評価されます。 次に例を示します。

```csharp
#define VC7
//...
#if debug
    Console.WriteLine("Debug build");
#elif VC7
    Console.WriteLine("Visual Studio 7");
#endif
```

`#else` を使用すると、複合条件付きディレクティブを作成できるため、前の `#if` または (省略可能な) `#elif` ディレクティブの式がいずれも `true` と評価されない場合は、コンパイラによって `#else` と次の `#endif` の間のすべてのコードが評価されます。 `#endif`(#endif) が、`#else` の後の次のプリプロセッサ ディレクティブになる必要があります。

`#endif` は、`#if` ディレクティブで始まる条件付きディレクティブの終了を示します。

ビルド システムは、SDK 型プロジェクトの各種[ターゲット フレームワーク](../../standard/frameworks.md)を表す、定義済みプリプロセッサ シンボルも認識します。 これは、複数の .NET バージョンをターゲットとできるアプリケーションを作成する場合に役立ちます。

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> 従来の非 SDK スタイルのプロジェクトでは、プロジェクトの [プロパティ] ページを使用して、Visual Studio のさまざまなターゲット フレームワークの条件付きコンパイル シンボルを手動で構成する必要があります。

他の定義済みシンボルには、`DEBUG` および `TRACE` 定数が含まれます。 `#define` を使用して、プロジェクトに設定された値をオーバーライドできます。 たとえば、DEBUG シンボルは、ビルド構成プロパティ ("デバッグ" モードまたは "リリース" モード) に応じて自動的に設定されます。

次の例では、ファイルで `MYTEST` シンボルを定義してから、`MYTEST` および `DEBUG` シンボルの値をテストする方法を示します。 この例の出力は、プロジェクトを **デバッグ** と **リリース** のどちらの構成モードでビルドしたかによって異なります。

```csharp
#define MYTEST
using System;
public class MyClass
{
    static void Main()
    {
#if (DEBUG && !MYTEST)
        Console.WriteLine("DEBUG is defined");
#elif (!DEBUG && MYTEST)
        Console.WriteLine("MYTEST is defined");
#elif (DEBUG && MYTEST)
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else
        Console.WriteLine("DEBUG and MYTEST are not defined");
#endif
    }
}
```

次の例は、各種ターゲット フレームワークをテストし、可能な場合には新しい API を使用できるようにする方法を示しています。

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="defining-symbols"></a>シンボルの定義

次の 2 つのプリプロセッサ ディレクティブを使用して、条件付きコンパイルのシンボルの定義またはその解除を行います。

- `#define`: シンボルを定義します。
- `#undef`シンボルの定義を解除します。

`#define` は、シンボルを定義するために使用します。 次の例に示すように、定義したシンボルを式として `#if` ディレクティブに渡すと、式は `true` と評価されます。

 ```csharp
 #define VERBOSE

#if VERBOSE
    Console.WriteLine("Verbose output version");
#endif

 ```

> [!NOTE]
> `#define` ディレクティブを使用して、通常 C および C++ で行うように定数値を宣言することはできません。 C# の定数は、クラスまたは構造体の静的メンバーとして定義することができます。 そのような定数がいくつかある場合は、それを保持するための "Constants" クラスを個別に作成することを検討してください。

シンボルを使用して、コンパイル条件を指定できます。 シンボルは、`#if` または `#elif` で評価できます。 また、<xref:System.Diagnostics.ConditionalAttribute> を使用して、条件付きコンパイルを実行することもできます。 シンボルを定義することはできますが、シンボルに値を代入することはできません。 `#define` ディレクティブは、ファイル内で、プリプロセッサ ディレクティブではない他の命令よりも前に記述する必要があります。 シンボルは、[**DefineConstants**](compiler-options/language.md#defineconstants) コンパイラ オプションでも定義できます。 `#undef` を使うと、シンボルを未定義状態にできます。

## <a name="defining-regions"></a>領域の定義

次の 2 つのプリプロセッサ ディレクティブを使用して、アウトラインで折りたたむことができるコードの領域を定義できます。

- `#region`: 領域を開始します。
- `#endregion`: 領域を終了します

`#region` を使用すると、コード ブロックを指定できます。このブロックは、コード エディターの[アウトライン](/visualstudio/ide/outlining)機能を使用して、展開や折りたたみを行うことができます。 コード ファイルが長い場合は、現在操作しているファイルの部分に集中できるように 1 つまたは複数の領域を折りたたむ (非表示にする) と便利です。 次の例では、領域を定義する方法を示します。

```csharp
#region MyClass definition
public class MyClass
{
    static void Main()
    {
    }
}
#endregion
```

`#region` ブロックは、`#endregion` ディレクティブで終了させる必要があります。 `#region` ブロックは、`#if` ブロックと重複することはできません。 しかし、`#region` ブロックを `#if` ブロック内に入れ子にしたり、`#if` ブロックを `#region` ブロック内に入れ子にしたりすることはできます。

## <a name="error-and-warning-information"></a>エラーと警告の情報

次のディレクティブを使用して、ユーザー定義のコンパイラ エラーと警告を生成し、行情報を制御するようにコンパイラに指示します。

- `#error`: 指定されたメッセージでコンパイラ エラーを生成します。
- `#warning`: 特定のメッセージでコンパイラ警告を生成します。
- `#line`: コンパイラ メッセージで出力される行番号を変更します。

`#error` を使用すると、コード内の特定の場所からユーザー定義の [CS1029](compiler-messages/cs1029.md) エラーを生成できます。 次に例を示します。

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> コンパイラは `#error version` を特別な方法で処理し、使用されているコンパイラと言語バージョンを含むメッセージと共にコンパイラ エラー CS8304 を報告します。

`#warning` を使用すると、コード内の特定の場所から [CS1030](../misc/cs1030.md) レベル 1 のコンパイラの警告を生成できます。 次に例を示します。

```csharp
#warning Deprecated code in this method.
```

`#line` を使用すると、コンパイラの行番号および (必要に応じて) エラーと警告に出力されるファイル名を変更することができます。

次の例では、行番号に関連付けられている 2 つの警告を報告する方法を示します。 `#line 200` ディレクティブは次の行番号が 200 (既定では #6) になるように強制し、次の `#line` ディレクティブまでファイル名を "Special" として報告します。 `#line default` ディレクティブは、行の番号付けをその既定の番号付けに戻します。つまり、前のディレクティブで番号が付け直された行をカウントします。

```csharp
class MainClass
{
    static void Main()
    {
#line 200 "Special"
        int i;
        int j;
#line default
        char c;
        float f;
#line hidden // numbering not affected
        string s;
        double d;
    }
}
```

コンパイルで生成される出力は次のとおりです。

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

`#line` ディレクティブは、ビルド プロセスで自動化された中間ステップで使用される場合があります。 たとえば、行が元のソース コード ファイルから削除されても、ファイル内の元の行番号付けに基づいてコンパイラに引き続き出力を生成させる場合は、行を削除してから `#line` を使用して元の行番号付けをシミュレートできます。

開発者がコードをステップ実行すると、`#line hidden` と次の `#line` ディレクティブ (別の `#line hidden` ディレクティブではないと仮定) の間のすべての行がステップ オーバーされるように、`#line hidden` ディレクティブによって、デバッガーに対して連続する行が非表示にされます。 このオプションは、ユーザー定義のコードとコンピューターによって生成されたコードを ASP.NET が区別できるようするために使用することもできます。 この機能を主に使われているのは ASP.NET ですが、より多くのソース ジェネレーターで利用できる可能性はあります。

`#line hidden` ディレクティブは、エラー報告でのファイル名や行番号には影響しません。 つまり、コンパイラによって非表示のブロックでエラーが検出された場合、そのコンパイラによってエラーの現在のファイル名と行番号が報告されます。

`#line filename` ディレクティブは、コンパイラ出力に表示するファイル名を指定します。 既定では、ソース コード ファイルの実際の名前が使用されます。 ファイル名は、二重引用符 ("") で囲み、前に行番号を付ける必要があります。

次の例では、デバッガーがコード内の非表示の行を無視する方法を示します。 例を実行すると、次の 3 行のテキストが表示されます。 しかし、例に示されているようにブレークポイントを設定し、F10 キーを押してコードをステップ実行すると、デバッガーで非表示の行が無視されます。 非表示の行にブレークポイントを設定した場合でも、デバッガーで引き続きそれが無視されます。

```csharp
// preprocessor_linehidden.cs
using System;
class MainClass
{
    static void Main()
    {
        Console.WriteLine("Normal line #1."); // Set break point here.
#line hidden
        Console.WriteLine("Hidden line.");
#line default
        Console.WriteLine("Normal line #2.");
    }
}
```

## <a name="pragmas"></a>プラグマ

`#pragma` は、ファイル内に指定され、そのファイルのコンパイルについての特別な命令をコンパイラに指示します。 命令はコンパイラによってサポートされている必要があります。 つまり、`#pragma` を使用してカスタムの前処理命令を作成することはできません。
  
- [`#pragma warning`](#pragma-warning): 警告を有効または無効にします。
- [`#pragma checksum`](#pragma-checksum): チェックサムを生成します。

```csharp
#pragma pragma-name pragma-arguments
```

ここで、`pragma-name` は認識されているプラグマの名前で、`pragma-arguments` は pragma 固有の引数です。

### <a name="pragma-warning"></a>#pragma 警告

`#pragma warning` を使用すると、特定の警告を有効または無効にすることができます。

```csharp
#pragma warning disable warning-list
#pragma warning restore warning-list
```

ここで、`warning-list` は警告番号のコンマ区切りのリストです。 "CS" というプレフィックスは省略可能です。 警告番号が指定されていないと、`disable` はすべての警告を無効にし、`restore` はすべての警告を有効にします。

> [!NOTE]
> Visual Studio で警告番号を調べるには、プロジェクトをビルドし、**[出力]** ウィンドウで警告番号を探してください。

`disable` は、ソース ファイルの次の行から有効になります。 警告は、`restore` の後の行で復元されます。 ファイルに `restore` が存在しない場合、警告は、同じコンパイルの以降のファイルの最初の行で既定の状態に復元されます。

```csharp
// pragma_warning.cs
using System;

#pragma warning disable 414, CS3021
[CLSCompliant(false)]
public class C
{
    int i = 1;
    static void Main()
    {
    }
}
#pragma warning restore CS3021
[CLSCompliant(false)]  // CS3021
public class D
{
    int i = 1;
    public static void F()
    {
    }
}
```

### <a name="pragma-checksum"></a>#pragma checksum

ASP.NET ページのデバッグに使用するソース ファイルのチェックサムを生成します。

```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"
```

ここで、`"filename"` は変更または更新の監視を必要とするファイルの名前、`"{guid}"` はハッシュ アルゴリズムのグローバル一意識別子 (GUID)、`"checksum_bytes"` はチェックサムのバイト数を表す 16 進数の文字列です。 偶数の 16 進数である必要があります。 奇数の数値を指定すると、コンパイル時に警告が出力され、ディレクティブが無視されます。

Visual Studio デバッガーは、常に正しいソースを検出するために、チェックサムを使用します。 コンパイラはソース ファイルのチェックサムを計算し、プログラム データベース (PDB) ファイルに結果を出力します。 デバッガーは、その PDB ファイルを使用して、ソース ファイルについて計算したチェックサムと比較します。

このソリューションは ASP.NET プロジェクトには使用できません。計算されたチェックサムは、.aspx ファイルではなく、生成されたソース ファイルを対象としているためです。 この問題に対応するため、`#pragma checksum` によって ASP.NET ページのチェックサムがサポートされています。

Visual C# で ASP.NET プロジェクトを作成すると、生成されるソース ファイルにソースの生成元である .aspx ファイルのチェックサムが含められます。 コンパイラは、この情報を PDB ファイルに書き込みます。

コンパイラによってファイルで `#pragma checksum` ディレクティブが検出されない場合、チェックサムが計算され、PDB ファイルにその値が書き込まれます。

```csharp
class TestClass
{
    static int Main()
    {
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum
    }
}
```
