---
title: .NET IoT ライブラリを使用して IoT デバイス用のアプリを開発する
description: .NET を使用して IoT デバイスとシナリオ用のアプリケーションを作成する方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: overview
ms.prod: dotnet
ms.openlocfilehash: 13460fdafbfd7ef4e047cb7537e832ae4039c614
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255432"
---
# <a name="develop-apps-for-iot-devices-with-the-net-iot-libraries"></a>.NET IoT ライブラリを使用して IoT デバイス用のアプリを開発する

.NET は、さまざまなプラットフォームとアーキテクチャで動作します。 Raspberry Pi や Hummingboard など、一般的なモノのインターネット (IoT) ボードがサポートされています。 IoT アプリは通常、センサー、アナログ-デジタルコンバーター、および LCD デバイスといった特殊なハードウェアと対話します。 .NET IoT ライブラリを使用すると、これらのシナリオを実現できます。

## <a name="video-overview"></a>ビデオの概要

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/IoT-101/Intro-to-IOT-with-NET-Core-1-of-9/player]

## <a name="libraries"></a>ライブラリ

.NET IoT ライブラリは、次の2つの NuGet パッケージで構成されています。

- [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/)
- [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/)

### <a name="systemdevicegpio"></a>System.Device.Gpio

`System.Device.Gpio` では、デバイスを制御するために低レベルのハードウェア pin と対話するためのさまざまなプロトコルがサポートされています。 次の設定があります。

- 汎用入出力 (GPIO)
- Inter-Integrated 回線 (I2C)
- シリアル周辺機器インターフェイス (SPI)
- パルス幅の変調 (PWM)
- シリアル ポート

### <a name="iotdevicebindings"></a>Iot.Device.Bindings

`Iot.Device.Bindings`パッケージ:

* System.string をラップすることによってアプリ開発を効率化するための [デバイスのバインド](https://github.com/dotnet/iot/blob/master/src/devices/README.md) が含まれています。
* コミュニティでサポートされており、追加のバインドが継続的に追加されます。

一般的に使用されるデバイスのバインドは次のとおりです。

- [文字 Lcd-LCD 文字ディスプレイ](https://github.com/dotnet/iot/tree/master/src/devices/CharacterLcd)
- [SN74HC595-8 ビットシフトレジスタ](https://github.com/dotnet/iot/tree/master/src/devices/Sn74hc595)
- [BrickPi3](https://github.com/dotnet/iot/tree/master/src/devices/BrickPi3)
- [Max7219-LED マトリックスドライバー](https://github.com/dotnet/iot/tree/master/src/devices/Max7219)
- [RGBLedMatrix-RGB LED マトリックス](https://github.com/dotnet/iot/tree/master/src/devices/RGBLedMatrix)

## <a name="supported-operating-systems"></a>サポートされるオペレーティング システム

`System.Device.Gpio` は、ARM/ARM64 と Windows 10 IoT Core をサポートするほとんどのバージョンの Linux でサポートされています。

> [!TIP]
> Raspberry Pi では、 [Raspberry PI OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)  (旧称 Raspbian) を使用することをお勧めします。

## <a name="supported-hardware-platforms"></a>サポートされているハードウェアプラットフォーム

`System.Device.Gpio` は、ほとんどのシングルボードプラットフォームと互換性があります。 推奨されるプラットフォームは Raspberry Pi (2 以上) と Hummingboard です。 互換性があるとわかっているその他のプラットフォームは、BeagleBoard と OID ID です。

PC プラットフォームは、USB から SPI/I2C ブリッジを使用することによってサポートされます。

> [!IMPORTANT]
> .NET は、Raspberry Pi 2 より前の Raspberry Pi 0 および Raspberry Pi デバイスを含む、ARMv6 アーキテクチャデバイスではサポートされていません。

## <a name="resources"></a>リソース

- [Github の .NET IoT ライブラリ](https://github.com/dotnet/iot)
