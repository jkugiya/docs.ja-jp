---
title: ASP.NET MVC と ASP.NET Core でのホスティングの相違点
description: ASP.NET MVC アプリと ASP.NET Core アプリでのホスト方法の相違点に関する概要を示します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 402dd5782cb215545ff2ef13f97ec269b8a2540b
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401382"
---
# <a name="hosting-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core でのホスティングの相違点

ASP.NET MVC アプリは IIS でホストされるため、動作が IIS の構成に依存している可能性があります。 これには多くの場合、[IIS モジュール](/iis/get-started/introduction-to-iis/iis-modules-overview)が含まれます。 ASP.NET MVC から ASP.NET Core にアプリを移植する準備のための確認の一環として、チームはサーバー上にインストールされている IIS モジュールの一覧の中から、使用中のモジュール (存在する場合) を特定する必要があります。

[ASP.NET Core アプリは多数の異なるサーバー上で実行できます](/aspnet/core/fundamentals/servers/)。 既定の選択肢としては、既定のクロス プラットフォーム サーバーである Kestrel が適しています。 Kestrel で実行されているアプリは、別のプロセスで実行されている IIS によってホストできます。 Windows では、アプリを IIS 上のプロセス内で、または HTTP.sys を使用して実行することもできます。 最適なパフォーマンスを得るには、通常は Kestrel をお勧めします。 HTTP.sys は、アプリがインターネットに公開されていて、必要な機能が HTTP.sys でサポートされているものの、Kestrel ではサポートされていないシナリオで使用できます。

Kestrel には、IIS モジュールに相当するものはありません (ただし、IIS でホストされているアプリで IIS モジュールを利用することはできます)。 同等の動作を実現するために、通常は、ASP.NET Core アプリ自体に構成されたミドルウェアが使用されます。

## <a name="references"></a>リファレンス

- [IIS モジュール](/iis/get-started/introduction-to-iis/iis-modules-overview)
- [ASP.NET Core サーバー](/aspnet/core/fundamentals/servers/)

>[!div class="step-by-step"]
>[前へ](app-startup-differences.md)
>[次へ](serving-static-files.md)
