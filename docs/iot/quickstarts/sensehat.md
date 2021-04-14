---
title: クイックスタート - .NET を使用して Raspberry Pi Sense HAT を動作させる
description: Raspberry Pi 用の拡張用基板である Sense HAT を使用して、.NET IoT ライブラリの使用を 5 分で開始します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: quickstart
ms.prod: dotnet
ms.openlocfilehash: 28d6650187bbf7b9ce91516f4da4d09b114c904a
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "102259701"
---
# <a name="quickstart---use-net-to-drive-a-raspberry-pi-sense-hat"></a><span data-ttu-id="7c32c-103">クイックスタート - .NET を使用して Raspberry Pi Sense HAT を動作させる</span><span class="sxs-lookup"><span data-stu-id="7c32c-103">Quickstart - Use .NET to drive a Raspberry Pi Sense HAT</span></span>

<span data-ttu-id="7c32c-104">Raspberry Pi [Sense HAT](https://www.raspberrypi.org/products/sense-hat/) (**H** ardware **A** ttached on **T** op (上部に取り付けるハードウェア)) は、Raspberry Pi 用の拡張用基板です。</span><span class="sxs-lookup"><span data-stu-id="7c32c-104">The Raspberry Pi [Sense HAT](https://www.raspberrypi.org/products/sense-hat/) (**H** ardware **A** ttached on **T** op) is an add-on board for Raspberry Pi.</span></span> <span data-ttu-id="7c32c-105">Sense HAT には、8×8 の RGB LED マトリックスと 5 ボタンのジョイスティックが搭載されており、次のセンサーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c32c-105">The Sense HAT is equipped with an 8×8 RGB LED matrix, a five-button joystick, and includes the following sensors:</span></span>

- <span data-ttu-id="7c32c-106">ジャイロスコープ</span><span class="sxs-lookup"><span data-stu-id="7c32c-106">Gyroscope</span></span>
- <span data-ttu-id="7c32c-107">加速度計</span><span class="sxs-lookup"><span data-stu-id="7c32c-107">Accelerometer</span></span>
- <span data-ttu-id="7c32c-108">磁力計</span><span class="sxs-lookup"><span data-stu-id="7c32c-108">Magnetometer</span></span>
- <span data-ttu-id="7c32c-109">気温</span><span class="sxs-lookup"><span data-stu-id="7c32c-109">Temperature</span></span>
- <span data-ttu-id="7c32c-110">気圧</span><span class="sxs-lookup"><span data-stu-id="7c32c-110">Barometric pressure</span></span>
- <span data-ttu-id="7c32c-111">湿度</span><span class="sxs-lookup"><span data-stu-id="7c32c-111">Humidity</span></span>

<span data-ttu-id="7c32c-112">このクイックスタートでは .NET を使用して、Sense HAT からセンサー値を取得し、ジョイスティック入力に応答し、LED マトリックスを動作させます。</span><span class="sxs-lookup"><span data-stu-id="7c32c-112">This quickstart uses .NET to retrieve sensor values from the Sense HAT, respond to joystick input, and drive the LED matrix.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7c32c-113">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7c32c-113">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="7c32c-114">Sense HAT</span><span class="sxs-lookup"><span data-stu-id="7c32c-114">Sense HAT</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="run-the-quickstart"></a><span data-ttu-id="7c32c-115">クイックスタートを実行する</span><span class="sxs-lookup"><span data-stu-id="7c32c-115">Run the quickstart</span></span>

<span data-ttu-id="7c32c-116">Sense HAT を Raspberry Pi に取り付けます。</span><span class="sxs-lookup"><span data-stu-id="7c32c-116">Attach the Sense HAT to your Raspberry Pi.</span></span> <span data-ttu-id="7c32c-117">Raspberry Pi 上の Bash プロンプト (ローカルまたはリモート) から、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="7c32c-117">From a Bash prompt on the Raspberry Pi (local or remote), run the following command:</span></span>

```bash
. <(wget -q -O - https://aka.ms/dotnet-iot-sensehat-quickstart)
```

<span data-ttu-id="7c32c-118">このコマンドにより、スクリプトがダウンロードされて実行されます。</span><span class="sxs-lookup"><span data-stu-id="7c32c-118">The command downloads and runs a script.</span></span> <span data-ttu-id="7c32c-119">スクリプトは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7c32c-119">The script:</span></span>

- <span data-ttu-id="7c32c-120">.NET SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="7c32c-120">Installs the .NET SDK.</span></span>
- <span data-ttu-id="7c32c-121">Sense HAT クイックスタート プロジェクトを含む GitHub リポジトリをクローンします。</span><span class="sxs-lookup"><span data-stu-id="7c32c-121">Clones a GitHub repository that includes the Sense HAT quickstart project.</span></span>
- <span data-ttu-id="7c32c-122">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="7c32c-122">Builds the project.</span></span>
- <span data-ttu-id="7c32c-123">プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="7c32c-123">Runs the project.</span></span>

<span data-ttu-id="7c32c-124">コンソールの出力でセンサー データが表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7c32c-124">Observe the console output as sensor data is displayed.</span></span> <span data-ttu-id="7c32c-125">LED マトリックスには、青のフィールド上に黄色のピクセルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7c32c-125">The LED matrix displays a yellow pixel on a field of blue.</span></span> <span data-ttu-id="7c32c-126">ジョイスティックを任意の方向に保持すると、その方向に黄色のピクセルが移動します。</span><span class="sxs-lookup"><span data-stu-id="7c32c-126">Holding the joystick in any direction moves the yellow pixel in that direction.</span></span> <span data-ttu-id="7c32c-127">中央のジョイスティック ボタンをクリックすると、背景が青から赤に切り替わります。</span><span class="sxs-lookup"><span data-stu-id="7c32c-127">Clicking the center joystick button causes the background to switch from blue to red.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="7c32c-128">ソース コードを入手する</span><span class="sxs-lookup"><span data-stu-id="7c32c-128">Get the source code</span></span>

<span data-ttu-id="7c32c-129">このクイックスタートのソースは、[GitHub から入手できます](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart)。</span><span class="sxs-lookup"><span data-stu-id="7c32c-129">The source for this quickstart is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7c32c-130">次の手順</span><span class="sxs-lookup"><span data-stu-id="7c32c-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c32c-131">汎用入出力を使用して LED を点滅させる方法を学習する</span><span class="sxs-lookup"><span data-stu-id="7c32c-131">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
