---
title: 挿入文字列
description: 補間された文字列について説明します。これは、F# の式を直接埋め込むことができる特殊な形式の文字列です。
ms.date: 11/12/2020
ms.openlocfilehash: 8c552b44cea7d6c51ec333b6bdd4d407c6f10da7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829688"
---
# <a name="interpolated-strings"></a><span data-ttu-id="d6dba-103">挿入文字列</span><span class="sxs-lookup"><span data-stu-id="d6dba-103">Interpolated strings</span></span>

<span data-ttu-id="d6dba-104">補間された文字列は、F# の式を埋め込むことができる[文字列](strings.md)です。</span><span class="sxs-lookup"><span data-stu-id="d6dba-104">Interpolated strings are [strings](strings.md) that allow you to embed F# expressions into them.</span></span> <span data-ttu-id="d6dba-105">これは、値または式の結果に基づいて文字列の値が変わる可能性があるさまざまなシナリオで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d6dba-105">They are helpful in a wide range of scenarios where the value of a string may change based on the result of a value or expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="d6dba-106">構文</span><span class="sxs-lookup"><span data-stu-id="d6dba-106">Syntax</span></span>

```fsharp
$"string-text {expr}"
$"string-text %format-specifier{expr}"
$"""string-text {"embedded string literal"}"""
```

## <a name="remarks"></a><span data-ttu-id="d6dba-107">解説</span><span class="sxs-lookup"><span data-stu-id="d6dba-107">Remarks</span></span>

<span data-ttu-id="d6dba-108">補間された文字列を使用すると、文字列リテラル内の "穴" にコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="d6dba-108">Interpolated strings let you write code in "holes" inside of a string literal.</span></span> <span data-ttu-id="d6dba-109">基本的な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d6dba-109">Here's a basic example:</span></span>

```fsharp
let name = "Phillip"
let age = 30
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

<span data-ttu-id="d6dba-110">各 `{}` 中かっこのペアで囲まれたコンテンツに、任意の F# 式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d6dba-110">The contents in between each `{}` brace pair can be any F# expression.</span></span>

<span data-ttu-id="d6dba-111">`{}` 中かっこのペアをエスケープするには、次のように 2 つのペアを記述します。</span><span class="sxs-lookup"><span data-stu-id="d6dba-111">To escape a `{}` brace pair, write two of them like so:</span></span>

```fsharp
let str = $"A pair of braces: {{}}"
// "A pair of braces: {}"
```

## <a name="typed-interpolated-strings"></a><span data-ttu-id="d6dba-112">型指定のある補間された文字列</span><span class="sxs-lookup"><span data-stu-id="d6dba-112">Typed interpolated strings</span></span>

<span data-ttu-id="d6dba-113">補間された文字列に F# の書式指定子を使用して、タイプ セーフを適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d6dba-113">Interpolated strings can also have F# format specifiers to enforce type safety.</span></span>

```fsharp
let name = "Phillip"
let age = 30

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

<span data-ttu-id="d6dba-114">上の例では、コードは `name` を渡す必要がある場所で誤って `age` 値を渡します (その逆も同様です)。</span><span class="sxs-lookup"><span data-stu-id="d6dba-114">In the previous example, the code mistakenly passes the `age` value where `name` should be, and vice/versa.</span></span> <span data-ttu-id="d6dba-115">この補間された文字列では書式指定子が使用されているので、これは些細な実行時のバグではなくコンパイル エラーとなります。</span><span class="sxs-lookup"><span data-stu-id="d6dba-115">Because the interpolated strings use format specifiers, this is a compile error instead of a subtle runtime bug.</span></span>

<span data-ttu-id="d6dba-116">補間された文字列内では、「[プレーンテキストの書式指定](plaintext-formatting.md)」で説明されているすべての書式指定子が有効となります。</span><span class="sxs-lookup"><span data-stu-id="d6dba-116">All format specifiers covered in [plaintext formatting](plaintext-formatting.md) are valid inside of an interpolated string.</span></span>

## <a name="verbatim-interpolated-strings"></a><span data-ttu-id="d6dba-117">逐語的な補間された文字列</span><span class="sxs-lookup"><span data-stu-id="d6dba-117">Verbatim interpolated strings</span></span>

<span data-ttu-id="d6dba-118">F# では、文字列リテラルを埋め込むことができるように、三重引用符を使用した逐語的な補間された文字列がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d6dba-118">F# supports verbatim interpolated strings with triple quotes so that you can embed string literals.</span></span>

```fsharp
let age = 30

printfn $"""Name: {"Phillip"}, Age: %d{age}"""
```

## <a name="aligning-expressions-in-interpolated-strings"></a><span data-ttu-id="d6dba-119">補間された文字列内での式の配置</span><span class="sxs-lookup"><span data-stu-id="d6dba-119">Aligning expressions in interpolated strings</span></span>

<span data-ttu-id="d6dba-120">`|` を使用し、スペースの数を指定することで、補間された文字列内で式を左揃えまたは右揃えにできます。</span><span class="sxs-lookup"><span data-stu-id="d6dba-120">You can left-align or right-align expressions inside interpolated strings with `|` and a specification of how many spaces.</span></span> <span data-ttu-id="d6dba-121">次の補間された文字列では、それぞれスペース 7 つを使用して、式を左揃えおよび右揃えにします。</span><span class="sxs-lookup"><span data-stu-id="d6dba-121">The following interpolated string aligns the left and right expressions to the left and right, respectively, by seven spaces.</span></span>

```fsharp
printfn $"""|{"Left",-7}|{"Right",7}|"""
// |Left   |  Right|
```

## <a name="interpolated-strings-and-formattablestring-formatting"></a><span data-ttu-id="d6dba-122">補間された文字列と `FormattableString` 書式指定</span><span class="sxs-lookup"><span data-stu-id="d6dba-122">Interpolated strings and `FormattableString` formatting</span></span>

<span data-ttu-id="d6dba-123"><xref:System.FormattableString> の規則に従う書式指定を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d6dba-123">You can also apply formatting that adheres to the rules for <xref:System.FormattableString>:</span></span>

```fsharp
let speedOfLight = 299792.458
printfn $"The speed of light is {speedOfLight:N3} km/s."
// "The speed of light is 299,792.458 km/s."
```

<span data-ttu-id="d6dba-124">さらに、型の注釈によって、補間された文字列を <xref:System.FormattableString> として型チェックできます。</span><span class="sxs-lookup"><span data-stu-id="d6dba-124">Additionally, an interpolated string can also be type checked as a <xref:System.FormattableString> via a type annotation:</span></span>

```fsharp
let frmtStr = $"The speed of light is {speedOfLight:N3} km/s." : FormattableString
// Type: FormattableString
// The speed of light is 299,792.458 km/s.
```

<span data-ttu-id="d6dba-125">型の注釈は、補間された文字列式自体に対して指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6dba-125">Note that the type annotation must be on the interpolated string expression itself.</span></span> <span data-ttu-id="d6dba-126">F# では、補間された文字列は暗黙的に <xref:System.FormattableString> に変換されません。</span><span class="sxs-lookup"><span data-stu-id="d6dba-126">F# does not implicitly convert an interpolated string into a <xref:System.FormattableString>.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6dba-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6dba-127">See also</span></span>

* [<span data-ttu-id="d6dba-128">文字列</span><span class="sxs-lookup"><span data-stu-id="d6dba-128">Strings</span></span>](strings.md)
