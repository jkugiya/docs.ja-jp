---
title: センサーから環境条件を読み取る
description: .NET IoT ライブラリを使用して、温度、気圧、湿度を読み取る方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/14/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: bc5c2b9f0876603c152da859547c58b83826969c
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "102259838"
---
# <a name="read-environmental-conditions-from-a-sensor"></a><span data-ttu-id="0d6ab-103">センサーから環境条件を読み取る</span><span class="sxs-lookup"><span data-stu-id="0d6ab-103">Read environmental conditions from a sensor</span></span>

<span data-ttu-id="0d6ab-104">IoT デバイスの最も一般的なシナリオの 1 つは、環境条件の検出です。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-104">One of the most common scenarios for IoT devices is detection of environmental conditions.</span></span> <span data-ttu-id="0d6ab-105">温度、湿度、気圧などを監視するために、さまざまなセンサーを利用できます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-105">A variety of sensors are available to monitor temperature, humidity, barometric pressure, and more.</span></span>

<span data-ttu-id="0d6ab-106">このトピックでは、.NET を使用してセンサーから環境条件を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-106">In this topic, you will use .NET to read environmental conditions from a sensor.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0d6ab-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="0d6ab-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="0d6ab-108">[BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) 湿度/気圧/温度センサー ブレークアウト</span><span class="sxs-lookup"><span data-stu-id="0d6ab-108">[BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) humidity/barometric pressure/temperature sensor breakout</span></span>
- <span data-ttu-id="0d6ab-109">ジャンパー ワイヤ</span><span class="sxs-lookup"><span data-stu-id="0d6ab-109">Jumper wires</span></span>
- <span data-ttu-id="0d6ab-110">ブレッドボード (省略可能)</span><span class="sxs-lookup"><span data-stu-id="0d6ab-110">Breadboard (optional)</span></span>
- <span data-ttu-id="0d6ab-111">Raspberry Pi GPIO ブレークアウト基板 (省略可能)</span><span class="sxs-lookup"><span data-stu-id="0d6ab-111">Raspberry Pi GPIO breakout board (optional)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!IMPORTANT]
> <span data-ttu-id="0d6ab-112">BME280 ブレークアウトの製造元は多数あります。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-112">There are many manufacturers of BME280 breakouts.</span></span> <span data-ttu-id="0d6ab-113">ほとんどの設計は類似しており、製造元が異なる機能を用意することはないはずです。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-113">Most designs are similar, and the manufacturer shouldn't make any difference to the functionality.</span></span> <span data-ttu-id="0d6ab-114">このチュートリアルでは、バリエーションを考慮しようと努めています。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-114">This tutorial attempts to account for variations.</span></span> <span data-ttu-id="0d6ab-115">お使いの BME280 ブレークアウトに、Inter-Integrated Circuit (I2C) インターフェイスが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-115">Ensure your BME280 breakout includes an Inter-Integrated Circuit (I2C) interface.</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="0d6ab-116">ハードウェアを準備する</span><span class="sxs-lookup"><span data-stu-id="0d6ab-116">Prepare the hardware</span></span>

<span data-ttu-id="0d6ab-117">ハードウェア コンポーネントを使用して、次の図に示すような回路を構築します。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-117">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-bmp280_i2c-thumb.png" alt-text="Raspberry Pi から BME280 ブレークアウト基板への接続を示す Fritzing 図" lightbox="../media/rpi-bmp280_i2c.png":::

<span data-ttu-id="0d6ab-119">Raspberry Pi から BME280 ブレークアウトへの接続を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-119">The following are the connections from the Raspberry Pi to the BME280 breakout:</span></span>

- <span data-ttu-id="0d6ab-120">3.3V から VIN "*または*" 3V3 へ (赤で表示)</span><span class="sxs-lookup"><span data-stu-id="0d6ab-120">3.3V to VIN *OR* 3V3 (shown in red)</span></span>
- <span data-ttu-id="0d6ab-121">グラウンドから GND へ (黒)</span><span class="sxs-lookup"><span data-stu-id="0d6ab-121">Ground to GND (black)</span></span>
- <span data-ttu-id="0d6ab-122">SDA (GPIO 2) から SDI "*または*" SDA へ (青)</span><span class="sxs-lookup"><span data-stu-id="0d6ab-122">SDA (GPIO 2) to SDI *OR* SDA (blue)</span></span>
- <span data-ttu-id="0d6ab-123">SCL (GPIO 3) から SCK "*または*" SCL へ (オレンジ)</span><span class="sxs-lookup"><span data-stu-id="0d6ab-123">SCL (GPIO 3) to SCK *OR* SCL (orange)</span></span>

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="0d6ab-124">アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="0d6ab-124">Create the app</span></span>

<span data-ttu-id="0d6ab-125">お好みの開発環境で、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-125">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="0d6ab-126">[.NET CLI](../../core/tools/dotnet-new.md) または [Visual Studio](../../core/tutorials/with-visual-studio.md) を使用して、新しい .NET コンソール アプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-126">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="0d6ab-127">「*SensorTutorial*」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-127">Name it *SensorTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o SensorTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="0d6ab-128">*Program.cs* の内容を次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-128">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/SensorTutorial/Program.cs" :::

    <span data-ttu-id="0d6ab-129">上のコードでは以下の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-129">In the preceding code:</span></span>

    - <span data-ttu-id="0d6ab-130">`i2cSettings` が `I2cConnectionSettings` の新しいインスタンスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-130">`i2cSettings` is set to a new instance of `I2cConnectionSettings`.</span></span> <span data-ttu-id="0d6ab-131">コンストラクターによって、`busId` パラメーターが 1 に、`deviceAddress` パラメーターが `Bme280.DefaultI2cAddress` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-131">The constructor sets the `busId` parameter to 1 and the `deviceAddress` parameter to `Bme280.DefaultI2cAddress`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="0d6ab-132">一部の BME280 ブレークアウト製造元では、第 2 のアドレス値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-132">Some BME280 breakout manufacturers use the secondary address value.</span></span> <span data-ttu-id="0d6ab-133">そのようなデバイスに対しては、`Bme280.SecondaryI2cAddress` を使用します。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-133">For those devices, use `Bme280.SecondaryI2cAddress`.</span></span>

    - <span data-ttu-id="0d6ab-134">[using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)により、`I2cDevice.Create` を呼び出して `i2cSettings` を渡すことによって、`I2cDevice` のインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-134">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `I2cDevice` by calling `I2cDevice.Create` and passing in `i2cSettings`.</span></span> <span data-ttu-id="0d6ab-135">この `I2cDevice` は、I2C バスを表しています。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-135">This `I2cDevice` represents the I2C bus.</span></span> <span data-ttu-id="0d6ab-136">この `using` 宣言により、オブジェクトが破棄され、ハードウェア リソースが適切に解放されます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-136">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="0d6ab-137">別の `using` 宣言によって、センサーを表す `Bme280` のインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-137">Another `using` declaration creates an instance of `Bme280` to represent the sensor.</span></span> <span data-ttu-id="0d6ab-138">`I2cDevice` は、コンストラクターで渡されます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-138">The `I2cDevice` is passed in the constructor.</span></span>
    - <span data-ttu-id="0d6ab-139">チップがチップの現在 (既定) の設定で測定を行うために必要な時間は、`GetMeasurementDuration` を呼び出すことによって取得されます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-139">The time required for the chip to take measurements with the chip's current (default) settings is retrieved by calling `GetMeasurementDuration`.</span></span>
    - <span data-ttu-id="0d6ab-140">`while` ループが無期限に実行されます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-140">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="0d6ab-141">それぞれの反復処理で、以下が実行されます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-141">Each iteration:</span></span>
        1. <span data-ttu-id="0d6ab-142">コンソールをクリアします。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-142">Clears the console.</span></span>
        1. <span data-ttu-id="0d6ab-143">電源モードを `Bmx280PowerMode.Forced` に設定します。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-143">Sets the power mode to `Bmx280PowerMode.Forced`.</span></span> <span data-ttu-id="0d6ab-144">これにより、チップで 1 つの測定が実行され、その結果が格納されて、スリープ状態になります。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-144">This forces the chip to perform one measurement, store the results, and then sleep.</span></span>
        1. <span data-ttu-id="0d6ab-145">温度、気圧、湿度、および高度の値を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-145">Reads the values for temperature, pressure, humidity, and altitude.</span></span>

            > [!NOTE]
            > <span data-ttu-id="0d6ab-146">高度はデバイスのバインドによって計算されます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-146">Altitude is calculated by the device binding.</span></span> <span data-ttu-id="0d6ab-147">この `TryReadAltitude` のオーバーロードでは、平均海面気圧を使用して推定値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-147">This overload of `TryReadAltitude` uses mean sea level pressure to generate an estimate.</span></span>

        1. <span data-ttu-id="0d6ab-148">現在の環境条件をコンソールに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-148">Writes the current environmental conditions to the console.</span></span>
        1. <span data-ttu-id="0d6ab-149">1000 ミリ秒スリープします。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-149">Sleeps 1000 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="0d6ab-150">配置ディレクトリに切り替え、実行可能ファイルを実行することで、Raspberry Pi でアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-150">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./SensorTutorial
    ```

    <span data-ttu-id="0d6ab-151">コンソールでセンサーの出力を観察します。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-151">Observe the sensor output in the console.</span></span>

1. <span data-ttu-id="0d6ab-152"><kbd>Ctrl + C</kbd> キーを押してプログラムを終了します。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-152">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="0d6ab-153">おめでとうございます。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-153">Congratulations!</span></span> <span data-ttu-id="0d6ab-154">I2C を使用して、気温、湿度、気圧のセンサーから値を読み取ることができました。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-154">You've used I2C to read values from a temperature/humidity/barometric pressure sensor!</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="0d6ab-155">ソース コードを入手する</span><span class="sxs-lookup"><span data-stu-id="0d6ab-155">Get the source code</span></span>

<span data-ttu-id="0d6ab-156">このチュートリアルのソースは、[GitHub から入手できます](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial)。</span><span class="sxs-lookup"><span data-stu-id="0d6ab-156">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0d6ab-157">次のステップ</span><span class="sxs-lookup"><span data-stu-id="0d6ab-157">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0d6ab-158">LCD にテキストを表示する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="0d6ab-158">Learn how to display text on an LCD</span></span>](../tutorials/lcd-display.md)
