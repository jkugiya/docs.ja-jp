---
description: '詳細情報: 日付、時刻、およびタイムゾーン'
title: 日付、時刻、およびタイム ゾーン
ms.date: 04/10/2017
helpviewer_keywords:
- time zone objects [.NET]
- date and time data [.NET]
- time zones [.NET]
- times [.NET], time zones
- time [.NET], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
ms.openlocfilehash: d991e43a9ee816885b41ec4c9cc28df644c87957
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702627"
---
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="5fa44-103">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="5fa44-103">Dates, times, and time zones</span></span>

<span data-ttu-id="5fa44-104">.NET は基本的な <xref:System.DateTime> 構造体だけでなく、タイム ゾーンでの作業をサポートする次のクラスも提供しています。</span><span class="sxs-lookup"><span data-stu-id="5fa44-104">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="5fa44-105">システムのローカル タイム ゾーンおよび世界協定時刻 (UTC) ゾーンでの作業を行うには、このクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-105">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.</span></span> <span data-ttu-id="5fa44-106">クラスの機能は、 <xref:System.TimeZone> クラスによって主に置き換えられてい <xref:System.TimeZoneInfo> ます。</span><span class="sxs-lookup"><span data-stu-id="5fa44-106">The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="5fa44-107">このクラスを使用すると、システムに事前に定義されている任意のタイム ゾーンを処理し、新しいタイム ゾーンを作成して、1 つのタイム ゾーンから別のタイム ゾーンに日付/時刻を簡単に変換できます。</span><span class="sxs-lookup"><span data-stu-id="5fa44-107">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="5fa44-108">新規に開発を行う場合は、<xref:System.TimeZoneInfo> クラスではなく、<xref:System.TimeZone> クラスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5fa44-108">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="5fa44-109">UTC からのオフセット (つまり時差) がわかっている日付および時刻で作業を行う場合は、この構造体を使用します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-109">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="5fa44-110"><xref:System.DateTimeOffset> 構造体は、日付および時刻の値と、その時刻の UTC からのオフセットを組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="5fa44-110">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="5fa44-111">UTC との関係により、個々の日付と時刻の値によって具体的な日時が明確に特定されます。</span><span class="sxs-lookup"><span data-stu-id="5fa44-111">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="5fa44-112">これにより、<xref:System.DateTime> の値よりも、<xref:System.DateTimeOffset> の値の方がコンピューター間で移植しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="5fa44-112">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="5fa44-113">ドキュメントのこのセクションでは、タイム ゾーンでの作業を行ったり、あるタイム ゾーンから別のタイム ゾーンに日付と時刻を変換できる、タイム ゾーンに対応したアプリケーションを作成するために必要な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-113">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5fa44-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5fa44-114">In this section</span></span>

<span data-ttu-id="5fa44-115">[タイム ゾーンの概要](time-zone-overview.md) タイム ゾーンに対応したアプリケーションの作成に関連する用語、概念、問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-115">[Time zone overview](time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="5fa44-116">[DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の選択](choosing-between-datetime.md)<xref:System.DateTime> <xref:System.DateTimeOffset> <xref:System.TimeZoneInfo> 日付と時刻のデータを操作するときに、型、型、および型を使用する場合について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-116">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="5fa44-117">[ローカル システムで定義されているタイム ゾーンの検索](finding-the-time-zones-on-local-system.md) ローカル システムで検出されたタイム ゾーンを列挙する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-117">[Finding the time zones defined on a local system](finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="5fa44-118">[方法: コンピューター上に存在するタイム ゾーンを列挙する](enumerate-time-zones.md) コンピューターのレジストリに定義されているタイム ゾーンを列挙して、ユーザーが一覧から事前定義のタイム ゾーンを選択できるようにするための例を提供します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-118">[How to: Enumerate time zones present on a computer](enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="5fa44-119">[方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする](access-utc-and-local.md) 世界協定時刻とローカル タイム ゾーンにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-119">[How to: Access the predefined UTC and local time zone objects](access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="5fa44-120">[方法: TimeZoneInfo オブジェクトをインスタンス化する](instantiate-time-zone-info.md) ローカル システムのレジストリから <xref:System.TimeZoneInfo> オブジェクトをインスタンス化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-120">[How to: Instantiate a TimeZoneInfo object](instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="5fa44-121">[DateTimeOffset オブジェクトのインスタンス化](instantiating-a-datetimeoffset-object.md)<xref:System.DateTimeOffset> オブジェクトをインスタンス化する方法、および <xref:System.DateTime> の値を <xref:System.DateTimeOffset> の値に変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-121">[Instantiating a DateTimeOffset object](instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="5fa44-122">[方法: 調整規則のないタイム ゾーンを作成する](create-time-zones-without-adjustment-rules.md) 夏時間の調整をサポートしないカスタム タイム ゾーンを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-122">[How to: Create time zones without adjustment rules](create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="5fa44-123">[方法 : 調整規則のあるタイム ゾーンを作成する](create-time-zones-with-adjustment-rules.md) 1 つ以上の夏時間調整をサポートするカスタム タイム ゾーンを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-123">[How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="5fa44-124">[タイム ゾーンの保存と復元](saving-and-restoring-time-zones.md) タイム ゾーン データのシリアル化と逆シリアル化が <xref:System.TimeZoneInfo> でどのようにサポートされるかを説明し、これらの機能を使用できるいくつかのシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-124">[Saving and restoring time zones](saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="5fa44-125">[方法 : 埋め込みリソースにタイム ゾーンを保存する](save-time-zones-to-an-embedded-resource.md) カスタム タイム ゾーンを作成し、その情報をリソース ファイルに保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-125">[How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="5fa44-126">[方法: 埋め込みリソースからタイム ゾーンを復元する](restore-time-zones-from-an-embedded-resource.md) 埋め込みリソース ファイルに保存されているカスタム タイム ゾーンをインスタンス化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-126">[How to: Restore time zones from an embedded resource](restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="5fa44-127">[日付と時刻を使用した算術演算の実行](performing-arithmetic-operations.md)<xref:System.DateTime> および <xref:System.DateTimeOffset> の値の加算、減算、比較に関連する問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-127">[Performing arithmetic operations with dates and times](performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="5fa44-128">[方法: 日付と時刻の演算でタイム ゾーンを使用する](use-time-zones-in-arithmetic.md) タイム ゾーンの調整規則を反映する日付と時刻の演算を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-128">[How to: Use time zones in date and time arithmetic](use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="5fa44-129">[DateTime と DateTimeOffset 間の変換](converting-between-datetime-and-offset.md)<xref:System.DateTime> の値と <xref:System.DateTimeOffset> の値の変換方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-129">[Converting between DateTime and DateTimeOffset](converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="5fa44-130">[タイム ゾーン間での時刻の変換](converting-between-time-zones.md) タイム ゾーン間での時刻の変換方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-130">[Converting times between time zones](converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="5fa44-131">[方法: あいまいな時刻を解決する](resolve-ambiguous-times.md) 時刻をタイム ゾーンの標準時刻に対応させることで、あいまいな時刻を解決する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-131">[How to: Resolve ambiguous times](resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="5fa44-132">[方法: ユーザーがあいまいな時刻を解決できるようにする](let-users-resolve-ambiguous-times.md) ユーザーがあいまいな現地時刻と世界協定時刻の対応を決定できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fa44-132">[How to: Let users resolve ambiguous times](let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="5fa44-133">参照先</span><span class="sxs-lookup"><span data-stu-id="5fa44-133">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
