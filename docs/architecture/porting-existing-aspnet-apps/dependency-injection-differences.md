---
title: ASP.NET MVC と ASP.NET Core の依存関係挿入の違い
description: ASP.NET MVC と ASP.NET Core での依存関係の挿入のしくみ、それらの違い、および ASP.NET MVC から ASP.NET Core への移行方法について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: aa1c7dd2f70e1a545352feb6560177bc6e2baa2d
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401390"
---
# <a name="dependency-injection-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core の依存関係挿入の違い

依存関係の注入 (DI) は ASP.NET MVC または Web API には組み込まれていませんが、多くのアプリでは、コントロールの反転 (IOC) コンテナーを含む NuGet パッケージを追加することで有効になります。 これらは、依存関係の挿入 (または反転) のために DI コンテナーと呼ばれることもあります。 ASP.NET MVC アプリで使用される最も一般的なコンテナーには、次のものがあります。

- [Autofac](https://www.autofac.org/)
- [Unity](https://unitycontainer.github.io/)
- [Ninject](http://www.ninject.org/)
- [構造体マップ](http://structuremap.github.io/) *(非推奨)*
- [城 Windsor](http://www.castleproject.org/projects/windsor/)

ASP.NET MVC アプリで DI を使用していない場合は、ASP.NET Core で DI の組み込みサポートを調査することをお勧めします。 DI では、アプリ内のモジュールの疎結合が促進され、 [堅牢](https://www.weeklydevtips.com/episodes/047)性というような、より優れたテスト性と原則への準拠が可能になります。

アプリで DI を使用している場合は、使用しているコンテナーが ASP.NET Core をサポートしているかどうかを確認するのが最善の方法です。 その場合は、そのまま使用することも、型マッピングと有効期間を記述したカスタム構成ルールを使用することもできます。

どちらの場合も、ASP.NET Core に付属している DI の組み込みサポートを使用することを検討する必要があります。これは、アプリのニーズを満たす可能性があるためです。

## <a name="dependency-injection-in-aspnet-core"></a>ASP.NET Core での依存関係の挿入

ASP.NET Core は、アプリが DI を使用することを前提としています。 フレームワークに組み込まれているだけでなく、フレームワークの機能のサポートを ASP.NET Core アプリに導入するために必要です。 アプリの起動時に、 `ConfigureServices` DI コンテナー (サービスコレクション/サービスプロバイダー) が作成してアプリで挿入できるすべての型を登録するための呼び出しが行われます。 Entity Framework Core、Id、MVC などの組み込みの ASP.NET Core 機能は、メソッドでサービスとして構成することで、アプリに取り込まれ `ConfigureServices` ます。

既定の実装を使用するだけでなく、アプリでもカスタムコンテナーを使用できます。 このドキュメントでは、 [既定のサービスコンテナーを置き換える方法について説明](../../core/extensions/dependency-injection-guidelines.md#default-service-container-replacement)します。

DI は、ASP.NET Core の基礎となります。 チームがこの実践に精通していない場合は、アプリを移植する前に理解しておくことをお勧めします。

## <a name="references"></a>関連項目

- [.NET での依存関係の挿入](../../core/extensions/dependency-injection.md)
- [ASP.NET Core での依存関係の挿入](/aspnet/core/fundamentals/dependency-injection)

>[!div class="step-by-step"]
>[前へ](serving-static-files.md)
>[次へ](middleware-modules-handlers.md)
