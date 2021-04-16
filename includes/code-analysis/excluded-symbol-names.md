---
ms.openlocfilehash: 83644b9205d650da68c910095dd1d22a14940c44
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "97366857"
---
### <a name="exclude-specific-symbols"></a><span data-ttu-id="c6a3a-101">特定のシンボルを除外する</span><span class="sxs-lookup"><span data-stu-id="c6a3a-101">Exclude specific symbols</span></span>

<span data-ttu-id="c6a3a-102">型やメソッドなど、特定のシンボルを分析から除外することができます。</span><span class="sxs-lookup"><span data-stu-id="c6a3a-102">You can exclude specific symbols, such as types and methods, from analysis.</span></span> <span data-ttu-id="c6a3a-103">たとえば、`MyType` という名前の型のコードで規則を実行しないように指定するには、プロジェクトの *.editorconfig* ファイルに次のキーと値のペアを追加します。</span><span class="sxs-lookup"><span data-stu-id="c6a3a-103">For example, to specify that the rule should not run on any code within types named `MyType`, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType
```

<span data-ttu-id="c6a3a-104">オプションの値で使用できるシンボル名の形式 (`|` で区切ります):</span><span class="sxs-lookup"><span data-stu-id="c6a3a-104">Allowed symbol name formats in the option value (separated by `|`):</span></span>

- <span data-ttu-id="c6a3a-105">シンボル名のみ (包含する型または名前空間に関係なく、その名前が指定されたすべてのシンボルが含まれます)。</span><span class="sxs-lookup"><span data-stu-id="c6a3a-105">Symbol name only (includes all symbols with the name, regardless of the containing type or namespace).</span></span>
- <span data-ttu-id="c6a3a-106">そのシンボルの[ドキュメント ID 形式](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)の完全修飾名。</span><span class="sxs-lookup"><span data-stu-id="c6a3a-106">Fully qualified names in the symbol's [documentation ID format](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings).</span></span> <span data-ttu-id="c6a3a-107">各シンボル名には、メソッドには `M:`、型には `T:`、名前空間には `N:` のように、シンボルの種類のプレフィックスが必要です。</span><span class="sxs-lookup"><span data-stu-id="c6a3a-107">Each symbol name requires a symbol-kind prefix, such as `M:` for methods, `T:` for types, and `N:` for namespaces.</span></span>
- <span data-ttu-id="c6a3a-108">コンストラクターには `.ctor`、静的コンストラクターには `.cctor`。</span><span class="sxs-lookup"><span data-stu-id="c6a3a-108">`.ctor` for constructors and `.cctor` for static constructors.</span></span>

<span data-ttu-id="c6a3a-109">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c6a3a-109">Examples:</span></span>

| <span data-ttu-id="c6a3a-110">オプション値</span><span class="sxs-lookup"><span data-stu-id="c6a3a-110">Option Value</span></span> | <span data-ttu-id="c6a3a-111">まとめ</span><span class="sxs-lookup"><span data-stu-id="c6a3a-111">Summary</span></span> |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType` | <span data-ttu-id="c6a3a-112">`MyType` という名前のすべてのシンボルを検索します。</span><span class="sxs-lookup"><span data-stu-id="c6a3a-112">Matches all symbols named `MyType`.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType1|MyType2` | <span data-ttu-id="c6a3a-113">`MyType1` または `MyType2` という名前のすべてのシンボルを検索します。</span><span class="sxs-lookup"><span data-stu-id="c6a3a-113">Matches all symbols named either `MyType1` or `MyType2`.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS.MyType.MyMethod(ParamType)` | <span data-ttu-id="c6a3a-114">指定された完全修飾シグネチャを持つ特定のメソッド `MyMethod` を検索します。</span><span class="sxs-lookup"><span data-stu-id="c6a3a-114">Matches specific method `MyMethod` with the specified fully qualified signature.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS1.MyType1.MyMethod1(ParamType)|M:NS2.MyType2.MyMethod2(ParamType)` | <span data-ttu-id="c6a3a-115">それぞれの完全修飾シグネチャを持つ特定のメソッド `MyMethod1` または `MyMethod2` を検索します。</span><span class="sxs-lookup"><span data-stu-id="c6a3a-115">Matches specific methods `MyMethod1` and `MyMethod2` with the respective fully qualified signatures.</span></span> |
