---
title: LED を点滅させる
description: .NET IoT ライブラリを使用して LED を点滅させる方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 0d5db19faac0293b9982731f26dfd85d6ce07b3a
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259025"
---
# <a name="blink-an-led"></a>LED を点滅させる

汎用 i/o (GPIO) ピンは、個別に制御できます。 これは、Led、リレー、およびその他のステートフルデバイスを制御する場合に便利です。 このトピックでは、.NET と Raspberry Pi の GPIO ピンを使用して、LED の電源を入れ、繰り返し点滅させます。

## <a name="prerequisites"></a>前提条件

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- 5 mm LED
- 330Ωの抵抗
- ブレッドボード
- ジャンパー ワイヤ
- Raspberry Pi GPIO ブレイクボードボード (省略可能/推奨)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [ensure-ssh](../includes/ensure-ssh.md)]

## <a name="prepare-the-hardware"></a>ハードウェアを準備する

ハードウェアコンポーネントを使用して、次の図に示すように回線を構築します。

:::image type="content" source="../media/rpi-led_bb-thumb.png" alt-text="LED と抵抗がある回線を示す Fritzing 図" lightbox="../media/rpi-led_bb.png":::

上の図は、次の接続を示しています。

- GPIO 18 から LED anode (長い潜在顧客)
- LED ブラウン (短い、負のリード) から330Ωの抵抗 (両端)
- 330Ωの抵抗 (他の端) から地面へ

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>アプリを作成する

お好みの開発環境で、次の手順を実行します。

1. [.NET CLI](../../core/tools/dotnet-new.md)または[Visual Studio](../../core/tutorials/with-visual-studio.md)を使用して、新しい .net コンソールアプリを作成します。 「 *Blinktutorial*」という名前を指定します。

    ```dotnetcli
    dotnet new console -o BlinkTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. *Program.cs* の内容を次のコードで置き換えます。

    :::code language="csharp" source="~/iot-samples/tutorials/BlinkTutorial/Program.cs" :::

    上のコードでは以下の操作が行われます。

    - [Using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)は、のインスタンスを作成し `GpioController` ます。 この `using` 宣言により、オブジェクトが破棄され、ハードウェアリソースが正常に解放されます。
    - 出力用に GPIO pin 18 が開かれています
    - `while`ループは無期限に実行されます。 各イテレーション:
        1. GPIO pin 18 に値を書き込みます。 `ledOn`が true の場合は、 `PinValue.High` (に) を書き込みます。 それ以外の場合は、を書き込み `PinValue.Low` ます。
        1. 1000ミリ秒スリープします。
        1. の値を切り替え `ledOn` ます。

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. 配置ディレクトリに切り替え、実行可能ファイルを実行して、Raspberry Pi でアプリを実行します。

    ```bash
    ./BlinkTutorial
    ```

    LED が点滅し、毎秒点灯します。

1. <kbd>Ctrl + C</kbd>キーを押してプログラムを終了します。

おめでとうございます。 これで、GPIO を使って LED を点滅させることができました。

## <a name="get-the-source-code"></a>ソース コードを入手する

このチュートリアルのソースは、 [GitHub で入手でき](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial)ます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [センサーから環境の状態を読み取る方法について説明します](../tutorials/temp-sensor.md)
