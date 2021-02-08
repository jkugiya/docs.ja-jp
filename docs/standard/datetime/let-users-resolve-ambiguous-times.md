---
description: '詳細については、「方法: ユーザーがあいまいな時刻を解決できるようにする」を参照してください。'
title: '方法: ユーザーがあいまいな時刻を解決できるようにする'
ms.date: 04/10/2017
helpviewer_keywords:
- time zones [.NET], ambiguous time
- ambiguous time [.NET]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: a64d20080ed021af273a2d114c7558615b8b04e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782482"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="17385-103">方法: ユーザーがあいまいな時刻を解決できるようにする</span><span class="sxs-lookup"><span data-stu-id="17385-103">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="17385-104">あいまいな時刻は複数の世界協定時刻 (UTC) にマップされる時刻です。</span><span class="sxs-lookup"><span data-stu-id="17385-104">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="17385-105">あいまいな時刻は、あるタイム ゾーンの夏時間から標準時間に移行する際など、時計の時刻を前に戻すときに発生します。</span><span class="sxs-lookup"><span data-stu-id="17385-105">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="17385-106">あいまいな時刻を処理する場合は、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="17385-106">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="17385-107">あいまいな時刻が、ユーザーによって入力されたデータ項目である場合は、あいまいさの解決をユーザーに任せることができます。</span><span class="sxs-lookup"><span data-stu-id="17385-107">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

- <span data-ttu-id="17385-108">時刻が UTC にどのようにマップされるかを想定します。</span><span class="sxs-lookup"><span data-stu-id="17385-108">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="17385-109">たとえば、あいまいな時刻は常にタイム ゾーンの標準時刻で表されると想定できます。</span><span class="sxs-lookup"><span data-stu-id="17385-109">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="17385-110">このトピックでは、ユーザーがあいまいな時刻を解決できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="17385-110">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="17385-111">ユーザーにあいまいな時刻を解決させるには</span><span class="sxs-lookup"><span data-stu-id="17385-111">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="17385-112">ユーザーによって入力された日付と時刻を取得します。</span><span class="sxs-lookup"><span data-stu-id="17385-112">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="17385-113">メソッドを呼び出して <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> 、時刻があいまいであるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="17385-113">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="17385-114">時刻があいまいな場合は、メソッドを呼び出して <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> オブジェクトの配列を取得し <xref:System.TimeSpan> ます。</span><span class="sxs-lookup"><span data-stu-id="17385-114">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="17385-115">配列の各要素には、あいまいな時刻をマップできる UTC オフセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="17385-115">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="17385-116">ユーザーに目的のオフセットを選択させます。</span><span class="sxs-lookup"><span data-stu-id="17385-116">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="17385-117">ローカル時刻からユーザーによって選択されたオフセットを減算して、UTC の日時を取得します。</span><span class="sxs-lookup"><span data-stu-id="17385-117">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="17385-118">`static`( `Shared` Visual Basic .net で) メソッドを呼び出して、 <xref:System.DateTime.SpecifyKind%2A> UTC の日付と時刻の値の <xref:System.DateTime.Kind%2A> プロパティをに設定し <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="17385-118">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="17385-119">例</span><span class="sxs-lookup"><span data-stu-id="17385-119">Example</span></span>

<span data-ttu-id="17385-120">次の例では、ユーザーに日付と時刻を入力するように求め、それがあいまいである場合は、ユーザーにあいまいな時刻をマップする UTC 時刻を選択させています。</span><span class="sxs-lookup"><span data-stu-id="17385-120">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="17385-121">この例のコードの中核となるのは、オブジェクトの配列を使用して、 <xref:System.TimeSpan> UTC からのあいまいな時刻のオフセットを示すことです。</span><span class="sxs-lookup"><span data-stu-id="17385-121">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="17385-122">ただし、これらのオフセットは、ユーザーにとって意味がない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="17385-122">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="17385-123">オフセットの意味を明確にするには、コードで、オフセットがローカル タイム ゾーンの標準時刻を表すか、または夏時間を表すかに注意します。</span><span class="sxs-lookup"><span data-stu-id="17385-123">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="17385-124">このコードでは、オフセットをプロパティの値と比較することによって、標準の時間と夏時間を判断し <xref:System.TimeZoneInfo.BaseUtcOffset%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="17385-124">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="17385-125">このプロパティは、UTC とタイム ゾーンの標準時間の差を示します。</span><span class="sxs-lookup"><span data-stu-id="17385-125">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="17385-126">この例では、ローカルタイムゾーンへのすべての参照は、プロパティを使用して行われ <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ます。ローカルタイムゾーンは、オブジェクト変数に割り当てられることはありません。</span><span class="sxs-lookup"><span data-stu-id="17385-126">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="17385-127">メソッドを呼び出すと、 <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> ローカルタイムゾーンが割り当てられているオブジェクトが無効になるため、この方法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="17385-127">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="17385-128">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="17385-128">Compiling the code</span></span>

<span data-ttu-id="17385-129">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="17385-129">This example requires:</span></span>

- <span data-ttu-id="17385-130"><xref:System> `using` ステートメント (C# コードでは必須) を使用して名前空間をインポートする。</span><span class="sxs-lookup"><span data-stu-id="17385-130">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="17385-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="17385-131">See also</span></span>

- [<span data-ttu-id="17385-132">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="17385-132">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="17385-133">方法: あいまいな時刻を解決する</span><span class="sxs-lookup"><span data-stu-id="17385-133">How to: Resolve ambiguous times</span></span>](resolve-ambiguous-times.md)
