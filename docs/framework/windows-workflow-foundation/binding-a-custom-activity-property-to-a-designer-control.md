---
description: '詳細情報: デザイナーコントロールへのカスタムアクティビティプロパティのバインド'
title: デザイナー コントロールへのカスタム アクティビティ プロパティのバインド
ms.date: 03/30/2017
ms.assetid: 2e8061ea-10f5-407c-a31f-d0d74ce12f27
ms.openlocfilehash: 522e3df3028270d42f7654026383c628ec951e8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787943"
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a><span data-ttu-id="dc66f-103">デザイナー コントロールへのカスタム アクティビティ プロパティのバインド</span><span class="sxs-lookup"><span data-stu-id="dc66f-103">Binding a custom activity property to a designer control</span></span>

<span data-ttu-id="dc66f-104">テキスト ボックスのデザイナー コントロールをアクティビティ引数にバインドする方法はきわめて簡単ですが、コンボ ボックスなどの複合デザイナー コントロールをアクティビティ引数にバインドする場合は困難が伴うことがあります。</span><span class="sxs-lookup"><span data-stu-id="dc66f-104">Binding a text box designer control to an activity argument is fairly straightforward; binding a complex designer control (such as a combo box) to an activity argument may present challenges, however.</span></span> <span data-ttu-id="dc66f-105">このトピックでは、カスタム アクティビティ デザイナーでアクティビティ引数をコンボ ボックス コントロールにバインドする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-105">This topic discusses how to bind an activity argument to a combo box control on a custom activity designer.</span></span>

## <a name="creating-the-combo-box-item-converter"></a><span data-ttu-id="dc66f-106">コンボ ボックス項目コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="dc66f-106">Creating the combo box item converter</span></span>

1. <span data-ttu-id="dc66f-107">Visual Studio で、CustomProperty という名前で新しい空のソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-107">Create a new empty solution in Visual Studio called CustomProperty.</span></span>

2. <span data-ttu-id="dc66f-108">ComboBoxItemConverter という名前で新しいクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-108">Create a new class called ComboBoxItemConverter.</span></span> <span data-ttu-id="dc66f-109">System.Windows.Data に参照を追加し、<xref:System.Windows.Data.IValueConverter> の派生クラスを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="dc66f-109">Add a reference to System.Windows.Data, and have the class derive from <xref:System.Windows.Data.IValueConverter>.</span></span> <span data-ttu-id="dc66f-110">Visual Studio で、`Convert` および `ConvertBack` のスタブを生成するインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-110">Have Visual Studio implement the interface to generate stubs for `Convert` and `ConvertBack`.</span></span>

3. <span data-ttu-id="dc66f-111">`Convert` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-111">Add the following code to the `Convert` method.</span></span> <span data-ttu-id="dc66f-112">次のコードはアクティビティの <xref:System.Activities.InArgument%601> 型の <xref:System.String> をデザイナーに配置される値に変換します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-112">This code converts the activity's <xref:System.Activities.InArgument%601> of type <xref:System.String> to the value to be placed in the designer.</span></span>

    ```csharp
    ModelItem modelItem = value as ModelItem;
    if (value != null)
    {
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;

        if (inArgument != null)
        {
            Activity<string> expression = inArgument.Expression;
            VisualBasicValue<string> vbexpression = expression as VisualBasicValue<string>;
            Literal<string> literal = expression as Literal<string>;

            if (literal != null)
            {
                return "\"" + literal.Value + "\"";
            }
            else if (vbexpression != null)
            {
                return vbexpression.ExpressionText;
            }
        }
    }
    return null;
    ```

     <span data-ttu-id="dc66f-113">上のコード スニペットの式は、<xref:Microsoft.CSharp.Activities.CSharpValue%601> の代わりに <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> を使用しても作成できます。</span><span class="sxs-lookup"><span data-stu-id="dc66f-113">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>

    ```csharp
    ModelItem modelItem = value as ModelItem;
    if (value != null)
    {
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;

        if (inArgument != null)
        {
            Activity<string> expression = inArgument.Expression;
            CSharpValue<string> csexpression = expression as CSharpValue<string>;
            Literal<string> literal = expression as Literal<string>;

            if (literal != null)
            {
                return "\"" + literal.Value + "\"";
            }
            else if (csexpression != null)
            {
                return csexpression.ExpressionText;
            }
        }
    }
    return null;
    ```

4. <span data-ttu-id="dc66f-114">`ConvertBack` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-114">Add the following code to the `ConvertBack` method.</span></span> <span data-ttu-id="dc66f-115">このコードは受信コンボ ボックス項目を <xref:System.Activities.InArgument%601> に戻します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-115">This code converts the incoming combo box item back to an <xref:System.Activities.InArgument%601>.</span></span>

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(vbArgument);
                return inArgument;
    ```

     <span data-ttu-id="dc66f-116">上のコード スニペットの式は、<xref:Microsoft.CSharp.Activities.CSharpValue%601> の代わりに <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> を使用しても作成できます。</span><span class="sxs-lookup"><span data-stu-id="dc66f-116">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(csArgument);
                return inArgument;
    ```

## <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a><span data-ttu-id="dc66f-117">アクティビティのカスタム デザイナーへの ComboBoxItemConverter の追加</span><span class="sxs-lookup"><span data-stu-id="dc66f-117">Adding the ComboBoxItemConverter to the custom designer of an activity</span></span>

1. <span data-ttu-id="dc66f-118">新しい項目をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-118">Add a new item to the project.</span></span> <span data-ttu-id="dc66f-119">[新しい項目] ダイアログ ボックスで [ワークフロー] ノードを選択し、新しい項目の種類として [アクティビティ デザイナー] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-119">In the New Item dialog, select the Workflow node and select Activity Designer as the type of the new item.</span></span> <span data-ttu-id="dc66f-120">項目に CustomPropertyDesigner という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="dc66f-120">Name the item CustomPropertyDesigner.</span></span>

2. <span data-ttu-id="dc66f-121">新しいデザイナーにコンボ ボックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-121">Add a Combo Box to the new designer.</span></span> <span data-ttu-id="dc66f-122">Items プロパティには、コンボ ボックスに 2 つの項目を追加し、コンテンツの値に "Item1" および "Item2" を指定します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-122">In the Items property, add a couple of items to the combo box, with Content values of "Item1" and 'Item2".</span></span>

3. <span data-ttu-id="dc66f-123">コンボ ボックスの XAML を変更し、新しい項目コンバーターをコンボ ボックスに使用する項目コンバーターとして追加します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-123">Modify the XAML of the combo box to add the new item converter as the item converter to be used for the combo box.</span></span> <span data-ttu-id="dc66f-124">コンバーターは ActivityDesigner.Resources セグメントにリソースとして追加され、<xref:System.Windows.Controls.ComboBox> の Converter 属性にコンバーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-124">The converter is added as a resource in the ActivityDesigner.Resources segment, and specifies the converter in the Converter attribute for the <xref:System.Windows.Controls.ComboBox>.</span></span> <span data-ttu-id="dc66f-125">プロジェクトの名前空間はアクティビティ デザイナーの名前空間属性で指定します。デザイナーを別のプロジェクトで使用する場合は、この名前空間を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc66f-125">Note that the namespace of the project is specified in the namespaces attributes for the activity designer; if the designer is to be used in a different project, this namespace will need to be changed.</span></span>

    ```xaml
    <sap:ActivityDesigner x:Class="CustomProperty.CustomPropertyDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:c="clr-namespace:CustomProperty"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">

        <sap:ActivityDesigner.Resources>
            <ResourceDictionary>
                <c:ComboBoxItemConverter x:Key="comboBoxItemConverter"/>
            </ResourceDictionary>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ComboBox SelectedValue="{Binding Path=ModelItem.Text, Mode=TwoWay, Converter={StaticResource comboBoxItemConverter}}"  Height="23" HorizontalAlignment="Left" Margin="132,5,0,0" Name="comboBox1" VerticalAlignment="Top" Width="120" ItemsSource="{Binding}">
                <ComboBoxItem>item1</ComboBoxItem>
                <ComboBoxItem>item2</ComboBoxItem>
            </ComboBox>
        </Grid>
    </sap:ActivityDesigner>
    ```

4. <span data-ttu-id="dc66f-126"><xref:System.Activities.CodeActivity> 型の新しい項目を作成します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-126">Create a new item of type <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="dc66f-127">この例では、アクティビティの IDE によって作成された既定のコードで十分です。</span><span class="sxs-lookup"><span data-stu-id="dc66f-127">The default code created by the IDE for the activity will be sufficient for this example.</span></span>

5. <span data-ttu-id="dc66f-128">クラス定義に次の属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-128">Add the following attribute to the class definition:</span></span>

    ```csharp
    [Designer(typeof(CustomPropertyDesigner))]
    ```

     <span data-ttu-id="dc66f-129">この行は、新しいデザイナーを新しいクラスに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="dc66f-129">This line associates the new designer with the new class.</span></span>

 <span data-ttu-id="dc66f-130">これで新しいアクティビティがデザイナーに関連付けられました。</span><span class="sxs-lookup"><span data-stu-id="dc66f-130">The new activity should now be associated with the designer.</span></span> <span data-ttu-id="dc66f-131">新しいアクティビティをテストするには、アクティビティをワークフローに追加し、コンボ ボックスに 2 つの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="dc66f-131">To test the new activity, add it to a workflow, and set the combo box to the two values.</span></span> <span data-ttu-id="dc66f-132">プロパティ ウィンドウが更新されてコンボ ボックスの値が反映されます。</span><span class="sxs-lookup"><span data-stu-id="dc66f-132">The properties window should update to reflect the combo box value.</span></span>
