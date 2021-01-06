---
title: LED を点滅させる
description: .NET IoT ライブラリを使用して LED を点滅させる方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 07a050c0655f9cae3d7f2b924c0dd07ac1c6c0b9
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96594150"
---
# <a name="blink-an-led"></a><span data-ttu-id="feb46-103">LED を点滅させる</span><span class="sxs-lookup"><span data-stu-id="feb46-103">Blink an LED</span></span>

<span data-ttu-id="feb46-104">汎用 i/o (GPIO) ピンは、個別に制御できます。</span><span class="sxs-lookup"><span data-stu-id="feb46-104">General-purpose I/O (GPIO) pins can be controlled individually.</span></span> <span data-ttu-id="feb46-105">これは、Led、リレー、およびその他のステートフルデバイスを制御する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="feb46-105">This is useful for controlling LEDs, relays, and other stateful devices.</span></span> <span data-ttu-id="feb46-106">このトピックでは、.NET と Raspberry Pi の GPIO ピンを使用して、LED の電源を入れ、繰り返し点滅させます。</span><span class="sxs-lookup"><span data-stu-id="feb46-106">In this topic, you will use .NET and your Raspberry Pi's GPIO pins to power an LED and blink it repeatedly.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="feb46-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="feb46-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="feb46-108">5 mm LED</span><span class="sxs-lookup"><span data-stu-id="feb46-108">5 mm LED</span></span>
- <span data-ttu-id="feb46-109">330Ωの抵抗</span><span class="sxs-lookup"><span data-stu-id="feb46-109">330 Ω resistor</span></span>
- <span data-ttu-id="feb46-110">ブレッドボード</span><span class="sxs-lookup"><span data-stu-id="feb46-110">Breadboard</span></span>
- <span data-ttu-id="feb46-111">ジャンパー ワイヤ</span><span class="sxs-lookup"><span data-stu-id="feb46-111">Jumper wires</span></span>
- <span data-ttu-id="feb46-112">Raspberry Pi GPIO ブレイクボードボード (省略可能/推奨)</span><span class="sxs-lookup"><span data-stu-id="feb46-112">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [ensure-ssh](../includes/ensure-ssh.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="feb46-113">ハードウェアを準備する</span><span class="sxs-lookup"><span data-stu-id="feb46-113">Prepare the hardware</span></span>

<span data-ttu-id="feb46-114">ハードウェアコンポーネントを使用して、次の図に示すように回線を構築します。</span><span class="sxs-lookup"><span data-stu-id="feb46-114">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-led_bb-thumb.png" alt-text="LED と抵抗がある回線を示す Fritzing 図" lightbox="../media/rpi-led_bb.png":::

<span data-ttu-id="feb46-116">上の図は、次の接続を示しています。</span><span class="sxs-lookup"><span data-stu-id="feb46-116">The image above depicts the following connections:</span></span>

- <span data-ttu-id="feb46-117">GPIO 18 から LED anode (長い潜在顧客)</span><span class="sxs-lookup"><span data-stu-id="feb46-117">GPIO 18 to LED anode (longer, positive lead)</span></span>
- <span data-ttu-id="feb46-118">LED ブラウン (短い、負のリード) から330Ωの抵抗 (両端)</span><span class="sxs-lookup"><span data-stu-id="feb46-118">LED cathode (shorter, negative lead) to 330 Ω resistor (either end)</span></span>
- <span data-ttu-id="feb46-119">330Ωの抵抗 (他の端) から地面へ</span><span class="sxs-lookup"><span data-stu-id="feb46-119">330 Ω resistor (other end) to ground</span></span>

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="feb46-120">アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="feb46-120">Create the app</span></span>

<span data-ttu-id="feb46-121">お好みの開発環境で、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="feb46-121">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="feb46-122">[.NET CLI](../../core/tools/dotnet-new.md)または[Visual Studio](../../core/tutorials/with-visual-studio.md)を使用して、新しい .net コンソールアプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="feb46-122">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="feb46-123">「 *Blinktutorial*」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="feb46-123">Name it *BlinkTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o BlinkTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="feb46-124">*Program.cs* の内容を次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="feb46-124">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/BlinkTutorial/Program.cs" :::

    <span data-ttu-id="feb46-125">上記のコードにより、次のことが行われます。</span><span class="sxs-lookup"><span data-stu-id="feb46-125">In the preceding code:</span></span>

    - <span data-ttu-id="feb46-126">[Using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)は、のインスタンスを作成し `GpioController` ます。</span><span class="sxs-lookup"><span data-stu-id="feb46-126">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `GpioController`.</span></span> <span data-ttu-id="feb46-127">この `using` 宣言により、オブジェクトが破棄され、ハードウェアリソースが正常に解放されます。</span><span class="sxs-lookup"><span data-stu-id="feb46-127">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="feb46-128">出力用に GPIO pin 18 が開かれています</span><span class="sxs-lookup"><span data-stu-id="feb46-128">GPIO pin 18 is opened for output</span></span>
    - <span data-ttu-id="feb46-129">`while`ループは無期限に実行されます。</span><span class="sxs-lookup"><span data-stu-id="feb46-129">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="feb46-130">各イテレーション:</span><span class="sxs-lookup"><span data-stu-id="feb46-130">Each iteration:</span></span>
        1. <span data-ttu-id="feb46-131">GPIO pin 18 に値を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="feb46-131">Writes a value to GPIO pin 18.</span></span> <span data-ttu-id="feb46-132">`ledOn`が true の場合は、 `PinValue.High` (に) を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="feb46-132">If `ledOn` is true, it writes `PinValue.High` (on).</span></span> <span data-ttu-id="feb46-133">それ以外の場合は、を書き込み `PinValue.Low` ます。</span><span class="sxs-lookup"><span data-stu-id="feb46-133">Otherwise, it writes `PinValue.Low`.</span></span>
        1. <span data-ttu-id="feb46-134">1000ミリ秒スリープします。</span><span class="sxs-lookup"><span data-stu-id="feb46-134">Sleeps 1000 ms.</span></span>
        1. <span data-ttu-id="feb46-135">の値を切り替え `ledOn` ます。</span><span class="sxs-lookup"><span data-stu-id="feb46-135">Toggles the value of `ledOn`.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="feb46-136">配置ディレクトリに切り替え、実行可能ファイルを実行して、Raspberry Pi でアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="feb46-136">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./BlinkTutorial
    ```

    <span data-ttu-id="feb46-137">LED が点滅し、毎秒点灯します。</span><span class="sxs-lookup"><span data-stu-id="feb46-137">The LED blinks off and on every second.</span></span>

1. <span data-ttu-id="feb46-138"><kbd>Ctrl + C</kbd>キーを押してプログラムを終了します。</span><span class="sxs-lookup"><span data-stu-id="feb46-138">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="feb46-139">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="feb46-139">Congratulations!</span></span> <span data-ttu-id="feb46-140">これで、GPIO を使って LED を点滅させることができました。</span><span class="sxs-lookup"><span data-stu-id="feb46-140">You've used GPIO to blink an LED.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="feb46-141">ソース コードを入手する</span><span class="sxs-lookup"><span data-stu-id="feb46-141">Get the source code</span></span>

<span data-ttu-id="feb46-142">このチュートリアルのソースは、 [GitHub で入手でき](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span> ます。</span><span class="sxs-lookup"><span data-stu-id="feb46-142">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="feb46-143">次の手順</span><span class="sxs-lookup"><span data-stu-id="feb46-143">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="feb46-144">センサーから環境の状態を読み取る方法について説明します</span><span class="sxs-lookup"><span data-stu-id="feb46-144">Learn how to read environmental conditions from a sensor</span></span>](../tutorials/temp-sensor.md)