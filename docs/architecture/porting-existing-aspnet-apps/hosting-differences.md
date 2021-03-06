---
title: ASP.NET MVC と ASP.NET Core のホストの違い
description: ASP.NET MVC アプリがホストされる方法と ASP.NET Core アプリの違いの概要について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 402dd5782cb215545ff2ef13f97ec269b8a2540b
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401382"
---
# <a name="hosting-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core のホストの違い

ASP.NET MVC アプリは IIS でホストされ、その動作には IIS 構成に依存する場合があります。 これには、多くの場合、 [IIS モジュール](/iis/get-started/introduction-to-iis/iis-modules-overview)が含まれます。 ASP.NET MVC から ASP.NET Core への移植を準備するアプリのレビューの一環として、チームは、サーバーにインストールされている IIS モジュールの一覧から、使用しているモジュール (存在する場合) を特定する必要があります。

[ASP.NET Core のアプリは、さまざまなサーバーで実行でき](/aspnet/core/fundamentals/servers/)ます。 既定のクロスプラットフォームサーバーである Kestrel が、既定の選択肢として適しています。 Kestrel で実行されているアプリは、別のプロセスで実行される IIS によってホストできます。 Windows では、アプリは IIS または HTTP.sys を使用してプロセス内で実行することもできます。 最適なパフォーマンスを得るには、通常は Kestrel をお勧めします。 HTTP.sys は、アプリがインターネットに公開されていて、必要な機能が HTTP.sys でサポートされているものの、Kestrel ではサポートされていないシナリオで使用できます。

Kestrel には、IIS モジュールに相当するものがありません (ただし、IIS でホストされているアプリでも IIS モジュールを利用できます)。 同等の動作を実現するには、通常、ASP.NET Core アプリ自体で構成されたミドルウェアを使用します。

## <a name="references"></a>関連項目

- [IIS モジュール](/iis/get-started/introduction-to-iis/iis-modules-overview)
- [ASP.NET Core サーバー](/aspnet/core/fundamentals/servers/)

>[!div class="step-by-step"]
>[前へ](app-startup-differences.md)
>[次へ](serving-static-files.md)
