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
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>方法: TimeZoneInfo オブジェクトをインスタンス化する

<xref:System.TimeZoneInfo> オブジェクトをインスタンス化する最も一般的な方法は、レジストリからオブジェクトに関する情報を取得することです。 このトピックでは、ローカル システムのレジストリから <xref:System.TimeZoneInfo> オブジェクトをインスタンス化する方法について説明します。

### <a name="to-instantiate-a-timezoneinfo-object"></a>TimeZoneInfo オブジェクトをインスタンス化するには

1. <xref:System.TimeZoneInfo> オブジェクトを宣言します。

2. `static` (Visual Basic では`Shared` ) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> メソッドを呼び出します。

3. メソッドによってスローされる例外 (特に、タイム ゾーンがレジストリで定義されていない場合にスローされる <xref:System.TimeZoneNotFoundException> ) を処理します。

## <a name="example"></a>例

次のコードでは、東部標準時のタイム ゾーンを表す <xref:System.TimeZoneInfo> オブジェクトを取得し、現地時刻に対応する東部標準時の時刻を表示します。

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> メソッドの唯一のパラメーターは、取得するタイム ゾーンの識別子です。これは、オブジェクトの <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> プロパティに対応します。 タイム ゾーン ID は、タイム ゾーンを一意に識別するキー フィールドです。 ほとんどのキーは比較的短いですが、タイム ゾーン ID はいくぶん長めです。 ほとんどの場合、ID の値は、タイム ゾーンの標準時刻の名前を表すために使用される <xref:System.TimeZoneInfo.StandardName%2A> オブジェクトの <xref:System.TimeZoneInfo> プロパティに対応します。 ただし、例外もあります。 有効な識別子を確実に指定する最良の方法は、システムで使用できるタイム ゾーンを列挙し、対応するタイム ゾーン識別子を記録しておくことです。 この具体例については、「 [How to: Enumerate time zones present on a computer](enumerate-time-zones.md)」を参照してください。 [Finding the time zones defined on a local system](finding-the-time-zones-on-local-system.md) トピックにも、選択したタイム ゾーン識別子の一覧があります。

タイム ゾーンが見つかると、メソッドは <xref:System.TimeZoneInfo> オブジェクトを返します。 タイム ゾーンが見つからない場合、メソッドから <xref:System.TimeZoneNotFoundException>がスローされます。 タイム ゾーンが見つかっても、そのデータが破損しているか不完全な場合には、メソッドから <xref:System.InvalidTimeZoneException>がスローされます。

アプリケーションが依存するタイム ゾーンが必ず存在していなければならない場合は、最初に <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> メソッドを呼び出して、レジストリからタイム ゾーンの情報を取得する必要があります。 メソッドの呼び出しが失敗した場合は、例外ハンドラーで、タイム ゾーンの新しいインスタンスを作成するか、シリアル化された <xref:System.TimeZoneInfo> オブジェクトを逆シリアル化してインスタンスを作成し直す必要があります。 例については、「[方法: 埋め込みリソースからタイム ゾーンを復元する](restore-time-zones-from-an-embedded-resource.md)」をご覧ください。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](index.md)
- [ローカル システムで定義されているタイム ゾーンの検索](finding-the-time-zones-on-local-system.md)
- [方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする](access-utc-and-local.md)
