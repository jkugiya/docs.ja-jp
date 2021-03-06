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
# <a name="dapr-for-net-developers"></a><span data-ttu-id="23bed-103">.NET 開発者向け Dapr</span><span class="sxs-lookup"><span data-stu-id="23bed-103">Dapr for .NET Developers</span></span>

![カバーの画像](./media/cover.png)

<span data-ttu-id="23bed-105">**プレビュー版**</span><span class="sxs-lookup"><span data-stu-id="23bed-105">**PREVIEW EDITION**</span></span>

<span data-ttu-id="23bed-106">発行者</span><span class="sxs-lookup"><span data-stu-id="23bed-106">PUBLISHED BY</span></span>

<span data-ttu-id="23bed-107">Microsoft 開発部門、.NET および Azure Incubations チーム</span><span class="sxs-lookup"><span data-stu-id="23bed-107">Microsoft Developer Division, .NET, and Azure Incubations teams</span></span>

<span data-ttu-id="23bed-108">A division of Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="23bed-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="23bed-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="23bed-109">One Microsoft Way</span></span>

<span data-ttu-id="23bed-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="23bed-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="23bed-111">Copyright &copy; 2021 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="23bed-111">Copyright &copy; 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="23bed-112">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="23bed-112">All rights reserved.</span></span> <span data-ttu-id="23bed-113">本書のいかなる部分も、書面による発行者の許可なしに、いかなる形式または方法によっても、複製または伝送することを禁じます。</span><span class="sxs-lookup"><span data-stu-id="23bed-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="23bed-114">本書は "現状有姿" で提供され、著者の見解と意見を表しています。</span><span class="sxs-lookup"><span data-stu-id="23bed-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="23bed-115">URL および他の参照されているインターネットの Web サイトをはじめ、本書に記載されている見解、意見、および情報は、通知なく変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="23bed-115">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="23bed-116">ここに記載したいくつかの例は、説明のためだけに提供された架空のものです。</span><span class="sxs-lookup"><span data-stu-id="23bed-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="23bed-117">実在のものとの関連性または関係性は一切ありません。</span><span class="sxs-lookup"><span data-stu-id="23bed-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="23bed-118"><https://www.microsoft.com> の "商標" Web ページに記載されている Microsoft および商標は、Microsoft グループの商標です。</span><span class="sxs-lookup"><span data-stu-id="23bed-118">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="23bed-119">Mac および macOS は Apple Inc. の商標です。</span><span class="sxs-lookup"><span data-stu-id="23bed-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="23bed-120">Docker のクジラのロゴは Docker, Inc. の登録商標です。許可を得て使用しています。</span><span class="sxs-lookup"><span data-stu-id="23bed-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="23bed-121">その他のすべてのマークおよびロゴは、該当する各社が所有しています。</span><span class="sxs-lookup"><span data-stu-id="23bed-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="23bed-122">作成者:</span><span class="sxs-lookup"><span data-stu-id="23bed-122">Authors:</span></span>

> <span data-ttu-id="23bed-123">**Rob Vettor**、Microsoft、プリンシパル クラウド ソリューション アーキテクト - [thinkingincloudnative.com](https://thinkingincloudnative.com/about/)</span><span class="sxs-lookup"><span data-stu-id="23bed-123">**Rob Vettor**, Principal Cloud Solution Architect - [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="23bed-124">**Sander Molenkamp**、プリンシパル クラウド アーキテクト/Microsoft MVP - [sandermolenkamp.com](https://www.sandermolenkamp.com)、[情報サポート](https://www.infosupport.com/en/)</span><span class="sxs-lookup"><span data-stu-id="23bed-124">**Sander Molenkamp**, Principal Cloud Architect/Microsoft MVP - [sandermolenkamp.com](https://www.sandermolenkamp.com), [Info Support](https://www.infosupport.com/en/)</span></span>
>
> <span data-ttu-id="23bed-125">**Edwin van Wijk**、プリンシパル ソリューション アーキテクト/Microsoft MVP - [defaultconstructor.com](https://defaultconstructor.com)、[情報サポート](https://www.infosupport.com/en/)</span><span class="sxs-lookup"><span data-stu-id="23bed-125">**Edwin van Wijk**, Principal Solution Architect/Microsoft MVP - [defaultconstructor.com](https://defaultconstructor.com), [Info Support](https://www.infosupport.com/en/)</span></span>

<span data-ttu-id="23bed-126">参加者とレビュー担当者:</span><span class="sxs-lookup"><span data-stu-id="23bed-126">Participants and Reviewers:</span></span>

> <span data-ttu-id="23bed-127">**Mark Russinovich**、Microsoft、Azure CTO 兼テクニカル フェロー、Azure Office of CTO</span><span class="sxs-lookup"><span data-stu-id="23bed-127">**Mark Russinovich**, Azure CTO and Technical Fellow, Azure Office of CTO, Microsoft</span></span>
>
> <span data-ttu-id="23bed-128">**Nish Anil**、Microsoft、.NET チーム、シニア プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="23bed-128">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="23bed-129">**Mark Fussell**、Microsoft、プリンシパル プログラム マネージャー、Azure Incubations</span><span class="sxs-lookup"><span data-stu-id="23bed-129">**Mark Fussell**, Principal Program Manager, Azure Incubations, Microsoft</span></span>
>
> <span data-ttu-id="23bed-130">**Yaron Schneider**、Microsoft、主任ソフトウェア エンジニア、Azure Incubations</span><span class="sxs-lookup"><span data-stu-id="23bed-130">**Yaron Schneider**, Principal Software Engineer, Azure Incubations, Microsoft</span></span>
>
> <span data-ttu-id="23bed-131">**Ori Zohar**、Microsoft、プリンシパル プログラム マネージャー、Azure Incubations</span><span class="sxs-lookup"><span data-stu-id="23bed-131">**Ori Zohar**, Senior Program Manager, Azure Incubations, Microsoft</span></span>

<span data-ttu-id="23bed-132">編集者:</span><span class="sxs-lookup"><span data-stu-id="23bed-132">Editors:</span></span>

> <span data-ttu-id="23bed-133">**David Pine**、Microsoft、.NET チーム、シニア コンテンツ開発者</span><span class="sxs-lookup"><span data-stu-id="23bed-133">**David Pine**, Senior Content Developer, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="23bed-134">**Maira Wenzel**、Microsoft、.NET チーム、シニア プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="23bed-134">**Maira Wenzel**, Senior Program Manager, .NET team, Microsoft</span></span>

## <a name="version"></a><span data-ttu-id="23bed-135">バージョン</span><span class="sxs-lookup"><span data-stu-id="23bed-135">Version</span></span>

<span data-ttu-id="23bed-136">このガイドは、**Dapr 1.0** バージョンに対応するように記述されています。</span><span class="sxs-lookup"><span data-stu-id="23bed-136">This guide has been written to cover the **Dapr 1.0** version.</span></span> <span data-ttu-id="23bed-137">.NET Core サンプルは、 **.NET Core 3.1** に基づいています。</span><span class="sxs-lookup"><span data-stu-id="23bed-137">.NET Core samples are based on **.NET Core 3.1**.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="23bed-138">対象読者</span><span class="sxs-lookup"><span data-stu-id="23bed-138">Who should use this guide</span></span>

<span data-ttu-id="23bed-139">本ガイドの対象読者は主に、クラウド向けに設計されたアプリケーションを構築する方法に関心がある開発者、開発リーダー、アーキテクトです。</span><span class="sxs-lookup"><span data-stu-id="23bed-139">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="23bed-140">2 番目の対象読者は、クラウドネイティブな手法でアプリケーションを構築するかどうかを決定する予定の技術部門の意思決定者です。</span><span class="sxs-lookup"><span data-stu-id="23bed-140">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="23bed-141">このガイドを使用する方法</span><span class="sxs-lookup"><span data-stu-id="23bed-141">How you can use this guide</span></span>

<span data-ttu-id="23bed-142">このガイドは [PDF](https://aka.ms/dapr-ebook) 形式とオンラインの両方で利用できます。</span><span class="sxs-lookup"><span data-stu-id="23bed-142">This guide is available both in [PDF](https://aka.ms/dapr-ebook) form and online.</span></span> <span data-ttu-id="23bed-143">本書やそのオンライン版のリンクをチームに転送し、トピックの共通理解に役立ててください。</span><span class="sxs-lookup"><span data-stu-id="23bed-143">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="23bed-144">トピックのほとんどは、基礎的な原則、基礎的なパターン、トピックに関連する意思決定に関係する折り合いが同じように理解されることで効果を発揮します。</span><span class="sxs-lookup"><span data-stu-id="23bed-144">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="23bed-145">本書の目標は、アプリケーションのアーキテクチャ、開発、ホスティングについて、十分に情報が与えられた上で意思決定するために必要な情報をチームとそのリーダーに与えることです。</span><span class="sxs-lookup"><span data-stu-id="23bed-145">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="23bed-146">フィードバックの送信</span><span class="sxs-lookup"><span data-stu-id="23bed-146">Send your feedback</span></span>

<span data-ttu-id="23bed-147">本書と関連サンプルは継続的に更新されるので、お客様のフィードバックを歓迎しています。</span><span class="sxs-lookup"><span data-stu-id="23bed-147">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="23bed-148">本書を改善する方法についてコメントがある場合、[GitHub の問題](https://github.com/dotnet/docs/issues)に関して作成されたあらゆるページの下部にあるフィードバック セクションをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="23bed-148">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="23bed-149">次へ</span><span class="sxs-lookup"><span data-stu-id="23bed-149">Next</span></span>](foreword.md)
