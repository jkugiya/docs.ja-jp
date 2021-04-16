---
description: '詳細情報: 方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする'
title: '方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET], retrieving
- time zones [.NET], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
ms.openlocfilehash: 74e3ca601ac0b3a6a684569b0931f8566b5d5d26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702757"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="cb83f-103">方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする</span><span class="sxs-lookup"><span data-stu-id="cb83f-103">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="cb83f-104"><xref:System.TimeZoneInfo> クラスに用意されている <xref:System.TimeZoneInfo.Utc%2A> および <xref:System.TimeZoneInfo.Local%2A> という 2 つのプロパティを使用すると、コードから定義済みのタイム ゾーン オブジェクトにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cb83f-104">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="cb83f-105">このトピックでは、これらのプロパティから返される <xref:System.TimeZoneInfo> オブジェクトにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb83f-105">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="cb83f-106">世界協定時刻 (UTC) の TimeZoneInfo オブジェクトにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="cb83f-106">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="cb83f-107">`static` (Visual Basic では `Shared`) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> プロパティを使用して、協定世界時にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="cb83f-107">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="cb83f-108">プロパティから返された <xref:System.TimeZoneInfo> オブジェクトをオブジェクト変数に割り当てるのではなく、そのまま <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> プロパティを使用して協定世界時にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="cb83f-108">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="cb83f-109">ローカル タイム ゾーンにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="cb83f-109">To access the local time zone</span></span>

1. <span data-ttu-id="cb83f-110">`static` (Visual Basic では `Shared`) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> プロパティを使用して、ローカル システム タイム ゾーンにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="cb83f-110">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="cb83f-111">プロパティから返された <xref:System.TimeZoneInfo> オブジェクトをオブジェクト変数に割り当てるのではなく、そのまま <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> プロパティを使用してローカル タイム ゾーンにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="cb83f-111">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="cb83f-112">例</span><span class="sxs-lookup"><span data-stu-id="cb83f-112">Example</span></span>

<span data-ttu-id="cb83f-113">次のコードでは、<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> および <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> プロパティを使用して、米国およびカナダ東部標準時タイム ゾーンの時刻を変換し、コンソールにタイム ゾーンの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="cb83f-113">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="cb83f-114">ローカル タイム ゾーンにアクセスする場合は、ローカル タイム ゾーンを <xref:System.TimeZoneInfo> オブジェクト変数に割り当てることはせず、常に <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> プロパティをお使いください。</span><span class="sxs-lookup"><span data-stu-id="cb83f-114">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="cb83f-115">同様に、協定世界時にアクセスする場合は、UTC ゾーンを <xref:System.TimeZoneInfo> オブジェクト変数に割り当てることはせず、常に <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> プロパティをお使いください。</span><span class="sxs-lookup"><span data-stu-id="cb83f-115">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="cb83f-116">これにより、<xref:System.TimeZoneInfo> メソッド呼び出しによって <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> オブジェクト変数が無効になるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="cb83f-116">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="cb83f-117">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="cb83f-117">Compiling the code</span></span>

<span data-ttu-id="cb83f-118">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cb83f-118">This example requires:</span></span>

- <span data-ttu-id="cb83f-119">`using` ステートメント (C# コードでは必須) を使用して <xref:System> 名前空間がインポートされること。</span><span class="sxs-lookup"><span data-stu-id="cb83f-119">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="cb83f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb83f-120">See also</span></span>

- [<span data-ttu-id="cb83f-121">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="cb83f-121">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="cb83f-122">ローカル システムで定義されているタイム ゾーンの検索</span><span class="sxs-lookup"><span data-stu-id="cb83f-122">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="cb83f-123">方法: TimeZoneInfo オブジェクトをインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="cb83f-123">How to: Instantiate a TimeZoneInfo object</span></span>](instantiate-time-zone-info.md)
