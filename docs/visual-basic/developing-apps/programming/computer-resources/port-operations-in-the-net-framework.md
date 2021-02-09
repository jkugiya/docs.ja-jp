---
description: '詳細情報: Visual Basic による .NET Framework でのポート操作'
title: .NET Framework でのポート操作
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 072baac53589f8a5d6405eb786b4e692cbaf6181
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641526"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="c2206-103">Visual Basic による .NET Framework でのポート操作</span><span class="sxs-lookup"><span data-stu-id="c2206-103">Port Operations in the .NET Framework with Visual Basic</span></span>

<span data-ttu-id="c2206-104"><xref:System.IO.Ports?displayProperty=nameWithType> 名前空間の .NET Framework クラスを介して、コンピューターのシリアル ポートにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c2206-104">You can access your computer's serial ports through the .NET Framework classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c2206-105">最も重要な役割を持つのが <xref:System.IO.Ports.SerialPort> クラスです。このクラスにより、同期 I/O とイベント ドリブン I/O のフレームワーク、ピンの状態とブレーク状態へのアクセス、およびシリアル ドライバーのプロパティへのアクセスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c2206-105">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="c2206-106">このクラスは、<xref:System.IO.Ports.SerialPort.BaseStream> プロパティを通じてアクセス可能な <xref:System.IO.Stream> オブジェクト内にラップできます。</span><span class="sxs-lookup"><span data-stu-id="c2206-106">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="c2206-107"><xref:System.IO.Stream> オブジェクト内で <xref:System.IO.Ports.SerialPort> をラップすることにより、ストリームを使用するクラスからシリアル ポートへのアクセスを実現できます。</span><span class="sxs-lookup"><span data-stu-id="c2206-107">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="c2206-108">名前空間には、シリアル ポートの制御を容易にする列挙型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c2206-108">The namespace includes enumerations that simplify the control of serial ports.</span></span>

<span data-ttu-id="c2206-109">最も簡単に <xref:System.IO.Ports.SerialPort> オブジェクトを作成する方法は、<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> メソッドを経由することです。</span><span class="sxs-lookup"><span data-stu-id="c2206-109">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>

> [!NOTE]
> <span data-ttu-id="c2206-110">.NET Framework クラスを使用してパラレル ポートや USB ポートなどの他の種類のポートに直接アクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c2206-110">You cannot use .NET Framework classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>

## <a name="enumerations"></a><span data-ttu-id="c2206-111">列挙型</span><span class="sxs-lookup"><span data-stu-id="c2206-111">Enumerations</span></span>

<span data-ttu-id="c2206-112">次の表は、シリアル ポートへのアクセスに使用される主な列挙型を一覧にまとめ、説明を加えたものです。</span><span class="sxs-lookup"><span data-stu-id="c2206-112">This table lists and describes the main enumerations used for accessing a serial port:</span></span>

|<span data-ttu-id="c2206-113">列挙</span><span class="sxs-lookup"><span data-stu-id="c2206-113">Enumeration</span></span>|<span data-ttu-id="c2206-114">説明</span><span class="sxs-lookup"><span data-stu-id="c2206-114">Description</span></span>|
|---|---|
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="c2206-115"><xref:System.IO.Ports.SerialPort> オブジェクトでのシリアル ポート通信の確立に使用する制御プロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="c2206-115">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="c2206-116"><xref:System.IO.Ports.SerialPort> オブジェクトのパリティ ビットを指定します。</span><span class="sxs-lookup"><span data-stu-id="c2206-116">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="c2206-117"><xref:System.IO.Ports.SerialPort> オブジェクトのシリアル ポートで受信した文字の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2206-117">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="c2206-118"><xref:System.IO.Ports.SerialPort> オブジェクトで発生するエラーを指定します。</span><span class="sxs-lookup"><span data-stu-id="c2206-118">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="c2206-119"><xref:System.IO.Ports.SerialPort> オブジェクトで発生した変更の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2206-119">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="c2206-120"><xref:System.IO.Ports.SerialPort> オブジェクトで使用するストップ ビットの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2206-120">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c2206-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2206-121">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="c2206-122">コンピューターのポートへのアクセス</span><span class="sxs-lookup"><span data-stu-id="c2206-122">Accessing the Computer's Ports</span></span>](accessing-the-computer-s-ports.md)
