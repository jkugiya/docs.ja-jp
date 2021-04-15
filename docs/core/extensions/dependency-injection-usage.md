---
title: .NET で依存関係の挿入を使用する
description: .NET アプリケーションで依存関係の挿入を使用する方法について説明します。
author: IEvangelist
ms.author: dapine
ms.date: 04/12/2021
ms.topic: tutorial
no-loc:
- Transient
- Scoped
- Singleton
- Example
ms.openlocfilehash: 03828496dfa3487ad70fac8cf32ff81844eca6fd
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494273"
---
# <a name="tutorial-use-dependency-injection-in-net"></a><span data-ttu-id="6f728-103">チュートリアル: .NET で依存関係の挿入を使用する</span><span class="sxs-lookup"><span data-stu-id="6f728-103">Tutorial: Use dependency injection in .NET</span></span>

<span data-ttu-id="6f728-104">このチュートリアルでは、[.NET で依存関係の挿入 (DI)](dependency-injection.md) を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6f728-104">This tutorial shows how to use [dependency injection (DI) in .NET](dependency-injection.md).</span></span> <span data-ttu-id="6f728-105">"*Microsoft 拡張機能*" の場合、DI は最も重要視されるものであり、それによって <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> にサービスが追加され構成されます。</span><span class="sxs-lookup"><span data-stu-id="6f728-105">With *Microsoft Extensions*, DI is a first-class citizen where services are added and configured in an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="6f728-106"><xref:Microsoft.Extensions.Hosting.IHost> インターフェイスには <xref:System.IServiceProvider> インスタンスが公開されています。これは、登録されたすべてのサービスのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="6f728-106">The <xref:Microsoft.Extensions.Hosting.IHost> interface exposes the <xref:System.IServiceProvider> instance, which acts as a container of all the registered services.</span></span>

<span data-ttu-id="6f728-107">このチュートリアルでは、以下の内容を学習します。</span><span class="sxs-lookup"><span data-stu-id="6f728-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="6f728-108">依存関係の挿入を使用する .NET コンソール アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="6f728-108">Create a .NET console app that uses dependency injection</span></span>
> - <span data-ttu-id="6f728-109">[汎用ホスト](generic-host.md)を構築して構成する</span><span class="sxs-lookup"><span data-stu-id="6f728-109">Build and configure a [Generic Host](generic-host.md)</span></span>
> - <span data-ttu-id="6f728-110">いくつかのインターフェイスとそれに対応する実装を記述する</span><span class="sxs-lookup"><span data-stu-id="6f728-110">Write several interfaces and corresponding implementations</span></span>
> - <span data-ttu-id="6f728-111">DI のサービス有効期間とスコープを使用する</span><span class="sxs-lookup"><span data-stu-id="6f728-111">Use service lifetime and scoping for DI</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6f728-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="6f728-112">Prerequisites</span></span>

- <span data-ttu-id="6f728-113">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) 以降。</span><span class="sxs-lookup"><span data-stu-id="6f728-113">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) or later.</span></span>
- <span data-ttu-id="6f728-114">新しい .NET アプリケーションの作成と NuGet パッケージのインストールに関する知識。</span><span class="sxs-lookup"><span data-stu-id="6f728-114">Familiarity with creating new .NET applications and installing NuGet packages.</span></span>

## <a name="create-a-new-console-application"></a><span data-ttu-id="6f728-115">新しいコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="6f728-115">Create a new console application</span></span>

<span data-ttu-id="6f728-116">[dotnet new](../tools/dotnet-new.md) コマンドまたは IDE の新しいプロジェクト ウィザードのいずれかを使用して、**ConsoleDI.Example** という名前の新しい .NET コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="6f728-116">Using either the [dotnet new](../tools/dotnet-new.md) command or an IDE new project wizard, create a new .NET console application named **ConsoleDI.Example**.</span></span> <span data-ttu-id="6f728-117">NuGet パッケージ [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="6f728-117">Add the [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet package to the project.</span></span>

## <a name="add-interfaces"></a><span data-ttu-id="6f728-118">インターフェイスを追加する</span><span class="sxs-lookup"><span data-stu-id="6f728-118">Add interfaces</span></span>

<span data-ttu-id="6f728-119">次のインターフェイスをプロジェクトのルート ディレクトリに追加します。</span><span class="sxs-lookup"><span data-stu-id="6f728-119">Add the following interfaces to the project root directory:</span></span>

<span data-ttu-id="6f728-120">*IOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="6f728-120">*IOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

<span data-ttu-id="6f728-121">`IOperation` インターフェイスでは、単一の `OperationId` プロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="6f728-121">The `IOperation` interface defines a single `OperationId` property.</span></span>

<span data-ttu-id="6f728-122">*ITransientOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="6f728-122">*ITransientOperation.cs*</span></span>

<span data-ttu-id="6f728-123">:::code language="csharp" source="snippets/configuration/console-di/ITransientOperation.cs":::</span><span class="sxs-lookup"><span data-stu-id="6f728-123">:::code language="csharp" source="snippets/configuration/console-di/ITransientOperation.cs":::</span></span>

<span data-ttu-id="6f728-124">*IScopedOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="6f728-124">*IScopedOperation.cs*</span></span>

<span data-ttu-id="6f728-125">:::code language="csharp" source="snippets/configuration/console-di/IScopedOperation.cs":::</span><span class="sxs-lookup"><span data-stu-id="6f728-125">:::code language="csharp" source="snippets/configuration/console-di/IScopedOperation.cs":::</span></span>

<span data-ttu-id="6f728-126">*ISingletonOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="6f728-126">*ISingletonOperation.cs*</span></span>

<span data-ttu-id="6f728-127">:::code language="csharp" source="snippets/configuration/console-di/ISingletonOperation.cs":::</span><span class="sxs-lookup"><span data-stu-id="6f728-127">:::code language="csharp" source="snippets/configuration/console-di/ISingletonOperation.cs":::</span></span>

<span data-ttu-id="6f728-128">`IOperation` のすべてのサブインターフェイスで、意図するサービスの有効期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="6f728-128">All of the subinterfaces of `IOperation` name their intended service lifetime.</span></span> <span data-ttu-id="6f728-129">たとえば、"Transient" や "Singleton" とします。</span><span class="sxs-lookup"><span data-stu-id="6f728-129">For example, "Transient" or "Singleton".</span></span>

## <a name="add-default-implementation"></a><span data-ttu-id="6f728-130">既定の実装を追加する</span><span class="sxs-lookup"><span data-stu-id="6f728-130">Add default implementation</span></span>

<span data-ttu-id="6f728-131">さまざまな操作に対して次の既定の実装を追加します。</span><span class="sxs-lookup"><span data-stu-id="6f728-131">Add the following default implementation for the various operations:</span></span>

<span data-ttu-id="6f728-132">*DefaultOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="6f728-132">*DefaultOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

<span data-ttu-id="6f728-133">`DefaultOperation` によって、すべての名前付きマーカー インターフェイスが実装され、`OperationId` プロパティが新しいグローバル一意識別子 (GUID) の最後の 4 文字に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="6f728-133">The `DefaultOperation` implements all of the named marker interfaces and initializes the `OperationId` property to the last four characters of a new globally unique identifier (GUID).</span></span>

## <a name="add-service-that-requires-di"></a><span data-ttu-id="6f728-134">DI を必要とするサービスを追加する</span><span class="sxs-lookup"><span data-stu-id="6f728-134">Add service that requires DI</span></span>

<span data-ttu-id="6f728-135">次の操作ロガー オブジェクトを追加します。これは、コンソール アプリに対するサービスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="6f728-135">Add the following operation logger object, which acts as a service to the console app:</span></span>

<span data-ttu-id="6f728-136">*OperationLogger.cs*</span><span class="sxs-lookup"><span data-stu-id="6f728-136">*OperationLogger.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

<span data-ttu-id="6f728-137">`OperationLogger` には、前述の各マーカー インターフェイス (つまり、`ITransientOperation`、`IScopedOperation`、および `ISingletonOperation`) を必要とするコンストラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="6f728-137">The `OperationLogger` defines a constructor that requires each of the aforementioned marker interfaces, that is; `ITransientOperation`, `IScopedOperation`, and `ISingletonOperation`.</span></span> <span data-ttu-id="6f728-138">このオブジェクトによって、指定された `scope` パラメーターを使用してコンシューマーが操作をログできるようにする 1 つのメソッドが公開されます。</span><span class="sxs-lookup"><span data-stu-id="6f728-138">The object exposes a single method that allows the consumer to log the operations with a given `scope` parameter.</span></span> <span data-ttu-id="6f728-139">`LogOperations` メソッドを呼び出すと、各操作の一意識別子がスコープの文字列とメッセージと共にログされます。</span><span class="sxs-lookup"><span data-stu-id="6f728-139">When invoked, the `LogOperations` method logs each operation's unique identifier with the scope string and message.</span></span>

## <a name="register-services-for-di"></a><span data-ttu-id="6f728-140">DI 用のサービスを登録する</span><span class="sxs-lookup"><span data-stu-id="6f728-140">Register services for DI</span></span>

<span data-ttu-id="6f728-141">次のコードを使用して *Program.cs* を更新します。</span><span class="sxs-lookup"><span data-stu-id="6f728-141">Update *Program.cs* with the following code:</span></span>

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

<span data-ttu-id="6f728-142">各 `services.Add{SERVICE_NAME}` 拡張メソッドは、サービスを追加 (および場合によっては構成) します。</span><span class="sxs-lookup"><span data-stu-id="6f728-142">Each `services.Add{SERVICE_NAME}` extension method adds (and potentially configures) services.</span></span> <span data-ttu-id="6f728-143">アプリをこの規則に従わせることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6f728-143">We recommended that apps follow this convention.</span></span> <span data-ttu-id="6f728-144">拡張メソッドを <xref:Microsoft.Extensions.DependencyInjection?displayProperty=fullName> 名前空間に配置して、サービス登録のグループをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="6f728-144">Place extension methods in the <xref:Microsoft.Extensions.DependencyInjection?displayProperty=fullName> namespace to encapsulate groups of service registrations.</span></span> <span data-ttu-id="6f728-145">DI 拡張メソッド用の名前空間部分として `Microsoft.Extensions.DependencyInjection` を含めると、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6f728-145">Including the namespace portion `Microsoft.Extensions.DependencyInjection` for DI extension methods also:</span></span>

- <span data-ttu-id="6f728-146">`using` ブロックを追加しなくても、それらを [IntelliSense](/visualstudio/ide/using-intellisense) で表示することができます。</span><span class="sxs-lookup"><span data-stu-id="6f728-146">Allows them to be displayed in [IntelliSense](/visualstudio/ide/using-intellisense) without adding additional `using` blocks.</span></span>
- <span data-ttu-id="6f728-147">それらの拡張メソッドの通常の呼び出し元である `Program` または `Startup` クラス内で `using` ステートメントが過剰になることはありません。</span><span class="sxs-lookup"><span data-stu-id="6f728-147">Prevents excessive `using` statements in the `Program` or `Startup` classes where these extension methods are typically called.</span></span>

<span data-ttu-id="6f728-148">このアプリによって次のことが行われます。</span><span class="sxs-lookup"><span data-stu-id="6f728-148">The app:</span></span>

- <span data-ttu-id="6f728-149">[既定のバインダー設定](generic-host.md#default-builder-settings)で <xref:Microsoft.Extensions.Hosting.IHostBuilder> インスタンスを作成する。</span><span class="sxs-lookup"><span data-stu-id="6f728-149">Creates an <xref:Microsoft.Extensions.Hosting.IHostBuilder> instance with the [default binder settings](generic-host.md#default-builder-settings).</span></span>
- <span data-ttu-id="6f728-150">サービスを構成し、対応するサービスの有効期間を指定してそれらを追加する。</span><span class="sxs-lookup"><span data-stu-id="6f728-150">Configures services and adds them with their corresponding service lifetime.</span></span>
- <span data-ttu-id="6f728-151"><xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> を呼び出して、<xref:Microsoft.Extensions.Hosting.IHost> のインスタンスを割り当てる。</span><span class="sxs-lookup"><span data-stu-id="6f728-151">Calls <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> and assigns an instance of <xref:Microsoft.Extensions.Hosting.IHost>.</span></span>
- <span data-ttu-id="6f728-152">`ExemplifyScoping` を呼び出して、<xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType> を渡す。</span><span class="sxs-lookup"><span data-stu-id="6f728-152">Calls `ExemplifyScoping`, passing in the <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType>.</span></span>

## <a name="conclusion"></a><span data-ttu-id="6f728-153">まとめ</span><span class="sxs-lookup"><span data-stu-id="6f728-153">Conclusion</span></span>

<span data-ttu-id="6f728-154">このアプリには、以下の例に示したような出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f728-154">The app displays output similar to the following example:</span></span>

```console
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ 80f4...Always different        ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ f3c0...Always different        ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]

Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ f9af...Always different        ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ fa65...Always different        ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
```

<span data-ttu-id="6f728-155">アプリの出力から、次のことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="6f728-155">From the app output, you can see that:</span></span>

- <span data-ttu-id="6f728-156">Transient 操作は常に異なり、サービスを取得するたびに新しいインスタンスが作成される。</span><span class="sxs-lookup"><span data-stu-id="6f728-156">Transient operations are always different, a new instance is created with every retrieval of the service.</span></span>
- <span data-ttu-id="6f728-157">Scoped 操作はスコープが新しくなった場合にのみ変更されますが、スコープ内では同じインスタンスである。</span><span class="sxs-lookup"><span data-stu-id="6f728-157">Scoped operations change only with a new scope, but are the same instance within a scope.</span></span>
- <span data-ttu-id="6f728-158">Singleton 操作は常に同じであり、新しいインスタンスは一度作成されるだけである。</span><span class="sxs-lookup"><span data-stu-id="6f728-158">Singleton operations are always the same, a new instance is only created once.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f728-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f728-159">See also</span></span>

* [<span data-ttu-id="6f728-160">依存関係の挿入のガイドライン</span><span class="sxs-lookup"><span data-stu-id="6f728-160">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
* [<span data-ttu-id="6f728-161">ASP.NET Core での依存関係の挿入</span><span class="sxs-lookup"><span data-stu-id="6f728-161">Dependency injection in ASP.NET Core</span></span>](/aspnet/core/fundamentals/dependency-injection)
