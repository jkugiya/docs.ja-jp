---
description: '詳細情報: 方法: 調整規則のあるタイム ゾーンを作成する'
title: '方法: 調整規則のあるタイム ゾーンを作成する'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], creating
- time zones [.NET], and adjustment rules
- adjustment rule [.NET]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
ms.openlocfilehash: d581d01d9f9386adf99079f4f8f8e09585b06848
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702770"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>方法: 調整規則のあるタイム ゾーンを作成する

アプリケーションで必要とされる正確なタイム ゾーン情報が、いくつかの理由で特定のシステムに存在しない場合があります。

- タイム ゾーンがローカル システムのレジストリに定義されていない。

- レジストリにあるタイム ゾーンに関するデータが変更または削除された。

- タイム ゾーンに、特定の期間のタイム ゾーン調整の履歴に関する正確な情報がない。

このような場合は、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを呼び出して、アプリケーションで必要とされるタイム ゾーンを定義できます。 このメソッドのオーバーロードを使用して、調整規則の有無に関係なくタイム ゾーンを作成できます。 タイム ゾーンで夏時間がサポートされている場合は、固定または浮動調整規則のいずれかを使用して調整を定義できます (これらの用語の定義については、「[タイム ゾーンの概要](time-zone-overview.md)」の「タイム ゾーンの用語」セクションをご覧ください)。

> [!IMPORTANT]
> <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを呼び出すことによって作成されたカスタム タイム ゾーンは、レジストリには追加されません。 代わりに、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッド呼び出しによって返されるオブジェクト参照を通してのみ、これらにアクセスできます。

このトピックでは、調整規則のあるタイム ゾーンを作成する方法について説明します。 夏時間調整規則をサポートしないタイム ゾーンを作成するには、「[方法: 調整規則のないタイム ゾーンを作成する](create-time-zones-without-adjustment-rules.md)」をご覧ください。

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>浮動調整規則のあるタイム ゾーンを作成する方法

1. 調整のたびに (つまり、特定の期間にわたって標準時との間で切り替えるたびに)、次の手順を実行します。

    1. タイム ゾーン調整の切り替え開始時刻を定義します。

       <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> メソッドを呼び出して、切り替える時刻を定義する <xref:System.DateTime> 値、切り替える月を定義する整数値、切り替えが発生する週を定義する整数値、切り替えが発生する曜日を定義する <xref:System.DayOfWeek> 値を渡す必要があります。 このメソッドの呼び出しで、<xref:System.TimeZoneInfo.TransitionTime> オブジェクトがインスタンス化されます。

    2. タイム ゾーン調整の切り替え終了時刻を定義します。 このために、もう一度 <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> メソッドを呼び出すことが必要です。 このメソッドの呼び出しで、2 番目の <xref:System.TimeZoneInfo.TransitionTime> オブジェクトがインスタンス化されます。

    3. <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> メソッドを呼び出し、調整の有効期間の開始および終了日、切り替えにかかる時間を定義する <xref:System.TimeSpan> オブジェクト、夏時間の開始と終了の切り替えが行われるタイミングを定義する 2 つの <xref:System.TimeZoneInfo.TransitionTime> オブジェクトを渡します。 このメソッドの呼び出しで、<xref:System.TimeZoneInfo.AdjustmentRule> オブジェクトがインスタンス化されます。

    4. <xref:System.TimeZoneInfo.AdjustmentRule> オブジェクトを <xref:System.TimeZoneInfo.AdjustmentRule> オブジェクトの配列に割り当てます。

2. タイム ゾーンの表示名を定義します。 表示名はごく標準的な形式に従います。つまり、協定世界時 (UTC) からタイム ゾーンまでのオフセットをかっこで囲み、その後にタイム ゾーン、タイム ゾーンの 1 つまたは複数の都市、またはタイム ゾーンの 1 つまたは複数の国または地域を識別する文字列を続けます。

3. タイム ゾーンの標準時の名前を定義します。 通常、この文字列はタイム ゾーンの識別子としても使用されます。

4. タイム ゾーンの夏時間の名前を定義します。

5. タイム ゾーンの標準名とは異なる識別子を使用する場合は、タイム ゾーンの識別子を定義します。

6. UTC からこのタイム ゾーンまでのオフセットを定義する <xref:System.TimeSpan> オブジェクトをインスタンス化します。 時刻が UTC より後のタイム ゾーンは正のオフセットになります。 時刻が UTC より前のタイム ゾーンは負のオフセットになります。

7. 新しいタイム ゾーンをインスタンス化するには、<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> メソッドを呼び出します。

## <a name="example"></a>例

次の例では、1918 年から現在に至るまでのさまざまな時間間隔の調整規則を含む米国の中部標準時のタイム ゾーンを定義します。

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

この例で作成されるタイム ゾーンには、複数の調整規則があります。 調整規則の有効期間の開始および終了日が、別の調整規則の日付と重複しないように注意する必要があります。 重複がある場合は、<xref:System.InvalidTimeZoneException> がスローされます。

浮動調整規則では、値 5 が <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> メソッドの `week` パラメーターに渡されます。これは、特定の月の最終週に切り替えが発生することを示します。

<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> メソッド呼び出しで使用される <xref:System.TimeZoneInfo.AdjustmentRule> オブジェクトの配列を作成する場合、コードはタイム ゾーンに対して作成される調整の数に必要なサイズに配列を初期化できます。 代わりに、このコード例では <xref:System.Collections.Generic.List%601.Add%2A> メソッドを呼び出して、<xref:System.TimeZoneInfo.AdjustmentRule> オブジェクトのジェネリック <xref:System.Collections.Generic.List%601> コレクションに各調整規則を追加します。 次に、このコードでは <xref:System.Collections.Generic.List%601.CopyTo%2A> メソッドを呼び出して、このコレクションのメンバーを配列にコピーします。

また、この例では、<xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> メソッドを使用して、固定日付の調整を定義します。 これは、<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> メソッドの呼び出しに似ていますが、切り替えの時刻、月、日付のパラメーターのみが必要です。

この例は、次のようなコードを使用してテストできます。

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

- 次の名前空間がインポートされていること。

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](index.md)
- [タイム ゾーンの概要](time-zone-overview.md)
- [方法: 調整規則のないタイム ゾーンを作成する](create-time-zones-without-adjustment-rules.md)
