---
title: ASP.NET Web Forms アプリを移行するための戦略
description: チームは、ASP.NET Web Forms アプリを .NET Core に移行するためにどのような戦略を使用できるでしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 0b37a37f047de50c347313be14a2228838da6995
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "102401282"
---
# <a name="strategies-for-migrating-aspnet-web-forms-apps"></a>ASP.NET Web Forms アプリを移行するための戦略

本書では、大規模な ASP.NET MVC アプリおよび Web API アプリを .NET Core に移行するためのガイダンスを提供します。 これらの ASP.NET アプリの中には、対応が必要な Web Forms ( *.aspx*) ページを含んでいるものがあります。 ASP.NET Web Forms は、.NET Core (および ASP.NET Web ページ) でサポートされていません。 通常は、ASP.NET Core に移植する際に、これらのページの機能を書き換える必要があります。 しかし、そのような移行の前または実行中に適用できるいくつかの戦略によって、必要な作業量を少なくすることができます。

Web Forms は、今後もかなりの期間にわたってサポートされる予定です。 1 つの選択肢は、この機能を ASP.NET 4.x アプリ内で保持することです。

## <a name="separate-business-logic-and-other-concerns"></a>ビジネス ロジックとその他の懸念事項を分離する

ASP.NET Web Forms ページに含めるコードは、なるべく少なくしてください。 可能な場合は、ビジネス ロジックとデータ アクセスなどのその他の懸念事項を、別のクラス内 (理想的には別のクラス ライブラリ内) で保持します。 これらのクラス ライブラリを .NET Standard に移植して、任意の ASP.NET Core アプリで使用することができます。

## <a name="implement-client-behavior-and-web-apis"></a>クライアントの動作と Web API を実装する

ロジックを Web Forms に実装するか、または API 呼び出しを利用してブラウザーに実装するかを検討します。 推奨されるのは後者です。 API の ASP.NET Core への移行はサポートされています。 クライアント側の動作は、アプリが使用しているサーバー側のスタックから独立している必要があります。 このアプローチを使用すると、より応答性に優れたユーザー エクスペリエンスを提供できるというベネフィットも得られます。

## <a name="consider-blazor"></a>Blazor を検討する

Blazor を使用すると、JavaScript の代わりに C# を使用して対話型の Web UI をビルドできます。 これは、サーバー上で、または WebAssembly を使用してブラウザー内で実行できます。 ASP.NET Web Forms アプリは、ページ単位で Blazor アプリに移植できます。 Web Forms アプリを Blazor に移植する方法の詳細については、「[ASP.NET Web Forms 開発者向け Blazor](https://devblogs.microsoft.com/aspnet/blazor-aspnet-webforms-ebook/)」を参照してください。 また、多数の Web Forms コントロールが、オープンソース コミュニティ プロジェクト「[Blazor Web Forms コンポーネント](https://fritzandfriends.github.io/BlazorWebFormsComponents/)」の一環として Blazor に移植されています。 これらのコンポーネントを使用すると、Web Forms ページで組み込みの Web Forms コントロールが使用されている場合でも、より簡単にページを Blazor に移植できます。

## <a name="summary"></a>まとめ

ASP.NET Web Forms から ASP.NET Core への直接の移行はサポートされていません。 しかし、ASP.NET Core への移行を容易にするための戦略がいくつかあります。 以下を行うことにより、Web Forms の機能を ASP.NET Core に正しく移行できます。

* Web 以外の機能はプロジェクトの外部で保持します。
* できる限り Web API を使用します。
* より新しい UI のためのオプションとして Blazor を検討します。

## <a name="references"></a>リファレンス

- [無料の電子書籍: ASP.NET Web Forms 開発者向け Blazor](https://devblogs.microsoft.com/aspnet/blazor-aspnet-webforms-ebook/)
- [Blazor Web Forms コンポーネント (コミュニティ プロジェクト)](https://fritzandfriends.github.io/BlazorWebFormsComponents/)

>[!div class="step-by-step"]
>[前へ](incremental-migration-strategies.md)
>[次へ](deployment-strategies.md)
