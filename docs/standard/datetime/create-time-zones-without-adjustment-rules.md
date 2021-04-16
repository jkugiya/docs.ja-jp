---
description: '詳細情報: 方法: 調整規則のないタイム ゾーンを作成する'
title: '方法: 調整規則のないタイム ゾーンを作成する'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], adjustment rule
- time zones [.NET], creating
- adjustment rule [.NET]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
ms.openlocfilehash: c2d1f2d2ea21c53c6a3b41603be4f31ec5442a30
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702731"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="b3085-103">方法: 調整規則のないタイム ゾーンを作成する</span><span class="sxs-lookup"><span data-stu-id="b3085-103">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="b3085-104">アプリケーションで必要とされる正確なタイム ゾーン情報が、いくつかの理由で特定のシステムに存在しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="b3085-104">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

- <span data-ttu-id="b3085-105">タイム ゾーンがローカル システムのレジストリに定義されていない。</span><span class="sxs-lookup"><span data-stu-id="b3085-105">The time zone has never been defined in the local system's registry.</span></span>

- <span data-ttu-id="b3085-106">レジストリにあるタイム ゾーンに関するデータが変更または削除された。</span><span class="sxs-lookup"><span data-stu-id="b3085-106">Data about the time zone has been modified or removed from the registry.</span></span>

- <span data-ttu-id="b3085-107">タイム ゾーンは存在するものの、特定の期間のタイム ゾーン調整の履歴に関する正確な情報がない。</span><span class="sxs-lookup"><span data-stu-id="b3085-107">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="b3085-108">このような場合は、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを呼び出して、アプリケーションで必要とされるタイム ゾーンを定義できます。</span><span class="sxs-lookup"><span data-stu-id="b3085-108">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="b3085-109">このメソッドのオーバーロードを使用して、調整規則の有無に関係なくタイム ゾーンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b3085-109">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="b3085-110">タイム ゾーンで夏時間がサポートされている場合は、固定または浮動調整規則のいずれかを使用して調整を定義できます</span><span class="sxs-lookup"><span data-stu-id="b3085-110">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="b3085-111">(これらの用語の定義については、「[タイム ゾーンの概要](time-zone-overview.md)」の「タイム ゾーンの用語」セクションをご覧ください)。</span><span class="sxs-lookup"><span data-stu-id="b3085-111">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b3085-112"><xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを呼び出すことによって作成されたカスタム タイム ゾーンは、レジストリには追加されません。</span><span class="sxs-lookup"><span data-stu-id="b3085-112">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="b3085-113">代わりに、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッド呼び出しによって返されるオブジェクト参照を通してのみ、これらにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b3085-113">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="b3085-114">このトピックでは、調整規則のないタイム ゾーンを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b3085-114">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="b3085-115">夏時間調整規則をサポートするタイム ゾーンを作成するには、「[方法: 調整規則のあるタイム ゾーンを作成する](create-time-zones-with-adjustment-rules.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b3085-115">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="b3085-116">調整規則のないタイム ゾーンを作成する方法</span><span class="sxs-lookup"><span data-stu-id="b3085-116">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="b3085-117">タイム ゾーンの表示名を定義します。</span><span class="sxs-lookup"><span data-stu-id="b3085-117">Define the time zone's display name.</span></span>

   <span data-ttu-id="b3085-118">表示名はごく標準的な形式に従います。つまり、協定世界時 (UTC) からタイム ゾーンまでのオフセットをかっこで囲み、その後にタイム ゾーン、タイム ゾーンの 1 つまたは複数の都市、またはタイム ゾーンの 1 つまたは複数の国または地域を識別する文字列を続けます。</span><span class="sxs-lookup"><span data-stu-id="b3085-118">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="b3085-119">タイム ゾーンの標準時の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="b3085-119">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="b3085-120">通常、この文字列はタイム ゾーンの識別子としても使用されます。</span><span class="sxs-lookup"><span data-stu-id="b3085-120">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="b3085-121">タイム ゾーンの標準名とは異なる識別子を使用する場合は、タイム ゾーンの識別子を定義します。</span><span class="sxs-lookup"><span data-stu-id="b3085-121">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="b3085-122">UTC からこのタイム ゾーンまでのオフセットを定義する <xref:System.TimeSpan> オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="b3085-122">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="b3085-123">時刻が UTC より後のタイム ゾーンは正のオフセットになります。</span><span class="sxs-lookup"><span data-stu-id="b3085-123">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="b3085-124">時刻が UTC より前のタイム ゾーンは負のオフセットになります。</span><span class="sxs-lookup"><span data-stu-id="b3085-124">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="b3085-125">新しいタイム ゾーンをインスタンス化するには、<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b3085-125">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="b3085-126">例</span><span class="sxs-lookup"><span data-stu-id="b3085-126">Example</span></span>

<span data-ttu-id="b3085-127">次の例では、調整規則のない南極のモーソン基地のカスタム タイム ゾーンを定義します。</span><span class="sxs-lookup"><span data-stu-id="b3085-127">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="b3085-128"><xref:System.TimeZoneInfo.DisplayName%2A> プロパティに割り当てられた文字列は、標準的な形式に従っています。つまり、UTC からタイム ゾーンまでのオフセットの後にタイム ゾーンのわかりやすい説明が続きます。</span><span class="sxs-lookup"><span data-stu-id="b3085-128">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="b3085-129">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b3085-129">Compiling the code</span></span>

<span data-ttu-id="b3085-130">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b3085-130">This example requires:</span></span>

- <span data-ttu-id="b3085-131">次の名前空間がインポートされていること。</span><span class="sxs-lookup"><span data-stu-id="b3085-131">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="b3085-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3085-132">See also</span></span>

- [<span data-ttu-id="b3085-133">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="b3085-133">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="b3085-134">タイム ゾーンの概要</span><span class="sxs-lookup"><span data-stu-id="b3085-134">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="b3085-135">方法: 調整規則のあるタイム ゾーンを作成する</span><span class="sxs-lookup"><span data-stu-id="b3085-135">How to: Create time zones with adjustment rules</span></span>](create-time-zones-with-adjustment-rules.md)
