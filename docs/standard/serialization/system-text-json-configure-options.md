---
title: System.Text.Json で JsonSerializerOptions をインスタンス化する方法
description: パフォーマンスの問題を回避する方法と、JsonSerializerOptions インスタンスで使用可能なコンストラクターを使用する方法について説明します。
ms.date: 01/19/2021
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
dev_langs:
- csharp
- vb
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: a74f4e0aa286f182906033e34be7bad63a72503f
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100583233"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-systemtextjson"></a><span data-ttu-id="fa784-103">System.Text.Json で JsonSerializerOptions インスタンスをインスタンス化する方法</span><span class="sxs-lookup"><span data-stu-id="fa784-103">How to instantiate JsonSerializerOptions instances with System.Text.Json</span></span>

<span data-ttu-id="fa784-104">この記事では、<xref:System.Text.Json.JsonSerializerOptions> の使用時にパフォーマンスの問題を回避する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fa784-104">This article explains how to avoid performance problems when you use <xref:System.Text.Json.JsonSerializerOptions>.</span></span> <span data-ttu-id="fa784-105">また、使用可能なパラメーター化コンストラクターの使用方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="fa784-105">It also shows how to use the parameterized constructors that are available.</span></span>

## <a name="reuse-jsonserializeroptions-instances"></a><span data-ttu-id="fa784-106">JsonSerializerOptions インスタンスの再利用</span><span class="sxs-lookup"><span data-stu-id="fa784-106">Reuse JsonSerializerOptions instances</span></span>

<span data-ttu-id="fa784-107">同じオプションで `JsonSerializerOptions` を繰り返し使用する場合、使用のたびに新しい `JsonSerializerOptions` インスタンスを作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="fa784-107">If you use `JsonSerializerOptions` repeatedly with the same options, don't create a new `JsonSerializerOptions` instance each time you use it.</span></span> <span data-ttu-id="fa784-108">すべての呼び出しで同じインスタンスを再利用します。</span><span class="sxs-lookup"><span data-stu-id="fa784-108">Reuse the same instance for every call.</span></span> <span data-ttu-id="fa784-109">ここでは、カスタム コンバーター用に作成し、<xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> または <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> を呼び出すコードに関して説明しています。</span><span class="sxs-lookup"><span data-stu-id="fa784-109">This guidance applies to code you write for custom converters and when you call <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> or <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="fa784-110">次のコードでは、新しいオプションのインスタンスを使用する場合にパフォーマンスが低下することを示しています。</span><span class="sxs-lookup"><span data-stu-id="fa784-110">The following code demonstrates the performance penalty for using new options instances.</span></span>

:::code language="csharp" source="snippets/system-text-json-configure-options/csharp/ReuseOptionsInstances.cs":::

<span data-ttu-id="fa784-111">上のコードでは、同じオプション インスタンスを使用して、小さいオブジェクトを 100,000 回シリアル化しています。</span><span class="sxs-lookup"><span data-stu-id="fa784-111">The preceding code serializes a small object 100,000 times using the same options instance.</span></span> <span data-ttu-id="fa784-112">その後、同じ回数だけ同じオブジェクトがシリアル化され、毎回新しいオプション インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="fa784-112">Then it serializes the same object the same number of times and creates a new options instance each time.</span></span> <span data-ttu-id="fa784-113">実行時の典型的な差は、40,140 ミリ秒と比較し 190 です。</span><span class="sxs-lookup"><span data-stu-id="fa784-113">A typical run time difference is 190 compared to 40,140 milliseconds.</span></span> <span data-ttu-id="fa784-114">イテレーションの回数を増やすと、この差はさらに広がります。</span><span class="sxs-lookup"><span data-stu-id="fa784-114">The difference is even greater if you increase the number of iterations.</span></span>

<span data-ttu-id="fa784-115">新しいオプション インスタンスが渡されると、オブジェクト グラフ内の各型の最初のシリアル化時にシリアライザーはウォームアップ フェーズになります。</span><span class="sxs-lookup"><span data-stu-id="fa784-115">The serializer undergoes a warm-up phase during the first serialization of each type in the object graph when a new options instance is passed to it.</span></span> <span data-ttu-id="fa784-116">このウォームアップには、シリアル化に必要なメタデータのキャッシュの作成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fa784-116">This warm-up includes creating a cache of metadata that is needed for serialization.</span></span> <span data-ttu-id="fa784-117">メタデータには、プロパティのゲッター、セッター、コンストラクターの引数、指定した属性などに対するデリゲートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fa784-117">The metadata includes delegates to property getters, setters, constructor arguments, specified attributes, and so forth.</span></span> <span data-ttu-id="fa784-118">このメタデータ キャッシュは、オプションのインスタンスに格納されています。</span><span class="sxs-lookup"><span data-stu-id="fa784-118">This metadata cache is stored in the options instance.</span></span> <span data-ttu-id="fa784-119">同じウォームアップ プロセスとキャッシュは逆シリアル化にも該当します。</span><span class="sxs-lookup"><span data-stu-id="fa784-119">The same warm-up process and cache applies to deserialization.</span></span>

<span data-ttu-id="fa784-120">`JsonSerializerOptions` インスタンスのメタデータのキャッシュのサイズは、シリアル化される型の数によって異なります。</span><span class="sxs-lookup"><span data-stu-id="fa784-120">The size of the metadata cache in a `JsonSerializerOptions` instance depends on the number of types to be serialized.</span></span> <span data-ttu-id="fa784-121">動的に生成された型など、多数の型をシリアライザーに渡すと、キャッシュのサイズは増加し続け、最終的に `OutOfMemoryException` が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fa784-121">If you pass numerous types—for example, dynamically generated types—to the serializer, the cache size will continue to grow and can end up causing an `OutOfMemoryException`.</span></span>

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="fa784-122">JsonSerializerOptions をコピーする</span><span class="sxs-lookup"><span data-stu-id="fa784-122">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="fa784-123">次の例で示されているように、既存のインスタンスと同じオプションを使用して新しいインスタンスを作成できる [JsonSerializerOptions コンストラクター](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions))があります。</span><span class="sxs-lookup"><span data-stu-id="fa784-123">There is a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/CopyOptions.vb" :::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="fa784-124">既存のインスタンスを受け取る `JsonSerializerOptions` コンストラクターは、.NET Core 3.1 では使用できません。</span><span class="sxs-lookup"><span data-stu-id="fa784-124">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="fa784-125">JsonSerializerOptions の Web の既定値</span><span class="sxs-lookup"><span data-stu-id="fa784-125">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="fa784-126">Web アプリ用に異なる既定値があるオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fa784-126">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="fa784-127">次の例で示されているように、ASP.NET Core によって Web アプリ用に使用される既定のオプションで新しいインスタンスを作成できる [JsonSerializerOptions コンストラクター](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true)があります。</span><span class="sxs-lookup"><span data-stu-id="fa784-127">There's a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/OptionsDefaults.vb" :::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="fa784-128">Web アプリ用に異なる既定値があるオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fa784-128">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

<span data-ttu-id="fa784-129">既定値のセットを指定する `JsonSerializerOptions` コンストラクターは、.NET Core 3.1 では使用できません。</span><span class="sxs-lookup"><span data-stu-id="fa784-129">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="fa784-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa784-130">See also</span></span>

* [<span data-ttu-id="fa784-131">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="fa784-131">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="fa784-132">JSON をシリアル化および逆シリアル化する方法</span><span class="sxs-lookup"><span data-stu-id="fa784-132">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="fa784-133">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="fa784-133">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="fa784-134">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="fa784-134">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="fa784-135">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="fa784-135">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="fa784-136">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="fa784-136">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="fa784-137">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="fa784-137">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="fa784-138">参照を保持する</span><span class="sxs-lookup"><span data-stu-id="fa784-138">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="fa784-139">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="fa784-139">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="fa784-140">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="fa784-140">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="fa784-141">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="fa784-141">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="fa784-142">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="fa784-142">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="fa784-143">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="fa784-143">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="fa784-144">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="fa784-144">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="fa784-145">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="fa784-145">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="fa784-146">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="fa784-146">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="fa784-147">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="fa784-147">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
