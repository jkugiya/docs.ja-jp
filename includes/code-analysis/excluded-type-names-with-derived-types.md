---
ms.openlocfilehash: 4125df1d64fe7f3f2eb1eb4a821ed46c8270c95f
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97531921"
---
### <a name="exclude-specific-types-and-their-derived-types"></a><span data-ttu-id="d4b4b-101">特定の型とその派生型を除外する</span><span class="sxs-lookup"><span data-stu-id="d4b4b-101">Exclude specific types and their derived types</span></span>

<span data-ttu-id="d4b4b-102">分析から特定の型とその派生型を除外できます。</span><span class="sxs-lookup"><span data-stu-id="d4b4b-102">You can exclude specific types and their derived types from analysis.</span></span> <span data-ttu-id="d4b4b-103">たとえば、という名前の型とその派生型内のメソッドで規則を実行しないように指定するには、 `MyType` 次のキーと値のペアをプロジェクトの *editorconfig* ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="d4b4b-103">For example, to specify that the rule should not run on any methods within types named `MyType` and their derived types, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType
```

<span data-ttu-id="d4b4b-104">オプションの値で使用できるシンボル名の形式 (で区切られてい `|` ます):</span><span class="sxs-lookup"><span data-stu-id="d4b4b-104">Allowed symbol name formats in the option value (separated by `|`):</span></span>

- <span data-ttu-id="d4b4b-105">型名のみ (包含する型または名前空間に関係なく、名前を持つすべての型が含まれます)。</span><span class="sxs-lookup"><span data-stu-id="d4b4b-105">Type name only (includes all types with the name, regardless of the containing type or namespace).</span></span>
- <span data-ttu-id="d4b4b-106">シンボルの [ドキュメント ID 形式](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)で、省略可能なプレフィックスを持つ完全修飾名 `T:` 。</span><span class="sxs-lookup"><span data-stu-id="d4b4b-106">Fully qualified names in the symbol's [documentation ID format](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings), with an optional `T:` prefix.</span></span>

<span data-ttu-id="d4b4b-107">例:</span><span class="sxs-lookup"><span data-stu-id="d4b4b-107">Examples:</span></span>

| <span data-ttu-id="d4b4b-108">オプション値</span><span class="sxs-lookup"><span data-stu-id="d4b4b-108">Option Value</span></span> | <span data-ttu-id="d4b4b-109">まとめ</span><span class="sxs-lookup"><span data-stu-id="d4b4b-109">Summary</span></span> |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType` | <span data-ttu-id="d4b4b-110">`MyType`と、そのすべての派生型と一致するすべての型を照合します。</span><span class="sxs-lookup"><span data-stu-id="d4b4b-110">Matches all types named `MyType` and all of their derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType1|MyType2` | <span data-ttu-id="d4b4b-111">`MyType1`または `MyType2` すべての派生型のいずれかという名前のすべての型と一致します。</span><span class="sxs-lookup"><span data-stu-id="d4b4b-111">Matches all types named either `MyType1` or `MyType2` and all of their derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS.MyType` | <span data-ttu-id="d4b4b-112">`MyType`指定された完全修飾名とそのすべての派生型を使用して、特定の型を照合します。</span><span class="sxs-lookup"><span data-stu-id="d4b4b-112">Matches specific type `MyType` with given fully qualified name and all of its derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS1.MyType1|M:NS2.MyType2` | <span data-ttu-id="d4b4b-113">特定の型 `MyType1` と、 `MyType2` それぞれの完全修飾名、およびそのすべての派生型を照合します。</span><span class="sxs-lookup"><span data-stu-id="d4b4b-113">Matches specific types `MyType1` and `MyType2` with the respective fully qualified names, and all of their derived types.</span></span> |