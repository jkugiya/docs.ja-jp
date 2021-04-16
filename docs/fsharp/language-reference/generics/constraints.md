---
title: 制約
description: ジェネリック型パラメーターに適用して、ジェネリック型または関数の型引数の要件を指定する F# の制約について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 70a8bec1ad67d7e814cb7a96b1876bb22399c5e7
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425015"
---
# <a name="constraints"></a>制約

このトピックでは、ジェネリック型パラメーターに適用して、ジェネリック型または関数内の型引数の要件を指定できる制約について説明します。

## <a name="syntax"></a>構文

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>解説

ジェネリック型で使用できる型を制限するために適用できる、いくつかの異なる制約があります。 次の表に、これらの制約の一覧とその説明を示します。

|制約|構文|説明|
|----------|------|-----------|
|型制約|*type-parameter* :&gt; *type*|規定される型は、指定する型と同じか、またはそれから派生したものである必要があります。または、型がインターフェイスの場合、規定される型ではそのインターフェイスを実装する必要があります。|
|Null 制約|*type-parameter* : null|規定される型では、NULL リテラルがサポートされている必要があります。 これには、すべての .NET オブジェクト型が含まれます。ただし、F# リスト、タプル、関数、クラス、レコード、共用体型は除きます。|
|明示的なメンバー制約|[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature*)|規定される型引数の少なくとも 1 つに、指定するシグネチャを持つメンバーが必要です。一般的な使用を目的としたものではありません。 メンバーは、明示的なメンバー制約のターゲットとして有効であるために、型に明示的に定義されているか、暗黙的な型拡張の一部でなければなりません。|
|コンストラクターの制約|*type-parameter* : ( new : unit -&gt; 'a )|規定される型には、パラメーターなしのコンストラクターが必要です。|
|値の型の制約|: struct|規定される型は、.NET の値の型である必要があります。|
|参照型の制約|: not struct|規定される型は、.NET の参照型である必要があります。|
|列挙型の制約|: enum&lt;*underlying-type*&gt;|規定される型は、指定された基になる型を持つ列挙型である必要があります。一般的な使用を目的としたものではありません。|
|デリゲート制約|: delegate&lt;*tuple-parameter-type*, *return-type*&gt;|規定される型は、指定された引数と戻り値を持つデリゲート型である必要があります。一般的な使用を目的としたものではありません。|
|比較制約|: comparison|規定される型では、比較がサポートされている必要があります。|
|等値制約|: equality|規定される型では、等値がサポートされている必要があります。|
|アンマネージド制約|: unmanaged|規定される型は、アンマネージド型である必要があります。 アンマネージ型とは、特定のプリミティブ型 (`sbyte`、`byte`、`char`、`nativeint`、`unativeint`、`float32`、`float`、`int16`、`uint16`、`int32`、`uint32`、`int64`、`uint64`、または `decimal`)、列挙型、`nativeptr<_>`、またはフィールドがすべてアンマネージ型である非ジェネリック構造体のことです。|

制約を追加する必要があるのは、制約型の上では使用できても、型一般の上では使用できない機能をコードで使用する必要がある場合です。 たとえば、型制約を使用してクラス型を指定する場合は、ジェネリック関数または型で、そのクラスの任意のメソッドを使用できます。

型パラメーターを明示的に記述するときに制約の指定が必要になることがあります。制約がないと、コンパイラには、使用しようとしている機能が、実行時に型パラメーターに提供される可能性のあるすべての型で利用できることを確認する方法がないためです。

F# コードで使用する最も一般的な制約は、基底クラスまたはインターフェイスを指定する型制約です。 他の制約は、算術演算子の演算子のオーバーロードを実装するために使用される明示的なメンバー制約など、特定の機能を実装するために F# ライブラリによって使用されるか、共通言語ランタイムによってサポートされている制約一式が F# でサポートされているということが主な理由で提供されているかのいずれかです。

型の推定プロセスでは、一部の制約がコンパイラによって自動的に推定されます。 たとえば、関数で `+` 演算子を使用する場合、コンパイラでは、式で使用されている変数型に対する明示的なメンバー制約が推定されます。

次のコードでは、いくつかの制約宣言を示しています。

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> =
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a>関連項目

- [ジェネリック](index.md)
- [制約](constraints.md)
