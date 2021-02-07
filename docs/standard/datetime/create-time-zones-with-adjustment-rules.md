---
description: '詳細については、「方法: 調整規則のあるタイムゾーンを作成する」を参照してください。'
title: '方法: 調整規則のあるタイム ゾーンを作成する'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], creating
- time zones [.NET], and adjustment rules
- adjustment rule [.NET]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
ms.openlocfilehash: d581d01d9f9386adf99079f4f8f8e09585b06848
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702770"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a><span data-ttu-id="464e7-103">方法: 調整規則のあるタイム ゾーンを作成する</span><span class="sxs-lookup"><span data-stu-id="464e7-103">How to: Create time zones with adjustment rules</span></span>

<span data-ttu-id="464e7-104">アプリケーションで必要とされる正確なタイムゾーン情報は、次のような理由で特定のシステムに存在しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="464e7-104">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

- <span data-ttu-id="464e7-105">タイムゾーンがローカルシステムのレジストリに定義されていません。</span><span class="sxs-lookup"><span data-stu-id="464e7-105">The time zone has never been defined in the local system's registry.</span></span>

- <span data-ttu-id="464e7-106">タイムゾーンに関するデータは、レジストリから変更または削除されています。</span><span class="sxs-lookup"><span data-stu-id="464e7-106">Data about the time zone has been modified or removed from the registry.</span></span>

- <span data-ttu-id="464e7-107">タイムゾーンには、特定の履歴期間のタイムゾーン調整に関する正確な情報がありません。</span><span class="sxs-lookup"><span data-stu-id="464e7-107">The time zone does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="464e7-108">このような場合は、メソッドを呼び出し <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> て、アプリケーションで必要とされるタイムゾーンを定義できます。</span><span class="sxs-lookup"><span data-stu-id="464e7-108">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="464e7-109">このメソッドのオーバーロードを使用して、調整規則の有無に関係なくタイムゾーンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="464e7-109">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="464e7-110">タイムゾーンで夏時間がサポートされている場合は、固定調整規則または浮動調整規則のいずれかを使用して調整を定義できます。</span><span class="sxs-lookup"><span data-stu-id="464e7-110">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="464e7-111">(これらの用語の定義については、「タイムゾーンの [概要](time-zone-overview.md)」の「タイムゾーンの用語」セクションを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="464e7-111">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="464e7-112">メソッドを呼び出すことによって作成されたカスタムタイムゾーン <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> は、レジストリには追加されません。</span><span class="sxs-lookup"><span data-stu-id="464e7-112">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="464e7-113">代わりに、メソッド呼び出しによって返されるオブジェクト参照を使用してのみアクセスでき <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="464e7-113">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="464e7-114">このトピックでは、調整規則を使用してタイムゾーンを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="464e7-114">This topic shows how to create a time zone with adjustment rules.</span></span> <span data-ttu-id="464e7-115">夏時間調整規則をサポートしていないタイムゾーンを作成するには、「 [方法: 調整規則のないタイムゾーンを作成](create-time-zones-without-adjustment-rules.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="464e7-115">To create a time zone that does not support daylight saving time adjustment rules, see [How to: Create Time Zones Without Adjustment Rules](create-time-zones-without-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a><span data-ttu-id="464e7-116">浮動調整規則を使用してタイムゾーンを作成するには</span><span class="sxs-lookup"><span data-stu-id="464e7-116">To create a time zone with floating adjustment rules</span></span>

1. <span data-ttu-id="464e7-117">それぞれの調整について (つまり、特定の期間にわたって標準時間外に移行するたびに)、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="464e7-117">For each adjustment (that is, for each transition away from and back to standard time over a particular time interval), do the following:</span></span>

    1. <span data-ttu-id="464e7-118">タイムゾーン調整の開始遷移時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="464e7-118">Define the starting transition time for the time zone adjustment.</span></span>

       <span data-ttu-id="464e7-119">メソッドを呼び出して、遷移の時刻を定義する値、遷移の月を定義する <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> <xref:System.DateTime> 整数値、遷移が発生する曜日を定義する整数値、および遷移が発生する曜日を定義する値を渡す必要があります。この場合、メソッドを呼び出す必要があり <xref:System.DayOfWeek> ます。</span><span class="sxs-lookup"><span data-stu-id="464e7-119">You must call the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method and pass it a <xref:System.DateTime> value that defines the time of the transition, an integer value that defines the month of the transition, an integer value that defines the week on which the transition occurs, and a <xref:System.DayOfWeek> value that defines the day of the week on which the transition occurs.</span></span> <span data-ttu-id="464e7-120">このメソッド呼び出しは、オブジェクトをインスタンス化 <xref:System.TimeZoneInfo.TransitionTime> します。</span><span class="sxs-lookup"><span data-stu-id="464e7-120">This method call instantiates a <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    2. <span data-ttu-id="464e7-121">タイムゾーン調整の終了遷移時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="464e7-121">Define the ending transition time for the time zone adjustment.</span></span> <span data-ttu-id="464e7-122">これには、メソッドの別の呼び出しが必要です <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="464e7-122">This requires another call to the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="464e7-123">このメソッド呼び出しは、2番目のオブジェクトをインスタンス化 <xref:System.TimeZoneInfo.TransitionTime> します。</span><span class="sxs-lookup"><span data-stu-id="464e7-123">This method call instantiates a second <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    3. <span data-ttu-id="464e7-124">メソッドを呼び出し、 <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> 調整の有効な開始日と終了日、 <xref:System.TimeSpan> 遷移の時間を定義するオブジェクト、および夏時間との <xref:System.TimeZoneInfo.TransitionTime> 間の切り替えが発生するタイミングを定義する2つのオブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="464e7-124">Call the <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> method and pass it the effective start and end dates of the adjustment, a <xref:System.TimeSpan> object that defines the amount of time in the transition, and the two <xref:System.TimeZoneInfo.TransitionTime> objects that define when the transitions to and from daylight saving time occur.</span></span> <span data-ttu-id="464e7-125">このメソッド呼び出しは、オブジェクトをインスタンス化 <xref:System.TimeZoneInfo.AdjustmentRule> します。</span><span class="sxs-lookup"><span data-stu-id="464e7-125">This method call instantiates a <xref:System.TimeZoneInfo.AdjustmentRule> object.</span></span>

    4. <span data-ttu-id="464e7-126">オブジェクトを <xref:System.TimeZoneInfo.AdjustmentRule> オブジェクトの配列に割り当て <xref:System.TimeZoneInfo.AdjustmentRule> ます。</span><span class="sxs-lookup"><span data-stu-id="464e7-126">Assign the <xref:System.TimeZoneInfo.AdjustmentRule> object to an array of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span>

2. <span data-ttu-id="464e7-127">タイムゾーンの表示名を定義します。</span><span class="sxs-lookup"><span data-stu-id="464e7-127">Define the time zone's display name.</span></span> <span data-ttu-id="464e7-128">表示名は、標準形式に準拠しています。この形式では、世界協定時刻 (UTC) からのタイムゾーンのオフセットがかっこで囲まれ、タイムゾーンの1つまたは複数の都市を識別する文字列、またはタイムゾーンの1つ以上の国または地域が続きます。</span><span class="sxs-lookup"><span data-stu-id="464e7-128">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

3. <span data-ttu-id="464e7-129">タイムゾーンの標準時刻の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="464e7-129">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="464e7-130">通常、この文字列はタイムゾーンの識別子としても使用されます。</span><span class="sxs-lookup"><span data-stu-id="464e7-130">Typically, this string is also used as the time zone's identifier.</span></span>

4. <span data-ttu-id="464e7-131">タイムゾーンの夏時間の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="464e7-131">Define the name of the time zone's daylight time.</span></span>

5. <span data-ttu-id="464e7-132">タイムゾーンの標準名とは異なる識別子を使用する場合は、タイムゾーン識別子を定義します。</span><span class="sxs-lookup"><span data-stu-id="464e7-132">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

6. <span data-ttu-id="464e7-133"><xref:System.TimeSpan>タイムゾーンの UTC からのオフセットを定義するオブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="464e7-133">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="464e7-134">時刻が UTC より遅いタイムゾーンには、正のオフセットがあります。</span><span class="sxs-lookup"><span data-stu-id="464e7-134">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="464e7-135">時刻が UTC より前のタイムゾーンでは、負のオフセットが使用されます。</span><span class="sxs-lookup"><span data-stu-id="464e7-135">Time zones with times that are earlier than UTC have a negative offset.</span></span>

7. <span data-ttu-id="464e7-136">メソッドを呼び出して <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> 、新しいタイムゾーンをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="464e7-136">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="464e7-137">例</span><span class="sxs-lookup"><span data-stu-id="464e7-137">Example</span></span>

<span data-ttu-id="464e7-138">次の例では、1918から現在のまでのさまざまな時間間隔の調整規則を含む米国の中部標準時のタイムゾーンを定義します。</span><span class="sxs-lookup"><span data-stu-id="464e7-138">The following example defines a Central Standard Time zone for the United States that includes adjustment rules for a variety of time intervals from 1918 to the present.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

<span data-ttu-id="464e7-139">この例で作成したタイムゾーンには、複数の調整規則があります。</span><span class="sxs-lookup"><span data-stu-id="464e7-139">The time zone created in this example has multiple adjustment rules.</span></span> <span data-ttu-id="464e7-140">調整規則の有効な開始日と終了日が、別の調整規則の日付と重複しないように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="464e7-140">Care must be taken to ensure that the effective start and end dates of any adjustment rule do not overlap with the dates of another adjustment rule.</span></span> <span data-ttu-id="464e7-141">重複がある場合は、 <xref:System.InvalidTimeZoneException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="464e7-141">If there is an overlap, an <xref:System.InvalidTimeZoneException> is thrown.</span></span>

<span data-ttu-id="464e7-142">浮動調整規則では、値5がメソッドのパラメーターに渡され、 `week` <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> 特定の月の最後の週に移行が行われることを示します。</span><span class="sxs-lookup"><span data-stu-id="464e7-142">For floating adjustment rules, the value 5 is passed to the `week` parameter of the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method to indicate that the transition occurs on the last week of a particular month.</span></span>

<span data-ttu-id="464e7-143"><xref:System.TimeZoneInfo.AdjustmentRule>メソッド呼び出しで使用するオブジェクトの配列を作成する <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> 場合、コードは、タイムゾーンに対して作成される調整の数に必要なサイズに配列を初期化できます。</span><span class="sxs-lookup"><span data-stu-id="464e7-143">In creating the array of <xref:System.TimeZoneInfo.AdjustmentRule> objects to use in the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method call, the code could initialize the array to the size required by the number of adjustments to be created for the time zone.</span></span> <span data-ttu-id="464e7-144">代わりに、このコード例ではメソッドを呼び出して、 <xref:System.Collections.Generic.List%601.Add%2A> オブジェクトのジェネリックコレクションに各調整規則を追加し <xref:System.Collections.Generic.List%601> <xref:System.TimeZoneInfo.AdjustmentRule> ます。</span><span class="sxs-lookup"><span data-stu-id="464e7-144">Instead, this code example calls the <xref:System.Collections.Generic.List%601.Add%2A> method to add each adjustment rule to a generic <xref:System.Collections.Generic.List%601> collection of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span> <span data-ttu-id="464e7-145">次に、メソッドを呼び出して、 <xref:System.Collections.Generic.List%601.CopyTo%2A> このコレクションのメンバーを配列にコピーします。</span><span class="sxs-lookup"><span data-stu-id="464e7-145">The code then calls the <xref:System.Collections.Generic.List%601.CopyTo%2A> method to copy the members of this collection to the array.</span></span>

<span data-ttu-id="464e7-146">また、この例では、メソッドを使用して、 <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> 固定日付の調整を定義しています。</span><span class="sxs-lookup"><span data-stu-id="464e7-146">The example also uses the <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> method to define fixed-date adjustments.</span></span> <span data-ttu-id="464e7-147">これは、メソッドの呼び出しに似ていますが、 <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> 移行パラメーターの時刻、月、および日のみが必要です。</span><span class="sxs-lookup"><span data-stu-id="464e7-147">This is similar to calling the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method, except that it requires only the time, month, and day of the transition parameters.</span></span>

<span data-ttu-id="464e7-148">この例は、次のようなコードを使用してテストできます。</span><span class="sxs-lookup"><span data-stu-id="464e7-148">The example can be tested using code such as the following:</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a><span data-ttu-id="464e7-149">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="464e7-149">Compiling the code</span></span>

<span data-ttu-id="464e7-150">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="464e7-150">This example requires:</span></span>

- <span data-ttu-id="464e7-151">次の名前空間がインポートされます。</span><span class="sxs-lookup"><span data-stu-id="464e7-151">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="464e7-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="464e7-152">See also</span></span>

- [<span data-ttu-id="464e7-153">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="464e7-153">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="464e7-154">タイム ゾーンの概要</span><span class="sxs-lookup"><span data-stu-id="464e7-154">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="464e7-155">方法: 調整規則のないタイムゾーンを作成する</span><span class="sxs-lookup"><span data-stu-id="464e7-155">How to: Create time zones without adjustment rules</span></span>](create-time-zones-without-adjustment-rules.md)
