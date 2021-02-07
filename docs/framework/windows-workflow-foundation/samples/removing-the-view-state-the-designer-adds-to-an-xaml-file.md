---
description: '詳細情報: デザイナーによって XAML ファイルに追加されるビューステートの削除'
title: デザイナーによって XAML ファイルに追加されるビューステートを削除する-WF
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: e6be1e8e4f754085b98f912923ad67cb12893910
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741797"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="dbc64-103">デザイナーによって XAML ファイルに追加されるビューステートを削除する</span><span class="sxs-lookup"><span data-stu-id="dbc64-103">Removing the view state the designer adds to an XAML file</span></span>

<span data-ttu-id="dbc64-104">このサンプルでは、<xref:System.Xaml.XamlWriter> から派生するクラスを作成する方法を示し、XAML ファイルからビュー ステートを削除します。</span><span class="sxs-lookup"><span data-stu-id="dbc64-104">This sample demonstrates how to create a class that derives from <xref:System.Xaml.XamlWriter> and removes view state from a XAML file.</span></span> <span data-ttu-id="dbc64-105">Windows ワークフローデザイナーは、ビューステートと呼ばれる情報を XAML ドキュメントに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="dbc64-105">Windows Workflow Designer writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="dbc64-106">ビュー ステートは、ランタイムでは不必要なレイアウト配置などの、デザイン時に必要な情報を参照します。</span><span class="sxs-lookup"><span data-stu-id="dbc64-106">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> <span data-ttu-id="dbc64-107">ワークフローデザイナーは、編集時にこの情報を XAML ドキュメントに挿入します。</span><span class="sxs-lookup"><span data-stu-id="dbc64-107">Workflow Designer inserts this information into the XAML document as it is edited.</span></span> <span data-ttu-id="dbc64-108">ワークフローデザイナーは、属性を使用してビューステートを XAML ファイルに書き込み `mc:Ignorable` ます。そのため、ランタイムが xaml ファイルを読み込むときに、この情報は読み込まれません。</span><span class="sxs-lookup"><span data-stu-id="dbc64-108">Workflow Designer writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="dbc64-109">このサンプルでは、XAML ノードの処理中にそのビューステート情報を削除するクラスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="dbc64-109">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>

## <a name="discussion"></a><span data-ttu-id="dbc64-110">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="dbc64-110">Discussion</span></span>

<span data-ttu-id="dbc64-111">このサンプルでは、カスタム ライターを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="dbc64-111">This sample demonstrates how to create a custom writer.</span></span>

<span data-ttu-id="dbc64-112">カスタム XAML ライターをビルドするには、<xref:System.Xaml.XamlWriter> を継承するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dbc64-112">To build a custom XAML writer, create a class that inherits from <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="dbc64-113">多くの場合、XAML ライターは入れ子になっているため、"内部" の XAML ライターを追跡します。</span><span class="sxs-lookup"><span data-stu-id="dbc64-113">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="dbc64-114">これらの "内部" ライターは、XAML ライターの残りのスタックへの参照と考えることができます。これにより、複数のエントリポイントを使用して処理を行い、処理をスタックの残りの部分に委任することができます。</span><span class="sxs-lookup"><span data-stu-id="dbc64-114">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>

<span data-ttu-id="dbc64-115">このサンプルには、重要な項目がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="dbc64-115">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="dbc64-116">その 1 つとして、書き込まれる項目がデザイナー名前空間からのものであるかどうかの確認が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="dbc64-116">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="dbc64-117">これにより、ワークフローでデザイナー名前空間の他の型の使用が排除されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="dbc64-117">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>

```csharp
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)
{
    return xamlMember.IsAttachable &&
        xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);
}

const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";

// The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.
public ViewStateCleaningWriter(XamlWriter innerWriter)
{
    this.InnerWriter = innerWriter;
    this.MemberStack = new Stack<XamlMember>();
}

XamlWriter InnerWriter {get; set; }
Stack<XamlMember> MemberStack {get; set; }
```

<span data-ttu-id="dbc64-118">これにより、ノード ストリームの走査中に使用される XAML メンバーのスタックも作成されます。</span><span class="sxs-lookup"><span data-stu-id="dbc64-118">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="dbc64-119">このサンプルの残りの作業は、主に `WriteStartMember` メソッドに含まれています。</span><span class="sxs-lookup"><span data-stu-id="dbc64-119">The remaining work of this sample is largely contained in the `WriteStartMember` method.</span></span>

```csharp
public override void WriteStartMember(XamlMember xamlMember)
{
    MemberStack.Push(xamlMember);

    if (IsDesignerAttachedProperty(xamlMember))
    {
        m_attachedPropertyDepth++;
    }

    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteStartMember(xamlMember);
}
```

<span data-ttu-id="dbc64-120">後続のメソッドで、まだビューステート コンテナーに含まれているかどうかがチェックされ、含まれている場合は制御が戻り、ノードはライター スタックに渡されません。</span><span class="sxs-lookup"><span data-stu-id="dbc64-120">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>

```csharp
public override void WriteValue(Object value)
{
    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteValue(value);
}
```

<span data-ttu-id="dbc64-121">カスタム XAML ライターを使用するには、XAML ライターのスタックでまとめて連結する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbc64-121">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="dbc64-122">この使用方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="dbc64-122">The following code shows how this can be used.</span></span>

```csharp
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);
```

## <a name="to-use-this-sample"></a><span data-ttu-id="dbc64-123">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="dbc64-123">To use this sample</span></span>

1. <span data-ttu-id="dbc64-124">Visual Studio 2010 を使用して、ViewStateCleaningWriter ソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="dbc64-124">Using Visual Studio 2010, open the ViewStateCleaningWriter.sln solution file.</span></span>

2. <span data-ttu-id="dbc64-125">コマンド プロンプトを開き、ViewStageCleaningWriter.exe がビルドされているディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="dbc64-125">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>

3. <span data-ttu-id="dbc64-126">Workflow1.xaml ファイルに対して ViewStateCleaningWriter.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="dbc64-126">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>

   <span data-ttu-id="dbc64-127">実行可能ファイルの構文の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dbc64-127">The syntax for the executable is shown in the following example.</span></span>

   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```

   <span data-ttu-id="dbc64-128">これにより \[ 、すべてのビューステート情報が削除された状態で、XAML ファイルがに出力されます。</span><span class="sxs-lookup"><span data-stu-id="dbc64-128">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>

> [!NOTE]
> <span data-ttu-id="dbc64-129"><xref:System.Activities.Statements.Sequence> ワークフローでは、多数の仮想化のヒントが削除されます。</span><span class="sxs-lookup"><span data-stu-id="dbc64-129">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="dbc64-130">その結果、デザイナーは次回の読み込み時にレイアウトを再計算します。</span><span class="sxs-lookup"><span data-stu-id="dbc64-130">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="dbc64-131">このサンプルを <xref:System.Activities.Statements.Flowchart> に対して使用すると、すべての配置情報および線のルーティング情報が削除され、後続のデザイナーへの読み込み時にすべてのアクティビティが画面の左側に積み上げられます。</span><span class="sxs-lookup"><span data-stu-id="dbc64-131">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>

## <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="dbc64-132">このサンプルで使用するサンプル XAML ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="dbc64-132">To create a sample XAML file for use with this sample</span></span>

1. <span data-ttu-id="dbc64-133">Visual Studio 2010 を開きます。</span><span class="sxs-lookup"><span data-stu-id="dbc64-133">Open Visual Studio 2010.</span></span>

2. <span data-ttu-id="dbc64-134">新しいワークフロー コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="dbc64-134">Create a new Workflow Console Application.</span></span>

3. <span data-ttu-id="dbc64-135">いくつかのアクティビティをキャンバスにドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="dbc64-135">Drag and drop a few activities onto the canvas</span></span>

4. <span data-ttu-id="dbc64-136">ワークフロー XAML ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="dbc64-136">Save the workflow XAML file.</span></span>

5. <span data-ttu-id="dbc64-137">XAML ファイルを調べて、ビューステートの添付プロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="dbc64-137">Inspect the XAML file to see the view state attached properties.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dbc64-138">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="dbc64-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dbc64-139">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="dbc64-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="dbc64-140">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="dbc64-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dbc64-141">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="dbc64-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
