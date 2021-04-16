---
description: '詳細情報: タイム ゾーンの保存と復元'
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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702445"
---
# <a name="saving-and-restoring-time-zones"></a><span data-ttu-id="63693-103">タイム ゾーンの保存と復元</span><span class="sxs-lookup"><span data-stu-id="63693-103">Saving and restoring time zones</span></span>

<span data-ttu-id="63693-104"><xref:System.TimeZoneInfo> クラスは、定義済みのタイム ゾーン データを取得するためにレジストリに依存しています。</span><span class="sxs-lookup"><span data-stu-id="63693-104">The <xref:System.TimeZoneInfo> class relies on the registry to retrieve predefined time zone data.</span></span> <span data-ttu-id="63693-105">ただし、レジストリは動的な構造です。</span><span class="sxs-lookup"><span data-stu-id="63693-105">However, the registry is a dynamic structure.</span></span> <span data-ttu-id="63693-106">また、レジストリに含まれているタイム ゾーン情報は、主に現在の年の時間調整と変換を処理するためにオペレーティング システムによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="63693-106">Additionally, the time zone information that the registry contains is used by the operating system primarily to handle time adjustments and conversions for the current year.</span></span> <span data-ttu-id="63693-107">これにより、正確なタイム ゾーン データに依存するアプリケーションには、次の 2 つの大きな影響があります。</span><span class="sxs-lookup"><span data-stu-id="63693-107">This has two major implications for applications that rely on accurate time zone data:</span></span>

- <span data-ttu-id="63693-108">アプリケーションで必要とされているタイム ゾーンがレジストリに定義されていなかったり、名前変更されたり、レジストリから削除されたりしている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="63693-108">A time zone that is required by an application may not be defined in the registry, or it may have been renamed or removed from the registry.</span></span>

- <span data-ttu-id="63693-109">レジストリに定義されているタイム ゾーンには、過去のタイム ゾーン変換に必要な特定の調整規則に関する情報が含まれていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="63693-109">A time zone that is defined in the registry may lack information about the particular adjustment rules that are necessary for historical time zone conversions.</span></span>

<span data-ttu-id="63693-110"><xref:System.TimeZoneInfo> クラスでは、タイム ゾーン データのシリアル化 (保存) と逆シリアル化 (復元) をサポートすることで、これらの制限に対処します。</span><span class="sxs-lookup"><span data-stu-id="63693-110">The <xref:System.TimeZoneInfo> class addresses these limitations through its support for serialization (saving) and deserialization (restoring) of time zone data.</span></span>

## <a name="time-zone-serialization-and-deserialization"></a><span data-ttu-id="63693-111">タイム ゾーンのシリアル化と逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="63693-111">Time zone serialization and deserialization</span></span>

<span data-ttu-id="63693-112">タイム ゾーン データをシリアル化および逆シリアル化してタイム ゾーンを保存および復元することに関係するのは、次の 2 つのメソッド呼び出しだけです。</span><span class="sxs-lookup"><span data-stu-id="63693-112">Saving and restoring a time zone by serializing and deserializing time zone data involves just two method calls:</span></span>

- <span data-ttu-id="63693-113"><xref:System.TimeZoneInfo.ToSerializedString%2A> オブジェクトのシリアル化は、オブジェクトの <xref:System.TimeZoneInfo> メソッドを呼び出すことによって行えます。</span><span class="sxs-lookup"><span data-stu-id="63693-113">You can serialize a <xref:System.TimeZoneInfo> object by calling that object's <xref:System.TimeZoneInfo.ToSerializedString%2A> method.</span></span> <span data-ttu-id="63693-114">このメソッドは、パラメーターを受け取らず、タイム ゾーン情報を含む文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="63693-114">The method takes no parameters and returns a string that contains time zone information.</span></span>

- <span data-ttu-id="63693-115">シリアル化された文字列から <xref:System.TimeZoneInfo> オブジェクトを逆シリアル化することは、`static` (Visual Basic では `Shared`) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> メソッドにその文字列を渡すことによって行えます。</span><span class="sxs-lookup"><span data-stu-id="63693-115">You can deserialize a <xref:System.TimeZoneInfo> object from a serialized string by passing that string to the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> method.</span></span>

## <a name="serialization-and-deserialization-scenarios"></a><span data-ttu-id="63693-116">シリアル化と逆シリアル化のシナリオ</span><span class="sxs-lookup"><span data-stu-id="63693-116">Serialization and deserialization scenarios</span></span>

<span data-ttu-id="63693-117"><xref:System.TimeZoneInfo> オブジェクトを文字列に保存 (またはシリアル化) し、後で使用できるように復元 (または逆シリアル化) する機能により、<xref:System.TimeZoneInfo> クラスの利便性と柔軟性が向上します。</span><span class="sxs-lookup"><span data-stu-id="63693-117">The ability to save (or serialize) a <xref:System.TimeZoneInfo> object to a string and to restore (or deserialize) it for later use increases both the utility and the flexibility of the <xref:System.TimeZoneInfo> class.</span></span> <span data-ttu-id="63693-118">このセクションでは、シリアル化と逆シリアル化が最も役立ついくつかの状況を調べます。</span><span class="sxs-lookup"><span data-stu-id="63693-118">This section examines some of the situations in which serialization and deserialization are most useful.</span></span>

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a><span data-ttu-id="63693-119">アプリケーション内のタイム ゾーン データのシリアル化と逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="63693-119">Serializing and deserializing time zone data in an application</span></span>

<span data-ttu-id="63693-120">必要なときに、文字列から、シリアル化されたタイム ゾーンを復元できます。</span><span class="sxs-lookup"><span data-stu-id="63693-120">A serialized time zone can be restored from a string when it is needed.</span></span> <span data-ttu-id="63693-121">アプリケーションでは、レジストリから取得したタイム ゾーンで特定の日付範囲内の日付と時刻を正しく変換できない場合に、このような処理が実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="63693-121">An application might do this if the time zone retrieved from the registry is unable to correctly convert a date and time within a particular date range.</span></span> <span data-ttu-id="63693-122">たとえば、Windows XP レジストリのタイム ゾーン データでは 1 つの調整規則がサポートされていますが、Windows Vista レジストリで定義されているタイム ゾーンでは通常、2 つの調整規則に関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="63693-122">For example, time zone data in the Windows XP registry supports a single adjustment rule, while time zones defined in the Windows Vista registry typically provide information about two adjustment rules.</span></span> <span data-ttu-id="63693-123">これは、過去の時刻変換が不正確になるおそれがあることを意味します。</span><span class="sxs-lookup"><span data-stu-id="63693-123">This means that historical time conversions may be inaccurate.</span></span> <span data-ttu-id="63693-124">タイム ゾーン データのシリアル化と逆シリアル化では、この制限に対処できます。</span><span class="sxs-lookup"><span data-stu-id="63693-124">Serialization and deserialization of time zone data can handle this limitation.</span></span>

<span data-ttu-id="63693-125">次の例では、カスタムの <xref:System.TimeZoneInfo> クラスには、米国東部標準タイム ゾーンを 1883 年から 1917 年の期間 (米国に夏時間が導入される前) について表現するための調整規則が定義されていません。</span><span class="sxs-lookup"><span data-stu-id="63693-125">In the following example, a custom <xref:System.TimeZoneInfo> class that has no adjustment rules is defined to represent the U.S. Eastern Standard Time zone from 1883 to 1917, before the introduction of daylight saving time in the United States.</span></span> <span data-ttu-id="63693-126">カスタム タイム ゾーンは、グローバル スコープを持つ変数にシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="63693-126">The custom time zone is serialized in a variable that has global scope.</span></span> <span data-ttu-id="63693-127">タイム ゾーンの変換メソッド `ConvertUtcTime` には、変換する協定世界時 (UTC) の時刻が渡されます。</span><span class="sxs-lookup"><span data-stu-id="63693-127">The time zone conversion method, `ConvertUtcTime`, is passed Coordinated Universal Time (UTC) times to convert.</span></span> <span data-ttu-id="63693-128">日付と時刻が 1917 年以前である場合は、シリアル化された文字列からカスタム東部標準タイム ゾーンが復元され、レジストリから取得したタイム ゾーンは置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="63693-128">If the date and time occurs in 1917 or earlier, the custom Eastern Standard Time zone is restored from a serialized string and replaces the time zone retrieved from the registry.</span></span>

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a><span data-ttu-id="63693-129">タイム ゾーンの例外を処理する</span><span class="sxs-lookup"><span data-stu-id="63693-129">Handling time zone exceptions</span></span>

<span data-ttu-id="63693-130">レジストリは動的な構造であるため、その内容は誤ってまたは意図的に変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="63693-130">Because the registry is a dynamic structure, its contents are subject to accidental or deliberate modification.</span></span> <span data-ttu-id="63693-131">これは、レジストリに定義されていなければならない、アプリケーションの正常実行に必要なタイム ゾーンが欠落している場合もあるということです。</span><span class="sxs-lookup"><span data-stu-id="63693-131">This means that a time zone that should be defined in the registry and that is required for an application to execute successfully may be absent.</span></span> <span data-ttu-id="63693-132">タイム ゾーンのシリアル化と逆シリアル化をサポートしていない場合は、結果として発生する <xref:System.TimeZoneNotFoundException> を、アプリケーションを終了することで処理するしかありません。</span><span class="sxs-lookup"><span data-stu-id="63693-132">Without support for time zone serialization and deserialization, you have little choice but to handle the resulting <xref:System.TimeZoneNotFoundException> by ending the application.</span></span> <span data-ttu-id="63693-133">しかし、タイム ゾーンのシリアル化と逆シリアル化を使用すれば、シリアル化された文字列から必要なタイム ゾーンを復元して予期しない <xref:System.TimeZoneNotFoundException> を処理でき、アプリケーションは継続して実行されます。</span><span class="sxs-lookup"><span data-stu-id="63693-133">However, by using time zone serialization and deserialization, you can handle an unexpected <xref:System.TimeZoneNotFoundException> by restoring the required time zone from a serialized string, and the application will continue to run.</span></span>

<span data-ttu-id="63693-134">次の例では、カスタムの中部標準時のタイム ゾーンを作成してシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="63693-134">The following example creates and serializes a custom Central Standard Time zone.</span></span> <span data-ttu-id="63693-135">その後、レジストリから中部標準時のタイム ゾーンを取得しようとします。</span><span class="sxs-lookup"><span data-stu-id="63693-135">It then tries to retrieve the Central Standard Time zone from the registry.</span></span> <span data-ttu-id="63693-136">取得操作によって <xref:System.TimeZoneNotFoundException> または <xref:System.InvalidTimeZoneException> のいずれかがスローされた場合、例外ハンドラーによってタイム ゾーンが逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="63693-136">If the retrieval operation throws either a <xref:System.TimeZoneNotFoundException> or an <xref:System.InvalidTimeZoneException>, the exception handler deserializes the time zone.</span></span>

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a><span data-ttu-id="63693-137">シリアル化された文字列を格納し、必要に応じて復元する</span><span class="sxs-lookup"><span data-stu-id="63693-137">Storing a serialized string and restoring it when needed</span></span>

<span data-ttu-id="63693-138">前の例では、タイム ゾーン情報を文字列変数に格納し、必要に応じて復元しました。</span><span class="sxs-lookup"><span data-stu-id="63693-138">The previous examples have stored time zone information to a string variable and restored it when needed.</span></span> <span data-ttu-id="63693-139">ただし、シリアル化されたタイム ゾーン情報を含む文字列そのものを、外部ファイル、アプリケーションに埋め込まれているリソース ファイル、レジストリなど、一部のストレージ メディアに格納することができます</span><span class="sxs-lookup"><span data-stu-id="63693-139">However, the string that contains serialized time zone information can itself be stored in some storage medium, such as an external file, a resource file embedded in the application, or the registry.</span></span> <span data-ttu-id="63693-140">(カスタム タイム ゾーンに関する情報は、レジストリ内のシステムのタイム ゾーン キーとは別に保存する必要があることにご注意ください)。</span><span class="sxs-lookup"><span data-stu-id="63693-140">(Note that information about custom time zones should be stored apart from the system's time zone keys in the registry.)</span></span>

<span data-ttu-id="63693-141">この方法でシリアル化されたタイム ゾーン文字列を格納すると、タイム ゾーン作成ルーチンもアプリケーション自体から分離されます。</span><span class="sxs-lookup"><span data-stu-id="63693-141">Storing a serialized time zone string in this manner also separates the time zone creation routine from the application itself.</span></span> <span data-ttu-id="63693-142">たとえば、タイム ゾーン作成ルーチンを実行して、アプリケーションが使用できる過去のタイム ゾーン情報が入ったデータ ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="63693-142">For example, a time zone creation routine can execute and create a data file that contains historical time zone information that an application can use.</span></span> <span data-ttu-id="63693-143">その後、データ ファイルをアプリケーションと共にインストールすることができます。アプリケーションで必要になったときにこれを開いて、1 つまたは複数のタイム ゾーンを逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="63693-143">The data file can be then be installed with the application, and it can be opened and one or more of its time zones can be deserialized when the application requires them.</span></span>

<span data-ttu-id="63693-144">埋め込みリソースを使用してシリアル化されたタイム ゾーン データを格納する例については、「[方法: 埋め込みリソースにタイム ゾーンを保存する](save-time-zones-to-an-embedded-resource.md)」および「[方法: 埋め込みリソースからタイム ゾーンを復元する](restore-time-zones-from-an-embedded-resource.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="63693-144">For an example that uses an embedded resource to store serialized time zone data, see [How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md) and [How to: Restore time zones from an embedded resource](restore-time-zones-from-an-embedded-resource.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63693-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="63693-145">See also</span></span>

- [<span data-ttu-id="63693-146">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="63693-146">Dates, times, and time zones</span></span>](index.md)
