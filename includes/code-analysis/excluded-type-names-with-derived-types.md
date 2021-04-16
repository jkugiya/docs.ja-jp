---
ms.openlocfilehash: 4125df1d64fe7f3f2eb1eb4a821ed46c8270c95f
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "97531921"
---
### <a name="exclude-specific-types-and-their-derived-types"></a>特定の型とその派生型を除外する

分析から特定の型とその派生型を除外できます。 たとえば、`MyType` という名前の型のメソッドとその派生型で規則を実行しないように指定するには、プロジェクトの *.editorconfig* ファイルに次のキーと値のペアを追加します。

```ini
dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType
```

オプションの値で使用できるシンボル名の形式 (`|` で区切ります):

- 型の名前のみ (包含する型または名前空間に関係なく、その名前が指定されたすべての型が含まれます)。
- そのシンボルの[ドキュメント ID 形式](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)の完全修飾名 (オプションで `T:` プレフィックスも使用可)。

次に例を示します。

| オプション値 | まとめ |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType` | `MyType` という名前のすべての型と、そのすべての派生型を検索します。 |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType1|MyType2` | `MyType1` または `MyType2` という名前のすべての型と、そのすべての派生型を検索します。 |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS.MyType` | 指定された完全修飾名を持つ特定の型 `MyType` と、そのすべての派生型を検索します。 |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS1.MyType1|M:NS2.MyType2` | それぞれの完全修飾名を持つ特定の型 `MyType1` または `MyType2` と、そのすべての派生型を検索します。 |
