---
title: ASP.NET MVC と ASP.NET Core での Razor の使用状況の比較
description: Razor は ASP.NET MVC と ASP.NET Core の違いはどのようなものですか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: a9f7fa2e6b8c0c6bf61c743cf8c956b1ad09713c
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401356"
---
# <a name="compare-razor-usage-in-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core での Razor の使用状況の比較

Razor の基本構文は、ASP.NET MVC と ASP.NET Core 間で大幅に変更されていません。 ただし、移行時に考慮する必要がある、 [タグヘルパー](/aspnet/core/mvc/views/tag-helpers/intro) と Razor Pages の導入など、いくつかの違いがあります。 アプリでカスタム Razor 機能を多用する場合は、 [ASP.NET Core の Razor 構文リファレンス](/aspnet/core/razor-pages) を参照して、ASP.NET Core に移行するときに必要となる変更点を確認してください。

## <a name="tag-helpers"></a>タグ ヘルパー

タグ ヘルパーを使用することで、Razor ファイルでの HTML 要素の作成とレンダリングに、サーバー側コードを組み込むことができます。 HTML ヘルパーよりも多くの利点があり、可能な限り HTML ヘルパーの代わりに使用する必要があります。 HTML を編集するために設計されたほとんどのツールでは無視されるため、HTML に適した開発エクスペリエンスを提供します。 _Visual Studio_ では、タグヘルパーを使用して HTML および Razor マークアップを作成するための豊富な IntelliSense がサポートされています。 タグヘルパーは、Razor ファイルの宣言型マークアップから単純または複雑な動作を提供できます。

## <a name="razor-pages"></a>Razor ページ

Razor Pages は、ページベースのアプリとフォームベースのアプリのコントローラー、アクション、ビューの代わりに使用できます。 [Razor Pages は、この章で前に説明した ASP.NET MVC と比較されました](./comparing-razor-pages-aspnet-mvc.md)。

## <a name="references"></a>関連項目

- [ASP.NET MVC から ASP.NET Core MVC: コントローラーとビューへの移行](/aspnet/core/migration/mvc#migrate-controllers-and-views)
- [ASP.NET Core のタグ ヘルパー](/aspnet/core/mvc/views/tag-helpers/intro)
- [ASP.NET Core での Razor ページの概要](/aspnet/core/razor-pages)
- [ASP.NET Core の Razor 構文リファレンス](/aspnet/core/razor-pages)

>[!div class="step-by-step"]
>[前へ](controller-differences.md)
>[次へ](signalr-differences.md)
