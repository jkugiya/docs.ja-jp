---
title: LCD にテキストを表示する
description: .NET IoT ライブラリを使用して液晶ディスプレイに文字を表示する方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 005b40a7d9f46b84fcd90541248f5f4fd243e612
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "102255536"
---
<!--markdownlint-disable DOCSMD011 -->
# <a name="display-text-on-an-lcd"></a><span data-ttu-id="6c239-103">LCD にテキストを表示する</span><span class="sxs-lookup"><span data-stu-id="6c239-103">Display text on an LCD</span></span>

<span data-ttu-id="6c239-104">LCD 文字ディスプレイは、外部モニターを必要とせずに情報を表示する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="6c239-104">LCD character displays are useful for displaying information without the need for an external monitor.</span></span> <span data-ttu-id="6c239-105">一般的な LCD 文字ディスプレイは GPIO ピンに直接接続できますが、そのような方法では最大 10 個の GPIO ピンを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c239-105">Common LCD character displays can be connected directly to the GPIO pins, but such an approach requires the use of up to 10 GPIO pins.</span></span> <span data-ttu-id="6c239-106">複数のデバイスの組み合わせに接続する必要があるシナリオでは、多くの場合、文字ディスプレイにそれほど多くの GPIO ヘッダーを充てるのは実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="6c239-106">For scenarios that require connecting to a combination of devices, devoting so much of the GPIO header to a character display is often impractical.</span></span>

<span data-ttu-id="6c239-107">多くの製造元では、20x4 の LCD 文字ディスプレイと一体化された GPIO エキスパンダーが販売されています。</span><span class="sxs-lookup"><span data-stu-id="6c239-107">Many manufacturers sell 20x4 LCD character displays with an integrated GPIO expander.</span></span> <span data-ttu-id="6c239-108">文字ディスプレイを GPIO エキスパンダーに直接接続し、次にそれを Inter-Integrated Circuit (I2C) シリアル プロトコルを介して Raspberry Pi に接続します。</span><span class="sxs-lookup"><span data-stu-id="6c239-108">The character display connects directly to the GPIO expander, which then connects to the Raspberry Pi via the Inter-Integrated Circuit (I2C) serial protocol.</span></span>

<span data-ttu-id="6c239-109">このトピックでは、.NET を使用して、I2C GPIO エキスパンダーを使用した LCD 文字ディスプレイにテキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="6c239-109">In this topic, you will use .NET to display text on an LCD character display using an I2C GPIO expander.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6c239-110">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6c239-110">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [<span data-ttu-id="6c239-111">I2C インターフェイスを備えた 20x4 の LCD 文字ディスプレイ</span><span class="sxs-lookup"><span data-stu-id="6c239-111">20x4 LCD Character Display with I2C interface</span></span>](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c)
- <span data-ttu-id="6c239-112">ジャンパー ワイヤ</span><span class="sxs-lookup"><span data-stu-id="6c239-112">Jumper wires</span></span>
- <span data-ttu-id="6c239-113">ブレッドボード (省略可能、推奨)</span><span class="sxs-lookup"><span data-stu-id="6c239-113">Breadboard (optional/recommended)</span></span>
- <span data-ttu-id="6c239-114">Raspberry Pi GPIO ブレークアウト基板 (省略可能、推奨)</span><span class="sxs-lookup"><span data-stu-id="6c239-114">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!NOTE]
> <span data-ttu-id="6c239-115">LCD 文字ディスプレイの製造元は多数あります。</span><span class="sxs-lookup"><span data-stu-id="6c239-115">There are many manufacturers of LCD character displays.</span></span> <span data-ttu-id="6c239-116">ほとんどの設計は同一であり、製造元が異なる機能を用意することはないはずです。</span><span class="sxs-lookup"><span data-stu-id="6c239-116">Most designs are identical, and the manufacturer shouldn't make any difference to the functionality.</span></span> <span data-ttu-id="6c239-117">参考までに、このチュートリアルは [SunFounder LCD2004](https://www.sunfounder.com/lcd2004-module.html) を使用して作成されました。</span><span class="sxs-lookup"><span data-stu-id="6c239-117">For reference, this tutorial was developed with the [SunFounder LCD2004](https://www.sunfounder.com/lcd2004-module.html).</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="6c239-118">ハードウェアを準備する</span><span class="sxs-lookup"><span data-stu-id="6c239-118">Prepare the hardware</span></span>

<span data-ttu-id="6c239-119">ジャンパー ワイヤを使用して、次のように I2C GPIO エキスパンダーの 4 つのピンを Raspberry Pi に接続します。</span><span class="sxs-lookup"><span data-stu-id="6c239-119">Use jumper wires to connect the four pins on the I2C GPIO expander to the Raspberry Pi as follows:</span></span>

- <span data-ttu-id="6c239-120">GND からグラウンドへ</span><span class="sxs-lookup"><span data-stu-id="6c239-120">GND to ground</span></span>
- <span data-ttu-id="6c239-121">VCC から 5V へ</span><span class="sxs-lookup"><span data-stu-id="6c239-121">VCC to 5V</span></span>
- <span data-ttu-id="6c239-122">SDA から SDA (GPIO 2) へ</span><span class="sxs-lookup"><span data-stu-id="6c239-122">SDA to SDA (GPIO 2)</span></span>
- <span data-ttu-id="6c239-123">SCL から SCL (GPIO 3) へ</span><span class="sxs-lookup"><span data-stu-id="6c239-123">SCL to SCL (GPIO 3)</span></span>

<span data-ttu-id="6c239-124">必要に応じて、次の図を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c239-124">Refer to the following figures as needed:</span></span>

| <span data-ttu-id="6c239-125">I2C インターフェイス (ディスプレイの背面)</span><span class="sxs-lookup"><span data-stu-id="6c239-125">I2C interface (back of display)</span></span> | <span data-ttu-id="6c239-126">Raspberry Pi GPIO</span><span class="sxs-lookup"><span data-stu-id="6c239-126">Raspberry Pi GPIO</span></span> |
|---------------------------------|-------------------|
| :::image type="content" source="../media/character-display-i2c-thumb.png" alt-text="I2C GPIO エキスパンダーを示す文字ディスプレイの背面の画像。" lightbox="../media/character-display-i2c.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Raspberry Pi GPIO ヘッダーのピン配列を示す図。画像提供: Raspberry Pi Foundation。" lightbox="../media/gpio-pinout-diagram.png":::<br /><span data-ttu-id="6c239-129">[画像提供: Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/)。</span><span class="sxs-lookup"><span data-stu-id="6c239-129">[Image courtesy Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).</span></span>
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="6c239-130">アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="6c239-130">Create the app</span></span>

<span data-ttu-id="6c239-131">お好みの開発環境で、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="6c239-131">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="6c239-132">[.NET CLI](../../core/tools/dotnet-new.md) または [Visual Studio](../../core/tutorials/with-visual-studio.md) を使用して、新しい .NET コンソール アプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="6c239-132">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="6c239-133">「*LcdTutorial*」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="6c239-133">Name it *LcdTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o LcdTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="6c239-134">*Program.cs* の内容を次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="6c239-134">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/LcdTutorial/Program.cs" :::

    <span data-ttu-id="6c239-135">上のコードでは以下の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="6c239-135">In the preceding code:</span></span>

    - <span data-ttu-id="6c239-136">[using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)により、`I2cDevice.Create` を呼び出して `busId` および `deviceAddress` パラメーターと共に新しい `I2cConnectionSettings` を渡すことによって、`I2cDevice` のインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6c239-136">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `I2cDevice` by calling `I2cDevice.Create` and passing in a new `I2cConnectionSettings` with the `busId` and `deviceAddress` parameters.</span></span> <span data-ttu-id="6c239-137">この `I2cDevice` は、I2C バスを表しています。</span><span class="sxs-lookup"><span data-stu-id="6c239-137">This `I2cDevice` represents the I2C bus.</span></span> <span data-ttu-id="6c239-138">この `using` 宣言により、オブジェクトが破棄され、ハードウェア リソースが適切に解放されます。</span><span class="sxs-lookup"><span data-stu-id="6c239-138">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>

        > [!WARNING]
        > <span data-ttu-id="6c239-139">GPIO エキスパンダーのデバイス アドレスは、製造元によって使用されるチップによって異なります。</span><span class="sxs-lookup"><span data-stu-id="6c239-139">The device address for the GPIO expander depends on the chip used by the manufacturer.</span></span> <span data-ttu-id="6c239-140">PCF8574 を備えた GPIO エキスパンダーではアドレス `0x27` が使用されます。一方、PCF8574A チップを使用するものの場合は `0x3F` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6c239-140">GPIO expanders equipped with a PCF8574 use the address `0x27`, while those using PCF8574A chips use `0x3F`.</span></span> <span data-ttu-id="6c239-141">使用する LCD のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c239-141">Consult your LCD's documentation.</span></span>

    - <span data-ttu-id="6c239-142">別の `using` 宣言では、`Pcf8574` のインスタンスが作成され、コンストラクターに `I2cDevice` が渡されます。</span><span class="sxs-lookup"><span data-stu-id="6c239-142">Another `using` declaration creates an instance of `Pcf8574` and passes the `I2cDevice` into the constructor.</span></span> <span data-ttu-id="6c239-143">このインスタンスは、GPIO エキスパンダーを表しています。</span><span class="sxs-lookup"><span data-stu-id="6c239-143">This instance represents the GPIO expander.</span></span>
    - <span data-ttu-id="6c239-144">別の `using` 宣言によって、ディスプレイを表す `Lcd2004` のインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6c239-144">Another `using` declaration creates an instance of `Lcd2004` to represent the display.</span></span> <span data-ttu-id="6c239-145">いくつかのパラメーターがコンストラクターに渡され、GPIO エキスパンダーとの通信に使用する設定が記述されています。</span><span class="sxs-lookup"><span data-stu-id="6c239-145">Several parameters are passed to the constructor describing the settings to use to communicate with the GPIO expander.</span></span> <span data-ttu-id="6c239-146">GPIO エキスパンダーは `controller` パラメーターとして渡されています。</span><span class="sxs-lookup"><span data-stu-id="6c239-146">The GPIO expander is passed as the `controller` parameter.</span></span>
    - <span data-ttu-id="6c239-147">`while` ループが無期限に実行されます。</span><span class="sxs-lookup"><span data-stu-id="6c239-147">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="6c239-148">それぞれの反復処理で、以下が実行されます。</span><span class="sxs-lookup"><span data-stu-id="6c239-148">Each iteration:</span></span>
        1. <span data-ttu-id="6c239-149">ディスプレイをクリアします。</span><span class="sxs-lookup"><span data-stu-id="6c239-149">Clears the display.</span></span>
        1. <span data-ttu-id="6c239-150">カーソル位置を、現在の行の最初の位置に設定します。</span><span class="sxs-lookup"><span data-stu-id="6c239-150">Sets the cursor position to the first position on the current line.</span></span>
        1. <span data-ttu-id="6c239-151">ディスプレイの現在のカーソル位置に、現在時刻を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="6c239-151">Writes the current time to the display at the current cursor position.</span></span>
        1. <span data-ttu-id="6c239-152">現在の行カウンターを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="6c239-152">Iterates the current line counter.</span></span>
        1. <span data-ttu-id="6c239-153">1000 ミリ秒スリープします。</span><span class="sxs-lookup"><span data-stu-id="6c239-153">Sleeps 1000 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="6c239-154">配置ディレクトリに切り替え、実行可能ファイルを実行することで、Raspberry Pi でアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="6c239-154">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./LcdTutorial
    ```

    <span data-ttu-id="6c239-155">LCD 文字ディスプレイの各行に現在の時刻が表示される様子を観察します。</span><span class="sxs-lookup"><span data-stu-id="6c239-155">Observe the LCD character display as the current time displays on each line.</span></span>

    > [!TIP]
    > <span data-ttu-id="6c239-156">ディスプレイは点灯するがテキストが表示されない場合は、ディスプレイの背面でコントラストの目盛りを調整してみてください。</span><span class="sxs-lookup"><span data-stu-id="6c239-156">If the display is lit but you don't see any text, try adjusting the contrast dial on the back of the display.</span></span>

1. <span data-ttu-id="6c239-157"><kbd>Ctrl + C</kbd> キーを押してプログラムを終了します。</span><span class="sxs-lookup"><span data-stu-id="6c239-157">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="6c239-158">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="6c239-158">Congratulations!</span></span> <span data-ttu-id="6c239-159">I2C と GPIO エキスパンダーを使用して、LCD にテキストを表示することができました。</span><span class="sxs-lookup"><span data-stu-id="6c239-159">You've displayed text on an LCD using a I2C and a GPIO expander!</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="6c239-160">ソース コードを入手する</span><span class="sxs-lookup"><span data-stu-id="6c239-160">Get the source code</span></span>

<span data-ttu-id="6c239-161">このチュートリアルのソースは、[GitHub から入手できます](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial)。</span><span class="sxs-lookup"><span data-stu-id="6c239-161">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial).</span></span>

## <a name="next-steps"></a><span data-ttu-id="6c239-162">次の手順</span><span class="sxs-lookup"><span data-stu-id="6c239-162">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6c239-163">汎用入出力を使用して LED を点滅させる方法を学習する</span><span class="sxs-lookup"><span data-stu-id="6c239-163">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
