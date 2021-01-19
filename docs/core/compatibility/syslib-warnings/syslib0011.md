---
title: SYSLIB0011 警告
description: コンパイル時の警告 SYSLIB0011 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 85b5e07b1ecd6852d8c8e93cc3e89ced4b021ef9
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189858"
---
# <a name="syslib0011-binaryformatter-serialization-is-obsolete"></a><span data-ttu-id="03b85-103">SYSLIB0011:BinaryFormatter は旧型式</span><span class="sxs-lookup"><span data-stu-id="03b85-103">SYSLIB0011: BinaryFormatter serialization is obsolete</span></span>

<span data-ttu-id="03b85-104"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> の[セキュリティの脆弱性](../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities)により、.NET 5.0 以降、次の API は古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="03b85-104">Due to [security vulnerabilities](../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) in <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, the following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="03b85-105">これらをコードで使用すると、コンパイル時に警告 `SYSLIB0011` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="03b85-105">Using them in code generates warning `SYSLIB0011` at compile time.</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="03b85-106">問題回避</span><span class="sxs-lookup"><span data-stu-id="03b85-106">Workarounds</span></span>

<span data-ttu-id="03b85-107"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> の代わりに、<xref:System.Text.Json.JsonSerializer> または <xref:System.Xml.Serialization.XmlSerializer> の使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="03b85-107">Consider using <xref:System.Text.Json.JsonSerializer> or <xref:System.Xml.Serialization.XmlSerializer> instead of <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span>

<span data-ttu-id="03b85-108">推奨される操作の詳細については、「[BinaryFormatter の廃止と無効化に関するエラーの解決](../../../standard/serialization/binaryformatter-security-guide.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="03b85-108">For more information about recommended actions, see [Resolving BinaryFormatter obsoletion and disablement errors](../../../standard/serialization/binaryformatter-security-guide.md).</span></span>

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="03b85-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="03b85-109">See also</span></span>

- [<span data-ttu-id="03b85-110">BinaryFormatter の旧型式と無効化に関するエラーの解決</span><span class="sxs-lookup"><span data-stu-id="03b85-110">Resolving BinaryFormatter obsoletion and disablement errors</span></span>](../../../standard/serialization/binaryformatter-security-guide.md)
- [<span data-ttu-id="03b85-111">BinaryFormatter シリアル化メソッドが古い形式になり、ASP.NET アプリでは使用不可に</span><span class="sxs-lookup"><span data-stu-id="03b85-111">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](../core-libraries/5.0/binaryformatter-serialization-obsolete.md)
