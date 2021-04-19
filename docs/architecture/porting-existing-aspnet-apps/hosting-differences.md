---
title: ASP.NET MVC と ASP.NET Core でのホスティングの相違点
description: ASP.NET MVC アプリと ASP.NET Core アプリでのホスト方法の相違点に関する概要を示します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 9881a40403f8109fa63e25167b753ed4ce8ade17
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122899"
---
# <a name="hosting-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core でのホスティングの相違点

ASP.NET MVC アプリは IIS でホストされるため、動作が IIS の構成に依存している可能性があります。 これには多くの場合、[IIS モジュール](/iis/get-started/introduction-to-iis/iis-modules-overview)が含まれます。 ASP.NET MVC から ASP.NET Core にアプリを移植する準備のための確認の一環として、チームはサーバー上にインストールされている IIS モジュールの一覧の中から、使用中のモジュール (存在する場合) を特定する必要があります。

[ASP.NET Core アプリは多数の異なるサーバー上で実行できます](/aspnet/core/fundamentals/servers/)。 既定の選択肢としては、既定のクロス プラットフォーム サーバーである Kestrel が適しています。 Kestrel で実行されているアプリは、別のプロセスで実行されている IIS によってホストできます。 Windows では、アプリを IIS 上のプロセス内で、または HTTP.sys を使用して実行することもできます。 最適なパフォーマンスを得るには、通常は Kestrel をお勧めします。 HTTP.sys は、アプリがインターネットに公開されていて、必要な機能が HTTP.sys でサポートされているものの、Kestrel ではサポートされていないシナリオで使用できます。

Kestrel には、IIS モジュールに相当するものはありません (ただし、IIS でホストされているアプリで IIS モジュールを利用することはできます)。 同等の動作を実現するために、通常は、ASP.NET Core アプリ自体に構成された[ミドルウェア](/aspnet/core/fundamentals/middleware/)が使用されます。

## <a name="references"></a>References

- [IIS モジュール](/iis/get-started/introduction-to-iis/iis-modules-overview)
- [ASP.NET Core のミドルウェア](/aspnet/core/fundamentals/middleware/)
- [ASP.NET Core サーバー](/aspnet/core/fundamentals/servers/)

>[!div class="step-by-step"]
>[前へ](app-startup-differences.md)
>[次へ](serving-static-files.md)
