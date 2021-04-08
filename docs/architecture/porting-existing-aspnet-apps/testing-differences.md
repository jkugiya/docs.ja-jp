---
title: ASP.NET MVC と ASP.NET Core のテスト オプションの比較
description: ASP.NET MVC アプリと ASP.NET Core アプリでは、テストはどのように異なるでしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: f0907d09df058c07ed993c251868f00bc28b0736
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401346"
---
# <a name="compare-testing-options-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core のテスト オプションの比較

ASP.NET MVC アプリではコントローラーの単体テストがサポートされていますが、このアプローチでは多くの場合、ルーティング、認可、モデル バインド、モデル検証、フィルターなどの多くの MVC 機能が省略されます。 コントローラー アクション自体に含まれるロジックに加えてこれらの MVC 機能をテストするには、多くの場合、アプリを展開してから Selenium などのツールを使用してテストする必要があります。 これらのテストは、アプリ全体をホストして実行しなくても実行できる一般的な単体テストよりもはるかにコストが高く、より不安定で低速です。

ASP.NET MVC コントローラーと同様に [ASP.NET Core コントローラーを単体テストする](/aspnet/core/mvc/controllers/testing)ことは可能ですが、同じ制限があります。 しかし、[ASP.NET Core では、高速で作成が簡単な統合テスト](/aspnet/core/test/integration-tests)もサポートされています。 統合テストは `TestHost` クラスによってホストされ、通常は、アプリの依存関係をオーバーライドまたは置換できるカスタム `WebApplicationFactory` 内で構成されます。 たとえば、統合テスト中にアプリが別のデータ ソースをターゲットとし、電子メールを送信するサービスをフェイクまたはモックの実装に置き換えることがよくあります。

ASP.NET MVC と Web API では、ASP.NET Core で利用できる統合テスト シナリオのようなものはサポートされていませんでした。 移行作業では、新しく移行したシステム用の統合テストを作成するための時間を取って、そのシステムが現在および将来も想定どおりに動作することを確認できるようにする必要があります。 移行前に Web アプリのロジックのテストを作成していなかった場合でも、ASP.NET Core に移行する際にそうすることを検討すべきです。

## <a name="references"></a>リファレンス

- [ASP.NET MVC アプリケーションの単体テストを作成する](/aspnet/mvc/overview/older-versions-1/unit-testing/creating-unit-tests-for-asp-net-mvc-applications-cs)
- [ASP.NET Core でコントローラーのロジックの単体テストを行う](/aspnet/core/mvc/controllers/testing)
- [ASP.NET Core での統合テスト](/aspnet/core/test/integration-tests)

>[!div class="step-by-step"]
>[前へ](signalr-differences.md)
>[次へ](migrate-large-solutions.md)
