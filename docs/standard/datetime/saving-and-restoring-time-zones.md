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
# <a name="saving-and-restoring-time-zones"></a>タイム ゾーンの保存と復元

<xref:System.TimeZoneInfo> クラスは、定義済みのタイム ゾーン データを取得するためにレジストリに依存しています。 ただし、レジストリは動的な構造です。 また、レジストリに含まれているタイム ゾーン情報は、主に現在の年の時間調整と変換を処理するためにオペレーティング システムによって使用されます。 これにより、正確なタイム ゾーン データに依存するアプリケーションには、次の 2 つの大きな影響があります。

- アプリケーションで必要とされているタイム ゾーンがレジストリに定義されていなかったり、名前変更されたり、レジストリから削除されたりしている可能性があります。

- レジストリに定義されているタイム ゾーンには、過去のタイム ゾーン変換に必要な特定の調整規則に関する情報が含まれていない場合があります。

<xref:System.TimeZoneInfo> クラスでは、タイム ゾーン データのシリアル化 (保存) と逆シリアル化 (復元) をサポートすることで、これらの制限に対処します。

## <a name="time-zone-serialization-and-deserialization"></a>タイム ゾーンのシリアル化と逆シリアル化

タイム ゾーン データをシリアル化および逆シリアル化してタイム ゾーンを保存および復元することに関係するのは、次の 2 つのメソッド呼び出しだけです。

- <xref:System.TimeZoneInfo.ToSerializedString%2A> オブジェクトのシリアル化は、オブジェクトの <xref:System.TimeZoneInfo> メソッドを呼び出すことによって行えます。 このメソッドは、パラメーターを受け取らず、タイム ゾーン情報を含む文字列を返します。

- シリアル化された文字列から <xref:System.TimeZoneInfo> オブジェクトを逆シリアル化することは、`static` (Visual Basic では `Shared`) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> メソッドにその文字列を渡すことによって行えます。

## <a name="serialization-and-deserialization-scenarios"></a>シリアル化と逆シリアル化のシナリオ

<xref:System.TimeZoneInfo> オブジェクトを文字列に保存 (またはシリアル化) し、後で使用できるように復元 (または逆シリアル化) する機能により、<xref:System.TimeZoneInfo> クラスの利便性と柔軟性が向上します。 このセクションでは、シリアル化と逆シリアル化が最も役立ついくつかの状況を調べます。

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>アプリケーション内のタイム ゾーン データのシリアル化と逆シリアル化

必要なときに、文字列から、シリアル化されたタイム ゾーンを復元できます。 アプリケーションでは、レジストリから取得したタイム ゾーンで特定の日付範囲内の日付と時刻を正しく変換できない場合に、このような処理が実行される可能性があります。 たとえば、Windows XP レジストリのタイム ゾーン データでは 1 つの調整規則がサポートされていますが、Windows Vista レジストリで定義されているタイム ゾーンでは通常、2 つの調整規則に関する情報が提供されます。 これは、過去の時刻変換が不正確になるおそれがあることを意味します。 タイム ゾーン データのシリアル化と逆シリアル化では、この制限に対処できます。

次の例では、カスタムの <xref:System.TimeZoneInfo> クラスには、米国東部標準タイム ゾーンを 1883 年から 1917 年の期間 (米国に夏時間が導入される前) について表現するための調整規則が定義されていません。 カスタム タイム ゾーンは、グローバル スコープを持つ変数にシリアル化されます。 タイム ゾーンの変換メソッド `ConvertUtcTime` には、変換する協定世界時 (UTC) の時刻が渡されます。 日付と時刻が 1917 年以前である場合は、シリアル化された文字列からカスタム東部標準タイム ゾーンが復元され、レジストリから取得したタイム ゾーンは置き換えられます。

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>タイム ゾーンの例外を処理する

レジストリは動的な構造であるため、その内容は誤ってまたは意図的に変更される可能性があります。 これは、レジストリに定義されていなければならない、アプリケーションの正常実行に必要なタイム ゾーンが欠落している場合もあるということです。 タイム ゾーンのシリアル化と逆シリアル化をサポートしていない場合は、結果として発生する <xref:System.TimeZoneNotFoundException> を、アプリケーションを終了することで処理するしかありません。 しかし、タイム ゾーンのシリアル化と逆シリアル化を使用すれば、シリアル化された文字列から必要なタイム ゾーンを復元して予期しない <xref:System.TimeZoneNotFoundException> を処理でき、アプリケーションは継続して実行されます。

次の例では、カスタムの中部標準時のタイム ゾーンを作成してシリアル化します。 その後、レジストリから中部標準時のタイム ゾーンを取得しようとします。 取得操作によって <xref:System.TimeZoneNotFoundException> または <xref:System.InvalidTimeZoneException> のいずれかがスローされた場合、例外ハンドラーによってタイム ゾーンが逆シリアル化されます。

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>シリアル化された文字列を格納し、必要に応じて復元する

前の例では、タイム ゾーン情報を文字列変数に格納し、必要に応じて復元しました。 ただし、シリアル化されたタイム ゾーン情報を含む文字列そのものを、外部ファイル、アプリケーションに埋め込まれているリソース ファイル、レジストリなど、一部のストレージ メディアに格納することができます (カスタム タイム ゾーンに関する情報は、レジストリ内のシステムのタイム ゾーン キーとは別に保存する必要があることにご注意ください)。

この方法でシリアル化されたタイム ゾーン文字列を格納すると、タイム ゾーン作成ルーチンもアプリケーション自体から分離されます。 たとえば、タイム ゾーン作成ルーチンを実行して、アプリケーションが使用できる過去のタイム ゾーン情報が入ったデータ ファイルを作成できます。 その後、データ ファイルをアプリケーションと共にインストールすることができます。アプリケーションで必要になったときにこれを開いて、1 つまたは複数のタイム ゾーンを逆シリアル化できます。

埋め込みリソースを使用してシリアル化されたタイム ゾーン データを格納する例については、「[方法: 埋め込みリソースにタイム ゾーンを保存する](save-time-zones-to-an-embedded-resource.md)」および「[方法: 埋め込みリソースからタイム ゾーンを復元する](restore-time-zones-from-an-embedded-resource.md)」をご覧ください。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](index.md)
