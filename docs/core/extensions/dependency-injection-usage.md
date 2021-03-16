---
title: .NET で依存関係の挿入を使用する
description: .NET アプリケーションで依存関係の挿入を使用する方法について説明します。
author: IEvangelist
ms.author: dapine
ms.date: 11/13/2020
ms.topic: tutorial
no-loc:
- Transient
- Scoped
- Singleton
- Example
ms.openlocfilehash: d6654d5d1c8f7959e96998c18a1790cce46ebf41
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102402160"
---
# <a name="tutorial-use-dependency-injection-in-net"></a>チュートリアル: .NET で依存関係の挿入を使用する

このチュートリアルでは、[.NET で依存関係の挿入 (DI)](dependency-injection.md) を使用する方法について説明します。 "*Microsoft 拡張機能*" の場合、DI は最も重要視されるものであり、それによって <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> にサービスが追加され構成されます。 <xref:Microsoft.Extensions.Hosting.IHost> インターフェイスには <xref:System.IServiceProvider> インスタンスが公開されています。これは、登録されたすべてのサービスのコンテナーとして機能します。

このチュートリアルでは、以下の内容を学習します。

> [!div class="checklist"]
>
> - 依存関係の挿入を使用する .NET コンソール アプリを作成する
> - [汎用ホスト](generic-host.md)を構築して構成する
> - いくつかのインターフェイスとそれに対応する実装を記述する
> - DI のサービス有効期間とスコープを使用する

## <a name="prerequisites"></a>前提条件

- [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) 以降。
- 新しい .NET アプリケーションの作成と NuGet パッケージのインストールに関する知識。

## <a name="create-a-new-console-application"></a>新しいコンソール アプリケーションを作成する

[dotnet new](../tools/dotnet-new.md) コマンドまたは IDE の新しいプロジェクト ウィザードのいずれかを使用して、**ConsoleDI.Example** という名前の新しい .NET コンソール アプリケーションを作成します。 NuGet パッケージ [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) をプロジェクトに追加します。

## <a name="add-interfaces"></a>インターフェイスを追加する

次のインターフェイスをプロジェクトのルート ディレクトリに追加します。

*IOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

`IOperation` インターフェイスでは、単一の `OperationId` プロパティを定義します。

*ITransientOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/ITransientOperation.cs":::

*IScopedOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/IScopedOperation.cs":::

*ISingletonOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/ISingletonOperation.cs":::

`IOperation` のすべてのサブインターフェイスで、意図するサービスの有効期間を指定します。 たとえば、"Transient" や "Singleton" とします。

## <a name="add-default-implementation"></a>既定の実装を追加する

さまざまな操作に対して次の既定の実装を追加します。

*DefaultOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

`DefaultOperation` によって、すべての名前付きマーカー インターフェイスが実装され、`OperationId` プロパティが新しいグローバル一意識別子 (GUID) の最後の 4 文字に初期化されます。

## <a name="add-service-that-requires-di"></a>DI を必要とするサービスを追加する

次の操作ロガー オブジェクトを追加します。これは、コンソール アプリに対するサービスとして機能します。

*OperationLogger.cs*

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

`OperationLogger` には、前述の各マーカー インターフェイス (つまり、`ITransientOperation`、`IScopedOperation`、および `ISingletonOperation`) を必要とするコンストラクターを定義します。 このオブジェクトによって、指定された `scope` パラメーターを使用してコンシューマーが操作をログできるようにする 1 つのメソッドが公開されます。 `LogOperations` メソッドを呼び出すと、各操作の一意識別子がスコープの文字列とメッセージと共にログされます。

## <a name="register-services-for-di"></a>DI 用のサービスを登録する

次のコードを使用して *Program.cs* を更新します。

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

> 各 `services.Add{SERVICE_NAME}` 拡張メソッドによって、サービスが追加、場合によっては構成されます。 アプリをこの規則に従わせることをお勧めします。 拡張メソッドを <xref:Microsoft.Extensions.DependencyInjection?displayProperty=fullName> 名前空間に配置して、サービス登録のグループをカプセル化します。 DI 拡張メソッド用の名前空間部分として `Microsoft.Extensions.DependencyInjection` を含めると、次のようになります。
>
> - `using` ブロックを追加しなくても、それらを [IntelliSense](/visualstudio/ide/using-intellisense) で表示することができます。
> - それらの拡張メソッドの通常の呼び出し元である `Program` または `Startup` クラス内で `using` ステートメントが過剰になることはありません。

このアプリによって次のことが行われます。

- [既定のバインダー設定](generic-host.md#default-builder-settings)で <xref:Microsoft.Extensions.Hosting.IHostBuilder> インスタンスを作成する。
- サービスを構成し、対応するサービスの有効期間を指定してそれらを追加する。
- <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> を呼び出して、<xref:Microsoft.Extensions.Hosting.IHost> のインスタンスを割り当てる。
- `ExemplifyScoping` を呼び出して、<xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType> を渡す。

## <a name="conclusion"></a>まとめ

このアプリには、以下の例に示したような出力が表示されます。

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

アプリの出力から、次のことを確認できます。

- Transient 操作は常に異なり、サービスを取得するたびに新しいインスタンスが作成される。
- Scoped 操作はスコープが新しくなった場合にのみ変更されますが、スコープ内では同じインスタンスである。
- Singleton 操作は常に同じであり、新しいインスタンスは一度作成されるだけである。

## <a name="see-also"></a>関連項目

* [依存関係の挿入のガイドライン](dependency-injection-guidelines.md)
* [ASP.NET Core での依存関係の挿入](/aspnet/core/fundamentals/dependency-injection)
