---
description: '詳細情報: CStr 関数の戻り値 (Visual Basic)'
title: CStr 関数の戻り値
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: ce45059db8ff8e926954014a09379ee54f1caf30
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731133"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="fdf4d-103">CStr 関数の戻り値 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fdf4d-103">Return Values for the CStr Function (Visual Basic)</span></span>

<span data-ttu-id="fdf4d-104">次の表に、`expression` のさまざまなデータ型に対する `CStr` の戻り値を示します。</span><span class="sxs-lookup"><span data-stu-id="fdf4d-104">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="fdf4d-105">`expression` 型が次の場合</span><span class="sxs-lookup"><span data-stu-id="fdf4d-105">If `expression` type is</span></span>|<span data-ttu-id="fdf4d-106">`CStr` 戻り値</span><span class="sxs-lookup"><span data-stu-id="fdf4d-106">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="fdf4d-107">Boolean データ型</span><span class="sxs-lookup"><span data-stu-id="fdf4d-107">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)|<span data-ttu-id="fdf4d-108">"True" または "False" を格納する文字列。</span><span class="sxs-lookup"><span data-stu-id="fdf4d-108">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="fdf4d-109">Date データ型</span><span class="sxs-lookup"><span data-stu-id="fdf4d-109">Date Data Type</span></span>](../data-types/date-data-type.md)|<span data-ttu-id="fdf4d-110">システムの短い日付形式の `Date` 値 (日付と時刻) を格納する文字列。</span><span class="sxs-lookup"><span data-stu-id="fdf4d-110">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="fdf4d-111">数値のデータ型</span><span class="sxs-lookup"><span data-stu-id="fdf4d-111">Numeric Data Types</span></span>](../../programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="fdf4d-112">数を表す文字列。</span><span class="sxs-lookup"><span data-stu-id="fdf4d-112">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="fdf4d-113">CStr と Date</span><span class="sxs-lookup"><span data-stu-id="fdf4d-113">CStr and Date</span></span>  

 <span data-ttu-id="fdf4d-114">`Date` 型には、常に日付と時刻の両方の情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="fdf4d-114">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="fdf4d-115">型変換の目的で、Visual Basic では、1/1/0001 (1 年の 1 月 1 日) を日付の *ニュートラル値* と見なし、00:00:00 (午前 0 時) を時刻のニュートラル値と見なします。</span><span class="sxs-lookup"><span data-stu-id="fdf4d-115">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="fdf4d-116">`CStr` では、結果の文字列にニュートラル値が含まれません。</span><span class="sxs-lookup"><span data-stu-id="fdf4d-116">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="fdf4d-117">たとえば、`#January 1, 0001 9:30:00#` を文字列に変換した場合、結果は "9:30:00 AM" になります。日付情報は含まれません。</span><span class="sxs-lookup"><span data-stu-id="fdf4d-117">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="fdf4d-118">ただし、日付情報は元の `Date` 値には引き続き存在しているため、<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> などの関数を使用して回復できます。</span><span class="sxs-lookup"><span data-stu-id="fdf4d-118">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fdf4d-119">`CStr` 関数では、アプリケーションの現在のカルチャ設定に基づいてその変換が実行されます。</span><span class="sxs-lookup"><span data-stu-id="fdf4d-119">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="fdf4d-120">特定のカルチャの数値の文字列表現を取得するには、数値の `ToString(IFormatProvider)` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="fdf4d-120">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="fdf4d-121">たとえば、型 `Double` の値を `String` に変換する場合は、<xref:System.Double.ToString%2A?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="fdf4d-121">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdf4d-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="fdf4d-122">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [<span data-ttu-id="fdf4d-123">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="fdf4d-123">Type Conversion Functions</span></span>](type-conversion-functions.md)
- [<span data-ttu-id="fdf4d-124">Boolean データ型</span><span class="sxs-lookup"><span data-stu-id="fdf4d-124">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="fdf4d-125">Date データ型</span><span class="sxs-lookup"><span data-stu-id="fdf4d-125">Date Data Type</span></span>](../data-types/date-data-type.md)
