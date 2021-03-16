---
title: 破壊的変更:char の逆シリアル化で 1 文字の文字列が求められる
description: System.Text.Json では、char ターゲットに逆シリアル化するとき、JSON に 1 文字の文字が必要になるという、.NET 5 の破壊的変更について説明します。
ms.date: 12/15/2020
ms.openlocfilehash: e901f8ee7e7521af948a3bcde5cf969640436f7f
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256336"
---
# <a name="systemtextjson-requires-single-char-string-to-deserialize-a-char"></a><span data-ttu-id="9a311-103">System.Text.Json では、char の逆シリアル化に 1 文字の文字列が必要です</span><span class="sxs-lookup"><span data-stu-id="9a311-103">System.Text.Json requires single-char string to deserialize a char</span></span>

<span data-ttu-id="9a311-104"><xref:System.Text.Json> を利用して <xref:System.Char> を正常に逆シリアル化するには、JSON 文字列に 1 文字を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a311-104">To successfully deserialize a <xref:System.Char> using <xref:System.Text.Json>, the JSON string must contain a single character.</span></span>

## <a name="change-description"></a><span data-ttu-id="9a311-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="9a311-105">Change description</span></span>

<span data-ttu-id="9a311-106">以前のバージョンの .NET では、JSON に複数の `char` からなる文字列があっても、`char` プロパティまたはフィールドに正常に逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="9a311-106">In previous .NET versions, a multi-`char` string in the JSON is successfully deserialized to a `char` property or field.</span></span> <span data-ttu-id="9a311-107">次の例のように、文字列の最初の `char` のみが使用されます。</span><span class="sxs-lookup"><span data-stu-id="9a311-107">Only the first `char` of the string is used, as in the following example:</span></span>

```csharp
// .NET Core 3.0 and 3.1: Returns the first char 'a'.
// .NET 5 and later: Throws JsonException because payload has more than one char.
char deserializedChar = JsonSerializer.Deserialize<char>("\"abc\"");
```

<span data-ttu-id="9a311-108">.NET 5 以降では、`char` が 1 つの文字列以外を渡すと、逆シリアル化のターゲットが `char` のとき、<xref:System.Text.Json.JsonException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9a311-108">In .NET 5 and later, anything other than a single-`char` string causes a <xref:System.Text.Json.JsonException> to be thrown when the deserialization target is a `char`.</span></span> <span data-ttu-id="9a311-109">次の例の文字列は、すべての .NET バージョンで正常に逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="9a311-109">The following example string is successfully deserialized in all .NET versions:</span></span>

```csharp
// Correct usage.
char deserializedChar = JsonSerializer.Deserialize<char>("\"a\"");
```

## <a name="version-introduced"></a><span data-ttu-id="9a311-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="9a311-110">Version introduced</span></span>

<span data-ttu-id="9a311-111">5.0</span><span class="sxs-lookup"><span data-stu-id="9a311-111">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="9a311-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="9a311-112">Reason for change</span></span>

<span data-ttu-id="9a311-113">逆シリアル化の解析は、指定されたペイロードがターゲットの型に対して有効なときにのみ、成功しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="9a311-113">Parsing for deserialization should only succeed when the provided payload is valid for the target type.</span></span> <span data-ttu-id="9a311-114">`char` 型の場合、有効なペイロードは `char` が 1 つの文字列のみです。</span><span class="sxs-lookup"><span data-stu-id="9a311-114">For a `char` type, the only valid payload is a single-`char` string.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="9a311-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="9a311-115">Recommended action</span></span>

<span data-ttu-id="9a311-116">JSON を `char` ターゲットに逆シリアル化するとき、文字列が 1 つの `char` で構成されるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="9a311-116">When you deserialize JSON into a `char` target, make sure the string consists of a single `char`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="9a311-117">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="9a311-117">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`

### Category

Serialization

-->
