---
title: ASP.NET MVC と ASP.NET Core での依存関係の挿入の相違点
description: ASP.NET MVC と ASP.NET Core での依存関係の挿入のしくみ、相違点、ASP.NET MVC から ASP.NET Core への移行方法について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: aa1c7dd2f70e1a545352feb6560177bc6e2baa2d
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401390"
---
# <a name="dependency-injection-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core での依存関係の挿入の相違点

依存関係の挿入 (DI) は ASP.NET MVC にも Web API にも組み込まれていませんが、多くのアプリでは、制御の反転 (IOC) コンテナーを含む NuGet パッケージを追加することでこれを実現します。 これらは DI コンテナーと呼ばれることもあります。DI は、依存関係の挿入 (または反転) を意味します。 ASP.NET MVC アプリで使用される最も一般的なコンテナーとして、次のものがあります。

- [Autofac](https://www.autofac.org/)
- [Unity](https://unitycontainer.github.io/)
- [Ninject](http://www.ninject.org/)
- [StructureMap](http://structuremap.github.io/) *(非推奨)*
- [Castle Windsor](http://www.castleproject.org/projects/windsor/)

ASP.NET MVC アプリで DI を使用していない場合は、ASP.NET Core に組み込まれている DI のサポートについて調べることをお勧めします。 DI により、アプリ内のモジュールの疎結合が促進され、テストの容易性と、[堅牢性](https://www.weeklydevtips.com/episodes/047)などの原則への準拠が向上します。

アプリで DI を使用している場合は、使用中のコンテナーで ASP.NET Core がサポートされているかどうかを確認するのが最善の方法でしょう。 サポートされていれば、型のマッピングと有効期間を記述したカスタム構成規則と共にそれを引き続き使用できます。

いずれの場合も、ASP.NET Core に付属している組み込みの DI のサポートでアプリのニーズを満たせる可能性があるため、その使用を検討する必要があります。

## <a name="dependency-injection-in-aspnet-core"></a>ASP.NET Core での依存関係の挿入

ASP.NET Core は、アプリで DI を使用することを前提としています。 これはフレームワークに組み込まれているだけでなく、ASP.NET Core アプリにフレームワークの機能のサポートを導入するために必要です。 アプリの起動時に、DI コンテナー (サービス コレクション/サービス プロバイダー) が作成してアプリに挿入することができるすべての型を登録するための `ConfigureServices` の呼び出しが行われます。 Entity Framework Core、Identity、MVC などの組み込みの ASP.NET Core 機能は、`ConfigureServices` メソッド内でサービスとして構成することでアプリに導入されます。

既定の実装の使用に加えて、アプリでカスタム コンテナーを使用することも可能です。 [既定のサービス コンテナーを置き換える方法については、ドキュメントを参照してください](../../core/extensions/dependency-injection-guidelines.md#default-service-container-replacement)。

DI は ASP.NET Core の基盤となるものです。 チームがその実践に精通していない場合は、アプリを移植する前に理解しておくことをお勧めします。

## <a name="references"></a>リファレンス

- [.NET での依存関係の挿入](../../core/extensions/dependency-injection.md)
- [ASP.NET Core での依存関係の挿入](/aspnet/core/fundamentals/dependency-injection)

>[!div class="step-by-step"]
>[前へ](serving-static-files.md)
>[次へ](middleware-modules-handlers.md)
