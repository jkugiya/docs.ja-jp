---
title: ASP.NET Web API 2 と ASP.NET Core の比較
description: ASP.NET Web API 2 つのアプリと ASP.NET Core アプリの間で web Api はどのように異なりますか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 93aa917174bce24fdf924f6372312c3972473289
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401344"
---
# <a name="compare-aspnet-web-api-2-and-aspnet-core"></a>ASP.NET Web API 2 と ASP.NET Core の比較

ASP.NET Core は ASP.NET Web API 2 に対する反復的な機能強化を提供しますが、Web API 2 を使用している開発者には慣れているはずです。 ASP.NET Web API 2 は ASP.NET MVC と共に開発および出荷されました。 このため、2つのアプローチには、属性ルーティングや依存関係の挿入など、似たような方法があります。 ASP.NET Core では、MVC と Web Api が区別されなくなりました。 ASP.NET MVC には、ビューベースのシナリオ、API エンドポイント、Razor Pages (および正常性チェックや SignalR などのその他のバリエーション) のサポートが含まれています。

.NET Core に組み込まれている Api は ASP.NET Core 内で一貫性と統合されるだけでなく、ASP.NET Web API 2 に構築された Api よりもはるかに簡単にテストできます。 [テストの違い](testing-differences.md)については、後で詳しく説明します。 アプリケーションに対してメモリ内の要求を行うを作成できるテストホストで ASP.NET Core アプリをホストするための組み込みのサポート `HttpClient` は、自動テストを行う場合に大きな利点となります。

ASP.NET Web API 2 から ASP.NET Core に移行する場合、移行は簡単です。 大規模な膨張コントローラーがある場合は、それを分割する方法の1つとして、パッケージを使用する方法があります[。](https://www.nuget.org/packages/Ardalis.ApiEndpoints/) このパッケージは、各エンドポイントを独自の特定のクラスに分割し、必要に応じて、要求と応答の種類を関連付けます。 このアプローチで [は、ビューベースのコード編成での Razor Pages プランと同じ特典](comparing-razor-pages-aspnet-mvc.md)の多くが得られます。

## <a name="references"></a>関連項目

- [ASP.NET Web API から ASP.NET Core への移行](/aspnet/core/migration/webapi)
- [シャードのエンドポイント NuGet パッケージ](https://www.nuget.org/packages/Ardalis.ApiEndpoints/)

>[!div class="step-by-step"]
>[前へ](comparing-razor-pages-aspnet-mvc.md)
>[次へ](authentication-differences.md)
