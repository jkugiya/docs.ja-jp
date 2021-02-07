---
description: '詳細情報: 実行可能インスタンスの検出期間'
title: 実行可能インスタンス検出期間
ms.date: 03/30/2017
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
ms.openlocfilehash: fc4305c11361a3d9ccf7079f4f1b639fb507c469
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720021"
---
# <a name="runnable-instances-detection-period"></a><span data-ttu-id="f86e0-103">実行可能インスタンス検出期間</span><span class="sxs-lookup"><span data-stu-id="f86e0-103">Runnable Instances Detection Period</span></span>

<span data-ttu-id="f86e0-104">SQL Workflow Instance Store が実行する内部タスクは、定期的にアクティブになり、実行可能またはアクティブ化可能なインスタンスを永続性データベースで検出します。</span><span class="sxs-lookup"><span data-stu-id="f86e0-104">The SQL Workflow Instance Store runs an internal task that periodically wakes up and detects runnable or activatable instances in the persistence database.</span></span> <span data-ttu-id="f86e0-105">SQL Workflow Instance Store の "実行可能 **インスタンス検出期間** " プロパティは、前の検出サイクルの後に、Sql Workflow instance store が永続性データベースで実行可能またはアクティブ化可能なワークフローインスタンスを検出する検出タスクを実行するまでの期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="f86e0-105">The **Runnable Instances Detection Period** property of the SQL Workflow Instance Store specifies the time period after which the SQL Workflow Instance Store runs a detection task to detect any runnable or activatable workflow instances in the persistence database after the previous detection cycle.</span></span>  
  
 <span data-ttu-id="f86e0-106">このプロパティの間隔を短く設定すると、ワークフロー インスタンスに関連付けられたタイマーの期限切れと、イベントのシグナリングおよび後続のインスタンスの読み込みの間の時間が短くなります。</span><span class="sxs-lookup"><span data-stu-id="f86e0-106">Setting a shorter interval for this property reduces the time between the expiration of a timer associated with a workflow instance and the signaling of the event and subsequent loading of the instance.</span></span> <span data-ttu-id="f86e0-107">ただし、ホストにかかる処理の負荷も増えるため、永続的なタイマーやホスト エラーがまれなシナリオでは望ましくない場合があります。</span><span class="sxs-lookup"><span data-stu-id="f86e0-107">However, it also increases the processing load on a host and may not be desirable in scenarios where durable timers and/or host failures are rare.</span></span> <span data-ttu-id="f86e0-108">プロパティの型は TimeSpan で、プロパティの値は hh:mm:ss の形式です。</span><span class="sxs-lookup"><span data-stu-id="f86e0-108">The type of the property is TimeSpan and the value of the property follows the format: hh:mm:ss.</span></span> <span data-ttu-id="f86e0-109">このプロパティの最小値は 00:00:01 です。</span><span class="sxs-lookup"><span data-stu-id="f86e0-109">The minimum value for this property is 00:00:01.</span></span> <span data-ttu-id="f86e0-110">プロパティの既定値は 00:00:05 です。</span><span class="sxs-lookup"><span data-stu-id="f86e0-110">The default value for the property is 00:00:05.</span></span>  
  
 <span data-ttu-id="f86e0-111">実行可能およびアクティブ化可能なワークフローインスタンスの検出とアクティブ化の詳細については、「 [インスタンスのアクティブ化](instance-activation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f86e0-111">For more information detecting and activating runnable and activatable workflow instances, see [Instance Activation](instance-activation.md).</span></span>
