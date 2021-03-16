---
title: 破壊的変更:BinaryFormatter.Deserialize によって例外の一部が再ラップされる
description: .NET 5 での破壊的変更について学習します。BinaryFormatter.Deserialize によって SerializationException 内の例外オブジェクトの一部が再ラップされます。
ms.date: 08/18/2020
ms.openlocfilehash: 8e357035908f34c6c5c77d2a0728ab213bdc791a
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256349"
---
# <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a><span data-ttu-id="76bb6-103">BinaryFormatter.Deserialize によって SerializationException の例外の一部が再ラップされる</span><span class="sxs-lookup"><span data-stu-id="76bb6-103">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>

<span data-ttu-id="76bb6-104"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> メソッドによって、<xref:System.Runtime.Serialization.SerializationException> 内の一部の例外オブジェクトが、例外を呼び出し元に伝達する前に再ラップされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="76bb6-104">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method now rewraps some exception objects inside a <xref:System.Runtime.Serialization.SerializationException> before propagating the exception back to the caller.</span></span>

## <a name="change-description"></a><span data-ttu-id="76bb6-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="76bb6-105">Change description</span></span>

<span data-ttu-id="76bb6-106">以前の <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> メソッドでは、<xref:System.ArgumentNullException> などの一部の任意の例外が、スタックの上の呼び出し元に伝達されることが可能でした。</span><span class="sxs-lookup"><span data-stu-id="76bb6-106">Previously, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method allowed some arbitrary exceptions, such as <xref:System.ArgumentNullException>, to propagate up the stack to its callers.</span></span>

<span data-ttu-id="76bb6-107">.NET 5 以降の <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> メソッドでは、無効な逆シリアル化操作によって発生した例外がより積極的にキャッチされ、<xref:System.Runtime.Serialization.SerializationException> にラップされます。</span><span class="sxs-lookup"><span data-stu-id="76bb6-107">In .NET 5 and later, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method more aggressively catches exceptions that occur due to invalid deserialization operations and wraps them in a <xref:System.Runtime.Serialization.SerializationException>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="76bb6-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="76bb6-108">Version introduced</span></span>

<span data-ttu-id="76bb6-109">5.0</span><span class="sxs-lookup"><span data-stu-id="76bb6-109">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="76bb6-110">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="76bb6-110">Recommended action</span></span>

<span data-ttu-id="76bb6-111">ほとんどの場合、お客様が何らかのアクションを実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="76bb6-111">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="76bb6-112">ただし、呼び出しサイトが、スローされる特定の例外に依存している場合は、次の例に示すように、外側の <xref:System.Runtime.Serialization.SerializationException> から例外のラップを解除できます。</span><span class="sxs-lookup"><span data-stu-id="76bb6-112">However, if your call site depends on a particular exception being thrown, you can unwrap the exception from the outer <xref:System.Runtime.Serialization.SerializationException>, as shown in the following example.</span></span>

```csharp
Stream inputStream = GetInputStream();
var formatter = new BinaryFormatter();

try
{
    object deserialized = formatter.Deserialize(inputStream);
}
catch (MyException myEx)
{
    // Handle 'myEx' here in case it was thrown directly.
}
catch (SerializationException serEx) when (serEx.InnerException is MyException myEx)
{
    // Handle 'myEx' here in case it was wrapped in SerializationException.
}
```

## <a name="affected-apis"></a><span data-ttu-id="76bb6-113">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="76bb6-113">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

### Category

Serialization

-->
