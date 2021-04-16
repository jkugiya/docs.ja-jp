---
ms.openlocfilehash: 4125df1d64fe7f3f2eb1eb4a821ed46c8270c95f
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "97531921"
---
### <a name="exclude-specific-types-and-their-derived-types"></a><span data-ttu-id="af5c1-101">特定の型とその派生型を除外する</span><span class="sxs-lookup"><span data-stu-id="af5c1-101">Exclude specific types and their derived types</span></span>

<span data-ttu-id="af5c1-102">分析から特定の型とその派生型を除外できます。</span><span class="sxs-lookup"><span data-stu-id="af5c1-102">You can exclude specific types and their derived types from analysis.</span></span> <span data-ttu-id="af5c1-103">たとえば、`MyType` という名前の型のメソッドとその派生型で規則を実行しないように指定するには、プロジェクトの *.editorconfig* ファイルに次のキーと値のペアを追加します。</span><span class="sxs-lookup"><span data-stu-id="af5c1-103">For example, to specify that the rule should not run on any methods within types named `MyType` and their derived types, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType
```

<span data-ttu-id="af5c1-104">オプションの値で使用できるシンボル名の形式 (`|` で区切ります):</span><span class="sxs-lookup"><span data-stu-id="af5c1-104">Allowed symbol name formats in the option value (separated by `|`):</span></span>

- <span data-ttu-id="af5c1-105">型の名前のみ (包含する型または名前空間に関係なく、その名前が指定されたすべての型が含まれます)。</span><span class="sxs-lookup"><span data-stu-id="af5c1-105">Type name only (includes all types with the name, regardless of the containing type or namespace).</span></span>
- <span data-ttu-id="af5c1-106">そのシンボルの[ドキュメント ID 形式](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)の完全修飾名 (オプションで `T:` プレフィックスも使用可)。</span><span class="sxs-lookup"><span data-stu-id="af5c1-106">Fully qualified names in the symbol's [documentation ID format](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings), with an optional `T:` prefix.</span></span>

<span data-ttu-id="af5c1-107">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="af5c1-107">Examples:</span></span>

| <span data-ttu-id="af5c1-108">オプション値</span><span class="sxs-lookup"><span data-stu-id="af5c1-108">Option Value</span></span> | <span data-ttu-id="af5c1-109">まとめ</span><span class="sxs-lookup"><span data-stu-id="af5c1-109">Summary</span></span> |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType` | <span data-ttu-id="af5c1-110">`MyType` という名前のすべての型と、そのすべての派生型を検索します。</span><span class="sxs-lookup"><span data-stu-id="af5c1-110">Matches all types named `MyType` and all of their derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType1|MyType2` | <span data-ttu-id="af5c1-111">`MyType1` または `MyType2` という名前のすべての型と、そのすべての派生型を検索します。</span><span class="sxs-lookup"><span data-stu-id="af5c1-111">Matches all types named either `MyType1` or `MyType2` and all of their derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS.MyType` | <span data-ttu-id="af5c1-112">指定された完全修飾名を持つ特定の型 `MyType` と、そのすべての派生型を検索します。</span><span class="sxs-lookup"><span data-stu-id="af5c1-112">Matches specific type `MyType` with given fully qualified name and all of its derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS1.MyType1|M:NS2.MyType2` | <span data-ttu-id="af5c1-113">それぞれの完全修飾名を持つ特定の型 `MyType1` または `MyType2` と、そのすべての派生型を検索します。</span><span class="sxs-lookup"><span data-stu-id="af5c1-113">Matches specific types `MyType1` and `MyType2` with the respective fully qualified names, and all of their derived types.</span></span> |
