---
description: '詳細については、「方法: 調整規則のないタイムゾーンを作成する」を参照してください。'
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
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702731"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="0259d-103">方法: 調整規則のないタイム ゾーンを作成する</span><span class="sxs-lookup"><span data-stu-id="0259d-103">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="0259d-104">アプリケーションで必要とされる正確なタイムゾーン情報は、次のような理由で特定のシステムに存在しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="0259d-104">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

- <span data-ttu-id="0259d-105">タイムゾーンがローカルシステムのレジストリに定義されていません。</span><span class="sxs-lookup"><span data-stu-id="0259d-105">The time zone has never been defined in the local system's registry.</span></span>

- <span data-ttu-id="0259d-106">タイムゾーンに関するデータは、レジストリから変更または削除されています。</span><span class="sxs-lookup"><span data-stu-id="0259d-106">Data about the time zone has been modified or removed from the registry.</span></span>

- <span data-ttu-id="0259d-107">タイムゾーンは存在しますが、特定の履歴期間のタイムゾーン調整に関する正確な情報がありません。</span><span class="sxs-lookup"><span data-stu-id="0259d-107">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="0259d-108">このような場合は、メソッドを呼び出し <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> て、アプリケーションで必要とされるタイムゾーンを定義できます。</span><span class="sxs-lookup"><span data-stu-id="0259d-108">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="0259d-109">このメソッドのオーバーロードを使用して、調整規則の有無に関係なくタイムゾーンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0259d-109">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="0259d-110">タイムゾーンで夏時間がサポートされている場合は、固定調整規則または浮動調整規則のいずれかを使用して調整を定義できます。</span><span class="sxs-lookup"><span data-stu-id="0259d-110">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="0259d-111">(これらの用語の定義については、「タイムゾーンの [概要](time-zone-overview.md)」の「タイムゾーンの用語」セクションを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="0259d-111">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0259d-112">メソッドを呼び出すことによって作成されたカスタムタイムゾーン <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> は、レジストリには追加されません。</span><span class="sxs-lookup"><span data-stu-id="0259d-112">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="0259d-113">代わりに、メソッド呼び出しによって返されるオブジェクト参照を使用してのみアクセスでき <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="0259d-113">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="0259d-114">このトピックでは、調整規則を使用せずにタイムゾーンを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0259d-114">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="0259d-115">夏時間調整規則をサポートするタイムゾーンを作成するには、「 [方法: 調整規則を使用してタイムゾーンを作成](create-time-zones-with-adjustment-rules.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0259d-115">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="0259d-116">調整規則のないタイムゾーンを作成するには</span><span class="sxs-lookup"><span data-stu-id="0259d-116">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="0259d-117">タイムゾーンの表示名を定義します。</span><span class="sxs-lookup"><span data-stu-id="0259d-117">Define the time zone's display name.</span></span>

   <span data-ttu-id="0259d-118">表示名は、標準形式に準拠しています。この形式では、世界協定時刻 (UTC) からのタイムゾーンのオフセットがかっこで囲まれ、タイムゾーンの1つまたは複数の都市を識別する文字列、またはタイムゾーンの1つ以上の国または地域が続きます。</span><span class="sxs-lookup"><span data-stu-id="0259d-118">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="0259d-119">タイムゾーンの標準時刻の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="0259d-119">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="0259d-120">通常、この文字列はタイムゾーンの識別子としても使用されます。</span><span class="sxs-lookup"><span data-stu-id="0259d-120">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="0259d-121">タイムゾーンの標準名とは異なる識別子を使用する場合は、タイムゾーン識別子を定義します。</span><span class="sxs-lookup"><span data-stu-id="0259d-121">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="0259d-122"><xref:System.TimeSpan>タイムゾーンの UTC からのオフセットを定義するオブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="0259d-122">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="0259d-123">時刻が UTC より遅いタイムゾーンには、正のオフセットがあります。</span><span class="sxs-lookup"><span data-stu-id="0259d-123">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="0259d-124">時刻が UTC より前のタイムゾーンでは、負のオフセットが使用されます。</span><span class="sxs-lookup"><span data-stu-id="0259d-124">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="0259d-125">メソッドを呼び出して <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> 、新しいタイムゾーンをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="0259d-125">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="0259d-126">例</span><span class="sxs-lookup"><span data-stu-id="0259d-126">Example</span></span>

<span data-ttu-id="0259d-127">次の例では、調整規則のない Mawson、南極のカスタムタイムゾーンを定義します。</span><span class="sxs-lookup"><span data-stu-id="0259d-127">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="0259d-128">プロパティに割り当てられた文字列は、 <xref:System.TimeZoneInfo.DisplayName%2A> 標準形式に従います。この形式では、UTC からのタイムゾーンのオフセットの後にタイムゾーンのわかりやすい説明が続きます。</span><span class="sxs-lookup"><span data-stu-id="0259d-128">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="0259d-129">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="0259d-129">Compiling the code</span></span>

<span data-ttu-id="0259d-130">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0259d-130">This example requires:</span></span>

- <span data-ttu-id="0259d-131">次の名前空間がインポートされます。</span><span class="sxs-lookup"><span data-stu-id="0259d-131">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="0259d-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="0259d-132">See also</span></span>

- [<span data-ttu-id="0259d-133">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="0259d-133">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="0259d-134">タイム ゾーンの概要</span><span class="sxs-lookup"><span data-stu-id="0259d-134">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="0259d-135">方法: 調整規則のあるタイムゾーンを作成する</span><span class="sxs-lookup"><span data-stu-id="0259d-135">How to: Create time zones with adjustment rules</span></span>](create-time-zones-with-adjustment-rules.md)
