---
title: 'チュートリアル: Model Builder で画像内のオブジェクトを検出する'
description: このチュートリアルでは、ML.NET Model Builder と Azure ML を使用して、物体検出モデルを構築し、画像内の一時停止標識を検出する方法について説明します。
author: briacht
ms.author: brachtma
ms.date: 03/12/2021
ms.topic: tutorial
ms.custom: mlnet-tooling
ms.openlocfilehash: 21b672b84c7f55578a76459fa9f02aca3455d719
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104658386"
---
# <a name="tutorial-detect-stop-signs-in-images-with-model-builder"></a><span data-ttu-id="85e0d-103">チュートリアル: Model Builder で画像内の一時停止標識を検出する</span><span class="sxs-lookup"><span data-stu-id="85e0d-103">Tutorial: Detect stop signs in images with Model Builder</span></span>

<span data-ttu-id="85e0d-104">ML.NET Model Builder と Azure ML を使用して、物体検出モデルを構築し、画像内の一時停止標識を検出して見つける方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-104">Learn how to build an object detection model using ML.NET Model Builder and Azure ML to detect and locate stop signs in images.</span></span>

<span data-ttu-id="85e0d-105">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="85e0d-106">データを準備して理解する</span><span class="sxs-lookup"><span data-stu-id="85e0d-106">Prepare and understand the data</span></span>
> - <span data-ttu-id="85e0d-107">シナリオを選択する</span><span class="sxs-lookup"><span data-stu-id="85e0d-107">Choose the scenario</span></span>
> - <span data-ttu-id="85e0d-108">トレーニング環境を選択する</span><span class="sxs-lookup"><span data-stu-id="85e0d-108">Choose the training environment</span></span>
> - <span data-ttu-id="85e0d-109">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="85e0d-109">Load the data</span></span>
> - <span data-ttu-id="85e0d-110">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="85e0d-110">Train the model</span></span>
> - <span data-ttu-id="85e0d-111">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="85e0d-111">Evaluate the model</span></span>
> - <span data-ttu-id="85e0d-112">モデルを使用して予測を行う</span><span class="sxs-lookup"><span data-stu-id="85e0d-112">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="85e0d-113">モデル ビルダーは現在のところ、プレビュー段階です。</span><span class="sxs-lookup"><span data-stu-id="85e0d-113">Model Builder is currently in Preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="85e0d-114">前提条件</span><span class="sxs-lookup"><span data-stu-id="85e0d-114">Prerequisites</span></span>

<span data-ttu-id="85e0d-115">前提条件の一覧とインストール手順は、[モデル ビルダーのインストール ガイド](../how-to-guides/install-model-builder.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85e0d-115">For a list of prerequisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="model-builder-object-detection-overview"></a><span data-ttu-id="85e0d-116">Model Builder の物体検出の概要</span><span class="sxs-lookup"><span data-stu-id="85e0d-116">Model Builder object detection overview</span></span>

<span data-ttu-id="85e0d-117">オブジェクト検出はコンピューターのビジョンの問題です。</span><span class="sxs-lookup"><span data-stu-id="85e0d-117">Object detection is a computer vision problem.</span></span> <span data-ttu-id="85e0d-118">画像の分類に密接に関連していますが、オブジェクト検出では、より詳細なスケールで画像分類が実行されます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-118">While closely related to image classification, object detection performs image classification at a more granular scale.</span></span> <span data-ttu-id="85e0d-119">オブジェクト検出では、画像内のエンティティの特定 "_と_" 分類の両方が行われます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-119">Object detection both locates _and_ categorizes entities within images.</span></span> <span data-ttu-id="85e0d-120">オブジェクト検出は、画像に異なる種類のオブジェクトが複数含まれる場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-120">Use object detection when images contain multiple objects of different types.</span></span>

![画像の分類とオブジェクトの分類を示すスクリーンショット。](./media/object-detection-onnx/img-classification-obj-detection.PNG)

<span data-ttu-id="85e0d-122">オブジェクト検出のユース ケースには、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="85e0d-122">Some use cases for object detection include:</span></span>

- <span data-ttu-id="85e0d-123">自動運転車</span><span class="sxs-lookup"><span data-stu-id="85e0d-123">Self-Driving Cars</span></span>
- <span data-ttu-id="85e0d-124">ロボティクス</span><span class="sxs-lookup"><span data-stu-id="85e0d-124">Robotics</span></span>
- <span data-ttu-id="85e0d-125">顔検出</span><span class="sxs-lookup"><span data-stu-id="85e0d-125">Face Detection</span></span>
- <span data-ttu-id="85e0d-126">職場の安全</span><span class="sxs-lookup"><span data-stu-id="85e0d-126">Workplace Safety</span></span>
- <span data-ttu-id="85e0d-127">オブジェクトのカウント</span><span class="sxs-lookup"><span data-stu-id="85e0d-127">Object Counting</span></span>
- <span data-ttu-id="85e0d-128">アクティビティ認識</span><span class="sxs-lookup"><span data-stu-id="85e0d-128">Activity Recognition</span></span>

<span data-ttu-id="85e0d-129">このサンプルでは、Model Builder で構築された機械学習モデルを使用して、画像内の一時停止標識を検出する C# .NET Core コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-129">This sample creates a C# .NET Core console application that detects stop signs in images using a machine learning model built with Model Builder.</span></span> <span data-ttu-id="85e0d-130">このチュートリアルのソース コードは、[dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/ObjectDetection_StopSigns) GitHub リポジトリにあります。</span><span class="sxs-lookup"><span data-stu-id="85e0d-130">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/ObjectDetection_StopSigns) GitHub repository.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="85e0d-131">データを準備して理解する</span><span class="sxs-lookup"><span data-stu-id="85e0d-131">Prepare and understand the data</span></span>

<span data-ttu-id="85e0d-132">一時停止標識データセットは、[Unsplash](https://unsplash.com/) からダウンロードされ、それぞれに少なくとも 1 つの一時停止標識が含まれている 50 個の画像で構成されています。</span><span class="sxs-lookup"><span data-stu-id="85e0d-132">The Stop Sign dataset consists of 50 images downloaded from [Unsplash](https://unsplash.com/), each of which contain at least one stop sign.</span></span>

<span data-ttu-id="85e0d-133">最初に実行する必要があることは、画像に注釈を付けるか、各画像の一時停止標識の周囲に境界ボックスを描画することです。</span><span class="sxs-lookup"><span data-stu-id="85e0d-133">The first thing you need to do is annotate your images, or draw bounding boxes around the stop signs in each image.</span></span> <span data-ttu-id="85e0d-134">このチュートリアルでは、[VoTT](https://github.com/microsoft/VoTT) というツールで画像に注釈を付けます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-134">In this tutorial, you will annotate your images with a tool called [VoTT](https://github.com/microsoft/VoTT).</span></span>

> <span data-ttu-id="85e0d-135">以下のデータのラベル付けの手順をスキップする場合は、[このデータセットのバージョンをダウンロード](https://aka.ms/mlnet-object-detection-tutorial-assets)して、「[コンソール アプリケーションを作成する](object-detection-model-builder.md#create-a-console-application)」に進みます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-135">If you want to skip the data labeling steps below, you can [download this version of the dataset](https://aka.ms/mlnet-object-detection-tutorial-assets) and skip to [Create a console application](object-detection-model-builder.md#create-a-console-application).</span></span>

### <a name="create-a-new-vott-project"></a><span data-ttu-id="85e0d-136">新しい VoTT プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="85e0d-136">Create a new VoTT project</span></span>

1. <span data-ttu-id="85e0d-137">50 個の一時停止標識画像の[データセットをダウンロード](https://aka.ms/mlnet-object-detection-tutorial-dataset)して、解凍します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-137">[Download the dataset](https://aka.ms/mlnet-object-detection-tutorial-dataset) of 50 stop sign images and unzip.</span></span>
1. <span data-ttu-id="85e0d-138">[VoTT (Visual Object Tagging Tool) をダウンロード](https://github.com/Microsoft/VoTT/releases)します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-138">[Download VoTT](https://github.com/Microsoft/VoTT/releases) (Visual Object Tagging Tool).</span></span>
1. <span data-ttu-id="85e0d-139">VoTT を開いて、 **[新しいプロジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-139">Open VoTT and select **New Project**.</span></span>

    ![VoTT ホーム画面](./media/object-detection-model-builder/vott.png)

1. <span data-ttu-id="85e0d-141">**[プロジェクトの設定]** で、 **[表示名]** を "StopSignObjDetection" に変更します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-141">In **Project Settings**, change the **Display Name** to "StopSignObjDetection".</span></span>
1. <span data-ttu-id="85e0d-142">**[セキュリティ トークン]** を *[新しいセキュリティ トークンの生成]* に変更します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-142">Change the **Security Token** to *Generate New Security Token*.</span></span>
1. <span data-ttu-id="85e0d-143">**[ソース接続]** の横にある **[接続の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-143">Next to **Source Connection**, select **Add Connection**.</span></span>
1. <span data-ttu-id="85e0d-144">**[接続の設定]** で、ソース接続の **[表示名]** を "StopSignImages" に変更し、 *[ローカル ファイル システム]* を **[プロバイダー]** として選択します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-144">In **Connection Settings**, change the **Display Name** for the source connection to "StopSignImages", and select *Local File System* as the **Provider**.</span></span> <span data-ttu-id="85e0d-145">**[フォルダー パス]** で、50 個のトレーニング画像を格納する *Stop-Signs* フォルダーを選択し、 **[接続の保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-145">For the **Folder Path**, select the *Stop-Signs* folder which contains the 50 training images, and then select **Save Connection**.</span></span>

    ![VoTT の [新しい接続] ダイアログ](./media/object-detection-model-builder/vott-new-connection.png)

1. <span data-ttu-id="85e0d-147">**[プロジェクトの設定]** で、 **[ソース接続]** を *[StopSignImages]* (先ほど作成した接続) に変更します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-147">In **Project Settings**, change the **Source Connection** to *StopSignImages* (the connection you just created).</span></span>
1. <span data-ttu-id="85e0d-148">**[ターゲット接続]** も *[StopSignImages]* に変更します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-148">Change the **Target Connection** to *StopSignImages* as well.</span></span> <span data-ttu-id="85e0d-149">**[プロジェクトの設定]** は、次のスクリーンショットのようになっているはずです。</span><span class="sxs-lookup"><span data-stu-id="85e0d-149">Your **Project Settings** should now look similar to this screenshot:</span></span>

    ![VoTT の [プロジェクトの設定] ダイアログ](./media/object-detection-model-builder/vott-new-project.png)

1. <span data-ttu-id="85e0d-151">**[プロジェクトの保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-151">Select **Save Project**.</span></span>

### <a name="add-tag-and-label-images"></a><span data-ttu-id="85e0d-152">タグとラベルの画像を追加する</span><span class="sxs-lookup"><span data-stu-id="85e0d-152">Add tag and label images</span></span>

<span data-ttu-id="85e0d-153">これで、左側にすべてのトレーニング画像のプレビュー画像、中央に選択した画像のプレビュー、右側に **[タグ]** 列があるウィンドウが表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="85e0d-153">You should now see a window with preview images of all the training images on the left, a preview of the selected image in the middle, and a **Tags** column on the right.</span></span> <span data-ttu-id="85e0d-154">この画面は、**タグ エディター** です。</span><span class="sxs-lookup"><span data-stu-id="85e0d-154">This screen is the **Tags editor**.</span></span>

1. <span data-ttu-id="85e0d-155">新しいタグを追加するには、 **[タグ]** ツールバーの最初 (プラス形) のアイコンを選択します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-155">Select the first (plus-shaped) icon in the **Tags** toolbar to add a new tag.</span></span>

    ![VoTT の [新しいタグ] アイコン](./media/object-detection-model-builder/vott-new-tag-icon.png)

1. <span data-ttu-id="85e0d-157">タグに "Stop-Sign" という名前を付け、キーボードの <kbd>Enter</kbd> を押します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-157">Name the tag "Stop-Sign" and hit <kbd>Enter</kbd> on your keyboard.</span></span>

    ![VoTT の [新しいタグ]](./media/object-detection-model-builder/vott-new-tag.png)

1. <span data-ttu-id="85e0d-159">クリックしてドラッグし、画像内の各一時停止標識の周囲に四角形を描画します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-159">Click and drag to draw a rectangle around each stop sign in the image.</span></span> <span data-ttu-id="85e0d-160">カーソルで四角形を描画できない場合は、上部のツールバーから **[四角形の描画]** ツールを選択するか、キーボード ショートカット <kbd>R</kbd> を使用してください。</span><span class="sxs-lookup"><span data-stu-id="85e0d-160">If the cursor does not let you draw a rectangle, try selecting the **Draw Rectangle** tool from the toolbar on the top, or use the keyboard shortcut <kbd>R</kbd>.</span></span>
1. <span data-ttu-id="85e0d-161">四角形の描画後、前の手順で作成した **[Stop-Sign]** タグを選択して、境界ボックスにタグを追加します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-161">After drawing your rectangle, select the **Stop-Sign** tag that you created in the previous steps to add the tag to the bounding box.</span></span>
1. <span data-ttu-id="85e0d-162">データセット内の次の画像のプレビュー画像をクリックし、このプロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-162">Click on the preview image for the next image in the dataset and repeat this process.</span></span>
1. <span data-ttu-id="85e0d-163">すべての画像のすべての一時停止標識に対して、手順 3 から 4 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-163">Continue steps 3-4 for every stop sign in every image.</span></span>

    ![VoTT の画像の注釈付け](./media/object-detection-model-builder/vott-annotating.gif)

### <a name="export-your-vott-json"></a><span data-ttu-id="85e0d-165">VoTT JSON をエクスポートする</span><span class="sxs-lookup"><span data-stu-id="85e0d-165">Export your VoTT JSON</span></span>

<span data-ttu-id="85e0d-166">すべてのトレーニング画像をラベル付けしたら、Model Builder でトレーニングに使用されるファイルをエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-166">Once you have labeled all of your training images, you can export the file that will be used by Model Builder for training.</span></span>

1. <span data-ttu-id="85e0d-167">左側のツールバーの 4 番目のアイコン (ボックスに斜めの矢印があるもの) を選択し、 **[エクスポート設定]** に移動します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-167">Select the fourth icon in the left toolbar (the one with the diagonal arrow in a box) to go to the **Export Settings**.</span></span>
1. <span data-ttu-id="85e0d-168">**[プロバイダー]** は *[VoTT JSON]* のままにします。</span><span class="sxs-lookup"><span data-stu-id="85e0d-168">Leave the **Provider** as *VoTT JSON*.</span></span>
1. <span data-ttu-id="85e0d-169">**[アセットの状態]** を、 *[タグ付きアセットのみ]* に変更します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-169">Change the **Asset State** to *Only tagged Assets*.</span></span>
1. <span data-ttu-id="85e0d-170">**[画像を含める]** をオフにします。</span><span class="sxs-lookup"><span data-stu-id="85e0d-170">Uncheck **Include Images**.</span></span> <span data-ttu-id="85e0d-171">画像を含める場合は、生成されるエクスポート フォルダーにトレーニング画像がコピーされますが、これは必要ではありません。</span><span class="sxs-lookup"><span data-stu-id="85e0d-171">If you include the images, then the training images will be copied to the export folder that is generated, which is not necessary.</span></span>
1. <span data-ttu-id="85e0d-172">**[エクスポート設定の保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-172">Select **Save Export Settings**.</span></span>

    ![VoTT の [エクスポート設定]](./media/object-detection-model-builder/vott-export.png)

1. <span data-ttu-id="85e0d-174">**タグ エディター** (リボンのような形をした、左側のツールバーの 2 番目のアイコン) に戻ります。</span><span class="sxs-lookup"><span data-stu-id="85e0d-174">Go back to the **Tags editor** (the second icon in the left toolbar shaped like a ribbon).</span></span> <span data-ttu-id="85e0d-175">上部のツールバーで、 **[プロジェクトのエクスポート]** アイコン (ボックス内の矢印のような形をした最後のアイコン) を選択するか、キーボード ショートカットの <kbd>Ctrl</kbd>+<kbd>E</kbd> を使用します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-175">In the top toolbar, select the **Export Project** icon (the last icon shaped like an arrow in a box), or use the keyboard shortcut <kbd>Ctrl</kbd>+<kbd>E</kbd>.</span></span>

    ![VoTT の [エクスポート] ボタン](./media/object-detection-model-builder/vott-export-button.png)

<span data-ttu-id="85e0d-177">このエクスポートによって、*Stop-Sign-Images* フォルダーに *vott-json-export* という新しいフォルダーが作成され、その新しいフォルダーに *StopSignObjDetection-export* という名前の JSON ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-177">This export will create a new folder called *vott-json-export* in your *Stop-Sign-Images* folder and will generate a JSON file named *StopSignObjDetection-export* in that new folder.</span></span> <span data-ttu-id="85e0d-178">この JSON ファイルは、次の手順で、Model Builder で物体検出モデルをトレーニングするために使用します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-178">You will use this JSON file in the next steps for training an object detection model in Model Builder.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="85e0d-179">コンソール アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="85e0d-179">Create a console application</span></span>

1. <span data-ttu-id="85e0d-180">Visual Studio で、*StopSignDetection* という **C# .NET Core コンソール アプリケーション** を作成します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-180">In Visual Studio, create a **C# .NET Core console application** called *StopSignDetection*.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="85e0d-181">シナリオを選択する</span><span class="sxs-lookup"><span data-stu-id="85e0d-181">Choose a scenario</span></span>

1. <span data-ttu-id="85e0d-182">**ソリューション エクスプローラー** で、*StopSignDetection* プロジェクトを右クリックし、 **[追加]**  >  **[機械学習]** を選択し、Model Builder UI を開きます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-182">In **Solution Explorer**, right-click the *StopSignDetection* project, and select **Add** > **Machine Learning** to open the Model Builder UI.</span></span>
1. <span data-ttu-id="85e0d-183">このサンプルの場合、シナリオは物体検出です。</span><span class="sxs-lookup"><span data-stu-id="85e0d-183">For this sample, the scenario is object detection.</span></span> <span data-ttu-id="85e0d-184">Model Builder の **[シナリオ]** 手順で、 **[物体検出]** シナリオを選択します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-184">In the **Scenario** step of Model Builder, select the **Object Detection** scenario.</span></span>

![Visual Studio のモデル ビルダー ウィザード](./media/object-detection-model-builder/obj-det-scenario.png)

> <span data-ttu-id="85e0d-186">シナリオの一覧に *[物体検出]* が表示されない場合は、[Model Builder のバージョンの更新](https://marketplace.visualstudio.com/items?itemName=MLNET.07)が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="85e0d-186">If you don't see *Object Detection* in the list of scenarios, you may need to [update your version of Model Builder](https://marketplace.visualstudio.com/items?itemName=MLNET.07).</span></span>

## <a name="choose-the-training-environment"></a><span data-ttu-id="85e0d-187">トレーニング環境を選択する</span><span class="sxs-lookup"><span data-stu-id="85e0d-187">Choose the training environment</span></span>

<span data-ttu-id="85e0d-188">現時点で、Model Builder では Azure Machine Learning による物体検出モデルのトレーニングのみがサポートされているため、既定で Azure トレーニング環境が選択されています。</span><span class="sxs-lookup"><span data-stu-id="85e0d-188">Currently, Model Builder supports training object detection models with Azure Machine Learning only, so the Azure training environment is selected by default.</span></span>

![Azure トレーニング環境の選択](./media/object-detection-model-builder/obj-det-environment.png)

<span data-ttu-id="85e0d-190">Azure ML を使用してモデルをトレーニングするには、Model Builder から Azure ML 実験を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85e0d-190">To train a model using Azure ML, you must create an Azure ML experiment from Model Builder.</span></span>

<span data-ttu-id="85e0d-191">**Azure ML 実験** は、1 回以上の機械学習トレーニングの実行の構成と結果をカプセル化するリソースです。</span><span class="sxs-lookup"><span data-stu-id="85e0d-191">An **Azure ML experiment** is a resource that encapsulates the configuration and results for one or more machine learning training runs.</span></span>

<span data-ttu-id="85e0d-192">Azure ML 実験を作成するには、まず Azure で環境を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85e0d-192">To create an Azure ML experiment, you first need to configure your environment in Azure.</span></span> <span data-ttu-id="85e0d-193">実験を実行するには、次のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="85e0d-193">An experiment needs the following to run:</span></span>

- <span data-ttu-id="85e0d-194">Azure サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="85e0d-194">An Azure subscription</span></span>
- <span data-ttu-id="85e0d-195">**ワークスペース**: トレーニング実行の一部として作成される Azure ML のすべてのリソースと成果物の一元的な場所を提供する Azure ML リソースです。</span><span class="sxs-lookup"><span data-stu-id="85e0d-195">A **workspace**: an Azure ML resource that provides a central place for all Azure ML resources and artifacts created as part of a training run.</span></span>
- <span data-ttu-id="85e0d-196">**コンピューティング**: Azure Machine Learning コンピューティングとは、トレーニングに使用するクラウドベースの Linux VM です。</span><span class="sxs-lookup"><span data-stu-id="85e0d-196">A **compute**: an Azure Machine Learning compute is a cloud-based Linux VM used for training.</span></span> <span data-ttu-id="85e0d-197">[Model Builder でサポートされているコンピューティングの種類](../resources/azure-training-concepts-model-builder.md#what-is-an-azure-machine-learning-compute)の詳細を確認してください。</span><span class="sxs-lookup"><span data-stu-id="85e0d-197">Learn more about [compute types supported by Model Builder](../resources/azure-training-concepts-model-builder.md#what-is-an-azure-machine-learning-compute).</span></span>

### <a name="set-up-an-azure-ml-workspace"></a><span data-ttu-id="85e0d-198">Azure ML ワークスペースを設定する</span><span class="sxs-lookup"><span data-stu-id="85e0d-198">Set up an Azure ML workspace</span></span>

<span data-ttu-id="85e0d-199">環境を構成するには:</span><span class="sxs-lookup"><span data-stu-id="85e0d-199">To configure your environment:</span></span>

1. <span data-ttu-id="85e0d-200">**[ワークスペースの設定]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-200">Select the **Set up workspace** button.</span></span>
1. <span data-ttu-id="85e0d-201">**[新しい実験の作成]** ダイアログで、Azure サブスクリプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-201">In the **Create new experiment** dialog, select your Azure subscription.</span></span>
1. <span data-ttu-id="85e0d-202">既存のワークスペースを選択するか、新しい Azure ML ワークスペースを作成します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-202">Select an existing workspace or create a new Azure ML workspace.</span></span>

    <span data-ttu-id="85e0d-203">新しいワークスペースを作成する場合、次のリソースがプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-203">When you create a new workspace, the following resources are provisioned:</span></span>

    - <span data-ttu-id="85e0d-204">Azure Machine Learning ワークスペース</span><span class="sxs-lookup"><span data-stu-id="85e0d-204">Azure Machine Learning workspace</span></span>
    - <span data-ttu-id="85e0d-205">Azure Storage</span><span class="sxs-lookup"><span data-stu-id="85e0d-205">Azure Storage</span></span>
    - <span data-ttu-id="85e0d-206">Azure Application Insights</span><span class="sxs-lookup"><span data-stu-id="85e0d-206">Azure Application Insights</span></span>
    - <span data-ttu-id="85e0d-207">Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="85e0d-207">Azure Container Registry</span></span>
    - <span data-ttu-id="85e0d-208">Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="85e0d-208">Azure Key Vault</span></span>

    <span data-ttu-id="85e0d-209">そのため、このプロセスには数分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="85e0d-209">As a result, this process may take a few minutes.</span></span>

1. <span data-ttu-id="85e0d-210">既存のコンピューティングを選択するか、新しい Azure ML コンピューティングを作成します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-210">Select an existing compute or create a new Azure ML compute.</span></span> <span data-ttu-id="85e0d-211">このプロセスは数分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="85e0d-211">This process may take a few minutes.</span></span>
1. <span data-ttu-id="85e0d-212">既定の実験名のままにして、 **[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-212">Leave the default experiment name and select **Create**.</span></span>

    ![Azure ワークスペース セットアップ ダイアログ](./media/object-detection-model-builder/azure-dialog.png)

<span data-ttu-id="85e0d-214">最初の実験が作成され、実験名がワークスペースに登録されます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-214">The first experiment is created, and the experiment name is registered in the workspace.</span></span> <span data-ttu-id="85e0d-215">それ以降の実行は (同じ実験名を使用した場合)、同じ実験の一部としてログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-215">Any subsequent runs (if the same experiment name is used ) are logged as part of the same experiment.</span></span> <span data-ttu-id="85e0d-216">そうでない場合は、新しい実験が作成されます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-216">Otherwise, a new experiment is created.</span></span>

<span data-ttu-id="85e0d-217">構成に満足したら、Model Builder の **[次のステップ]** ボタンを選択して、 **[データ]** ステップに移動します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-217">If you’re satisfied with your configuration, select the **Next step** button in Model Builder to move to the **Data** step.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="85e0d-218">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="85e0d-218">Load the data</span></span>

<span data-ttu-id="85e0d-219">Model Builder の **[データ]** ステップで、トレーニング データセットを選択します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-219">In the **Data** step of Model Builder, you will select your training dataset.</span></span>

><span data-ttu-id="85e0d-220">現在、Model Builder では、VoTT によって生成される JSON の形式のみが受け入れられますが、チームでは今後、サポートする形式を増やしていく予定です。</span><span class="sxs-lookup"><span data-stu-id="85e0d-220">Model Builder currently only accepts the format of JSON generated by VoTT, but the team plans to add support for more formats in the future.</span></span> <span data-ttu-id="85e0d-221">Model Builder でサポートされることを期待する物体検出用のデータセット形式がある場合は、[GitHub](https://github.com/dotnet/machinelearning-modelbuilder/issues/new?assignees=&labels=&template=data_suggestion.md&title=) でフィードバックをお寄せください。</span><span class="sxs-lookup"><span data-stu-id="85e0d-221">If there is a dataset format for object detection that you’d like to see supported in Model Builder, leave your feedback on [GitHub](https://github.com/dotnet/machinelearning-modelbuilder/issues/new?assignees=&labels=&template=data_suggestion.md&title=).</span></span>

1. <span data-ttu-id="85e0d-222">**[フォルダーの選択]** テキスト ボックスの横にあるボタンを選択し、エクスプローラーを使用して、*Stop-Signs/vott-json-export* ディレクトリにある `StopSignObjDetection-export.json` を見つけます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-222">Select the button next to the **Select a folder** text box and use the File Explorer to find the `StopSignObjDetection-export.json` which should be located in the *Stop-Signs/vott-json-export* directory.</span></span>

    ![Model Builder のデータ ステップ](./media/object-detection-model-builder/obj-det-data.png)

1. <span data-ttu-id="85e0d-224">**データ プレビュー** でデータが正しく表示されている場合は、 **[次のステップ]** を選択して、 **[トレーニング]** ステップに進みます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-224">If your data looks correct in the **Data Preview**, select **Next step** to move on to the **Train** step.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="85e0d-225">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="85e0d-225">Train the model</span></span>

<span data-ttu-id="85e0d-226">次のステップは、モデルをトレーニングすることです。</span><span class="sxs-lookup"><span data-stu-id="85e0d-226">The next step is to train your model.</span></span>

<span data-ttu-id="85e0d-227">Model Builder の **[トレーニング]** 画面で、 **[トレーニングの開始]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-227">In the Model Builder **Train** screen, select the **Start training** button.</span></span>

<span data-ttu-id="85e0d-228">この時点で、データは Azure Storage にアップロードされ、Azure ML でトレーニング プロセスが開始されます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-228">At this point, your data is uploaded to Azure Storage and the training process begins in Azure ML.</span></span>

><span data-ttu-id="85e0d-229">トレーニング プロセスには時間がかかり、この時間は選択したコンピューティングのサイズやデータ量によって変わります。</span><span class="sxs-lookup"><span data-stu-id="85e0d-229">The training process takes some time, and the amount of time may vary depending on the size of compute selected as well as the amount of data.</span></span> <span data-ttu-id="85e0d-230">Azure でのモデルの初回トレーニング時は、リソースをプロビジョニングする必要があるため、トレーニング時間が若干長くなることが予想されます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-230">The first time a model is trained in Azure, you can expect a slightly longer training time because resources have to be provisioned.</span></span> <span data-ttu-id="85e0d-231">この 50 個の画像のサンプルでは、トレーニングに約 16 分かかりました。</span><span class="sxs-lookup"><span data-stu-id="85e0d-231">For this sample of 50 images, training took about 16 minutes.</span></span>

<span data-ttu-id="85e0d-232">Visual Studio で **[Azure portal で現在の実行を監視する]** リンクを選択すると、Azure Machine Learning ポータルで実行の進行状況を追跡できます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-232">You can track the progress of your runs in the Azure Machine Learning portal by selecting the **Monitor current run in Azure portal** link in Visual Studio.</span></span>

<span data-ttu-id="85e0d-233">トレーニングが完了したら、 **[次のステップ]** ボタンを選択して、 **[評価]** ステップに進みます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-233">Once training is complete, select the **Next step** button to move on to the **Evaluate** step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="85e0d-234">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="85e0d-234">Evaluate the model</span></span>

<span data-ttu-id="85e0d-235">[評価] 画面には、モデルの精度など、トレーニング プロセスの結果の概要が表示されます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-235">In the Evaluate screen, you get an overview of the results from the training process, including the model accuracy.</span></span>

![Model Builder の評価ステップ](./media/object-detection-model-builder/obj-det-evaluate.png)

<span data-ttu-id="85e0d-237">この例では、精度が 100% と表示されていますが、これは、データセット内の画像が少なすぎるため、モデルが *オーバーフィット* している可能性がかなり高いことを意味します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-237">In this case, the accuracy says 100%, which means that the model is more than likely *overfit* due to too few images in the dataset.</span></span>

<span data-ttu-id="85e0d-238">**[独自のモデルを試す]** 実験を使用して、モデルが想定どおりに実行されているかどうかをすばやく確認できます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-238">You can use the **Try your model** experience to quickly check whether your model is performing as expected.</span></span>

<span data-ttu-id="85e0d-239">**[画像の参照]** を選択し、テスト画像 (できれば、モデルでトレーニングの一部として使用されていないもの) を提供します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-239">Select **Browse an image** and provide a test image, preferably one that the model did not use as part of training.</span></span>

![Model Builder の独自のモデルを試す](./media/object-detection-model-builder/obj-det-try-model.png)

<span data-ttu-id="85e0d-241">検出された各境界ボックスに表示されるスコアは、検出されたオブジェクトの **信頼度** を示します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-241">The score shown on each detected bounding box indicates the **confidence** of the detected object.</span></span> <span data-ttu-id="85e0d-242">たとえば、上のスクリーンショットでは、一時停止標識を囲む境界ボックス上のスコアは、モデルで、検出されたオブジェクトは一時停止標識であることが 99% 確実であるとされていることを示しています。</span><span class="sxs-lookup"><span data-stu-id="85e0d-242">For instance, in the screenshot above, the score on the bounding box around the stop sign indicates that the model is 99% sure that the detected object is a stop sign.</span></span>

<span data-ttu-id="85e0d-243">**スコアしきい値** は、しきい値スライダーで増減でき、それらのスコアに基づいて検出されたオブジェクトが追加および削除されます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-243">The **Score threshold**, which can be increased or decreased with the threshold slider, will add and remove detected objects based on their scores.</span></span> <span data-ttu-id="85e0d-244">たとえば、しきい値が 0.51 の場合、モデルには、信頼スコアが 0.51 以上のオブジェクトのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-244">For instance, if the threshold is .51, then the model will only show objects that have a confidence score of .51 or above.</span></span> <span data-ttu-id="85e0d-245">しきい値を大きくするほど、検出されるオブジェクトが少なくなり、しきい値を小さくするほど、検出されるオブジェクトが多くなります。</span><span class="sxs-lookup"><span data-stu-id="85e0d-245">As you increase the threshold, you will see less detected objects, and as you decrease the threshold, you will see more detected objects.</span></span>

<span data-ttu-id="85e0d-246">精度のメトリックに不満がある場合、モデルの精度を高めるために試してみる簡単な 1 つの方法は、使用するデータを増やすことです。</span><span class="sxs-lookup"><span data-stu-id="85e0d-246">If you're not satisfied with your accuracy metrics, one easy way to try to improve model accuracy is to use more data.</span></span> <span data-ttu-id="85e0d-247">そうでない場合は、 **[次のステップ]** リンクを選択して、Model Builder の **[コード]** ステップに進みます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-247">Otherwise, select the **Next step** link to move on to the **Code** step in Model Builder.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="85e0d-248">予測を行うコードを追加する</span><span class="sxs-lookup"><span data-stu-id="85e0d-248">Add the code to make predictions</span></span>

<span data-ttu-id="85e0d-249">トレーニング プロセスの結果として 2 つのプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-249">Two projects are created as a result of the training process.</span></span>

- <span data-ttu-id="85e0d-250">*StopSignDetectionML.ConsoleApp*: モデルのトレーニング コードとサンプルの使用に関するコードが含まれる C# .NET Core コンソール アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="85e0d-250">*StopSignDetectionML.ConsoleApp*: A C# .NET Core Console application that contains the model training code and sample consumption code.</span></span>
- <span data-ttu-id="85e0d-251">*StopSignDetectionML.Model*: 入力および出力モデル データのスキーマを定義するデータ モデル、トレーニング時にパフォーマンスが最高のモデルの保存バージョン、および予測を行う `ConsumeModel` というヘルパー クラスを含む .NET Standard クラス ライブラリ。</span><span class="sxs-lookup"><span data-stu-id="85e0d-251">*StopSignDetectionML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training, and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="85e0d-252">Model Builder のコード ステップで、 **[プロジェクトの追加]** を選択して、自動生成されたプロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-252">In the code step of Model Builder, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="85e0d-253">*StopSignDetection* プロジェクトで *Program.cs* ファイルを開き、ファイルの先頭に次の using ステートメントを追加して *StopSignDetectionML.Model* プロジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-253">Open the *Program.cs* file in the *StopSignDetection* project, and add the following using statement at the top of the file to reference the *StopSignDetectionML.Model* project:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/Program.cs#L2)]

1. <span data-ttu-id="85e0d-254">次の[テスト画像](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/test-image1.jpeg)をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="85e0d-254">Download the following [test image](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/test-image1.jpeg).</span></span>
1. <span data-ttu-id="85e0d-255">`ImageSource` プロパティを、アプリケーションの `Main` メソッド内のテスト画像のファイルパスに設定して、`ModelInput` クラスの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-255">Create a new instance of the `ModelInput` class with the `ImageSource` property set to the filepath of your test image inside the `Main` method of your application.</span></span> <span data-ttu-id="85e0d-256">"Hello World" ステートメントを、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="85e0d-256">Replace the "Hello World" statement with the following code:</span></span>

    [!code-csharp [InputData](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/Program.cs#L10-L15)]

1. <span data-ttu-id="85e0d-257">`ConsumeModel` クラスの `Predict` メソッドを使用して、トレーニング済みモデルを読み込み、モデルの [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) を作成して、新しいデータに対して予測を行います。</span><span class="sxs-lookup"><span data-stu-id="85e0d-257">Use the `Predict` method from the `ConsumeModel` class to load the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model, and make predictions on new data.</span></span> <span data-ttu-id="85e0d-258">`ModelInput` ステートメントの下に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-258">Add the following code below the `ModelInput` statement:</span></span>

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/Program.cs#L15)]

1. <span data-ttu-id="85e0d-259">次のコードを追加して、ラベル、座標、スコアを含む予測の出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-259">Print out the Prediction's output, including the label, coordinates, and score by adding the following code:</span></span>

    [!code-csharp [PrintResults](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/Program.cs#L17-L18)]

1. <span data-ttu-id="85e0d-260">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="85e0d-260">Run the application.</span></span>

    <span data-ttu-id="85e0d-261">プログラムによって生成される出力は次のスニペットのようになります。</span><span class="sxs-lookup"><span data-stu-id="85e0d-261">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Boxes:
    
    Top: 89.453415, Left: 481.95343, Right: 724.8073, Bottom: 388.32385, Label: Stop-Sign, Score: 0.99539465
    ```

<span data-ttu-id="85e0d-262">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="85e0d-262">Congratulations!</span></span> <span data-ttu-id="85e0d-263">Model Builder を使用して、画像内の一時停止標識を検出する機械学習モデルを正常に構築しました。</span><span class="sxs-lookup"><span data-stu-id="85e0d-263">You've successfully built a machine learning model to detect stop signs in images using Model Builder.</span></span> <span data-ttu-id="85e0d-264">このチュートリアルのソース コードは、[dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/ObjectDetection_StopSigns) GitHub リポジトリにあります。</span><span class="sxs-lookup"><span data-stu-id="85e0d-264">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/ObjectDetection_StopSigns) GitHub repository.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="85e0d-265">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="85e0d-265">Additional resources</span></span>

<span data-ttu-id="85e0d-266">このチュートリアルで説明しているトピックについて詳しくは、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="85e0d-266">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="85e0d-267">モデル ビルダーのシナリオ</span><span class="sxs-lookup"><span data-stu-id="85e0d-267">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenario)
- [<span data-ttu-id="85e0d-268">ML.NET で ONNX を使用した物体検出</span><span class="sxs-lookup"><span data-stu-id="85e0d-268">Object Detection using ONNX in ML.NET</span></span>](object-detection-onnx.md)
