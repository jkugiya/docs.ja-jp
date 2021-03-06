---
title: LCD にテキストを表示する
description: .NET IoT ライブラリを使用して液晶ディスプレイに文字を表示する方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 005b40a7d9f46b84fcd90541248f5f4fd243e612
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255536"
---
<!--markdownlint-disable DOCSMD011 -->
# <a name="display-text-on-an-lcd"></a><span data-ttu-id="eb212-103">LCD にテキストを表示する</span><span class="sxs-lookup"><span data-stu-id="eb212-103">Display text on an LCD</span></span>

<span data-ttu-id="eb212-104">LCD 文字ディスプレイは、外部モニターを必要とせずに情報を表示する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="eb212-104">LCD character displays are useful for displaying information without the need for an external monitor.</span></span> <span data-ttu-id="eb212-105">一般的な LCD 文字ディスプレイは、GPIO ピンに直接接続できますが、このようなアプローチでは、最大10個の GPIO ピンを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb212-105">Common LCD character displays can be connected directly to the GPIO pins, but such an approach requires the use of up to 10 GPIO pins.</span></span> <span data-ttu-id="eb212-106">デバイスの組み合わせに接続する必要があるシナリオでは、多くの場合、GPIO ヘッダーの大部分を文字表示に取り上げことは現実的ではありません。</span><span class="sxs-lookup"><span data-stu-id="eb212-106">For scenarios that require connecting to a combination of devices, devoting so much of the GPIO header to a character display is often impractical.</span></span>

<span data-ttu-id="eb212-107">多くの製造元は、20x4 LCD 文字ディスプレイと統合された GPIO を販売しています。</span><span class="sxs-lookup"><span data-stu-id="eb212-107">Many manufacturers sell 20x4 LCD character displays with an integrated GPIO expander.</span></span> <span data-ttu-id="eb212-108">文字表示は、GPIO エキスパンダーに直接接続し、その後、Inter-Integrated 回線 (I2C) シリアルプロトコルを介して Raspberry Pi に接続します。</span><span class="sxs-lookup"><span data-stu-id="eb212-108">The character display connects directly to the GPIO expander, which then connects to the Raspberry Pi via the Inter-Integrated Circuit (I2C) serial protocol.</span></span>

<span data-ttu-id="eb212-109">このトピックでは、.NET を使用して、I2C GPIO 展開を使用して LCD 文字ディスプレイにテキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="eb212-109">In this topic, you will use .NET to display text on an LCD character display using an I2C GPIO expander.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eb212-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="eb212-110">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [<span data-ttu-id="eb212-111">20x4 I2C インターフェイスを使用した LCD 文字表示</span><span class="sxs-lookup"><span data-stu-id="eb212-111">20x4 LCD Character Display with I2C interface</span></span>](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c)
- <span data-ttu-id="eb212-112">ジャンパー ワイヤ</span><span class="sxs-lookup"><span data-stu-id="eb212-112">Jumper wires</span></span>
- <span data-ttu-id="eb212-113">ブレッドボード (省略可能/推奨)</span><span class="sxs-lookup"><span data-stu-id="eb212-113">Breadboard (optional/recommended)</span></span>
- <span data-ttu-id="eb212-114">Raspberry Pi GPIO ブレイクボードボード (省略可能/推奨)</span><span class="sxs-lookup"><span data-stu-id="eb212-114">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!NOTE]
> <span data-ttu-id="eb212-115">多くの製造元が LCD 文字を表示しています。</span><span class="sxs-lookup"><span data-stu-id="eb212-115">There are many manufacturers of LCD character displays.</span></span> <span data-ttu-id="eb212-116">ほとんどの設計は同一であり、製造元は機能に違いを持たせることはできません。</span><span class="sxs-lookup"><span data-stu-id="eb212-116">Most designs are identical, and the manufacturer shouldn't make any difference to the functionality.</span></span> <span data-ttu-id="eb212-117">参考までに、このチュートリアルは [SUNFOUNDER LCD2004](https://www.sunfounder.com/lcd2004-module.html)を使用して開発されました。</span><span class="sxs-lookup"><span data-stu-id="eb212-117">For reference, this tutorial was developed with the [SunFounder LCD2004](https://www.sunfounder.com/lcd2004-module.html).</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="eb212-118">ハードウェアを準備する</span><span class="sxs-lookup"><span data-stu-id="eb212-118">Prepare the hardware</span></span>

<span data-ttu-id="eb212-119">ジャンパー回線を使用して、次のように、I2C GPIO エキスパンダーの4つのピンを Raspberry Pi に接続します。</span><span class="sxs-lookup"><span data-stu-id="eb212-119">Use jumper wires to connect the four pins on the I2C GPIO expander to the Raspberry Pi as follows:</span></span>

- <span data-ttu-id="eb212-120">GND を地面に</span><span class="sxs-lookup"><span data-stu-id="eb212-120">GND to ground</span></span>
- <span data-ttu-id="eb212-121">VCC 5V</span><span class="sxs-lookup"><span data-stu-id="eb212-121">VCC to 5V</span></span>
- <span data-ttu-id="eb212-122">SDA SDA (GPIO 2)</span><span class="sxs-lookup"><span data-stu-id="eb212-122">SDA to SDA (GPIO 2)</span></span>
- <span data-ttu-id="eb212-123">SCL から SCL へ (GPIO 3)</span><span class="sxs-lookup"><span data-stu-id="eb212-123">SCL to SCL (GPIO 3)</span></span>

<span data-ttu-id="eb212-124">必要に応じて、次の図を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb212-124">Refer to the following figures as needed:</span></span>

| <span data-ttu-id="eb212-125">I2C インターフェイス (ディスプレイの背面)</span><span class="sxs-lookup"><span data-stu-id="eb212-125">I2C interface (back of display)</span></span> | <span data-ttu-id="eb212-126">Raspberry Pi GPIO</span><span class="sxs-lookup"><span data-stu-id="eb212-126">Raspberry Pi GPIO</span></span> |
|---------------------------------|-------------------|
| :::image type="content" source="../media/character-display-i2c-thumb.png" alt-text="I2C GPIO エキスパンダーを示す文字表示の背面の画像。" lightbox="../media/character-display-i2c.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Raspberry Pi GPIO ヘッダーのピンアウトを示す図。イメージの Raspberry Pi Foundation。" lightbox="../media/gpio-pinout-diagram.png":::<br /><span data-ttu-id="eb212-129">[イメージの Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/)。</span><span class="sxs-lookup"><span data-stu-id="eb212-129">[Image courtesy Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).</span></span>
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="eb212-130">アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="eb212-130">Create the app</span></span>

<span data-ttu-id="eb212-131">お好みの開発環境で、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="eb212-131">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="eb212-132">[.NET CLI](../../core/tools/dotnet-new.md)または[Visual Studio](../../core/tutorials/with-visual-studio.md)を使用して、新しい .net コンソールアプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="eb212-132">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="eb212-133">*Lcdtutorial* という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="eb212-133">Name it *LcdTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o LcdTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="eb212-134">*Program.cs* の内容を次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="eb212-134">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/LcdTutorial/Program.cs" :::

    <span data-ttu-id="eb212-135">上のコードでは以下の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="eb212-135">In the preceding code:</span></span>

    - <span data-ttu-id="eb212-136">[Using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)は、を `I2cDevice` 呼び出し `I2cDevice.Create` 、 `I2cConnectionSettings` パラメーターとパラメーターを使用して新しいを渡すことによって、のインスタンスを作成し `busId` `deviceAddress` ます。</span><span class="sxs-lookup"><span data-stu-id="eb212-136">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `I2cDevice` by calling `I2cDevice.Create` and passing in a new `I2cConnectionSettings` with the `busId` and `deviceAddress` parameters.</span></span> <span data-ttu-id="eb212-137">これ `I2cDevice` は、I2C バスを表します。</span><span class="sxs-lookup"><span data-stu-id="eb212-137">This `I2cDevice` represents the I2C bus.</span></span> <span data-ttu-id="eb212-138">この `using` 宣言により、オブジェクトが破棄され、ハードウェアリソースが正常に解放されます。</span><span class="sxs-lookup"><span data-stu-id="eb212-138">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>

        > [!WARNING]
        > <span data-ttu-id="eb212-139">GPIO エキスパンダーのデバイスアドレスは、製造元が使用するチップによって異なります。</span><span class="sxs-lookup"><span data-stu-id="eb212-139">The device address for the GPIO expander depends on the chip used by the manufacturer.</span></span> <span data-ttu-id="eb212-140">PCF8574 を装備した GPIO 展開コントロールはアドレスを使用し、PCF8574A チップを使用する GPIO はを `0x27` 使用し `0x3F` ます。</span><span class="sxs-lookup"><span data-stu-id="eb212-140">GPIO expanders equipped with a PCF8574 use the address `0x27`, while those using PCF8574A chips use `0x3F`.</span></span> <span data-ttu-id="eb212-141">LCD のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb212-141">Consult your LCD's documentation.</span></span>

    - <span data-ttu-id="eb212-142">別 `using` の宣言によってのインスタンスが作成され、 `Pcf8574` が `I2cDevice` コンストラクターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="eb212-142">Another `using` declaration creates an instance of `Pcf8574` and passes the `I2cDevice` into the constructor.</span></span> <span data-ttu-id="eb212-143">このインスタンスは、GPIO 展開を表します。</span><span class="sxs-lookup"><span data-stu-id="eb212-143">This instance represents the GPIO expander.</span></span>
    - <span data-ttu-id="eb212-144">別 `using` の宣言 `Lcd2004` によって、表示を表すのインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="eb212-144">Another `using` declaration creates an instance of `Lcd2004` to represent the display.</span></span> <span data-ttu-id="eb212-145">いくつかのパラメーターは、GPIO 展開との通信に使用する設定を記述するコンストラクターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="eb212-145">Several parameters are passed to the constructor describing the settings to use to communicate with the GPIO expander.</span></span> <span data-ttu-id="eb212-146">GPIO エキスパンダーはパラメーターとして渡され `controller` ます。</span><span class="sxs-lookup"><span data-stu-id="eb212-146">The GPIO expander is passed as the `controller` parameter.</span></span>
    - <span data-ttu-id="eb212-147">`while`ループは無期限に実行されます。</span><span class="sxs-lookup"><span data-stu-id="eb212-147">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="eb212-148">各イテレーション:</span><span class="sxs-lookup"><span data-stu-id="eb212-148">Each iteration:</span></span>
        1. <span data-ttu-id="eb212-149">ディスプレイをクリアします。</span><span class="sxs-lookup"><span data-stu-id="eb212-149">Clears the display.</span></span>
        1. <span data-ttu-id="eb212-150">カーソル位置を現在の行の最初の位置に設定します。</span><span class="sxs-lookup"><span data-stu-id="eb212-150">Sets the cursor position to the first position on the current line.</span></span>
        1. <span data-ttu-id="eb212-151">現在のカーソル位置にあるディスプレイに現在の時刻を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="eb212-151">Writes the current time to the display at the current cursor position.</span></span>
        1. <span data-ttu-id="eb212-152">現在の行カウンターを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="eb212-152">Iterates the current line counter.</span></span>
        1. <span data-ttu-id="eb212-153">1000ミリ秒スリープします。</span><span class="sxs-lookup"><span data-stu-id="eb212-153">Sleeps 1000 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="eb212-154">配置ディレクトリに切り替え、実行可能ファイルを実行して、Raspberry Pi でアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="eb212-154">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./LcdTutorial
    ```

    <span data-ttu-id="eb212-155">現在の時刻が各行に表示されているときに、LCD 文字の表示を観察します。</span><span class="sxs-lookup"><span data-stu-id="eb212-155">Observe the LCD character display as the current time displays on each line.</span></span>

    > [!TIP]
    > <span data-ttu-id="eb212-156">ディスプレイが点灯してもテキストが表示されない場合は、ディスプレイの背面でコントラストを調整してみてください。</span><span class="sxs-lookup"><span data-stu-id="eb212-156">If the display is lit but you don't see any text, try adjusting the contrast dial on the back of the display.</span></span>

1. <span data-ttu-id="eb212-157"><kbd>Ctrl + C</kbd>キーを押してプログラムを終了します。</span><span class="sxs-lookup"><span data-stu-id="eb212-157">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="eb212-158">おめでとうございます。</span><span class="sxs-lookup"><span data-stu-id="eb212-158">Congratulations!</span></span> <span data-ttu-id="eb212-159">I2C と GPIO の展開を使用して、LCD にテキストを表示しました。</span><span class="sxs-lookup"><span data-stu-id="eb212-159">You've displayed text on an LCD using a I2C and a GPIO expander!</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="eb212-160">ソース コードを入手する</span><span class="sxs-lookup"><span data-stu-id="eb212-160">Get the source code</span></span>

<span data-ttu-id="eb212-161">このチュートリアルのソースは、 [GitHub で入手でき](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial)ます。</span><span class="sxs-lookup"><span data-stu-id="eb212-161">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial).</span></span>

## <a name="next-steps"></a><span data-ttu-id="eb212-162">次のステップ</span><span class="sxs-lookup"><span data-stu-id="eb212-162">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eb212-163">General Purpose 入力/出力を使用して LED を点滅させる方法について説明します</span><span class="sxs-lookup"><span data-stu-id="eb212-163">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
