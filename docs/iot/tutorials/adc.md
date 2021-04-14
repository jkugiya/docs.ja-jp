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
# <a name="read-values-from-an-analog-to-digital-converter"></a>アナログ デジタル コンバーターから値を読み取る

アナログ デジタル コンバーター (ADC) は、アナログの入力電圧値を読み取り、デジタル値に変換できるデバイスです。 ADC は、特定の条件に基づいて抵抗が変化するサーミスター、ポテンショメーター、およびその他のデバイスから値を読み取るために使用されます。

このトピックでは、ポテンショメーターを使用して入力電圧を変化させながら、.NET を使用して ADC から値を読み取ります。

## <a name="prerequisites"></a>前提条件

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [MCP3008](https://www.microchip.com/wwwproducts/MCP3008) アナログ デジタル コンバーター
- 3 ピン ポテンショメーター
- ブレッドボード
- ジャンパー ワイヤ
- Raspberry Pi GPIO ブレークアウト基板 (省略可能、推奨)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [prepare-pi-spi](../includes/prepare-pi-spi.md)]

## <a name="prepare-the-hardware"></a>ハードウェアを準備する

ハードウェア コンポーネントを使用して、次の図に示すような回路を構築します。

:::image type="content" source="../media/rpi-trimpot_spi-thumb.png" alt-text="MCP3008 ADC とポテンショメーターがある回路を示す Fritzing 図" lightbox="../media/rpi-trimpot_spi.png":::

MCP3008 では、シリアル周辺機器インターフェイス (SPI) を使用して通信を行います。 MCP3008 から Raspberry Pi およびポテンショメーターへの接続は次のとおりです。

- V<sub>DD</sub> から 3.3V へ (赤で表示)
- V<sub>REF</sub> から 3.3V へ (赤)
- AGND からグラウンドへ (黒)
- CLK から SCLK へ (オレンジ)
- D<sub>OUT</sub> から MISO へ (オレンジ)
- D<sub>IN</sub> から MOSI へ (オレンジ)
- CS/SHDN から CE0 へ (緑)
- DGND からグラウンドへ (黒)
- CH0 からポテンショメーターの可変 (中央) ピンへ (黄色)

ポテンショメーターの外側のピンに、3.3V とグラウンドを供給します。 順序は重要ではありません。

必要に応じて、次のピン配列図を参照してください。

| MCP3008  | Raspberry Pi GPIO |
|----------|-------------------|
| :::image type="content" source="../media/mcp3008-diagram-thumb.png" alt-text="MCP3008 のピン配列を示す図" lightbox="../media/mcp3008-diagram.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Raspberry Pi GPIO ヘッダーのピン配列を示す図。画像提供: Raspberry Pi Foundation。" lightbox="../media/gpio-pinout-diagram.png":::<br />[画像提供: Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/)。
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>アプリを作成する

お好みの開発環境で、次の手順を実行します。

1. [.NET CLI](../../core/tools/dotnet-new.md) または [Visual Studio](../../core/tutorials/with-visual-studio.md) を使用して、新しい .NET コンソール アプリを作成します。 「*AdcTutorial*」という名前を付けます。

    ```dotnetcli
    dotnet new console -o AdcTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. *Program.cs* の内容を次のコードで置き換えます。

    :::code language="csharp" source="~/iot-samples/tutorials/AdcTutorial/Program.cs" :::

    上のコードでは以下の操作が行われます。

    - `hardwareSpiSettings` が `SpiConnectionSettings` の新しいインスタンスに設定されます。 コンストラクターによって、`busId` パラメーターが 0 に、`chipSelectLine` パラメーターが 0 に設定されます。
    - [using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)により、`SpiDevice.Create` を呼び出して `hardwareSpiSettings` を渡すことによって、`SpiDevice` のインスタンスが作成されます。 この `SpiDevice` は、SPI バスを表しています。 この `using` 宣言により、オブジェクトが破棄され、ハードウェア リソースが適切に解放されます。
    - 別の `using` 宣言では、`Mcp3008` のインスタンスが作成され、コンストラクターに `SpiDevice` が渡されます。
    - `while` ループが無期限に実行されます。 それぞれの反復処理で、以下が実行されます。
        1. `mcp.Read(0)` を呼び出して、ADC の CH0 の値を読み取ります。
        1. その値を 10.24 で除算します。 MCP3008 は 10 ビット ADC です。つまり、0-1023 の範囲で 1024 通りの値を返すことができます。 その値を 10.24 で割ると、値はパーセンテージで表されます。
        1. 値を最も近い整数に丸めます。
        1. パーセンテージとして書式設定された値をコンソールに書き込みます。
        1. 500 ミリ秒スリープします。

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. 配置ディレクトリに切り替え、実行可能ファイルを実行することで、Raspberry Pi でアプリを実行します。

    ```bash
    ./AdcTutorial
    ```

    ポテンショメーターのつまみを回しながら出力を観察します。 これは、ポテンショメーターによって、ADC の CH0 に供給される電圧が変化するためです。 ADC では、CH0 の入力電圧を V<sub>REF</sub> に供給された基準電圧と比較して、値を生成します。

1. <kbd>Ctrl + C</kbd> キーを押してプログラムを終了します。

おめでとうございます! SPI を使用して、アナログ デジタル コンバーターから値を読み取ることができました。

## <a name="get-the-source-code"></a>ソース コードを入手する

このチュートリアルのソースは、[GitHub から入手できます](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial)。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [汎用入出力を使用して LED を点滅させる方法を学習する](../tutorials/blink-led.md)
