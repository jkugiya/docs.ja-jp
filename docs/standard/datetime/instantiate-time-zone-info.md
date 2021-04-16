---
description: '詳細情報: 方法: TimeZoneInfo オブジェクトをインスタンス化する'
title: '方法: TimeZoneInfo オブジェクトをインスタンス化する'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
ms.openlocfilehash: d063833aa60142bf6f942a836c7f89777d9073a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702614"
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="dc0c0-103">方法: TimeZoneInfo オブジェクトをインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="dc0c0-103">How to: Instantiate a TimeZoneInfo object</span></span>

<span data-ttu-id="dc0c0-104"><xref:System.TimeZoneInfo> オブジェクトをインスタンス化する最も一般的な方法は、レジストリからオブジェクトに関する情報を取得することです。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-104">The most common way to instantiate a <xref:System.TimeZoneInfo> object is to retrieve information about it from the registry.</span></span> <span data-ttu-id="dc0c0-105">このトピックでは、ローカル システムのレジストリから <xref:System.TimeZoneInfo> オブジェクトをインスタンス化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-105">This topic discusses how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

### <a name="to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="dc0c0-106">TimeZoneInfo オブジェクトをインスタンス化するには</span><span class="sxs-lookup"><span data-stu-id="dc0c0-106">To instantiate a TimeZoneInfo object</span></span>

1. <span data-ttu-id="dc0c0-107"><xref:System.TimeZoneInfo> オブジェクトを宣言します。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-107">Declare a <xref:System.TimeZoneInfo> object.</span></span>

2. <span data-ttu-id="dc0c0-108">`static` (Visual Basic では`Shared` ) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-108">Call the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> method.</span></span>

3. <span data-ttu-id="dc0c0-109">メソッドによってスローされる例外 (特に、タイム ゾーンがレジストリで定義されていない場合にスローされる <xref:System.TimeZoneNotFoundException> ) を処理します。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-109">Handle any exceptions thrown by the method, particularly the <xref:System.TimeZoneNotFoundException> that is thrown if the time zone is not defined in the registry.</span></span>

## <a name="example"></a><span data-ttu-id="dc0c0-110">例</span><span class="sxs-lookup"><span data-stu-id="dc0c0-110">Example</span></span>

<span data-ttu-id="dc0c0-111">次のコードでは、東部標準時のタイム ゾーンを表す <xref:System.TimeZoneInfo> オブジェクトを取得し、現地時刻に対応する東部標準時の時刻を表示します。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-111">The following code retrieves a <xref:System.TimeZoneInfo> object that represents the Eastern Standard Time zone and displays the Eastern Standard time that corresponds to the local time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<span data-ttu-id="dc0c0-112"><xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> メソッドの唯一のパラメーターは、取得するタイム ゾーンの識別子です。これは、オブジェクトの <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> プロパティに対応します。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-112">The <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> method's single parameter is the identifier of the time zone that you want to retrieve, which corresponds to the object's <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="dc0c0-113">タイム ゾーン ID は、タイム ゾーンを一意に識別するキー フィールドです。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-113">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="dc0c0-114">ほとんどのキーは比較的短いですが、タイム ゾーン ID はいくぶん長めです。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-114">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="dc0c0-115">ほとんどの場合、ID の値は、タイム ゾーンの標準時刻の名前を表すために使用される <xref:System.TimeZoneInfo.StandardName%2A> オブジェクトの <xref:System.TimeZoneInfo> プロパティに対応します。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-115">In most cases, its value corresponds to the <xref:System.TimeZoneInfo.StandardName%2A> property of a <xref:System.TimeZoneInfo> object, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="dc0c0-116">ただし、例外もあります。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-116">However, there are exceptions.</span></span> <span data-ttu-id="dc0c0-117">有効な識別子を確実に指定する最良の方法は、システムで使用できるタイム ゾーンを列挙し、対応するタイム ゾーン識別子を記録しておくことです。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-117">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note the identifiers of the time zones present on them.</span></span> <span data-ttu-id="dc0c0-118">この具体例については、「 [How to: Enumerate time zones present on a computer](enumerate-time-zones.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-118">For an illustration, see [How to: Enumerate time zones present on a computer](enumerate-time-zones.md).</span></span> <span data-ttu-id="dc0c0-119">[Finding the time zones defined on a local system](finding-the-time-zones-on-local-system.md) トピックにも、選択したタイム ゾーン識別子の一覧があります。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-119">The [Finding the time zones defined on a local system](finding-the-time-zones-on-local-system.md) topic also contains a list of selected time zone identifiers.</span></span>

<span data-ttu-id="dc0c0-120">タイム ゾーンが見つかると、メソッドは <xref:System.TimeZoneInfo> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-120">If the time zone is found, the method returns its <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="dc0c0-121">タイム ゾーンが見つからない場合、メソッドから <xref:System.TimeZoneNotFoundException>がスローされます。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-121">If the time zone is not found, the method throws a <xref:System.TimeZoneNotFoundException>.</span></span> <span data-ttu-id="dc0c0-122">タイム ゾーンが見つかっても、そのデータが破損しているか不完全な場合には、メソッドから <xref:System.InvalidTimeZoneException>がスローされます。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-122">If the time zone is found but its data is corrupted or incomplete, the method throws an <xref:System.InvalidTimeZoneException>.</span></span>

<span data-ttu-id="dc0c0-123">アプリケーションが依存するタイム ゾーンが必ず存在していなければならない場合は、最初に <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> メソッドを呼び出して、レジストリからタイム ゾーンの情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-123">If your application relies on a time zone that must be present, you should first call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method to retrieve the time zone information from the registry.</span></span> <span data-ttu-id="dc0c0-124">メソッドの呼び出しが失敗した場合は、例外ハンドラーで、タイム ゾーンの新しいインスタンスを作成するか、シリアル化された <xref:System.TimeZoneInfo> オブジェクトを逆シリアル化してインスタンスを作成し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-124">If the method call fails, your exception handler should then either create a new instance of the time zone or re-create it by deserializing a serialized <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="dc0c0-125">例については、「[方法: 埋め込みリソースからタイム ゾーンを復元する](restore-time-zones-from-an-embedded-resource.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dc0c0-125">See [How to: Restore time zones from an embedded resource](restore-time-zones-from-an-embedded-resource.md) for an example.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc0c0-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc0c0-126">See also</span></span>

- [<span data-ttu-id="dc0c0-127">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="dc0c0-127">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="dc0c0-128">ローカル システムで定義されているタイム ゾーンの検索</span><span class="sxs-lookup"><span data-stu-id="dc0c0-128">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="dc0c0-129">方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする</span><span class="sxs-lookup"><span data-stu-id="dc0c0-129">How to: Access the predefined UTC and local time zone objects</span></span>](access-utc-and-local.md)
