---
description: 詳細については、カスタムアクティビティデザイナーでの式の使用に関するページを参照してください。
title: カスタム アクティビティ デザイナーでの ExpressionTextBox の使用
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: c333832c2f955354233371c6572f8ae27e5d8643
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787761"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="ff557-103">カスタム アクティビティ デザイナーでの ExpressionTextBox の使用</span><span class="sxs-lookup"><span data-stu-id="ff557-103">Using the ExpressionTextBox in a Custom Activity Designer</span></span>

<span data-ttu-id="ff557-104">このサンプルでは、カスタム アクティビティ デザイナーで <xref:System.Activities.Presentation.View.ExpressionTextBox> を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ff557-104">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="ff557-105">カスタム アクティビティ `MultiAssign` は、2 つの文字列値を 2 つの文字列変数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ff557-105">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="ff557-106"><xref:System.Activities.Presentation.View.ExpressionTextBox> コントロールには、<xref:System.Activities.InArgument> にバインドされるものと <xref:System.Activities.OutArgument> にバインドされるものがあります。</span><span class="sxs-lookup"><span data-stu-id="ff557-106">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>

## <a name="sample-details"></a><span data-ttu-id="ff557-107">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="ff557-107">Sample details</span></span>

 <span data-ttu-id="ff557-108">`ArgumentToExpressionConverter` は、式を引数にバインドするときに使用される型コンバーターです。</span><span class="sxs-lookup"><span data-stu-id="ff557-108">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="ff557-109">`ConverterParameter` は、必要に応じて、`In` または `Out` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff557-109">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="ff557-110">`InOut` がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ff557-110">`InOut` is not supported.</span></span>

 <span data-ttu-id="ff557-111">`UseLocationExpression`属性は、式が `OutArgument` 左辺値 ("左辺値" または "location value") 式であることを指定するために、s で使用されます。</span><span class="sxs-lookup"><span data-stu-id="ff557-111">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="ff557-112">ほとんど場合、L 値式は、返される `OutArgument` が変数または引数の名前であることを示すために使用される有効な Visual Basic 識別子です。</span><span class="sxs-lookup"><span data-stu-id="ff557-112">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>

 <span data-ttu-id="ff557-113">この例では、`MaxLines` 属性は 1 に設定され、`MinLines` は設定されていません。</span><span class="sxs-lookup"><span data-stu-id="ff557-113">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="ff557-114">つまり、ユーザーによって入力されるテキストの量に関係なく、<xref:System.Activities.Presentation.View.ExpressionTextBox> のサイズが 1 行に固定されることを示しています。</span><span class="sxs-lookup"><span data-stu-id="ff557-114">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="ff557-115"><xref:System.Activities.Presentation.View.ExpressionTextBox> がユーザーの入力に合わせて拡大されるようにするには、`MaxLines` に `MinLines` より大きい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="ff557-115">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>

 <span data-ttu-id="ff557-116">ExpressionTextBox は、引数にのみバインドできます。CLR プロパティにはバインドできません。</span><span class="sxs-lookup"><span data-stu-id="ff557-116">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="ff557-117">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="ff557-117">To use this sample</span></span>

1. <span data-ttu-id="ff557-118">Visual Studio 2010 を使用して、ExpressionTextBoxSample ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="ff557-118">Using Visual Studio 2010, open the ExpressionTextBoxSample.sln file.</span></span>

2. <span data-ttu-id="ff557-119">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ff557-119">To build the solution, press CTRL+SHIFT+B.</span></span>

#### <a name="to-run-this-sample"></a><span data-ttu-id="ff557-120">このサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="ff557-120">To run this sample</span></span>

1. <span data-ttu-id="ff557-121">新しいワークフロー コンソール アプリケーションをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="ff557-121">Add a new Workflow Console Application to the solution.</span></span>

2. <span data-ttu-id="ff557-122">新しいワークフローコンソールアプリケーションプロジェクトから、 **ExpressionTextBoxSample** プロジェクトへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="ff557-122">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>

3. <span data-ttu-id="ff557-123">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="ff557-123">Build the solution.</span></span>

4. <span data-ttu-id="ff557-124">[ツールボックス] から [ **Multiassign** ] アクティビティをドラッグし、ワークフローにドロップします。</span><span class="sxs-lookup"><span data-stu-id="ff557-124">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ff557-125">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="ff557-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ff557-126">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ff557-126">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ff557-127">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="ff557-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ff557-128">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ff557-128">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="ff557-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff557-129">See also</span></span>

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [<span data-ttu-id="ff557-130">ワークフロー デザイナーを使用したアプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="ff557-130">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
