---
title: ASP.NET MVC と ASP.NET Core での静的ファイルの提供
description: IIS 上の ASP.NET MVC と比較して、ASP.NET Core で静的ファイルを提供するためのサポートを構成するには何が必要でしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 02f84a6985835502c24db8cc68db24c8de086b18
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401350"
---
# <a name="serve-static-files-in-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core での静的ファイルの提供

ほとんどの Web アプリには、サーバー側のロジックと、クライアントにそのまま送信する必要がある静的ファイルの組み合わせが含まれています。 ASP.NET MVC から ASP.NET Core への移行では、静的ファイルの提供をどのように処理すればよいでしょうか?

## <a name="host-static-files-in-aspnet-mvc"></a>ASP.NET MVC での静的ファイルのホスト

通常、IIS によってホストされる ASP.NET MVC アプリは、静的ファイルをアプリから直接ホストします。 ASP.NET MVC では、静的ファイルを、サーバー上で非公開にする必要があるファイルとサイドバイサイドで配置できます。 IIS および ASP.NET では、ASP.NET アプリがホストされているフォルダーから特定のファイルまたはファイル拡張子が提供されないように明示的に制限する必要があります。

多くの静的ファイルに対しては、コンテンツ配信ネットワーク (CDN) を使用することをお勧めします。 [静的コンテンツ ホスティング](/azure/architecture/patterns/static-content-hosting)を使用すると、アプリ サーバーからの負荷と帯域幅を抑えつつ、パフォーマンスを向上できます。

## <a name="host-static-files-in-aspnet-core"></a>ASP.NET Core での静的ファイルのホスト

意外かもしれませんが、ASP.NET Core には静的ファイルのサポートが組み込まれていません。 ASP.NET の一部として常に存在し、IIS によって実現されていたこの機能は、ASP.NET Core やその Kestrel Web サーバーには組み込まれていません。 ASP.NET Core アプリから静的ファイルを提供するには、[静的ファイル ミドルウェア](/aspnet/core/fundamentals/static-files)を構成する必要があります。

静的ファイル ミドルウェアを構成されると、ASP.NET Core アプリは特定のフォルダー (通常は */wwwroot*) 内にあるすべてのファイルを提供します。 アプリまたはプロジェクト フォルダーに含まれるそれ以外のファイルがサーバーによって誤って公開される危険性はありません。 IIS のように、ファイル名または拡張機能に基づいて特別な制限を構成する必要はありません。 代わりに、開発者はファイルを *wwwroot* フォルダー内に配置することで、そのファイルを公開することを明示的に選択します。 既定では、このフォルダー外にあるファイルは共有されません。

静的ファイルのサポートではミドルウェアが使用されるため、他の任意のミドルウェアを同じ要求パイプラインの一部として適用できます。 ミドルウェアの例としては、認証、キャッシュ、圧縮などがあります。

もちろん、CDN は、ASP.NET MVC アプリで使用されているのとまったく同じ理由で、ASP.NET Core アプリでも良い選択であることに変わりありません。 .NET Core への移行の準備の一環として、CDN を使用することでアプリが得られるベネフィットがある場合は、.NET Core に移行する前に静的ファイルを CDN に移動しておくことをお勧めします。 それにより、静的アセットに関する移行作業のスコープ全体を縮小できます。

## <a name="references"></a>リファレンス

- [静的コンテンツ ホスティング](/azure/architecture/patterns/static-content-hosting)
- [ASP.NET Core の静的ファイル](/aspnet/core/fundamentals/static-files)

>[!div class="step-by-step"]
>[前へ](hosting-differences.md)
>[次へ](dependency-injection-differences.md)
