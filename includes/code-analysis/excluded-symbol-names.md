---
ms.openlocfilehash: 83644b9205d650da68c910095dd1d22a14940c44
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "97366857"
---
### <a name="exclude-specific-symbols"></a>特定のシンボルを除外する

型やメソッドなど、特定のシンボルを分析から除外することができます。 たとえば、`MyType` という名前の型のコードで規則を実行しないように指定するには、プロジェクトの *.editorconfig* ファイルに次のキーと値のペアを追加します。

```ini
dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType
```

オプションの値で使用できるシンボル名の形式 (`|` で区切ります):

- シンボル名のみ (包含する型または名前空間に関係なく、その名前が指定されたすべてのシンボルが含まれます)。
- そのシンボルの[ドキュメント ID 形式](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)の完全修飾名。 各シンボル名には、メソッドには `M:`、型には `T:`、名前空間には `N:` のように、シンボルの種類のプレフィックスが必要です。
- コンストラクターには `.ctor`、静的コンストラクターには `.cctor`。

次に例を示します。

| オプション値 | まとめ |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType` | `MyType` という名前のすべてのシンボルを検索します。 |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType1|MyType2` | `MyType1` または `MyType2` という名前のすべてのシンボルを検索します。 |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS.MyType.MyMethod(ParamType)` | 指定された完全修飾シグネチャを持つ特定のメソッド `MyMethod` を検索します。 |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS1.MyType1.MyMethod1(ParamType)|M:NS2.MyType2.MyMethod2(ParamType)` | それぞれの完全修飾シグネチャを持つ特定のメソッド `MyMethod1` または `MyMethod2` を検索します。 |
