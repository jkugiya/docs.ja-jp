---
title: まとめ
description: ASP.NET MVC アプリと Web API 2 アプリの ASP.NET Core への移植に関する概要と一連の重要事項。
author: ardalis
ms.date: 12/16/2020
ms.openlocfilehash: 596ab8621008d1cdc16d841e8faede5f4a1fdd16
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "102401275"
---
# <a name="summary"></a>まとめ

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

本書では、組織の .NET Framework 上で実行されている既存の ASP.NET アプリを ASP.NET Core に移植することが理にかなっているかどうかを判断するために必要なリソースを示しました。 .NET Core に移行することが理にかなっている場合と、アプリ (の一部) を .NET Framework 上で保持することが適切と思われる場合を選別するための[重要な考慮事項](migration-considerations.md)について説明しました。 .NET Core のバージョン間で、機能や .NET Framework との互換性に違いがあるため、[アプリに適した .NET Core のバージョンを選択する方法](choose-net-core-version.md)について説明しました。

多くの場合、大規模なアプリの移植にはかなりのリスクと作業量が伴います。 1 つまたは複数の[段階的な移行戦略](incremental-migration-strategies.md)と、部分的に移行したアプリを運用環境で実行し続けるためのいくつかの[展開戦略](deployment-strategies.md)を併用することでこのリスクを軽減する方法について説明しました。

[ASP.NET と ASP.NET Core の間には、アーキテクチャの相違点](architectural-differences.md)が数多くあります。 第 2 章では、これらの相違点の多くについて説明し、それがアプリの移行にどのように関連するかを示しました。 この章では、[アプリの起動](app-startup-differences.md)と低レベルの[ミドルウェア](middleware-modules-handlers.md)から高レベルの[コントローラー](controller-differences.md)、[Web API の相違点](webapi-differences.md)、[より優れたテスト シナリオ](testing-differences.md)を実現する新機能に至るまで、幅広く説明しています。

大規模なアプリは多くの場合、多数のプロジェクトとパッケージで構成されており、移行の難易度を判断するうえで依存関係が重要な役割を果たします。 [第 3 章](migrate-large-solutions.md)では、[プロジェクトを移行する順序の確認](identify-migration-sequence.md)と、[アプリの依存関係を把握し、更新する方法](understand-update-dependencies.md)について説明しました。 また、[アプリを運用環境で実行し続けながら移行するためのその他の戦略](strategies-migrating-in-production.md)についても詳しく説明しました。

[第 4 章では、実際の ASP.NET MVC 参照アプリを ASP.NET Core に移行する方法を示しました](example-migration-eshop.md)。 この章では、既存のアプリを移植して ASP.NET Core 上で実行できるようにするために必要なすべての変更について詳しく説明しました。 移植プロセスやその詳細についての疑問点が生じた場合は、これを再度参照してください。

最後に、[第 5 章では、IIS に重点を置いた特定の展開シナリオについて詳しく説明しました](deployment-scenarios.md)。 既存の IIS Web サーバーを使用して、アプリの ASP.NET Core に移植されている部分を、アプリのパブリック URL の一貫性を維持したままホストする方法を示しました。 IIS には URL リライトと要求ルーティングに関する優れたサポートが含まれているので、アプリによって公開されるパブリック URL に変更を加えることなく、サイトの複数のバージョンをサイドバイサイドでホストしたり別々のサーバー上でホストしたりできます。

>[!div class="step-by-step"]
>[[戻る]](deployment-scenarios.md)
