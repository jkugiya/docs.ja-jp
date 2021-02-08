---
description: '詳細情報: コンピューター リソースへのアクセス (Visual Basic)'
title: コンピューター リソースへのアクセス
ms.date: 07/20/2015
helpviewer_keywords:
- computer resources [Visual Basic]
- My.Computer object [Visual Basic], tasks
- computer resources [Visual Basic], accessing
ms.assetid: 75b81c88-f7c0-46e0-95c8-0c006d2120f9
ms.openlocfilehash: 20b91557bb5940be048f9c38e03b087c07f96c85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792337"
---
# <a name="accessing-computer-resources-visual-basic"></a><span data-ttu-id="714cc-103">コンピューター リソースへのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="714cc-103">Accessing computer resources (Visual Basic)</span></span>

<span data-ttu-id="714cc-104">`My.Computer` オブジェクトは、`My` の中心となる 3 つのオブジェクトの 1 つであり、情報とよく使用される機能へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="714cc-104">The `My.Computer` object is one of the three central objects in `My`, providing access to information and commonly used functionality.</span></span> <span data-ttu-id="714cc-105">`My.Computer` には、アプリケーションが実行されているコンピューターにアクセスするためのメソッド、プロパティ、イベントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="714cc-105">`My.Computer` provides methods, properties, and events for accessing the computer on which the application is running.</span></span> <span data-ttu-id="714cc-106">そのオブジェクトには、以下のものがあります。</span><span class="sxs-lookup"><span data-stu-id="714cc-106">Its objects include:</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <span data-ttu-id="714cc-107">クリップボード (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span><span class="sxs-lookup"><span data-stu-id="714cc-107">Clipboard (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span></span>
- <xref:Microsoft.VisualBasic.Devices.Clock>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
- <xref:Microsoft.VisualBasic.Devices.Keyboard>
- <xref:Microsoft.VisualBasic.Devices.Mouse>
- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <span data-ttu-id="714cc-108">レジストリ (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span><span class="sxs-lookup"><span data-stu-id="714cc-108">Registry (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span></span>

## <a name="in-this-section"></a><span data-ttu-id="714cc-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="714cc-109">In this section</span></span>

[<span data-ttu-id="714cc-110">サウンドの再生</span><span class="sxs-lookup"><span data-stu-id="714cc-110">Playing Sounds</span></span>](playing-sounds.md)  
<span data-ttu-id="714cc-111">`My.Computer.Audio` に関連付けられたタスクを一覧表示します (例: バックグラウンドでのサウンドの再生)。</span><span class="sxs-lookup"><span data-stu-id="714cc-111">Lists tasks associated with `My.Computer.Audio`, such as playing a sound in the background.</span></span>

[<span data-ttu-id="714cc-112">クリップボードのデータの格納と読み取り</span><span class="sxs-lookup"><span data-stu-id="714cc-112">Storing Data to and Reading from the Clipboard</span></span>](storing-data-to-and-reading-from-the-clipboard.md)  
<span data-ttu-id="714cc-113">`My.Computer.Clipboard` に関連付けられたタスクを一覧表示します (例: クリップボードからのデータ読み取り、またはクリップボードへのデータ書き込み)。</span><span class="sxs-lookup"><span data-stu-id="714cc-113">Lists tasks associated with `My.Computer.Clipboard`, such as reading data from or writing data to the Clipboard.</span></span>

[<span data-ttu-id="714cc-114">コンピューターについての情報の取得</span><span class="sxs-lookup"><span data-stu-id="714cc-114">Getting Information about the Computer</span></span>](getting-information-about-the-computer.md)  
<span data-ttu-id="714cc-115">`My.Computer.Info` に関連付けられたタスクを一覧表示します (例: コンピューターの完全な名前または IP アドレスの特定)。</span><span class="sxs-lookup"><span data-stu-id="714cc-115">Lists tasks associated with `My.Computer.Info`, such as determining a computer's full name or IP addresses.</span></span>

[<span data-ttu-id="714cc-116">キーボードへのアクセス</span><span class="sxs-lookup"><span data-stu-id="714cc-116">Accessing the Keyboard</span></span>](accessing-the-keyboard.md)  
<span data-ttu-id="714cc-117">`My.Computer.Keyboard` に関連付けられたタスクを一覧表示します (例: CapsLock がオンになっているかどうかの特定)。</span><span class="sxs-lookup"><span data-stu-id="714cc-117">Lists tasks associated with `My.Computer.Keyboard`, such as determining whether CAPS LOCK is on.</span></span>

[<span data-ttu-id="714cc-118">マウスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="714cc-118">Accessing the Mouse</span></span>](accessing-the-mouse.md)  
<span data-ttu-id="714cc-119">`My.Computer.Mouse` に関連付けられたタスクを一覧表示します (例: マウスの有無の特定)。</span><span class="sxs-lookup"><span data-stu-id="714cc-119">Lists tasks associated with `My.Computer.Mouse`, such as determining whether a mouse is present.</span></span>

[<span data-ttu-id="714cc-120">ネットワーク操作の実行</span><span class="sxs-lookup"><span data-stu-id="714cc-120">Performing Network Operations</span></span>](performing-network-operations.md)  
<span data-ttu-id="714cc-121">`My.Computer.Network` に関連付けられたタスクを一覧表示します (例: ファイルのアップロードまたはダウンロード)。</span><span class="sxs-lookup"><span data-stu-id="714cc-121">Lists tasks associated with `My.Computer.Network`, such as uploading or downloading files.</span></span>

[<span data-ttu-id="714cc-122">コンピューターのポートへのアクセス</span><span class="sxs-lookup"><span data-stu-id="714cc-122">Accessing the Computer's Ports</span></span>](accessing-the-computer-s-ports.md)  
<span data-ttu-id="714cc-123">`My.Computer.Ports` に関連付けられたタスクを一覧表示します (例: 使用できるシリアル ポートの表示、またはシリアル ポートへの文字列の送信)。</span><span class="sxs-lookup"><span data-stu-id="714cc-123">Lists tasks associated with `My.Computer.Ports`, such as showing available serial ports or sending strings to serial ports.</span></span>

[<span data-ttu-id="714cc-124">レジストリからの読み取りとレジストリへの書き込み</span><span class="sxs-lookup"><span data-stu-id="714cc-124">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)  
<span data-ttu-id="714cc-125">`My.Computer.Registry` に関連付けられたタスクを一覧表示します (例: レジストリ キーからのデータ読み取り、またはレジストリ キーへのデータ書き込み)。</span><span class="sxs-lookup"><span data-stu-id="714cc-125">Lists tasks associated with `My.Computer.Registry`, such as reading data from or writing data to registry keys.</span></span>
