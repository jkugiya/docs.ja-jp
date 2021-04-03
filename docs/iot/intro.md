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
# <a name="develop-apps-for-iot-devices-with-the-net-iot-libraries"></a><span data-ttu-id="65eab-103">.NET IoT ライブラリを使用して IoT デバイス用のアプリを開発する</span><span class="sxs-lookup"><span data-stu-id="65eab-103">Develop apps for IoT devices with the .NET IoT Libraries</span></span>

<span data-ttu-id="65eab-104">.NET は、さまざまなプラットフォームとアーキテクチャ上で動作します。</span><span class="sxs-lookup"><span data-stu-id="65eab-104">.NET runs on a variety of platforms and architectures.</span></span> <span data-ttu-id="65eab-105">Raspberry Pi や Hummingboard など、一般的なモノのインターネット (IoT) ボードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="65eab-105">Common Internet of things (IoT) boards, such as Raspberry Pi and Hummingboard, are supported.</span></span> <span data-ttu-id="65eab-106">IoT アプリは、通常、センサー、アナログ デジタル コンバーター、LCD デバイスなどの専用ハードウェアと対話します。</span><span class="sxs-lookup"><span data-stu-id="65eab-106">IoT apps typically interact with specialized hardware, such as sensors, analog-to-digital converters, and LCD devices.</span></span> <span data-ttu-id="65eab-107">.NET IoT ライブラリを使用すると、これらのシナリオを実現できます。</span><span class="sxs-lookup"><span data-stu-id="65eab-107">The .NET IoT Libraries enable these scenarios.</span></span>

## <a name="video-overview"></a><span data-ttu-id="65eab-108">ビデオの概要</span><span class="sxs-lookup"><span data-stu-id="65eab-108">Video overview</span></span>

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/IoT-101/Intro-to-IOT-with-NET-Core-1-of-9/player]

## <a name="libraries"></a><span data-ttu-id="65eab-109">ライブラリ</span><span class="sxs-lookup"><span data-stu-id="65eab-109">Libraries</span></span>

<span data-ttu-id="65eab-110">.NET IoT ライブラリは、次の 2 つの NuGet パッケージで構成されています。</span><span class="sxs-lookup"><span data-stu-id="65eab-110">The .NET IoT Libraries are composed of two NuGet packages:</span></span>

- [<span data-ttu-id="65eab-111">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="65eab-111">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio/)
- [<span data-ttu-id="65eab-112">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="65eab-112">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings/)

### <a name="systemdevicegpio"></a><span data-ttu-id="65eab-113">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="65eab-113">System.Device.Gpio</span></span>

<span data-ttu-id="65eab-114">`System.Device.Gpio` では、低レベル ハードウェア ピンと対話してデバイスを制御するためのさまざまなプロトコルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="65eab-114">`System.Device.Gpio` supports a variety of protocols for interacting with low-level hardware pins to control devices.</span></span> <span data-ttu-id="65eab-115">これには以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="65eab-115">These include:</span></span>

- <span data-ttu-id="65eab-116">汎用入出力 (GPIO)</span><span class="sxs-lookup"><span data-stu-id="65eab-116">General-purpose I/O (GPIO)</span></span>
- <span data-ttu-id="65eab-117">Inter-Integrated Circuit (I2C)</span><span class="sxs-lookup"><span data-stu-id="65eab-117">Inter-Integrated Circuit (I2C)</span></span>
- <span data-ttu-id="65eab-118">シリアル周辺機器インターフェイス (SPI)</span><span class="sxs-lookup"><span data-stu-id="65eab-118">Serial Peripheral Interface (SPI)</span></span>
- <span data-ttu-id="65eab-119">パルス幅変調 (PWM)</span><span class="sxs-lookup"><span data-stu-id="65eab-119">Pulse Width Modulation (PWM)</span></span>
- <span data-ttu-id="65eab-120">シリアル ポート</span><span class="sxs-lookup"><span data-stu-id="65eab-120">Serial port</span></span>

### <a name="iotdevicebindings"></a><span data-ttu-id="65eab-121">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="65eab-121">Iot.Device.Bindings</span></span>

<span data-ttu-id="65eab-122">`Iot.Device.Bindings` パッケージ:</span><span class="sxs-lookup"><span data-stu-id="65eab-122">The `Iot.Device.Bindings` package:</span></span>

* <span data-ttu-id="65eab-123">System.Device.Gpio をラップすることによってアプリ開発を効率化するための[デバイス バインド](https://github.com/dotnet/iot/blob/main/src/devices/README.md)が含まれています。</span><span class="sxs-lookup"><span data-stu-id="65eab-123">Contains [device bindings](https://github.com/dotnet/iot/blob/main/src/devices/README.md) to streamline app development by wrapping System.Device.Gpio.</span></span>
* <span data-ttu-id="65eab-124">コミュニティでサポートされており、さらなるバインドが継続的に追加されています。</span><span class="sxs-lookup"><span data-stu-id="65eab-124">Is community-supported, and additional bindings are added continually.</span></span>

<span data-ttu-id="65eab-125">一般的に使用されるデバイス バインドには、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="65eab-125">Commonly used device bindings include:</span></span>

- [<span data-ttu-id="65eab-126">CharacterLcd - LCD 文字表示</span><span class="sxs-lookup"><span data-stu-id="65eab-126">CharacterLcd - LCD character display</span></span>](https://github.com/dotnet/iot/tree/main/src/devices/CharacterLcd)
- [<span data-ttu-id="65eab-127">SN74HC595 - 8 ビット シフト レジスタ</span><span class="sxs-lookup"><span data-stu-id="65eab-127">SN74HC595 - 8-bit shift register</span></span>](https://github.com/dotnet/iot/tree/main/src/devices/Sn74hc595)
- [<span data-ttu-id="65eab-128">BrickPi3</span><span class="sxs-lookup"><span data-stu-id="65eab-128">BrickPi3</span></span>](https://github.com/dotnet/iot/tree/main/src/devices/BrickPi3)
- [<span data-ttu-id="65eab-129">Max7219 - LED マトリックス ドライバー</span><span class="sxs-lookup"><span data-stu-id="65eab-129">Max7219 - LED Matrix driver</span></span>](https://github.com/dotnet/iot/tree/main/src/devices/Max7219)
- [<span data-ttu-id="65eab-130">RGBLedMatrix - RGB LED マトリックス</span><span class="sxs-lookup"><span data-stu-id="65eab-130">RGBLedMatrix - RGB LED Matrix</span></span>](https://github.com/dotnet/iot/tree/main/src/devices/RGBLedMatrix)

## <a name="supported-operating-systems"></a><span data-ttu-id="65eab-131">サポートされるオペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="65eab-131">Supported operating systems</span></span>

<span data-ttu-id="65eab-132">`System.Device.Gpio` は、ARM または ARM64 がサポートされているほとんどの Linux のバージョン、および Windows 10 IoT Core でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="65eab-132">`System.Device.Gpio` is supported on most versions of Linux that support ARM/ARM64 and Windows 10 IoT Core.</span></span>

> [!TIP]
> <span data-ttu-id="65eab-133">Raspberry Pi に対しては、[Raspberry Pi OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) (旧称 Raspbian) をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="65eab-133">For Raspberry Pi, [Raspberry Pi OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)  (formerly Raspbian) is recommended.</span></span>

## <a name="supported-hardware-platforms"></a><span data-ttu-id="65eab-134">サポートされているハードウェア プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="65eab-134">Supported hardware platforms</span></span>

<span data-ttu-id="65eab-135">`System.Device.Gpio` は、ほとんどのシングルボード プラットフォームと互換性があります。</span><span class="sxs-lookup"><span data-stu-id="65eab-135">`System.Device.Gpio` is compatible with most single-board platforms.</span></span> <span data-ttu-id="65eab-136">推奨されるプラットフォームは、Raspberry Pi (2 以上) と Hummingboard です。</span><span class="sxs-lookup"><span data-stu-id="65eab-136">Recommended platforms are Raspberry Pi (2 and greater) and Hummingboard.</span></span> <span data-ttu-id="65eab-137">互換性が確認されているその他のプラットフォームは、BeagleBoard と ODROID です。</span><span class="sxs-lookup"><span data-stu-id="65eab-137">Other platforms known to be compatible are BeagleBoard and ODROID.</span></span>

<span data-ttu-id="65eab-138">PC プラットフォームは、USB から SPI/I2C へのブリッジを使用することによってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="65eab-138">PC platforms are supported via the use of a USB to SPI/I2C bridge.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="65eab-139">.NET は、Raspberry Pi 2 より前の Raspberry Pi Zero デバイスや Raspberry Pi デバイスを含む ARMv6 アーキテクチャ デバイスではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="65eab-139">.NET is not supported on ARMv6 architecture devices, including Raspberry Pi Zero and Raspberry Pi devices prior to Raspberry Pi 2.</span></span>

## <a name="resources"></a><span data-ttu-id="65eab-140">リソース</span><span class="sxs-lookup"><span data-stu-id="65eab-140">Resources</span></span>

- [<span data-ttu-id="65eab-141">GitHub の .NET IoT ライブラリ</span><span class="sxs-lookup"><span data-stu-id="65eab-141">.NET IoT Libraries on Github</span></span>](https://github.com/dotnet/iot)
