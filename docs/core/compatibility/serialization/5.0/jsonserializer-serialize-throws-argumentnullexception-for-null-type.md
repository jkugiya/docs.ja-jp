---
title: 破壊的変更:型パラメーターが null の場合にシリアル化によって例外がスローされる
description: .NET 5 での破壊的変更について学習します。型パラメーターに null が渡されるたびに、そのパラメーターを持つ JsonSerialize シリアル化メソッドによって例外がスローされるようになりました。
ms.date: 10/18/2020
ms.openlocfilehash: 81b3b754c11599eea435c750f1386fcaa2f0b54d
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256297"
---
# <a name="jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null"></a><span data-ttu-id="30e70-103">型パラメーターが null の場合に JsonSerializer.Serialize によって ArgumentNullException がスローされる</span><span class="sxs-lookup"><span data-stu-id="30e70-103">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>

<span data-ttu-id="30e70-104"><xref:System.Type> の型パラメーターに `null` が渡されるたびに、そのパラメーターを持つ <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>、<xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType>、<xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> のオーバーロードによって <xref:System.ArgumentNullException> がスローされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="30e70-104"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType>, and <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> overloads that have a parameter of type <xref:System.Type> now throw an <xref:System.ArgumentNullException> whenever `null` is passed for that parameter.</span></span>

## <a name="change-description"></a><span data-ttu-id="30e70-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="30e70-105">Change description</span></span>

<span data-ttu-id="30e70-106">.NET Core 3.1 では、`Type inputType` パラメーターに `null` が渡されると、<xref:System.Type> パラメーターを持つ <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>、<xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType>、<xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> のオーバーロードによって <xref:System.ArgumentNullException> がスローされますが、`Object value` パラメーターも `null` の場合はされません。</span><span class="sxs-lookup"><span data-stu-id="30e70-106">In .NET Core 3.1, the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType>, and <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> overloads that have a <xref:System.Type> parameter throw an <xref:System.ArgumentNullException> when `null` is passed for the `Type inputType` parameter, but not if the `Object value` parameter is also `null`.</span></span> <span data-ttu-id="30e70-107">.NET 5 以降では、`null` が <xref:System.Type> パラメーターに渡されると、これらのメソッドによって "*常に*" <xref:System.ArgumentNullException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="30e70-107">Starting in .NET 5, these methods *always* throw an <xref:System.ArgumentNullException> when `null` is passed for the <xref:System.Type> parameter.</span></span>

<span data-ttu-id="30e70-108">.NET Core 3.1 での動作:</span><span class="sxs-lookup"><span data-stu-id="30e70-108">Behavior in .NET Core 3.1:</span></span>

```csharp
// Returns a string with value "null".
JsonSerializer.Serialize(null, null);

// Returns a byte array with value "null".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

<span data-ttu-id="30e70-109">.NET 5 以降での動作:</span><span class="sxs-lookup"><span data-stu-id="30e70-109">Behavior in .NET 5 and later:</span></span>

```csharp
// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.Serialize(null, null);

// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

## <a name="version-introduced"></a><span data-ttu-id="30e70-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="30e70-110">Version introduced</span></span>

<span data-ttu-id="30e70-111">5.0</span><span class="sxs-lookup"><span data-stu-id="30e70-111">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="30e70-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="30e70-112">Reason for change</span></span>

<span data-ttu-id="30e70-113">`Type inputType` パラメーターに `null` を渡すことは許容されておらず、常に <xref:System.ArgumentNullException> をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="30e70-113">Passing in `null` for the `Type inputType` parameter is unacceptable and should always throw an <xref:System.ArgumentNullException>.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="30e70-114">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="30e70-114">Recommended action</span></span>

<span data-ttu-id="30e70-115">これらのメソッドの `Type inputType` パラメーターに `null` が渡されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="30e70-115">Make sure that you are not passing `null` for the `Type inputType` parameter of these methods.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="30e70-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="30e70-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)`
- `M:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`

### Category

Serialization

-->
