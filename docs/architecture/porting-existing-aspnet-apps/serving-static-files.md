---
title: ASP.NET MVC および ASP.NET Core で静的ファイルを提供する
description: IIS での ASP.NET MVC と比較して、ASP.NET Core での静的ファイルの提供に関するサポートを構成するための関係
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 02f84a6985835502c24db8cc68db24c8de086b18
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401350"
---
# <a name="serve-static-files-in-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC および ASP.NET Core で静的ファイルを提供する

ほとんどの web アプリには、サーバー側のロジックと静的ファイルを組み合わせたものが含まれており、そのようにクライアントに送信する必要があります。 ASP.NET MVC から静的ファイルを提供する ASP.NET Core ハンドルに移行するにはどうすればよいですか。

## <a name="host-static-files-in-aspnet-mvc"></a>ASP.NET MVC での静的ファイルのホスト

IIS によってホストされる ASP.NET MVC アプリは、通常、静的ファイルをアプリから直接ホストします。 ASP.NET MVC では、静的ファイルを、サーバー上でプライベートに保持する必要があるファイルと同時に配置できます。 IIS と ASP.NET では、ASP.NET アプリがホストされているフォルダーから、特定のファイルまたはファイル拡張子が明示的に制限されている必要があります。

多くの静的ファイルでは、コンテンツ配信ネットワーク (CDN) を使用することをお勧めします。 [静的コンテンツホスティング](/azure/architecture/patterns/static-content-hosting) では、アプリサーバーからの負荷と帯域幅を削減しながら、パフォーマンスを向上させることができます。

## <a name="host-static-files-in-aspnet-core"></a>ASP.NET Core での静的ファイルのホスト

当然のことですが、ASP.NET Core 静的ファイルのサポートは組み込まれていません。 この機能は、IIS によって有効にされる ASP.NET の一部として常に存在していたものであり、ASP.NET Core またはその Kestrel web サーバーには組み込まれていません。 ASP.NET Core アプリから静的ファイルを提供するには、 [静的ファイルミドルウェア](/aspnet/core/fundamentals/static-files)を構成する必要があります。

静的ファイルミドルウェアが構成されている場合、ASP.NET Core アプリは、特定のフォルダー (通常は */wwwroot*) にあるすべてのファイルに対して機能します。 アプリまたはプロジェクトフォルダー内の他のファイルが、サーバーによって誤って公開される危険性があります。 IIS の場合と同様に、ファイル名または拡張機能に基づく特別な制限を構成する必要はありません。 代わりに、開発者は、 *wwwroot* フォルダーにファイルを配置するときに、ファイルを公開するように明示的に選択します。 既定では、このフォルダー以外のファイルは共有されません。

静的ファイルのサポートはミドルウェアを使用するため、その他のミドルウェアは同じ要求パイプラインの一部として適用できます。 ミドルウェアの例としては、認証、キャッシュ、圧縮などがあります。

もちろん、ASP.NET MVC アプリで使用されているのと同じ理由で、CDNs は ASP.NET Core アプリに適しています。 .NET Core への移行の準備の一環として、CDN を使用してアプリの利点が得られる場合は、.NET Core に移行する前に、静的なファイルを CDN に移動することをお勧めします。 これにより、静的な資産の移行作業全体の範囲が短縮されます。

## <a name="references"></a>関連項目

- [静的コンテンツホスティング](/azure/architecture/patterns/static-content-hosting)
- [ASP.NET Core の静的ファイル](/aspnet/core/fundamentals/static-files)

>[!div class="step-by-step"]
>[前へ](hosting-differences.md)
>[次へ](dependency-injection-differences.md)
