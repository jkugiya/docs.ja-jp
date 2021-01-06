---
title: '破壊的変更: インスタンスが既に存在する場合、CreateCounterSetInstance が InvalidOperationException をスローするようになった'
description: Core .NET ライブラリでの .NET 5.0 に関する破壊的変更について学習します。この変更により、CounterSet.CreateCounterSetInstance は、カウンターが既に存在する場合に別の例外をスローします。
ms.date: 11/01/2020
ms.openlocfilehash: 28042690b71f9b86e4e54748ec75467bbe232684
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759837"
---
# <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a><span data-ttu-id="8b6ae-103">インスタンスが既に存在する場合、CounterSet.CreateCounterSetInstance は InvalidOperationException をスローするようになった</span><span class="sxs-lookup"><span data-stu-id="8b6ae-103">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exists</span></span>

<span data-ttu-id="8b6ae-104">.NET 5.0 以降では、カウンター セットが既に存在する場合、<xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> は <xref:System.ArgumentException> ではなく <xref:System.InvalidOperationException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-104">Starting in .NET 5.0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> throws an <xref:System.InvalidOperationException> instead of an <xref:System.ArgumentException> if the counter set already exists.</span></span>

## <a name="change-description"></a><span data-ttu-id="8b6ae-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="8b6ae-105">Change description</span></span>

<span data-ttu-id="8b6ae-106">.NET Framework と .NET Core 1.0 から 3.1 では、<xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> を呼び出すことによって、カウンター セットのインスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-106">In .NET Framework and .NET Core 1.0 to 3.1, you can create an instance of the counter set by calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>.</span></span> <span data-ttu-id="8b6ae-107">ただし、カウンター セットが既に存在する場合、このメソッドは <xref:System.ArgumentException> 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-107">However, if the counter set already exists, the method throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="8b6ae-108">.NET 5.0 以降のバージョンでは、<xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> を呼び出したときにカウンター セットが存在すると、<xref:System.InvalidOperationException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-108">In .NET 5.0 and later versions, when you call <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> and the counter set exists, an <xref:System.InvalidOperationException> exception is thrown.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="8b6ae-109">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="8b6ae-109">Version introduced</span></span>

<span data-ttu-id="8b6ae-110">5.0</span><span class="sxs-lookup"><span data-stu-id="8b6ae-110">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="8b6ae-111">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="8b6ae-111">Recommended action</span></span>

<span data-ttu-id="8b6ae-112"><xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> を呼び出すときにアプリで <xref:System.ArgumentException> 例外をキャッチする場合は、<xref:System.InvalidOperationException> 例外もキャッチすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-112">If you catch <xref:System.ArgumentException> exceptions in your app when calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>, consider also catching <xref:System.InvalidOperationException> exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="8b6ae-113"><xref:System.ArgumentException> 例外をキャッチすることは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-113">Catching <xref:System.ArgumentException> exceptions is not recommended.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="8b6ae-114">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="8b6ae-114">Affected APIs</span></span>

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->