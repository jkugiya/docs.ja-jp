---
title: C# を使用した JSON のシリアル化と逆シリアル化 - .NET
description: この概要では、.NET で JSON との間でシリアル化または逆シリアル化を行うための System.Text.Json 名前空間機能について説明します。
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 9a57319dc1d744bfc06cc7360ffcb59b24fe3646
ms.sourcegitcommit: fdfa01f6cd3aa4c36b6e8a1830693ff22d35aeea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2021
ms.locfileid: "107292263"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="7c109-103">.NET での JSON のシリアル化と逆シリアル化 (マーシャリングとマーシャリング解除) - 概要</span><span class="sxs-lookup"><span data-stu-id="7c109-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="7c109-104">`System.Text.Json` 名前空間は、JavaScript Object Notation (JSON) との間でのシリアル化と逆シリアル化の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="7c109-104">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="7c109-105">ライブラリの設計では、ハイ パフォーマンスと、高度な豊富なセットに対する少ないメモリ割り当てが強調されています。</span><span class="sxs-lookup"><span data-stu-id="7c109-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="7c109-106">組み込みの UTF-8 サポートによって、UTF-8 としてエンコードされた JSON テキストの読み取りと書き込みのプロセスが最適化されます。これは、web 上のデータおよびディスク上のファイルのための最も一般的なエンコードです。</span><span class="sxs-lookup"><span data-stu-id="7c109-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="7c109-107">ライブラリには、メモリ内のドキュメント オブジェクト モデル (DOM) を操作するためのクラスも用意されています。</span><span class="sxs-lookup"><span data-stu-id="7c109-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="7c109-108">この機能により、JSON ファイルまたは文字列内の要素に対する読み取り専用のランダムアクセスが可能になります。</span><span class="sxs-lookup"><span data-stu-id="7c109-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

<span data-ttu-id="7c109-109">Visual Basic コードから使用できるライブラリの部分には、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="7c109-109">There are some limitations on what parts of the library that you can use from Visual Basic code.</span></span> <span data-ttu-id="7c109-110">詳細については、「[Visual Basic のサポート](system-text-json-how-to.md#visual-basic-support)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7c109-110">For more information, see [Visual Basic support](system-text-json-how-to.md#visual-basic-support).</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="7c109-111">ライブラリの入手方法</span><span class="sxs-lookup"><span data-stu-id="7c109-111">How to get the library</span></span>

* <span data-ttu-id="7c109-112">ライブラリは、.NET Core 3.0 以降のバージョン用の共有フレームワークの一部として組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="7c109-112">The library is built-in as part of the shared framework for .NET Core 3.0 and later versions.</span></span>
* <span data-ttu-id="7c109-113">それより前のバージョンの Framework では、[System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="7c109-113">For earlier framework versions, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="7c109-114">このパッケージで以下がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7c109-114">The package supports:</span></span>

  * <span data-ttu-id="7c109-115">.NET Standard 2.0 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="7c109-115">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="7c109-116">.NET Framework 4.7.2 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="7c109-116">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="7c109-117">.NET Core 2.0、2.1、および 2.2</span><span class="sxs-lookup"><span data-stu-id="7c109-117">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="security-information"></a><span data-ttu-id="7c109-118">セキュリティ情報</span><span class="sxs-lookup"><span data-stu-id="7c109-118">Security information</span></span>

<span data-ttu-id="7c109-119"><xref:System.Text.Json.JsonSerializer> の設計時に考慮されたセキュリティ上の脅威と、その脅威を軽減する方法については、「[`System.Text.Json` 脅威モデル](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Text.Json/docs/ThreatModel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c109-119">For information about security threats that were considered when designing <xref:System.Text.Json.JsonSerializer>, and how they can be mitigated, see [`System.Text.Json` Threat Model](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Text.Json/docs/ThreatModel.md).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7c109-120">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="7c109-120">Additional resources</span></span>

* [<span data-ttu-id="7c109-121">ライブラリを使用する方法</span><span class="sxs-lookup"><span data-stu-id="7c109-121">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="7c109-122">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="7c109-122">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="7c109-123">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="7c109-123">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="7c109-124">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="7c109-124">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="7c109-125">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="7c109-125">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="7c109-126">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="7c109-126">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="7c109-127">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="7c109-127">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="7c109-128">参照を保持する</span><span class="sxs-lookup"><span data-stu-id="7c109-128">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="7c109-129">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="7c109-129">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="7c109-130">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="7c109-130">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="7c109-131">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="7c109-131">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="7c109-132">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="7c109-132">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="7c109-133">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="7c109-133">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="7c109-134">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="7c109-134">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="7c109-135">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="7c109-135">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="7c109-136">System.Text.Json でサポートされているコレクション型</span><span class="sxs-lookup"><span data-stu-id="7c109-136">Supported collection types in System.Text.Json</span></span>](system-text-json-supported-collection-types.md)
* <span data-ttu-id="7c109-137">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="7c109-137">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="7c109-138">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="7c109-138">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
