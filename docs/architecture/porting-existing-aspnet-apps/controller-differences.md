---
title: ASP.NET MVC と ASP.NET Core でのコントローラーの比較
description: MVC コントローラーは、ASP.NET MVC 5 と Web API 2 コントローラーに似ていますが、重要な違いがあります。 ASP.NET Core このセクションでは、ASP.NET MVC および Web API 2 のアプリを ASP.NET Core に移植するために必要な相違点と手順について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 2c2b7b848162a6ab9901ac9f7779787e2cc994ce
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401391"
---
# <a name="compare-controllers-in-aspnet-mvc-and-web-api-with-controllers-in-aspnet-core"></a>ASP.NET MVC と Web API のコントローラーを ASP.NET Core のコントローラーと比較する

ASP.NET MVC 5 と Web API 2 では、2つの異なる基本型がありました `Controller` 。 から継承された MVC コントローラー `Controller`から継承された Web API コントローラー `ApiController` 。 ASP.NET Core では、このオブジェクト階層はマージされています。 ASP.NET Core の API コントローラーは、から継承して属性を追加することをお勧めし `ControllerBase` `[ApiController]` ます。 標準のビューベースの MVC コントローラーは、から継承する必要があり `Controller` ます。

どちらのフレームワークでも、コントローラーは一連のアクションメソッドを整理するために使用されます。 フィルターとルートは、アクションレベルに加えて、コントローラーレベルでも適用できます。 これらの規則は、 `Controller` 既定の動作と属性が適用されたカスタム基本型を使用してさらに拡張できます。

ASP.NET MVC では、コンテンツネゴシエーションはサポートされていません。 ASP.NET Web API 2 では、ASP.NET Core のように、コンテンツネゴシエーションがサポートされます。 [コンテンツネゴシエーション](/aspnet/core/web-api/advanced/formatting)を使用すると、要求に返されるコンテンツの形式は、クライアントが提供するヘッダーによって、コンテンツを受信するための適切な方法を示すことができます。

ASP.NET Web API コントローラーを ASP.NET Core に移行する場合は、いくつかのコンポーネントが存在する場合は変更する必要があります。 これには、 `ApiController` 基底クラス、 `System.Web.Http` 名前空間、およびインターフェイスへの参照が含ま `IHttpActionResult` れます。 [これらの特定の相違点の移行方法に関する推奨事項につい](/aspnet/core/migration/webapi)ては、ドキュメントを参照してください。 ASP.NET Core の API アクションの推奨される戻り値の型は `ActionResult<T>` です。

また、属性は `[ChildActionOnly]` ASP.NET Core ではサポートされていません。 ASP.NET Core では、 [表示コンポーネント](/aspnet/core/mvc/views/view-components)を使用して同様の機能が実現されます。

ASP.NET Core には、 [ConsumesAttribute](/dotnet/api/microsoft.aspnetcore.mvc.consumesattribute) と [ProducesAttribute](/dotnet/api/microsoft.aspnetcore.mvc.producesattribute)という2つの新しい属性が含まれています。 これらは、アクションが使用または生成する型を指定するために使用されます。これは、 [Swagger/OpenAPI](/aspnet/core/tutorials/web-api-help-pages-using-swagger)などのツールを使用して API をルーティングおよびドキュメント化する場合に役立ちます。

## <a name="references"></a>関連項目

- [ASP.NET Core Web API の応答データの書式設定](/aspnet/core/web-api/advanced/formatting)
- [ASP.NET Web API から ASP.NET Core への移行](/aspnet/core/migration/webapi)

>[!div class="step-by-step"]
>[前へ](identity-differences.md)
>[次へ](razor-differences.md)
