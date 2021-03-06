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
# <a name="display-text-on-an-lcd"></a>LCD にテキストを表示する

LCD 文字ディスプレイは、外部モニターを必要とせずに情報を表示する場合に便利です。 一般的な LCD 文字ディスプレイは、GPIO ピンに直接接続できますが、このようなアプローチでは、最大10個の GPIO ピンを使用する必要があります。 デバイスの組み合わせに接続する必要があるシナリオでは、多くの場合、GPIO ヘッダーの大部分を文字表示に取り上げことは現実的ではありません。

多くの製造元は、20x4 LCD 文字ディスプレイと統合された GPIO を販売しています。 文字表示は、GPIO エキスパンダーに直接接続し、その後、Inter-Integrated 回線 (I2C) シリアルプロトコルを介して Raspberry Pi に接続します。

このトピックでは、.NET を使用して、I2C GPIO 展開を使用して LCD 文字ディスプレイにテキストを表示します。

## <a name="prerequisites"></a>前提条件

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [20x4 I2C インターフェイスを使用した LCD 文字表示](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c)
- ジャンパー ワイヤ
- ブレッドボード (省略可能/推奨)
- Raspberry Pi GPIO ブレイクボードボード (省略可能/推奨)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!NOTE]
> 多くの製造元が LCD 文字を表示しています。 ほとんどの設計は同一であり、製造元は機能に違いを持たせることはできません。 参考までに、このチュートリアルは [SUNFOUNDER LCD2004](https://www.sunfounder.com/lcd2004-module.html)を使用して開発されました。

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a>ハードウェアを準備する

ジャンパー回線を使用して、次のように、I2C GPIO エキスパンダーの4つのピンを Raspberry Pi に接続します。

- GND を地面に
- VCC 5V
- SDA SDA (GPIO 2)
- SCL から SCL へ (GPIO 3)

必要に応じて、次の図を参照してください。

| I2C インターフェイス (ディスプレイの背面) | Raspberry Pi GPIO |
|---------------------------------|-------------------|
| :::image type="content" source="../media/character-display-i2c-thumb.png" alt-text="I2C GPIO エキスパンダーを示す文字表示の背面の画像。" lightbox="../media/character-display-i2c.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Raspberry Pi GPIO ヘッダーのピンアウトを示す図。イメージの Raspberry Pi Foundation。" lightbox="../media/gpio-pinout-diagram.png":::<br />[イメージの Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/)。
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>アプリを作成する

お好みの開発環境で、次の手順を実行します。

1. [.NET CLI](../../core/tools/dotnet-new.md)または[Visual Studio](../../core/tutorials/with-visual-studio.md)を使用して、新しい .net コンソールアプリを作成します。 *Lcdtutorial* という名前を指定します。

    ```dotnetcli
    dotnet new console -o LcdTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. *Program.cs* の内容を次のコードで置き換えます。

    :::code language="csharp" source="~/iot-samples/tutorials/LcdTutorial/Program.cs" :::

    上のコードでは以下の操作が行われます。

    - [Using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)は、を `I2cDevice` 呼び出し `I2cDevice.Create` 、 `I2cConnectionSettings` パラメーターとパラメーターを使用して新しいを渡すことによって、のインスタンスを作成し `busId` `deviceAddress` ます。 これ `I2cDevice` は、I2C バスを表します。 この `using` 宣言により、オブジェクトが破棄され、ハードウェアリソースが正常に解放されます。

        > [!WARNING]
        > GPIO エキスパンダーのデバイスアドレスは、製造元が使用するチップによって異なります。 PCF8574 を装備した GPIO 展開コントロールはアドレスを使用し、PCF8574A チップを使用する GPIO はを `0x27` 使用し `0x3F` ます。 LCD のドキュメントを参照してください。

    - 別 `using` の宣言によってのインスタンスが作成され、 `Pcf8574` が `I2cDevice` コンストラクターに渡されます。 このインスタンスは、GPIO 展開を表します。
    - 別 `using` の宣言 `Lcd2004` によって、表示を表すのインスタンスが作成されます。 いくつかのパラメーターは、GPIO 展開との通信に使用する設定を記述するコンストラクターに渡されます。 GPIO エキスパンダーはパラメーターとして渡され `controller` ます。
    - `while`ループは無期限に実行されます。 各イテレーション:
        1. ディスプレイをクリアします。
        1. カーソル位置を現在の行の最初の位置に設定します。
        1. 現在のカーソル位置にあるディスプレイに現在の時刻を書き込みます。
        1. 現在の行カウンターを反復処理します。
        1. 1000ミリ秒スリープします。

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. 配置ディレクトリに切り替え、実行可能ファイルを実行して、Raspberry Pi でアプリを実行します。

    ```bash
    ./LcdTutorial
    ```

    現在の時刻が各行に表示されているときに、LCD 文字の表示を観察します。

    > [!TIP]
    > ディスプレイが点灯してもテキストが表示されない場合は、ディスプレイの背面でコントラストを調整してみてください。

1. <kbd>Ctrl + C</kbd>キーを押してプログラムを終了します。

おめでとうございます。 I2C と GPIO の展開を使用して、LCD にテキストを表示しました。

## <a name="get-the-source-code"></a>ソース コードを入手する

このチュートリアルのソースは、 [GitHub で入手でき](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial)ます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [General Purpose 入力/出力を使用して LED を点滅させる方法について説明します](../tutorials/blink-led.md)
