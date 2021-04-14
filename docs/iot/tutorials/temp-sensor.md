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
# <a name="read-environmental-conditions-from-a-sensor"></a>センサーから環境条件を読み取る

IoT デバイスの最も一般的なシナリオの 1 つは、環境条件の検出です。 温度、湿度、気圧などを監視するために、さまざまなセンサーを利用できます。

このトピックでは、.NET を使用してセンサーから環境条件を読み取ります。

## <a name="prerequisites"></a>前提条件

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) 湿度/気圧/温度センサー ブレークアウト
- ジャンパー ワイヤ
- ブレッドボード (省略可能)
- Raspberry Pi GPIO ブレークアウト基板 (省略可能)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!IMPORTANT]
> BME280 ブレークアウトの製造元は多数あります。 ほとんどの設計は類似しており、製造元が異なる機能を用意することはないはずです。 このチュートリアルでは、バリエーションを考慮しようと努めています。 お使いの BME280 ブレークアウトに、Inter-Integrated Circuit (I2C) インターフェイスが含まれていることを確認してください。

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a>ハードウェアを準備する

ハードウェア コンポーネントを使用して、次の図に示すような回路を構築します。

:::image type="content" source="../media/rpi-bmp280_i2c-thumb.png" alt-text="Raspberry Pi から BME280 ブレークアウト基板への接続を示す Fritzing 図" lightbox="../media/rpi-bmp280_i2c.png":::

Raspberry Pi から BME280 ブレークアウトへの接続を次に示します。

- 3.3V から VIN "*または*" 3V3 へ (赤で表示)
- グラウンドから GND へ (黒)
- SDA (GPIO 2) から SDI "*または*" SDA へ (青)
- SCL (GPIO 3) から SCK "*または*" SCL へ (オレンジ)

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>アプリを作成する

お好みの開発環境で、次の手順を実行します。

1. [.NET CLI](../../core/tools/dotnet-new.md) または [Visual Studio](../../core/tutorials/with-visual-studio.md) を使用して、新しい .NET コンソール アプリを作成します。 「*SensorTutorial*」という名前を指定します。

    ```dotnetcli
    dotnet new console -o SensorTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. *Program.cs* の内容を次のコードで置き換えます。

    :::code language="csharp" source="~/iot-samples/tutorials/SensorTutorial/Program.cs" :::

    上のコードでは以下の操作が行われます。

    - `i2cSettings` が `I2cConnectionSettings` の新しいインスタンスに設定されます。 コンストラクターによって、`busId` パラメーターが 1 に、`deviceAddress` パラメーターが `Bme280.DefaultI2cAddress` に設定されます。

        > [!IMPORTANT]
        > 一部の BME280 ブレークアウト製造元では、第 2 のアドレス値が使用されます。 そのようなデバイスに対しては、`Bme280.SecondaryI2cAddress` を使用します。

    - [using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)により、`I2cDevice.Create` を呼び出して `i2cSettings` を渡すことによって、`I2cDevice` のインスタンスが作成されます。 この `I2cDevice` は、I2C バスを表しています。 この `using` 宣言により、オブジェクトが破棄され、ハードウェア リソースが適切に解放されます。
    - 別の `using` 宣言によって、センサーを表す `Bme280` のインスタンスが作成されます。 `I2cDevice` は、コンストラクターで渡されます。
    - チップがチップの現在 (既定) の設定で測定を行うために必要な時間は、`GetMeasurementDuration` を呼び出すことによって取得されます。
    - `while` ループが無期限に実行されます。 それぞれの反復処理で、以下が実行されます。
        1. コンソールをクリアします。
        1. 電源モードを `Bmx280PowerMode.Forced` に設定します。 これにより、チップで 1 つの測定が実行され、その結果が格納されて、スリープ状態になります。
        1. 温度、気圧、湿度、および高度の値を読み取ります。

            > [!NOTE]
            > 高度はデバイスのバインドによって計算されます。 この `TryReadAltitude` のオーバーロードでは、平均海面気圧を使用して推定値が生成されます。

        1. 現在の環境条件をコンソールに書き込みます。
        1. 1000 ミリ秒スリープします。

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. 配置ディレクトリに切り替え、実行可能ファイルを実行することで、Raspberry Pi でアプリを実行します。

    ```bash
    ./SensorTutorial
    ```

    コンソールでセンサーの出力を観察します。

1. <kbd>Ctrl + C</kbd> キーを押してプログラムを終了します。

おめでとうございます。 I2C を使用して、気温、湿度、気圧のセンサーから値を読み取ることができました。

## <a name="get-the-source-code"></a>ソース コードを入手する

このチュートリアルのソースは、[GitHub から入手できます](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial)。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [LCD にテキストを表示する方法を学習する](../tutorials/lcd-display.md)
