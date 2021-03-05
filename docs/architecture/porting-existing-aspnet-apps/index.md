---
title: .NET Core への既存の ASP.NET アプリの移植
description: ASP.NET MVC および Web API アプリを ASP.NET Core に変換するための無料ガイドです。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 848f0e9533a65b59055853f1d502307abb69118c
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105946"
---
# <a name="porting-existing-aspnet-apps-to-net-core"></a>.NET Core への既存の ASP.NET アプリの移植

![カバーの画像](./media/index/porting-existing-aspnet-apps.png)

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

発行者

Microsoft 開発部門、.NET および Visual Studio 製品チーム

A division of Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright &copy; 2020 by Microsoft Corporation

All rights reserved. 本書の内容のいかなる部分も、書面による発行者の許可なしに、いかなる形式または方法によっても、複製または伝送することを禁じます。

本書は "現状有姿" で提供され、著者の見解と意見を表しています。 URL および他の参照されているインターネットの Web サイトをはじめ、本書に記載されている見解、意見、および情報は、通知なく変更されることがあります。

ここに記載したいくつかの例は、説明のためだけに提供された架空のものです。 実在のものとの関連性または関係性は一切ありません。

<https://www.microsoft.com> の "商標" Web ページに記載されている Microsoft および商標は、Microsoft グループの商標です。

Mac および macOS は Apple Inc. の商標です。

Docker のクジラのロゴは Docker, Inc. の登録商標です。許可を得て使用しています。

その他のすべてのマークおよびロゴは、該当する各社が所有しています。

作成者:

> **Steve "ardalis" Smith**、ソフトウェア アーキテクトおよびトレーナー - [Ardalis.com](https://ardalis.com)

参加者とレビュー担当者:

> **Nish Anil**、Microsoft、.NET チーム、シニア プログラム マネージャー

> **Mike Rousos**、Microsoft、.NET チーム、主任ソフトウェア エンジニア

> **Scott Addie**、Microsoft、.NET チーム、シニア コンテンツ開発者

> **David Pine**、Microsoft、.NET チーム、シニア コンテンツ開発者

## <a name="version"></a>バージョン

このガイドでは、 **.NET Core 3.1** と、.NET Core 3.1 リリースと同時期の同じテクノロジの "流れ" (つまり、Azure やその他のサードパーティ製テクノロジ) に関連する更新プログラムについて説明します。 .NET Core 3.1 から .NET 5.0 (次のバージョン) への更新は比較的わかりやすく、.NET Framework から .NET Core への移植よりも必要な作業量がかなり少なくなります。 .NET Framework 4.x から .NET 5.0 への移行は、.NET Core 3.1 への移行に似ています。 詳細については、[適切な .NET Core バージョンの選択](choose-net-core-version.md)に関する記事を参照してください。

## <a name="who-should-use-this-guide"></a>対象読者

このガイドの対象読者は、ASP.NET MVC および Web API (.NET Framework 4.x) 用に作成された既存のアプリを .NET Core に移行することに関心をお持ちの開発者、開発リーダー、およびアーキテクトです。 ASP.NET Web Forms の開発者はこのガイドを活用できますが、電子書籍『[ASP.NET Web Forms 開発者向け Blazor](../blazor-for-web-forms-developers/index.md)』も併せてご覧いただく必要があります。

第 2 の対象読者は、アプリを .NET Core に移行するタイミングを計画している技術的な意思決定者です。

この書籍の対象読者は、ASP.NET MVC および Web API で実行する既存の大規模なアプリをお持ちの .NET 開発者です。 ASP.NET Web Forms 上に構築されたアプリはこの書籍の対象範囲外ですが、.NET Framework と .NET Core を比較する情報の多くは関連している可能性があります。

## <a name="how-you-can-use-this-guide"></a>このガイドを使用する方法

この書籍は、多くの読者がそうするように、はじめから終わりまで読んでいくことが可能です。 この書籍ではまず、そもそも自分のアプリを移植する必要があるかどうかについての考慮事項が説明されます。 その内容の次に、.NET Framework と .NET Core のアーキテクチャの相違点が示されます。 そこから、大規模なソリューションを徐々に移行していくための戦略と、実際のアプリを移植する方法を学習します。 書籍では次に、異なるアプリを、ユーザーに対しては 1 つのアプリのように見せながら実行する必要性に対応する展開シナリオについて説明します。 最後に、ASP.NET MVC から ASP.NET Core に移行された実際のアプリについて説明する 2 つのケース スタディで書籍は締めくくられます。

第 1 章から開始するかどうかにかかわらず、これらのいずれかの章を参照して特定の概念について学習することができます。

- [アーキテクチャの相違点](architectural-differences.md)
- [大規模なソリューションの移行](migrate-large-solutions.md)
- [移行の例](example-migration-eshop.md)
- [展開シナリオ](deployment-scenarios.md)

このガイドは [PDF 形式](https://aka.ms/aspnet-porting-ebook)とオンラインの両方で利用できます。 本書やそのオンライン版のリンクをご自由にチームに転送し、これらの概念の共通理解に役立ててください。

## <a name="send-your-feedback"></a>フィードバックの送信

本書と関連サンプルは継続的に更新されるので、お客様のフィードバックを歓迎しています。 本書を改善する方法についてコメントがある場合、[GitHub の問題](https://github.com/dotnet/docs/issues)に関して作成されたあらゆるページの下部にあるフィードバック セクションをご利用ください。

>[!div class="step-by-step"]
>[次へ](introduction.md)
