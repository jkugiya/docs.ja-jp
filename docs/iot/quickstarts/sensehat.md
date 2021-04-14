---
title: クイックスタート - .NET を使用して Raspberry Pi Sense HAT を動作させる
description: Raspberry Pi 用の拡張用基板である Sense HAT を使用して、.NET IoT ライブラリの使用を 5 分で開始します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: quickstart
ms.prod: dotnet
ms.openlocfilehash: 28d6650187bbf7b9ce91516f4da4d09b114c904a
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "102259701"
---
# <a name="quickstart---use-net-to-drive-a-raspberry-pi-sense-hat"></a>クイックスタート - .NET を使用して Raspberry Pi Sense HAT を動作させる

Raspberry Pi [Sense HAT](https://www.raspberrypi.org/products/sense-hat/) (**H** ardware **A** ttached on **T** op (上部に取り付けるハードウェア)) は、Raspberry Pi 用の拡張用基板です。 Sense HAT には、8×8 の RGB LED マトリックスと 5 ボタンのジョイスティックが搭載されており、次のセンサーが含まれています。

- ジャイロスコープ
- 加速度計
- 磁力計
- 気温
- 気圧
- 湿度

このクイックスタートでは .NET を使用して、Sense HAT からセンサー値を取得し、ジョイスティック入力に応答し、LED マトリックスを動作させます。

## <a name="prerequisites"></a>必須コンポーネント

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- Sense HAT

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="run-the-quickstart"></a>クイックスタートを実行する

Sense HAT を Raspberry Pi に取り付けます。 Raspberry Pi 上の Bash プロンプト (ローカルまたはリモート) から、次のコマンドを実行します。

```bash
. <(wget -q -O - https://aka.ms/dotnet-iot-sensehat-quickstart)
```

このコマンドにより、スクリプトがダウンロードされて実行されます。 スクリプトは次のようになります。

- .NET SDK をインストールします。
- Sense HAT クイックスタート プロジェクトを含む GitHub リポジトリをクローンします。
- プロジェクトをビルドします。
- プロジェクトを実行します。

コンソールの出力でセンサー データが表示されていることを確認します。 LED マトリックスには、青のフィールド上に黄色のピクセルが表示されます。 ジョイスティックを任意の方向に保持すると、その方向に黄色のピクセルが移動します。 中央のジョイスティック ボタンをクリックすると、背景が青から赤に切り替わります。

## <a name="get-the-source-code"></a>ソース コードを入手する

このクイックスタートのソースは、[GitHub から入手できます](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart)。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [汎用入出力を使用して LED を点滅させる方法を学習する](../tutorials/blink-led.md)
