---
description: '詳細については、「方法: 日付と時刻の演算でタイムゾーンを使用する」を参照してください。'
title: '方法: 日付と時刻の演算でタイム ゾーンを使用する'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], arithmetic operations
- arithmetic operations [.NET], dates and times
- dates [.NET], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
ms.openlocfilehash: 74f878da85dc959114013d7296b738e8198fc992
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702367"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="7101d-103">方法: 日付と時刻の演算でタイム ゾーンを使用する</span><span class="sxs-lookup"><span data-stu-id="7101d-103">How to: Use time zones in date and time arithmetic</span></span>

<span data-ttu-id="7101d-104">通常、またはの値を使用して日付と時刻の演算を実行する場合、 <xref:System.DateTime> <xref:System.DateTimeOffset> 結果にはタイムゾーン調整規則は反映されません。</span><span class="sxs-lookup"><span data-stu-id="7101d-104">Ordinarily, when you perform date and time arithmetic using <xref:System.DateTime> or <xref:System.DateTimeOffset> values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="7101d-105">これは、日付と時刻の値のタイムゾーンが明確に識別できる場合 (たとえば、 <xref:System.DateTime.Kind%2A> プロパティがに設定されている場合) にも当てはまり <xref:System.DateTimeKind.Local> ます。</span><span class="sxs-lookup"><span data-stu-id="7101d-105">This is true even when the time zone of the date and time value is clearly identifiable (for example, when the <xref:System.DateTime.Kind%2A> property is set to <xref:System.DateTimeKind.Local>).</span></span> <span data-ttu-id="7101d-106">このトピックでは、特定のタイムゾーンに属する日付と時刻の値に対して算術演算を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7101d-106">This topic shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="7101d-107">算術演算の結果には、タイム ゾーンの調整規則が反映されます。</span><span class="sxs-lookup"><span data-stu-id="7101d-107">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="7101d-108">日付と時刻の演算に調整規則を適用するには</span><span class="sxs-lookup"><span data-stu-id="7101d-108">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="7101d-109">なんらかの方法を実装して、日付と時刻の値と、その値が属するタイム ゾーンを密接に結び付けます。</span><span class="sxs-lookup"><span data-stu-id="7101d-109">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="7101d-110">たとえば、日付と時刻の値とそのタイム ゾーンの両方を含む構造体を宣言します。</span><span class="sxs-lookup"><span data-stu-id="7101d-110">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="7101d-111">次の例では、この方法を使用して、値とそのタイムゾーンをリンクして <xref:System.DateTime> います。</span><span class="sxs-lookup"><span data-stu-id="7101d-111">The following example uses this approach to link a <xref:System.DateTime> value with its time zone.</span></span>

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. <span data-ttu-id="7101d-112">メソッドまたはメソッドのいずれかを呼び出して、時刻を世界協定時刻 (UTC) に変換し <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> <xref:System.TimeZoneInfo.ConvertTime%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="7101d-112">Convert a time to Coordinated Universal Time (UTC) by calling either the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> method or the <xref:System.TimeZoneInfo.ConvertTime%2A> method.</span></span>

3. <span data-ttu-id="7101d-113">UTC 時刻で算術演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="7101d-113">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="7101d-114">メソッドを呼び出して、時刻を UTC から元の時刻に関連付けられているタイムゾーンに変換し <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="7101d-114">Convert the time from UTC to the original time's associated time zone by calling the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span>

## <a name="example"></a><span data-ttu-id="7101d-115">例</span><span class="sxs-lookup"><span data-stu-id="7101d-115">Example</span></span>

<span data-ttu-id="7101d-116">次の例では、中部標準時の 2008 年 3 月 9 日午前 1 時 30 分に、2 時間 30 分を</span><span class="sxs-lookup"><span data-stu-id="7101d-116">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="7101d-117">加えます。</span><span class="sxs-lookup"><span data-stu-id="7101d-117">Central Standard Time.</span></span> <span data-ttu-id="7101d-118">夏時間へのタイム ゾーンの切り替えは、30 分後の 2008 年 3 月 9 日午前 2 時に</span><span class="sxs-lookup"><span data-stu-id="7101d-118">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="7101d-119">発生します。</span><span class="sxs-lookup"><span data-stu-id="7101d-119">on March 9, 2008.</span></span> <span data-ttu-id="7101d-120">この例は前に示した 4 つの手順に従うため、結果は正しい時刻である 2008 年 3 月 9 日午前 5 時に</span><span class="sxs-lookup"><span data-stu-id="7101d-120">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="7101d-121">発生します。</span><span class="sxs-lookup"><span data-stu-id="7101d-121">on March 9, 2008.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

<span data-ttu-id="7101d-122"><xref:System.DateTime>との <xref:System.DateTimeOffset> 値の両方が、所属するタイムゾーンとの関連付けが解除されます。</span><span class="sxs-lookup"><span data-stu-id="7101d-122">Both <xref:System.DateTime> and <xref:System.DateTimeOffset> values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="7101d-123">タイム ゾーンの調整規則が自動的に適用されるような方法で日付と時刻の演算を実行するには、日付と時刻の値の属するタイム ゾーンがすぐに識別できる状態でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="7101d-123">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="7101d-124">つまり、日時と関連付けられているタイム ゾーンを密に結合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7101d-124">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="7101d-125">これは、次のようないくつかの方法で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7101d-125">There are several ways to do this, which include the following:</span></span>

- <span data-ttu-id="7101d-126">アプリケーションで使用されるすべての時刻が、特定のタイム ゾーンに属するものと仮定します。</span><span class="sxs-lookup"><span data-stu-id="7101d-126">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="7101d-127">この方法は、適切な場合もありますが、柔軟性が限られ、移植性が制限される可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="7101d-127">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

- <span data-ttu-id="7101d-128">日時と関連付けられているタイム ゾーンを型のフィールドとして組み込むことで、両者を密に結合する型を定義します。</span><span class="sxs-lookup"><span data-stu-id="7101d-128">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="7101d-129">コード例ではこの方法を使用して、日時とタイム ゾーンを 2 つのメンバー フィールドに格納する構造体を定義しています。</span><span class="sxs-lookup"><span data-stu-id="7101d-129">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

<span data-ttu-id="7101d-130">この例では、値に対して算術演算を実行し、 <xref:System.DateTime> タイムゾーン調整規則が結果に適用されるようにする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7101d-130">The example illustrates how to perform arithmetic operations on <xref:System.DateTime> values so that time zone adjustment rules are applied to the result.</span></span> <span data-ttu-id="7101d-131">ただし、 <xref:System.DateTimeOffset> 値は簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="7101d-131">However, <xref:System.DateTimeOffset> values can be used just as easily.</span></span> <span data-ttu-id="7101d-132">次の例は、元の例のコードを値の代わりに使用するように調整する方法を示してい <xref:System.DateTimeOffset> <xref:System.DateTime> ます。</span><span class="sxs-lookup"><span data-stu-id="7101d-132">The following example illustrates how the code in the original example might be adapted to use <xref:System.DateTimeOffset> instead of <xref:System.DateTime> values.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

<span data-ttu-id="7101d-133">この加算を最初に UTC に変換せずに値に対して実行すると、結果には <xref:System.DateTimeOffset> 正しいポイントが反映されますが、その時間の指定したタイムゾーンのオフセットは反映されません。</span><span class="sxs-lookup"><span data-stu-id="7101d-133">Note that if this addition is simply performed on the <xref:System.DateTimeOffset> value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="7101d-134">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="7101d-134">Compiling the code</span></span>

<span data-ttu-id="7101d-135">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7101d-135">This example requires:</span></span>

- <span data-ttu-id="7101d-136"><xref:System> `using` ステートメント (C# コードでは必須) を使用して名前空間をインポートする。</span><span class="sxs-lookup"><span data-stu-id="7101d-136">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="7101d-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="7101d-137">See also</span></span>

- [<span data-ttu-id="7101d-138">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="7101d-138">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="7101d-139">日付と時刻を使用した算術演算の実行</span><span class="sxs-lookup"><span data-stu-id="7101d-139">Performing arithmetic operations with dates and times</span></span>](performing-arithmetic-operations.md)
