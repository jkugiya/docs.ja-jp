---
title: 破壊的変更:BinaryFormatter シリアル化メソッドが古い形式になり、ASP.NET アプリでは使用不可に
description: Core .NET ライブラリにおける .NET 5 の破壊的変更について学習します。BinaryFormatter、Formatter、および IFormatter におけるシリアル化と逆シリアル化メソッドが古いものになりました。
ms.date: 11/01/2020
ms.openlocfilehash: 8c31a95683526ba394101d449b5ae3328f57f3c3
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257662"
---
# <a name="binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps"></a>BinaryFormatter シリアル化メソッドが古い形式になり、ASP.NET アプリでは使用不可に

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>、<xref:System.Runtime.Serialization.Formatter>、および <xref:System.Runtime.Serialization.IFormatter> の `Serialize` と `Deserialize` のメソッドが古いと見なされ、警告が示されるようになりました。 また、ASP.NET アプリでは、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> のシリアル化が既定で禁止されます。

## <a name="change-description"></a>変更の説明

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> の[セキュリティ脆弱性](../../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities)により、次のメソッドは古いと見なされ、ID `SYSLIB0011` のコンパイル時警告が生成されるようになりました。 また、ASP.NET Core 5.0 以降のアプリでは、Web アプリによって <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 機能が再有効化されていない限り、<xref:System.NotSupportedException> がスローされます。

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>

次のシリアル化メソッドも古いと見なされ、警告 `SYSLIB0011` が生成されますが、動作変更はありません。

- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="reason-for-change"></a>変更理由

.NET エコシステム内における <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> の使用を段階的に縮小するための取り組みの一環として、これらのメソッドが古い形式としてマークされています。

## <a name="recommended-action"></a>推奨アクション

- コードでの <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> の使用を停止してください。 代わりに、<xref:System.Text.Json.JsonSerializer> または <xref:System.Xml.Serialization.XmlSerializer> の使用を検討してください。 詳しくは、「[BinaryFormatter セキュリティ ガイド](../../../../standard/serialization/binaryformatter-security-guide.md)」をご覧ください。

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> のコンパイル時の警告 (`SYSLIB0011`) を一時的に抑制することができます。 このオプションを選択する前に、リスクについてコードを十分に評価することをお勧めします。 警告を抑制する最も簡単な方法は、個々の呼び出しサイトを `#pragma` ディレクティブで囲むことです。

  ```csharp
  // Now read the purchase order back from disk
  using (var readStream = new FileStream("myfile.bin", FileMode.Open))
  {
      var formatter = new BinaryFormatter();
  #pragma warning disable SYSLIB0011
      return (PurchaseOrder)formatter.Deserialize(readStream);
  #pragma warning restore SYSLIB0011
  }
  ```

  また、プロジェクト ファイルで警告を抑制することもできます。

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "BinaryFormatter is obsolete" warnings for entire project -->
    <NoWarn>$(NoWarn);SYSLIB0011</NoWarn>
  </PropertyGroup>
  ```

  プロジェクト ファイルで警告を抑制すると、プロジェクト内のすべてのコード ファイルに対して警告が抑制されます。 `SYSLIB0011` を抑制しても、他の古い API の使用によって発生した警告は抑制されません。

- ASP.NET アプリで引き続き <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> を使用する場合は、プロジェクト ファイルで再有効化することができます。 ただし、そうしないことを強くお勧めします。 詳しくは、「[BinaryFormatter セキュリティ ガイド](../../../../standard/serialization/binaryformatter-security-guide.md)」をご覧ください。

  ```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Warning: Setting the following switch is *NOT* recommended in web apps. -->
    <EnableUnsafeBinaryFormatterSerialization>true</EnableUnsafeBinaryFormatterSerialization>
  </PropertyGroup>
  ```

推奨される操作の詳細については、「[BinaryFormatter の廃止と無効化に関するエラーの解決](../../../../standard/serialization/binaryformatter-security-guide.md)」をご覧ください。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- ASP.NET Core

### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize`
- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`
- `M:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)`

-->
