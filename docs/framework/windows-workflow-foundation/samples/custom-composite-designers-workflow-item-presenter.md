---
description: 詳細については、「カスタム複合デザイナー-ワークフロー項目プレゼンター」を参照してください。
title: カスタム複合デザイナー - Workflow Item Presenter
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: 20a3bddf7efd69b6138d6b8a5caae250aa377999
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787813"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="af186-103">カスタム複合デザイナー - Workflow Item Presenter</span><span class="sxs-lookup"><span data-stu-id="af186-103">Custom Composite Designers - Workflow Item Presenter</span></span>

<span data-ttu-id="af186-104"><xref:System.Activities.Presentation.WorkflowItemPresenter>は、任意のアクティビティを配置できる "ドロップゾーン" の作成を可能にする WF デザイナープログラミングモデルのキーの種類です。</span><span class="sxs-lookup"><span data-stu-id="af186-104">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="af186-105">このサンプルでは、このような "ドロップゾーン" を格納するアクティビティデザイナーを構築する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="af186-105">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>

<span data-ttu-id="af186-106">このサンプルは次の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="af186-106">This sample demonstrates:</span></span>

- <span data-ttu-id="af186-107"><xref:System.Activities.Presentation.WorkflowItemPresenter> を使用したカスタム アクティビティ デザイナーの作成</span><span class="sxs-lookup"><span data-stu-id="af186-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

- <span data-ttu-id="af186-108">メタデータ ストアを使用したカスタム デザイナーの登録。</span><span class="sxs-lookup"><span data-stu-id="af186-108">Registering the custom designer using the metadata store.</span></span>

- <span data-ttu-id="af186-109">宣言および命令による再ホストされたツールボックスのプログラミング。</span><span class="sxs-lookup"><span data-stu-id="af186-109">Programming the rehosted toolbox declaratively and imperatively.</span></span>

## <a name="sample-details"></a><span data-ttu-id="af186-110">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="af186-110">Sample Details</span></span>

<span data-ttu-id="af186-111">このサンプルのコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="af186-111">The code for this sample shows:</span></span>

- <span data-ttu-id="af186-112">カスタム アクティビティ デザイナーは `SimpleNativeActivity` クラス用に作成されます。</span><span class="sxs-lookup"><span data-stu-id="af186-112">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>

- <span data-ttu-id="af186-113"><xref:System.Activities.Presentation.WorkflowItemPresenter> を使用してカスタム アクティビティ デザイナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="af186-113">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

```xaml
<sap:ActivityDesigner x:Class="Microsoft.Samples.UsingWorkflowItemPresenter.SimpleNativeDesigner"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
    xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
    <sap:ActivityDesigner.Resources>
        <DataTemplate x:Key="Collapsed">
            <StackPanel>
                <TextBlock>This is the collapsed view</TextBlock>
            </StackPanel>
        </DataTemplate>
        <DataTemplate x:Key="Expanded">
            <StackPanel>
                <TextBlock>Custom Text</TextBlock>
                <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                        HintText="Please drop an activity here" />
            </StackPanel>
        </DataTemplate>
        <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
            <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
            <Style.Triggers>
                <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                    <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                </DataTrigger>
            </Style.Triggers>
        </Style>
    </sap:ActivityDesigner.Resources>
    <Grid>
        <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
    </Grid>
</sap:ActivityDesigner>
```

 <span data-ttu-id="af186-114">`ModelItem.Body` にバインドする WPF のデータ バインディングの使用に注意してください。</span><span class="sxs-lookup"><span data-stu-id="af186-114">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="af186-115">`ModelItem` は、 <xref:System.Activities.Presentation.ActivityDesigner> デザイナーが使用されている基になるオブジェクト (この場合は **simplenativeactivity)**) を参照するのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="af186-115">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="af186-116">サンプルをセットアップ、ビルド、および実行する</span><span class="sxs-lookup"><span data-stu-id="af186-116">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="af186-117">Visual Studio でソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="af186-117">Open the solution in Visual Studio.</span></span>

2. <span data-ttu-id="af186-118">**F5** キーを押して、アプリケーションをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="af186-118">Press **F5** to compile and run the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="af186-119">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="af186-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="af186-120">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="af186-120">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="af186-121">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="af186-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="af186-122">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="af186-122">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`

## <a name="see-also"></a><span data-ttu-id="af186-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="af186-123">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [<span data-ttu-id="af186-124">ワークフロー デザイナーを使用したアプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="af186-124">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
