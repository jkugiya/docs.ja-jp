---
description: '詳細情報: WF のプリミティブアクティビティ'
title: WF 内のプリミティブ アクティビティ
ms.date: 03/30/2017
ms.assetid: 8e9009d1-236e-4d8e-86fc-e43132bf6dfc
ms.openlocfilehash: 5f613eeb8f4153f349fad8232f6dec1123b1a8a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742070"
---
# <a name="primitives-activities-in-wf"></a><span data-ttu-id="2be62-103">WF 内のプリミティブ アクティビティ</span><span class="sxs-lookup"><span data-stu-id="2be62-103">Primitives Activities in WF</span></span>

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="2be62-104">には、共通のタスクを実行する便利な機構を提供する、システムによって提供されるアクティビティがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="2be62-104">provides several system-provided activities that provide a convenient mechanism for performing common tasks.</span></span>  
  
|<span data-ttu-id="2be62-105">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="2be62-105">Activity</span></span>|<span data-ttu-id="2be62-106">説明</span><span class="sxs-lookup"><span data-stu-id="2be62-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|<span data-ttu-id="2be62-107">現在のスコープで、変数に値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2be62-107">Assigns a value to a variable at the current scope.</span></span>|  
|<xref:System.Activities.Statements.Delay>|<span data-ttu-id="2be62-108">1 つの実行パスをアイドル状態にして、場合によってはワークフローをアンロードできるようにします。</span><span class="sxs-lookup"><span data-stu-id="2be62-108">Puts one path of execution into an idle state, possibly allowing the workflow to be unloaded.</span></span>|  
|<xref:System.Activities.Statements.InvokeDelegate>|<span data-ttu-id="2be62-109"><xref:System.Activities.ActivityDelegate> から派生し、プロパティとして公開されるデリゲートを実行します。</span><span class="sxs-lookup"><span data-stu-id="2be62-109">Executes a delegate that derives from <xref:System.Activities.ActivityDelegate> and is exposed as a property.</span></span>|  
|<xref:System.Activities.Statements.InvokeMethod>|<span data-ttu-id="2be62-110">CLR オブジェクトのパブリック メソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="2be62-110">Executes a public method of a CLR object.</span></span>|  
|<xref:System.Activities.Statements.WriteLine>|<span data-ttu-id="2be62-111">指定した文字列を、コンソールまたは指定した <xref:System.IO.TextWriter> オブジェクトに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="2be62-111">Writes a specified string to the console or a specified <xref:System.IO.TextWriter> object.</span></span>|
