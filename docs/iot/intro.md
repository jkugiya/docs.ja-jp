---
title: .NET IoT ライブラリを使用して IoT デバイス用のアプリを開発する
description: .NET を使用して、IoT のデバイスとシナリオ向けのアプリケーションを作成する方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: overview
ms.prod: dotnet
ms.openlocfilehash: 4d8dffb28b28c999b3d1bf77a65265280a8ae7a1
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874785"
---
# <a name="develop-apps-for-iot-devices-with-the-net-iot-libraries"></a>.NET IoT ライブラリを使用して IoT デバイス用のアプリを開発する

.NET は、さまざまなプラットフォームとアーキテクチャ上で動作します。 Raspberry Pi や Hummingboard など、一般的なモノのインターネット (IoT) ボードがサポートされています。 IoT アプリは、通常、センサー、アナログ デジタル コンバーター、LCD デバイスなどの専用ハードウェアと対話します。 .NET IoT ライブラリを使用すると、これらのシナリオを実現できます。

## <a name="video-overview"></a>ビデオの概要

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/IoT-101/Intro-to-IOT-with-NET-Core-1-of-9/player]

## <a name="libraries"></a>ライブラリ

.NET IoT ライブラリは、次の 2 つの NuGet パッケージで構成されています。

- [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/)
- [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/)

### <a name="systemdevicegpio"></a>System.Device.Gpio

`System.Device.Gpio` では、低レベル ハードウェア ピンと対話してデバイスを制御するためのさまざまなプロトコルがサポートされています。 これには以下が含まれます。

- 汎用入出力 (GPIO)
- Inter-Integrated Circuit (I2C)
- シリアル周辺機器インターフェイス (SPI)
- パルス幅変調 (PWM)
- シリアル ポート

### <a name="iotdevicebindings"></a>Iot.Device.Bindings

`Iot.Device.Bindings` パッケージ:

* System.Device.Gpio をラップすることによってアプリ開発を効率化するための[デバイス バインド](https://github.com/dotnet/iot/blob/main/src/devices/README.md)が含まれています。
* コミュニティでサポートされており、さらなるバインドが継続的に追加されています。

一般的に使用されるデバイス バインドには、次のものがあります。

- [CharacterLcd - LCD 文字表示](https://github.com/dotnet/iot/tree/main/src/devices/CharacterLcd)
- [SN74HC595 - 8 ビット シフト レジスタ](https://github.com/dotnet/iot/tree/main/src/devices/Sn74hc595)
- [BrickPi3](https://github.com/dotnet/iot/tree/main/src/devices/BrickPi3)
- [Max7219 - LED マトリックス ドライバー](https://github.com/dotnet/iot/tree/main/src/devices/Max7219)
- [RGBLedMatrix - RGB LED マトリックス](https://github.com/dotnet/iot/tree/main/src/devices/RGBLedMatrix)

## <a name="supported-operating-systems"></a>サポートされるオペレーティング システム

`System.Device.Gpio` は、ARM または ARM64 がサポートされているほとんどの Linux のバージョン、および Windows 10 IoT Core でサポートされています。

> [!TIP]
> Raspberry Pi に対しては、[Raspberry Pi OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) (旧称 Raspbian) をお勧めします。

## <a name="supported-hardware-platforms"></a>サポートされているハードウェア プラットフォーム

`System.Device.Gpio` は、ほとんどのシングルボード プラットフォームと互換性があります。 推奨されるプラットフォームは、Raspberry Pi (2 以上) と Hummingboard です。 互換性が確認されているその他のプラットフォームは、BeagleBoard と ODROID です。

PC プラットフォームは、USB から SPI/I2C へのブリッジを使用することによってサポートされます。

> [!IMPORTANT]
> .NET は、Raspberry Pi 2 より前の Raspberry Pi Zero デバイスや Raspberry Pi デバイスを含む ARMv6 アーキテクチャ デバイスではサポートされていません。

## <a name="resources"></a>リソース

- [GitHub の .NET IoT ライブラリ](https://github.com/dotnet/iot)
