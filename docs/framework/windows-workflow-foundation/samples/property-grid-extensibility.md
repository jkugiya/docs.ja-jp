---
description: 詳細については、「プロパティグリッド機能拡張」を参照してください。
title: プロパティグリッドの拡張性-WF サンプル
ms.date: 03/30/2017
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
ms.openlocfilehash: 784705146974ffca5cd2e6c21dba722598544771
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741810"
---
# <a name="property-grid-extensibility"></a><span data-ttu-id="07257-103">プロパティグリッドの機能拡張</span><span class="sxs-lookup"><span data-stu-id="07257-103">Property grid extensibility</span></span>

<span data-ttu-id="07257-104">開発者は、デザイナー内で特定のアクティビティを選択したときに表示されるプロパティ グリッドをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="07257-104">A developer can customize the property grid that is displayed when a given activity is selected within the designer.</span></span> <span data-ttu-id="07257-105">これにより、高度な編集操作の作成が可能になります。</span><span class="sxs-lookup"><span data-stu-id="07257-105">This can be done to create a rich editing experience.</span></span> <span data-ttu-id="07257-106">このサンプルでは、その方法を示します。</span><span class="sxs-lookup"><span data-stu-id="07257-106">This sample shows how this can be done.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="07257-107">対象</span><span class="sxs-lookup"><span data-stu-id="07257-107">Demonstrates</span></span>

<span data-ttu-id="07257-108">ワークフロー デザイナーのプロパティ グリッドの拡張。</span><span class="sxs-lookup"><span data-stu-id="07257-108">Workflow designer property grid extensibility.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07257-109">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="07257-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="07257-110">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="07257-110">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="07257-111">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="07257-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="07257-112">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="07257-112">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a><span data-ttu-id="07257-113">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="07257-113">Discussion</span></span>

<span data-ttu-id="07257-114">開発者がプロパティ グリッドを拡張できるように、プロパティ グリッド エディターのインラインの外観をカスタマイズするオプションと、高度な編集画面用のダイアログを表示するオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="07257-114">To extend the property grid, a developer has options to customize the inline appearance of a property grid editor or provide a dialog that appears for a more advanced editing surface.</span></span> <span data-ttu-id="07257-115">このサンプルでは、インライン エディターとダイアログ エディターの 2 種類のエディターを示します。</span><span class="sxs-lookup"><span data-stu-id="07257-115">There are two different editors demonstrated in this sample; an inline editor and a dialog editor.</span></span>

## <a name="inline-editor"></a><span data-ttu-id="07257-116">インラインエディター</span><span class="sxs-lookup"><span data-stu-id="07257-116">Inline editor</span></span>

<span data-ttu-id="07257-117">インライン エディターのサンプルで示す内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="07257-117">The inline editor sample demonstrates the following:</span></span>

- <span data-ttu-id="07257-118"><xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor> から派生する型を作成します。</span><span class="sxs-lookup"><span data-stu-id="07257-118">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span></span>

- <span data-ttu-id="07257-119">コンストラクターで <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> は、値は Windows Presentation Foundation (WPF) データテンプレートを使用して設定されます。</span><span class="sxs-lookup"><span data-stu-id="07257-119">In the constructor, the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value is set with a Windows Presentation Foundation (WPF) data template.</span></span> <span data-ttu-id="07257-120">これは XAML テンプレートにバインドできますが、このサンプルではコードを使用してデータ バインディングを初期化します。</span><span class="sxs-lookup"><span data-stu-id="07257-120">This can be bound to a XAML template, but in this sample, code is used to initialize data binding.</span></span>

- <span data-ttu-id="07257-121">プロパティ グリッドに表示される項目の <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> のデータ コンテキストは、データ テンプレートに含まれています。</span><span class="sxs-lookup"><span data-stu-id="07257-121">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="07257-122">次のコード (CustomInlineEditor.cs のコード) で、このコンテキストが `Value` プロパティにバインドされていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="07257-122">Note in the following code (from CustomInlineEditor.cs) that this context then binds to the `Value` property.</span></span>

    ```csharp
    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));
    FrameworkElementFactory slider = new FrameworkElementFactory(typeof(Slider));
    Binding sliderBinding = new Binding("Value");
    sliderBinding.Mode = BindingMode.TwoWay;
    slider.SetValue(Slider.MinimumProperty, 0.0);
    slider.SetValue(Slider.MaximumProperty, 100.0);
    slider.SetValue(Slider.ValueProperty, sliderBinding);
    stack.AppendChild(slider);
    ```

- <span data-ttu-id="07257-123">アクティビティとデザイナーが同じアセンブリにあるため、アクティビティ デザイナーの属性の登録は、アクティビティ自体の静的コンストラクターで行われます。SimpleCodeActivity.cs の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="07257-123">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="dialog-editor"></a><span data-ttu-id="07257-124">ダイアログ エディター</span><span class="sxs-lookup"><span data-stu-id="07257-124">Dialog editor</span></span>

<span data-ttu-id="07257-125">ダイアログ エディターのサンプルで示す内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="07257-125">The dialog editor sample demonstrates the following:</span></span>

1. <span data-ttu-id="07257-126"><xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor> から派生する型を作成します。</span><span class="sxs-lookup"><span data-stu-id="07257-126">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span></span>

2. <span data-ttu-id="07257-127">WPF データテンプレートを使用してコンストラクターの値を設定し <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="07257-127">Sets the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value in the constructor with a WPF data template.</span></span> <span data-ttu-id="07257-128">これは XAML で作成できますが、このサンプルではコードで作成します。</span><span class="sxs-lookup"><span data-stu-id="07257-128">This can be created in XAML, but in this sample, this is created in code.</span></span>

3. <span data-ttu-id="07257-129">プロパティ グリッドに表示される項目の <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> のデータ コンテキストは、データ テンプレートに含まれています。</span><span class="sxs-lookup"><span data-stu-id="07257-129">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="07257-130">次のコードで、これが `Value` プロパティにバインドされています。</span><span class="sxs-lookup"><span data-stu-id="07257-130">In the following code, this then binds to the `Value` property.</span></span> <span data-ttu-id="07257-131">FilePickerEditor.cs では、ダイアログを起動するボタンを指定するための <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> を含めることも重要です。</span><span class="sxs-lookup"><span data-stu-id="07257-131">It is critical to also include an <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> to provide the button that raises the dialog in FilePickerEditor.cs.</span></span>

    ```csharp
    this.InlineEditorTemplate = new DataTemplate();

    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));
    stack.SetValue(StackPanel.OrientationProperty, Orientation.Horizontal);
    FrameworkElementFactory label = new FrameworkElementFactory(typeof(Label));
    Binding labelBinding = new Binding("Value");
    label.SetValue(Label.ContentProperty, labelBinding);
    label.SetValue(Label.MaxWidthProperty, 90.0);

    stack.AppendChild(label);

    FrameworkElementFactory editModeSwitch = new FrameworkElementFactory(typeof(EditModeSwitchButton));

    editModeSwitch.SetValue(EditModeSwitchButton.TargetEditModeProperty, PropertyContainerEditMode.Dialog);

    stack.AppendChild(editModeSwitch);

    this.InlineEditorTemplate.VisualTree = stack;
    ```

4. <span data-ttu-id="07257-132">ダイアログの表示を処理するデザイナー型の <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="07257-132">Overrides the <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> method in the designer type to handle the display of the dialog.</span></span> <span data-ttu-id="07257-133">このサンプルでは、基本的な <xref:System.Windows.Forms.FileDialog> を示します。</span><span class="sxs-lookup"><span data-stu-id="07257-133">In this sample, a basic <xref:System.Windows.Forms.FileDialog> is shown.</span></span>

    ```csharp
    public override void ShowDialog(PropertyValue propertyValue, IInputElement commandSource)
    {
        Microsoft.Win32.OpenFileDialog ofd = new Microsoft.Win32.OpenFileDialog();
        if (ofd.ShowDialog() == true)
        {
            propertyValue.Value = ofd.FileName;
        }
    }
    ```

5. <span data-ttu-id="07257-134">アクティビティとデザイナーが同じアセンブリにあるため、アクティビティ デザイナーの属性の登録は、アクティビティ自体の静的コンストラクターで行われます。SimpleCodeActivity.cs の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="07257-134">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="07257-135">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="07257-135">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="07257-136">ソリューションをビルドし、Workflow1.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="07257-136">Build the solution, and then open Workflow1.xaml.</span></span>

2. <span data-ttu-id="07257-137">ツールボックスからデザイナーキャンバスに **SimpleCodeActivity** をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="07257-137">Drag a **SimpleCodeActivity** from the toolbox onto the designer canvas.</span></span>

3. <span data-ttu-id="07257-138">**SimpleCodeActivity** をクリックし、[プロパティ] グリッドを開きます。スライダーコントロールとファイルの選択コントロールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="07257-138">Click the **SimpleCodeActivity** and then open the property grid where there is a slider control and a file picking control.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07257-139">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="07257-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="07257-140">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="07257-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="07257-141">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="07257-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="07257-142">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="07257-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
