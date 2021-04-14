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
# <a name="display-text-on-an-lcd"></a>LCD にテキストを表示する

LCD 文字ディスプレイは、外部モニターを必要とせずに情報を表示する場合に便利です。 一般的な LCD 文字ディスプレイは GPIO ピンに直接接続できますが、そのような方法では最大 10 個の GPIO ピンを使用する必要があります。 複数のデバイスの組み合わせに接続する必要があるシナリオでは、多くの場合、文字ディスプレイにそれほど多くの GPIO ヘッダーを充てるのは実用的ではありません。

多くの製造元では、20x4 の LCD 文字ディスプレイと一体化された GPIO エキスパンダーが販売されています。 文字ディスプレイを GPIO エキスパンダーに直接接続し、次にそれを Inter-Integrated Circuit (I2C) シリアル プロトコルを介して Raspberry Pi に接続します。

このトピックでは、.NET を使用して、I2C GPIO エキスパンダーを使用した LCD 文字ディスプレイにテキストを表示します。

## <a name="prerequisites"></a>必須コンポーネント

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [I2C インターフェイスを備えた 20x4 の LCD 文字ディスプレイ](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c)
- ジャンパー ワイヤ
- ブレッドボード (省略可能、推奨)
- Raspberry Pi GPIO ブレークアウト基板 (省略可能、推奨)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!NOTE]
> LCD 文字ディスプレイの製造元は多数あります。 ほとんどの設計は同一であり、製造元が異なる機能を用意することはないはずです。 参考までに、このチュートリアルは [SunFounder LCD2004](https://www.sunfounder.com/lcd2004-module.html) を使用して作成されました。

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a>ハードウェアを準備する

ジャンパー ワイヤを使用して、次のように I2C GPIO エキスパンダーの 4 つのピンを Raspberry Pi に接続します。

- GND からグラウンドへ
- VCC から 5V へ
- SDA から SDA (GPIO 2) へ
- SCL から SCL (GPIO 3) へ

必要に応じて、次の図を参照してください。

| I2C インターフェイス (ディスプレイの背面) | Raspberry Pi GPIO |
|---------------------------------|-------------------|
| :::image type="content" source="../media/character-display-i2c-thumb.png" alt-text="I2C GPIO エキスパンダーを示す文字ディスプレイの背面の画像。" lightbox="../media/character-display-i2c.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Raspberry Pi GPIO ヘッダーのピン配列を示す図。画像提供: Raspberry Pi Foundation。" lightbox="../media/gpio-pinout-diagram.png":::<br />[画像提供: Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/)。
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>アプリを作成する

お好みの開発環境で、次の手順を実行します。

1. [.NET CLI](../../core/tools/dotnet-new.md) または [Visual Studio](../../core/tutorials/with-visual-studio.md) を使用して、新しい .NET コンソール アプリを作成します。 「*LcdTutorial*」という名前を指定します。

    ```dotnetcli
    dotnet new console -o LcdTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. *Program.cs* の内容を次のコードで置き換えます。

    :::code language="csharp" source="~/iot-samples/tutorials/LcdTutorial/Program.cs" :::

    上のコードでは以下の操作が行われます。

    - [using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)により、`I2cDevice.Create` を呼び出して `busId` および `deviceAddress` パラメーターと共に新しい `I2cConnectionSettings` を渡すことによって、`I2cDevice` のインスタンスが作成されます。 この `I2cDevice` は、I2C バスを表しています。 この `using` 宣言により、オブジェクトが破棄され、ハードウェア リソースが適切に解放されます。

        > [!WARNING]
        > GPIO エキスパンダーのデバイス アドレスは、製造元によって使用されるチップによって異なります。 PCF8574 を備えた GPIO エキスパンダーではアドレス `0x27` が使用されます。一方、PCF8574A チップを使用するものの場合は `0x3F` が使用されます。 使用する LCD のドキュメントを参照してください。

    - 別の `using` 宣言では、`Pcf8574` のインスタンスが作成され、コンストラクターに `I2cDevice` が渡されます。 このインスタンスは、GPIO エキスパンダーを表しています。
    - 別の `using` 宣言によって、ディスプレイを表す `Lcd2004` のインスタンスが作成されます。 いくつかのパラメーターがコンストラクターに渡され、GPIO エキスパンダーとの通信に使用する設定が記述されています。 GPIO エキスパンダーは `controller` パラメーターとして渡されています。
    - `while` ループが無期限に実行されます。 それぞれの反復処理で、以下が実行されます。
        1. ディスプレイをクリアします。
        1. カーソル位置を、現在の行の最初の位置に設定します。
        1. ディスプレイの現在のカーソル位置に、現在時刻を書き込みます。
        1. 現在の行カウンターを反復処理します。
        1. 1000 ミリ秒スリープします。

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. 配置ディレクトリに切り替え、実行可能ファイルを実行することで、Raspberry Pi でアプリを実行します。

    ```bash
    ./LcdTutorial
    ```

    LCD 文字ディスプレイの各行に現在の時刻が表示される様子を観察します。

    > [!TIP]
    > ディスプレイは点灯するがテキストが表示されない場合は、ディスプレイの背面でコントラストの目盛りを調整してみてください。

1. <kbd>Ctrl + C</kbd> キーを押してプログラムを終了します。

おめでとうございます! I2C と GPIO エキスパンダーを使用して、LCD にテキストを表示することができました。

## <a name="get-the-source-code"></a>ソース コードを入手する

このチュートリアルのソースは、[GitHub から入手できます](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial)。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [汎用入出力を使用して LED を点滅させる方法を学習する](../tutorials/blink-led.md)
