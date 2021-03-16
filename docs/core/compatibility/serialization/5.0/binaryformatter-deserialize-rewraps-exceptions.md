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
# <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a>BinaryFormatter.Deserialize によって SerializationException の例外の一部が再ラップされる

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> メソッドによって、<xref:System.Runtime.Serialization.SerializationException> 内の一部の例外オブジェクトが、例外を呼び出し元に伝達する前に再ラップされるようになりました。

## <a name="change-description"></a>変更の説明

以前の <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> メソッドでは、<xref:System.ArgumentNullException> などの一部の任意の例外が、スタックの上の呼び出し元に伝達されることが可能でした。

.NET 5 以降の <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> メソッドでは、無効な逆シリアル化操作によって発生した例外がより積極的にキャッチされ、<xref:System.Runtime.Serialization.SerializationException> にラップされます。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

ほとんどの場合、お客様が何らかのアクションを実行する必要はありません。 ただし、呼び出しサイトが、スローされる特定の例外に依存している場合は、次の例に示すように、外側の <xref:System.Runtime.Serialization.SerializationException> から例外のラップを解除できます。

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

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

### Category

Serialization

-->
