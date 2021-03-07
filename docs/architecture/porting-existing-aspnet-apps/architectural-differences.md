---
title: ASP.NET MVC と ASP.NET Core のアーキテクチャの相違点
description: ASP.NET と ASP.NET Core のアーキテクチャの違いを確認します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 96477f2393482380eee9891e9b2dbbb6445e15bd
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401418"
---
# <a name="architectural-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core のアーキテクチャの相違点

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

.NET Framework と ASP.NET Core の ASP.NET MVC には、さまざまなアーキテクチャ上の違いがあります。 チームは、ASP.NET MVC アプリを ASP.NET Core に移植する際の作業を評価する際に、これらの違いについて幅広く理解しておくことが重要です。 この章では、ASP.NET MVC と ASP.NET Core が大きく異なる方法について説明します。

## <a name="breaking-changes"></a>重大な変更

.NET Core は、.NET Framework のクロスプラットフォームの書き換えです。 [2 つのフレームワーク間](../../core/compatibility/fx-core.md)には多くの重大な変更があります。 以下のセクションでは、ASP.NET MVC と ASP.NET Core アプリを設計および開発する方法の具体的な違いについて説明します。 また、ドキュメントを調べて、使用しているフレームワークライブラリを変更する必要があるかどうかを確認してください。 多くの場合、.NET Framework と .NET Core の間に残されているギャップを埋めるために、代替の NuGet パッケージが存在します。 まれなケースとして、サードパーティのソリューションを見つけたり、非互換性に対処するための新しいカスタムコードを実装したりする必要がある場合があります。

>[!div class="step-by-step"]
>[前へ](additional-migration-resources.md)
>[次へ](app-startup-differences.md)
