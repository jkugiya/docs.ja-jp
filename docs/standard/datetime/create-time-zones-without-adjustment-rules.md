---
description: '詳細情報: 方法: 調整規則のないタイム ゾーンを作成する'
title: '方法: 調整規則のないタイム ゾーンを作成する'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], adjustment rule
- time zones [.NET], creating
- adjustment rule [.NET]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
ms.openlocfilehash: c2d1f2d2ea21c53c6a3b41603be4f31ec5442a30
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702731"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>方法: 調整規則のないタイム ゾーンを作成する

アプリケーションで必要とされる正確なタイム ゾーン情報が、いくつかの理由で特定のシステムに存在しない場合があります。

- タイム ゾーンがローカル システムのレジストリに定義されていない。

- レジストリにあるタイム ゾーンに関するデータが変更または削除された。

- タイム ゾーンは存在するものの、特定の期間のタイム ゾーン調整の履歴に関する正確な情報がない。

このような場合は、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを呼び出して、アプリケーションで必要とされるタイム ゾーンを定義できます。 このメソッドのオーバーロードを使用して、調整規則の有無に関係なくタイム ゾーンを作成できます。 タイム ゾーンで夏時間がサポートされている場合は、固定または浮動調整規則のいずれかを使用して調整を定義できます (これらの用語の定義については、「[タイム ゾーンの概要](time-zone-overview.md)」の「タイム ゾーンの用語」セクションをご覧ください)。

> [!IMPORTANT]
> <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを呼び出すことによって作成されたカスタム タイム ゾーンは、レジストリには追加されません。 代わりに、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッド呼び出しによって返されるオブジェクト参照を通してのみ、これらにアクセスできます。

このトピックでは、調整規則のないタイム ゾーンを作成する方法について説明します。 夏時間調整規則をサポートするタイム ゾーンを作成するには、「[方法: 調整規則のあるタイム ゾーンを作成する](create-time-zones-with-adjustment-rules.md)」をご覧ください。

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>調整規則のないタイム ゾーンを作成する方法

1. タイム ゾーンの表示名を定義します。

   表示名はごく標準的な形式に従います。つまり、協定世界時 (UTC) からタイム ゾーンまでのオフセットをかっこで囲み、その後にタイム ゾーン、タイム ゾーンの 1 つまたは複数の都市、またはタイム ゾーンの 1 つまたは複数の国または地域を識別する文字列を続けます。

2. タイム ゾーンの標準時の名前を定義します。 通常、この文字列はタイム ゾーンの識別子としても使用されます。

3. タイム ゾーンの標準名とは異なる識別子を使用する場合は、タイム ゾーンの識別子を定義します。

4. UTC からこのタイム ゾーンまでのオフセットを定義する <xref:System.TimeSpan> オブジェクトをインスタンス化します。 時刻が UTC より後のタイム ゾーンは正のオフセットになります。 時刻が UTC より前のタイム ゾーンは負のオフセットになります。

5. 新しいタイム ゾーンをインスタンス化するには、<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> メソッドを呼び出します。

## <a name="example"></a>例

次の例では、調整規則のない南極のモーソン基地のカスタム タイム ゾーンを定義します。

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<xref:System.TimeZoneInfo.DisplayName%2A> プロパティに割り当てられた文字列は、標準的な形式に従っています。つまり、UTC からタイム ゾーンまでのオフセットの後にタイム ゾーンのわかりやすい説明が続きます。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

- 次の名前空間がインポートされていること。

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](index.md)
- [タイム ゾーンの概要](time-zone-overview.md)
- [方法: 調整規則のあるタイム ゾーンを作成する](create-time-zones-with-adjustment-rules.md)
