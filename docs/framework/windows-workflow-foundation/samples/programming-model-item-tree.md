---
description: '詳細情報: モデルアイテムツリーのプログラミング'
title: モデル アイテム ツリーのプログラミング
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: 8dfcab99bb5e32d202fe2bdc09d63d8b7da6e748
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741851"
---
# <a name="programming-model-item-tree"></a><span data-ttu-id="c4e12-103">モデル アイテム ツリーのプログラミング</span><span class="sxs-lookup"><span data-stu-id="c4e12-103">Programming Model Item Tree</span></span>

<span data-ttu-id="c4e12-104">このサンプル <xref:System.Activities.Presentation.Model.ModelItem> では、Windows Presentation Foundation (WPF) ツリービューの宣言型データバインディングを使用してツリー内を移動する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c4e12-104">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="c4e12-105">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="c4e12-105">Sample Details</span></span>

 <span data-ttu-id="c4e12-106"><xref:System.Activities.Presentation.Model.ModelItem>ツリーは、編集されている基になるインスタンスに関するデータを公開するために Windows ワークフローデザイナーインフラストラクチャによって使用される抽象化です。</span><span class="sxs-lookup"><span data-stu-id="c4e12-106">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the Windows Workflow Designer infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="c4e12-107">次の図は、ワークフローデザイナー内のインフラストラクチャのさまざまな層を示しています。</span><span class="sxs-lookup"><span data-stu-id="c4e12-107">The following illustration is a depiction of the various layers of infrastructure within the Workflow Designer.</span></span>

 ![ワークフローデザイナーアーキテクチャを示す図。](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="c4e12-109"><xref:System.Activities.Presentation.Model.ModelItem> は、基になる値へのポインターと、<xref:System.Activities.Presentation.Model.ModelProperty> オブジェクトのコレクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="c4e12-109">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="c4e12-110"><xref:System.Activities.Presentation.Model.ModelProperty> オブジェクトはさらに、プロパティの名前や型などのデータと、また別の <xref:System.Activities.Presentation.Model.ModelItem> である値へのポインターで構成されています。</span><span class="sxs-lookup"><span data-stu-id="c4e12-110">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="c4e12-111"><xref:System.Activities.Presentation.Model.ModelItem> から返される一部の <xref:System.Activities.Presentation.Model.ModelProperty> に対しては、ツリー ビューに正しく表示されるように操作するために値コンバーターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4e12-111">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="c4e12-112">このサンプルでは、次の例のような命令構文を使用して <xref:System.Activities.Presentation.Model.ModelItem> ツリーを命令型プログラミングで操作する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c4e12-112">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="c4e12-113">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="c4e12-113">To use this sample</span></span>

1. <span data-ttu-id="c4e12-114">Visual Studio 2010 で ProgrammingModelItemTree ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="c4e12-114">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="c4e12-115">[**ビルド**] メニューの [**ソリューションのビルド**] を選択して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="c4e12-115">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="c4e12-116">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="c4e12-116">Press F5 to run the application.</span></span> <span data-ttu-id="c4e12-117">WPF フォームが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4e12-117">The WPF form is then displayed.</span></span>

4. <span data-ttu-id="c4e12-118">[ **WF の読み込み** ] ボタンをクリックすると、が読み込まれ、 <xref:System.Activities.Presentation.Model.ModelItem> ツリービューにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="c4e12-118">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="c4e12-119">[ **モデル項目ツリーの変更** ] ボタンをクリックすると、前のコードが実行され、ツリーに項目が追加され、プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="c4e12-119">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c4e12-120">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="c4e12-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c4e12-121">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c4e12-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c4e12-122">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="c4e12-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c4e12-123">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c4e12-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="c4e12-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4e12-124">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
