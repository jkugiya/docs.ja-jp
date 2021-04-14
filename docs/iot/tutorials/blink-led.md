---
title: LED を点滅させる
description: .NET IoT ライブラリを使用して LED を点滅させる方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 0d5db19faac0293b9982731f26dfd85d6ce07b3a
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "102259025"
---
# <a name="blink-an-led"></a><span data-ttu-id="eeab8-103">LED を点滅させる</span><span class="sxs-lookup"><span data-stu-id="eeab8-103">Blink an LED</span></span>

<span data-ttu-id="eeab8-104">汎用 I/O (GPIO) ピンは、個別に制御できます。</span><span class="sxs-lookup"><span data-stu-id="eeab8-104">General-purpose I/O (GPIO) pins can be controlled individually.</span></span> <span data-ttu-id="eeab8-105">これは、LED、リレー、その他のステートフル デバイスを制御する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="eeab8-105">This is useful for controlling LEDs, relays, and other stateful devices.</span></span> <span data-ttu-id="eeab8-106">このトピックでは、.NET とお使いの Raspberry Pi の GPIO ピンを使用して、LED に電力を供給し、繰り返し点滅させます。</span><span class="sxs-lookup"><span data-stu-id="eeab8-106">In this topic, you will use .NET and your Raspberry Pi's GPIO pins to power an LED and blink it repeatedly.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eeab8-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="eeab8-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="eeab8-108">5 mm LED</span><span class="sxs-lookup"><span data-stu-id="eeab8-108">5 mm LED</span></span>
- <span data-ttu-id="eeab8-109">330 Ω の抵抗</span><span class="sxs-lookup"><span data-stu-id="eeab8-109">330 Ω resistor</span></span>
- <span data-ttu-id="eeab8-110">ブレッドボード</span><span class="sxs-lookup"><span data-stu-id="eeab8-110">Breadboard</span></span>
- <span data-ttu-id="eeab8-111">ジャンパー ワイヤ</span><span class="sxs-lookup"><span data-stu-id="eeab8-111">Jumper wires</span></span>
- <span data-ttu-id="eeab8-112">Raspberry Pi GPIO ブレークアウト基板 (省略可能、推奨)</span><span class="sxs-lookup"><span data-stu-id="eeab8-112">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [ensure-ssh](../includes/ensure-ssh.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="eeab8-113">ハードウェアを準備する</span><span class="sxs-lookup"><span data-stu-id="eeab8-113">Prepare the hardware</span></span>

<span data-ttu-id="eeab8-114">ハードウェア コンポーネントを使用して、次の図に示すような回路を構築します。</span><span class="sxs-lookup"><span data-stu-id="eeab8-114">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-led_bb-thumb.png" alt-text="LED と抵抗がある回路を示す Fritzing 図" lightbox="../media/rpi-led_bb.png":::

<span data-ttu-id="eeab8-116">上の図では、次の接続が示されています。</span><span class="sxs-lookup"><span data-stu-id="eeab8-116">The image above depicts the following connections:</span></span>

- <span data-ttu-id="eeab8-117">GPIO 18 から LED の陽極 (長い正のリード) へ</span><span class="sxs-lookup"><span data-stu-id="eeab8-117">GPIO 18 to LED anode (longer, positive lead)</span></span>
- <span data-ttu-id="eeab8-118">LED の陰極 (短い負のリード) から 330 Ω の抵抗 (どちらかの端) へ</span><span class="sxs-lookup"><span data-stu-id="eeab8-118">LED cathode (shorter, negative lead) to 330 Ω resistor (either end)</span></span>
- <span data-ttu-id="eeab8-119">330 Ω の抵抗 (他の端) からグラウンドへ</span><span class="sxs-lookup"><span data-stu-id="eeab8-119">330 Ω resistor (other end) to ground</span></span>

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="eeab8-120">アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="eeab8-120">Create the app</span></span>

<span data-ttu-id="eeab8-121">お好みの開発環境で、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="eeab8-121">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="eeab8-122">[.NET CLI](../../core/tools/dotnet-new.md) または [Visual Studio](../../core/tutorials/with-visual-studio.md) を使用して、新しい .NET コンソール アプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="eeab8-122">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="eeab8-123">「*BlinkTutorial*」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="eeab8-123">Name it *BlinkTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o BlinkTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="eeab8-124">*Program.cs* の内容を次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="eeab8-124">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/BlinkTutorial/Program.cs" :::

    <span data-ttu-id="eeab8-125">上のコードでは以下の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="eeab8-125">In the preceding code:</span></span>

    - <span data-ttu-id="eeab8-126">[using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)によって、`GpioController` のインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="eeab8-126">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `GpioController`.</span></span> <span data-ttu-id="eeab8-127">この `using` 宣言により、オブジェクトが破棄され、ハードウェア リソースが適切に解放されます。</span><span class="sxs-lookup"><span data-stu-id="eeab8-127">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="eeab8-128">出力用に GPIO ピン 18 が開かれています</span><span class="sxs-lookup"><span data-stu-id="eeab8-128">GPIO pin 18 is opened for output</span></span>
    - <span data-ttu-id="eeab8-129">`while` ループが無期限に実行されます。</span><span class="sxs-lookup"><span data-stu-id="eeab8-129">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="eeab8-130">それぞれの反復処理で、以下が実行されます。</span><span class="sxs-lookup"><span data-stu-id="eeab8-130">Each iteration:</span></span>
        1. <span data-ttu-id="eeab8-131">GPIO ピン 18 に値を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="eeab8-131">Writes a value to GPIO pin 18.</span></span> <span data-ttu-id="eeab8-132">`ledOn` が true の場合は、`PinValue.High` (オン) を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="eeab8-132">If `ledOn` is true, it writes `PinValue.High` (on).</span></span> <span data-ttu-id="eeab8-133">それ以外の場合は、`PinValue.Low` を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="eeab8-133">Otherwise, it writes `PinValue.Low`.</span></span>
        1. <span data-ttu-id="eeab8-134">1000 ミリ秒スリープします。</span><span class="sxs-lookup"><span data-stu-id="eeab8-134">Sleeps 1000 ms.</span></span>
        1. <span data-ttu-id="eeab8-135">`ledOn` の値を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="eeab8-135">Toggles the value of `ledOn`.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="eeab8-136">配置ディレクトリに切り替え、実行可能ファイルを実行することで、Raspberry Pi でアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="eeab8-136">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./BlinkTutorial
    ```

    <span data-ttu-id="eeab8-137">LED は毎秒点滅します。</span><span class="sxs-lookup"><span data-stu-id="eeab8-137">The LED blinks off and on every second.</span></span>

1. <span data-ttu-id="eeab8-138"><kbd>Ctrl + C</kbd> キーを押してプログラムを終了します。</span><span class="sxs-lookup"><span data-stu-id="eeab8-138">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="eeab8-139">おめでとうございます。</span><span class="sxs-lookup"><span data-stu-id="eeab8-139">Congratulations!</span></span> <span data-ttu-id="eeab8-140">GPIO を使って LED を点滅させることができました。</span><span class="sxs-lookup"><span data-stu-id="eeab8-140">You've used GPIO to blink an LED.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="eeab8-141">ソース コードを入手する</span><span class="sxs-lookup"><span data-stu-id="eeab8-141">Get the source code</span></span>

<span data-ttu-id="eeab8-142">このチュートリアルのソースは、[GitHub から入手できます](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial)。</span><span class="sxs-lookup"><span data-stu-id="eeab8-142">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial).</span></span>

## <a name="next-steps"></a><span data-ttu-id="eeab8-143">次のステップ</span><span class="sxs-lookup"><span data-stu-id="eeab8-143">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eeab8-144">センサーから環境条件を読み取る方法を学習する</span><span class="sxs-lookup"><span data-stu-id="eeab8-144">Learn how to read environmental conditions from a sensor</span></span>](../tutorials/temp-sensor.md)
