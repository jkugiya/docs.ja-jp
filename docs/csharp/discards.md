---
title: 破棄 - C# ガイド
description: C# の破棄のサポートについて説明します。破棄は、未割り当てで破棄可能な変数です。また、破棄の使用例についても説明します。
ms.technology: csharp-fundamentals
ms.date: 09/22/2020
ms.openlocfilehash: eefa81d3bd8d56c9296e01533aaf93c4725323a3
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104953"
---
# <a name="discards---c-guide"></a>破棄 - C# ガイド

C# 7.0 以降では、C# で破棄がサポートされます。これらは、アプリケーション コードで意図的に使用しないプレースホルダー変数です。 破棄は、未割り当ての変数と同等です。つまり、値がありません。 破棄によって、あなたのコードを読み取るコンパイラおよびその他のユーザーに対して、次のような意図が伝わります。あなたは式の結果を無視するつもりでした。 あなたは、式の結果、タプル式の 1 つ以上のメンバー、メソッドの `out` パラメーター、またはパターン マッチング式のターゲットを無視したい可能性があります。

破棄変数は 1 つしかないため、その変数にストレージが割り当てられていない可能性もあります。 破棄すると、メモリ割り当てを減らすことができます。 破棄することで、コードの意図が明確になります。 そのため、読みやすさと保守容易性が向上します。

変数を破棄と指定するには、変数名にアンダースコア (`_`) を指定します。 たとえば、次のメソッド呼び出しでタプルが返され、1 つ目と 2 つ目の値は破棄です。 `area` は、`GetCityInformation` によって返される 3 つ目のコンポーネントに設定された、以前に宣言された変数です。

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

C# 9.0 以降では、破棄を使用して、ラムダ式の未使用の入力パラメーターを指定できます。 詳細については、[ラムダ式](language-reference/operators/lambda-expressions.md)に関する記事の「[ラムダ式の入力パラメーター](language-reference/operators/lambda-expressions.md#input-parameters-of-a-lambda-expression)」セクションを参照してください。

`_` が有効な破棄の場合、その値を取得しようとすると、または代入演算で使用しようとすると、"名前 '\_' は、現在のコンテキストに存在していません" というコンパイラ エラー CS0301 が生成されます。 このエラーの原因は、`_` に値が割り当てられておらず、記憶域の場所も割り当てることができないことです。 実際の変数であれば、前の例のように、複数の値を破棄できません。

## <a name="tuple-and-object-deconstruction"></a>タプルとオブジェクトの分解

分解は、複数のタプルがあり、アプリケーション コードで一部のタプル要素を使用し、その他の要素を無視する場合に便利です。 たとえば、次の `QueryCityDataForYears` メソッドは、市区町村名、その地域、年、市区町村のその年の人口、2 つ目の年、市区町村のその 2 つ目の年の人口というタプルを返します。 この例は、2 つの年の間に変化した人口数を示しています。 タプルから使用できるデータのうち、市区町村の地域は使用しません。また、指定時に市区町村名と 2 つの日付はわかっています。 そのため、タプルに格納されている 2 つの人口値のみが必要であり、残りの値は破棄対象として処理できます。  

:::code language="csharp" source="snippets/discards/discard-tuple.cs" ID="DiscardTupleMember" :::

破棄を使用したタプルの分解の詳細については、「[タプルとその他の型の分解](deconstruct.md#deconstructing-tuple-elements-with-discards)」を参照してください。

また、クラス、構造体、またはインターフェイスの `Deconstruct` メソッドを使用すると、オブジェクトから特定セットのデータを取得し、分解することもできます。 分解された値の一部のみが必要な場合は、破棄を使用できます。 `Person` オブジェクトを 4 つの文字列 (名、姓、市区町村、州) に分解し、姓と州を破棄する例を次に示します。

:::code language="csharp" source="snippets/discards/discard-class.cs" :::

破棄を使用したユーザー定義型の分解の詳細については、「[タプルとその他の型の分解](deconstruct.md#deconstructing-a-user-defined-type-with-discards)」を参照してください。

## <a name="pattern-matching-with-switch"></a>`switch` を使用したパターン マッチング

"*破棄パターン*" は、[switch 式](language-reference/operators/switch-expression.md)を使用したパターン マッチングで使用できます。 `null` も含め、あらゆる式は常に破棄パターンと一致します。

`switch` 式を使用して、オブジェクトが <xref:System.IFormatProvider> 実装を提供しているかどうかを判断し、オブジェクトが `null` かどうかをテストする `ProvidesFormatInfo` メソッドの定義例を次に示します。 また、破棄パターンを使用して、その他の任意の型の null 以外のオブジェクトを処理します。

:::code language="csharp" source="snippets/discards/discard-pattern2.cs" ID="DiscardSwitchExample" :::

## <a name="calls-to-methods-with-out-parameters"></a>`out` パラメーターを使用したメソッドの呼び出し

`Deconstruct` メソッドを呼び出してユーザー定義型 (クラス、構造体、またはインターフェイスのインスタンス) を分解する場合、個々の `out` 引数の値を破棄できます。 また、`out` パラメーターを指定して任意のメソッドを呼び出すときに、`out` 引数の値を破棄することもできます

次の例では、[DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) メソッドを呼び出して、現在のカルチャで日付の文字列表現が有効かどうかを判断します。 この例では、日付文字列の検証のみが目的で、解析して日付を抽出する処理は行わないため、メソッドの `out` 引数は破棄されます。

:::code language="csharp" source="snippets/discards/discard-out1.cs" ID="DiscardOutParameter" :::

## <a name="a-standalone-discard"></a>スタンドアロンの破棄

スタンドアロンの破棄を使用して、無視対象として任意の変数を指定できます。 一般的な用途の 1 つは、割り当てを使用して、引数が null でないことを確認することです。 次のコードでは、破棄を使用して割り当てを強制しています。 代入の右側には [null 合体演算子](language-reference/operators/null-coalescing-operator.md)が使用され、引数が `null` の場合に <xref:System.ArgumentNullException?displayProperty=nameWithType> がスローされます。 このコードに割り当ての結果は不要なため、破棄されます。 式によって null チェックが強制的に実行されます。 破棄を使用して、割り当ての結果は必要ではないか、使用されない、という意図を明確にします。

:::code language="csharp" source="snippets/discards/standalone-discard1.cs" ID="ArgNullCheck" :::

次の例では、スタンドアロンの破棄を使用して、非同期操作で返される <xref:System.Threading.Tasks.Task> オブジェクトを無視します。 タスクの割り当ての結果、この処理が完了するときにスローされる例外が抑制される効果があります。 これにより、次のようなあなたの意図が明確になります。あなたは、`Task` を破棄し、その非同期操作から生成されるエラーを無視したいと考えています。

:::code language="csharp" source="snippets/discards/standalone-discard1.cs" ID="SnippetDiscardTask" :::

タスクを破棄に割り当てないと、次のコードにより、コンパイラの警告が生成されます。

:::code language="csharp" source="snippets/discards/standalone-discard1.cs" ID="SnippetNoDiscardTask" :::

> [!NOTE]
> デバッガーを使用して上の 2 つのサンプルのいずれかを実行すると、例外がスローされたときにデバッガーによってプログラムが停止します。 デバッガーがアタッチされていない場合、どちらの場合も例外は警告なしで無視されます。

`_` は有効な識別子でもあります。 サポートされるコンテキスト以外で `_` を使用すると、破棄対象ではなく、有効な変数として扱われます。 `_` という識別子が既にスコープ内にある場合、スタンドアロンの破棄として `_` を使用すると、次のような結果になります。

- 意図した破棄の値を割り当てることで、スコープ内の `_` 変数の値が誤って変更される。 次に例を示します。
   :::code language="csharp" source="snippets/discards/standalone-discard2.cs" ID="VariableIdentifier" :::
- タイプ セーフに違反するコンパイラ エラーが発生する。 次に例を示します。
   :::code language="csharp" source="snippets/discards/standalone-discard2.cs" ID="VariableTypeInference" :::
- コンパイラ エラー CS0136 "ローカルまたはパラメーター '\_' は、その名前が外側のローカルのスコープでローカルやパラメーターの定義に使用されているため、このスコープでは宣言できません" が発生する。 次に例を示します。
   :::code language="csharp" source="snippets/discards/standalone-discard2.cs" ID="CannotRedeclare" :::

## <a name="see-also"></a>関連項目

- [タプルとその他の型の分解](deconstruct.md)
- [`is` キーワード](language-reference/keywords/is.md)
- [`switch` キーワード](language-reference/keywords/switch.md)
