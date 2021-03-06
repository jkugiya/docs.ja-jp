---
title: ASP.NET MVC と ASP.NET Core 間のテストオプションを比較する
description: ASP.NET MVC アプリと ASP.NET Core アプリでは、テストはどのように異なりますか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: f0907d09df058c07ed993c251868f00bc28b0736
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401346"
---
# <a name="compare-testing-options-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core 間のテストオプションを比較する

ASP.NET MVC アプリはコントローラーの単体テストをサポートしていますが、このアプローチでは多くの場合、ルーティング、承認、モデルバインド、モデル検証、フィルターなどの多くの MVC 機能が省略されます。 コントローラーアクション自体内のロジックに加えてこれらの MVC 機能をテストするには、多くの場合、アプリをデプロイし、Selenium などのツールでテストする必要があります。 これらのテストは、アプリ全体をホストして実行しなくても、実行できる一般的な単体テストよりもはるかにコストが高く、不安定で、動作が遅くなります。

[ASP.NET Core コントローラー](/aspnet/core/mvc/controllers/testing) は、ASP.NET MVC コントローラーと同様に単体テストが可能ですが、同じ制限があります。 ただし、 [ASP.NET Core は、高速で使いやすい統合テストもサポート](/aspnet/core/test/integration-tests) しています。 統合テストはクラスによってホストされ、 `TestHost` 通常は、 `WebApplicationFactory` アプリの依存関係をオーバーライドまたは置き換えることができるカスタムで構成されます。 たとえば、統合テスト中に多くの場合、アプリは別のデータソースを対象とし、フェイクまたはモックの実装で電子メールを送信するサービスを置き換えることができます。

ASP.NET MVC および Web API は、ASP.NET Core で使用できる統合テストシナリオのようなものをサポートしていませんでした。 移行作業では、新しく移行されたシステムの統合テストを作成するための時間を割り当てて、想定どおりに動作することを確認し、そのまま続行する必要があります。 移行の前に web アプリのロジックのテストを作成していない場合でも、ASP.NET Core に移行する際には、これを行うことを強くお勧めします。

## <a name="references"></a>関連項目

- [ASP.NET MVC アプリケーションの単体テストを作成する](/aspnet/mvc/overview/older-versions-1/unit-testing/creating-unit-tests-for-asp-net-mvc-applications-cs)
- [ASP.NET Core でコントローラーのロジックの単体テストを行う](/aspnet/core/mvc/controllers/testing)
- [ASP.NET Core での統合テスト](/aspnet/core/test/integration-tests)

>[!div class="step-by-step"]
>[前へ](signalr-differences.md)
>[次へ](migrate-large-solutions.md)
