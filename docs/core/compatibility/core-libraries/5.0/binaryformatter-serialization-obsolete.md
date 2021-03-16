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
# <a name="binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps"></a><span data-ttu-id="16e83-103">BinaryFormatter シリアル化メソッドが古い形式になり、ASP.NET アプリでは使用不可に</span><span class="sxs-lookup"><span data-stu-id="16e83-103">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>

<span data-ttu-id="16e83-104"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>、<xref:System.Runtime.Serialization.Formatter>、および <xref:System.Runtime.Serialization.IFormatter> の `Serialize` と `Deserialize` のメソッドが古いと見なされ、警告が示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="16e83-104">`Serialize` and `Deserialize` methods on <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, <xref:System.Runtime.Serialization.Formatter>, and <xref:System.Runtime.Serialization.IFormatter> are now obsolete as warning.</span></span> <span data-ttu-id="16e83-105">また、ASP.NET アプリでは、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> のシリアル化が既定で禁止されます。</span><span class="sxs-lookup"><span data-stu-id="16e83-105">Additionally, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is prohibited by default for ASP.NET apps.</span></span>

## <a name="change-description"></a><span data-ttu-id="16e83-106">変更の説明</span><span class="sxs-lookup"><span data-stu-id="16e83-106">Change description</span></span>

<span data-ttu-id="16e83-107"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> の[セキュリティ脆弱性](../../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities)により、次のメソッドは古いと見なされ、ID `SYSLIB0011` のコンパイル時警告が生成されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="16e83-107">Due to [security vulnerabilities](../../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) in <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, the following methods are now obsolete and produce a compile-time warning with ID `SYSLIB0011`.</span></span> <span data-ttu-id="16e83-108">また、ASP.NET Core 5.0 以降のアプリでは、Web アプリによって <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 機能が再有効化されていない限り、<xref:System.NotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="16e83-108">Additionally, in ASP.NET Core 5.0 and later apps, they will throw a <xref:System.NotSupportedException>, unless the web app has re-enabled <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> functionality.</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>

<span data-ttu-id="16e83-109">次のシリアル化メソッドも古いと見なされ、警告 `SYSLIB0011` が生成されますが、動作変更はありません。</span><span class="sxs-lookup"><span data-stu-id="16e83-109">The following serialization methods are also obsolete and produce warning `SYSLIB0011`, but have no behavioral changes:</span></span>

- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="version-introduced"></a><span data-ttu-id="16e83-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="16e83-110">Version introduced</span></span>

<span data-ttu-id="16e83-111">5.0</span><span class="sxs-lookup"><span data-stu-id="16e83-111">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="16e83-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="16e83-112">Reason for change</span></span>

<span data-ttu-id="16e83-113">.NET エコシステム内における <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> の使用を段階的に縮小するための取り組みの一環として、これらのメソッドが古い形式としてマークされています。</span><span class="sxs-lookup"><span data-stu-id="16e83-113">These methods are marked obsolete as part of an effort to wind down usage of <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> within the .NET ecosystem.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="16e83-114">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="16e83-114">Recommended action</span></span>

- <span data-ttu-id="16e83-115">コードでの <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> の使用を停止してください。</span><span class="sxs-lookup"><span data-stu-id="16e83-115">Stop using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> in your code.</span></span> <span data-ttu-id="16e83-116">代わりに、<xref:System.Text.Json.JsonSerializer> または <xref:System.Xml.Serialization.XmlSerializer> の使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="16e83-116">Instead, consider using <xref:System.Text.Json.JsonSerializer> or <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="16e83-117">詳しくは、「[BinaryFormatter セキュリティ ガイド](../../../../standard/serialization/binaryformatter-security-guide.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="16e83-117">For more information, see [BinaryFormatter security guide](../../../../standard/serialization/binaryformatter-security-guide.md).</span></span>

- <span data-ttu-id="16e83-118"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> のコンパイル時の警告 (`SYSLIB0011`) を一時的に抑制することができます。</span><span class="sxs-lookup"><span data-stu-id="16e83-118">You can temporarily suppress the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> compile-time warning, which is `SYSLIB0011`.</span></span> <span data-ttu-id="16e83-119">このオプションを選択する前に、リスクについてコードを十分に評価することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="16e83-119">We recommend that you thoroughly assess your code for risks before choosing this option.</span></span> <span data-ttu-id="16e83-120">警告を抑制する最も簡単な方法は、個々の呼び出しサイトを `#pragma` ディレクティブで囲むことです。</span><span class="sxs-lookup"><span data-stu-id="16e83-120">The easiest way to suppress the warnings is to surround the individual call site with `#pragma` directives.</span></span>

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

  <span data-ttu-id="16e83-121">また、プロジェクト ファイルで警告を抑制することもできます。</span><span class="sxs-lookup"><span data-stu-id="16e83-121">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "BinaryFormatter is obsolete" warnings for entire project -->
    <NoWarn>$(NoWarn);SYSLIB0011</NoWarn>
  </PropertyGroup>
  ```

  <span data-ttu-id="16e83-122">プロジェクト ファイルで警告を抑制すると、プロジェクト内のすべてのコード ファイルに対して警告が抑制されます。</span><span class="sxs-lookup"><span data-stu-id="16e83-122">If you suppress the warning in the project file, the warning is suppressed for all code files in the project.</span></span> <span data-ttu-id="16e83-123">`SYSLIB0011` を抑制しても、他の古い API の使用によって発生した警告は抑制されません。</span><span class="sxs-lookup"><span data-stu-id="16e83-123">Suppressing `SYSLIB0011` does not suppress warnings caused by using other obsolete APIs.</span></span>

- <span data-ttu-id="16e83-124">ASP.NET アプリで引き続き <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> を使用する場合は、プロジェクト ファイルで再有効化することができます。</span><span class="sxs-lookup"><span data-stu-id="16e83-124">To continue using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> in ASP.NET apps, you can re-enable it in the project file.</span></span> <span data-ttu-id="16e83-125">ただし、そうしないことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="16e83-125">However, it's strongly recommended not to do this.</span></span> <span data-ttu-id="16e83-126">詳しくは、「[BinaryFormatter セキュリティ ガイド](../../../../standard/serialization/binaryformatter-security-guide.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="16e83-126">For more information, see [BinaryFormatter security guide](../../../../standard/serialization/binaryformatter-security-guide.md).</span></span>

  ```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Warning: Setting the following switch is *NOT* recommended in web apps. -->
    <EnableUnsafeBinaryFormatterSerialization>true</EnableUnsafeBinaryFormatterSerialization>
  </PropertyGroup>
  ```

<span data-ttu-id="16e83-127">推奨される操作の詳細については、「[BinaryFormatter の廃止と無効化に関するエラーの解決](../../../../standard/serialization/binaryformatter-security-guide.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="16e83-127">For more information about recommended actions, see [Resolving BinaryFormatter obsoletion and disablement errors](../../../../standard/serialization/binaryformatter-security-guide.md).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="16e83-128">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="16e83-128">Affected APIs</span></span>

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
