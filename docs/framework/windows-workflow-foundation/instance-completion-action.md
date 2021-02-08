---
description: '詳細情報: インスタンス完了アクション'
title: インスタンス完了アクション
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 84405ca9869369e4fe00b0049d628671a79a9f68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792688"
---
# <a name="instance-completion-action"></a><span data-ttu-id="26076-103">インスタンス完了アクション</span><span class="sxs-lookup"><span data-stu-id="26076-103">Instance Completion Action</span></span>

<span data-ttu-id="26076-104">SQL Workflow Instance Store の **インスタンス完了アクション** プロパティを使用すると、インスタンスの完了後にワークフローインスタンスのデータとメタデータを永続性データベースから削除するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="26076-104">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="26076-105">このプロパティに指定できる値は、 **DeleteAll** および **DeleteNothing** です。</span><span class="sxs-lookup"><span data-stu-id="26076-105">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="26076-106">これらのオプションについて次の一覧で説明します。</span><span class="sxs-lookup"><span data-stu-id="26076-106">The following list describes these options:</span></span>

- <span data-ttu-id="26076-107">**DeleteAll (既定)。**</span><span class="sxs-lookup"><span data-stu-id="26076-107">**DeleteAll (default).**</span></span> <span data-ttu-id="26076-108">このプロパティの値を DeleteAll に設定すると、ワークフロー インスタンスの完了後に、永続性データベースからワークフロー インスタンスのデータおよびメタデータは削除されます。</span><span class="sxs-lookup"><span data-stu-id="26076-108">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>

- <span data-ttu-id="26076-109">**DeleteNothing。**</span><span class="sxs-lookup"><span data-stu-id="26076-109">**DeleteNothing.**</span></span> <span data-ttu-id="26076-110">このプロパティの値を DeleteNothing に設定すると、ワークフロー インスタンスが完了しても、ワークフロー インスタンスのデータおよびメタデータは永続性データベースに残ります。</span><span class="sxs-lookup"><span data-stu-id="26076-110">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="26076-111">インスタンスの完了後にインスタンス状態情報を残すと、永続性データベースのサイズが大きくなります。</span><span class="sxs-lookup"><span data-stu-id="26076-111">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="26076-112">データベースのサイズが大きくなるにつれて、永続性サブシステムが実行するデータベース操作にかかる時間が長くなります。そのため、永続性データベースからインスタンス状態情報を定期的に削除して、パフォーマンスの要件を満たすレベルでサービスが実行されるようにします。</span><span class="sxs-lookup"><span data-stu-id="26076-112">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
