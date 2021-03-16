---
title: .NET でカスタム構成プロバイダーを実装する
description: .NET アプリケーションにカスタム構成プロバイダーを実装する方法について説明します。
author: IEvangelist
ms.author: dapine
ms.date: 12/04/2020
ms.topic: how-to
ms.openlocfilehash: 22e46b7df8b02421633d6be251d990879baa8b2b
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "102402023"
---
# <a name="implement-a-custom-configuration-provider-in-net"></a><span data-ttu-id="68c17-103">.NET でカスタム構成プロバイダーを実装する</span><span class="sxs-lookup"><span data-stu-id="68c17-103">Implement a custom configuration provider in .NET</span></span>

<span data-ttu-id="68c17-104">JSON、XML、INI ファイルなどの一般的な構成ソースに使用できる[構成プロバイダー](configuration-providers.md)は多数あります。</span><span class="sxs-lookup"><span data-stu-id="68c17-104">There are many [configuration providers](configuration-providers.md) available for common configuration sources such as JSON, XML, and INI files.</span></span> <span data-ttu-id="68c17-105">使用できるプロバイダーの 1 つがアプリケーションのニーズに合わない場合は、必要に応じてカスタム構成プロバイダーを実装します。</span><span class="sxs-lookup"><span data-stu-id="68c17-105">You may need to implement a custom configuration provider when one of the available providers doesn't suit your application needs.</span></span> <span data-ttu-id="68c17-106">この記事では、構成ソースとしてデータベースに依存するカスタム構成プロバイダーを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="68c17-106">In this article, you'll learn how to implement a custom configuration provider that relies on a database as its configuration source.</span></span>

## <a name="custom-configuration-provider"></a><span data-ttu-id="68c17-107">カスタム構成プロバイダー</span><span class="sxs-lookup"><span data-stu-id="68c17-107">Custom configuration provider</span></span>

<span data-ttu-id="68c17-108">このサンプル アプリは、[Entity Framework (EF) Core](/ef/core) を使用してデータベースから構成のキーと値のペアを読み取る、基本的な構成プロバイダーを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="68c17-108">The sample app demonstrates how to create a basic configuration provider that reads configuration key-value pairs from a database using [Entity Framework (EF) Core](/ef/core).</span></span>

<span data-ttu-id="68c17-109">プロバイダーの特徴は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="68c17-109">The provider has the following characteristics:</span></span>

- <span data-ttu-id="68c17-110">EF のメモリ内データベースは、デモンストレーションのために使用されます。</span><span class="sxs-lookup"><span data-stu-id="68c17-110">The EF in-memory database is used for demonstration purposes.</span></span> <span data-ttu-id="68c17-111">接続文字列を必要とするデータベースを使用するには、第 2 の `ConfigurationBuilder` を実装して、別の構成プロバイダーからの接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="68c17-111">To use a database that requires a connection string, implement a secondary `ConfigurationBuilder` to supply the connection string from another configuration provider.</span></span>
- <span data-ttu-id="68c17-112">プロバイダーは、起動時に、構成にデータベース テーブルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="68c17-112">The provider reads a database table into configuration at startup.</span></span> <span data-ttu-id="68c17-113">プロバイダーは、キー単位でデータベースを照会しません。</span><span class="sxs-lookup"><span data-stu-id="68c17-113">The provider doesn't query the database on a per-key basis.</span></span>
- <span data-ttu-id="68c17-114">変更時に再度読み込む機能は実装されていません。このため、アプリの起動後にデータベースを更新しても、アプリの構成には影響がありません。</span><span class="sxs-lookup"><span data-stu-id="68c17-114">Reload-on-change isn't implemented, so updating the database after the app starts has no effect on the app's configuration.</span></span>

<span data-ttu-id="68c17-115">データベースに構成値を格納するための `Settings` レコード型のエンティティを定義します。</span><span class="sxs-lookup"><span data-stu-id="68c17-115">Define a `Settings` record type entity for storing configuration values in the database.</span></span> <span data-ttu-id="68c17-116">たとえば、*Models* フォルダーに *Settings.cs* ファイルを追加できます。</span><span class="sxs-lookup"><span data-stu-id="68c17-116">For example, you could add a *Settings.cs* file in your *Models* folder:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Models/Settings.cs":::

<span data-ttu-id="68c17-117">レコード型については、[C# 9 でのレコード型](../../csharp/whats-new/csharp-9.md#record-types)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68c17-117">For information on record types, see [Record types in C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span></span>

<span data-ttu-id="68c17-118">構成した値を格納し、その値にアクセスするための `EntityConfigurationContext` を追加します。</span><span class="sxs-lookup"><span data-stu-id="68c17-118">Add an `EntityConfigurationContext` to store and access the configured values.</span></span>

<span data-ttu-id="68c17-119">*Providers/EntityConfigurationContext.cs*:</span><span class="sxs-lookup"><span data-stu-id="68c17-119">*Providers/EntityConfigurationContext.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationContext.cs":::

<span data-ttu-id="68c17-120"><xref:Microsoft.Extensions.Configuration.IConfigurationSource> を実装するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="68c17-120">Create a class that implements <xref:Microsoft.Extensions.Configuration.IConfigurationSource>.</span></span>

<span data-ttu-id="68c17-121">*Providers/EntityConfigurationSource.cs*:</span><span class="sxs-lookup"><span data-stu-id="68c17-121">*Providers/EntityConfigurationSource.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationSource.cs":::

<span data-ttu-id="68c17-122"><xref:Microsoft.Extensions.Configuration.ConfigurationProvider> から継承して、カスタム構成プロバイダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="68c17-122">Create the custom configuration provider by inheriting from <xref:Microsoft.Extensions.Configuration.ConfigurationProvider>.</span></span> <span data-ttu-id="68c17-123">データベースが空だった場合、構成プロバイダーはこれを初期化します。</span><span class="sxs-lookup"><span data-stu-id="68c17-123">The configuration provider initializes the database when it's empty.</span></span> <span data-ttu-id="68c17-124">構成キーでは大文字と小文字が区別されないため、データベースの初期化に使用されるディクショナリは、大文字と小文字を区別しない比較子 ([StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)) を使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="68c17-124">Since configuration keys are case-insensitive, the dictionary used to initialize the database is created with the case-insensitive comparer ([StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)).</span></span>

<span data-ttu-id="68c17-125">*Providers/EntityConfigurationProvider.cs*:</span><span class="sxs-lookup"><span data-stu-id="68c17-125">*Providers/EntityConfigurationProvider.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationProvider.cs":::

<span data-ttu-id="68c17-126">`AddEntityConfiguration` 拡張メソッドを使用すると、<xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> インスタンスに構成ソースを追加できます。</span><span class="sxs-lookup"><span data-stu-id="68c17-126">An `AddEntityConfiguration` extension method permits adding the configuration source to a <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance.</span></span>

<span data-ttu-id="68c17-127">*Extensions/ConfigurationBuilderExtensions.cs*:</span><span class="sxs-lookup"><span data-stu-id="68c17-127">*Extensions/ConfigurationBuilderExtensions.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Extensions/ConfigurationBuilderExtensions.cs":::

<span data-ttu-id="68c17-128">次のコードでは、*Program.cs* でカスタムの `EntityConfigurationProvider` を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="68c17-128">The following code shows how to use the custom `EntityConfigurationProvider` in *Program.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Program.cs" highlight="27-28":::

## <a name="see-also"></a><span data-ttu-id="68c17-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="68c17-129">See also</span></span>

- [<span data-ttu-id="68c17-130">.NET での構成</span><span class="sxs-lookup"><span data-stu-id="68c17-130">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="68c17-131">.NET の構成プロバイダー</span><span class="sxs-lookup"><span data-stu-id="68c17-131">Configuration providers in .NET</span></span>](configuration-providers.md)
