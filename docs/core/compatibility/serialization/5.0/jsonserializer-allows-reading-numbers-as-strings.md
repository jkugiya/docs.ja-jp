---
title: 破壊的変更:ASP.NET Core アプリで、引用符で囲まれた数値を逆シリアル化できる
description: .NET 5 の破壊的変更について学習します。この変更後、例外がスローされるのではなく、JSON 文字列として表される数値が ASP.NET Core アプリによって正常に逆シリアル化されるようになります。
ms.date: 10/21/2020
ms.openlocfilehash: bc1531bb9b159bfd9e80eafacafb50aa509973cc
ms.sourcegitcommit: d623f686701b94bef905ec5e93d8b55d031c5d6f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624150"
---
# <a name="aspnet-core-apps-allow-deserializing-quoted-numbers"></a><span data-ttu-id="c40a9-103">ASP.NET Core アプリで、引用符で囲まれた数値を逆シリアル化できる</span><span class="sxs-lookup"><span data-stu-id="c40a9-103">ASP.NET Core apps allow deserializing quoted numbers</span></span>

<span data-ttu-id="c40a9-104">.NET 5 以降では、ASP.NET Core アプリによって、<xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> で指定された既定の逆シリアル化オプションが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c40a9-104">Starting in .NET 5, ASP.NET Core apps use the default deserialization options as specified by <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c40a9-105"><xref:System.Text.Json.JsonSerializerDefaults.Web> オプション セットには、<xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType>への <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> の設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c40a9-105">The <xref:System.Text.Json.JsonSerializerDefaults.Web> set of options includes setting <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> to <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c40a9-106">この変更は、例外がスローされるのではなく、JSON 文字列として表される数値が ASP.NET Core アプリによって正常に逆シリアル化されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="c40a9-106">This change means that ASP.NET Core apps will successfully deserialize numbers that are represented as JSON strings instead of throwing an exception.</span></span>

## <a name="change-description"></a><span data-ttu-id="c40a9-107">変更内容</span><span class="sxs-lookup"><span data-stu-id="c40a9-107">Change description</span></span>

<span data-ttu-id="c40a9-108">.NET Core 3.0 から 3.1 では、JSON ペイロードで引用符で囲まれた数値が検出された場合、逆シリアル化中に <xref:System.Text.Json.JsonSerializer> によって <xref:System.Text.Json.JsonException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="c40a9-108">In .NET Core 3.0 - 3.1, <xref:System.Text.Json.JsonSerializer> throws a <xref:System.Text.Json.JsonException> during deserialization if it encounters a quoted number in a JSON payload.</span></span> <span data-ttu-id="c40a9-109">引用符で囲まれた数値は、オブジェクト グラフの数値プロパティとマップするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c40a9-109">The quoted numbers are used to map with number properties in object graphs.</span></span> <span data-ttu-id="c40a9-110">.NET Core 3.0 から 3.1 では、数値は <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType> トークンからのみ読み取られます。</span><span class="sxs-lookup"><span data-stu-id="c40a9-110">In .NET Core 3.0 - 3.1, numbers are only read from <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType> tokens.</span></span>

<span data-ttu-id="c40a9-111">.NET 5 以降では、JSON ペイロードの引用符で囲まれた数値は、既定で ASP.NET Core アプリに対して有効と見なされます。</span><span class="sxs-lookup"><span data-stu-id="c40a9-111">Starting in .NET 5, quoted numbers in JSON payloads are considered valid, by default, for ASP.NET Core apps.</span></span> <span data-ttu-id="c40a9-112">引用符で囲まれた数値の逆シリアル化中に例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="c40a9-112">No exception is thrown during deserialization of quoted numbers.</span></span>

> [!TIP]
>
> - <span data-ttu-id="c40a9-113">既定のスタンドアロンの <xref:System.Text.Json.JsonSerializer> や <xref:System.Text.Json.JsonSerializerOptions> の動作変更はありません。</span><span class="sxs-lookup"><span data-stu-id="c40a9-113">There is no behavior change for the default, standalone <xref:System.Text.Json.JsonSerializer> or <xref:System.Text.Json.JsonSerializerOptions>.</span></span>
> - <span data-ttu-id="c40a9-114">これは厳密には破壊的変更ではありません。これにより、シナリオがより制限の厳しいものになるのではなく、より制限の少ないものになるためです (つまり、例外をスローするのではなく、JSON 文字列からの数値の強制変換が正常に行われます)。</span><span class="sxs-lookup"><span data-stu-id="c40a9-114">This is technically not a breaking change, since it makes a scenario more permissive instead of more restrictive (that is, it succeeds in coercing a number from a JSON string instead of throwing an exception).</span></span> <span data-ttu-id="c40a9-115">しかし、これは多くの ASP.NET Core アプリに影響する重要な動作変更であるため、ここに記載されています。</span><span class="sxs-lookup"><span data-stu-id="c40a9-115">However, since this is a significant behavioral change that affects many ASP.NET Core apps, it is documented here.</span></span>
> - <span data-ttu-id="c40a9-116"><xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> および <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A?displayProperty=nameWithType> 拡張メソッドで <xref:System.Text.Json.JsonSerializerDefaults.Web> シリアル化オプション セットも使用されます。</span><span class="sxs-lookup"><span data-stu-id="c40a9-116">The <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A?displayProperty=nameWithType> extension methods also use the <xref:System.Text.Json.JsonSerializerDefaults.Web> set of serialization options.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c40a9-117">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="c40a9-117">Version introduced</span></span>

<span data-ttu-id="c40a9-118">5.0</span><span class="sxs-lookup"><span data-stu-id="c40a9-118">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="c40a9-119">変更理由</span><span class="sxs-lookup"><span data-stu-id="c40a9-119">Reason for change</span></span>

<span data-ttu-id="c40a9-120">複数のユーザーから、<xref:System.Text.Json.JsonSerializer> でのより制限の少ない数値処理のためのオプションを求められました。</span><span class="sxs-lookup"><span data-stu-id="c40a9-120">Multiple users have requested an option for more permissive number handling in <xref:System.Text.Json.JsonSerializer>.</span></span> <span data-ttu-id="c40a9-121">このフィードバックは、多くの JSON プロデューサー (たとえば、Web 全体のサービス) によって引用符で囲まれた数値が生成されることを示しています。</span><span class="sxs-lookup"><span data-stu-id="c40a9-121">This feedback indicates that many JSON producers (for example, services across the web) emit quoted numbers.</span></span> <span data-ttu-id="c40a9-122">引用符で囲まれた数値の読み取り (逆シリアル化) を許可することにより、.NET アプリでこれらのペイロードを既定で Web コンテキストで正常に解析できます。</span><span class="sxs-lookup"><span data-stu-id="c40a9-122">By allowing quoted numbers to be read (deserialized), .NET apps can successfully parse these payloads, by default, in web contexts.</span></span> <span data-ttu-id="c40a9-123">この構成は <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> を介して公開されるので、クライアント、サーバー、および共有など、異なるアプリケーション層全体で同じオプションを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="c40a9-123">The configuration is exposed via <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> so that you can specify the same options across different application layers, for example, client, server, and shared.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c40a9-124">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="c40a9-124">Recommended action</span></span>

<span data-ttu-id="c40a9-125">この変更が破壊的なものである場合、たとえば、検証のために厳密な数値の処理に依存している場合は、以前の動作を再び有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="c40a9-125">If this change is disruptive, for example, if you depend on the strict number handling for validation, you can re-enable the previous behavior.</span></span> <span data-ttu-id="c40a9-126"><xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType> オプションを <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType> に設定します。</span><span class="sxs-lookup"><span data-stu-id="c40a9-126">Set the <xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType> option to <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c40a9-127">ASP.NET Core MVC および Web API アプリの場合は、次のコードを使用して `Startup` でオプションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="c40a9-127">For ASP.NET Core MVC and web API apps, you can configure the option in `Startup` by using the following code:</span></span>

```csharp
services.AddControllers()
   .AddJsonOptions(options => options.JsonSerializerOptions.NumberHandling = JsonNumberHandling.Strict);
```

## <a name="affected-apis"></a><span data-ttu-id="c40a9-128">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="c40a9-128">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

- ASP.NET Core
- Serialization

-->
