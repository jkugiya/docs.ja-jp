---
title: ASP.NET MVC と ASP.NET Core での Razor の使用の比較
description: ASP.NET MVC と ASP.NET Core で、Razor は どのように異なるでしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: a9f7fa2e6b8c0c6bf61c743cf8c956b1ad09713c
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401356"
---
# <a name="compare-razor-usage-in-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core での Razor の使用の比較

Razor の基本構文は、ASP.NET MVC と ASP.NET Core で大きな変わりはありません。 ただし、[タグ ヘルパー](/aspnet/core/mvc/views/tag-helpers/intro)と Razor Pages の導入など、移行時に考慮する必要があるいくつかの相違点があります。 アプリでカスタム Razor 機能を多用している場合は、「[ASP.NET Core の Razor 構文リファレンス](/aspnet/core/razor-pages)」を参照して、ASP.NET Core への移行時にどのような変更が必要になるかを確認してください。

## <a name="tag-helpers"></a>タグ ヘルパー

タグ ヘルパーを使用することで、Razor ファイルでの HTML 要素の作成とレンダリングに、サーバー側コードを組み込むことができます。 これは HTML ヘルパーよりも多くの利点があるので、可能な限り HTML ヘルパーの代わりに使用してください。 これは標準の HTML のように見え、HTML を編集するように設計されたほとんどのツールによって無視されるので、HTML に最適な開発エクスペリエンスを提供します。 _Visual Studio_ 内では、タグ ヘルパーを使用して HTML および Razor のマークアップを作成するための機能豊富な IntelliSense がサポートされています。 タグ ヘルパーは、Razor ファイル内の宣言型マークアップから、単純または複雑な動作を提供できます。

## <a name="razor-pages"></a>Razor ページ

Razor Pages は、ページベース アプリとフォームベース アプリでコントローラー、アクション、ビューの代わりとして使用できます。 [Razor Pages と ASP.NET MVC の比較については、この章の前のほうで説明しています](./comparing-razor-pages-aspnet-mvc.md)。

## <a name="references"></a>リファレンス

- [ASP.NET MVC から ASP.NET Core MVC への移行: コントローラーとビュー](/aspnet/core/migration/mvc#migrate-controllers-and-views)
- [ASP.NET Core のタグ ヘルパー](/aspnet/core/mvc/views/tag-helpers/intro)
- [ASP.NET Core での Razor ページの概要](/aspnet/core/razor-pages)
- [ASP.NET Core の Razor 構文リファレンス](/aspnet/core/razor-pages)

>[!div class="step-by-step"]
>[前へ](controller-differences.md)
>[次へ](signalr-differences.md)
