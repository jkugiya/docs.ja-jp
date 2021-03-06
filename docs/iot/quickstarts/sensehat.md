---
title: クイックスタート-.NET を使用して Raspberry Pi Sense HAT を駆動する
description: Raspberry Pi のアドオンボードである Sense HAT を使用して、5分で .NET IoT ライブラリを使い始めることができます。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: quickstart
ms.prod: dotnet
ms.openlocfilehash: 28d6650187bbf7b9ce91516f4da4d09b114c904a
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259701"
---
# <a name="quickstart---use-net-to-drive-a-raspberry-pi-sense-hat"></a><span data-ttu-id="d7d40-103">クイックスタート-.NET を使用して Raspberry Pi Sense HAT を駆動する</span><span class="sxs-lookup"><span data-stu-id="d7d40-103">Quickstart - Use .NET to drive a Raspberry Pi Sense HAT</span></span>

<span data-ttu-id="d7d40-104">Raspberry Pi [SENSE HAT](https://www.raspberrypi.org/products/sense-hat/) (**H** ttached on **T** op)**は、Raspberry** pi のアドオンボードです。</span><span class="sxs-lookup"><span data-stu-id="d7d40-104">The Raspberry Pi [Sense HAT](https://www.raspberrypi.org/products/sense-hat/) (**H** ardware **A** ttached on **T** op) is an add-on board for Raspberry Pi.</span></span> <span data-ttu-id="d7d40-105">Sense HAT には、8×8の RGB LED 行列 (5 ボタンのジョイスティック) が搭載されており、次のセンサーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d7d40-105">The Sense HAT is equipped with an 8×8 RGB LED matrix, a five-button joystick, and includes the following sensors:</span></span>

- <span data-ttu-id="d7d40-106">ジャイロスコープ</span><span class="sxs-lookup"><span data-stu-id="d7d40-106">Gyroscope</span></span>
- <span data-ttu-id="d7d40-107">加速度計</span><span class="sxs-lookup"><span data-stu-id="d7d40-107">Accelerometer</span></span>
- <span data-ttu-id="d7d40-108">磁力計</span><span class="sxs-lookup"><span data-stu-id="d7d40-108">Magnetometer</span></span>
- <span data-ttu-id="d7d40-109">気温</span><span class="sxs-lookup"><span data-stu-id="d7d40-109">Temperature</span></span>
- <span data-ttu-id="d7d40-110">気圧の圧力</span><span class="sxs-lookup"><span data-stu-id="d7d40-110">Barometric pressure</span></span>
- <span data-ttu-id="d7d40-111">湿度</span><span class="sxs-lookup"><span data-stu-id="d7d40-111">Humidity</span></span>

<span data-ttu-id="d7d40-112">このクイックスタートでは、.NET を使用して Sense HAT からセンサー値を取得し、ジョイスティック入力に応答して、LED マトリックスを駆動しています。</span><span class="sxs-lookup"><span data-stu-id="d7d40-112">This quickstart uses .NET to retrieve sensor values from the Sense HAT, respond to joystick input, and drive the LED matrix.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d7d40-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="d7d40-113">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="d7d40-114">Sense HAT</span><span class="sxs-lookup"><span data-stu-id="d7d40-114">Sense HAT</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="run-the-quickstart"></a><span data-ttu-id="d7d40-115">クイックスタートを実行する</span><span class="sxs-lookup"><span data-stu-id="d7d40-115">Run the quickstart</span></span>

<span data-ttu-id="d7d40-116">Sense HAT を Raspberry Pi に接続します。</span><span class="sxs-lookup"><span data-stu-id="d7d40-116">Attach the Sense HAT to your Raspberry Pi.</span></span> <span data-ttu-id="d7d40-117">Raspberry Pi (ローカルまたはリモート) の Bash プロンプトから、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d7d40-117">From a Bash prompt on the Raspberry Pi (local or remote), run the following command:</span></span>

```bash
. <(wget -q -O - https://aka.ms/dotnet-iot-sensehat-quickstart)
```

<span data-ttu-id="d7d40-118">コマンドは、スクリプトをダウンロードして実行します。</span><span class="sxs-lookup"><span data-stu-id="d7d40-118">The command downloads and runs a script.</span></span> <span data-ttu-id="d7d40-119">スクリプトは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d7d40-119">The script:</span></span>

- <span data-ttu-id="d7d40-120">.NET SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="d7d40-120">Installs the .NET SDK.</span></span>
- <span data-ttu-id="d7d40-121">Sense HAT クイックスタートプロジェクトを含む GitHub リポジトリを複製します。</span><span class="sxs-lookup"><span data-stu-id="d7d40-121">Clones a GitHub repository that includes the Sense HAT quickstart project.</span></span>
- <span data-ttu-id="d7d40-122">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="d7d40-122">Builds the project.</span></span>
- <span data-ttu-id="d7d40-123">プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="d7d40-123">Runs the project.</span></span>

<span data-ttu-id="d7d40-124">センサーデータが表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d7d40-124">Observe the console output as sensor data is displayed.</span></span> <span data-ttu-id="d7d40-125">LED マトリックスには、青のフィールドに黄色のピクセルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7d40-125">The LED matrix displays a yellow pixel on a field of blue.</span></span> <span data-ttu-id="d7d40-126">ジョイスティックを任意の方向に保持すると、その方向に黄色のピクセルが移動します。</span><span class="sxs-lookup"><span data-stu-id="d7d40-126">Holding the joystick in any direction moves the yellow pixel in that direction.</span></span> <span data-ttu-id="d7d40-127">[Center ジョイスティック] ボタンをクリックすると、背景が青から赤に切り替わります。</span><span class="sxs-lookup"><span data-stu-id="d7d40-127">Clicking the center joystick button causes the background to switch from blue to red.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="d7d40-128">ソース コードを入手する</span><span class="sxs-lookup"><span data-stu-id="d7d40-128">Get the source code</span></span>

<span data-ttu-id="d7d40-129">このクイックスタートのソースは、 [GitHub で入手でき](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart)ます。</span><span class="sxs-lookup"><span data-stu-id="d7d40-129">The source for this quickstart is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d7d40-130">次のステップ</span><span class="sxs-lookup"><span data-stu-id="d7d40-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d7d40-131">General Purpose 入力/出力を使用して LED を点滅させる方法について説明します</span><span class="sxs-lookup"><span data-stu-id="d7d40-131">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
