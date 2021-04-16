---
description: '詳細情報: ローカル システムで定義されているタイム ゾーンの検索'
title: ローカル システムで定義されているタイム ゾーンの検索
ms.date: 04/10/2017
helpviewer_keywords:
- time zones [.NET], local
- time zones [.NET], finding local system time zones
- time zone identifiers [.NET]
- local time zone access
- time zones [.NET], retrieving
- UTC times, finding local system time zones
- time zones [.NET], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
ms.openlocfilehash: 1b7a4d1962adac42b47cda42d4d1223c4b79852a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702640"
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a>ローカル システムで定義されているタイム ゾーンの検索

<xref:System.TimeZoneInfo> クラスは、パブリック コンストラクターを公開しません。 そのため、`new` キーワードを使用して新しい <xref:System.TimeZoneInfo> オブジェクトを作成することはできません。 <xref:System.TimeZoneInfo> オブジェクトをインスタンス化するには、代わりに、定義済みのタイム ゾーンの情報をレジストリから取得するか、カスタム タイム ゾーンを作成します。 このトピックでは、レジストリに格納されているデータからタイム ゾーンをインスタンス化する方法について説明します。 また、<xref:System.TimeZoneInfo> クラスの `static` (Visual Basic では `shared`) プロパティを使用すると、世界協定時刻 (UTC: Coordinated Universal Time) およびローカル タイム ゾーンにアクセスできます。

> [!NOTE]
> レジストリで定義されていないタイム ゾーンの場合は、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドのオーバーロードを呼び出すことによりカスタム タイム ゾーンを作成できます。 カスタム タイム ゾーンを作成する方法については、「[方法: 調整規則のないタイム ゾーンを作成する](create-time-zones-without-adjustment-rules.md)」と「[方法: 調整規則のあるタイム ゾーンを作成する](create-time-zones-with-adjustment-rules.md)」の各トピックを参照してください。 さらに、<xref:System.TimeZoneInfo.FromSerializedString%2A> メソッドを使用して、シリアル化された文字列から復元することにより、<xref:System.TimeZoneInfo> オブジェクトをインスタンス化することもできます。 <xref:System.TimeZoneInfo> オブジェクトのシリアル化と逆シリアル化については、「[埋め込みリソースにタイム ゾーンを保存する](save-time-zones-to-an-embedded-resource.md)」と「[方法: 埋め込みリソースからタイム ゾーンを復元する](restore-time-zones-from-an-embedded-resource.md)」の各トピックを参照してください。

## <a name="accessing-individual-time-zones"></a>個別のタイム ゾーンへのアクセス

<xref:System.TimeZoneInfo> クラスには、UTC 時刻とローカル タイム ゾーンを表す 2 つの定義済みタイム ゾーン オブジェクトがあります。 これらは、それぞれ <xref:System.TimeZoneInfo.Utc%2A> プロパティと <xref:System.TimeZoneInfo.Local%2A> プロパティから取得できます。 UTC またはローカル タイム ゾーンにアクセスする方法については、「[方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする](access-utc-and-local.md)」を参照してください。

また、レジストリで定義されているタイム ゾーンを表す <xref:System.TimeZoneInfo> オブジェクトをインスタンス化することもできます。 特定のタイム ゾーン オブジェクトをインスタンス化する方法については、「[方法: TimeZoneInfo オブジェクトをインスタンス化する](instantiate-time-zone-info.md)」を参照してください。

## <a name="time-zone-identifiers"></a>タイム ゾーン ID

タイム ゾーン ID は、タイム ゾーンを一意に識別するキー フィールドです。 ほとんどのキーは比較的短いですが、タイム ゾーン ID はいくぶん長めです。 ほとんどの場合、ID の値は、タイム ゾーンの標準時刻の名前を表すために使用される <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> プロパティに対応します。 ただし、例外もあります。 有効な ID を確実に指定する最良の方法は、システムで使用できるタイム ゾーンを列挙し、それに対応するタイム ゾーン ID を記録することです。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](index.md)
- [方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする](access-utc-and-local.md)
- [方法: TimeZoneInfo オブジェクトをインスタンス化する](instantiate-time-zone-info.md)
- [タイム ゾーン間での時刻の変換](converting-between-time-zones.md)
