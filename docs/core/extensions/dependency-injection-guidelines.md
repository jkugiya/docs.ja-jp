---
title: 依存関係の挿入のガイドライン
description: さまざまな依存関係の挿入のガイドラインと、.NET アプリケーション開発のベスト プラクティスについて説明します。
author: IEvangelist
ms.author: dapine
ms.date: 10/29/2020
ms.topic: guide
ms.openlocfilehash: 105536df873829dc79dcca1b86d080360e71303f
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "102402148"
---
# <a name="dependency-injection-guidelines"></a><span data-ttu-id="9fce1-103">依存関係の挿入のガイドライン</span><span class="sxs-lookup"><span data-stu-id="9fce1-103">Dependency injection guidelines</span></span>

<span data-ttu-id="9fce1-104">この記事では、.NET アプリケーションで依存関係の挿入を実装するための一般的なガイドラインとベスト プラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9fce1-104">This article provides general guidelines and best practices for implementing dependency injection in .NET applications.</span></span>

## <a name="design-services-for-dependency-injection"></a><span data-ttu-id="9fce1-105">依存関係の挿入のためのサービスの設計</span><span class="sxs-lookup"><span data-stu-id="9fce1-105">Design services for dependency injection</span></span>

<span data-ttu-id="9fce1-106">依存関係の挿入のためのサービスの設計時には:</span><span class="sxs-lookup"><span data-stu-id="9fce1-106">When designing services for dependency injection:</span></span>

- <span data-ttu-id="9fce1-107">ステートフル、静的クラス、およびメンバーは避けてください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-107">Avoid stateful, static classes and members.</span></span> <span data-ttu-id="9fce1-108">代わりにシングルトン サービスを使用するようにアプリを設計し、グローバルな状態を作成しないようにします。</span><span class="sxs-lookup"><span data-stu-id="9fce1-108">Avoid creating global state by designing apps to use singleton services instead.</span></span>
- <span data-ttu-id="9fce1-109">サービス内部で依存関係のあるクラスを直接インスタンス化することを回避します。</span><span class="sxs-lookup"><span data-stu-id="9fce1-109">Avoid direct instantiation of dependent classes within services.</span></span> <span data-ttu-id="9fce1-110">直接のインスタンス化は、コードの固有の実装につながります。</span><span class="sxs-lookup"><span data-stu-id="9fce1-110">Direct instantiation couples the code to a particular implementation.</span></span>
- <span data-ttu-id="9fce1-111">サービスを、小さく、十分に要素に分割された、テストしやすいものにします。</span><span class="sxs-lookup"><span data-stu-id="9fce1-111">Make services small, well-factored, and easily tested.</span></span>

<span data-ttu-id="9fce1-112">クラスに多数の挿入される依存関係がある場合、それは、クラスの責任が多すぎて、[単一責任の原則 (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility) に違反することを示している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9fce1-112">If a class has many injected dependencies, it might be a sign that the class has too many responsibilities and violates the [Single Responsibility Principle (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility).</span></span> <span data-ttu-id="9fce1-113">責任の一部を新しいクラスに移動することにより、クラスのリファクタリングを試みます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-113">Attempt to refactor the class by moving some of its responsibilities into new classes.</span></span>

### <a name="disposal-of-services"></a><span data-ttu-id="9fce1-114">サービスの破棄</span><span class="sxs-lookup"><span data-stu-id="9fce1-114">Disposal of services</span></span>

<span data-ttu-id="9fce1-115">コンテナーで作成された型のクリーンアップはコンテナーによって行われ、<xref:System.IDisposable> インスタンスで <xref:System.IDisposable.Dispose%2A> が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-115">The container is responsible for cleanup of types it creates, and calls <xref:System.IDisposable.Dispose%2A> on <xref:System.IDisposable> instances.</span></span> <span data-ttu-id="9fce1-116">コンテナーから解決されたサービスが、開発者によって破棄されることはありません。</span><span class="sxs-lookup"><span data-stu-id="9fce1-116">Services resolved from the container should never be disposed by the developer.</span></span> <span data-ttu-id="9fce1-117">型またはファクトリがシングルトンとして登録されている場合、コンテナーによってシングルトンが自動的に破棄されます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-117">If a type or factory is registered as a singleton, the container disposes the singleton automatically.</span></span>

<span data-ttu-id="9fce1-118">次の例では、サービスがサービス コンテナーによって作成され、自動的に破棄されます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-118">In the following example, the services are created by the service container and disposed automatically:</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/TransientDisposable.cs":::

<span data-ttu-id="9fce1-119">上の破棄は、一時的な有効期間を使用するためのものです。</span><span class="sxs-lookup"><span data-stu-id="9fce1-119">The preceding disposable is intended to have a transient lifetime.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/ScopedDisposable.cs":::

<span data-ttu-id="9fce1-120">上の破棄は、スコープ付きの有効期間を使用するためのものです。</span><span class="sxs-lookup"><span data-stu-id="9fce1-120">The preceding disposable is intended to have a scoped lifetime.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/SingletonDisposable.cs":::

<span data-ttu-id="9fce1-121">上の破棄は、シングルトン有効期間を使用するためのものです。</span><span class="sxs-lookup"><span data-stu-id="9fce1-121">The preceding disposable is intended to have a singleton lifetime.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/Program.cs" range="1-21,41-60" highlight="":::

<span data-ttu-id="9fce1-122">デバッグ コンソールには、実行後に次のサンプル出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-122">The debug console shows the following sample output after running:</span></span>

```console
Scope 1...
ScopedDisposable.Dispose()
TransientDisposable.Dispose()

Scope 2...
ScopedDisposable.Dispose()
TransientDisposable.Dispose()

info: Microsoft.Hosting.Lifetime[0]
      Application started.Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
     Hosting environment: Production
info: Microsoft.Hosting.Lifetime[0]
     Content root path: .\configuration\console-di-disposable\bin\Debug\net5.0
info: Microsoft.Hosting.Lifetime[0]
     Application is shutting down...
SingletonDisposable.Dispose()
```

### <a name="services-not-created-by-the-service-container"></a><span data-ttu-id="9fce1-123">サービス コンテナーによって作成されていないサービス</span><span class="sxs-lookup"><span data-stu-id="9fce1-123">Services not created by the service container</span></span>

<span data-ttu-id="9fce1-124">次のコードがあるとします。</span><span class="sxs-lookup"><span data-stu-id="9fce1-124">Consider the following code:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSingleton(new ExampleService());

    // ...
}
```

<span data-ttu-id="9fce1-125">上のコードでは以下の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-125">In the preceding code:</span></span>

- <span data-ttu-id="9fce1-126">サービス コンテナーにより、`ExampleService` インスタンスが作成されることは **ありません**。</span><span class="sxs-lookup"><span data-stu-id="9fce1-126">The `ExampleService` instance is **not** created by the service container.</span></span>
- <span data-ttu-id="9fce1-127">フレームワークにより、サービスが自動的に破棄されることは **ありません**。</span><span class="sxs-lookup"><span data-stu-id="9fce1-127">The framework does **not** dispose of the services automatically.</span></span>
- <span data-ttu-id="9fce1-128">サービスを破棄する責任は開発者にあります。</span><span class="sxs-lookup"><span data-stu-id="9fce1-128">The developer is responsible for disposing the services.</span></span>

### <a name="idisposable-guidance-for-transient-and-shared-instances"></a><span data-ttu-id="9fce1-129">一時的なインスタンスと共有インスタンスのための IDisposable ガイダンス</span><span class="sxs-lookup"><span data-stu-id="9fce1-129">IDisposable guidance for Transient and shared instances</span></span>

#### <a name="transient-limited-lifetime"></a><span data-ttu-id="9fce1-130">一時的で限定的な有効期間</span><span class="sxs-lookup"><span data-stu-id="9fce1-130">Transient, limited lifetime</span></span>

<span data-ttu-id="9fce1-131">**シナリオ**</span><span class="sxs-lookup"><span data-stu-id="9fce1-131">**Scenario**</span></span>

<span data-ttu-id="9fce1-132">アプリには、次のいずれかのシナリオに対して一時的な有効期間を持つ <xref:System.IDisposable> インスタンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="9fce1-132">The app requires an <xref:System.IDisposable> instance with a transient lifetime for either of the following scenarios:</span></span>

- <span data-ttu-id="9fce1-133">インスタンスは、ルート スコープ (ルート コンテナー) で解決されます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-133">The instance is resolved in the root scope (root container).</span></span>
- <span data-ttu-id="9fce1-134">インスタンスは、スコープが終了する前に破棄する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fce1-134">The instance should be disposed before the scope ends.</span></span>

<span data-ttu-id="9fce1-135">**解決方法**</span><span class="sxs-lookup"><span data-stu-id="9fce1-135">**Solution**</span></span>

<span data-ttu-id="9fce1-136">ファクトリ パターンを使用して、親スコープの外部にインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9fce1-136">Use the factory pattern to create an instance outside of the parent scope.</span></span> <span data-ttu-id="9fce1-137">このような状況では、通常、アプリケーションには、最終的な型のコンストラクターを直接呼び出す `Create` メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="9fce1-137">In this situation, the app would generally have a `Create` method that calls the final type's constructor directly.</span></span> <span data-ttu-id="9fce1-138">最終的な型に他の依存関係がある場合、ファクトリは次のことができます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-138">If the final type has other dependencies, the factory can:</span></span>

- <span data-ttu-id="9fce1-139">そのコンストラクターで <xref:System.IServiceProvider> を受け取る。</span><span class="sxs-lookup"><span data-stu-id="9fce1-139">Receive an <xref:System.IServiceProvider> in its constructor.</span></span>
- <span data-ttu-id="9fce1-140"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> を使用してコンテナー外部でインスタンスをインスタンス化し、同時にコンテナーを依存関係のために使用する。</span><span class="sxs-lookup"><span data-stu-id="9fce1-140">Use <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> to instantiate the instance outside of the container, while using the container for its dependencies.</span></span>

#### <a name="shared-instance-limited-lifetime"></a><span data-ttu-id="9fce1-141">共有インスタンス、限定的な有効期間</span><span class="sxs-lookup"><span data-stu-id="9fce1-141">Shared instance, limited lifetime</span></span>

<span data-ttu-id="9fce1-142">**シナリオ**</span><span class="sxs-lookup"><span data-stu-id="9fce1-142">**Scenario**</span></span>

<span data-ttu-id="9fce1-143">アプリでは、複数のサービスにわたって共有 <xref:System.IDisposable> インスタンスが必要ですが、<xref:System.IDisposable> インスタンスの有効期間は限られています。</span><span class="sxs-lookup"><span data-stu-id="9fce1-143">The app requires a shared <xref:System.IDisposable> instance across multiple services, but the <xref:System.IDisposable> instance should have a limited lifetime.</span></span>

<span data-ttu-id="9fce1-144">**解決方法**</span><span class="sxs-lookup"><span data-stu-id="9fce1-144">**Solution**</span></span>

<span data-ttu-id="9fce1-145">インスタンスをスコープ付きの有効期間で登録します。</span><span class="sxs-lookup"><span data-stu-id="9fce1-145">Register the instance with a scoped lifetime.</span></span> <span data-ttu-id="9fce1-146"><xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> を使用して新しい <xref:Microsoft.Extensions.DependencyInjection.IServiceScope>を作成します。</span><span class="sxs-lookup"><span data-stu-id="9fce1-146">Use <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> to create a new <xref:Microsoft.Extensions.DependencyInjection.IServiceScope>.</span></span> <span data-ttu-id="9fce1-147">スコープの <xref:System.IServiceProvider> を使用して必要なサービスを取得します。</span><span class="sxs-lookup"><span data-stu-id="9fce1-147">Use the scope's <xref:System.IServiceProvider> to get required services.</span></span> <span data-ttu-id="9fce1-148">不要になったスコープを破棄します。</span><span class="sxs-lookup"><span data-stu-id="9fce1-148">Dispose the scope when it's no longer needed.</span></span>

#### <a name="general-idisposable-guidelines"></a><span data-ttu-id="9fce1-149">`IDisposable` の一般的なガイドライン</span><span class="sxs-lookup"><span data-stu-id="9fce1-149">General `IDisposable` guidelines</span></span>

- <span data-ttu-id="9fce1-150"><xref:System.IDisposable> インスタンスは、一時的な有効期間で登録しないでください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-150">Don't register <xref:System.IDisposable> instances with a transient lifetime.</span></span> <span data-ttu-id="9fce1-151">代わりに、ファクトリ パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="9fce1-151">Use the factory pattern instead.</span></span>
- <span data-ttu-id="9fce1-152">一時的またはスコープ付きの有効期間の <xref:System.IDisposable> インスタンスをルート スコープ内で解決しないでください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-152">Don't resolve <xref:System.IDisposable> instances with a transient or scoped lifetime in the root scope.</span></span> <span data-ttu-id="9fce1-153">唯一の例外は、アプリが <xref:System.IServiceProvider> を作成/再作成し、破棄する場合ですが、これは理想的なパターンではありません。</span><span class="sxs-lookup"><span data-stu-id="9fce1-153">The only exception to this is if the app creates/recreates and disposes <xref:System.IServiceProvider>, but this isn't an ideal pattern.</span></span>
- <span data-ttu-id="9fce1-154">DI を使用して <xref:System.IDisposable> 依存関係を受け取る場合、受信側が <xref:System.IDisposable> 自体を実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9fce1-154">Receiving an <xref:System.IDisposable> dependency via DI doesn't require that the receiver implement <xref:System.IDisposable> itself.</span></span> <span data-ttu-id="9fce1-155"><xref:System.IDisposable> 依存関係の受信側は、その依存関係で <xref:System.IDisposable.Dispose%2A> を呼び出してはなりません。</span><span class="sxs-lookup"><span data-stu-id="9fce1-155">The receiver of the <xref:System.IDisposable> dependency shouldn't call <xref:System.IDisposable.Dispose%2A> on that dependency.</span></span>
- <span data-ttu-id="9fce1-156">サービスの有効期間を制御するには、スコープを使用します。</span><span class="sxs-lookup"><span data-stu-id="9fce1-156">Use scopes to control the lifetimes of services.</span></span> <span data-ttu-id="9fce1-157">スコープは階層構造ではなく、スコープ間に特別な接続はありません。</span><span class="sxs-lookup"><span data-stu-id="9fce1-157">Scopes aren't hierarchical, and there's no special connection among scopes.</span></span>

<span data-ttu-id="9fce1-158">リソースのクリーンアップの詳細については、「[`Dispose` メソッドの実装](../../standard/garbage-collection/implementing-dispose.md)」または「[`DisposeAsync` メソッドの実装](../../standard/garbage-collection/implementing-disposeasync.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-158">For more information on resource cleanup, see [Implement a `Dispose` method](../../standard/garbage-collection/implementing-dispose.md), or [Implement a `DisposeAsync` method](../../standard/garbage-collection/implementing-disposeasync.md).</span></span> <span data-ttu-id="9fce1-159">また、リソースのクリーンアップに関係があるので、「[コンテナーによってキャプチャされた破棄可能な一時サービス](#disposable-transient-services-captured-by-container)」のシナリオについても検討してください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-159">Additionally, consider the [Disposable transient services captured by container](#disposable-transient-services-captured-by-container) scenario as it relates to resource cleanup.</span></span>

## <a name="default-service-container-replacement"></a><span data-ttu-id="9fce1-160">既定のサービス コンテナーの置換</span><span class="sxs-lookup"><span data-stu-id="9fce1-160">Default service container replacement</span></span>

<span data-ttu-id="9fce1-161">組み込みのサービス コンテナーは、フレームワークと、ほとんどのコンシューマー アプリのニーズに対応することを目的としたものです。</span><span class="sxs-lookup"><span data-stu-id="9fce1-161">The built-in service container is designed to serve the needs of the framework and most consumer apps.</span></span> <span data-ttu-id="9fce1-162">次のようなサポートされない特定の機能が必要な場合でなければ、組み込みのコンテナーを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9fce1-162">We recommend using the built-in container unless you need a specific feature that it doesn't support, such as:</span></span>

- <span data-ttu-id="9fce1-163">プロパティの挿入</span><span class="sxs-lookup"><span data-stu-id="9fce1-163">Property injection</span></span>
- <span data-ttu-id="9fce1-164">名前に基づく挿入</span><span class="sxs-lookup"><span data-stu-id="9fce1-164">Injection based on name</span></span>
- <span data-ttu-id="9fce1-165">子コンテナー</span><span class="sxs-lookup"><span data-stu-id="9fce1-165">Child containers</span></span>
- <span data-ttu-id="9fce1-166">有効期間のカスタム管理</span><span class="sxs-lookup"><span data-stu-id="9fce1-166">Custom lifetime management</span></span>
- <span data-ttu-id="9fce1-167">遅延初期化に対する `Func<T>` のサポート</span><span class="sxs-lookup"><span data-stu-id="9fce1-167">`Func<T>` support for lazy initialization</span></span>
- <span data-ttu-id="9fce1-168">規則に基づく登録</span><span class="sxs-lookup"><span data-stu-id="9fce1-168">Convention-based registration</span></span>

<span data-ttu-id="9fce1-169">次のサードパーティ コンテナーは ASP.NET Core アプリで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-169">The following third-party containers can be used with ASP.NET Core apps:</span></span>

- [<span data-ttu-id="9fce1-170">Autofac</span><span class="sxs-lookup"><span data-stu-id="9fce1-170">Autofac</span></span>](https://autofac.readthedocs.io/en/latest/integration/aspnetcore.html)
- [<span data-ttu-id="9fce1-171">DryIoc</span><span class="sxs-lookup"><span data-stu-id="9fce1-171">DryIoc</span></span>](https://www.nuget.org/packages/DryIoc.Microsoft.DependencyInjection)
- [<span data-ttu-id="9fce1-172">Grace</span><span class="sxs-lookup"><span data-stu-id="9fce1-172">Grace</span></span>](https://www.nuget.org/packages/Grace.DependencyInjection.Extensions)
- [<span data-ttu-id="9fce1-173">LightInject</span><span class="sxs-lookup"><span data-stu-id="9fce1-173">LightInject</span></span>](https://github.com/seesharper/LightInject.Microsoft.DependencyInjection)
- [<span data-ttu-id="9fce1-174">Lamar</span><span class="sxs-lookup"><span data-stu-id="9fce1-174">Lamar</span></span>](https://jasperfx.github.io/lamar/)
- [<span data-ttu-id="9fce1-175">Stashbox</span><span class="sxs-lookup"><span data-stu-id="9fce1-175">Stashbox</span></span>](https://github.com/z4kn4fein/stashbox-extensions-dependencyinjection)
- [<span data-ttu-id="9fce1-176">Unity</span><span class="sxs-lookup"><span data-stu-id="9fce1-176">Unity</span></span>](https://www.nuget.org/packages/Unity.Microsoft.DependencyInjection)

## <a name="thread-safety"></a><span data-ttu-id="9fce1-177">スレッド セーフ</span><span class="sxs-lookup"><span data-stu-id="9fce1-177">Thread safety</span></span>

<span data-ttu-id="9fce1-178">スレッド セーフのシングルトン サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9fce1-178">Create thread-safe singleton services.</span></span> <span data-ttu-id="9fce1-179">シングルトン サービスに一時的なサービスへの依存関係がある場合、シングルトンによる使い方によっては、一時的なサービスもスレッド セーフであることが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="9fce1-179">If a singleton service has a dependency on a transient service, the transient service may also require thread safety depending on how it's used by the singleton.</span></span>

<span data-ttu-id="9fce1-180">シングルトン サービスのファクトリ メソッド (例: [AddSingleton\<TService>(IServiceCollection, Func\<IServiceProvider,TService>)](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A) に対する 2 番目の引数) を、スレッドセーフにする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9fce1-180">The factory method of a singleton service, such as the second argument to [AddSingleton\<TService>(IServiceCollection, Func\<IServiceProvider,TService>)](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), doesn't need to be thread-safe.</span></span> <span data-ttu-id="9fce1-181">型 (`static`) のコンストラクターのように、1 つのスレッドによって 1 回のみ呼び出されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-181">Like a type (`static`) constructor, it's guaranteed to be called only once by a single thread.</span></span>

## <a name="recommendations"></a><span data-ttu-id="9fce1-182">Recommendations</span><span class="sxs-lookup"><span data-stu-id="9fce1-182">Recommendations</span></span>

- <span data-ttu-id="9fce1-183">`async/await` および `Task` ベースのサービスの解決はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9fce1-183">`async/await` and `Task` based service resolution isn't supported.</span></span> <span data-ttu-id="9fce1-184">C# では非同期コンストラクターがサポートされていないため、非同期メソッドはサービスを同期的に解決した後に使用してください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-184">Because C# doesn't support asynchronous constructors, use asynchronous methods after synchronously resolving the service.</span></span>
- <span data-ttu-id="9fce1-185">データと構成をサービス コンテナーに直接格納しないようにします。</span><span class="sxs-lookup"><span data-stu-id="9fce1-185">Avoid storing data and configuration directly in the service container.</span></span> <span data-ttu-id="9fce1-186">たとえば、通常、ユーザーのショッピング カートはサービス コンテナーに追加しません。</span><span class="sxs-lookup"><span data-stu-id="9fce1-186">For example, a user's shopping cart shouldn't typically be added to the service container.</span></span> <span data-ttu-id="9fce1-187">構成では、オプション パターンを使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fce1-187">Configuration should use the options pattern.</span></span> <span data-ttu-id="9fce1-188">同様に、他のオブジェクトへのアクセスを許可するためだけに存在する "データ ホルダー" オブジェクトは避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fce1-188">Similarly, avoid "data holder" objects that only exist to allow access to another object.</span></span> <span data-ttu-id="9fce1-189">実際のアイテムを DI 経由で要求することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9fce1-189">It's better to request the actual item via DI.</span></span>
- <span data-ttu-id="9fce1-190">サービスへの静的なアクセスを行わないようにします。</span><span class="sxs-lookup"><span data-stu-id="9fce1-190">Avoid static access to services.</span></span> <span data-ttu-id="9fce1-191">たとえば、他の場所で使用するために [IApplicationBuilder.ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) を静的フィールドまたはプロパティとしてキャプチャしないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-191">For example, avoid capturing [IApplicationBuilder.ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) as a static field or property for use elsewhere.</span></span>
- <span data-ttu-id="9fce1-192">[DI ファクトリ](#async-di-factories-can-cause-deadlocks)の高速性と同期性を維持します。</span><span class="sxs-lookup"><span data-stu-id="9fce1-192">Keep [DI factories](#async-di-factories-can-cause-deadlocks) fast and synchronous.</span></span>
- <span data-ttu-id="9fce1-193">[*サービス ロケーター パターン*](#scoped-service-as-singleton)は使用しないようにします。</span><span class="sxs-lookup"><span data-stu-id="9fce1-193">Avoid using the [*service locator pattern*](#scoped-service-as-singleton).</span></span> <span data-ttu-id="9fce1-194">たとえば、サービス インスタンスを取得する場合、DI を使用できるときに、<xref:System.IServiceProvider.GetService%2A> を呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-194">For example, don't invoke <xref:System.IServiceProvider.GetService%2A> to obtain a service instance when you can use DI instead.</span></span>
- <span data-ttu-id="9fce1-195">回避すべき別のサービス ロケーターのバリエーションは、実行時に依存関係を解決するファクトリを挿入することです。</span><span class="sxs-lookup"><span data-stu-id="9fce1-195">Another service locator variation to avoid is injecting a factory that resolves dependencies at runtime.</span></span> <span data-ttu-id="9fce1-196">この両方のプラクティスによって、複数の[制御の反転](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion)方式が組み合わせられます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-196">Both of these practices mix [Inversion of Control](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion) strategies.</span></span>
- <span data-ttu-id="9fce1-197">`ConfigureServices` で <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> を呼び出すことは避けてください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-197">Avoid calls to <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> in `ConfigureServices`.</span></span> <span data-ttu-id="9fce1-198">`BuildServiceProvider` の呼び出しは、通常、開発者が `ConfigureServices` でサービスを解決する必要がある場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="9fce1-198">Calling `BuildServiceProvider` typically happens when the developer wants to resolve a service in `ConfigureServices`.</span></span>
- <span data-ttu-id="9fce1-199">[破棄可能な一時サービスは、破棄のためにコンテナーによってキャプチャ](#disposable-transient-services-captured-by-container)されます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-199">[Disposable transient services are captured](#disposable-transient-services-captured-by-container) by the container for disposal.</span></span> <span data-ttu-id="9fce1-200">これにより、最上位のコンテナーから解決された場合、メモリ リークが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9fce1-200">This can turn into a memory leak if resolved from the top-level container.</span></span>
- <span data-ttu-id="9fce1-201">スコープの検証を有効にすることで、アプリにスコープ付きサービスをキャプチャするシングルトンがないようにします。</span><span class="sxs-lookup"><span data-stu-id="9fce1-201">Enable scope validation to make sure the app doesn't have singletons that capture scoped services.</span></span> <span data-ttu-id="9fce1-202">詳しくは、「[スコープの検証](dependency-injection.md#scope-validation)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-202">For more information, see [Scope validation](dependency-injection.md#scope-validation).</span></span>

<span data-ttu-id="9fce1-203">どのような推奨事項であっても、それを無視する必要がある状況が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9fce1-203">Like all sets of recommendations, you may encounter situations where ignoring a recommendation is required.</span></span> <span data-ttu-id="9fce1-204">例外はまれです。ほとんどがフレームワーク自体の内の特殊なケースです。</span><span class="sxs-lookup"><span data-stu-id="9fce1-204">Exceptions are rare, mostly special cases within the framework itself.</span></span>

<span data-ttu-id="9fce1-205">DI は静的/グローバル オブジェクト アクセス パターンの *代替機能* です。</span><span class="sxs-lookup"><span data-stu-id="9fce1-205">DI is an *alternative* to static/global object access patterns.</span></span> <span data-ttu-id="9fce1-206">静的オブジェクト アクセスと併用した場合、DI のメリットを実現することはできません。</span><span class="sxs-lookup"><span data-stu-id="9fce1-206">You may not be able to realize the benefits of DI if you mix it with static object access.</span></span>

## <a name="example-anti-patterns"></a><span data-ttu-id="9fce1-207">アンチパターンの例</span><span class="sxs-lookup"><span data-stu-id="9fce1-207">Example anti-patterns</span></span>

<span data-ttu-id="9fce1-208">この記事のガイドラインに加えて、"\*回避する \*\*必要がある\*\*\*" アンチパターンがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="9fce1-208">In addition to the guidelines in this article, there are several anti-patterns *you **should** avoid*.</span></span> <span data-ttu-id="9fce1-209">このようなアンチパターンの一部は、ランタイム自体の開発によってわかることです。</span><span class="sxs-lookup"><span data-stu-id="9fce1-209">Some of these anti-patterns are learnings from developing the runtimes themselves.</span></span>

> [!WARNING]
> <span data-ttu-id="9fce1-210">これらはアンチパターンの例です。そのコードをコピー "*しないでください*"。これらのパターンを使用 "*しないでください*"。そして、これらのパターンは絶対に避けてください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-210">These are example anti-patterns, *do not* copy the code, *do not* use these patterns, and avoid these patterns at all costs.</span></span>

### <a name="disposable-transient-services-captured-by-container"></a><span data-ttu-id="9fce1-211">コンテナーによってキャプチャされる破棄可能な一時サービス</span><span class="sxs-lookup"><span data-stu-id="9fce1-211">Disposable transient services captured by container</span></span>

<span data-ttu-id="9fce1-212"><xref:System.IDisposable> が実装されている "*一時*" サービスを登録すると、既定では、アプリケーションが停止してコンテナーが破棄されるまで (コンテナーから解決された場合) またはスコープが破棄されるまで (スコープから解決された場合)、これらの <xref:System.IDisposable.Dispose> ではなく、これらの参照が DI コンテナーに保持されます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-212">When you register *Transient* services that implement <xref:System.IDisposable>, by default the DI container will hold onto these references, and not <xref:System.IDisposable.Dispose> of them until the container is disposed when application stops if they were resolved from the container, or until the scope is disposed if they were resolved from a scope.</span></span> <span data-ttu-id="9fce1-213">これにより、コンテナー レベルから解決された場合、メモリ リークが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9fce1-213">This can turn into a memory leak if resolved from container level.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="18-30":::

<span data-ttu-id="9fce1-214">前のアンチパターンでは、1,000 の `ExampleDisposable` オブジェクトがインスタンス化されてルート化されます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-214">In the preceding anti-pattern, 1,000 `ExampleDisposable` objects are instantiated and rooted.</span></span> <span data-ttu-id="9fce1-215">それらは、`serviceProvider` のインスタンスが破棄されるまで破棄されません。</span><span class="sxs-lookup"><span data-stu-id="9fce1-215">They will not be disposed of until the `serviceProvider` instance is disposed.</span></span>

<span data-ttu-id="9fce1-216">メモリ リークのデバッグの詳細については、[.NET でのメモリ リークのデバッグ](../diagnostics/debug-memory-leak.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-216">For more information on debugging memory leaks, see [Debug a memory leak in .NET](../diagnostics/debug-memory-leak.md).</span></span>

### <a name="async-di-factories-can-cause-deadlocks"></a><span data-ttu-id="9fce1-217">非同期 DI ファクトリでデッドロックが発生する可能性がある</span><span class="sxs-lookup"><span data-stu-id="9fce1-217">Async DI factories can cause deadlocks</span></span>

<span data-ttu-id="9fce1-218">"DI ファクトリ" とは、`Add{LIFETIME}` を呼び出すと存在するようになるオーバーロード メソッドのことです。</span><span class="sxs-lookup"><span data-stu-id="9fce1-218">The term "DI factories" refers to the overload methods that exist when calling `Add{LIFETIME}`.</span></span> <span data-ttu-id="9fce1-219">`Func<IServiceProvider, T>` を受け入れるオーバーロードがあります。`T` は登録されているサービスであり、パラメーターの名前は `implementationFactory` です。</span><span class="sxs-lookup"><span data-stu-id="9fce1-219">There are overloads accepting a `Func<IServiceProvider, T>` where `T` is the service being registered, and the parameter is named `implementationFactory`.</span></span> <span data-ttu-id="9fce1-220">`implementationFactory` は、ラムダ式、ローカル関数、またはメソッドとして提供できます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-220">The `implementationFactory` can be provided as a lambda expression, local function, or method.</span></span> <span data-ttu-id="9fce1-221">ファクトリが非同期であり、<xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> を使用している場合、デッドロックが発生します。</span><span class="sxs-lookup"><span data-stu-id="9fce1-221">If the factory is asynchronous, and you use <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType>, this will cause a deadlock.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="32-45" highlight="4-8":::

<span data-ttu-id="9fce1-222">前のコードでは、`implementationFactory` にラムダ式が提供され、その本体で `Task<Bar>` の <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> が呼び出されてメソッドが返されます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-222">In the preceding code, the `implementationFactory` is given a lambda expression where the body calls <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> on a `Task<Bar>` returning method.</span></span> <span data-ttu-id="9fce1-223">これにより、"***デッドロックが発生します***"。</span><span class="sxs-lookup"><span data-stu-id="9fce1-223">This ***causes a deadlock***.</span></span> <span data-ttu-id="9fce1-224">`GetBarAsync` メソッドは <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> で非同期操作を単にエミュレートしてから、<xref:Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService%60%601(System.IServiceProvider)> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9fce1-224">The `GetBarAsync` method simply emulates an asynchronous work operation with <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType>, and then calls <xref:Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService%60%601(System.IServiceProvider)>.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="47-53":::

<span data-ttu-id="9fce1-225">非同期ガイダンスの詳細については、「[非同期プログラミング: 重要な情報とアドバイス](../../csharp/async.md#important-info-and-advice)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-225">For more information on asynchronous guidance, see [Asynchronous programming: Important info and advice](../../csharp/async.md#important-info-and-advice).</span></span> <span data-ttu-id="9fce1-226">デッドロックのデバッグの詳細については、[.NET でのデッドロックのデバッグ](../diagnostics/debug-deadlock.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-226">For more information debugging deadlocks, see [Debug a deadlock in .NET](../diagnostics/debug-deadlock.md).</span></span>

<span data-ttu-id="9fce1-227">このアンチパターンを実行していてデッドロックが発生した場合は、Visual Studio の [並列スタック] ウィンドウで待機している 2 つのスレッドを確認できます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-227">When you're running this anti-pattern and the deadlock occurs, you can view the two threads waiting from Visual Studio's Parallel Stacks window.</span></span> <span data-ttu-id="9fce1-228">詳細については、「[[並列スタック] ウィンドウでスレッドを表示する](/visualstudio/debugger/using-the-parallel-stacks-window)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-228">For more information, see [View threads and tasks in the Parallel Stacks window](/visualstudio/debugger/using-the-parallel-stacks-window).</span></span>

### <a name="captive-dependency"></a><span data-ttu-id="9fce1-229">キャプティブ依存関係</span><span class="sxs-lookup"><span data-stu-id="9fce1-229">Captive dependency</span></span>

<span data-ttu-id="9fce1-230">[Mark Seeman](https://blog.ploeh.dk/about) によって作成された ["キャプティブ依存関係"](https://blog.ploeh.dk/2014/06/02/captive-dependency) という用語は、サービスの有効期間の誤った構成により、有効期間が長いサービスによって有効期間の短いサービスが捕獲されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9fce1-230">The term ["captive dependency"](https://blog.ploeh.dk/2014/06/02/captive-dependency) was coined by [Mark Seeman](https://blog.ploeh.dk/about), and refers to the misconfiguration of service lifetimes, where a longer-lived service holds a shorter-lived service captive.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="55-65":::

<span data-ttu-id="9fce1-231">上のコードで、`Foo` はシングルトンとして登録され、`Bar` はスコープ指定されています。これは表面上は有効であるように見えます。</span><span class="sxs-lookup"><span data-stu-id="9fce1-231">In the preceding code, `Foo` is registered as a singleton and `Bar` is scoped - which on the surface seems valid.</span></span> <span data-ttu-id="9fce1-232">しかし、`Foo` の実装を考えてみてください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-232">However, consider the implementation of `Foo`.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Foo.cs" highlight="5":::

<span data-ttu-id="9fce1-233">`Foo` オブジェクトには `Bar` オブジェクトが必要であり、`Foo` はシングルトンであるため、`Bar` はスコープ指定されます。これは不適切な構成です。</span><span class="sxs-lookup"><span data-stu-id="9fce1-233">The `Foo` object requires a `Bar` object, and since `Foo` is a singleton, and `Bar` is scoped - this is a misconfiguration.</span></span> <span data-ttu-id="9fce1-234">そのように、`Foo` は 1 回だけインスタンス化され、その有効期間にわたって `Bar` を保持します。これは、`Bar` の意図されるスコープ指定された有効期間より長くなります。</span><span class="sxs-lookup"><span data-stu-id="9fce1-234">As is, `Foo` would only be instantiated once, and it would hold onto `Bar` for its lifetime, which is longer than the intended scoped lifetime of `Bar`.</span></span> <span data-ttu-id="9fce1-235">`validateScopes: true` を <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Boolean)> に渡すことによって、スコープを検証することを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fce1-235">You should consider validating scopes, by passing `validateScopes: true` to the <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Boolean)>.</span></span> <span data-ttu-id="9fce1-236">スコープを検証すると、<xref:System.InvalidOperationException> と "シングルトン 'Foo' からスコープ指定されたサービス 'bar' を使用することはできません" のようなメッセージを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="9fce1-236">When you validate the scopes, you'd get an <xref:System.InvalidOperationException> with a message similar to "Cannot consume scoped service 'Bar' from singleton 'Foo'.".</span></span>

<span data-ttu-id="9fce1-237">詳しくは、「[スコープの検証](dependency-injection.md#scope-validation)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9fce1-237">For more information, see [Scope validation](dependency-injection.md#scope-validation).</span></span>

### <a name="scoped-service-as-singleton"></a><span data-ttu-id="9fce1-238">シングルトンとしてのスコープ指定されたサービス</span><span class="sxs-lookup"><span data-stu-id="9fce1-238">Scoped service as singleton</span></span>

<span data-ttu-id="9fce1-239">スコープ指定されたサービスを使用するとき、スコープを作成しない場合、または既存のスコープ内にいない場合は、サービスはシングルトンになります。</span><span class="sxs-lookup"><span data-stu-id="9fce1-239">When using scoped services, if you're not creating a scope or within an existing scope - the service becomes a singleton.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="68-82" highlight="13-14":::

<span data-ttu-id="9fce1-240">上のコードで、`Bar` は <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> 内で取得されており、これは正しいことです。</span><span class="sxs-lookup"><span data-stu-id="9fce1-240">In the preceding code, `Bar` is retrieved within an <xref:Microsoft.Extensions.DependencyInjection.IServiceScope>, which is correct.</span></span> <span data-ttu-id="9fce1-241">アンチパターンの場合は、`Bar` はスコープの外側で取得されており、どの例の取得が正しくないかを示すため、変数には `avoid` という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="9fce1-241">The anti-pattern is the retrieval of `Bar` outside of the scope, and the variable is named `avoid` to show which example retrieval is incorrect.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fce1-242">関連項目</span><span class="sxs-lookup"><span data-stu-id="9fce1-242">See also</span></span>

- [<span data-ttu-id="9fce1-243">.NET での依存関係の挿入</span><span class="sxs-lookup"><span data-stu-id="9fce1-243">Dependency injection in .NET</span></span>](dependency-injection.md)
- [<span data-ttu-id="9fce1-244">チュートリアル: .NET で依存関係の挿入を使用する</span><span class="sxs-lookup"><span data-stu-id="9fce1-244">Tutorial: Use dependency injection in .NET</span></span>](dependency-injection-usage.md)
