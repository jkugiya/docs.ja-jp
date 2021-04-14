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
# <a name="how-to-install-gpu-support-in-model-builder"></a>Model Builder に GPU サポートをインストールする方法

Model Builder で GPU を使用するために GPU ドライバーをインストールする方法について説明します。

## <a name="prerequisites"></a>前提条件

- Model Builder Visual Studio 拡張機能。 この拡張機能は、Visual Studio バージョン 16.6.1 以降に組み込まれています。
- [Model Builder Visual Studio GPU サポート拡張機能](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU)。
- 少なくとも 1 つの CUDA 互換 GPU。 互換性のある GPU の一覧については、[NVIDIA のガイド](https://developer.nvidia.com/cuda-gpus)を参照してください。
- NVIDIA 開発者アカウント。 アカウントがない場合は、[無料アカウントを作成](https://developer.nvidia.com/developer-program)してください。

## <a name="install-dependencies"></a>依存関係のインストール

1. [CUDA v10.1](https://developer.nvidia.com/cuda-10.1-download-archive-update2) をインストールします。 他の新しいバージョンではなく、必ず CUDA v10.1 をインストールします。 CUDA の複数のバージョンをインストールすることはできません。
1. [CUDA 10.1 用の cuDNN v7.6.4](https://developer.nvidia.com/rdp/cudnn-download) をインストールします。 cuDNN の複数のバージョンをインストールすることはできません。 cuDNN v7.6.4 zip ファイルをダウンロードしてアンパックした後、`<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` を `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\bin` にコピーします。

## <a name="troubleshooting"></a>トラブルシューティング

**使用している GPU の種類を確認するにはどうすればよいですか?**

以下の手順のようにします。

1. デスクトップを右クリックします
1. ポップアップ ウィンドウに [NVIDIA Control Panel]\(NVIDIA コントロール パネル\) または [NVIDIA Display]\(NVIDIA ディスプレイ\) と表示される場合は、NVIDIA GPU を使用しています。
1. ポップアップ ウィンドウで [NVIDIA Control Panel]\(NVIDIA コントロール パネル\) または [NVIDIA Display]\(NVIDIA ディスプレイ\) をクリックします。
1. [Graphics Card Information]\(グラフィックス カード情報\) を確認します
1. お使いの NVIDIA GPU の名前が表示されます

**[NVIDIA Control Panel]\(NVIDIA コントロール パネル\) は表示されません (または開くことができません) が、NVIDIA GPU があることはわかっています。**

1. デバイス マネージャーを開きます
1. ディスプレイ アダプターを確認します
1. GPU に対して適切な[ドライバー](https://www.nvidia.com/drivers)をインストールします。
