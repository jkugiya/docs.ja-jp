---
title: LED を点滅させる
description: .NET IoT ライブラリを使用して LED を点滅させる方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 0d5db19faac0293b9982731f26dfd85d6ce07b3a
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "102259025"
---
# <a name="blink-an-led"></a>LED を点滅させる

汎用 I/O (GPIO) ピンは、個別に制御できます。 これは、LED、リレー、その他のステートフル デバイスを制御する場合に便利です。 このトピックでは、.NET とお使いの Raspberry Pi の GPIO ピンを使用して、LED に電力を供給し、繰り返し点滅させます。

## <a name="prerequisites"></a>前提条件

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- 5 mm LED
- 330 Ω の抵抗
- ブレッドボード
- ジャンパー ワイヤ
- Raspberry Pi GPIO ブレークアウト基板 (省略可能、推奨)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [ensure-ssh](../includes/ensure-ssh.md)]

## <a name="prepare-the-hardware"></a>ハードウェアを準備する

ハードウェア コンポーネントを使用して、次の図に示すような回路を構築します。

:::image type="content" source="../media/rpi-led_bb-thumb.png" alt-text="LED と抵抗がある回路を示す Fritzing 図" lightbox="../media/rpi-led_bb.png":::

上の図では、次の接続が示されています。

- GPIO 18 から LED の陽極 (長い正のリード) へ
- LED の陰極 (短い負のリード) から 330 Ω の抵抗 (どちらかの端) へ
- 330 Ω の抵抗 (他の端) からグラウンドへ

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>アプリを作成する

お好みの開発環境で、次の手順を実行します。

1. [.NET CLI](../../core/tools/dotnet-new.md) または [Visual Studio](../../core/tutorials/with-visual-studio.md) を使用して、新しい .NET コンソール アプリを作成します。 「*BlinkTutorial*」という名前を指定します。

    ```dotnetcli
    dotnet new console -o BlinkTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. *Program.cs* の内容を次のコードで置き換えます。

    :::code language="csharp" source="~/iot-samples/tutorials/BlinkTutorial/Program.cs" :::

    上のコードでは以下の操作が行われます。

    - [using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)によって、`GpioController` のインスタンスが作成されます。 この `using` 宣言により、オブジェクトが破棄され、ハードウェア リソースが適切に解放されます。
    - 出力用に GPIO ピン 18 が開かれています
    - `while` ループが無期限に実行されます。 それぞれの反復処理で、以下が実行されます。
        1. GPIO ピン 18 に値を書き込みます。 `ledOn` が true の場合は、`PinValue.High` (オン) を書き込みます。 それ以外の場合は、`PinValue.Low` を書き込みます。
        1. 1000 ミリ秒スリープします。
        1. `ledOn` の値を切り替えます。

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. 配置ディレクトリに切り替え、実行可能ファイルを実行することで、Raspberry Pi でアプリを実行します。

    ```bash
    ./BlinkTutorial
    ```

    LED は毎秒点滅します。

1. <kbd>Ctrl + C</kbd> キーを押してプログラムを終了します。

おめでとうございます。 GPIO を使って LED を点滅させることができました。

## <a name="get-the-source-code"></a>ソース コードを入手する

このチュートリアルのソースは、[GitHub から入手できます](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial)。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [センサーから環境条件を読み取る方法を学習する](../tutorials/temp-sensor.md)
