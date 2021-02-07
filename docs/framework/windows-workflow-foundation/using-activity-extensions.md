---
description: 詳細については、「アクティビティ拡張機能の使用」をご覧ください。
title: アクティビティ拡張機能の使用
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: d0286850bf685497d3a2471a3b4e0db4630070b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755071"
---
# <a name="using-activity-extensions"></a><span data-ttu-id="6418a-103">アクティビティ拡張機能の使用</span><span class="sxs-lookup"><span data-stu-id="6418a-103">Using Activity Extensions</span></span>

<span data-ttu-id="6418a-104">アクティビティは、ワークフローで明示的にモデル化されていない追加機能の提供をホストに許可するワークフロー アプリケーション拡張機能と相互作用することができます。</span><span class="sxs-lookup"><span data-stu-id="6418a-104">Activities can interact with workflow application extensions that allow the host to provide additional functionality that is not explicitly modeled in the workflow.</span></span>  <span data-ttu-id="6418a-105">ここでは、アクティビティの実行回数をカウントする拡張機能を作成および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6418a-105">This topic describes how to create and use an extension to count the number of times the activity executes.</span></span>

### <a name="to-use-an-activity-extension-to-count-executions"></a><span data-ttu-id="6418a-106">実行回数をカウントするアクティビティ拡張機能を使用するには</span><span class="sxs-lookup"><span data-stu-id="6418a-106">To use an activity extension to count executions</span></span>

1. <span data-ttu-id="6418a-107">Visual Studio 2010 を開きます。</span><span class="sxs-lookup"><span data-stu-id="6418a-107">Open Visual Studio 2010.</span></span> <span data-ttu-id="6418a-108">[ **新規**]、[ **プロジェクト**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6418a-108">Select **New**, **Project**.</span></span> <span data-ttu-id="6418a-109">[ **Visual C#** ] ノードで、[ **ワークフロー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6418a-109">Under the **Visual C#** node, select **Workflow**.</span></span>  <span data-ttu-id="6418a-110">テンプレートの一覧から [ **ワークフローコンソールアプリケーション** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6418a-110">Select **Workflow Console Application** from the list of templates.</span></span> <span data-ttu-id="6418a-111">プロジェクトに `Extensions` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="6418a-111">Name the project `Extensions`.</span></span> <span data-ttu-id="6418a-112">**[OK]** をクリックしてプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6418a-112">Click **OK** to create the project.</span></span>

2. <span data-ttu-id="6418a-113">`using`Program.cs 名前空間のステートメント **を、** ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="6418a-113">Add a `using` statement in the Program.cs file for the **System.Collections.Generic** namespace.</span></span>

    ```csharp
    using System.Collections.Generic;
    ```

3. <span data-ttu-id="6418a-114">Program.cs ファイルで、 **Executioncountextension** という名前の新しいクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="6418a-114">In the Program.cs file, create a new class named **ExecutionCountExtension**.</span></span> <span data-ttu-id="6418a-115">次のコードは、その **Register** メソッドが呼び出されたときにインスタンス id を追跡するワークフロー拡張機能を作成します。</span><span class="sxs-lookup"><span data-stu-id="6418a-115">The following code creates a workflow extension that tracks instance IDs when its **Register** method is called.</span></span>

    ```csharp
    // This extension collects a list of workflow Ids
    public class ExecutionCountExtension
    {
        IList<Guid> instances = new List<Guid>();

        public int ExecutionCount
        {
            get
            {
                return this.instances.Count;
            }
        }

        public IEnumerable<Guid> InstanceIds
        {
            get
            {
                return this.instances;
            }
        }

        public void Register(Guid activityInstanceId)
        {
            if (!this.instances.Contains<Guid>(activityInstanceId))
            {
                instances.Add(activityInstanceId);
            }
        }
    }
    ```

4. <span data-ttu-id="6418a-116">**Executioncountextension** を使用するアクティビティを作成します。</span><span class="sxs-lookup"><span data-stu-id="6418a-116">Create an activity that consumes the **ExecutionCountExtension**.</span></span> <span data-ttu-id="6418a-117">次のコードは、ランタイムから **Executioncountextension** オブジェクトを取得し、アクティビティの実行時にその **Register** メソッドを呼び出すアクティビティを定義します。</span><span class="sxs-lookup"><span data-stu-id="6418a-117">The following code defines an activity that retrieves the **ExecutionCountExtension** object from the runtime and calls its **Register** method when the activity executes.</span></span>

    ```csharp
    // Activity that consumes an extension provided by the host. If the extension is available
    // in the context, it will invoke (in this case, registers the Id of the executing workflow)
    public class MyActivity: CodeActivity
    {
        protected override void Execute(CodeActivityContext context)
        {
            ExecutionCountExtension ext = context.GetExtension<ExecutionCountExtension>();
            if (ext != null)
            {
                ext.Register(context.WorkflowInstanceId);
            }

        }
    }
    ```

5. <span data-ttu-id="6418a-118">Program.cs ファイルの **Main** メソッドにアクティビティを実装します。</span><span class="sxs-lookup"><span data-stu-id="6418a-118">Implement the activity in the **Main** method of the program.cs file.</span></span> <span data-ttu-id="6418a-119">次のコードには、2 つの異なるワークフローを生成し、各ワークフローを数回実行して、拡張機能に含まれる結果のデータを表示するメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6418a-119">The following code contains methods to generate two different workflows, execute each workflow several times, and display the resulting data that is contained in the extension.</span></span>

    ```csharp
    class Program
    {
        // Creates a workflow that uses the activity that consumes the extension
        static Activity CreateWorkflow1()
        {
            return new Sequence
            {
                Activities =
                {
                    new MyActivity()
                }
            };
        }

        // Creates a workflow that uses two instances of the activity that consumes the extension
        static Activity CreateWorkflow2()
        {
            return new Sequence
            {
                Activities =
                {
                    new MyActivity(),
                    new MyActivity()
                }
            };
        }

        static void Main(string[] args)
        {
            // create the extension
            ExecutionCountExtension executionCountExt = new ExecutionCountExtension();

            // configure the first invoker and execute 3 times
            WorkflowInvoker invoker = new WorkflowInvoker(CreateWorkflow1());
            invoker.Extensions.Add(executionCountExt);
            invoker.Invoke();
            invoker.Invoke();
            invoker.Invoke();

            // configure the second invoker and execute 2 times
            WorkflowInvoker invoker2 = new WorkflowInvoker(CreateWorkflow2());
            invoker2.Extensions.Add(executionCountExt);
            invoker2.Invoke();
            invoker2.Invoke();

            // show the data in the extension
            Console.WriteLine("Executed {0} times", executionCountExt.ExecutionCount);
            executionCountExt.InstanceIds.ToList().ForEach(i => Console.WriteLine("...{0}", i));
        }
    }
    ```
