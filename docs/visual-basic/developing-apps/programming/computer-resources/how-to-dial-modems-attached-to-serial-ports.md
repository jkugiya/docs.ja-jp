---
description: '詳細情報: 方法:Visual Basic で、シリアル ポートに接続されているモデムをダイヤルする'
title: '方法: シリアル ポートに接続されているモデムをダイヤルする'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: 016a3f768020c551c4f4ca7f5a097f4f1f9d07d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797706"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="5f087-103">方法 : Visual Basic で、シリアル ポートに接続されているモデムをダイヤルする</span><span class="sxs-lookup"><span data-stu-id="5f087-103">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="5f087-104">このトピックでは、Visual Basic で `My.Computer.Ports` を使用してモデムをダイヤルする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f087-104">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="5f087-105">通常、モデムはコンピューターのいずれかのシリアル ポートに接続されています。</span><span class="sxs-lookup"><span data-stu-id="5f087-105">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="5f087-106">アプリケーションがモデムとやり取りするには、適切なシリアル ポートにコマンドを送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f087-106">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="5f087-107">モデムをダイヤルするには</span><span class="sxs-lookup"><span data-stu-id="5f087-107">To dial a modem</span></span>  
  
1. <span data-ttu-id="5f087-108">モデムが接続されているシリアル ポートを確認します。</span><span class="sxs-lookup"><span data-stu-id="5f087-108">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="5f087-109">この例では、モデムが COM1 に接続されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="5f087-109">This example assumes the modem is on COM1.</span></span>  
  
2. <span data-ttu-id="5f087-110">`My.Computer.Ports.OpenSerialPort` メソッドを使用して、ポートへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="5f087-110">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="5f087-111">詳細については、「<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f087-111">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="5f087-112">`Using` ブロックを使用すると、アプリケーションは、例外を生成した場合でもシリアル ポートを閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="5f087-112">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="5f087-113">シリアル ポートを操作するコードはすべて、このブロックまたは `Try...Catch...Finally` ブロック内に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f087-113">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. <span data-ttu-id="5f087-114">コンピューターがモデムからの伝送を受け取る準備ができたことを示しよう `DtrEnable` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="5f087-114">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. <span data-ttu-id="5f087-115"><xref:System.IO.Ports.SerialPort.Write%2A> メソッドを使用して、ダイヤル コマンドと電話番号をシリアル ポート経由でモデムに送信します。</span><span class="sxs-lookup"><span data-stu-id="5f087-115">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="5f087-116">例</span><span class="sxs-lookup"><span data-stu-id="5f087-116">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 <span data-ttu-id="5f087-117">このコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="5f087-117">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="5f087-118">コード スニペット ピッカーでは、これは **[接続とネットワーク]** にあります。</span><span class="sxs-lookup"><span data-stu-id="5f087-118">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="5f087-119">詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f087-119">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5f087-120">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="5f087-120">Compiling the Code</span></span>  

 <span data-ttu-id="5f087-121">この例では、<xref:System?displayProperty=nameWithType> 名前空間への参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="5f087-121">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5f087-122">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="5f087-122">Robust Programming</span></span>  

 <span data-ttu-id="5f087-123">この例では、モデムが COM1 に接続されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="5f087-123">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="5f087-124">コードによって、利用可能なシリアル ポートの一覧から、目的のポートをユーザーが選択できるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5f087-124">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="5f087-125">詳しくは、「[方法: 利用可能なシリアル ポートを表示する](how-to-show-available-serial-ports.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5f087-125">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="5f087-126">この例では、アプリケーションが例外をスローした場合でもポートを閉じられるよう、`Using` ブロックを使用しています。</span><span class="sxs-lookup"><span data-stu-id="5f087-126">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="5f087-127">詳細については、「[Using ステートメント](../../../language-reference/statements/using-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f087-127">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="5f087-128">この例では、アプリケーションは、モデムをダイヤルした後でシリアル ポートを切断しています。</span><span class="sxs-lookup"><span data-stu-id="5f087-128">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="5f087-129">実際には、モデムとの間でデータの転送が必要となります。</span><span class="sxs-lookup"><span data-stu-id="5f087-129">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="5f087-130">詳細については、「[方法: シリアル ポートから文字列を受信する](how-to-receive-strings-from-serial-ports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f087-130">For more information, see [How to: Receive Strings From Serial Ports](how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f087-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f087-131">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="5f087-132">方法: シリアル ポートに文字列を送信する</span><span class="sxs-lookup"><span data-stu-id="5f087-132">How to: Send Strings to Serial Ports</span></span>](how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="5f087-133">方法: シリアル ポートから文字列を受信する</span><span class="sxs-lookup"><span data-stu-id="5f087-133">How to: Receive Strings From Serial Ports</span></span>](how-to-receive-strings-from-serial-ports.md)
- [<span data-ttu-id="5f087-134">方法: 利用可能なシリアル ポートを表示する</span><span class="sxs-lookup"><span data-stu-id="5f087-134">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)
