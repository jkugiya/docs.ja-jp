---
title: レコード型を使用する - C# チュートリアル
description: レコード型を使用する方法、レコードの階層を構築する方法、クラスではなくレコードを選択する判断基準について説明します。
ms.date: 11/12/2020
ms.openlocfilehash: c8a1922fdf113d046dc087ec289accce4312c4ae
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075538"
---
# <a name="create-record-types"></a>レコード型を作成する

C# 9 で導入された [*レコード*](../../language-reference/builtin-types/record.md) は、クラスまたは構造体の代わりに作成できる新しい参照型です。 レコードがクラスと異なるのは、レコード型では "*値ベースの等値性*" が使用されることです。 レコード型の 2 つの変数は、レコード型の定義が同じで、すべてのフィールドについて、両方のレコードの値が等しい場合、等しいと見なされます。 クラス型の 2 つの変数は、参照されているオブジェクトが同じクラス型であり、変数で同じオブジェクトが参照されている場合に等しくなります。 値ベースの等値性により、レコード型では他にもいくつかの機能が必要になると思われます。 `class` ではなく `record` を宣言すると、コンパイラによってそれらのメンバーの多くが生成されます。

このチュートリアルで学習する内容は次のとおりです。

> [!div class="checklist"]
>
> - `class` または `record` を宣言する必要があるかどうかを判断する。
> - レコード型と位置指定レコード型を宣言する。
> - レコードのコンパイラによって生成されたメソッドを独自のメソッドに置き換える。

## <a name="prerequisites"></a>[前提条件]

C# 9.0 以降のコンパイラが含まれる .NET 5 以降が実行されるように、コンピューターを設定する必要があります。 C# 9.0 コンパイラは、[Visual Studio 2019 バージョン 16.8](https://visualstudio.microsoft.com/vs) 以降または [.NET 5.0 SDK](https://dotnet.microsoft.com/download) 以降で使用できます。

## <a name="characteristics-of-records"></a>レコードの特性

"*レコード*" を定義するには、`class` または `struct` キーワードの代わりに、`record` キーワードを使用して型を宣言します。 レコードは参照型であり、値ベースの等値性のセマンティクスに従います。 値のセマンティクスを適用するため、コンパイラによりレコード型用のいくつかのメソッドが生成されます。

- <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> のオーバーライド。
- パラメーターがレコード型である仮想 `Equals` メソッド。
- <xref:System.Object.GetHashCode?displayProperty=nameWithType> のオーバーライド。
- `operator ==` と `operator !=` のメソッド。
- レコード型によって実装される <xref:System.IEquatable%601?displayProperty=nameWithType>。

さらに、レコードでは <xref:System.Object.ToString?displayProperty=nameWithType> のオーバーライドが提供されます。 コンパイラにより、<xref:System.Object.ToString?displayProperty=nameWithType> を使用してレコードを表示するためのメソッドが合成されます。 このチュートリアルでコードを記述しながら、それらのメンバーについて調べます。 レコードでは、レコードの非破壊的な変化を可能にする `with` 式がサポートされています。

また、より簡潔な構文を使用して "*位置指定レコード*" を宣言することもできます。 位置指定レコードを宣言すると、コンパイラによってさらに多くのメソッドが合成されます。

- パラメーターがレコード宣言の位置指定パラメーターと一致するプライマリ コンストラクター。
- プライマリ コンストラクターの各パラメーターに対するパブリック初期化専用プロパティ。
- レコードからプロパティを抽出するための `Deconstruct` メソッド。

## <a name="build-temperature-data"></a>温度データを作成する

レコードを使用するのが望ましいシナリオには、データと統計に関するものが含まれます。 このチュートリアルでは、さまざまな用途の "*度日数*" を計算するアプリケーションを作成します。 "*度日数*" とは、日、週、または月の単位での熱量 (または熱量不足) の尺度です。 度日数を使用して、エネルギー使用量を追跡および予測します。 暑い日が多いほど空調の使用量が増え、寒い日が多いほど暖房の使用量が増えることを意味します。 度日数は、プラントの作成を管理したり、季節の変化に応じてプラントの成長に関連付けたりするのに役立ちます。 度日数は、気候に合わせて場所を変える種の動物の移動を追跡するのに役立ちます。

数式は、特定の日の平均気温と基準温度に基づいています。 ある期間の度日数を計算するには、その期間の各日の最高気温と最低気温が必要になります。 それでは、新しいアプリケーションの作成を始めましょう。 新しいコンソール アプリケーションを作成します。 "DailyTemperature.cs" という名前の新しいファイルに新しいレコード型を作成します。

:::code language="csharp" source="snippets/record-types/InterimSteps.cs" ID="DailyRecord":::

上記のコードでは、"*位置指定レコード*" が定義されています。 2 つのプロパティ `HighTemp` と `LowTemp` を含む参照型を作成しました。 それらのプロパティは "*初期化専用プロパティ*" であり、コンストラクター内で、またはプロパティ初期化子を使用して、設定できることを意味します。 `DailyTemperature` 型には、2 つのプロパティと一致する 2 つのパラメーターを持つ "*プライマリ コンストラクター*" もあります。 `DailyTemperature` レコードを初期化するには、プライマリ コンストラクターを使用します。

:::code language="csharp" source="snippets/record-types/Program.cs" ID="DeclareData":::

位置指定レコードも含めて、独自のプロパティやメソッドをレコードに追加することができます。 毎日の平均気温を計算する必要があります。 そのプロパティを `DailyTemperature` レコードに追加できます。

:::code language="csharp" source="snippets/record-types/DailyTemperature.cs" ID="TemperatureRecord":::

このデータを使用できることを確認してみましょう。 次のコードを `Main` メソッドに追加します。

```csharp
foreach (var item in data)
    Console.WriteLine(item);
```

アプリケーションを実行すると、次のような出力が表示されます (スペースの都合で何行か削除されています)。

```dotnetcli
DailyTemperature { HighTemp = 57, LowTemp = 30, Mean = 43.5 }
DailyTemperature { HighTemp = 60, LowTemp = 35, Mean = 47.5 }


DailyTemperature { HighTemp = 80, LowTemp = 60, Mean = 70 }
DailyTemperature { HighTemp = 85, LowTemp = 66, Mean = 75.5 }
```

上記のコードは、コンパイラによって合成された `ToString` のオーバーライドからの出力を示したものです。 別のテキストを使用する場合は、独自のバージョンを記述することで、コンパイラによって `ToString` バージョンが自動的に合成されなくすることができます。

## <a name="compute-degree-days"></a>度日数を計算する

度日数を計算するには、基準温度と特定の日の平均気温との差を計算します。 ある期間の暑さを測定するには、平均気温が基準値を下回っている日を破棄します。 ある期間の寒さを測定するには、平均気温が基準値を上回っている日を破棄します。 たとえば、米国では、暖房と冷房の両方の度日数に対する基準として 65F が使用されています。 これは、暖房や冷房の必要がない温度です。 ある日の平均気温が 70F の場合、その日は 5 冷房度日数で、0 暖房度日数です。 逆に、平均気温が 55F の場合は、その日は 10 暖房度日数で、0 冷房度日数です。

これらの数式を、レコード型の小さな階層として表すことができます。つまり、度日を表す 1 つの抽象型と、暖房度日数と冷房度日数のための 2 つの具象型です。 これらの型は、位置指定レコードにすることもできます。 それらは、プライマリ コンストラクターの引数として、基準温度と一連の毎日の気温レコードを受け取ります。

:::code language="csharp" source="snippets/record-types/InterimSteps.cs" ID="DegreeDaysRecords":::

抽象 `DegreeDays` レコードは、`HeatingDegreeDays` レコードと `CoolingDegreeDays` レコードの両方に対する共有基底クラスです。 派生レコードでのプライマリ コンストラクターの宣言により、基本レコードの初期化を管理する方法が示されています。 派生レコードにより、基本レコードのプライマリ コンストラクターに含まれるすべてのパラメーターに対するパラメーターが宣言されています。 基本レコードにより、それらのプロパティが宣言されて初期化されます。 派生レコードによってそれらは隠ぺいされませんが、基本レコードで宣言されていないパラメーターのプロパティのみが作成されて初期化されます。 この例では、派生レコードによって新しいプライマリ コンストラクター パラメーターが追加されることはありません。 `Main` メソッドに次のコードを追加することで、コードをテストします。

:::code language="csharp" source="snippets/record-types/Program.cs" ID="HeatingAndCooling":::

次のような出力が表示されます。

```dotnetcli
HeatingDegreeDays { BaseTemperature = 65, TempRecords = record_types.DailyTemperature[], DegreeDays = 85 }
CoolingDegreeDays { BaseTemperature = 65, TempRecords = record_types.DailyTemperature[], DegreeDays = 71.5 }
```

## <a name="define-compiler-synthesized-methods"></a>コンパイラ合成メソッドを定義する

コードで、その期間における暖房度日数と冷房度日数の正しい値を計算します。 ただし、この例では、レコードに対する合成メソッドの一部を置き換える必要がある理由を示します。 クローン メソッドを除き、あるレコード型でのどのコンパイラ合成メソッドについても、独自のバージョンを宣言できます。 クローン メソッドにはコンパイラによって生成される名前があり、別の実装を提供することはできません。 これらの合成メソッドには、コピー コンストラクター、<xref:System.IEquatable%601?displayProperty=nameWithType> インターフェイスのメンバー、等値テストと非等値テスト、<xref:System.Object.GetHashCode> が含まれます。 このために、`PrintMembers` を合成します。 独自の `ToString` を宣言することもできますが、継承のシナリオには`PrintMembers` の方が適しています。 独自バージョンの合成メソッドを提供するには、シグネチャが合成メソッドと一致している必要があります。

コンソール出力の `TempRecords` 要素は役に立ちません。 型が表示されるだけで、他には何も表示されません。 合成メソッド `PrintMembers` の独自の実装を提供することにより、この動作を変更できます。 シグネチャは、`record` の宣言に適用される修飾子によって異なります。

- レコード型が `sealed` の場合、シグネチャは `private bool PrintMembers(StringBuilder builder);` です
- レコード型が `sealed` ではなく、`object` から派生している場合は (つまり、基本レコードが宣言されていない場合)、シグネチャは `protected virtual bool PrintMembers(StringBuilder builder);` となります
- レコード型が `sealed` ではなく、別のレコードから派生している場合は、シグネチャは `protected override bool PrintMembers(StringBuilder builder);` となります

これらのルールは、`PrintMembers` の目的を理解することで把握するのが最も簡単です。 `PrintMembers` により、レコード型の各プロパティに関する情報が文字列に追加されます。 コントラクトでは、表示にメンバーを追加するための基本レコードが必要であり、派生メンバーによってそれらのメンバーが追加されるものと想定されています。 各レコード型により、`HeatingDegreeDays` に対する次の例のような `ToString` のオーバーライドが合成されます。

```csharp
public override string ToString()
{
    StringBuilder stringBuilder = new StringBuilder();
    stringBuilder.Append("HeatingDegreeDays");
    stringBuilder.Append(" { ");
    if (PrintMembers(stringBuilder))
    {
        stringBuilder.Append(" ");
    }
    stringBuilder.Append("}");
    return stringBuilder.ToString();
}
```

コレクションの型が出力されない `DegreeDays` レコードで、`PrintMembers` メソッドを宣言します。

:::code language="csharp" source="snippets/record-types/DegreeDays.cs" ID="AddPrintMembers":::

コンパイラのバージョンと一致するように、シグネチャで `virtual protected` メソッドを宣言します。 アクセサーが間違っていても気にしないでください。言語によって正しいシグネチャが適用されます。 合成メソッドの正しい修飾子を忘れた場合は、適切なシグネチャを取得するのに役立つ警告またはエラーがコンパイラによって表示されます。

## <a name="non-destructive-mutation"></a>非破壊的な変化

位置指定レコードの合成メンバーによって、レコードの状態が変更されることはありません。 目標は、変更不可能なレコードをより簡単に作成できるようにすることです。 前に示した `HeatingDegreeDays` と `CoolingDegreeDays` の宣言をもう一度見てみましょう。 追加されたメンバーにより、レコードの値に対する計算は行われますが、状態は変更されません。 位置指定レコードを使用すると、変更不可能な参照型をより簡単に作成できます。

変更不可能な参照型を作成するということは、非破壊的な変化を使用することを意味します。 [`with` 式](../../language-reference/operators/with-expression.md)を使用して、既存のレコード インスタンスに似た新しいレコード インスタンスを作成します。 これらの式は、コピーの構築にコピーを変更する割り当てを追加したものです。 結果として、既存のレコードから各プロパティがコピーされ、必要に応じて変更が加えられた、新しいレコード インスタンスが作成されます。 元のレコードは変更されません。

`with` 式を示すいくつかの機能をプログラムに追加してみましょう。 最初に、同じデータを使用して、成長度日数を計算する新しいレコードを作成してみます。 "*成長度日数*" の場合は、通常、基準として 41F を使用し、基準を上回る温度を測定します。 同じデータを使用するため、`coolingDegreeDays` に似た新しいレコードを作成しますが、異なる基準温度を使用します。

:::code language="csharp" source="snippets/record-types/Program.cs" ID="GrowingDegreeDays":::

計算された度数と、より高い基準温度で生成された値を比較できます。 レコードは "*参照型*" であり、これらのコピーは簡易コピーであることに注意してください。 データの配列はコピーされず、両方のレコードで同じデータが参照されています。 その事実は、他のもう 1 つのシナリオでの利点になります。 成長度日数の場合、過去 5 日間の合計を追跡しておくと便利です。 `with` 式を使用して、異なるソース データで新しいレコードを作成できます。 次のコードを使用すると、これらの累積のコレクションが作成されてから、値が表示されます。

:::code language="csharp" source="snippets/record-types/Program.cs" ID="RunningFiveDayTotal":::

`with` 式を使用して、レコードのコピーを作成することもできます。 `with` 式の中かっこの間には、プロパティを指定しないでください。 それはコピーを作成することを意味し、プロパティは変更されません。

```csharp
var growingDegreeDaysCopy = growingDegreeDays with { };
```

完成したアプリケーションを実行して結果を確認します。

## <a name="summary"></a>まとめ

このチュートリアルでは、レコードのいくつかの側面を見てきました。 レコードにより、基本的な用途がデータの格納である参照型に対する、簡潔な構文が提供されます。 オブジェクト指向のクラスの場合は、基本的な用途は役割を定義することです。 このチュートリアルで焦点を当てた "*位置指定レコード*" を使用すると、簡潔な構文を使用して、レコードの初期化専用プロパティを宣言できます。 コンパイラにより、レコードのコピーと比較のために、レコードの複数のメンバーが合成されます。 レコード型の必要に応じて他のメンバーを追加できます。 コンパイラによって生成されるどのメンバーも状態が変化しないことがわかっている場合は、変更不可能なレコード型を作成できます。 また、`with` 式を使用すると、非破壊的な変化に簡単に対応できます。

レコードにより、型を定義する別の方法が追加されます。 オブジェクトの役割と動作に焦点を当てたオブジェクト指向の階層を作成するには、`class` 定義を使用します。 データを格納する、効率的にコピーするのに十分に小さいデータ構造の場合は、`struct` 型を作成します。 値ベースの等値性と比較が必要で、値をコピーする必要はなく、参照変数を使用したい場合は、`record` 型を作成します。

レコードの詳細な説明については、[レコード型に関する C# 言語のリファレンス記事](../../language-reference/builtin-types/record.md)と[提案されるレコード型の仕様](~/_csharplang/proposals/csharp-9.0/records.md)の記事を参照してください。
