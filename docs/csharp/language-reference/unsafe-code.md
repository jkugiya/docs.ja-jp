---
title: アンセーフ コード、データへのポインター、および関数ポインター
description: アンセーフ コード、ポインター、および関数ポインターについて説明します。 C# では、これらの機能を使用してメモリまたは関数ポインターを直接操作するために、unsafe コンテキストを宣言する必要があります。
ms.date: 04/01/2021
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 9c55fc48b5805ba38dcf289cb5e03626cf3e96ec
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498579"
---
# <a name="unsafe-code-and-pointer-types"></a>アンセーフ コードとポインター型

記述する C# コードのほとんどは、"検証可能なセーフ コード" です。 "*検証可能なセーフ コード*" は、コードが安全であることを .NET ツールが検証できることを意味します。 一般に、セーフ コードはポインターを使用してメモリに直接アクセスしません。 また、生のメモリも割り当てられません。 代わりに、マネージド オブジェクトが作成されます。

C# では、"*検証不可能*" なコードを記述できる [`unsafe`](keywords/unsafe.md) コンテキストがサポートされています。 `unsafe` コンテキストでは、コードがポインターの使用、メモリ ブロックの割り当てと解放、関数ポインターを使用したメソッドの呼び出しを行うことができます。 C# のアンセーフ コードは、必ずしも危険ではありません。ただ、安全性を確認できないコードであるというだけです。

アンセーフ コードには次の特徴があります。

- メソッド、型、およびコード ブロックをアンセーフとして定義できます。
- アンセーフ コードでアプリケーションのパフォーマンスが向上することがあります。これは、配列のバインド チェックが削除されるためです。
- アンセーフ コードは、ポインターを必要とするネイティブ関数を呼び出すときに必要です。
- アンセーフ コードを使用すると、セキュリティと安定性の面でリスクが生じます。
- unsafe ブロックを含むコードは、[**AllowUnsafeBlocks**](compiler-options/language.md#allowunsafeblocks) コンパイラ オプションを使ってコンパイルする必要があります。

## <a name="pointer-types"></a>ポインター型

unsafe コンテキストの型には、値の型に加えてポインター型、または参照型を設定できます。 ポインター型の宣言は、次のいずれかの形式になります。

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

ポインター型の `*` の前に指定された型は、**参照型** と呼ばれます。 参照型にできるのは[アンマネージド型](builtin-types/unmanaged-types.md)だけです。

ポインター型は [object](builtin-types/reference-types.md) を継承せず、ポインター型と `object` の間で変換を行う方法はありません。 また、ボックス化とボックス化解除もポインターをサポートしません。 ただし、異なるポインター型の間で変換したり、ポインター型と整数型の間で変換したりすることはできます。

同じ宣言で複数のポインターを宣言する場合、アスタリスク (`*`) は基底の型のみと一緒に記述します。 各ポインター名のプレフィックスとしては使用されません。 次に例を示します。

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

オブジェクト参照は、それを指すポインターがあってもガベージ コレクションされる可能性があるため、ポインターによって参照や、参照を含む [struct](builtin-types/struct.md) を指すことはできません。 ガベージ コレクターは、オブジェクトを指すポインター型があるかどうかを追跡しません。

`MyType*` 型のポインター変数の値は、`MyType` 型の変数のアドレスです。 ポインター型の宣言の例を次に示します。

- `int* p`: `p` は、整数へのポインターです。
- `int** p`: `p` は、整数へのポインターのポインターです。
- `int*[] p`: `p` は、整数へのポインターの 1 次元配列です。
- `char* p`: `p` は、char へのポインターです。
- `void* p`: `p` は、未知の型へのポインターです。

ポインター間接参照演算子 `*` を使用すると、ポインター変数が指す位置にあるコンテンツにアクセスできます。 たとえば、次のような宣言があるとします。

```csharp
int* myVariable;
```

この例の式 `*myVariable` は、`int` に含まれているアドレスの位置にある `myVariable` 変数を示しています。

[`fixed` ステートメント](keywords/fixed-statement.md)の記事に、いくつかのポインターの例があります。 次の例は、`unsafe` キーワードと `fixed` ステートメントの使用例と、内部ポインターのインクリメント方法を示しています。  このコードは、コンソール アプリケーションの Main 関数に貼り付けて実行することができます これらの例は、[**AllowUnsafeBlocks**](compiler-options/language.md#allowunsafeblocks) コンパイラ オプションを設定してコンパイルする必要があります。

:::code language="csharp" source="snippets/unsafe-code/FixedKeywordExamples.cs" ID="5":::

間接参照演算子は、`void*` 型のポインターに適用できません。 ただし、void ポインターと他のポインター型はキャストを使用して相互に変換できます。

ポインターは、`null` にできます。 null ポインターに間接演算子を適用すると、実装で定義されている動作が発生します。

ポインターをメソッド間で引き渡すと、未定義の動作が発生する可能性があります。 たとえば、`in`、`out` または `ref` パラメーターを介してポインターをローカル変数に返したり、関数の結果として返したりするメソッドがあるとします。 ポインターが固定ブロックに設定されていた場合は、そのポインターが指す変数が既に固定されていない可能性があります。

次の表は、unsafe コンテキストでポインターに使用できる演算子とステートメントの一覧を示しています。

|演算子/ステートメント|使用|
|-------------------------|---------|
|`*`|ポインターの間接参照を実行します。|
|`->`|ポインター経由で構造体のメンバーにアクセスします。|
|`[]`|ポインターにインデックスを付けます。|
|`&`|変数のアドレスを取得します。|
|`++` および `--`|ポインターをインクリメントおよびデクリメントします。|
|`+` および `-`|ポインター演算を実行します。|
|`==`、`!=`、`<`、`>`、`<=`、`>=`|ポインターを比較します。|
|[`stackalloc`](operators/stackalloc.md)|スタックにメモリを割り当てます。|
|[`fixed` ステートメント](keywords/fixed-statement.md)|変数を一時的に固定して、そのアドレスを取得できるようにします。|

ポインター関連の演算子について詳しくは、「[ポインターに関連する演算子](operators/pointer-related-operators.md)」をご覧ください。

どのポインター型も、暗黙的に `void*` 型に変換できます。 どのポインター型にも、値 `null` を割り当てることができます。 どのポインター型も、キャスト式を使用して、他のポインター型に明示的に変換できます。 また、任意の整数型をポインター型に、または任意のポインター型を整数型に変換することもできます。 これらの変換には、明示的なキャストが必要です。

次の例では、`int*` を `byte*` に変換しています。 ポインターは、変数の最下位バイト アドレスを指すことに注意してください。 `int` のサイズ (4 バイト) まで結果を連続してインクリメントする場合、変数の残りのバイトを表示することができます。

:::code language="csharp" source="snippets/unsafe-code/Conversions.cs" ID="Conversion":::

## <a name="fixed-size-buffers"></a>固定サイズ バッファー

C# では、[fixed](keywords/fixed-statement.md) ステートメントを使って、データの構造体に固定サイズの配列を持ったバッファーを作成することができます。 固定サイズのバッファーは、他の言語またはプラットフォームのデータ ソースと相互運用するメソッドを作成するときに便利です。 この固定配列には、標準的な構造体メンバーで許容されている属性または修飾子であれば、何でも適用することができます。 ただし配列の型は `bool`、`byte`、`char`、`short`、`int`、`long`、`sbyte`、`ushort`、`uint`、`ulong`、`float`、`double` のいずれかに該当する必要があり、それが唯一の制限となります。

```csharp
private fixed char name[30];
```

セーフ コードでは、配列を含む C# 構造体に配列要素が含まれません。 代わりに、構造体には、要素の参照が格納されます。 [unsafe](keywords/unsafe.md) のコード ブロックで使われている [struct](builtin-types/struct.md) に、固定サイズの配列を埋め込むことができます。

`pathName` が参照であるため、次の `struct` のサイズは配列内の要素の数に依存しません。

:::code language="csharp" source="snippets/unsafe-code/FixedKeywordExamples.cs" ID="6":::

アンセーフ コードでは、`struct` に埋め込み配列を含めることができます。 以下の例の `fixedBuffer` 配列は固定サイズです。 `fixed` ステートメントを使用して、先頭要素へのポインターを確立します。 このポインターを使用して配列の要素にアクセスします。 `fixed` ステートメントによって、`fixedBuffer` インスタンス フィールドがメモリ内の特定の位置に固定されます。

:::code language="csharp" source="snippets/unsafe-code/FixedKeywordExamples.cs" ID="7":::

要素数 128 の `char` 配列のサイズは 256 バイトです。 固定サイズの [char](builtin-types/char.md) バッファーは、エンコーディングに関係なく常に、1 文字あたり 2 バイトを消費します。 この配列サイズは、char のバッファーが、`CharSet = CharSet.Auto` または `CharSet = CharSet.Ansi` で API メソッドや構造体にマーシャリングされたときにも当てはまります。 詳細については、「<xref:System.Runtime.InteropServices.CharSet>」を参照してください。

上記の例は、固定せずに `fixed` フィールドにアクセスする方法を示しています。この方法は C# 7.3 以降から使用できます。

一般的な固定サイズの配列としては、他にも [bool](builtin-types/bool.md) 配列があります。 `bool` 配列内の要素のサイズは常に 1 バイトです。 `bool` 配列は、ビット配列やバッファーの作成には適していません。

固定サイズ バッファーは <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>を使用してコンパイルされます。これにより、オーバーフローする可能性があるアンマネージド配列が型に含まれていることが共通言語ランタイム (CLR) に指示されます。 [Stackalloc](operators/stackalloc.md) を使用して割り当てられたメモリによって、CLR のバッファー オーバーラン検出機能も自動的に有効になります。 前の例では、`unsafe struct` に固定サイズ バッファーがどのようにして存在できるかを示しています。

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

`Buffer` 用にコンパイラで生成された C# は、次のように属性が付けられます。

```csharp
internal struct Buffer
{
    [StructLayout(LayoutKind.Sequential, Size = 256)]
    [CompilerGenerated]
    [UnsafeValueType]
    public struct <fixedBuffer>e__FixedBuffer
    {
        public char FixedElementField;
    }

    [FixedBuffer(typeof(char), 128)]
    public <fixedBuffer>e__FixedBuffer fixedBuffer;
}
```

固定サイズ バッファーは、次の点で通常の配列とは異なります。

- `unsafe` のコンテキストでのみ使用できます。
- 構造体のインスタンス フィールドのみを指定できます。
- これらは常にベクター (1 次元配列) です。
- 宣言には、`fixed char id[8]` などの長さを含める必要があります。 `fixed char id[]` は使用できません。

## <a name="how-to-use-pointers-to-copy-an-array-of-bytes"></a>ポインターを使用してバイトの配列をコピーする方法

次の例では、ポインターを使って 1 つの配列から別の配列にバイトをコピーします。

この例では、[unsafe](keywords/unsafe.md) キーワードを使います。このキーワードは、`Copy` メソッドでのポインターの使用を可能にします。 [fixed](keywords/fixed-statement.md) ステートメントを使って、コピー元とコピー先の配列へのポインターを宣言します。 `fixed` ステートメントを使って、コピー元配列とコピー先配列のメモリ内での位置を "*固定*" し、ガベージ コレクションによって移動されないようにします。 `fixed` ブロックが完了すると、これらの配列のメモリ ブロックは固定解除されます。 この例の `Copy` メソッドは `unsafe` キーワードを使っているので、[**AllowUnsafeBlocks**](compiler-options/language.md#allowunsafeblocks) コンパイラ オプションを指定してコンパイルする必要があります。

この例では、2 番目のアンマネージド ポインターではなくインデックスを使って、両方の配列の要素にアクセスします。 `pSource` と `pTarget` のポインターの宣言を使って配列を固定します。 この機能は、C# 7.3 以降から使用できます。

:::code language="csharp" source="snippets/unsafe-code/FixedKeywordExamples.cs" ID="8":::

## <a name="function-pointers"></a>関数ポインター

C# には、安全な関数ポインター オブジェクトを定義するための [`delegate`](builtin-types/reference-types.md#the-delegate-type) 型が用意されています。 デリゲートを呼び出すには、<xref:System.Delegate?displayProperty=nameWithType> から派生した型をインスタンス化し、その `Invoke` メソッドへの仮想メソッド呼び出しを行う必要があります。 この仮想呼び出しでは、`callvirt` IL 命令が使用されます。 パフォーマンスを重視するコード パスでは、`calli` IL 命令を使用する方が効率的です。

関数ポインターは、`delegate*` 構文を使用して定義できます。 コンパイラは、`delegate` オブジェクトをインスタンス化して `Invoke` を呼び出すのではなく、`calli` 命令を使用して関数を呼び出します。 次のコードでは、`delegate` または `delegate*` を使用する 2 つのメソッドを宣言して、同じ型の 2 つのオブジェクトを結合しています。 最初のメソッドは、<xref:System.Func%603?displayProperty=nameWithType> デリゲート型を使用します。 2 番目のメソッドは、同じパラメーターと戻り値の型を持つ `delegate*` 宣言を使用します。

:::code language="csharp" source="snippets/unsafe-code/FunctionPointers.cs" ID="UseDelegateOrPointer":::

次のコードは、静的ローカル関数を宣言し、そのローカル関数へのポインターを使用して `UnsafeCombine` メソッドを呼び出す方法を示しています。

:::code language="csharp" source="snippets/unsafe-code/FunctionPointers.cs" ID="InvokeViaFunctionPointer":::

上記のコードは、関数ポインターとしてアクセスされる関数に対するいくつかの規則を示しています。

- 関数ポインターは、`unsafe` コンテキスト内でのみ宣言できます。
- `delegate*` を受け取る (または `delegate*` を返す) メソッドは、`unsafe` コンテキストでのみ呼び出すことができます。
- 関数のアドレスを取得する `&` 演算子は、`static` 関数でのみ使用できます。 (この規則は、メンバー関数とローカル関数の両方に適用されます)。

この構文は、`delegate` 型を宣言し、ポインターを使用する場合と似ています。 `delegate` の `*` サフィックスは、宣言が "*関数ポインター*" であることを示します。 メソッド グループを関数ポインターに割り当てるときの `&` は演算がメソッドのアドレスを受け取ることを示します。

`delegate*` の呼び出し規則はキーワード `managed` と `unmanaged` を使用して指定することができます。 また、`unmanaged` 関数ポインターにも、呼び出し規則を指定できます。 次の宣言は、それぞれの例を示しています。 最初の宣言では、既定の `managed` の呼び出し規則が使用されます。 次の 3 つでは、`unmanaged` の呼び出し規則が使用されます。 それぞれ、ECMA 335 呼び出し規則のいずれか (`Cdecl`、`Stdcall`、`Fastcall`、または `Thiscall`) を指定しています。 最後の宣言では、`unmanaged` の呼び出し規則を使用して、プラットフォームの既定の呼び出し規則を選択するように CLR に指示しています。 CLR は、実行時に呼び出し規則を選択します。

:::code language="csharp" source="snippets/unsafe-code/FunctionPointers.cs" ID="UnmanagedFunctionPointers":::

関数ポインターの詳細については、C# 9.0 の[関数ポインター](~/_csharplang/proposals/csharp-9.0/function-pointers.md)に関する提案を参照してください。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)の[アンセーフ コード](~/_csharplang/spec/unsafe-code.md)に関する章を参照してください。
