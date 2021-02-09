---
description: '詳細情報: My.Resources オブジェクト'
title: My.Resources オブジェクト
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: ecd8e79aacea85080dc341ae36b362a595893034
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640629"
---
# <a name="myresources-object"></a><span data-ttu-id="358c6-103">My.Resources オブジェクト</span><span class="sxs-lookup"><span data-stu-id="358c6-103">My.Resources Object</span></span>

<span data-ttu-id="358c6-104">アプリケーションのリソースにアクセスするためのプロパティとクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="358c6-104">Provides properties and classes for accessing the application's resources.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="358c6-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="358c6-105">Remarks</span></span>  

 <span data-ttu-id="358c6-106">`My.Resources` オブジェクトは、アプリケーションのリソースへのアクセスを提供し、アプリケーションのリソースを動的に取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="358c6-106">The `My.Resources` object provides access to the application's resources and lets you dynamically retrieve resources for your application.</span></span> <span data-ttu-id="358c6-107">詳細については、「[アプリケーション リソースの管理 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="358c6-107">For more information, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
 <span data-ttu-id="358c6-108">`My.Resources` オブジェクトは、グローバル リソースのみを公開します。</span><span class="sxs-lookup"><span data-stu-id="358c6-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="358c6-109">フォームに関連付けられたリソース ファイルへのアクセスは提供しません。</span><span class="sxs-lookup"><span data-stu-id="358c6-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="358c6-110">フォームのリソースには、フォームからアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="358c6-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="358c6-111">`My.Resources` オブジェクトから、アプリケーションのカルチャ固有のリソース ファイルにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="358c6-111">You can access the application's culture-specific resource files from the `My.Resources` object.</span></span> <span data-ttu-id="358c6-112">既定では、`My.Resources` オブジェクトは、<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> プロパティのカルチャに一致するリソース ファイルからリソースを検索します。</span><span class="sxs-lookup"><span data-stu-id="358c6-112">By default, the `My.Resources` object looks up resources from the resource file that matches the culture in the <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> property.</span></span> <span data-ttu-id="358c6-113">ただし、この動作をオーバーライドして、リソースに使用する特定のカルチャを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="358c6-113">However, you can override this behavior and specify a particular culture to use for the resources.</span></span> <span data-ttu-id="358c6-114">詳細については、「[デスクトップ アプリケーションのリソース](../../../framework/resources/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="358c6-114">For more information, see [Resources in Desktop Apps](../../../framework/resources/index.md).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="358c6-115">プロパティ</span><span class="sxs-lookup"><span data-stu-id="358c6-115">Properties</span></span>  

 <span data-ttu-id="358c6-116">`My.Resources` オブジェクトのプロパティは、アプリケーションのリソースへの読み取り専用アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="358c6-116">The properties of the `My.Resources` object provide read-only access to your application's resources.</span></span> <span data-ttu-id="358c6-117">リソースを追加または削除するには、**プロジェクト デザイナー** を使用します。</span><span class="sxs-lookup"><span data-stu-id="358c6-117">To add or remove resources, use the **Project Designer**.</span></span> <span data-ttu-id="358c6-118">`My.Resources.`*resourceName* を使用することで、**プロジェクト デザイナー** を使用して追加されたリソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="358c6-118">You can access resources added through the **Project Designer** by using `My.Resources.`*resourceName*.</span></span>  
  
 <span data-ttu-id="358c6-119">また、**ソリューション エクスプローラー** でプロジェクトを選択し、 **[プロジェクト]** メニューの **[新しい項目の追加]** または **[既存項目の追加]** をクリックして、リソース ファイルを追加または削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="358c6-119">You can also add or remove resource files by selecting your project in **Solution Explorer** and clicking **Add New Item** or **Add Existing Item** from the **Project** menu.</span></span> <span data-ttu-id="358c6-120">この方法で追加されたリソースには、`My.Resources.`*resourceFileName*`.`*resourceName* を使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="358c6-120">You can access resources added in this manner by using `My.Resources.`*resourceFileName*`.`*resourceName*.</span></span>  
  
 <span data-ttu-id="358c6-121">各リソースには名前、カテゴリ、および値が含まれ、これらのリソース設定によって、リソースにアクセスするためのプロパティが `My.Resources` オブジェクトにどのように表示されるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="358c6-121">Each resource has a name, category, and value, and these resource settings determine how the property to access the resource appears in the `My.Resources` object.</span></span> <span data-ttu-id="358c6-122">**プロジェクト デザイナー** で追加したリソースの場合:</span><span class="sxs-lookup"><span data-stu-id="358c6-122">For resources added in the **Project Designer**:</span></span>  
  
- <span data-ttu-id="358c6-123">名前はプロパティの名前を決定します。</span><span class="sxs-lookup"><span data-stu-id="358c6-123">The name determines the name of the property,</span></span>  
  
- <span data-ttu-id="358c6-124">リソース データはプロパティの値です。</span><span class="sxs-lookup"><span data-stu-id="358c6-124">The resource data is the value of the property,</span></span>  
  
- <span data-ttu-id="358c6-125">カテゴリはプロパティの型を決定します。</span><span class="sxs-lookup"><span data-stu-id="358c6-125">The category determines the type of the property:</span></span>  
  
|<span data-ttu-id="358c6-126">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="358c6-126">Category</span></span>|<span data-ttu-id="358c6-127">プロパティのデータ型</span><span class="sxs-lookup"><span data-stu-id="358c6-127">Property data type</span></span>|  
|---|---|  
|<span data-ttu-id="358c6-128">**文字列**</span><span class="sxs-lookup"><span data-stu-id="358c6-128">**Strings**</span></span>|[<span data-ttu-id="358c6-129">String</span><span class="sxs-lookup"><span data-stu-id="358c6-129">String</span></span>](../data-types/string-data-type.md)|  
|<span data-ttu-id="358c6-130">**イメージ**</span><span class="sxs-lookup"><span data-stu-id="358c6-130">**Images**</span></span>|<xref:System.Drawing.Bitmap>|  
|<span data-ttu-id="358c6-131">**アイコン**</span><span class="sxs-lookup"><span data-stu-id="358c6-131">**Icons**</span></span>|<xref:System.Drawing.Icon>|  
|<span data-ttu-id="358c6-132">**オーディオ**</span><span class="sxs-lookup"><span data-stu-id="358c6-132">**Audio**</span></span>|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <span data-ttu-id="358c6-133"><xref:System.IO.UnmanagedMemoryStream> クラスは <xref:System.IO.Stream> クラスから導出されるため、<xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> メソッドなどのストリームを受け取るメソッドで使用できます。</span><span class="sxs-lookup"><span data-stu-id="358c6-133">The <xref:System.IO.UnmanagedMemoryStream> class derives from the <xref:System.IO.Stream> class, so it can be used with methods that take streams, such as the <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> method.</span></span>|  
|<span data-ttu-id="358c6-134">**ファイル**</span><span class="sxs-lookup"><span data-stu-id="358c6-134">**Files**</span></span>|<span data-ttu-id="358c6-135">-   [String](../data-types/string-data-type.md) (テキスト ファイルの場合)。</span><span class="sxs-lookup"><span data-stu-id="358c6-135">-   [String](../data-types/string-data-type.md) for text files.</span></span><br /><span data-ttu-id="358c6-136">-   <xref:System.Drawing.Bitmap> (イメージ ファイルの場合)。</span><span class="sxs-lookup"><span data-stu-id="358c6-136">-   <xref:System.Drawing.Bitmap> for image files.</span></span><br /><span data-ttu-id="358c6-137">-   <xref:System.Drawing.Icon> (アイコン ファイルの場合)。</span><span class="sxs-lookup"><span data-stu-id="358c6-137">-   <xref:System.Drawing.Icon> for icon files.</span></span><br /><span data-ttu-id="358c6-138">-   <xref:System.IO.UnmanagedMemoryStream> (音声ファイルの場合)。</span><span class="sxs-lookup"><span data-stu-id="358c6-138">-   <xref:System.IO.UnmanagedMemoryStream> for sound files.</span></span>|  
|<span data-ttu-id="358c6-139">**その他**</span><span class="sxs-lookup"><span data-stu-id="358c6-139">**Other**</span></span>|<span data-ttu-id="358c6-140">デザイナーの **[型]** 列の情報によって決まります。</span><span class="sxs-lookup"><span data-stu-id="358c6-140">Determined by the information in the designer's **Type** column.</span></span>|  
  
## <a name="classes"></a><span data-ttu-id="358c6-141">クラス</span><span class="sxs-lookup"><span data-stu-id="358c6-141">Classes</span></span>  

 <span data-ttu-id="358c6-142">`My.Resources` オブジェクトは、各リソース ファイルを共有プロパティを持つクラスとして公開します。</span><span class="sxs-lookup"><span data-stu-id="358c6-142">The `My.Resources` object exposes each resource file as a class with shared properties.</span></span> <span data-ttu-id="358c6-143">クラス名は、リソース ファイルの名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="358c6-143">The class name is the same as the name of the resource file.</span></span> <span data-ttu-id="358c6-144">前のセクションで説明したように、リソース ファイル内のリソースはクラスのプロパティとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="358c6-144">As described in the previous section, the resources in a resource file are exposed as properties in the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="358c6-145">例</span><span class="sxs-lookup"><span data-stu-id="358c6-145">Example</span></span>  

 <span data-ttu-id="358c6-146">この例では、フォームのタイトルを、アプリケーション リソース ファイル内の `Form1Title` という名前の文字列リソースに設定します。</span><span class="sxs-lookup"><span data-stu-id="358c6-146">This example sets the title of a form to the string resource named `Form1Title` in the application resource file.</span></span> <span data-ttu-id="358c6-147">この例を機能させるには、アプリケーションのリソース ファイルに `Form1Title` という名前の文字列が必要です。</span><span class="sxs-lookup"><span data-stu-id="358c6-147">For the example to work, the application must have a string named `Form1Title` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="358c6-148">例</span><span class="sxs-lookup"><span data-stu-id="358c6-148">Example</span></span>  

 <span data-ttu-id="358c6-149">この例では、フォームのアイコンを、アプリケーションのリソース ファイルに格納されている `Form1Icon` という名前のアイコンに設定します。</span><span class="sxs-lookup"><span data-stu-id="358c6-149">This example sets the icon of the form to the icon named `Form1Icon` that is stored in the application's resource file.</span></span> <span data-ttu-id="358c6-150">この例を機能させるには、アプリケーションのリソース ファイルに `Form1Icon` という名前のアイコンが必要です。</span><span class="sxs-lookup"><span data-stu-id="358c6-150">For the example to work, the application must have an icon named `Form1Icon` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="358c6-151">例</span><span class="sxs-lookup"><span data-stu-id="358c6-151">Example</span></span>  

 <span data-ttu-id="358c6-152">この例では、フォームの背景イメージを、アプリケーション リソース ファイル内にある `Form1Background` という名前のイメージ リソースに設定します。</span><span class="sxs-lookup"><span data-stu-id="358c6-152">This example sets the background image of a form to the image resource named `Form1Background`, which is in the application resource file.</span></span> <span data-ttu-id="358c6-153">この例を機能させるには、アプリケーションのリソース ファイルに `Form1Background` という名前のイメージ リソースが必要です。</span><span class="sxs-lookup"><span data-stu-id="358c6-153">For this example to work, the application must have an image resource named `Form1Background` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="358c6-154">例</span><span class="sxs-lookup"><span data-stu-id="358c6-154">Example</span></span>  

 <span data-ttu-id="358c6-155">この例では、アプリケーションのリソースファイルに `Form1Greeting` という名前のオーディオ リソースとして格納されているサウンドを再生します。</span><span class="sxs-lookup"><span data-stu-id="358c6-155">This example plays the sound that is stored as an audio resource named `Form1Greeting` in the application's resource file.</span></span> <span data-ttu-id="358c6-156">この例を機能させるには、アプリケーションのリソース ファイルに `Form1Greeting` という名前のオーディオ リソースが必要です。</span><span class="sxs-lookup"><span data-stu-id="358c6-156">For the example to work, the application must have an audio resource named `Form1Greeting` in its resource file.</span></span> <span data-ttu-id="358c6-157">`My.Computer.Audio.Play` は、Windows フォーム アプリケーションでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="358c6-157">The `My.Computer.Audio.Play` method is available only for Windows Forms applications.</span></span>  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="358c6-158">例</span><span class="sxs-lookup"><span data-stu-id="358c6-158">Example</span></span>  

 <span data-ttu-id="358c6-159">この例では、フランス語のカルチャ バージョンのアプリケーションの文字列リソースを取得します。</span><span class="sxs-lookup"><span data-stu-id="358c6-159">This example retrieves the French-culture version of a  string resource of the application.</span></span> <span data-ttu-id="358c6-160">リソースには `Message` という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="358c6-160">The resource is named `Message`.</span></span> <span data-ttu-id="358c6-161">`My.Resources` オブジェクトが使用するカルチャを変更するために、この例では <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A> を使用しています。</span><span class="sxs-lookup"><span data-stu-id="358c6-161">To change the culture that the `My.Resources` object uses, the example uses <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</span></span>  
  
 <span data-ttu-id="358c6-162">この例を機能させるには、アプリケーションのリソース ファイルに `Message` という名前の文字列が必要であり、アプリケーションには、そのリソース ファイルのフランス語のカルチャ バージョン、Resources.fr-FR.resx が必要です。</span><span class="sxs-lookup"><span data-stu-id="358c6-162">For this example to work, the application must have a string named `Message` in its resource file, and the application should have the French-culture version of that resource file, Resources.fr-FR.resx.</span></span> <span data-ttu-id="358c6-163">アプリケーションにフランス語のカルチャ バージョンのリソース ファイルがない場合、`My.Resource` オブジェクトは、既定のカルチャ リソース ファイルからリソースを取得します。</span><span class="sxs-lookup"><span data-stu-id="358c6-163">If the application does not have the French-culture version of the resource file, the `My.Resource` object retrieves the resource from the default-culture resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="358c6-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="358c6-164">See also</span></span>

- [<span data-ttu-id="358c6-165">アプリケーション リソースの管理 (.NET)</span><span class="sxs-lookup"><span data-stu-id="358c6-165">Managing Application Resources (.NET)</span></span>](/visualstudio/ide/managing-application-resources-dotnet)
- [<span data-ttu-id="358c6-166">デスクトップ アプリケーションのリソース</span><span class="sxs-lookup"><span data-stu-id="358c6-166">Resources in Desktop Apps</span></span>](../../../framework/resources/index.md)
