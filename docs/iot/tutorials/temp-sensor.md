---
title: センサーから環境条件を読み取る
description: .NET IoT ライブラリを使用して termperature、気圧、湿度を読み取る方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/14/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: bc5c2b9f0876603c152da859547c58b83826969c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259838"
---
# <a name="read-environmental-conditions-from-a-sensor"></a>センサーから環境条件を読み取る

IoT デバイスの最も一般的なシナリオの1つは、環境の状態の検出です。 温度、湿度、気圧などを監視するために、さまざまなセンサーを利用できます。

このトピックでは、.NET を使用してセンサーから環境の状態を読み取ります。

## <a name="prerequisites"></a>前提条件

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) 湿度/気圧/温度センサーのブレイクアウト
- ジャンパー ワイヤ
- ブレッドボード (省略可能)
- Raspberry Pi GPIO ブレイクボードボード (オプション)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!IMPORTANT]
> BME280 テクニカルの製造元は多数あります。 ほとんどの設計は類似しており、製造元は機能に違いがないようにしてください。 このチュートリアルでは、バリエーションの考慮を試みます。 BME280 のブレイクアウトに Inter-Integrated サーキット (I2C) インターフェイスが含まれていることを確認します。

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a>ハードウェアを準備する

ハードウェアコンポーネントを使用して、次の図に示すように回線を構築します。

:::image type="content" source="../media/rpi-bmp280_i2c-thumb.png" alt-text="Raspberry Pi から BME280 ブレイクボードボードへの接続を示す Fritzing 図" lightbox="../media/rpi-bmp280_i2c.png":::

Raspberry Pi から BME280 ブレイクアウトへの接続を次に示します。

- 3.3 v から VIN *または* 3v3 (赤で表示)
- グランドから GND (黒)
- SDA (GPIO 2) から SDI *または* SDA へ (ブルー)
- SCL (GPIO 3) から SCK *または* scl (オレンジ色)

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>アプリを作成する

お好みの開発環境で、次の手順を実行します。

1. [.NET CLI](../../core/tools/dotnet-new.md)または[Visual Studio](../../core/tutorials/with-visual-studio.md)を使用して、新しい .net コンソールアプリを作成します。 *Sensortutorial* という名前を指定します。

    ```dotnetcli
    dotnet new console -o SensorTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. *Program.cs* の内容を次のコードで置き換えます。

    :::code language="csharp" source="~/iot-samples/tutorials/SensorTutorial/Program.cs" :::

    上のコードでは以下の操作が行われます。

    - `i2cSettings` は、の新しいインスタンスに設定され `I2cConnectionSettings` ます。 コンストラクターは、パラメーターを1に設定し、 `busId` `deviceAddress` パラメーターをに設定し `Bme280.DefaultI2cAddress` ます。

        > [!IMPORTANT]
        > 一部の BME280 のブレイクアウト製造元は、セカンダリアドレス値を使用します。 これらのデバイスについては、を使用 `Bme280.SecondaryI2cAddress` します。

    - [Using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)は、を `I2cDevice` 呼び出してを渡すことによって、のインスタンスを作成し `I2cDevice.Create` `i2cSettings` ます。 これ `I2cDevice` は、I2C バスを表します。 この `using` 宣言により、オブジェクトが破棄され、ハードウェアリソースが正常に解放されます。
    - 別 `using` の宣言によって、センサーを表すのインスタンスが作成さ `Bme280` れます。 は、 `I2cDevice` コンストラクターで渡されます。
    - チップの現在 (既定) の設定で測定を行うために必要な時間は、を呼び出すことによって取得され `GetMeasurementDuration` ます。
    - `while`ループは無期限に実行されます。 各イテレーション:
        1. コンソールをクリアします。
        1. 電源モードをに設定し `Bmx280PowerMode.Forced` ます。 これにより、チップが1つの測定を実行し、結果を格納して、スリープ状態になります。
        1. 温度、気圧、湿度、および高度の値を読み取ります。

            > [!NOTE]
            > 高度はデバイスのバインドによって計算されます。 のこのオーバーロード `TryReadAltitude` は、平均海面レベルの圧力を使用して推定を生成します。

        1. 現在の環境条件をコンソールに書き込みます。
        1. 1000ミリ秒スリープします。

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. 配置ディレクトリに切り替え、実行可能ファイルを実行して、Raspberry Pi でアプリを実行します。

    ```bash
    ./SensorTutorial
    ```

    コンソールでセンサーの出力を確認します。

1. <kbd>Ctrl + C</kbd>キーを押してプログラムを終了します。

おめでとうございます。 I2C を使用して、気温/湿度/気圧センサーから値を読み取りました。

## <a name="get-the-source-code"></a>ソース コードを入手する

このチュートリアルのソースは、 [GitHub で入手でき](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial)ます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [LCD にテキストを表示する方法について説明します](../tutorials/lcd-display.md)
