---
description: '詳細情報: 日付と時刻の値をラウンドトリップさせる方法'
title: '方法: 日付と時刻の値をラウンドトリップさせる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- round-trip date and time values
- dates [.NET], round-trip values
- time zones [.NET], round-trip date and time values
- time [.NET], round-trip values
- formatting strings [.NET], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
ms.openlocfilehash: 66f1ac2e8b51d7117f771a966a3c01cff24b78a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642748"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="01631-103">方法: 日付と時刻の値をラウンドトリップさせる</span><span class="sxs-lookup"><span data-stu-id="01631-103">How to: Round-trip Date and Time Values</span></span>

<span data-ttu-id="01631-104">ある特定の時点を明確に表すように日付と時刻の値を保つことは、多くのアプリケーションに共通する要件です。</span><span class="sxs-lookup"><span data-stu-id="01631-104">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="01631-105">この記事では、<xref:System.DateTime> 値、<xref:System.DateTimeOffset> 値、日付と時刻の値とタイム ゾーンの情報を保存し、復元する方法について示します。復元した値によって、保存した値と同じ時刻が識別されるようにします。</span><span class="sxs-lookup"><span data-stu-id="01631-105">This article shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>

## <a name="round-trip-a-datetime-value"></a><span data-ttu-id="01631-106">DateTime 値をラウンドトリップさせる</span><span class="sxs-lookup"><span data-stu-id="01631-106">Round-trip a DateTime value</span></span>

1. <span data-ttu-id="01631-107"><xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> メソッドを "o" 書式指定子と共に呼び出して、<xref:System.DateTime> 値を対応する文字列形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="01631-107">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="01631-108"><xref:System.DateTime> 値の文字列形式をファイルに保存するか、プロセス、アプリケーション ドメイン、またはマシン境界を通過させます。</span><span class="sxs-lookup"><span data-stu-id="01631-108">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="01631-109"><xref:System.DateTime> 値を表す文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="01631-109">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>

4. <span data-ttu-id="01631-110"><xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> メソッドを呼び出し、`styles` パラメーターの値として <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> を渡します。</span><span class="sxs-lookup"><span data-stu-id="01631-110">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="01631-111"><xref:System.DateTime> 値をラウンドトリップさせる方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="01631-111">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

<span data-ttu-id="01631-112"><xref:System.DateTime> 値をラウンドトリップさせる場合、この方法により、あらゆる現地時刻と協定世界時刻を適切に保存できます。</span><span class="sxs-lookup"><span data-stu-id="01631-112">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="01631-113">たとえば、現地時刻の <xref:System.DateTime> 値が米国太平洋標準時タイム ゾーンのシステムで保存され、米国中部標準時タイム ゾーンのシステムで復元された場合、復元された日付と時刻は 2 つのタイム ゾーンの時差を反映し、元の時刻より 2 時間後になります。</span><span class="sxs-lookup"><span data-stu-id="01631-113">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="01631-114">ただし、タイム ゾーンが指定されていない時刻の場合、この方法では必ずしも正確な結果を得られるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="01631-114">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="01631-115"><xref:System.DateTime.Kind%2A> プロパティが <xref:System.DateTimeKind.Unspecified> であるすべての <xref:System.DateTime> 値がローカル時間のように扱われます。</span><span class="sxs-lookup"><span data-stu-id="01631-115">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="01631-116">ローカル時間でない場合は、<xref:System.DateTime> によって正しい時点を識別することはできません。</span><span class="sxs-lookup"><span data-stu-id="01631-116">If it's not a local time, the <xref:System.DateTime> doesn't successfully identify the correct point in time.</span></span> <span data-ttu-id="01631-117">この制限を回避するには、日付と時刻の値と該当するタイム ゾーンを確実に関連付けてから保存操作と復元操作を行います。</span><span class="sxs-lookup"><span data-stu-id="01631-117">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>

## <a name="round-trip-a-datetimeoffset-value"></a><span data-ttu-id="01631-118">DateTimeOffset 値をラウンドトリップさせる</span><span class="sxs-lookup"><span data-stu-id="01631-118">Round-trip a DateTimeOffset value</span></span>

1. <span data-ttu-id="01631-119"><xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> メソッドを "o" 書式指定子と共に呼び出して、<xref:System.DateTimeOffset> 値を対応する文字列形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="01631-119">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="01631-120"><xref:System.DateTimeOffset> 値の文字列形式をファイルに保存するか、プロセス、アプリケーション ドメイン、またはマシン境界を通過させます。</span><span class="sxs-lookup"><span data-stu-id="01631-120">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="01631-121"><xref:System.DateTimeOffset> 値を表す文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="01631-121">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>

4. <span data-ttu-id="01631-122"><xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> メソッドを呼び出し、`styles` パラメーターの値として <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> を渡します。</span><span class="sxs-lookup"><span data-stu-id="01631-122">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="01631-123"><xref:System.DateTimeOffset> 値をラウンドトリップさせる方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="01631-123">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

<span data-ttu-id="01631-124">この方法により、<xref:System.DateTimeOffset> 値は常にある特定の時点として明確に識別されます。</span><span class="sxs-lookup"><span data-stu-id="01631-124">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="01631-125">識別されたら、<xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> メソッドを呼び出すことで、この値を協定世界時 (UTC) に変換できます。あるいは、<xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> または <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> メソッドを呼び出すことで、特定のタイム ゾーンの時刻に変換できます。</span><span class="sxs-lookup"><span data-stu-id="01631-125">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="01631-126">この方法には、特定のタイム ゾーンの時刻を表す <xref:System.DateTimeOffset> 値に対して日付と時刻の演算を行ったときに、そのタイム ゾーンにおける正確な結果を得ることができない場合があるという重要な制限があります。</span><span class="sxs-lookup"><span data-stu-id="01631-126">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="01631-127">これは、<xref:System.DateTimeOffset> 値をインスタンス化すると、対応するタイム ゾーンとの関連付けが解除されるためです。</span><span class="sxs-lookup"><span data-stu-id="01631-127">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="01631-128">したがって、日付と時刻の計算を実行した場合、タイム ゾーンの調整規則は適用されなくなります。</span><span class="sxs-lookup"><span data-stu-id="01631-128">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="01631-129">この問題を回避するには、日付と時刻の値、および付随するタイム ゾーンの両方を保持するカスタム型を定義します。</span><span class="sxs-lookup"><span data-stu-id="01631-129">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>

## <a name="round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="01631-130">日付と時刻の値とそのタイム ゾーンをラウンドトリップさせる</span><span class="sxs-lookup"><span data-stu-id="01631-130">Round-trip a date and time value with its time zone</span></span>

1. <span data-ttu-id="01631-131">クラスまたは構造と 2 つのフィールドを定義します。</span><span class="sxs-lookup"><span data-stu-id="01631-131">Define a class or a structure with two fields.</span></span> <span data-ttu-id="01631-132">最初のフィールドは <xref:System.DateTime> または <xref:System.DateTimeOffset> オブジェクトです。2 つ目のフィールドは <xref:System.TimeZoneInfo> オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="01631-132">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="01631-133">次の例は、このような型を簡易にしたものです。</span><span class="sxs-lookup"><span data-stu-id="01631-133">The following example is a simple version of such a type.</span></span>

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. <span data-ttu-id="01631-134">クラスに <xref:System.SerializableAttribute> 属性を付けます。</span><span class="sxs-lookup"><span data-stu-id="01631-134">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>

3. <span data-ttu-id="01631-135"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> メソッドを使用し、オブジェクトをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="01631-135">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="01631-136"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> メソッドを使用し、オブジェクトを復元します。</span><span class="sxs-lookup"><span data-stu-id="01631-136">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>

5. <span data-ttu-id="01631-137">逆シリアル化されたオブジェクトを適切な型のオブジェクトにキャスト (C# の場合) するか、変換 (Visual Basic の場合) します。</span><span class="sxs-lookup"><span data-stu-id="01631-137">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>

<span data-ttu-id="01631-138">次の例では、タイム ゾーンと日時の情報の両方を格納するオブジェクトをラウンドトリップさせる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="01631-138">The following example illustrates how to round-trip an object that stores both time zone and date and time information.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

<span data-ttu-id="01631-139">この手法では、日時とタイム ゾーン オブジェクトを組み合わせるとき、日付値とタイム ゾーン値の同期が外れてはならないとき、保存と復元の前後で必ず、常に正しい時点を不明瞭なところなく反映する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01631-139">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="01631-140">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="01631-140">Compile the code</span></span>

<span data-ttu-id="01631-141">これらの例には以下が必要です。</span><span class="sxs-lookup"><span data-stu-id="01631-141">These examples require that:</span></span>

- <span data-ttu-id="01631-142">次の名前空間を C# `using` ステートメントまたは Visual Basic `Imports` ステートメントでインポートする</span><span class="sxs-lookup"><span data-stu-id="01631-142">The following namespaces be imported with C# `using` directives or Visual Basic `Imports` statements:</span></span>

  - <span data-ttu-id="01631-143"><xref:System> (C# のみ)</span><span class="sxs-lookup"><span data-stu-id="01631-143"><xref:System> (C# only)</span></span>

  - <xref:System.Globalization?displayProperty=nameWithType>

  - <xref:System.IO?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>

- <span data-ttu-id="01631-144">`DateInTimeZone` クラス以外、各コード例はクラスまたは Visual Basic モジュールに含め、メソッドでラップし、`Main` メソッドから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="01631-144">Each code example, other than the `DateInTimeZone` class, be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>

## <a name="see-also"></a><span data-ttu-id="01631-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="01631-145">See also</span></span>

- [<span data-ttu-id="01631-146">DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け</span><span class="sxs-lookup"><span data-stu-id="01631-146">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../datetime/choosing-between-datetime.md)
- [<span data-ttu-id="01631-147">標準の日時形式文字列</span><span class="sxs-lookup"><span data-stu-id="01631-147">Standard Date and Time Format Strings</span></span>](standard-date-and-time-format-strings.md)
