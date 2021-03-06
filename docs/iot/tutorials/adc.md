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
# <a name="read-values-from-an-analog-to-digital-converter"></a>アナログ デジタル コンバーターから値を読み取る

アナログ-デジタルコンバーター (ADC) は、アナログ入力電圧値を読み取り、デジタル値に変換できるデバイスです。 ADCs は、特定の条件に基づいて抵抗を変更する thermistors、potentiometers、およびその他のデバイスから値を読み取るために使用されます。

このトピックでは、potentiometer を使用して入力電圧を乗算するときに、.NET を使用して ADC から値を読み取ります。

## <a name="prerequisites"></a>前提条件

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [MCP3008](https://www.microchip.com/wwwproducts/MCP3008) のアナログ/デジタルコンバーター
- 3ピン potentiometer
- ブレッドボード
- ジャンパー ワイヤ
- Raspberry Pi GPIO ブレイクボードボード (省略可能/推奨)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [prepare-pi-spi](../includes/prepare-pi-spi.md)]

## <a name="prepare-the-hardware"></a>ハードウェアを準備する

ハードウェアコンポーネントを使用して、次の図に示すように回線を構築します。

:::image type="content" source="../media/rpi-trimpot_spi-thumb.png" alt-text="MCP3008 ADC と potentiometer がある回線を示す Fritzing 図" lightbox="../media/rpi-trimpot_spi.png":::

MCP3008 は、シリアルペリフェラルインターフェイス (SPI) を使用して通信を行います。 MCP3008 から Raspberry Pi と potentiometer への接続は次のとおりです。

- V<sub>DD</sub> から 3.3 v (赤で表示)
- V<sub>REF</sub> から 3.3 v (赤)
- AGND からグランド (黒)
- CLK から SCLK (オレンジ)
- D<sub>-</sub> 誤 o (オレンジ)
- D<sub>IN</sub> mosi (オレンジ色)
- CS/SHDN から CE0 (緑)
- DGND から地面 (黒)
- Potentiometer の CH0 (中間) pin (黄)

Potentiometer の外側のピンに 3.3 V とグランドを提供します。 順序は重要ではありません。

必要に応じて、次のピンチャートを参照してください。

| MCP3008  | Raspberry Pi GPIO |
|----------|-------------------|
| :::image type="content" source="../media/mcp3008-diagram-thumb.png" alt-text="MCP3008 のピンを示す図" lightbox="../media/mcp3008-diagram.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Raspberry Pi GPIO ヘッダーのピンアウトを示す図。イメージの Raspberry Pi Foundation。" lightbox="../media/gpio-pinout-diagram.png":::<br />[イメージの Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/)。
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>アプリを作成する

お好みの開発環境で、次の手順を実行します。

1. [.NET CLI](../../core/tools/dotnet-new.md)または[Visual Studio](../../core/tutorials/with-visual-studio.md)を使用して、新しい .net コンソールアプリを作成します。 *Adctutorial* に名前を指定します。

    ```dotnetcli
    dotnet new console -o AdcTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. *Program.cs* の内容を次のコードで置き換えます。

    :::code language="csharp" source="~/iot-samples/tutorials/AdcTutorial/Program.cs" :::

    上のコードでは以下の操作が行われます。

    - `hardwareSpiSettings` は、の新しいインスタンスに設定され `SpiConnectionSettings` ます。 コンストラクターは、 `busId` パラメーターを0に設定し、パラメーターを0に設定し `chipSelectLine` ます。
    - [Using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)は、を `SpiDevice` 呼び出してを渡すことによって、のインスタンスを作成し `SpiDevice.Create` `hardwareSpiSettings` ます。 これ `SpiDevice` は、SPI バスを表します。 この `using` 宣言により、オブジェクトが破棄され、ハードウェアリソースが正常に解放されます。
    - 別 `using` の宣言によってのインスタンスが作成され、 `Mcp3008` が `SpiDevice` コンストラクターに渡されます。
    - `while`ループは無期限に実行されます。 各イテレーション:
        1. を呼び出して、ADC の CH0 の値を読み取り `mcp.Read(0)` ます。
        1. 値を10.24 で除算します。 MCP3008 は10ビット ADC です。つまり、0-1023 の範囲で1024の値を返すことができます。 値を10.24 で割ると、値はパーセンテージで表されます。
        1. 値を最も近い整数に丸めます。
        1. 値をパーセンテージとして書式設定されたコンソールに書き込みます。
        1. 500ミリ秒スリープします。

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. 配置ディレクトリに切り替え、実行可能ファイルを実行して、Raspberry Pi でアプリを実行します。

    ```bash
    ./AdcTutorial
    ```

    Potentiometer ダイヤルを回転させながら出力を観察します。 これは、potentiometer によって、ADC の CH0 に提供される電圧が変化するためです。 ADC は、CH0 の入力電圧を V<sub>REF</sub> に指定された参照電圧と比較して、値を生成します。

1. <kbd>Ctrl + C</kbd>キーを押してプログラムを終了します。

おめでとうございます。 SPI を使用して、アナログからデジタルへのコンバーターから値を読み取りました。

## <a name="get-the-source-code"></a>ソース コードを入手する

このチュートリアルのソースは、 [GitHub で入手でき](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial)ます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [General Purpose 入力/出力を使用して LED を点滅させる方法について説明します](../tutorials/blink-led.md)
