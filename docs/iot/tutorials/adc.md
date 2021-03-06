---
title: アナログ デジタル コンバーターから値を読み取る
description: アナログ-デジタルコンバーターを使用して、可変電圧値を読み取る方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 509616e3423fbb83b74bfbb8ecec1a7df49f0a20
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259742"
---
<!--markdownlint-disable DOCSMD011 -->
# <a name="read-values-from-an-analog-to-digital-converter"></a><span data-ttu-id="bfaf5-103">アナログ デジタル コンバーターから値を読み取る</span><span class="sxs-lookup"><span data-stu-id="bfaf5-103">Read values from an analog-to-digital converter</span></span>

<span data-ttu-id="bfaf5-104">アナログ-デジタルコンバーター (ADC) は、アナログ入力電圧値を読み取り、デジタル値に変換できるデバイスです。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-104">An analog-to-digital converter (ADC) is a device that can read an analog input voltage value and convert it into a digital value.</span></span> <span data-ttu-id="bfaf5-105">ADCs は、特定の条件に基づいて抵抗を変更する thermistors、potentiometers、およびその他のデバイスから値を読み取るために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-105">ADCs are used for reading values from thermistors, potentiometers, and other devices that change resistance based on certain conditions.</span></span>

<span data-ttu-id="bfaf5-106">このトピックでは、potentiometer を使用して入力電圧を乗算するときに、.NET を使用して ADC から値を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-106">In this topic, you will use .NET to read values from an ADC as you modulate the input voltage with a potentiometer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bfaf5-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="bfaf5-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="bfaf5-108">[MCP3008](https://www.microchip.com/wwwproducts/MCP3008) のアナログ/デジタルコンバーター</span><span class="sxs-lookup"><span data-stu-id="bfaf5-108">[MCP3008](https://www.microchip.com/wwwproducts/MCP3008) analog-to-digital converter</span></span>
- <span data-ttu-id="bfaf5-109">3ピン potentiometer</span><span class="sxs-lookup"><span data-stu-id="bfaf5-109">Three-pin potentiometer</span></span>
- <span data-ttu-id="bfaf5-110">ブレッドボード</span><span class="sxs-lookup"><span data-stu-id="bfaf5-110">Breadboard</span></span>
- <span data-ttu-id="bfaf5-111">ジャンパー ワイヤ</span><span class="sxs-lookup"><span data-stu-id="bfaf5-111">Jumper wires</span></span>
- <span data-ttu-id="bfaf5-112">Raspberry Pi GPIO ブレイクボードボード (省略可能/推奨)</span><span class="sxs-lookup"><span data-stu-id="bfaf5-112">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [prepare-pi-spi](../includes/prepare-pi-spi.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="bfaf5-113">ハードウェアを準備する</span><span class="sxs-lookup"><span data-stu-id="bfaf5-113">Prepare the hardware</span></span>

<span data-ttu-id="bfaf5-114">ハードウェアコンポーネントを使用して、次の図に示すように回線を構築します。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-114">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-trimpot_spi-thumb.png" alt-text="MCP3008 ADC と potentiometer がある回線を示す Fritzing 図" lightbox="../media/rpi-trimpot_spi.png":::

<span data-ttu-id="bfaf5-116">MCP3008 は、シリアルペリフェラルインターフェイス (SPI) を使用して通信を行います。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-116">The MCP3008 uses Serial Peripheral Interface (SPI) to communicate.</span></span> <span data-ttu-id="bfaf5-117">MCP3008 から Raspberry Pi と potentiometer への接続は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-117">The following are the connections from the MCP3008 to the Raspberry Pi and potentiometer:</span></span>

- <span data-ttu-id="bfaf5-118">V<sub>DD</sub> から 3.3 v (赤で表示)</span><span class="sxs-lookup"><span data-stu-id="bfaf5-118">V<sub>DD</sub> to 3.3V (shown in red)</span></span>
- <span data-ttu-id="bfaf5-119">V<sub>REF</sub> から 3.3 v (赤)</span><span class="sxs-lookup"><span data-stu-id="bfaf5-119">V<sub>REF</sub> to 3.3V (red)</span></span>
- <span data-ttu-id="bfaf5-120">AGND からグランド (黒)</span><span class="sxs-lookup"><span data-stu-id="bfaf5-120">AGND to ground (black)</span></span>
- <span data-ttu-id="bfaf5-121">CLK から SCLK (オレンジ)</span><span class="sxs-lookup"><span data-stu-id="bfaf5-121">CLK to SCLK (orange)</span></span>
- <span data-ttu-id="bfaf5-122">D<sub>-</sub> 誤 o (オレンジ)</span><span class="sxs-lookup"><span data-stu-id="bfaf5-122">D<sub>OUT</sub> to MISO (orange)</span></span>
- <span data-ttu-id="bfaf5-123">D<sub>IN</sub> mosi (オレンジ色)</span><span class="sxs-lookup"><span data-stu-id="bfaf5-123">D<sub>IN</sub> to MOSI (orange)</span></span>
- <span data-ttu-id="bfaf5-124">CS/SHDN から CE0 (緑)</span><span class="sxs-lookup"><span data-stu-id="bfaf5-124">CS/SHDN to CE0 (green)</span></span>
- <span data-ttu-id="bfaf5-125">DGND から地面 (黒)</span><span class="sxs-lookup"><span data-stu-id="bfaf5-125">DGND to ground (black)</span></span>
- <span data-ttu-id="bfaf5-126">Potentiometer の CH0 (中間) pin (黄)</span><span class="sxs-lookup"><span data-stu-id="bfaf5-126">CH0 to variable (middle) pin on potentiometer (yellow)</span></span>

<span data-ttu-id="bfaf5-127">Potentiometer の外側のピンに 3.3 V とグランドを提供します。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-127">Supply 3.3V and ground to the outer pins on the potentiometer.</span></span> <span data-ttu-id="bfaf5-128">順序は重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-128">Order is unimportant.</span></span>

<span data-ttu-id="bfaf5-129">必要に応じて、次のピンチャートを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-129">Refer to the following pinout diagrams as needed:</span></span>

| <span data-ttu-id="bfaf5-130">MCP3008</span><span class="sxs-lookup"><span data-stu-id="bfaf5-130">MCP3008</span></span>  | <span data-ttu-id="bfaf5-131">Raspberry Pi GPIO</span><span class="sxs-lookup"><span data-stu-id="bfaf5-131">Raspberry Pi GPIO</span></span> |
|----------|-------------------|
| :::image type="content" source="../media/mcp3008-diagram-thumb.png" alt-text="MCP3008 のピンを示す図" lightbox="../media/mcp3008-diagram.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Raspberry Pi GPIO ヘッダーのピンアウトを示す図。イメージの Raspberry Pi Foundation。" lightbox="../media/gpio-pinout-diagram.png":::<br /><span data-ttu-id="bfaf5-134">[イメージの Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/)。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-134">[Image courtesy Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).</span></span>
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="bfaf5-135">アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="bfaf5-135">Create the app</span></span>

<span data-ttu-id="bfaf5-136">お好みの開発環境で、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-136">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="bfaf5-137">[.NET CLI](../../core/tools/dotnet-new.md)または[Visual Studio](../../core/tutorials/with-visual-studio.md)を使用して、新しい .net コンソールアプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-137">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="bfaf5-138">*Adctutorial* に名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-138">Name it *AdcTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o AdcTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="bfaf5-139">*Program.cs* の内容を次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-139">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/AdcTutorial/Program.cs" :::

    <span data-ttu-id="bfaf5-140">上のコードでは以下の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-140">In the preceding code:</span></span>

    - <span data-ttu-id="bfaf5-141">`hardwareSpiSettings` は、の新しいインスタンスに設定され `SpiConnectionSettings` ます。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-141">`hardwareSpiSettings` is set to a new instance of `SpiConnectionSettings`.</span></span> <span data-ttu-id="bfaf5-142">コンストラクターは、 `busId` パラメーターを0に設定し、パラメーターを0に設定し `chipSelectLine` ます。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-142">The constructor sets the `busId` parameter to 0 and the `chipSelectLine` parameter to 0.</span></span>
    - <span data-ttu-id="bfaf5-143">[Using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)は、を `SpiDevice` 呼び出してを渡すことによって、のインスタンスを作成し `SpiDevice.Create` `hardwareSpiSettings` ます。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-143">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `SpiDevice` by calling `SpiDevice.Create` and passing in `hardwareSpiSettings`.</span></span> <span data-ttu-id="bfaf5-144">これ `SpiDevice` は、SPI バスを表します。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-144">This `SpiDevice` represents the SPI bus.</span></span> <span data-ttu-id="bfaf5-145">この `using` 宣言により、オブジェクトが破棄され、ハードウェアリソースが正常に解放されます。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-145">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="bfaf5-146">別 `using` の宣言によってのインスタンスが作成され、 `Mcp3008` が `SpiDevice` コンストラクターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-146">Another `using` declaration creates an instance of `Mcp3008` and passes the `SpiDevice` into the constructor.</span></span>
    - <span data-ttu-id="bfaf5-147">`while`ループは無期限に実行されます。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-147">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="bfaf5-148">各イテレーション:</span><span class="sxs-lookup"><span data-stu-id="bfaf5-148">Each iteration:</span></span>
        1. <span data-ttu-id="bfaf5-149">を呼び出して、ADC の CH0 の値を読み取り `mcp.Read(0)` ます。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-149">Reads the value of CH0 on the ADC by calling `mcp.Read(0)`.</span></span>
        1. <span data-ttu-id="bfaf5-150">値を10.24 で除算します。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-150">Divides the value by 10.24.</span></span> <span data-ttu-id="bfaf5-151">MCP3008 は10ビット ADC です。つまり、0-1023 の範囲で1024の値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-151">The MCP3008 is a 10-bit ADC, which means it returns 1024 possible values ranging 0-1023.</span></span> <span data-ttu-id="bfaf5-152">値を10.24 で割ると、値はパーセンテージで表されます。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-152">Dividing the value by 10.24 represents the value as a percentage.</span></span>
        1. <span data-ttu-id="bfaf5-153">値を最も近い整数に丸めます。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-153">Rounds the value to the nearest integer.</span></span>
        1. <span data-ttu-id="bfaf5-154">値をパーセンテージとして書式設定されたコンソールに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-154">Writes the value to the console formatted as a percentage.</span></span>
        1. <span data-ttu-id="bfaf5-155">500ミリ秒スリープします。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-155">Sleeps 500 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="bfaf5-156">配置ディレクトリに切り替え、実行可能ファイルを実行して、Raspberry Pi でアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-156">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./AdcTutorial
    ```

    <span data-ttu-id="bfaf5-157">Potentiometer ダイヤルを回転させながら出力を観察します。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-157">Observe the output as you rotate the potentiometer dial.</span></span> <span data-ttu-id="bfaf5-158">これは、potentiometer によって、ADC の CH0 に提供される電圧が変化するためです。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-158">This is due to the potentiometer varying the voltage supplied to CH0 on the ADC.</span></span> <span data-ttu-id="bfaf5-159">ADC は、CH0 の入力電圧を V<sub>REF</sub> に指定された参照電圧と比較して、値を生成します。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-159">The ADC compares the input voltage on CH0 to the reference voltage supplied to V<sub>REF</sub> to generate a value.</span></span>

1. <span data-ttu-id="bfaf5-160"><kbd>Ctrl + C</kbd>キーを押してプログラムを終了します。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-160">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="bfaf5-161">おめでとうございます。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-161">Congratulations!</span></span> <span data-ttu-id="bfaf5-162">SPI を使用して、アナログからデジタルへのコンバーターから値を読み取りました。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-162">You've used SPI to read values from an analog-to-digital converter.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="bfaf5-163">ソース コードを入手する</span><span class="sxs-lookup"><span data-stu-id="bfaf5-163">Get the source code</span></span>

<span data-ttu-id="bfaf5-164">このチュートリアルのソースは、 [GitHub で入手でき](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial)ます。</span><span class="sxs-lookup"><span data-stu-id="bfaf5-164">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial).</span></span>

## <a name="next-steps"></a><span data-ttu-id="bfaf5-165">次のステップ</span><span class="sxs-lookup"><span data-stu-id="bfaf5-165">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bfaf5-166">General Purpose 入力/出力を使用して LED を点滅させる方法について説明します</span><span class="sxs-lookup"><span data-stu-id="bfaf5-166">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
