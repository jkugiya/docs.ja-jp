---
title: .NET Core へのアプリの移植の概要
description: この章では、既存の ASP.NET アプリから .NET Core への移行を検討しているチーム向けの考慮事項の一覧を示します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: a346d1c693389cc4ca682b41a3b7fc094cfa5482
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "102401231"
---
# <a name="introduction-to-porting-apps-to-net-core"></a>.NET Core へのアプリの移植の概要

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

.NET Core は、.NET Framework を画期的に進歩させたものです。 生産性からパフォーマンスまで、またクロスプラットフォーム サポートから開発者満足度まで、.NET Framework 全体にわたって数多くのメリットをもたらします。 ASP.NET Core は、[Stack Overflow の 2020 年開発者調査](https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-web-frameworks)で、最も人気のある Web フレームワークに選ばれました。 移行を検討するだけの強力な理由があるのは明らかです。

[.NET Core は .NET の未来である](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/)ことを念頭に置いておくことが重要です。 以下は、この記事からの引用です。

> 新しいアプリは .NET Core 上で構築する必要があります。 .Net Core は、.NET への今後の投資が行われる場所です。 既存のアプリは、今後サポートされる .NET Framework 上で安全に維持できます。 .NET の新機能を利用したい既存のアプリは、.NET Core に移行することを検討する必要があります。 Microsoft の今後の計画では、さらに多くの機能がこのプラットフォームに導入される予定です。

ただし、アプリを ASP.NET Core にアップグレードするにはいくつかの作業が必要になります。 その作業量と、ビジネス バリューおよびゴールとを天秤にかける必要があります。 .NET Framework アプリは、当面の間 Windows にサポートが組み込まれるため、まだ長い寿命があります。 .NET Core への移行が適切であると判断する前に、どのような疑問について検討する必要があるでしょうか? 期待されるメリットは何ですか? どのようなトレードオフがありますか? どれだけの作業量が必要になりますか? これらの明白な質問はほんの始まりにすぎませんが、チームが現在と将来のアプリに関する顧客のニーズをどのようにサポートするかを検討する際の良い出発点となります。

- .NET Core への移行は適切ですか?
- .NET Framework にとどまることが理にかなっているのはどのような場合ですか?
- 足がかりとして、ASP.NET Core 2.1 をアプリのターゲットにする必要がありますか?
- チームは、ターゲットにする適切な .NET Core のバージョンをどのように選択しますか?
- 大規模なアプリの段階的な移行には、どのような戦略が推奨されますか?
- .NET Core への移行時にはどのような展開戦略を検討する必要がありますか?
- 追加のリソースはどこで入手できますか?

この序章では、後の章でより具体的かつ技術的な考慮事項に進む前に、これらすべてを含めたさまざまな疑問に答えます。

## <a name="references"></a>リファレンス

- [Stack Overflow の 2020 年開発者調査における最も人気のある Web フレームワーク](https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-web-frameworks)
- [.Net Core は .NET の未来である](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/)

>[!div class="step-by-step"]
>[前へ](index.md)
>[次へ](migration-considerations.md)
