---
description: '詳細情報: カスタム My 拡張をパッケージ化して配置する (Visual Basic)'
title: カスタム My 拡張のパッケージ化と配置
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 7037cc72951fc5228ae47998f39dca3455bf57de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775410"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a><span data-ttu-id="6b597-103">カスタム My 拡張をパッケージ化して配置する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b597-103">Package and deploy custom My extensions (Visual Basic)</span></span>

<span data-ttu-id="6b597-104">Visual Basic では、Visual Studio テンプレートを使用してカスタムの `My` 名前空間拡張を簡単に配置できます。</span><span class="sxs-lookup"><span data-stu-id="6b597-104">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="6b597-105">`My` 拡張が新しいプロジェクト タイプに不可欠な要素であるプロジェクト テンプレートを作成する場合、テンプレートをエクスポートするときに、カスタムの `My` 拡張コードをプロジェクトに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6b597-105">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="6b597-106">プロジェクト テンプレートのエクスポートの詳細については、「[方法: プロジェクト テンプレートを作成する](/visualstudio/ide/how-to-create-project-templates)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b597-106">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>

<span data-ttu-id="6b597-107">カスタムの `My` 拡張が単一のコード ファイルに含まれている場合、そのファイルを、ユーザーが任意の種類の Visual Basic プロジェクトに追加できる項目テンプレートとしてエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="6b597-107">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="6b597-108">その後、項目テンプレートをカスタマイズして、Visual Basic プロジェクト内のカスタムの `My` の追加機能や動作を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="6b597-108">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="6b597-109">これらの機能としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="6b597-109">Those capabilities include the following:</span></span>

- <span data-ttu-id="6b597-110">ユーザーが、Visual Basic プロジェクト デザイナーの **[My 拡張]** ページからカスタムの `My` 拡張を管理できるようにします。</span><span class="sxs-lookup"><span data-stu-id="6b597-110">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>

- <span data-ttu-id="6b597-111">指定されたアセンブリへの参照をプロジェクトに追加するときに、カスタムの `My` 拡張が自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="6b597-111">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>

- <span data-ttu-id="6b597-112">**[項目の追加]** ダイアログ ボックスで `My` 拡張の項目テンプレートを非表示にして、プロジェクト項目の一覧に含まれないようにします。</span><span class="sxs-lookup"><span data-stu-id="6b597-112">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>

<span data-ttu-id="6b597-113">このトピックでは、カスタムの `My` 拡張を非表示の項目テンプレートとしてパッケージ化し、Visual Basic プロジェクト デザイナーの **[My 拡張]** ページから管理できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6b597-113">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="6b597-114">指定されたアセンブリへの参照をプロジェクトに追加するときに、カスタムの `My` 拡張も自動的に追加できます。</span><span class="sxs-lookup"><span data-stu-id="6b597-114">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>

## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="6b597-115">My 名前空間拡張を作成する</span><span class="sxs-lookup"><span data-stu-id="6b597-115">Create a My namespace extension</span></span>

<span data-ttu-id="6b597-116">カスタムの `My` 拡張の展開パッケージを作成する場合、最初のステップとして、拡張を単一のコード ファイルとして作成します。</span><span class="sxs-lookup"><span data-stu-id="6b597-116">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="6b597-117">カスタムの `My` 拡張を作成する方法の詳細とガイダンスについては、「[Visual Basic における My 名前空間の拡張](extending-the-my-namespace.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b597-117">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](extending-the-my-namespace.md).</span></span>

## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="6b597-118">My 名前空間拡張を項目テンプレートとしてエクスポートする</span><span class="sxs-lookup"><span data-stu-id="6b597-118">Export a My namespace extension as an item template</span></span>

<span data-ttu-id="6b597-119">`My` 名前空間拡張を含むコード ファイルを作成した後、そのコード ファイルを Visual Studio 項目テンプレートとしてエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="6b597-119">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="6b597-120">ファイルを Visual Studio 項目テンプレートとしてエクスポートする手順については、「[方法: 項目テンプレートを作成する](/visualstudio/ide/how-to-create-item-templates)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b597-120">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>

> [!NOTE]
> <span data-ttu-id="6b597-121">`My` 名前空間拡張に、特定のアセンブリに対する依存関係がある場合、項目テンプレートをカスタマイズして、そのアセンブリへの参照が追加されるときに `My` 名前空間拡張が自動的にインストールされるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="6b597-121">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="6b597-122">そのため、コード ファイルを Visual Studio 項目テンプレートとしてエクスポートするときにそのアセンブリへの参照を除外する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b597-122">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>

## <a name="customize-the-item-template"></a><span data-ttu-id="6b597-123">項目テンプレートをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="6b597-123">Customize the item template</span></span>

<span data-ttu-id="6b597-124">項目テンプレートを Visual Basic プロジェクト デザイナーの **[My 拡張]** ページから管理できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="6b597-124">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="6b597-125">また、指定されたアセンブリへの参照をプロジェクトに追加するときに、項目テンプレートも自動的に追加されるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6b597-125">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="6b597-126">これらのカスタマイズを有効にするには、CustomData ファイルという名前の新しいファイルをテンプレートに追加し、.vstemplate ファイル内の XML に新しい要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="6b597-126">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>

### <a name="add-the-customdata-file"></a><span data-ttu-id="6b597-127">CustomData ファイルを追加する</span><span class="sxs-lookup"><span data-stu-id="6b597-127">Add the CustomData file</span></span>

<span data-ttu-id="6b597-128">CustomData ファイルは、ファイル名拡張子が .CustomData のテキスト ファイルで (ファイル名は、テンプレートにとって意味のある任意の値に設定できます)、XML が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6b597-128">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="6b597-129">CustomData ファイル内の XML は、ユーザーが Visual Basic プロジェクト デザイナーの **[My 拡張]** ページを使用するときに `My` 拡張を含めるように Visual Basic に指示します。</span><span class="sxs-lookup"><span data-stu-id="6b597-129">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="6b597-130">必要に応じて、<`AssemblyFullName>` 属性を CustomData ファイルの XML に追加できます。</span><span class="sxs-lookup"><span data-stu-id="6b597-130">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="6b597-131">これは、特定のアセンブリへの参照をプロジェクトに追加するときにカスタムの `My` 拡張を自動的にインストールするように Visual Basic に指示します。</span><span class="sxs-lookup"><span data-stu-id="6b597-131">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="6b597-132">任意のテキスト エディターまたは XML エディターを使用して CustomData ファイルを作成し、その後、ファイルを項目テンプレートの圧縮フォルダー (.zip ファイル) に追加できます。</span><span class="sxs-lookup"><span data-stu-id="6b597-132">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>

<span data-ttu-id="6b597-133">たとえば、次の XML は、Microsoft.VisualBasic.PowerPacks.Vs.dll アセンブリへの参照をプロジェクトに追加するときに、Visual Basic プロジェクトの [My 拡張] フォルダーにテンプレート項目を追加する CustomData ファイルの内容を示します。</span><span class="sxs-lookup"><span data-stu-id="6b597-133">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

<span data-ttu-id="6b597-134">この CustomData ファイルには、次の表に一覧表示する属性を持つ <`VBMyExtensionTemplate>` 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6b597-134">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>

|<span data-ttu-id="6b597-135">属性</span><span class="sxs-lookup"><span data-stu-id="6b597-135">Attribute</span></span>|<span data-ttu-id="6b597-136">説明</span><span class="sxs-lookup"><span data-stu-id="6b597-136">Description</span></span>|
|---|---|
|`ID`|<span data-ttu-id="6b597-137">必須です。</span><span class="sxs-lookup"><span data-stu-id="6b597-137">Required.</span></span> <span data-ttu-id="6b597-138">拡張の一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="6b597-138">A unique identifier for the extension.</span></span> <span data-ttu-id="6b597-139">この ID を持つ拡張がプロジェクトに既に追加されている場合、ユーザーに対して、再度追加するように要求されません。</span><span class="sxs-lookup"><span data-stu-id="6b597-139">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|
|`Version`|<span data-ttu-id="6b597-140">必須です。</span><span class="sxs-lookup"><span data-stu-id="6b597-140">Required.</span></span> <span data-ttu-id="6b597-141">項目テンプレートのバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="6b597-141">A version number for the item template.</span></span>|
|`AssemblyFullName`|<span data-ttu-id="6b597-142">任意。</span><span class="sxs-lookup"><span data-stu-id="6b597-142">Optional.</span></span> <span data-ttu-id="6b597-143">アセンブリ名。</span><span class="sxs-lookup"><span data-stu-id="6b597-143">An assembly name.</span></span> <span data-ttu-id="6b597-144">このアセンブリへの参照をプロジェクトに追加する場合、ユーザーに対して、この項目テンプレートから `My` 拡張を追加するように要求されます。</span><span class="sxs-lookup"><span data-stu-id="6b597-144">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="6b597-145">\<CustomDataSignature> 要素を .vstemplate ファイルに追加する</span><span class="sxs-lookup"><span data-stu-id="6b597-145">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>

<span data-ttu-id="6b597-146">Visual Studio 項目テンプレートを `My` 名前空間拡張として識別するには、項目テンプレートの .vstemplate ファイルも変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b597-146">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="6b597-147">`<CustomDataSignature>` 要素を `<TemplateData>` に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b597-147">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="6b597-148">次の例に示すように、`<CustomDataSignature>` 要素には、テキスト `Microsoft.VisualBasic.MyExtension` を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b597-148">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

<span data-ttu-id="6b597-149">圧縮フォルダー (.zip ファイル) 内のファイルを直接変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="6b597-149">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="6b597-150">圧縮フォルダーから .vstemplate ファイルをコピーし、それを変更して、圧縮フォルダー内の .vstemplate ファイルを、更新したコピーに置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b597-150">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>

<span data-ttu-id="6b597-151">次の例は、`<CustomDataSignature>` 要素が追加された .vstemplate ファイルの内容を示します。</span><span class="sxs-lookup"><span data-stu-id="6b597-151">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>

```xml
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
  <TemplateData>
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>
    <Name>MyPrinterInfo</Name>
    <Description>Custom My Extensions Item Template</Description>
    <ProjectType>VisualBasic</ProjectType>
    <SortOrder>10</SortOrder>
    <Icon>__TemplateIcon.ico</Icon>
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>
  </TemplateData>
  <TemplateContent>
    <References />
    <ProjectItem SubType="Code"
                 TargetFileName="$fileinputname$.vb"
                 ReplaceParameters="true"
     >MyCustomExtensionModule.vb</ProjectItem>
  </TemplateContent>
</VSTemplate>
```

## <a name="install-the-template"></a><span data-ttu-id="6b597-152">テンプレートのインストール</span><span class="sxs-lookup"><span data-stu-id="6b597-152">Install the template</span></span>

<span data-ttu-id="6b597-153">テンプレートをインストールするには、圧縮フォルダー ( *.zip* ファイル) を Visual Basic 項目テンプレート フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="6b597-153">To install the template, you can copy the compressed folder (*.zip* file) to the Visual Basic item templates folder.</span></span> <span data-ttu-id="6b597-154">既定では、ユーザー項目テンプレートは、 *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic* にあります。</span><span class="sxs-lookup"><span data-stu-id="6b597-154">By default, user item templates are located in *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic*.</span></span> <span data-ttu-id="6b597-155">または、テンプレートを Visual Studio インストーラー ( *.vsi*) ファイルとして発行することもできます。</span><span class="sxs-lookup"><span data-stu-id="6b597-155">Alternatively, you can publish the template as a Visual Studio Installer (*.vsi*) file.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b597-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b597-156">See also</span></span>

- [<span data-ttu-id="6b597-157">Visual Basic における My 名前空間の拡張</span><span class="sxs-lookup"><span data-stu-id="6b597-157">Extending the My Namespace in Visual Basic</span></span>](extending-the-my-namespace.md)
- [<span data-ttu-id="6b597-158">Visual Basic アプリケーション モデルの拡張</span><span class="sxs-lookup"><span data-stu-id="6b597-158">Extending the Visual Basic Application Model</span></span>](extending-the-visual-basic-application-model.md)
- [<span data-ttu-id="6b597-159">My で利用可能なオブジェクトのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="6b597-159">Customizing Which Objects are Available in My</span></span>](customizing-which-objects-are-available-in-my.md)
- <span data-ttu-id="6b597-160">[[マイ拡張] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="6b597-160">[My Extensions Page, Project Designer](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)</span></span>
