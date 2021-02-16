---
description: '詳細情報: 文字列とその他の型との変換 (Visual Basic)'
title: 文字列とその他の型との変換
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: c0f7f7637d173d039d58b2516fba41ae55b990ac
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100477217"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="b1e0b-103">文字列とその他の型との変換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1e0b-103">Conversions Between Strings and Other Types (Visual Basic)</span></span>

<span data-ttu-id="b1e0b-104">数値、`Boolean`、または日付/時刻値を `String` に変換できます。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-104">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="b1e0b-105">文字列の内容が変換先データ型の有効な値と解釈される場合は、逆方向 (文字列値を数値、`Boolean`、または `Date`) に変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-105">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="b1e0b-106">そうでない場合は、実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-106">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="b1e0b-107">これらのすべての代入での変換は、どちらの方向でも縮小変換です。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-107">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="b1e0b-108">型変換キーワード (`CBool`、`CByte`、`CDate`、`CDbl`、`CDec`、`CInt`、`CLng`、`CSByte`、`CShort`、`CSng`、`CStr`、`CUInt`、`CULng`、`CUShort`、および `CType`) を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-108">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="b1e0b-109"><xref:Microsoft.VisualBasic.Strings.Format%2A> 関数や <xref:Microsoft.VisualBasic.Conversion.Val%2A> 関数を使用すると、文字列と数値の間の変換をさらに制御できます。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-109">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="b1e0b-110">クラスまたは構造体を定義している場合は、`String` とクラスまたは構造体の型との間に型変換演算子を定義できます。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-110">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="b1e0b-111">詳細については、「[方法:変換演算子を定義する](../procedures/how-to-define-a-conversion-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-111">For more information, see [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="b1e0b-112">数値から文字列への変換</span><span class="sxs-lookup"><span data-stu-id="b1e0b-112">Conversion of Numbers to Strings</span></span>  

 <span data-ttu-id="b1e0b-113">`Format` 関数を使用して、数値を書式設定された文字列に変換できます。これは、該当する数字だけでなく、通貨記号 (`$` など)、3 桁ごとの区切りつまり "*桁区切り記号*" (`,` など)、小数点 (`.` など) のような書式設定記号を含むことができます。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-113">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="b1e0b-114">`Format` は、Windows の **[コントロール パネル]** に指定された **[地域のオプション]** 設定に従って適切な記号を自動的に使用します。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-114">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="b1e0b-115">次の例のように、連結 (`&`) 演算子を使用して、数値を文字列に暗黙に変換できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-115">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="b1e0b-116">文字列から数値への変換</span><span class="sxs-lookup"><span data-stu-id="b1e0b-116">Conversion of Strings to Numbers</span></span>  

 <span data-ttu-id="b1e0b-117">`Val` 関数を使用すると、明示的に文字列の数字を数値に変換できます。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-117">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="b1e0b-118">`Val` は、数字、スペース、タブ、改行、またはピリオド以外の文字が見つかるまで文字列を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-118">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="b1e0b-119">シーケンス "&O" と "&H" によって記数法の基数が変更され、これでスキャンが終了します。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-119">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="b1e0b-120">読み取りを終了するまで、`Val` は該当するすべての文字を数値に変換します。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-120">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="b1e0b-121">たとえば、次のステートメントでは値 `141.825` が返されます。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-121">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="b1e0b-122">Visual Basic が文字列を数値に変換するとき、Windows の **[コントロール パネル]** の **[地域のオプション]** 設定を使用して、桁区切り記号、小数点、および通貨記号を解釈します。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-122">When Visual Basic converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="b1e0b-123">つまり、変換は 1 つの設定では成功しますが、別の設定では成功しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-123">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="b1e0b-124">たとえば、`"$14.20"` は英語 (米国) のロケールでは許容されますが、フランス語のロケールでは許容されません。</span><span class="sxs-lookup"><span data-stu-id="b1e0b-124">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1e0b-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1e0b-125">See also</span></span>

- [<span data-ttu-id="b1e0b-126">Visual Basic における型変換</span><span class="sxs-lookup"><span data-stu-id="b1e0b-126">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="b1e0b-127">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="b1e0b-127">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="b1e0b-128">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="b1e0b-128">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="b1e0b-129">方法: Visual Basic でオブジェクトを別の型に変換する</span><span class="sxs-lookup"><span data-stu-id="b1e0b-129">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="b1e0b-130">配列変換</span><span class="sxs-lookup"><span data-stu-id="b1e0b-130">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="b1e0b-131">データの種類</span><span class="sxs-lookup"><span data-stu-id="b1e0b-131">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="b1e0b-132">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="b1e0b-132">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="b1e0b-133">グローバル化およびローカライズされたアプリの開発</span><span class="sxs-lookup"><span data-stu-id="b1e0b-133">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)
