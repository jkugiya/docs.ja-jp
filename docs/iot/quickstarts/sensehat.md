---
title: クイックスタート-.NET を使用して Raspberry Pi Sense HAT を駆動する
description: Raspberry Pi のアドオンボードである Sense HAT を使用して、5分で .NET IoT ライブラリを使い始めることができます。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: quickstart
ms.prod: dotnet
ms.openlocfilehash: 2919db55304590f5557aa0cbda50cc4bd6640443
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739531"
---
# <a name="quickstart---use-net-to-drive-a-raspberry-pi-sense-hat"></a><span data-ttu-id="a6ca5-103">クイックスタート-.NET を使用して Raspberry Pi Sense HAT を駆動する</span><span class="sxs-lookup"><span data-stu-id="a6ca5-103">Quickstart - Use .NET to drive a Raspberry Pi Sense HAT</span></span>

<span data-ttu-id="a6ca5-104">Raspberry pi [Sense HAT](https://www.raspberrypi.org/products/sense-hat/) <span class="docon docon-navigate-external x-hidden-focus"></span> (**H** ttached on **T** op) は、Raspberry pi のアドオンボードです **A**。</span><span class="sxs-lookup"><span data-stu-id="a6ca5-104">The Raspberry Pi [Sense HAT](https://www.raspberrypi.org/products/sense-hat/) <span class="docon docon-navigate-external x-hidden-focus"></span> (**H** ardware **A** ttached on **T** op) is an add-on board for Raspberry Pi.</span></span> <span data-ttu-id="a6ca5-105">Sense HAT には、8×8の RGB LED 行列 (5 ボタンのジョイスティック) が搭載されており、次のセンサーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a6ca5-105">The Sense HAT is equipped with an 8×8 RGB LED matrix, a five-button joystick, and includes the following sensors:</span></span>

- <span data-ttu-id="a6ca5-106">ジャイロスコープ</span><span class="sxs-lookup"><span data-stu-id="a6ca5-106">Gyroscope</span></span>
- <span data-ttu-id="a6ca5-107">加速度計</span><span class="sxs-lookup"><span data-stu-id="a6ca5-107">Accelerometer</span></span>
- <span data-ttu-id="a6ca5-108">磁力計</span><span class="sxs-lookup"><span data-stu-id="a6ca5-108">Magnetometer</span></span>
- <span data-ttu-id="a6ca5-109">気温</span><span class="sxs-lookup"><span data-stu-id="a6ca5-109">Temperature</span></span>
- <span data-ttu-id="a6ca5-110">気圧の圧力</span><span class="sxs-lookup"><span data-stu-id="a6ca5-110">Barometric pressure</span></span>
- <span data-ttu-id="a6ca5-111">湿度</span><span class="sxs-lookup"><span data-stu-id="a6ca5-111">Humidity</span></span>

<span data-ttu-id="a6ca5-112">このクイックスタートでは、.NET を使用して Sense HAT からセンサー値を取得し、ジョイスティック入力に応答して、LED マトリックスを駆動しています。</span><span class="sxs-lookup"><span data-stu-id="a6ca5-112">This quickstart uses .NET to retrieve sensor values from the Sense HAT, respond to joystick input, and drive the LED matrix.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a6ca5-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="a6ca5-113">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="a6ca5-114">Sense HAT</span><span class="sxs-lookup"><span data-stu-id="a6ca5-114">Sense HAT</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="run-the-quickstart"></a><span data-ttu-id="a6ca5-115">クイックスタートを実行する</span><span class="sxs-lookup"><span data-stu-id="a6ca5-115">Run the quickstart</span></span>

<span data-ttu-id="a6ca5-116">Sense HAT を Raspberry Pi に接続します。</span><span class="sxs-lookup"><span data-stu-id="a6ca5-116">Attach the Sense HAT to your Raspberry Pi.</span></span> <span data-ttu-id="a6ca5-117">Raspberry Pi (ローカルまたはリモート) の Bash プロンプトから、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a6ca5-117">From a Bash prompt on the Raspberry Pi (local or remote), run the following command:</span></span>

```bash
. <(wget -q -O - https://aka.ms/dotnet-iot-sensehat-quickstart)
```

<span data-ttu-id="a6ca5-118">コマンドは、スクリプトをダウンロードして実行します。</span><span class="sxs-lookup"><span data-stu-id="a6ca5-118">The command downloads and runs a script.</span></span> <span data-ttu-id="a6ca5-119">スクリプト:</span><span class="sxs-lookup"><span data-stu-id="a6ca5-119">The script:</span></span>

- <span data-ttu-id="a6ca5-120">.NET SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="a6ca5-120">Installs the .NET SDK.</span></span>
- <span data-ttu-id="a6ca5-121">Sense HAT クイックスタートプロジェクトを含む GitHub リポジトリを複製します。</span><span class="sxs-lookup"><span data-stu-id="a6ca5-121">Clones a GitHub repository that includes the Sense HAT quickstart project.</span></span>
- <span data-ttu-id="a6ca5-122">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="a6ca5-122">Builds the project.</span></span>
- <span data-ttu-id="a6ca5-123">プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="a6ca5-123">Runs the project.</span></span>

<span data-ttu-id="a6ca5-124">センサーデータが表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a6ca5-124">Observe the console output as sensor data is displayed.</span></span> <span data-ttu-id="a6ca5-125">LED マトリックスには、青のフィールドに黄色のピクセルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a6ca5-125">The LED matrix displays a yellow pixel on a field of blue.</span></span> <span data-ttu-id="a6ca5-126">ジョイスティックを任意の方向に保持すると、その方向に黄色のピクセルが移動します。</span><span class="sxs-lookup"><span data-stu-id="a6ca5-126">Holding the joystick in any direction moves the yellow pixel in that direction.</span></span> <span data-ttu-id="a6ca5-127">[Center ジョイスティック] ボタンをクリックすると、背景が青から赤に切り替わります。</span><span class="sxs-lookup"><span data-stu-id="a6ca5-127">Clicking the center joystick button causes the background to switch from blue to red.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="a6ca5-128">ソース コードを入手する</span><span class="sxs-lookup"><span data-stu-id="a6ca5-128">Get the source code</span></span>

<span data-ttu-id="a6ca5-129">このクイックスタートのソースは、 [GitHub で入手でき](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart) <span class="docon docon-navigate-external x-hidden-focus"></span> ます。</span><span class="sxs-lookup"><span data-stu-id="a6ca5-129">The source for this quickstart is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a6ca5-130">次のステップ</span><span class="sxs-lookup"><span data-stu-id="a6ca5-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a6ca5-131">General Purpose 入力/出力を使用して LED を点滅させる方法について説明します</span><span class="sxs-lookup"><span data-stu-id="a6ca5-131">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)