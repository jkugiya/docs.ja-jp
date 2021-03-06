---
title: .NET 開発者向け Dapr
description: Microsoft のオープン ソースの分散型アプリケーション ランタイムを理解し、最大限に活用するための .NET 開発者向けガイドです。
author: robvet
ms.date: 02/07/2021
ms.openlocfilehash: fc38dd1a98570cc4d2b367d272a107e3ad67ead9
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206569"
---
# <a name="dapr-for-net-developers"></a>.NET 開発者向け Dapr

![カバーの画像](./media/cover.png)

**プレビュー版**

発行者

Microsoft 開発部門、.NET および Azure Incubations チーム

A division of Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright &copy; 2021 by Microsoft Corporation

All rights reserved. 本書のいかなる部分も、書面による発行者の許可なしに、いかなる形式または方法によっても、複製または伝送することを禁じます。

本書は "現状有姿" で提供され、著者の見解と意見を表しています。 URL および他の参照されているインターネットの Web サイトをはじめ、本書に記載されている見解、意見、および情報は、通知なく変更されることがあります。

ここに記載したいくつかの例は、説明のためだけに提供された架空のものです。 実在のものとの関連性または関係性は一切ありません。

<https://www.microsoft.com> の "商標" Web ページに記載されている Microsoft および商標は、Microsoft グループの商標です。

Mac および macOS は Apple Inc. の商標です。

Docker のクジラのロゴは Docker, Inc. の登録商標です。許可を得て使用しています。

その他のすべてのマークおよびロゴは、該当する各社が所有しています。

作成者:

> **Rob Vettor**、Microsoft、プリンシパル クラウド ソリューション アーキテクト - [thinkingincloudnative.com](https://thinkingincloudnative.com/about/)
>
> **Sander Molenkamp**、プリンシパル クラウド アーキテクト/Microsoft MVP - [sandermolenkamp.com](https://www.sandermolenkamp.com)、[情報サポート](https://www.infosupport.com/en/)
>
> **Edwin van Wijk**、プリンシパル ソリューション アーキテクト/Microsoft MVP - [defaultconstructor.com](https://defaultconstructor.com)、[情報サポート](https://www.infosupport.com/en/)

参加者とレビュー担当者:

> **Mark Russinovich**、Microsoft、Azure CTO 兼テクニカル フェロー、Azure Office of CTO
>
> **Nish Anil**、Microsoft、.NET チーム、シニア プログラム マネージャー
>
> **Mark Fussell**、Microsoft、プリンシパル プログラム マネージャー、Azure Incubations
>
> **Yaron Schneider**、Microsoft、主任ソフトウェア エンジニア、Azure Incubations
>
> **Ori Zohar**、Microsoft、プリンシパル プログラム マネージャー、Azure Incubations

編集者:

> **David Pine**、Microsoft、.NET チーム、シニア コンテンツ開発者
>
> **Maira Wenzel**、Microsoft、.NET チーム、シニア プログラム マネージャー

## <a name="version"></a>バージョン

このガイドは、**Dapr 1.0** バージョンに対応するように記述されています。 .NET Core サンプルは、 **.NET Core 3.1** に基づいています。

## <a name="who-should-use-this-guide"></a>対象読者

本ガイドの対象読者は主に、クラウド向けに設計されたアプリケーションを構築する方法に関心がある開発者、開発リーダー、アーキテクトです。

2 番目の対象読者は、クラウドネイティブな手法でアプリケーションを構築するかどうかを決定する予定の技術部門の意思決定者です。

## <a name="how-you-can-use-this-guide"></a>このガイドを使用する方法

このガイドは [PDF](https://aka.ms/dapr-ebook) 形式とオンラインの両方で利用できます。 本書やそのオンライン版のリンクをチームに転送し、トピックの共通理解に役立ててください。 トピックのほとんどは、基礎的な原則、基礎的なパターン、トピックに関連する意思決定に関係する折り合いが同じように理解されることで効果を発揮します。 本書の目標は、アプリケーションのアーキテクチャ、開発、ホスティングについて、十分に情報が与えられた上で意思決定するために必要な情報をチームとそのリーダーに与えることです。

## <a name="send-your-feedback"></a>フィードバックの送信

本書と関連サンプルは継続的に更新されるので、お客様のフィードバックを歓迎しています。 本書を改善する方法についてコメントがある場合、[GitHub の問題](https://github.com/dotnet/docs/issues)に関して作成されたあらゆるページの下部にあるフィードバック セクションをご利用ください。

>[!div class="step-by-step"]
>[次へ](foreword.md)
