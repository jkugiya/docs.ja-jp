---
title: .NET Core へのアプリの移植の概要
description: この章では、既存の ASP.NET アプリを .NET Core に移行することを検討しているチーム向けの考慮事項の一覧を示します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: a346d1c693389cc4ca682b41a3b7fc094cfa5482
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "102401231"
---
# <a name="introduction-to-porting-apps-to-net-core"></a>.NET Core へのアプリの移植の概要

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

.NET Core は .NET Framework からの画期的なステップです。 また、クロスプラットフォームのサポートから開発者の満足度まで、生産性からパフォーマンスまで、.NET Framework よりも優れたホストを提供します。 ASP.NET Core は、 [2020 Stack Overflow 開発者アンケート](https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-web-frameworks)の中でも、最適な web フレームワークに投票しました。 移行を検討すべき理由は明らかです。

[.Net Core は .net の未来](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/)であることを念頭に置くことが重要です。 この記事を引用するには:

> 新しいアプリは .NET Core 上に構築する必要があります。 .Net Core は、.NET における将来の投資が行われる場所です。 既存のアプリは、サポートされる .NET Framework に安全に維持されます。 .NET の新機能を利用する既存のアプリでは、.NET Core への移行を検討する必要があります。 今後の計画では、プラットフォームにさらに多くの機能が導入される予定です。

ただし、アプリを ASP.NET Core にアップグレードするには、いくつかの作業が必要になります。 この作業は、ビジネス価値と目標に対してバランスを取る必要があります。 .NET Framework のアプリには長い時間がかかっており、将来、Windows に組み込まれています。 .NET Core への移行を決定する前に考慮する必要がある質問のいくつかを次の中からお選びください。 期待される利点は何ですか。 トレードオフとは何ですか。 どの程度の労力が関係していますか? これらの明らかな質問は最初のものですが、チームは今日と明日のアプリで顧客のニーズをサポートする方法を検討することをお勧めします。

- .NET Core への移行は適切ですか?
- .NET Framework にとどまるのはいつでしょうか。
- アプリのターゲットをステップ実行のストーンとして 2.1 ASP.NET Core する必要がありますか。
- 対象とする適切な .NET Core バージョンをチームでどのように選択すればよいですか。
- 大規模なアプリの増分移行には、どのような戦略が推奨されますか。
- .NET Core に移植するときに考慮する必要があるデプロイメント戦略
- その他のリソースはどこで入手できますか。

この入門編では、今後の章で、より具体的で技術的な考慮事項に進む前に、これらのすべての質問とその詳細について説明します。

## <a name="references"></a>関連項目

- [2020 Stack Overflow 開発者にとって最も人気のある web フレームワーク](https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-web-frameworks)
- [.Net Core は .NET の未来です](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/)

>[!div class="step-by-step"]
>[前へ](index.md)
>[次へ](migration-considerations.md)
