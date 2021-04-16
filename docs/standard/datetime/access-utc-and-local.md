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
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする

<xref:System.TimeZoneInfo> クラスに用意されている <xref:System.TimeZoneInfo.Utc%2A> および <xref:System.TimeZoneInfo.Local%2A> という 2 つのプロパティを使用すると、コードから定義済みのタイム ゾーン オブジェクトにアクセスできます。 このトピックでは、これらのプロパティから返される <xref:System.TimeZoneInfo> オブジェクトにアクセスする方法について説明します。

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>世界協定時刻 (UTC) の TimeZoneInfo オブジェクトにアクセスするには

1. `static` (Visual Basic では `Shared`) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> プロパティを使用して、協定世界時にアクセスします。

2. プロパティから返された <xref:System.TimeZoneInfo> オブジェクトをオブジェクト変数に割り当てるのではなく、そのまま <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> プロパティを使用して協定世界時にアクセスします。

### <a name="to-access-the-local-time-zone"></a>ローカル タイム ゾーンにアクセスするには

1. `static` (Visual Basic では `Shared`) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> プロパティを使用して、ローカル システム タイム ゾーンにアクセスします。

2. プロパティから返された <xref:System.TimeZoneInfo> オブジェクトをオブジェクト変数に割り当てるのではなく、そのまま <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> プロパティを使用してローカル タイム ゾーンにアクセスします。

## <a name="example"></a>例

次のコードでは、<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> および <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> プロパティを使用して、米国およびカナダ東部標準時タイム ゾーンの時刻を変換し、コンソールにタイム ゾーンの名前を表示します。

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

ローカル タイム ゾーンにアクセスする場合は、ローカル タイム ゾーンを <xref:System.TimeZoneInfo> オブジェクト変数に割り当てることはせず、常に <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> プロパティをお使いください。 同様に、協定世界時にアクセスする場合は、UTC ゾーンを <xref:System.TimeZoneInfo> オブジェクト変数に割り当てることはせず、常に <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> プロパティをお使いください。 これにより、<xref:System.TimeZoneInfo> メソッド呼び出しによって <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> オブジェクト変数が無効になるのを防ぐことができます。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

- `using` ステートメント (C# コードでは必須) を使用して <xref:System> 名前空間がインポートされること。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](index.md)
- [ローカル システムで定義されているタイム ゾーンの検索](finding-the-time-zones-on-local-system.md)
- [方法: TimeZoneInfo オブジェクトをインスタンス化する](instantiate-time-zone-info.md)
