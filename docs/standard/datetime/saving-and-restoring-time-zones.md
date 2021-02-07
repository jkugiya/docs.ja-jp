---
description: 詳細については、「タイムゾーンの保存と復元」を参照してください。
title: タイム ゾーンの保存と復元
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- restoring time zones
- deserialization [.NET], time zones
- serialization [.NET], time zones
- time zone objects [.NET], restoring
- saving time zones
- time zone objects [.NET], deserializing
- time zones [.NET], saving
- time zones [.NET], restoring
- time zone objects [.NET], serializing
- time zone objects [.NET], saving
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
ms.openlocfilehash: bd888c2d9a1f02fa05fd1abf9d984022be03e192
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702445"
---
# <a name="saving-and-restoring-time-zones"></a><span data-ttu-id="85f0d-103">タイム ゾーンの保存と復元</span><span class="sxs-lookup"><span data-stu-id="85f0d-103">Saving and restoring time zones</span></span>

<span data-ttu-id="85f0d-104">クラスは、 <xref:System.TimeZoneInfo> 定義済みのタイムゾーンデータを取得するためにレジストリに依存しています。</span><span class="sxs-lookup"><span data-stu-id="85f0d-104">The <xref:System.TimeZoneInfo> class relies on the registry to retrieve predefined time zone data.</span></span> <span data-ttu-id="85f0d-105">ただし、レジストリは動的な構造です。</span><span class="sxs-lookup"><span data-stu-id="85f0d-105">However, the registry is a dynamic structure.</span></span> <span data-ttu-id="85f0d-106">また、レジストリに格納されているタイムゾーン情報は、主に現在の年の時間調整と変換を処理するためにオペレーティングシステムによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="85f0d-106">Additionally, the time zone information that the registry contains is used by the operating system primarily to handle time adjustments and conversions for the current year.</span></span> <span data-ttu-id="85f0d-107">正確なタイムゾーンデータに依存するアプリケーションには、次の2つの大きな影響があります。</span><span class="sxs-lookup"><span data-stu-id="85f0d-107">This has two major implications for applications that rely on accurate time zone data:</span></span>

- <span data-ttu-id="85f0d-108">アプリケーションで必要なタイムゾーンがレジストリで定義されていないか、名前が変更されたか、レジストリから削除された可能性があります。</span><span class="sxs-lookup"><span data-stu-id="85f0d-108">A time zone that is required by an application may not be defined in the registry, or it may have been renamed or removed from the registry.</span></span>

- <span data-ttu-id="85f0d-109">レジストリに定義されているタイムゾーンには、履歴のタイムゾーンの変換に必要な特定の調整規則に関する情報が含まれていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="85f0d-109">A time zone that is defined in the registry may lack information about the particular adjustment rules that are necessary for historical time zone conversions.</span></span>

<span data-ttu-id="85f0d-110">クラスは、 <xref:System.TimeZoneInfo> タイムゾーンデータのシリアル化 (保存) と逆シリアル化 (復元) をサポートすることで、これらの制限に対処します。</span><span class="sxs-lookup"><span data-stu-id="85f0d-110">The <xref:System.TimeZoneInfo> class addresses these limitations through its support for serialization (saving) and deserialization (restoring) of time zone data.</span></span>

## <a name="time-zone-serialization-and-deserialization"></a><span data-ttu-id="85f0d-111">タイムゾーンのシリアル化と逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="85f0d-111">Time zone serialization and deserialization</span></span>

<span data-ttu-id="85f0d-112">タイムゾーンデータをシリアル化および逆シリアル化してタイムゾーンを保存および復元するには、次の2つのメソッド呼び出しのみが必要です。</span><span class="sxs-lookup"><span data-stu-id="85f0d-112">Saving and restoring a time zone by serializing and deserializing time zone data involves just two method calls:</span></span>

- <span data-ttu-id="85f0d-113">オブジェクト <xref:System.TimeZoneInfo> のメソッドを呼び出すことによって、オブジェクトをシリアル化でき <xref:System.TimeZoneInfo.ToSerializedString%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="85f0d-113">You can serialize a <xref:System.TimeZoneInfo> object by calling that object's <xref:System.TimeZoneInfo.ToSerializedString%2A> method.</span></span> <span data-ttu-id="85f0d-114">メソッドはパラメーターを取らず、タイムゾーン情報を含む文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="85f0d-114">The method takes no parameters and returns a string that contains time zone information.</span></span>

- <span data-ttu-id="85f0d-115"><xref:System.TimeZoneInfo> `static` (Visual Basic) メソッドにその文字列を渡すことによって、シリアル化された文字列からオブジェクトを逆シリアル化でき `Shared` <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="85f0d-115">You can deserialize a <xref:System.TimeZoneInfo> object from a serialized string by passing that string to the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> method.</span></span>

## <a name="serialization-and-deserialization-scenarios"></a><span data-ttu-id="85f0d-116">シリアル化と逆シリアル化のシナリオ</span><span class="sxs-lookup"><span data-stu-id="85f0d-116">Serialization and deserialization scenarios</span></span>

<span data-ttu-id="85f0d-117">オブジェクトを文字列に保存 (シリアル化) し、 <xref:System.TimeZoneInfo> 後で使用できるように復元 (または逆シリアル化) する機能により、ユーティリティとクラスの柔軟性が向上し <xref:System.TimeZoneInfo> ます。</span><span class="sxs-lookup"><span data-stu-id="85f0d-117">The ability to save (or serialize) a <xref:System.TimeZoneInfo> object to a string and to restore (or deserialize) it for later use increases both the utility and the flexibility of the <xref:System.TimeZoneInfo> class.</span></span> <span data-ttu-id="85f0d-118">ここでは、シリアル化と逆シリアル化が最も役立つ状況について説明します。</span><span class="sxs-lookup"><span data-stu-id="85f0d-118">This section examines some of the situations in which serialization and deserialization are most useful.</span></span>

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a><span data-ttu-id="85f0d-119">アプリケーション内のタイムゾーンデータのシリアル化と逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="85f0d-119">Serializing and deserializing time zone data in an application</span></span>

<span data-ttu-id="85f0d-120">シリアル化されたタイムゾーンは、必要に応じて文字列から復元できます。</span><span class="sxs-lookup"><span data-stu-id="85f0d-120">A serialized time zone can be restored from a string when it is needed.</span></span> <span data-ttu-id="85f0d-121">アプリケーションは、レジストリから取得したタイムゾーンが特定の日付範囲内の日付と時刻を正しく変換できない場合に、このような処理を実行する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="85f0d-121">An application might do this if the time zone retrieved from the registry is unable to correctly convert a date and time within a particular date range.</span></span> <span data-ttu-id="85f0d-122">たとえば、Windows XP レジストリのタイムゾーンデータは1つの調整規則をサポートしますが、Windows Vista レジストリで定義されているタイムゾーンは通常、2つの調整規則に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="85f0d-122">For example, time zone data in the Windows XP registry supports a single adjustment rule, while time zones defined in the Windows Vista registry typically provide information about two adjustment rules.</span></span> <span data-ttu-id="85f0d-123">これは、過去の時刻の変換が不正確になる可能性があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="85f0d-123">This means that historical time conversions may be inaccurate.</span></span> <span data-ttu-id="85f0d-124">タイムゾーンデータのシリアル化と逆シリアル化では、この制限を処理できます。</span><span class="sxs-lookup"><span data-stu-id="85f0d-124">Serialization and deserialization of time zone data can handle this limitation.</span></span>

<span data-ttu-id="85f0d-125">次の例で <xref:System.TimeZoneInfo> は、米国に夏時間を導入する前に、調整規則のないカスタムクラスを定義して、米国東部標準時のタイムゾーンを1883から1917に設定しています。</span><span class="sxs-lookup"><span data-stu-id="85f0d-125">In the following example, a custom <xref:System.TimeZoneInfo> class that has no adjustment rules is defined to represent the U.S. Eastern Standard Time zone from 1883 to 1917, before the introduction of daylight saving time in the United States.</span></span> <span data-ttu-id="85f0d-126">カスタムタイムゾーンは、グローバルスコープを持つ変数でシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="85f0d-126">The custom time zone is serialized in a variable that has global scope.</span></span> <span data-ttu-id="85f0d-127">タイムゾーンの変換メソッドは、 `ConvertUtcTime` 協定世界時 (UTC) の時刻に変換されます。</span><span class="sxs-lookup"><span data-stu-id="85f0d-127">The time zone conversion method, `ConvertUtcTime`, is passed Coordinated Universal Time (UTC) times to convert.</span></span> <span data-ttu-id="85f0d-128">日付と時刻が1917以前である場合は、カスタム東部標準時のタイムゾーンがシリアル化された文字列から復元され、レジストリから取得したタイムゾーンが置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="85f0d-128">If the date and time occurs in 1917 or earlier, the custom Eastern Standard Time zone is restored from a serialized string and replaces the time zone retrieved from the registry.</span></span>

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a><span data-ttu-id="85f0d-129">タイムゾーンの例外の処理</span><span class="sxs-lookup"><span data-stu-id="85f0d-129">Handling time zone exceptions</span></span>

<span data-ttu-id="85f0d-130">レジストリは動的な構造であるため、その内容は偶発的または意図的に変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="85f0d-130">Because the registry is a dynamic structure, its contents are subject to accidental or deliberate modification.</span></span> <span data-ttu-id="85f0d-131">これは、レジストリで定義され、アプリケーションを正常に実行するために必要なタイムゾーンが存在しない可能性があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="85f0d-131">This means that a time zone that should be defined in the registry and that is required for an application to execute successfully may be absent.</span></span> <span data-ttu-id="85f0d-132">タイムゾーンのシリアル化と逆シリアル化をサポートしていない場合は、アプリケーションを終了することによって、その結果を処理することはほとんどありません <xref:System.TimeZoneNotFoundException> 。</span><span class="sxs-lookup"><span data-stu-id="85f0d-132">Without support for time zone serialization and deserialization, you have little choice but to handle the resulting <xref:System.TimeZoneNotFoundException> by ending the application.</span></span> <span data-ttu-id="85f0d-133">ただし、タイムゾーンのシリアル化と逆シリアル化を使用すると、 <xref:System.TimeZoneNotFoundException> シリアル化された文字列から必要なタイムゾーンを復元することで、予期しないを処理できます。この場合、アプリケーションは実行を続行します。</span><span class="sxs-lookup"><span data-stu-id="85f0d-133">However, by using time zone serialization and deserialization, you can handle an unexpected <xref:System.TimeZoneNotFoundException> by restoring the required time zone from a serialized string, and the application will continue to run.</span></span>

<span data-ttu-id="85f0d-134">次の例では、カスタムの中部標準タイムゾーンを作成してシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="85f0d-134">The following example creates and serializes a custom Central Standard Time zone.</span></span> <span data-ttu-id="85f0d-135">次に、レジストリから中部標準時ゾーンを取得しようとします。</span><span class="sxs-lookup"><span data-stu-id="85f0d-135">It then tries to retrieve the Central Standard Time zone from the registry.</span></span> <span data-ttu-id="85f0d-136">取得操作によってまたはがスローされた場合、 <xref:System.TimeZoneNotFoundException> <xref:System.InvalidTimeZoneException> 例外ハンドラーはタイムゾーンを逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="85f0d-136">If the retrieval operation throws either a <xref:System.TimeZoneNotFoundException> or an <xref:System.InvalidTimeZoneException>, the exception handler deserializes the time zone.</span></span>

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a><span data-ttu-id="85f0d-137">シリアル化された文字列を格納し、必要に応じて復元する</span><span class="sxs-lookup"><span data-stu-id="85f0d-137">Storing a serialized string and restoring it when needed</span></span>

<span data-ttu-id="85f0d-138">前の例では、タイムゾーン情報が文字列変数に格納され、必要に応じて復元されています。</span><span class="sxs-lookup"><span data-stu-id="85f0d-138">The previous examples have stored time zone information to a string variable and restored it when needed.</span></span> <span data-ttu-id="85f0d-139">ただし、シリアル化されたタイムゾーン情報を含む文字列は、外部ファイル、アプリケーションに埋め込まれているリソースファイル、レジストリなど、一部のストレージメディアに格納することができます。</span><span class="sxs-lookup"><span data-stu-id="85f0d-139">However, the string that contains serialized time zone information can itself be stored in some storage medium, such as an external file, a resource file embedded in the application, or the registry.</span></span> <span data-ttu-id="85f0d-140">(カスタムタイムゾーンに関する情報は、レジストリ内のシステムのタイムゾーンキーとは別に保存する必要があることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="85f0d-140">(Note that information about custom time zones should be stored apart from the system's time zone keys in the registry.)</span></span>

<span data-ttu-id="85f0d-141">この方法でシリアル化されたタイムゾーン文字列を格納すると、タイムゾーン作成ルーチンもアプリケーション自体から分離されます。</span><span class="sxs-lookup"><span data-stu-id="85f0d-141">Storing a serialized time zone string in this manner also separates the time zone creation routine from the application itself.</span></span> <span data-ttu-id="85f0d-142">たとえば、タイムゾーン作成ルーチンを実行して、アプリケーションが使用できる履歴タイムゾーン情報を含むデータファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="85f0d-142">For example, a time zone creation routine can execute and create a data file that contains historical time zone information that an application can use.</span></span> <span data-ttu-id="85f0d-143">その後、データファイルをアプリケーションと共にインストールすることができます。これを開くと、アプリケーションで必要になったときに1つ以上のタイムゾーンを逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="85f0d-143">The data file can be then be installed with the application, and it can be opened and one or more of its time zones can be deserialized when the application requires them.</span></span>

<span data-ttu-id="85f0d-144">埋め込みリソースを使用してシリアル化されたタイムゾーンデータを格納する例については、「方法: 埋め込みリソース [にタイムゾーンを保存](save-time-zones-to-an-embedded-resource.md) する」および「 [方法: 埋め込みリソースからタイムゾーンを復元する](restore-time-zones-from-an-embedded-resource.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85f0d-144">For an example that uses an embedded resource to store serialized time zone data, see [How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md) and [How to: Restore time zones from an embedded resource](restore-time-zones-from-an-embedded-resource.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="85f0d-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="85f0d-145">See also</span></span>

- [<span data-ttu-id="85f0d-146">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="85f0d-146">Dates, times, and time zones</span></span>](index.md)
