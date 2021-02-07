---
description: '詳細については、「タスク 3: ツールボックスペインと PropertyGrid ペインを作成する」を参照してください。'
title: タスク 3:ツールボックス ペインと PropertyGrid ペインの作成
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: c07bfc2f974018cb0d789a6cc1181f9bed861382
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755163"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a><span data-ttu-id="7012a-103">タスク 3:ツールボックス ペインと PropertyGrid ペインの作成</span><span class="sxs-lookup"><span data-stu-id="7012a-103">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>

<span data-ttu-id="7012a-104">このタスクでは、 **ツールボックス** ペインと **PropertyGrid** ペインを作成し、再ホストされた Windows ワークフローデザイナーに追加します。</span><span class="sxs-lookup"><span data-stu-id="7012a-104">In this task, you will create the **Toolbox** and **PropertyGrid** panes and add them to the rehosted Windows Workflow Designer.</span></span>

<span data-ttu-id="7012a-105">参考として、このトピックの最後に、ワークフローデザイナーシリーズのトピックの再 [ホスト](rehosting-the-workflow-designer.md) に関する3つのタスクを完了した後に MainWindow.xaml.cs ファイルに含まれている必要があるコードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7012a-105">For reference, the code that should be in the MainWindow.xaml.cs file after completing the three tasks in the [Rehosting the Workflow Designer](rehosting-the-workflow-designer.md) series of topics is provided at the end of this topic.</span></span>

## <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a><span data-ttu-id="7012a-106">ツールボックスを作成し、グリッドに追加するには</span><span class="sxs-lookup"><span data-stu-id="7012a-106">To create the Toolbox and add it to the grid</span></span>

1. <span data-ttu-id="7012a-107">「 [タスク 2: ワークフローデザイナーをホストする](task-2-host-the-workflow-designer.md)」で説明されている手順に従って、取得した HostingApplication プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="7012a-107">Open the HostingApplication project you obtained by following the procedure described in [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md).</span></span>

2. <span data-ttu-id="7012a-108">**ソリューションエクスプローラー** ペインで、 *mainwindow.xaml* ファイルを右クリックし、[**コードの表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7012a-108">In the **Solution Explorer** pane, right-click the *MainWindow.xaml* file and select **View Code**.</span></span>

3. <span data-ttu-id="7012a-109">`GetToolboxControl` `MainWindow` を作成するクラスにメソッドを追加し <xref:System.Activities.Presentation.Toolbox.ToolboxControl> 、**ツール** ボックスに新しい **ツールボックス** カテゴリを追加して、 <xref:System.Activities.Statements.Assign> アクティビティの <xref:System.Activities.Statements.Sequence> 種類とアクティビティの種類をそのカテゴリに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7012a-109">Add a `GetToolboxControl` method to the `MainWindow` class that creates a <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, adds a new **Toolbox** category to the **Toolbox**, and assigns the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activity types to that category.</span></span>

    ```csharp
    private ToolboxControl GetToolboxControl()
    {
        // Create the ToolBoxControl.
        var ctrl = new ToolboxControl();

        // Create a category.
        var category = new ToolboxCategory("category1");

        // Create Toolbox items.
        var tool1 =
            new ToolboxItemWrapper("System.Activities.Statements.Assign",
            typeof(Assign).Assembly.FullName, null, "Assign");

        var tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",
            typeof(Sequence).Assembly.FullName, null, "Sequence");

        // Add the Toolbox items to the category.
        category.Add(tool1);
        category.Add(tool2);

        // Add the category to the ToolBox control.
        ctrl.Categories.Add(category);
        return ctrl;
    }
    ```

4. <span data-ttu-id="7012a-110">`AddToolbox` `MainWindow` グリッドの左側の列に **ツールボックス** を配置するプライベートメソッドをクラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="7012a-110">Add a private `AddToolbox` method to the `MainWindow` class that places the **Toolbox** in the left column on the grid.</span></span>

    ```csharp
    private void AddToolBox()
    {
        ToolboxControl tc = GetToolboxControl();
        Grid.SetColumn(tc, 0);
        grid1.Children.Add(tc);
    }
    ```

5. <span data-ttu-id="7012a-111">`AddToolBox`次のコードに示すように、クラスコンストラクターにメソッドの呼び出しを追加 `MainWindow()` します。</span><span class="sxs-lookup"><span data-stu-id="7012a-111">Add a call to the `AddToolBox` method in the `MainWindow()` class constructor as shown in the following code:</span></span>

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();

        this.AddToolBox();
    }
    ```

6. <span data-ttu-id="7012a-112"><kbd>F5</kbd>キーを押して、ソリューションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="7012a-112">Press <kbd>F5</kbd> to build and run your solution.</span></span> <span data-ttu-id="7012a-113">アクティビティとアクティビティを含む **ツールボックス** が <xref:System.Activities.Statements.Assign> <xref:System.Activities.Statements.Sequence> 表示されます。</span><span class="sxs-lookup"><span data-stu-id="7012a-113">The **Toolbox** containing the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activities should be displayed.</span></span>

## <a name="to-create-the-propertygrid"></a><span data-ttu-id="7012a-114">PropertyGrid を作成するには</span><span class="sxs-lookup"><span data-stu-id="7012a-114">To create the PropertyGrid</span></span>

1. <span data-ttu-id="7012a-115">**ソリューションエクスプローラー** ペインで、 *mainwindow.xaml* ファイルを右クリックし、[**コードの表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7012a-115">In the **Solution Explorer** pane, right-click the *MainWindow.xaml* file and select **View Code**.</span></span>

2. <span data-ttu-id="7012a-116">クラスにメソッドを追加して、 `AddPropertyInspector` `MainWindow` グリッドの一番右の列に **PropertyGrid** ペインを配置します。</span><span class="sxs-lookup"><span data-stu-id="7012a-116">Add the `AddPropertyInspector` method to the `MainWindow` class to place the **PropertyGrid** pane in the rightmost column on the grid:</span></span>

    ```csharp
    private void AddPropertyInspector()
    {
        Grid.SetColumn(wd.PropertyInspectorView, 2);
        grid1.Children.Add(wd.PropertyInspectorView);
    }
    ```

3. <span data-ttu-id="7012a-117">`AddPropertyInspector`次のコードに示すように、クラスコンストラクターにメソッドの呼び出しを追加 `MainWindow()` します。</span><span class="sxs-lookup"><span data-stu-id="7012a-117">Add a call to the `AddPropertyInspector` method in the `MainWindow()` class constructor as shown in the following code:</span></span>

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();
        this.AddToolBox();

        this.AddPropertyInspector();
    }
    ```

4. <span data-ttu-id="7012a-118"><kbd>F5</kbd>キーを押して、ソリューションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="7012a-118">Press <kbd>F5</kbd> to build and run the solution.</span></span> <span data-ttu-id="7012a-119">[ **ツールボックス**]、[ワークフローデザインキャンバス]、および [ **PropertyGrid** ] の各ウィンドウがすべて表示され <xref:System.Activities.Statements.Assign> ます。また、アクティビティまたはアクティビティをデザインキャンバスにドラッグすると、 <xref:System.Activities.Statements.Sequence> 強調表示されているアクティビティに応じてプロパティグリッドが更新されます。</span><span class="sxs-lookup"><span data-stu-id="7012a-119">The **Toolbox**, workflow design canvas, and **PropertyGrid** panes should all be displayed, and when you drag an <xref:System.Activities.Statements.Assign> activity or a <xref:System.Activities.Statements.Sequence> activity onto the design canvas, the property grid should update depending on the highlighted activity.</span></span>

## <a name="example"></a><span data-ttu-id="7012a-120">例</span><span class="sxs-lookup"><span data-stu-id="7012a-120">Example</span></span>

<span data-ttu-id="7012a-121">*MainWindow.xaml.cs* ファイルには、次のコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7012a-121">The *MainWindow.xaml.cs* file should now contain the following code:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;
// dlls added.
using System.Activities;
using System.Activities.Core.Presentation;
using System.Activities.Presentation;
using System.Activities.Presentation.Metadata;
using System.Activities.Presentation.Toolbox;
using System.Activities.Statements;
using System.ComponentModel;

namespace HostingApplication
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        private WorkflowDesigner wd;

        public MainWindow()
        {
            InitializeComponent();
            RegisterMetadata();
            AddDesigner();
            this.AddToolBox();
            this.AddPropertyInspector();
        }

        private void AddDesigner()
        {
            // Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            // Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            // Load a new Sequence as default.
            this.wd.Load(new Sequence());

            // Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }

        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }

        private ToolboxControl GetToolboxControl()
        {
            // Create the ToolBoxControl.
            var ctrl = new ToolboxControl();

            // Create a category.
            var category = new ToolboxCategory("category1");

            // Create Toolbox items.
            var tool1 =
                new ToolboxItemWrapper("System.Activities.Statements.Assign",
                typeof(Assign).Assembly.FullName, null, "Assign");

            var tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",
                typeof(Sequence).Assembly.FullName, null, "Sequence");

            // Add the Toolbox items to the category.
            category.Add(tool1);
            category.Add(tool2);

            // Add the category to the ToolBox control.
            ctrl.Categories.Add(category);
            return ctrl;
        }

        private void AddToolBox()
        {
            ToolboxControl tc = GetToolboxControl();
            Grid.SetColumn(tc, 0);
            grid1.Children.Add(tc);
        }

        private void AddPropertyInspector()
        {
            Grid.SetColumn(wd.PropertyInspectorView, 2);
            grid1.Children.Add(wd.PropertyInspectorView);
        }

    }
}
```

## <a name="see-also"></a><span data-ttu-id="7012a-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="7012a-122">See also</span></span>

- [<span data-ttu-id="7012a-123">ワークフロー デザイナーのホスト変更</span><span class="sxs-lookup"><span data-stu-id="7012a-123">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="7012a-124">タスク 1:新しい Windows Presentation Foundation アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="7012a-124">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="7012a-125">タスク 2:ワークフロー デザイナーのホスティング</span><span class="sxs-lookup"><span data-stu-id="7012a-125">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
