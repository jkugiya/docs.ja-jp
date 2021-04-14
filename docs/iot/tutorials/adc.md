---
title: アナログ デジタル コンバーターから値を読み取る
description: アナログ デジタル コンバーターを使用して、可変電圧の値を読み取る方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 509616e3423fbb83b74bfbb8ecec1a7df49f0a20
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "102259742"
---
<!--markdownlint-disable DOCSMD011 -->
# <a name="read-values-from-an-analog-to-digital-converter"></a><span data-ttu-id="d921e-103">アナログ デジタル コンバーターから値を読み取る</span><span class="sxs-lookup"><span data-stu-id="d921e-103">Read values from an analog-to-digital converter</span></span>

<span data-ttu-id="d921e-104">アナログ デジタル コンバーター (ADC) は、アナログの入力電圧値を読み取り、デジタル値に変換できるデバイスです。</span><span class="sxs-lookup"><span data-stu-id="d921e-104">An analog-to-digital converter (ADC) is a device that can read an analog input voltage value and convert it into a digital value.</span></span> <span data-ttu-id="d921e-105">ADC は、特定の条件に基づいて抵抗が変化するサーミスター、ポテンショメーター、およびその他のデバイスから値を読み取るために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d921e-105">ADCs are used for reading values from thermistors, potentiometers, and other devices that change resistance based on certain conditions.</span></span>

<span data-ttu-id="d921e-106">このトピックでは、ポテンショメーターを使用して入力電圧を変化させながら、.NET を使用して ADC から値を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="d921e-106">In this topic, you will use .NET to read values from an ADC as you modulate the input voltage with a potentiometer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d921e-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="d921e-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="d921e-108">[MCP3008](https://www.microchip.com/wwwproducts/MCP3008) アナログ デジタル コンバーター</span><span class="sxs-lookup"><span data-stu-id="d921e-108">[MCP3008](https://www.microchip.com/wwwproducts/MCP3008) analog-to-digital converter</span></span>
- <span data-ttu-id="d921e-109">3 ピン ポテンショメーター</span><span class="sxs-lookup"><span data-stu-id="d921e-109">Three-pin potentiometer</span></span>
- <span data-ttu-id="d921e-110">ブレッドボード</span><span class="sxs-lookup"><span data-stu-id="d921e-110">Breadboard</span></span>
- <span data-ttu-id="d921e-111">ジャンパー ワイヤ</span><span class="sxs-lookup"><span data-stu-id="d921e-111">Jumper wires</span></span>
- <span data-ttu-id="d921e-112">Raspberry Pi GPIO ブレークアウト基板 (省略可能、推奨)</span><span class="sxs-lookup"><span data-stu-id="d921e-112">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [prepare-pi-spi](../includes/prepare-pi-spi.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="d921e-113">ハードウェアを準備する</span><span class="sxs-lookup"><span data-stu-id="d921e-113">Prepare the hardware</span></span>

<span data-ttu-id="d921e-114">ハードウェア コンポーネントを使用して、次の図に示すような回路を構築します。</span><span class="sxs-lookup"><span data-stu-id="d921e-114">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-trimpot_spi-thumb.png" alt-text="MCP3008 ADC とポテンショメーターがある回路を示す Fritzing 図" lightbox="../media/rpi-trimpot_spi.png":::

<span data-ttu-id="d921e-116">MCP3008 では、シリアル周辺機器インターフェイス (SPI) を使用して通信を行います。</span><span class="sxs-lookup"><span data-stu-id="d921e-116">The MCP3008 uses Serial Peripheral Interface (SPI) to communicate.</span></span> <span data-ttu-id="d921e-117">MCP3008 から Raspberry Pi およびポテンショメーターへの接続は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d921e-117">The following are the connections from the MCP3008 to the Raspberry Pi and potentiometer:</span></span>

- <span data-ttu-id="d921e-118">V<sub>DD</sub> から 3.3V へ (赤で表示)</span><span class="sxs-lookup"><span data-stu-id="d921e-118">V<sub>DD</sub> to 3.3V (shown in red)</span></span>
- <span data-ttu-id="d921e-119">V<sub>REF</sub> から 3.3V へ (赤)</span><span class="sxs-lookup"><span data-stu-id="d921e-119">V<sub>REF</sub> to 3.3V (red)</span></span>
- <span data-ttu-id="d921e-120">AGND からグラウンドへ (黒)</span><span class="sxs-lookup"><span data-stu-id="d921e-120">AGND to ground (black)</span></span>
- <span data-ttu-id="d921e-121">CLK から SCLK へ (オレンジ)</span><span class="sxs-lookup"><span data-stu-id="d921e-121">CLK to SCLK (orange)</span></span>
- <span data-ttu-id="d921e-122">D<sub>OUT</sub> から MISO へ (オレンジ)</span><span class="sxs-lookup"><span data-stu-id="d921e-122">D<sub>OUT</sub> to MISO (orange)</span></span>
- <span data-ttu-id="d921e-123">D<sub>IN</sub> から MOSI へ (オレンジ)</span><span class="sxs-lookup"><span data-stu-id="d921e-123">D<sub>IN</sub> to MOSI (orange)</span></span>
- <span data-ttu-id="d921e-124">CS/SHDN から CE0 へ (緑)</span><span class="sxs-lookup"><span data-stu-id="d921e-124">CS/SHDN to CE0 (green)</span></span>
- <span data-ttu-id="d921e-125">DGND からグラウンドへ (黒)</span><span class="sxs-lookup"><span data-stu-id="d921e-125">DGND to ground (black)</span></span>
- <span data-ttu-id="d921e-126">CH0 からポテンショメーターの可変 (中央) ピンへ (黄色)</span><span class="sxs-lookup"><span data-stu-id="d921e-126">CH0 to variable (middle) pin on potentiometer (yellow)</span></span>

<span data-ttu-id="d921e-127">ポテンショメーターの外側のピンに、3.3V とグラウンドを供給します。</span><span class="sxs-lookup"><span data-stu-id="d921e-127">Supply 3.3V and ground to the outer pins on the potentiometer.</span></span> <span data-ttu-id="d921e-128">順序は重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="d921e-128">Order is unimportant.</span></span>

<span data-ttu-id="d921e-129">必要に応じて、次のピン配列図を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d921e-129">Refer to the following pinout diagrams as needed:</span></span>

| <span data-ttu-id="d921e-130">MCP3008</span><span class="sxs-lookup"><span data-stu-id="d921e-130">MCP3008</span></span>  | <span data-ttu-id="d921e-131">Raspberry Pi GPIO</span><span class="sxs-lookup"><span data-stu-id="d921e-131">Raspberry Pi GPIO</span></span> |
|----------|-------------------|
| :::image type="content" source="../media/mcp3008-diagram-thumb.png" alt-text="MCP3008 のピン配列を示す図" lightbox="../media/mcp3008-diagram.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Raspberry Pi GPIO ヘッダーのピン配列を示す図。画像提供: Raspberry Pi Foundation。" lightbox="../media/gpio-pinout-diagram.png":::<br /><span data-ttu-id="d921e-134">[画像提供: Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/)。</span><span class="sxs-lookup"><span data-stu-id="d921e-134">[Image courtesy Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).</span></span>
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="d921e-135">アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="d921e-135">Create the app</span></span>

<span data-ttu-id="d921e-136">お好みの開発環境で、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d921e-136">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="d921e-137">[.NET CLI](../../core/tools/dotnet-new.md) または [Visual Studio](../../core/tutorials/with-visual-studio.md) を使用して、新しい .NET コンソール アプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="d921e-137">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="d921e-138">「*AdcTutorial*」という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="d921e-138">Name it *AdcTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o AdcTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="d921e-139">*Program.cs* の内容を次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d921e-139">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/AdcTutorial/Program.cs" :::

    <span data-ttu-id="d921e-140">上のコードでは以下の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="d921e-140">In the preceding code:</span></span>

    - <span data-ttu-id="d921e-141">`hardwareSpiSettings` が `SpiConnectionSettings` の新しいインスタンスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="d921e-141">`hardwareSpiSettings` is set to a new instance of `SpiConnectionSettings`.</span></span> <span data-ttu-id="d921e-142">コンストラクターによって、`busId` パラメーターが 0 に、`chipSelectLine` パラメーターが 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d921e-142">The constructor sets the `busId` parameter to 0 and the `chipSelectLine` parameter to 0.</span></span>
    - <span data-ttu-id="d921e-143">[using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)により、`SpiDevice.Create` を呼び出して `hardwareSpiSettings` を渡すことによって、`SpiDevice` のインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d921e-143">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `SpiDevice` by calling `SpiDevice.Create` and passing in `hardwareSpiSettings`.</span></span> <span data-ttu-id="d921e-144">この `SpiDevice` は、SPI バスを表しています。</span><span class="sxs-lookup"><span data-stu-id="d921e-144">This `SpiDevice` represents the SPI bus.</span></span> <span data-ttu-id="d921e-145">この `using` 宣言により、オブジェクトが破棄され、ハードウェア リソースが適切に解放されます。</span><span class="sxs-lookup"><span data-stu-id="d921e-145">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="d921e-146">別の `using` 宣言では、`Mcp3008` のインスタンスが作成され、コンストラクターに `SpiDevice` が渡されます。</span><span class="sxs-lookup"><span data-stu-id="d921e-146">Another `using` declaration creates an instance of `Mcp3008` and passes the `SpiDevice` into the constructor.</span></span>
    - <span data-ttu-id="d921e-147">`while` ループが無期限に実行されます。</span><span class="sxs-lookup"><span data-stu-id="d921e-147">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="d921e-148">それぞれの反復処理で、以下が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d921e-148">Each iteration:</span></span>
        1. <span data-ttu-id="d921e-149">`mcp.Read(0)` を呼び出して、ADC の CH0 の値を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="d921e-149">Reads the value of CH0 on the ADC by calling `mcp.Read(0)`.</span></span>
        1. <span data-ttu-id="d921e-150">その値を 10.24 で除算します。</span><span class="sxs-lookup"><span data-stu-id="d921e-150">Divides the value by 10.24.</span></span> <span data-ttu-id="d921e-151">MCP3008 は 10 ビット ADC です。つまり、0-1023 の範囲で 1024 通りの値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="d921e-151">The MCP3008 is a 10-bit ADC, which means it returns 1024 possible values ranging 0-1023.</span></span> <span data-ttu-id="d921e-152">その値を 10.24 で割ると、値はパーセンテージで表されます。</span><span class="sxs-lookup"><span data-stu-id="d921e-152">Dividing the value by 10.24 represents the value as a percentage.</span></span>
        1. <span data-ttu-id="d921e-153">値を最も近い整数に丸めます。</span><span class="sxs-lookup"><span data-stu-id="d921e-153">Rounds the value to the nearest integer.</span></span>
        1. <span data-ttu-id="d921e-154">パーセンテージとして書式設定された値をコンソールに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="d921e-154">Writes the value to the console formatted as a percentage.</span></span>
        1. <span data-ttu-id="d921e-155">500 ミリ秒スリープします。</span><span class="sxs-lookup"><span data-stu-id="d921e-155">Sleeps 500 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="d921e-156">配置ディレクトリに切り替え、実行可能ファイルを実行することで、Raspberry Pi でアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="d921e-156">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./AdcTutorial
    ```

    <span data-ttu-id="d921e-157">ポテンショメーターのつまみを回しながら出力を観察します。</span><span class="sxs-lookup"><span data-stu-id="d921e-157">Observe the output as you rotate the potentiometer dial.</span></span> <span data-ttu-id="d921e-158">これは、ポテンショメーターによって、ADC の CH0 に供給される電圧が変化するためです。</span><span class="sxs-lookup"><span data-stu-id="d921e-158">This is due to the potentiometer varying the voltage supplied to CH0 on the ADC.</span></span> <span data-ttu-id="d921e-159">ADC では、CH0 の入力電圧を V<sub>REF</sub> に供給された基準電圧と比較して、値を生成します。</span><span class="sxs-lookup"><span data-stu-id="d921e-159">The ADC compares the input voltage on CH0 to the reference voltage supplied to V<sub>REF</sub> to generate a value.</span></span>

1. <span data-ttu-id="d921e-160"><kbd>Ctrl + C</kbd> キーを押してプログラムを終了します。</span><span class="sxs-lookup"><span data-stu-id="d921e-160">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="d921e-161">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="d921e-161">Congratulations!</span></span> <span data-ttu-id="d921e-162">SPI を使用して、アナログ デジタル コンバーターから値を読み取ることができました。</span><span class="sxs-lookup"><span data-stu-id="d921e-162">You've used SPI to read values from an analog-to-digital converter.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="d921e-163">ソース コードを入手する</span><span class="sxs-lookup"><span data-stu-id="d921e-163">Get the source code</span></span>

<span data-ttu-id="d921e-164">このチュートリアルのソースは、[GitHub から入手できます](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial)。</span><span class="sxs-lookup"><span data-stu-id="d921e-164">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d921e-165">次のステップ</span><span class="sxs-lookup"><span data-stu-id="d921e-165">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d921e-166">汎用入出力を使用して LED を点滅させる方法を学習する</span><span class="sxs-lookup"><span data-stu-id="d921e-166">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
