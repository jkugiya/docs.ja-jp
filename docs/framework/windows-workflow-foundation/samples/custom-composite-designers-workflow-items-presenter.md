---
description: 詳細については、「カスタム複合デザイナー-ワークフロー項目プレゼンター」を参照してください。
title: カスタム複合デザイナー - Workflow Items Presenter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: 07970763e12eccd981370f1241642cc28f675824
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792584"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a><span data-ttu-id="d5e5b-103">カスタム複合デザイナー - Workflow Items Presenter</span><span class="sxs-lookup"><span data-stu-id="d5e5b-103">Custom Composite Designers - Workflow Items Presenter</span></span>

<span data-ttu-id="d5e5b-104"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> は、格納されている要素のコレクションを編集できる、WF デザイナー プログラミング モデル内の主要な型です。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-104">The <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> is a key type in the WF designer programming model that allows for the editing of a collection of contained elements.</span></span> <span data-ttu-id="d5e5b-105">このサンプルでは、このような編集可能なコレクションを表示するアクティビティ デザイナーの構築方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-105">This sample shows how to build an activity designer that surfaces such an editable collection.</span></span>

<span data-ttu-id="d5e5b-106">このサンプルは次の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-106">This sample demonstrates:</span></span>

- <span data-ttu-id="d5e5b-107"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> を使用したカスタム アクティビティ デザイナーの作成</span><span class="sxs-lookup"><span data-stu-id="d5e5b-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="d5e5b-108">"折りたたまれた" ビューと "展開済み" ビューを使用してアクティビティデザイナーを作成する。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-108">Creating an activity designer with a "collapsed" and "expanded" view.</span></span>

- <span data-ttu-id="d5e5b-109">再ホストされたアプリケーションでの既定のデザイナーのオーバーライド</span><span class="sxs-lookup"><span data-stu-id="d5e5b-109">Overriding a default designer in a rehosted application.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="d5e5b-110">サンプルをセットアップ、ビルド、および実行する</span><span class="sxs-lookup"><span data-stu-id="d5e5b-110">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="d5e5b-111">C# の **UsingWorkflowItemsPresenter** サンプルソリューション、または Visual Studio 2010 の Visual Basic を開きます。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-111">Open the **UsingWorkflowItemsPresenter.sln** sample solution for C# or for Visual Basic in Visual Studio 2010.</span></span>

2. <span data-ttu-id="d5e5b-112">ソリューションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-112">Build and run the solution.</span></span>

   <span data-ttu-id="d5e5b-113">再ホストされたワークフローデザイナーアプリケーションが開き、キャンバスにアクティビティをドラッグできるようになります。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-113">A rehosted workflow designer application opens, and you can drag activities onto the canvas.</span></span>

## <a name="sample-highlights"></a><span data-ttu-id="d5e5b-114">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="d5e5b-114">Sample Highlights</span></span>

<span data-ttu-id="d5e5b-115">このサンプルのコードには、次の内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-115">The code for this sample shows the following:</span></span>

- <span data-ttu-id="d5e5b-116">デザイナーをビルドするアクティビティは `Parallel` です。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-116">The activity a designer is built for:  `Parallel`</span></span>

- <span data-ttu-id="d5e5b-117"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> を使用してカスタム アクティビティ デザイナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-117">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d5e5b-118">次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-118">A few things to point out:</span></span>

  - <span data-ttu-id="d5e5b-119">`ModelItem.Branches` にバインドする WPF のデータ バインディングの使用に注意してください。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-119">Note the use of WPF data binding to bind to `ModelItem.Branches`.</span></span> <span data-ttu-id="d5e5b-120">`ModelItem` は、デザイナーが使用されている、基になるオブジェクト (この例では `WorkflowElementDesigner`) を参照する `Parallel` のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-120">`ModelItem` is the property on `WorkflowElementDesigner` that refers to the underlying object the designer is being used for, in this case, our `Parallel`.</span></span>

  - <span data-ttu-id="d5e5b-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> は、コレクション内の個々の項目間にビジュアル表示を配置するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-121">The <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> can be used to put a visual to display between the individual items in the collection.</span></span>

  - <span data-ttu-id="d5e5b-122"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> は、コレクション内の項目のレイアウトを決定するために提供できるテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-122"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> is a template that can be provided to determine the layout of the items in the collection.</span></span> <span data-ttu-id="d5e5b-123">この例では、水平方向のスタック パネルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-123">In this case, a horizontal stack panel is used.</span></span>

  <span data-ttu-id="d5e5b-124">このコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-124">This following example code shows this.</span></span>

  ```xaml
  <sad:WorkflowItemsPresenter HintText="Drop Activities Here"
                                Items="{Binding Path=ModelItem.Branches}">
      <sad:WorkflowItemsPresenter.SpacerTemplate>
        <DataTemplate>
          <Ellipse Width="10" Height="10" Fill="Black"/>
        </DataTemplate>
      </sad:WorkflowItemsPresenter.SpacerTemplate>
      <sad:WorkflowItemsPresenter.ItemsPanel>
        <ItemsPanelTemplate>
          <StackPanel Orientation="Horizontal"/>
        </ItemsPanelTemplate>
      </sad:WorkflowItemsPresenter.ItemsPanel>
    </sad:WorkflowItemsPresenter>
  ```

- <span data-ttu-id="d5e5b-125">`DesignerAttribute` の `Parallel` 型への関連付けを実行し、報告された属性を出力します。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-125">Perform an association of the `DesignerAttribute` to the `Parallel` type and then output the attributes reported.</span></span>

  - <span data-ttu-id="d5e5b-126">最初に、すべての既定のデザイナーを登録します。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-126">First, register all of the default designers.</span></span>

    <span data-ttu-id="d5e5b-127">このコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-127">The following is the code example.</span></span>

    ```csharp
    // register metadata
    (new DesignerMetadata()).Register();
    RegisterCustomMetadata();
    ```

    ```vb
    ' register metadata
    Dim metadata = New DesignerMetadata()
    metadata.Register()
    ' register custom metadata
    RegisterCustomMetadata()
    ```

  - <span data-ttu-id="d5e5b-128">次に、`RegisterCustomMetadata` メソッドで parallel をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-128">Then, override the parallel in `RegisterCustomMetadata` method.</span></span>

    <span data-ttu-id="d5e5b-129">次に、C# と Visual Basic のコード例をそれぞれ示します。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-129">The following code shows this in C# and Visual Basic.</span></span>

    ```csharp
    void RegisterCustomMetadata()
    {
          AttributeTableBuilder builder = new AttributeTableBuilder();
          builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
          MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

    ```vb
    Sub RegisterCustomMetadata()
       Dim builder As New AttributeTableBuilder()
       builder.AddCustomAttributes(GetType(Parallel), New DesignerAttribute(GetType(CustomParallelDesigner)))
       MetadataStore.AddAttributeTable(builder.CreateTable())
    End Sub
    ```

- <span data-ttu-id="d5e5b-130">最後に、さまざまなデータ テンプレートとトリガーを使用して、`IsRootDesigner` プロパティに基づいて適切なテンプレートを選択していることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-130">Finally, note the use of differing data templates and triggers to select the appropriate template based on the `IsRootDesigner` property.</span></span>

  <span data-ttu-id="d5e5b-131">このコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-131">The following is the code example.</span></span>

  ```xaml
  <sad:ActivityDesigner x:Class="Microsoft.Samples.CustomParallelDesigner"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:sad="clr-namespace:System.Activities.Design;assembly=System.Activities.Design"
      xmlns:sadv="clr-namespace:System.Activities.Design.View;assembly=System.Activities.Design">
    <sad:ActivityDesigner.Resources>
      <DataTemplate x:Key="Expanded">
        <StackPanel>
          <TextBlock>This is the Expanded View</TextBlock>
          <sad:WorkflowItemsPresenter HintText="Drop Activities Here"
                                      Items="{Binding Path=ModelItem.Branches}">
            <sad:WorkflowItemsPresenter.SpacerTemplate>
              <DataTemplate>
                <Ellipse Width="10" Height="10" Fill="Black"/>
              </DataTemplate>
            </sad:WorkflowItemsPresenter.SpacerTemplate>
            <sad:WorkflowItemsPresenter.ItemsPanel>
              <ItemsPanelTemplate>
                <StackPanel Orientation="Horizontal"/>
              </ItemsPanelTemplate>
            </sad:WorkflowItemsPresenter.ItemsPanel>
          </sad:WorkflowItemsPresenter>
        </StackPanel>
      </DataTemplate>
      <DataTemplate x:Key="Collapsed">
        <TextBlock>This is the Collapsed View</TextBlock>
      </DataTemplate>
      <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
        <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
        <Style.Triggers>
          <DataTrigger Binding="{Binding Path=IsRootDesigner}" Value="true">
            <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
          </DataTrigger>
        </Style.Triggers>
      </Style>
    </sad: ActivityDesigner.Resources>
    <Grid>
      <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
    </Grid>
  </sad: ActivityDesigner>
  ```

> [!IMPORTANT]
> <span data-ttu-id="d5e5b-132">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d5e5b-133">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-133">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d5e5b-134">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d5e5b-135">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d5e5b-135">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`

## <a name="see-also"></a><span data-ttu-id="d5e5b-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5e5b-136">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [<span data-ttu-id="d5e5b-137">ワークフロー デザイナーを使用したアプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="d5e5b-137">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
