---
title: '破壊的変更: インスタンスが既に存在する場合、CreateCounterSetInstance が InvalidOperationException をスローするようになった'
description: Core .NET ライブラリでの .NET 5 に関する破壊的変更について学習します。この変更により、CounterSet.CreateCounterSetInstance は、カウンターが既に存在する場合に別の例外をスローします。
ms.date: 11/01/2020
ms.openlocfilehash: bf59677a85538bc4992c589f8642ab4a0fce54ac
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257571"
---
# <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a>インスタンスが既に存在する場合、CounterSet.CreateCounterSetInstance は InvalidOperationException をスローするようになった

.NET 5 以降では、カウンター セットが既に存在する場合、<xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> は <xref:System.ArgumentException> ではなく <xref:System.InvalidOperationException> をスローします。

## <a name="change-description"></a>変更の説明

.NET Framework と .NET Core 1.0 から 3.1 では、<xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> を呼び出すことによって、カウンター セットのインスタンスを作成できます。 ただし、カウンター セットが既に存在する場合、このメソッドは <xref:System.ArgumentException> 例外をスローします。

.NET 5 以降のバージョンでは、<xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> を呼び出したときにカウンター セットが存在すると、<xref:System.InvalidOperationException> 例外がスローされます。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

<xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> を呼び出すときにアプリで <xref:System.ArgumentException> 例外をキャッチする場合は、<xref:System.InvalidOperationException> 例外もキャッチすることを検討してください。

> [!NOTE]
> <xref:System.ArgumentException> 例外をキャッチすることは推奨されません。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
