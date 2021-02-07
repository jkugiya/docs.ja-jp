---
description: '詳細については、「方法: あいまいな時刻を解決する」を参照してください。'
title: '方法: あいまいな時刻を解決する'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], ambiguous time
- ambiguous time [.NET]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
ms.openlocfilehash: 743aff3303669efcf20e233b1f5b2d520475d5f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702523"
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="2b2de-103">方法: あいまいな時刻を解決する</span><span class="sxs-lookup"><span data-stu-id="2b2de-103">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="2b2de-104">あいまいな時刻は複数の世界協定時刻 (UTC) にマップされる時刻です。</span><span class="sxs-lookup"><span data-stu-id="2b2de-104">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="2b2de-105">あいまいな時刻は、あるタイム ゾーンの夏時間から標準時間に移行する際など、時計の時刻を前に戻すときに発生します。</span><span class="sxs-lookup"><span data-stu-id="2b2de-105">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="2b2de-106">あいまいな時刻を処理する場合は、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2b2de-106">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="2b2de-107">時刻が UTC にどのようにマップされるかを想定します。</span><span class="sxs-lookup"><span data-stu-id="2b2de-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="2b2de-108">たとえば、あいまいな時刻は常にタイム ゾーンの標準時刻で表されると想定できます。</span><span class="sxs-lookup"><span data-stu-id="2b2de-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

- <span data-ttu-id="2b2de-109">あいまいな時刻が、ユーザーによって入力されたデータ項目である場合は、あいまいさの解決をユーザーに任せることができます。</span><span class="sxs-lookup"><span data-stu-id="2b2de-109">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="2b2de-110">このトピックでは、タイムゾーンの標準時刻を表すと想定して、あいまいな時刻を解決する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2b2de-110">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="2b2de-111">あいまいな時刻をタイム ゾーンの標準時刻にマップするには</span><span class="sxs-lookup"><span data-stu-id="2b2de-111">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="2b2de-112">メソッドを呼び出して <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> 、時刻があいまいであるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="2b2de-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="2b2de-113">時刻があいまいな場合は、タイム <xref:System.TimeSpan> ゾーンのプロパティによって返されたオブジェクトから時刻を減算し <xref:System.TimeZoneInfo.BaseUtcOffset%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="2b2de-113">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="2b2de-114">`static`( `Shared` Visual Basic .net で) メソッドを呼び出して、 <xref:System.DateTime.SpecifyKind%2A> UTC の日付と時刻の値の <xref:System.DateTime.Kind%2A> プロパティをに設定し <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="2b2de-114">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="2b2de-115">例</span><span class="sxs-lookup"><span data-stu-id="2b2de-115">Example</span></span>

<span data-ttu-id="2b2de-116">次の例は、ローカルタイムゾーンの標準時刻を表すと想定して、あいまいな時刻を UTC に変換する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2b2de-116">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="2b2de-117">この例は、渡された `ResolveAmbiguousTime` 値があいまいであるかどうかを判断するという名前のメソッドで構成されてい <xref:System.DateTime> ます。</span><span class="sxs-lookup"><span data-stu-id="2b2de-117">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="2b2de-118">値があいまいな場合、メソッドは対応する <xref:System.DateTime> UTC 時刻を表す値を返します。</span><span class="sxs-lookup"><span data-stu-id="2b2de-118">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="2b2de-119">メソッドは、ローカルタイムゾーンのプロパティの値をローカル時刻から減算することによって、この変換を処理し <xref:System.TimeZoneInfo.BaseUtcOffset%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="2b2de-119">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="2b2de-120">通常、あいまいな時刻は、メソッドを呼び出して、 <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> <xref:System.TimeSpan> あいまいな時刻の UTC オフセットを含むオブジェクトの配列を取得することによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="2b2de-120">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="2b2de-121">しかし、この例は、あいまいな時刻は常にタイム ゾーンの標準時刻にマップされるという想定に基づいています。</span><span class="sxs-lookup"><span data-stu-id="2b2de-121">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="2b2de-122">プロパティは、 <xref:System.TimeZoneInfo.BaseUtcOffset%2A> UTC とタイムゾーンの標準時刻の間のオフセットを返します。</span><span class="sxs-lookup"><span data-stu-id="2b2de-122">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="2b2de-123">この例では、ローカルタイムゾーンへのすべての参照は、プロパティを使用して行われ <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ます。ローカルタイムゾーンは、オブジェクト変数に割り当てられることはありません。</span><span class="sxs-lookup"><span data-stu-id="2b2de-123">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="2b2de-124">メソッドを呼び出すと、 <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> ローカルタイムゾーンが割り当てられているオブジェクトが無効になるため、この方法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2b2de-124">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="2b2de-125">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="2b2de-125">Compiling the code</span></span>

<span data-ttu-id="2b2de-126">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2b2de-126">This example requires:</span></span>

- <span data-ttu-id="2b2de-127"><xref:System> `using` ステートメント (C# コードでは必須) を使用して名前空間をインポートする。</span><span class="sxs-lookup"><span data-stu-id="2b2de-127">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b2de-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b2de-128">See also</span></span>

- [<span data-ttu-id="2b2de-129">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="2b2de-129">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="2b2de-130">方法: ユーザーがあいまいな時刻を解決できるようにする</span><span class="sxs-lookup"><span data-stu-id="2b2de-130">How to: Let users resolve ambiguous times</span></span>](let-users-resolve-ambiguous-times.md)
