---
description: '詳細情報: データの変更と変更の送信'
title: データの変更と変更の送信
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: 260dab911057b45250d44ded7c254dd903e2aed7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695568"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="c5e2d-103">データの変更と変更の送信</span><span class="sxs-lookup"><span data-stu-id="c5e2d-103">Making and Submitting Data Changes</span></span>

<span data-ttu-id="c5e2d-104">このセクションのトピックでは、データベースを変更し、その変更を送信する方法と、オプティミスティック コンカレンシーの競合を処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c5e2d-104">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>

> [!NOTE]
> <span data-ttu-id="c5e2d-105">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の `Insert`、`Update`、および `Delete` の既定のデータベース操作メソッドはオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="c5e2d-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="c5e2d-106">詳細については、「[挿入、更新、および削除の各操作のカスタマイズ](customizing-insert-update-and-delete-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5e2d-106">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="c5e2d-107">Visual Studio を使用している開発者は、オブジェクト リレーショナル デザイナーを使用して、同じ用途のストアド プロシージャを開発できます。</span><span class="sxs-lookup"><span data-stu-id="c5e2d-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c5e2d-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c5e2d-108">In This Section</span></span>

<span data-ttu-id="c5e2d-109">[方法: 行をデータベースに挿入する](how-to-insert-rows-into-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="c5e2d-109">[How to: Insert Rows Into the Database](how-to-insert-rows-into-the-database.md) </span></span>\
<span data-ttu-id="c5e2d-110">オブジェクト モデルにオブジェクトを追加することにより、データベースに行を挿入する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c5e2d-110">Describes how to insert rows in the database by adding objects to the object model.</span></span>

<span data-ttu-id="c5e2d-111">[方法: データベースの行を更新する](how-to-update-rows-in-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="c5e2d-111">[How to: Update Rows in the Database](how-to-update-rows-in-the-database.md) </span></span>\
<span data-ttu-id="c5e2d-112">オブジェクト モデルのオブジェクトを更新することにより、データベースの行を更新する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c5e2d-112">Describes how to update rows in the database by updating objects in the object model.</span></span>

<span data-ttu-id="c5e2d-113">[方法: 行をデータベースから削除する](how-to-delete-rows-from-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="c5e2d-113">[How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md) </span></span>\
<span data-ttu-id="c5e2d-114">オブジェクト モデルのオブジェクトを削除することにより、データベースの行を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c5e2d-114">Describes how to delete rows in the database by deleting objects in the object model.</span></span>

<span data-ttu-id="c5e2d-115">[方法: データベースに変更内容を送信する](how-to-submit-changes-to-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="c5e2d-115">[How to: Submit Changes to the Database](how-to-submit-changes-to-the-database.md) </span></span>\
<span data-ttu-id="c5e2d-116">オブジェクト モデルに対する変更をデータベースに送信する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c5e2d-116">Describes how to send object-model changes to the database.</span></span>

<span data-ttu-id="c5e2d-117">[方法: データ送信をトランザクションで囲む](how-to-bracket-data-submissions-by-using-transactions.md) </span><span class="sxs-lookup"><span data-stu-id="c5e2d-117">[How to: Bracket Data Submissions by Using Transactions](how-to-bracket-data-submissions-by-using-transactions.md) </span></span>\
<span data-ttu-id="c5e2d-118">トランザクションに操作を含める方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c5e2d-118">Describes how to include operations in a transaction.</span></span>

<span data-ttu-id="c5e2d-119">[方法: データベースを動的に作成する](how-to-dynamically-create-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="c5e2d-119">[How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md) </span></span>\
<span data-ttu-id="c5e2d-120">動的にデータベースを生成する方法と、この方法を使用する一般的なシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c5e2d-120">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>

<span data-ttu-id="c5e2d-121">[方法: 変更の競合を管理する](how-to-manage-change-conflicts.md) </span><span class="sxs-lookup"><span data-stu-id="c5e2d-121">[How to: Manage Change Conflicts](how-to-manage-change-conflicts.md) </span></span>\
<span data-ttu-id="c5e2d-122">オプティミスティック コンカレンシーの問題に対処する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c5e2d-122">Describes techniques for addressing optimistic concurrency issues.</span></span>
