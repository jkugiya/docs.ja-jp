---
description: 詳細については、「例外、トランザクション、および補正」を参照してください。
title: 例外、トランザクション、および補正
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
ms.openlocfilehash: 3188b0238b1909847c289bb56274671ff4b307b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720190"
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="091b6-103">例外、トランザクション、および補正</span><span class="sxs-lookup"><span data-stu-id="091b6-103">Exceptions, Transactions, and Compensation</span></span>

[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="091b6-104">には、ワークフロー内のランタイム エラー条件を処理するさまざまな機構が用意されています。</span><span class="sxs-lookup"><span data-stu-id="091b6-104">provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="091b6-105">ワークフローでは、例外ハンドラー、トランザクション、キャンセル、および補正の組み合わせを使用して、エラー条件の処理と適切な回復を行えます。</span><span class="sxs-lookup"><span data-stu-id="091b6-105">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="091b6-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="091b6-106">In This Section</span></span>  

 [<span data-ttu-id="091b6-107">例外</span><span class="sxs-lookup"><span data-stu-id="091b6-107">Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="091b6-108"><xref:System.Activities.Statements.TryCatch> アクティビティを使用して、ワークフローで例外を処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="091b6-108">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="091b6-109">トランザクション</span><span class="sxs-lookup"><span data-stu-id="091b6-109">Transactions</span></span>](workflow-transactions.md)  
 <span data-ttu-id="091b6-110"><xref:System.Activities.Statements.TransactionScope> アクティビティを利用してワークフローでトランザクションを使用する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="091b6-110">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="091b6-111">補正</span><span class="sxs-lookup"><span data-stu-id="091b6-111">Compensation</span></span>](compensation.md)  
 <span data-ttu-id="091b6-112">ワークフローの補正について説明します。また、<xref:System.Activities.Statements.CompensableActivity>、<xref:System.Activities.Statements.Compensate>、および <xref:System.Activities.Statements.Confirm> などの補正アクティビティを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="091b6-112">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="091b6-113">キャンセル</span><span class="sxs-lookup"><span data-stu-id="091b6-113">Cancellation</span></span>](modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="091b6-114">組み込みのアクティビティとカスタム アクティビティを使用してワークフローでキャンセル処理を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="091b6-114">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="091b6-115">デバッグのワークフロー</span><span class="sxs-lookup"><span data-stu-id="091b6-115">Debugging Workflows</span></span>](debugging-workflows.md)  
 <span data-ttu-id="091b6-116">ワークフローをデバッグする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="091b6-116">Describes how to debug workflows.</span></span>
