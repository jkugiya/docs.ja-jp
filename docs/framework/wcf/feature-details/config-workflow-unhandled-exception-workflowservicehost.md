---
description: '詳細については、「方法: WorkflowServiceHost を使用してワークフローの未処理の例外動作を構成する」を参照してください。'
title: '方法: WorkflowServiceHost を使用してワークフロー サービスの未処理の例外動作を構成する'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 7d32ccf1262895d948cae26f0922adf3003664ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743383"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="db46f-103">方法: WorkflowServiceHost を使用してワークフロー サービスの未処理の例外動作を構成する</span><span class="sxs-lookup"><span data-stu-id="db46f-103">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>

<span data-ttu-id="db46f-104"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> は、<xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされるワークフロー内で未処理の例外が発生した場合のアクションを指定できるようにする動作です。</span><span class="sxs-lookup"><span data-stu-id="db46f-104">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="db46f-105">このトピックでは、この動作を構成ファイルで構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="db46f-105">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="db46f-106">WorkflowUnhandledExceptionBehavior を構成するには</span><span class="sxs-lookup"><span data-stu-id="db46f-106">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1. <span data-ttu-id="db46f-107">次の例に示すように、属性を使用して、ハンドルされ `workflowUnhandledException` `behavior` `serviceBehaviors` `action` ない例外が発生したときに実行するアクションを指定して、<> 要素内の <> 要素に <> 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="db46f-107">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="db46f-108">前の構成サンプルでは、簡略化された構成を使用しています。</span><span class="sxs-lookup"><span data-stu-id="db46f-108">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="db46f-109">詳細については、「簡略化された [構成](../simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db46f-109">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="db46f-110">この動作は、次の例に示すように、コードで構成できます。</span><span class="sxs-lookup"><span data-stu-id="db46f-110">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="db46f-111">`action`<> 要素の属性は、 `workflowUnhandledException` 次のいずれかの値に設定できます。</span><span class="sxs-lookup"><span data-stu-id="db46f-111">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="db46f-112">**破棄**</span><span class="sxs-lookup"><span data-stu-id="db46f-112">**abandon**</span></span>  
     <span data-ttu-id="db46f-113">永続化されているインスタンス状態を変更することなく、メモリ内のインスタンスを中止します (つまり、最後の永続性ポイントにロールバックします)。</span><span class="sxs-lookup"><span data-stu-id="db46f-113">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="db46f-114">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="db46f-114">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="db46f-115">メモリ内のインスタンスを中止し、永続化されているインスタンスを中断状態に更新します。</span><span class="sxs-lookup"><span data-stu-id="db46f-115">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="db46f-116">**cancel**</span><span class="sxs-lookup"><span data-stu-id="db46f-116">**cancel**</span></span>  
     <span data-ttu-id="db46f-117">インスタンスのキャンセル ハンドラーを呼び出してから、メモリ内のインスタンスを完了状態にします。これにより、そのインスタンスがインスタンス ストアから削除される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="db46f-117">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="db46f-118">**解約**</span><span class="sxs-lookup"><span data-stu-id="db46f-118">**terminate**</span></span>  
     <span data-ttu-id="db46f-119">メモリ内のインスタンスを完了状態にし、そのインスタンスをインスタンス ストアから削除します。</span><span class="sxs-lookup"><span data-stu-id="db46f-119">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="db46f-120">の詳細について <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> は、「 [ワークフローサービスホストの機能拡張](workflow-service-host-extensibility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db46f-120">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db46f-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="db46f-121">See also</span></span>

- [<span data-ttu-id="db46f-122">ワークフロー サービス ホストの拡張機能</span><span class="sxs-lookup"><span data-stu-id="db46f-122">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)
- [<span data-ttu-id="db46f-123">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="db46f-123">Workflow Services</span></span>](workflow-services.md)
