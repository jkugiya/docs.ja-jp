---
description: '詳細情報: 方法: 調整規則のあるタイム ゾーンを作成する'
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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702770"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a><span data-ttu-id="6c21f-103">方法: 調整規則のあるタイム ゾーンを作成する</span><span class="sxs-lookup"><span data-stu-id="6c21f-103">How to: Create time zones with adjustment rules</span></span>

<span data-ttu-id="6c21f-104">アプリケーションで必要とされる正確なタイム ゾーン情報が、いくつかの理由で特定のシステムに存在しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="6c21f-104">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

- <span data-ttu-id="6c21f-105">タイム ゾーンがローカル システムのレジストリに定義されていない。</span><span class="sxs-lookup"><span data-stu-id="6c21f-105">The time zone has never been defined in the local system's registry.</span></span>

- <span data-ttu-id="6c21f-106">レジストリにあるタイム ゾーンに関するデータが変更または削除された。</span><span class="sxs-lookup"><span data-stu-id="6c21f-106">Data about the time zone has been modified or removed from the registry.</span></span>

- <span data-ttu-id="6c21f-107">タイム ゾーンに、特定の期間のタイム ゾーン調整の履歴に関する正確な情報がない。</span><span class="sxs-lookup"><span data-stu-id="6c21f-107">The time zone does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="6c21f-108">このような場合は、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを呼び出して、アプリケーションで必要とされるタイム ゾーンを定義できます。</span><span class="sxs-lookup"><span data-stu-id="6c21f-108">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="6c21f-109">このメソッドのオーバーロードを使用して、調整規則の有無に関係なくタイム ゾーンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6c21f-109">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="6c21f-110">タイム ゾーンで夏時間がサポートされている場合は、固定または浮動調整規則のいずれかを使用して調整を定義できます</span><span class="sxs-lookup"><span data-stu-id="6c21f-110">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="6c21f-111">(これらの用語の定義については、「[タイム ゾーンの概要](time-zone-overview.md)」の「タイム ゾーンの用語」セクションをご覧ください)。</span><span class="sxs-lookup"><span data-stu-id="6c21f-111">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6c21f-112"><xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを呼び出すことによって作成されたカスタム タイム ゾーンは、レジストリには追加されません。</span><span class="sxs-lookup"><span data-stu-id="6c21f-112">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="6c21f-113">代わりに、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッド呼び出しによって返されるオブジェクト参照を通してのみ、これらにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6c21f-113">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="6c21f-114">このトピックでは、調整規則のあるタイム ゾーンを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-114">This topic shows how to create a time zone with adjustment rules.</span></span> <span data-ttu-id="6c21f-115">夏時間調整規則をサポートしないタイム ゾーンを作成するには、「[方法: 調整規則のないタイム ゾーンを作成する](create-time-zones-without-adjustment-rules.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6c21f-115">To create a time zone that does not support daylight saving time adjustment rules, see [How to: Create Time Zones Without Adjustment Rules](create-time-zones-without-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a><span data-ttu-id="6c21f-116">浮動調整規則のあるタイム ゾーンを作成する方法</span><span class="sxs-lookup"><span data-stu-id="6c21f-116">To create a time zone with floating adjustment rules</span></span>

1. <span data-ttu-id="6c21f-117">調整のたびに (つまり、特定の期間にわたって標準時との間で切り替えるたびに)、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-117">For each adjustment (that is, for each transition away from and back to standard time over a particular time interval), do the following:</span></span>

    1. <span data-ttu-id="6c21f-118">タイム ゾーン調整の切り替え開始時刻を定義します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-118">Define the starting transition time for the time zone adjustment.</span></span>

       <span data-ttu-id="6c21f-119"><xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> メソッドを呼び出して、切り替える時刻を定義する <xref:System.DateTime> 値、切り替える月を定義する整数値、切り替えが発生する週を定義する整数値、切り替えが発生する曜日を定義する <xref:System.DayOfWeek> 値を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c21f-119">You must call the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method and pass it a <xref:System.DateTime> value that defines the time of the transition, an integer value that defines the month of the transition, an integer value that defines the week on which the transition occurs, and a <xref:System.DayOfWeek> value that defines the day of the week on which the transition occurs.</span></span> <span data-ttu-id="6c21f-120">このメソッドの呼び出しで、<xref:System.TimeZoneInfo.TransitionTime> オブジェクトがインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="6c21f-120">This method call instantiates a <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    2. <span data-ttu-id="6c21f-121">タイム ゾーン調整の切り替え終了時刻を定義します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-121">Define the ending transition time for the time zone adjustment.</span></span> <span data-ttu-id="6c21f-122">このために、もう一度 <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> メソッドを呼び出すことが必要です。</span><span class="sxs-lookup"><span data-stu-id="6c21f-122">This requires another call to the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6c21f-123">このメソッドの呼び出しで、2 番目の <xref:System.TimeZoneInfo.TransitionTime> オブジェクトがインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="6c21f-123">This method call instantiates a second <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    3. <span data-ttu-id="6c21f-124"><xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> メソッドを呼び出し、調整の有効期間の開始および終了日、切り替えにかかる時間を定義する <xref:System.TimeSpan> オブジェクト、夏時間の開始と終了の切り替えが行われるタイミングを定義する 2 つの <xref:System.TimeZoneInfo.TransitionTime> オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-124">Call the <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> method and pass it the effective start and end dates of the adjustment, a <xref:System.TimeSpan> object that defines the amount of time in the transition, and the two <xref:System.TimeZoneInfo.TransitionTime> objects that define when the transitions to and from daylight saving time occur.</span></span> <span data-ttu-id="6c21f-125">このメソッドの呼び出しで、<xref:System.TimeZoneInfo.AdjustmentRule> オブジェクトがインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="6c21f-125">This method call instantiates a <xref:System.TimeZoneInfo.AdjustmentRule> object.</span></span>

    4. <span data-ttu-id="6c21f-126"><xref:System.TimeZoneInfo.AdjustmentRule> オブジェクトを <xref:System.TimeZoneInfo.AdjustmentRule> オブジェクトの配列に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="6c21f-126">Assign the <xref:System.TimeZoneInfo.AdjustmentRule> object to an array of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span>

2. <span data-ttu-id="6c21f-127">タイム ゾーンの表示名を定義します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-127">Define the time zone's display name.</span></span> <span data-ttu-id="6c21f-128">表示名はごく標準的な形式に従います。つまり、協定世界時 (UTC) からタイム ゾーンまでのオフセットをかっこで囲み、その後にタイム ゾーン、タイム ゾーンの 1 つまたは複数の都市、またはタイム ゾーンの 1 つまたは複数の国または地域を識別する文字列を続けます。</span><span class="sxs-lookup"><span data-stu-id="6c21f-128">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

3. <span data-ttu-id="6c21f-129">タイム ゾーンの標準時の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-129">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="6c21f-130">通常、この文字列はタイム ゾーンの識別子としても使用されます。</span><span class="sxs-lookup"><span data-stu-id="6c21f-130">Typically, this string is also used as the time zone's identifier.</span></span>

4. <span data-ttu-id="6c21f-131">タイム ゾーンの夏時間の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-131">Define the name of the time zone's daylight time.</span></span>

5. <span data-ttu-id="6c21f-132">タイム ゾーンの標準名とは異なる識別子を使用する場合は、タイム ゾーンの識別子を定義します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-132">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

6. <span data-ttu-id="6c21f-133">UTC からこのタイム ゾーンまでのオフセットを定義する <xref:System.TimeSpan> オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-133">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="6c21f-134">時刻が UTC より後のタイム ゾーンは正のオフセットになります。</span><span class="sxs-lookup"><span data-stu-id="6c21f-134">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="6c21f-135">時刻が UTC より前のタイム ゾーンは負のオフセットになります。</span><span class="sxs-lookup"><span data-stu-id="6c21f-135">Time zones with times that are earlier than UTC have a negative offset.</span></span>

7. <span data-ttu-id="6c21f-136">新しいタイム ゾーンをインスタンス化するには、<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-136">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="6c21f-137">例</span><span class="sxs-lookup"><span data-stu-id="6c21f-137">Example</span></span>

<span data-ttu-id="6c21f-138">次の例では、1918 年から現在に至るまでのさまざまな時間間隔の調整規則を含む米国の中部標準時のタイム ゾーンを定義します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-138">The following example defines a Central Standard Time zone for the United States that includes adjustment rules for a variety of time intervals from 1918 to the present.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

<span data-ttu-id="6c21f-139">この例で作成されるタイム ゾーンには、複数の調整規則があります。</span><span class="sxs-lookup"><span data-stu-id="6c21f-139">The time zone created in this example has multiple adjustment rules.</span></span> <span data-ttu-id="6c21f-140">調整規則の有効期間の開始および終了日が、別の調整規則の日付と重複しないように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c21f-140">Care must be taken to ensure that the effective start and end dates of any adjustment rule do not overlap with the dates of another adjustment rule.</span></span> <span data-ttu-id="6c21f-141">重複がある場合は、<xref:System.InvalidTimeZoneException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="6c21f-141">If there is an overlap, an <xref:System.InvalidTimeZoneException> is thrown.</span></span>

<span data-ttu-id="6c21f-142">浮動調整規則では、値 5 が <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> メソッドの `week` パラメーターに渡されます。これは、特定の月の最終週に切り替えが発生することを示します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-142">For floating adjustment rules, the value 5 is passed to the `week` parameter of the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method to indicate that the transition occurs on the last week of a particular month.</span></span>

<span data-ttu-id="6c21f-143"><xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> メソッド呼び出しで使用される <xref:System.TimeZoneInfo.AdjustmentRule> オブジェクトの配列を作成する場合、コードはタイム ゾーンに対して作成される調整の数に必要なサイズに配列を初期化できます。</span><span class="sxs-lookup"><span data-stu-id="6c21f-143">In creating the array of <xref:System.TimeZoneInfo.AdjustmentRule> objects to use in the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method call, the code could initialize the array to the size required by the number of adjustments to be created for the time zone.</span></span> <span data-ttu-id="6c21f-144">代わりに、このコード例では <xref:System.Collections.Generic.List%601.Add%2A> メソッドを呼び出して、<xref:System.TimeZoneInfo.AdjustmentRule> オブジェクトのジェネリック <xref:System.Collections.Generic.List%601> コレクションに各調整規則を追加します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-144">Instead, this code example calls the <xref:System.Collections.Generic.List%601.Add%2A> method to add each adjustment rule to a generic <xref:System.Collections.Generic.List%601> collection of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span> <span data-ttu-id="6c21f-145">次に、このコードでは <xref:System.Collections.Generic.List%601.CopyTo%2A> メソッドを呼び出して、このコレクションのメンバーを配列にコピーします。</span><span class="sxs-lookup"><span data-stu-id="6c21f-145">The code then calls the <xref:System.Collections.Generic.List%601.CopyTo%2A> method to copy the members of this collection to the array.</span></span>

<span data-ttu-id="6c21f-146">また、この例では、<xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> メソッドを使用して、固定日付の調整を定義します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-146">The example also uses the <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> method to define fixed-date adjustments.</span></span> <span data-ttu-id="6c21f-147">これは、<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> メソッドの呼び出しに似ていますが、切り替えの時刻、月、日付のパラメーターのみが必要です。</span><span class="sxs-lookup"><span data-stu-id="6c21f-147">This is similar to calling the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method, except that it requires only the time, month, and day of the transition parameters.</span></span>

<span data-ttu-id="6c21f-148">この例は、次のようなコードを使用してテストできます。</span><span class="sxs-lookup"><span data-stu-id="6c21f-148">The example can be tested using code such as the following:</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a><span data-ttu-id="6c21f-149">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="6c21f-149">Compiling the code</span></span>

<span data-ttu-id="6c21f-150">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6c21f-150">This example requires:</span></span>

- <span data-ttu-id="6c21f-151">次の名前空間がインポートされていること。</span><span class="sxs-lookup"><span data-stu-id="6c21f-151">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="6c21f-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c21f-152">See also</span></span>

- [<span data-ttu-id="6c21f-153">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="6c21f-153">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="6c21f-154">タイム ゾーンの概要</span><span class="sxs-lookup"><span data-stu-id="6c21f-154">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="6c21f-155">方法: 調整規則のないタイム ゾーンを作成する</span><span class="sxs-lookup"><span data-stu-id="6c21f-155">How to: Create time zones without adjustment rules</span></span>](create-time-zones-without-adjustment-rules.md)
