---
description: '詳細情報: 文字列型 (String) (Visual Basic)'
title: 文字列型 (String)
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: 6597a5c4b8ee0eb961d3e33bee52ae493068da35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792116"
---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="c0c07-103">文字列型 (String) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0c07-103">String Data Type (Visual Basic)</span></span>

<span data-ttu-id="c0c07-104">0 から 65535 までの値の範囲の符号なし 16 ビット (2 バイト) のコード ポイントにシーケンスを保持します。</span><span class="sxs-lookup"><span data-stu-id="c0c07-104">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="c0c07-105">各 *コード ポイント* (文字コード) は、1 つの Unicode 文字を表します。</span><span class="sxs-lookup"><span data-stu-id="c0c07-105">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="c0c07-106">文字列には、0 ～ 約 20 億 (2 ^ 31) の Unicode 文字を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c0c07-106">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0c07-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="c0c07-107">Remarks</span></span>  

 <span data-ttu-id="c0c07-108">`String` データ型を使用して、`Char` 要素の配列である `Char()` の配列管理のオーバーヘッドを発生させることなく、複数の文字を保持します。</span><span class="sxs-lookup"><span data-stu-id="c0c07-108">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="c0c07-109">`String` の既定値は `Nothing` (null 参照) です。</span><span class="sxs-lookup"><span data-stu-id="c0c07-109">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="c0c07-110">これは空の文字列 (値 `""`) と同じではありません。</span><span class="sxs-lookup"><span data-stu-id="c0c07-110">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="c0c07-111">Unicode 文字</span><span class="sxs-lookup"><span data-stu-id="c0c07-111">Unicode Characters</span></span>  

 <span data-ttu-id="c0c07-112">Unicode の最初の 128 コード ポイント (0 ～ 127) は、標準の米国キーボードの文字と記号に対応しています。</span><span class="sxs-lookup"><span data-stu-id="c0c07-112">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="c0c07-113">これらの最初の 128 コード ポイントは、ASCII 文字セットで定義されているものと同じです。</span><span class="sxs-lookup"><span data-stu-id="c0c07-113">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="c0c07-114">2 番目の 128 コード ポイント (128 ～ 255) は、ラテン語に基づくアルファベット文字、アクセント、通貨記号、分数などの特殊文字を表します。</span><span class="sxs-lookup"><span data-stu-id="c0c07-114">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="c0c07-115">Unicode では、さまざまな記号に残りのコード ポイント (256-65535) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c0c07-115">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="c0c07-116">これには、世界中のテキスト文字、分音記号、算術記号、および技術用記号が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c0c07-116">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="c0c07-117">`String` 変数内の個々の文字に対して <xref:System.Char.IsDigit%2A> や <xref:System.Char.IsPunctuation%2A> などのメソッドを使用して、その Unicode の分類を判断できます。</span><span class="sxs-lookup"><span data-stu-id="c0c07-117">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="c0c07-118">書式の要件</span><span class="sxs-lookup"><span data-stu-id="c0c07-118">Format Requirements</span></span>  

 <span data-ttu-id="c0c07-119">`String` リテラルは、引用符 (`" "`) で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0c07-119">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="c0c07-120">文字列内の文字のいずれかとして引用符を含める必要がある場合は、2 つの連続する引用符 (`""`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c0c07-120">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="c0c07-121">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c0c07-121">The following example illustrates this.</span></span>  
  
```vb  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="c0c07-122">文字列内の引用符を表す連続する引用符は、`String` リテラルを開始および終了する引用符とは独立しています。</span><span class="sxs-lookup"><span data-stu-id="c0c07-122">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="c0c07-123">文字列の処理</span><span class="sxs-lookup"><span data-stu-id="c0c07-123">String Manipulations</span></span>  

 <span data-ttu-id="c0c07-124">文字列を `String` 変数に割り当てた後、その文字列は *不変* になります。つまり、長さや内容を変更できなくなります。</span><span class="sxs-lookup"><span data-stu-id="c0c07-124">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="c0c07-125">文字列を何らかの方法で変更すると、Visual Basic によって新しい文字列が作成され、前の文字列が破棄されます。</span><span class="sxs-lookup"><span data-stu-id="c0c07-125">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="c0c07-126">その後、`String` 変数は新しい文字列を指します。</span><span class="sxs-lookup"><span data-stu-id="c0c07-126">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="c0c07-127">さまざまな文字列関数を使用することで、`String` 変数の内容を操作できます。</span><span class="sxs-lookup"><span data-stu-id="c0c07-127">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="c0c07-128"><xref:Microsoft.VisualBasic.Strings.Left%2A> 関数の例を次に示します</span><span class="sxs-lookup"><span data-stu-id="c0c07-128">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```vb  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="c0c07-129">別のコンポーネントによって作成された文字列は、先頭または末尾にスペースが埋め込まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c0c07-129">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="c0c07-130">このような文字列を受け取った場合は、<xref:Microsoft.VisualBasic.Strings.Trim%2A>、<xref:Microsoft.VisualBasic.Strings.LTrim%2A>、および <xref:Microsoft.VisualBasic.Strings.RTrim%2A> の各関数を使用して、これらのスペースを削除できます。</span><span class="sxs-lookup"><span data-stu-id="c0c07-130">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="c0c07-131">文字列操作の詳細については、「[文字列](../../programming-guide/language-features/strings/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0c07-131">For more information about string manipulations, see [Strings](../../programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="c0c07-132">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="c0c07-132">Programming Tips</span></span>  
  
- <span data-ttu-id="c0c07-133">**負の数値。**</span><span class="sxs-lookup"><span data-stu-id="c0c07-133">**Negative Numbers.**</span></span> <span data-ttu-id="c0c07-134">`String` によって保持されている文字は符号なしであり、負の値を表すことはできないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c0c07-134">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="c0c07-135">いかなる場合でも、`String` を使用して数値を保持しないでください。</span><span class="sxs-lookup"><span data-stu-id="c0c07-135">In any case, you should not use `String` to hold numeric values.</span></span>  
  
- <span data-ttu-id="c0c07-136">**相互運用の考慮事項。**</span><span class="sxs-lookup"><span data-stu-id="c0c07-136">**Interop Considerations.**</span></span> <span data-ttu-id="c0c07-137">オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合、他の環境では文字列の文字のデータ幅 (8 ビット) が異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c0c07-137">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="c0c07-138">そのようなコンポーネントに 8 ビット文字の文字列引数を渡す場合は、新しい Visual Basic のコードで、`String` ではなく、`Byte` 要素の配列である `Byte()` として宣言します。</span><span class="sxs-lookup"><span data-stu-id="c0c07-138">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="c0c07-139">**型文字。**</span><span class="sxs-lookup"><span data-stu-id="c0c07-139">**Type Characters.**</span></span> <span data-ttu-id="c0c07-140">ある識別子に識別子の型文字 `$` を付けると、その識別子は `String` データ型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="c0c07-140">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="c0c07-141">`String` にはリテラルの型文字は含まれません。</span><span class="sxs-lookup"><span data-stu-id="c0c07-141">`String` has no literal type character.</span></span> <span data-ttu-id="c0c07-142">ただし、コンパイラでは、引用符 (`" "`) で囲まれたリテラルは、`String` として処理されます。</span><span class="sxs-lookup"><span data-stu-id="c0c07-142">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
- <span data-ttu-id="c0c07-143">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="c0c07-143">**Framework Type.**</span></span> <span data-ttu-id="c0c07-144">.NET Framework において対応する型は、<xref:System.String?displayProperty=nameWithType> クラスです。</span><span class="sxs-lookup"><span data-stu-id="c0c07-144">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0c07-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0c07-145">See also</span></span>

- <xref:System.String?displayProperty=nameWithType>
- [<span data-ttu-id="c0c07-146">データの種類</span><span class="sxs-lookup"><span data-stu-id="c0c07-146">Data Types</span></span>](index.md)
- [<span data-ttu-id="c0c07-147">Char データ型</span><span class="sxs-lookup"><span data-stu-id="c0c07-147">Char Data Type</span></span>](char-data-type.md)
- [<span data-ttu-id="c0c07-148">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="c0c07-148">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="c0c07-149">変換の概要</span><span class="sxs-lookup"><span data-stu-id="c0c07-149">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="c0c07-150">方法: 符号なしの型を使用する Windows の機能を呼び出す</span><span class="sxs-lookup"><span data-stu-id="c0c07-150">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="c0c07-151">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="c0c07-151">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
