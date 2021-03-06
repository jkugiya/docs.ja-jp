---
title: まとめ
description: ASP.NET MVC および Web API 2 アプリを ASP.NET Core に移植するための概要と主要な事項のセット。
author: ardalis
ms.date: 12/16/2020
ms.openlocfilehash: 596ab8621008d1cdc16d841e8faede5f4a1fdd16
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "102401275"
---
# <a name="summary"></a>まとめ

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

この本では、.NET Framework で実行されている組織の既存の ASP.NET アプリを ASP.NET Core に移植することが理にかなっているかどうかを判断するために必要なリソースを提供しました。 .NET Core に移行することが理にかなっているかを選択するための [重要な考慮事項](migration-considerations.md) について説明しました。また、アプリを .NET Framework に保持することが適切な場合もあります。 .NET Core のバージョンとその機能、および .NET Framework との間に違いがあり、 [アプリに適したバージョンの .Net core を選択する方法につい](choose-net-core-version.md)て学習しました。

多くの場合、大規模なアプリの移植には、かなりのリスクと労力が伴います。 このリスクを軽減する方法については、1つまたは複数の [増分移行戦略](incremental-migration-strategies.md) と、部分的に移行されたアプリを運用環境で実行するためのいくつかの [展開方法](deployment-strategies.md) を採用しています。

[ASP.NET と ASP.NET Core](architectural-differences.md)には、さまざまなアーキテクチャ上の違いがあります。 第2章では、これらの違いの多くと、アプリの移行にどのように関連するかについて学習しました。 この章では、 [アプリの起動](app-startup-differences.md) と低レベルの [ミドルウェア](middleware-modules-handlers.md) から高レベルの [コントローラー](controller-differences.md) と [Web API の違い](webapi-differences.md) について説明し、新しい機能を使用して [より優れたテストシナリオ](testing-differences.md)を実現します。

大規模なアプリは多くのプロジェクトとパッケージで構成されており、依存関係は、移行が簡単かどうかを判断するうえで大きな役割を果たします。 [第3章](migrate-large-solutions.md)[では、プロジェクトを移行する順序を特定](identify-migration-sequence.md)し、[アプリの依存関係を理解し、更新する方法を説明](understand-update-dependencies.md)しました。 また、 [運用環境での実行を維持しながら、アプリを移行するための追加の方法](strategies-migrating-in-production.md)も詳しく説明します。

[4 章では、実際の ASP.NET MVC 参照アプリが ASP.NET Core に移行された方法を説明しまし](example-migration-eshop.md)た。 この章には、既存のアプリを実行するために必要なすべての変更の詳細な内訳と、ASP.NET Core で実行するためのポートが含まれています。 移植プロセスに関する具体的な質問がある場合は、それについての説明を参照してください。

最後に、 [IIS に重点を置いた詳細な特定の展開シナリオについて説明](deployment-scenarios.md)します。 既存の IIS web サーバーを使用して、アプリのパブリック Url の整合性を維持しながら ASP.NET Core に移植されたアプリの一部をホストする方法について説明しました。 IIS には、URL の書き換えと要求のルーティングに関する優れたサポートが含まれています。これにより、アプリケーションが公開する公開 Url を変更することなく、サイトの複数のバージョンを並行して、または異なるサーバー上でホストできます。

>[!div class="step-by-step"]
>[[戻る]](deployment-scenarios.md)
