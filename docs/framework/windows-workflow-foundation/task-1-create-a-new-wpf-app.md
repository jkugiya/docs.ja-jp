---
description: '詳細については、「タスク 1: 新しい Windows Presentation Foundation アプリケーションを作成する」を参照してください。'
title: タスク 1:新しい Windows Presentation Foundation アプリケーションの作成
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 7bbb49e3d663d1878b2b3e150a24f775eeca0135
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755240"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="ea280-103">タスク 1:新しい Windows Presentation Foundation アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="ea280-103">Task 1: Create a New Windows Presentation Foundation Application</span></span>

<span data-ttu-id="ea280-104">このタスクでは、WPF Application Visual Studio テンプレートを使用して空の Windows Presentation Foundation (WPF) アプリケーションを作成し、適切なワークフローアセンブリに参照を追加し [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ea280-104">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
## <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="ea280-105">WPF アプリケーション プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="ea280-105">To create the WPF Application project</span></span>

1. <span data-ttu-id="ea280-106">Visual Studio を開き、[ **ファイル** ] メニューの [ **新規作成**] をポイントし、[ **プロジェクト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea280-106">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="ea280-107">[**新しいプロジェクト**] ダイアログボックスで、ボックスの左側にある [**インストールされたテンプレート**] ペインの [ **Visual C#** ] または [ **Visual Basic** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea280-107">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="ea280-108">選択した言語が表示されない場合は、[ **その他の言語**] を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea280-108">If the language of your choice does not appear, look under **Other Languages**.</span></span>

3. <span data-ttu-id="ea280-109">[**インストールさ** れたテンプレート] ペインで [ **Windows** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea280-109">Select **Windows** in the **Installed Templates** pane.</span></span>

4. <span data-ttu-id="ea280-110">上部のウィンドウで、ドロップダウンリストボックスで (既定値) **.NET Framework 4** が選択されていることを確認し、[ **WPF アプリケーション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea280-110">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>

5. <span data-ttu-id="ea280-111">ウィンドウの下部にあるプロジェクトの名前を **HostingApplication** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ea280-111">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>

6. <span data-ttu-id="ea280-112">ソリューション名を **RehostingTheDesigner** に設定します。</span><span class="sxs-lookup"><span data-stu-id="ea280-112">Set the solution name to **RehostingTheDesigner**.</span></span>

7. <span data-ttu-id="ea280-113">[ **OK]** をクリックして、アプリケーションプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="ea280-113">Click **OK** to create the application project.</span></span> <span data-ttu-id="ea280-114">Visual Studio では、アプリケーション用の基本的な WPF UI が作成され、適切な XAML と分離コードファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ea280-114">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>

8. <span data-ttu-id="ea280-115">**Workflowmodel** アセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="ea280-115">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="ea280-116">これを行うには、 **ソリューションエクスプローラー** で **HostingApplication** プロジェクトを右クリックし、[ **参照の追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea280-116">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>

9. <span data-ttu-id="ea280-117">[ **参照の追加** ] ダイアログボックスで、[ **.net** ] タブをクリックし、CTRL キーを押しながら次のアセンブリを選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea280-117">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>

    - <span data-ttu-id="ea280-118">System.Activities</span><span class="sxs-lookup"><span data-stu-id="ea280-118">System.Activities</span></span>
    - <span data-ttu-id="ea280-119">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="ea280-119">System.Activities.Presentation</span></span>
    - <span data-ttu-id="ea280-120">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="ea280-120">System.Activities.Core.Presentation</span></span>

10. <span data-ttu-id="ea280-121">ワークフローデザイナーデザインキャンバスをホストする方法については [、「タスク 2: ワークフローデザイナーのホスト](task-2-host-the-workflow-designer.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea280-121">See [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea280-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea280-122">See also</span></span>

- [<span data-ttu-id="ea280-123">ワークフロー デザイナーのホスト変更</span><span class="sxs-lookup"><span data-stu-id="ea280-123">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="ea280-124">タスク 2:ワークフロー デザイナーのホスティング</span><span class="sxs-lookup"><span data-stu-id="ea280-124">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
