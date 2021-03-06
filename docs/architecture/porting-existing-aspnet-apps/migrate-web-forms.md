---
title: ASP.NET Web Forms アプリを移行するための戦略
description: チームは ASP.NET Web フォームアプリを .NET Core に移行するためにどのような戦略を使用できますか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 0b37a37f047de50c347313be14a2228838da6995
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "102401282"
---
# <a name="strategies-for-migrating-aspnet-web-forms-apps"></a>ASP.NET Web Forms アプリを移行するための戦略

この書籍では、大規模な ASP.NET MVC と Web API アプリを .NET Core に移行するためのガイダンスを提供します。 これらの ASP.NET アプリには、対処する必要がある Web フォーム (*.aspx*) ページも含まれる場合があります。 ASP.NET Web フォームは .NET Core ではサポートされていません (ASP.NET Web ページ)。 通常は、ASP.NET Core に移植するときに、これらのページの機能を書き直す必要があります。 ただし、このような移行の前または実行中に適用できるいくつかの戦略によって、必要な全体的な作業量を減らすことができます。

Web フォームは、かなりの時間にわたり引き続きサポートされます。 1つのオプションとして、この機能を ASP.NET 4.x アプリで保持することができます。

## <a name="separate-business-logic-and-other-concerns"></a>ビジネスロジックとその他の懸念事項の分離

ASP.NET の Web フォームページのコードが少ないほど、改善されます。 可能であれば、ビジネスロジックや、データアクセスなどの他の懸念事項を別のクラスに保持し、理想的には別のクラスライブラリを使用します。 これらのクラスライブラリは、任意の ASP.NET Core アプリによって .NET Standard および使用されるように移植できます。

## <a name="implement-client-behavior-and-web-apis"></a>クライアント動作と web Api を実装する

API 呼び出しを使用して、Web フォームまたはブラウザーでロジックを実装するかどうかを選択します。 後者を優先します。 Api の ASP.NET Core への移行はサポートされています。 クライアント側の動作は、アプリが使用しているサーバー側のスタックから独立している必要があります。 このアプローチを使用すると、より応答性に優れたユーザーエクスペリエンスを提供するという利点があります。

## <a name="consider-blazor"></a>Blazor を検討する

Blazor を使用すると、JavaScript の代わりに、C# で対話型の web Ui を作成できます。 サーバーまたはブラウザーで、WebAssembly 使用して実行できます。 ASP.NET Web Forms アプリをページごとに Blazor アプリに移植できます。 Web フォームアプリを Blazor に移植する方法の詳細については、「 [Blazor for ASP.NET Web Forms デベロッパー](https://devblogs.microsoft.com/aspnet/blazor-aspnet-webforms-ebook/)」を参照してください。 また、多くの Web フォームコントロールは、オープンソースのコミュニティプロジェクトの一部として Blazor に移植されています。 [Blazor Web フォームコンポーネント](https://fritzandfriends.github.io/BlazorWebFormsComponents/)。 これらのコンポーネントを使用すると、組み込みの Web フォームコントロールを使用している場合でも、Web フォームページを Blazor に簡単に移植できます。

## <a name="summary"></a>まとめ

ASP.NET Web フォームから ASP.NET Core への直接移行はサポートされていません。 ただし、ASP.NET Core を簡単に移行できるようにするための戦略があります。 次の方法で、Web フォーム機能を ASP.NET Core に正常に移行できます。

* プロジェクトから非 web 機能を維持します。
* 可能な限り、web Api を使用します。
* より新しい UI のオプションとして Blazor を検討しています。

## <a name="references"></a>関連項目

- [無料の電子書籍: ASP.NET Web Forms 開発者向けの Blazor](https://devblogs.microsoft.com/aspnet/blazor-aspnet-webforms-ebook/)
- [Blazor Web フォームコンポーネント (コミュニティプロジェクト)](https://fritzandfriends.github.io/BlazorWebFormsComponents/)

>[!div class="step-by-step"]
>[前へ](incremental-migration-strategies.md)
>[次へ](deployment-strategies.md)
