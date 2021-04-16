---
description: '詳細情報: 日付と時刻を使用した算術演算の実行'
title: 日付と時刻を使用した算術演算の実行
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET], arithmetic operations
- dates [.NET], arithmetic operations
- time zones [.NET], arithmetic operations
- arithmetic operations [.NET], dates and times
- dates [.NET], comparing
- DateTime structure, arithmetic operations
- DateTimeOffset structure, arithmetic operations
ms.assetid: 87c7ddf2-f15e-48af-8602-b3642237e6d0
ms.openlocfilehash: 7b39a6dec3abc2206c8eef7566f74aab6614aae6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702562"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>日付と時刻を使用した算術演算の実行

<xref:System.DateTime> および <xref:System.DateTimeOffset> 構造体には、その値に対して算術演算を実行するメンバーが用意されていますが、算術演算の結果は大きく異なります。 このトピックでは、それらの相違点を検討し、日付と時刻のデータがどの程度タイム ゾーンに対応しているかを明らかにして、日付と時刻のデータを使用してタイム ゾーンに完全に対応した操作を実行する方法について説明します。

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>DateTime 値を使用した比較および算術演算

<xref:System.DateTime.Kind%2A?displayProperty=nameWithType> プロパティでは、<xref:System.DateTimeKind> 値を日付と時刻に割り当てて、その日付と時刻が現地時刻、協定世界時 (UTC)、またはタイム ゾーンが指定されていない時刻のどれを表すかを示すことができます。 ただし、この制限付きのタイム ゾーン情報は、<xref:System.DateTimeKind> 値に対して比較操作を行うか、日付と時刻の算術演算を実行するときには無視されます。 次の例では、現在の現地時刻と現在の UTC 時刻を比較することで、この問題を示しています。

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

<xref:System.DateTime.CompareTo%28System.DateTime%29> メソッドは、現地時刻が UTC 時刻より早い (より小さい) という結果を出力しており、減算の操作は、UTC と米国の太平洋標準時ゾーンにあるシステムの現地時刻との差が7 時間であることを示しています。 しかし、これら 2 つの値は、ある特定の時点を異なる表現で示したものであるため、この場合、時間差の原因は、UTC を基準としたローカル タイム ゾーンのオフセットにあることは明らかです。

一般的に、<xref:System.DateTime.Kind%2A?displayProperty=nameWithType> プロパティは、<xref:System.DateTime.Kind> の比較および算術メソッドによって返される結果に影響を与えません (2 つの同じ時点の比較結果が示すとおり)。ただし、その結果の解釈には影響を与えることがあります。 次に例を示します。

- 算術演算の実行対象となる 2 つの日付と時刻の値の <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> プロパティが両方とも <xref:System.DateTimeKind> である場合、実行結果には、2 つの値の実際の時間差が反映されます。 同様に、そのような 2 つの日付と時刻の値を比較した結果には、2 つの時間の関係が正確に反映されます。

- 算術演算または比較操作の実行対象となる 2 つの日付と時刻の値の <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> プロパティが両方とも <xref:System.DateTimeKind> であるか、または 2 つの日付と時刻の値の <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> プロパティ値が異なる場合、実行結果には、2 つの値の間の時刻差が反映されます。

- ローカルの日付と時刻の値に対する算術演算または比較操作では、特定の値があいまいであるかや、無効であるかどうかは考慮されず、ローカル タイム ゾーンでの夏時間の開始や終了による調整規則の影響についても考慮されません。

- UTC と現地時刻の差を比較または計算する操作の結果には、UTC を基準としたローカル タイム ゾーンのオフセットに等しい時間差が含まれます。

- タイム ゾーンが指定されていない時刻と UTC または現地時刻との差を比較または計算する操作では、単純な時刻差が反映されます。 タイム ゾーンの違いは考慮されず、結果にはタイム ゾーン調整規則の適用が反映されません。

- タイム ゾーンが指定されていない 2 つの時刻の差を比較または計算する操作の結果には、2 つの異なるタイム ゾーンの時刻の差を反映した未知の時間差が含まれる場合があります。

多くの場合、タイム ゾーンの違いは日付と時刻の計算には影響しないか (いくつかの詳細については、「[DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け](choosing-between-datetime.md)」を参照してください)、または日付と時刻のデータのコンテキストによって比較操作や算術演算の意味が規定されます。

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>DateTimeOffset 値を使用した比較および算術演算

<xref:System.DateTimeOffset> 値には、日付と時刻だけでなく、UTC を基準としてその日付と時刻を明確に定義するオフセットが含まれています。 このため、<xref:System.DateTimeOffset> 値とはいくらか異なる等価性を規定できるようになります。 <xref:System.DateTime> 値が等しくなるのは日付と時刻の値が同じ場合ですが、<xref:System.DateTimeOffset> 値が等しくなるのは、両方の値が同じ時点を表す場合です。 これにより、2 つの日付と時刻の間隔を決定する比較操作やほとんどの算術演算では、<xref:System.DateTimeOffset> 値を使用すると、より正確な結果を得ることができ、結果を正しく解釈する手間を減らすことができます。 次の例では、現地時刻と UTC の <xref:System.DateTimeOffset> 値を比較した前の例に <xref:System.DateTimeOffset> を使用して、動作の違いを示しています。

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

この例では、<xref:System.DateTimeOffset.CompareTo%2A> メソッドが、現在の現地時刻と現在の UTC 時刻が等しいことを示しており、<xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> 値を減算することで、2 つの時刻の差が <xref:System.TimeSpan.Zero?displayProperty=nameWithType> であることを示しています。

日付と時刻の算術演算に <xref:System.DateTimeOffset> 値を使用する際の主な制限は、<xref:System.DateTimeOffset> 値はタイム ゾーンに一部対応していますが、完全対応しているわけではないことです。 <xref:System.DateTimeOffset> 値のオフセットには、<xref:System.DateTimeOffset> 変数に最初に値が割り当てられたときに UTC を基準としたタイム ゾーンのオフセットが反映されますが、その後は、タイム ゾーンと関連付けられなくなります。 特定可能な時刻との直接の関連付けは失われるため、日付と時刻の間隔に対して加算や減算を行っても、タイム ゾーンの調整規則は考慮されません。

たとえば、米国の中部標準時のタイム ゾーンが夏時間に移行するのは、 発生します。 つまり、中部標準時の 2008 年 3 月 9 日の午前 1 時 30 分に 2 時間 30 分の間隔を加算すると、日付と時刻は 2008 年 3 月 9 日の 発生します。 しかし、次の例に示すように、加算の結果は 2008 年 3 月 9 日の 発生します。 この操作の結果は正しい時点を表していますが、目的のタイム ゾーンの時刻ではありません (つまり、予想されるタイム ゾーンのオフセットが適用されていません)。

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>タイム ゾーンの時刻を使用した算術演算

<xref:System.TimeZoneInfo> クラスには、タイム ゾーンどうしの間で時刻を変換するときに調整を自動的に適用する多数の変換メソッドが含まれています。 これらには、次のものが含まれます。

- <xref:System.TimeZoneInfo.ConvertTime%2A> メソッドと <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> メソッド。2 つのタイム ゾーン間で時刻を変換します。

- <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> メソッドと <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> メソッド。特定のタイム ゾーンの時刻を UTC に変換するか、UTC を特定のタイム ゾーンの時刻に変換します。

詳細については、「[タイム ゾーン間での時刻の変換](converting-between-time-zones.md)」を参照してください。

<xref:System.TimeZoneInfo> クラスには、日付と時刻の算術演算を実行するときに調整規則を自動的に適用するメソッドは用意されていません。 ただし、あるタイム ゾーンの時刻を UTC に変換してから算術演算を実行し、その後 UTC から元のタイム ゾーンの時刻に再変換することで、調整規則を適用したときと同じ結果を得ることができます。 詳細については、「[方法: 日付と時刻の演算でタイム ゾーンを使用する](use-time-zones-in-arithmetic.md)」を参照してください。

たとえば、次のコードは、2008 年 3 月 9 日の午前 2 時に 2 時間 30 分を加算する 発生します。 ただし、中部標準時を UTC に変換した後に日付と時刻の算術演算を実行し、その結果を UTC から中部標準時に変換するため、得られた時刻は中部標準時タイム ゾーンの夏時間への移行を反映しています。

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](index.md)
- [方法: 日付と時刻の演算でタイム ゾーンを使用する](use-time-zones-in-arithmetic.md)
