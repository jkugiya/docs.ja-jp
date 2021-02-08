---
description: 詳細については、「WF でのランタイムアクティビティ」を参照してください。
title: WF のランタイム アクティビティ
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: 5ff164539b9efd7b2b8a4e7cffd5239eae6145fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792636"
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="96427-103">WF のランタイム アクティビティ</span><span class="sxs-lookup"><span data-stu-id="96427-103">Runtime Activities in WF</span></span>

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="96427-104">には、永続化や終了などのワークフロー ランタイムの機能にアクセスするために、システムによって提供されるアクティビティがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="96427-104">provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="96427-105">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="96427-105">Activity</span></span>|<span data-ttu-id="96427-106">説明</span><span class="sxs-lookup"><span data-stu-id="96427-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="96427-107">ワークフローがその状態を永続化するように明示的に要求します。</span><span class="sxs-lookup"><span data-stu-id="96427-107">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="96427-108">実行中のワークフロー インスタンスを終了します。</span><span class="sxs-lookup"><span data-stu-id="96427-108">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="96427-109">子アクティビティの永続化を防ぐコンテナー アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="96427-109">A container activity that prevents child activities from persisting.</span></span>|
