---
title: '例外: try...with 式'
description: F# の 'try...with' 式を使用して例外処理を行う方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: e4d615086a93e26b76cca460e797659ca13792b5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630252"
---
# <a name="exceptions-the-trywith-expression"></a>例外: try...with 式

このトピックでは、F# 言語での例外処理に使用される式である `try...with` 式について説明します。

## <a name="syntax"></a>構文

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a>解説

`try...with` 式は、F# で例外を処理するために使用されます。 これは、C# の `try...catch` ステートメントに似ています。 前の構文で、*expression1* のコードによって例外が生成されるとします。 `try...with` 式によって値が返されます。 例外がスローされない場合、式全体によって *expression1* の値が返されます。 例外がスローされた場合、各 "*パターン*" がその例外と比較され、最初の一致パターンで、そのブランチに対応する "*式*" ("*例外ハンドラー*" と呼ばれる) が実行され、式全体により、その例外ハンドラーの式の値が返されます。 一致するパターンがない場合、例外は、一致するハンドラーが見つかるまで呼び出し履歴をさかのぼります。 例外ハンドラー内の各式から返される値の型は、`try` ブロック内の式から返される型と一致する必要があります。

多くの場合、エラーが発生したということは、各例外ハンドラーの式から返される有効な値がないことも示します。 一般的なパターンは、式の型がオプション型になるというものです。 このパターンを次のコード例に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

例外は .NET 例外とすることも、F# 例外とすることもできます。 `exception` キーワードを使用して、F# 例外を定義できます。

さまざまなパターンを使用して、例外の種類やその他の条件を基にフィルター処理が行えます。次の表に、オプションの概要を示します。

|パターン|説明|
|-------|-----------|
|:? *exception-type*|指定された .NET 例外の種類と一致します。|
|:? *exception-type* as *identifier*|指定された .NET 例外の種類と一致しますが、例外に名前付きの値を指定します。|
|*exception-name*(*arguments*)|F# 例外の種類と一致し、引数をバインドします。|
|*identifier*|任意の例外と一致し、その名前を例外オブジェクトにバインドします。 **:?System.Exception as**_identifier_ と同じです|
|*identifier* when *condition*|条件が true の場合、すべての例外と一致します。|

## <a name="examples"></a>例

次のコード例は、さまざまな例外ハンドラー パターンの使用方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> `try...with` コンストラクトは、`try...finally` 式とは別の式です。 したがって、コードに `with` ブロックと `finally` ブロックの両方が必要な場合は、2 つの式を入れ子にする必要があります。

> [!NOTE]
> `try...with` は、非同期ワークフローやその他のコンピュテーション式で使用することができます。その場合は、`try...with` 式のカスタマイズされたバージョンを使用します。 詳細については、「[非同期ワークフロー](../asynchronous-workflows.md)」、「[コンピュテーション式](../computation-expressions.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [例外処理](index.md)
- [例外の種類](exception-types.md)
- [例外: `try...finally` 式](the-try-finally-expression.md)
