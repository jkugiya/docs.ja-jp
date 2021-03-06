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
# <a name="develop-apps-for-iot-devices-with-the-net-iot-libraries"></a><span data-ttu-id="a9672-103">.NET IoT ライブラリを使用して IoT デバイス用のアプリを開発する</span><span class="sxs-lookup"><span data-stu-id="a9672-103">Develop apps for IoT devices with the .NET IoT Libraries</span></span>

<span data-ttu-id="a9672-104">.NET は、さまざまなプラットフォームとアーキテクチャで動作します。</span><span class="sxs-lookup"><span data-stu-id="a9672-104">.NET runs on a variety of platforms and architectures.</span></span> <span data-ttu-id="a9672-105">Raspberry Pi や Hummingboard など、一般的なモノのインターネット (IoT) ボードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a9672-105">Common Internet of things (IoT) boards, such as Raspberry Pi and Hummingboard, are supported.</span></span> <span data-ttu-id="a9672-106">IoT アプリは通常、センサー、アナログ-デジタルコンバーター、および LCD デバイスといった特殊なハードウェアと対話します。</span><span class="sxs-lookup"><span data-stu-id="a9672-106">IoT apps typically interact with specialized hardware, such as sensors, analog-to-digital converters, and LCD devices.</span></span> <span data-ttu-id="a9672-107">.NET IoT ライブラリを使用すると、これらのシナリオを実現できます。</span><span class="sxs-lookup"><span data-stu-id="a9672-107">The .NET IoT Libraries enable these scenarios.</span></span>

## <a name="video-overview"></a><span data-ttu-id="a9672-108">ビデオの概要</span><span class="sxs-lookup"><span data-stu-id="a9672-108">Video overview</span></span>

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/IoT-101/Intro-to-IOT-with-NET-Core-1-of-9/player]

## <a name="libraries"></a><span data-ttu-id="a9672-109">ライブラリ</span><span class="sxs-lookup"><span data-stu-id="a9672-109">Libraries</span></span>

<span data-ttu-id="a9672-110">.NET IoT ライブラリは、次の2つの NuGet パッケージで構成されています。</span><span class="sxs-lookup"><span data-stu-id="a9672-110">The .NET IoT Libraries are composed of two NuGet packages:</span></span>

- [<span data-ttu-id="a9672-111">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="a9672-111">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio/)
- [<span data-ttu-id="a9672-112">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="a9672-112">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings/)

### <a name="systemdevicegpio"></a><span data-ttu-id="a9672-113">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="a9672-113">System.Device.Gpio</span></span>

<span data-ttu-id="a9672-114">`System.Device.Gpio` では、デバイスを制御するために低レベルのハードウェア pin と対話するためのさまざまなプロトコルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a9672-114">`System.Device.Gpio` supports a variety of protocols for interacting with low-level hardware pins to control devices.</span></span> <span data-ttu-id="a9672-115">次の設定があります。</span><span class="sxs-lookup"><span data-stu-id="a9672-115">These include:</span></span>

- <span data-ttu-id="a9672-116">汎用入出力 (GPIO)</span><span class="sxs-lookup"><span data-stu-id="a9672-116">General-purpose I/O (GPIO)</span></span>
- <span data-ttu-id="a9672-117">Inter-Integrated 回線 (I2C)</span><span class="sxs-lookup"><span data-stu-id="a9672-117">Inter-Integrated Circuit (I2C)</span></span>
- <span data-ttu-id="a9672-118">シリアル周辺機器インターフェイス (SPI)</span><span class="sxs-lookup"><span data-stu-id="a9672-118">Serial Peripheral Interface (SPI)</span></span>
- <span data-ttu-id="a9672-119">パルス幅の変調 (PWM)</span><span class="sxs-lookup"><span data-stu-id="a9672-119">Pulse Width Modulation (PWM)</span></span>
- <span data-ttu-id="a9672-120">シリアル ポート</span><span class="sxs-lookup"><span data-stu-id="a9672-120">Serial port</span></span>

### <a name="iotdevicebindings"></a><span data-ttu-id="a9672-121">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="a9672-121">Iot.Device.Bindings</span></span>

<span data-ttu-id="a9672-122">`Iot.Device.Bindings`パッケージ:</span><span class="sxs-lookup"><span data-stu-id="a9672-122">The `Iot.Device.Bindings` package:</span></span>

* <span data-ttu-id="a9672-123">System.string をラップすることによってアプリ開発を効率化するための [デバイスのバインド](https://github.com/dotnet/iot/blob/master/src/devices/README.md) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a9672-123">Contains [device bindings](https://github.com/dotnet/iot/blob/master/src/devices/README.md) to streamline app development by wrapping System.Device.Gpio.</span></span>
* <span data-ttu-id="a9672-124">コミュニティでサポートされており、追加のバインドが継続的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="a9672-124">Is community-supported, and additional bindings are added continually.</span></span>

<span data-ttu-id="a9672-125">一般的に使用されるデバイスのバインドは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a9672-125">Commonly used device bindings include:</span></span>

- [<span data-ttu-id="a9672-126">文字 Lcd-LCD 文字ディスプレイ</span><span class="sxs-lookup"><span data-stu-id="a9672-126">CharacterLcd - LCD character display</span></span>](https://github.com/dotnet/iot/tree/master/src/devices/CharacterLcd)
- [<span data-ttu-id="a9672-127">SN74HC595-8 ビットシフトレジスタ</span><span class="sxs-lookup"><span data-stu-id="a9672-127">SN74HC595 - 8-bit shift register</span></span>](https://github.com/dotnet/iot/tree/master/src/devices/Sn74hc595)
- [<span data-ttu-id="a9672-128">BrickPi3</span><span class="sxs-lookup"><span data-stu-id="a9672-128">BrickPi3</span></span>](https://github.com/dotnet/iot/tree/master/src/devices/BrickPi3)
- [<span data-ttu-id="a9672-129">Max7219-LED マトリックスドライバー</span><span class="sxs-lookup"><span data-stu-id="a9672-129">Max7219 - LED Matrix driver</span></span>](https://github.com/dotnet/iot/tree/master/src/devices/Max7219)
- [<span data-ttu-id="a9672-130">RGBLedMatrix-RGB LED マトリックス</span><span class="sxs-lookup"><span data-stu-id="a9672-130">RGBLedMatrix - RGB LED Matrix</span></span>](https://github.com/dotnet/iot/tree/master/src/devices/RGBLedMatrix)

## <a name="supported-operating-systems"></a><span data-ttu-id="a9672-131">サポートされるオペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="a9672-131">Supported operating systems</span></span>

<span data-ttu-id="a9672-132">`System.Device.Gpio` は、ARM/ARM64 と Windows 10 IoT Core をサポートするほとんどのバージョンの Linux でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a9672-132">`System.Device.Gpio` is supported on most versions of Linux that support ARM/ARM64 and Windows 10 IoT Core.</span></span>

> [!TIP]
> <span data-ttu-id="a9672-133">Raspberry Pi では、 [Raspberry PI OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)  (旧称 Raspbian) を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a9672-133">For Raspberry Pi, [Raspberry Pi OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)  (formerly Raspbian) is recommended.</span></span>

## <a name="supported-hardware-platforms"></a><span data-ttu-id="a9672-134">サポートされているハードウェアプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="a9672-134">Supported hardware platforms</span></span>

<span data-ttu-id="a9672-135">`System.Device.Gpio` は、ほとんどのシングルボードプラットフォームと互換性があります。</span><span class="sxs-lookup"><span data-stu-id="a9672-135">`System.Device.Gpio` is compatible with most single-board platforms.</span></span> <span data-ttu-id="a9672-136">推奨されるプラットフォームは Raspberry Pi (2 以上) と Hummingboard です。</span><span class="sxs-lookup"><span data-stu-id="a9672-136">Recommended platforms are Raspberry Pi (2 and greater) and Hummingboard.</span></span> <span data-ttu-id="a9672-137">互換性があるとわかっているその他のプラットフォームは、BeagleBoard と OID ID です。</span><span class="sxs-lookup"><span data-stu-id="a9672-137">Other platforms known to be compatible are BeagleBoard and ODROID.</span></span>

<span data-ttu-id="a9672-138">PC プラットフォームは、USB から SPI/I2C ブリッジを使用することによってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a9672-138">PC platforms are supported via the use of a USB to SPI/I2C bridge.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a9672-139">.NET は、Raspberry Pi 2 より前の Raspberry Pi 0 および Raspberry Pi デバイスを含む、ARMv6 アーキテクチャデバイスではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a9672-139">.NET is not supported on ARMv6 architecture devices, including Raspberry Pi Zero and Raspberry Pi devices prior to Raspberry Pi 2.</span></span>

## <a name="resources"></a><span data-ttu-id="a9672-140">リソース</span><span class="sxs-lookup"><span data-stu-id="a9672-140">Resources</span></span>

- [<span data-ttu-id="a9672-141">Github の .NET IoT ライブラリ</span><span class="sxs-lookup"><span data-stu-id="a9672-141">.NET IoT Libraries on Github</span></span>](https://github.com/dotnet/iot)
