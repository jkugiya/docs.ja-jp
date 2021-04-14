---
title: Model Builder に GPU サポートをインストールする方法
description: Model Builder に GPU サポートをインストールする方法について説明します
ms.date: 04/08/2021
author: luisquintanilla
ms.author: luquinta
ms.topic: how-to
ms.openlocfilehash: 81f84a17429fd03506bbce30f5646941e4e80b3b
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255429"
---
# <a name="how-to-install-gpu-support-in-model-builder"></a><span data-ttu-id="a8ae1-103">Model Builder に GPU サポートをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="a8ae1-103">How to install GPU support in Model Builder</span></span>

<span data-ttu-id="a8ae1-104">Model Builder で GPU を使用するために GPU ドライバーをインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-104">Learn how to install the GPU drivers to use your GPU with Model Builder.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a8ae1-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="a8ae1-105">Prerequisites</span></span>

- <span data-ttu-id="a8ae1-106">Model Builder Visual Studio 拡張機能。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-106">Model Builder Visual Studio extension.</span></span> <span data-ttu-id="a8ae1-107">この拡張機能は、Visual Studio バージョン 16.6.1 以降に組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-107">The extension is built into Visual Studio as of version 16.6.1.</span></span>
- <span data-ttu-id="a8ae1-108">[Model Builder Visual Studio GPU サポート拡張機能](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU)。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-108">[Model Builder Visual Studio GPU support extension](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU).</span></span>
- <span data-ttu-id="a8ae1-109">少なくとも 1 つの CUDA 互換 GPU。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-109">At least one CUDA compatible GPU.</span></span> <span data-ttu-id="a8ae1-110">互換性のある GPU の一覧については、[NVIDIA のガイド](https://developer.nvidia.com/cuda-gpus)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-110">For a list of compatible GPUs, see [NVIDIA's guide](https://developer.nvidia.com/cuda-gpus).</span></span>
- <span data-ttu-id="a8ae1-111">NVIDIA 開発者アカウント。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-111">NVIDIA developer account.</span></span> <span data-ttu-id="a8ae1-112">アカウントがない場合は、[無料アカウントを作成](https://developer.nvidia.com/developer-program)してください。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-112">If you don't have one, [create a free account](https://developer.nvidia.com/developer-program).</span></span>

## <a name="install-dependencies"></a><span data-ttu-id="a8ae1-113">依存関係のインストール</span><span class="sxs-lookup"><span data-stu-id="a8ae1-113">Install dependencies</span></span>

1. <span data-ttu-id="a8ae1-114">[CUDA v10.1](https://developer.nvidia.com/cuda-10.1-download-archive-update2) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-114">Install [CUDA v10.1](https://developer.nvidia.com/cuda-10.1-download-archive-update2).</span></span> <span data-ttu-id="a8ae1-115">他の新しいバージョンではなく、必ず CUDA v10.1 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-115">Make sure you install CUDA v10.1, not any other newer version.</span></span> <span data-ttu-id="a8ae1-116">CUDA の複数のバージョンをインストールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-116">You cannot have multiple versions of CUDA installed.</span></span>
1. <span data-ttu-id="a8ae1-117">[CUDA 10.1 用の cuDNN v7.6.4](https://developer.nvidia.com/rdp/cudnn-download) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-117">Install [cuDNN v7.6.4 for CUDA 10.1](https://developer.nvidia.com/rdp/cudnn-download).</span></span> <span data-ttu-id="a8ae1-118">cuDNN の複数のバージョンをインストールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-118">You cannot have multiple versions of cuDNN installed.</span></span> <span data-ttu-id="a8ae1-119">cuDNN v7.6.4 zip ファイルをダウンロードしてアンパックした後、`<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` を `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\bin` にコピーします。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-119">After downloading cuDNN v7.6.4 zip file and unpacking it, copy `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` to `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\bin`.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="a8ae1-120">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a8ae1-120">Troubleshooting</span></span>

<span data-ttu-id="a8ae1-121">**使用している GPU の種類を確認するにはどうすればよいですか?**</span><span class="sxs-lookup"><span data-stu-id="a8ae1-121">**How do I know what GPU I have?**</span></span>

<span data-ttu-id="a8ae1-122">以下の手順のようにします。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-122">Follow instructions provided:</span></span>

1. <span data-ttu-id="a8ae1-123">デスクトップを右クリックします</span><span class="sxs-lookup"><span data-stu-id="a8ae1-123">Right-click on desktop</span></span>
1. <span data-ttu-id="a8ae1-124">ポップアップ ウィンドウに [NVIDIA Control Panel]\(NVIDIA コントロール パネル\) または [NVIDIA Display]\(NVIDIA ディスプレイ\) と表示される場合は、NVIDIA GPU を使用しています。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-124">If you see "NVIDIA Control Panel" or "NVIDIA Display" in the pop-up window, you have an NVIDIA GPU</span></span>
1. <span data-ttu-id="a8ae1-125">ポップアップ ウィンドウで [NVIDIA Control Panel]\(NVIDIA コントロール パネル\) または [NVIDIA Display]\(NVIDIA ディスプレイ\) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-125">Click on "NVIDIA Control Panel" or "NVIDIA Display" in the pop-up window</span></span>
1. <span data-ttu-id="a8ae1-126">[Graphics Card Information]\(グラフィックス カード情報\) を確認します</span><span class="sxs-lookup"><span data-stu-id="a8ae1-126">Look at "Graphics Card Information"</span></span>
1. <span data-ttu-id="a8ae1-127">お使いの NVIDIA GPU の名前が表示されます</span><span class="sxs-lookup"><span data-stu-id="a8ae1-127">You will see the name of your NVIDIA GPU</span></span>

<span data-ttu-id="a8ae1-128">**[NVIDIA Control Panel]\(NVIDIA コントロール パネル\) は表示されません (または開くことができません) が、NVIDIA GPU があることはわかっています。**</span><span class="sxs-lookup"><span data-stu-id="a8ae1-128">**I don't see NVIDIA Control Panel (or it fails to open) but I know I have an NVIDIA GPU.**</span></span>

1. <span data-ttu-id="a8ae1-129">デバイス マネージャーを開きます</span><span class="sxs-lookup"><span data-stu-id="a8ae1-129">Open Device Manager</span></span>
1. <span data-ttu-id="a8ae1-130">ディスプレイ アダプターを確認します</span><span class="sxs-lookup"><span data-stu-id="a8ae1-130">Look at Display adapters</span></span>
1. <span data-ttu-id="a8ae1-131">GPU に対して適切な[ドライバー](https://www.nvidia.com/drivers)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="a8ae1-131">Install appropriate [driver](https://www.nvidia.com/drivers) for your GPU.</span></span>
