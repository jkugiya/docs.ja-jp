---
description: '詳細情報: 方法:Visual Basic でシリアル ポートに文字列を送信する'
title: '方法: シリアル ポートに文字列を送信する'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: 66dedaab05090af2659701e57b37b4813447b8ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666486"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="ba263-103">方法 : Visual Basic でシリアル ポートに文字列を送信する</span><span class="sxs-lookup"><span data-stu-id="ba263-103">How to: Send Strings to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="ba263-104">このトピックでは、`My.Computer.Ports` を使用して、Visual Basic でコンピューターのシリアルポートに文字列を送信する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba263-104">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba263-105">例</span><span class="sxs-lookup"><span data-stu-id="ba263-105">Example</span></span>  

 <span data-ttu-id="ba263-106">この例では、COM1 シリアル ポートに文字列を送信します。</span><span class="sxs-lookup"><span data-stu-id="ba263-106">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="ba263-107">コンピューターによっては、別のシリアル ポートを使用する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba263-107">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="ba263-108">`My.Computer.Ports.OpenSerialPort` メソッドを使用して、ポートへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="ba263-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="ba263-109">詳細については、「<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba263-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="ba263-110">`Using` ブロックを使用すると、アプリケーションは、例外を生成した場合でもシリアル ポートを閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="ba263-110">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="ba263-111">シリアル ポートを操作するコードはすべて、このブロックまたは `Try...Catch...Finally` ブロック内に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba263-111">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="ba263-112"><xref:System.IO.Ports.SerialPort.WriteLine%2A> メソッドで、データをシリアル ポートに送信しています。</span><span class="sxs-lookup"><span data-stu-id="ba263-112">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ba263-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="ba263-113">Compiling the Code</span></span>  
  
- <span data-ttu-id="ba263-114">この例では、コンピューターが `COM1` を使用しているものと想定しています。</span><span class="sxs-lookup"><span data-stu-id="ba263-114">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ba263-115">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="ba263-115">Robust Programming</span></span>  

 <span data-ttu-id="ba263-116">この例では、コンピューターが `COM1` を使用しているものと想定しています。実際に作成するコードでは、柔軟性を高めるために、利用可能なポートの一覧から目的のシリアル ポートを選択できるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ba263-116">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="ba263-117">詳しくは、「[方法: 利用可能なシリアル ポートを表示する](how-to-show-available-serial-ports.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ba263-117">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="ba263-118">この例では、アプリケーションが例外をスローした場合でもポートを閉じられるよう、`Using` ブロックを使用しています。</span><span class="sxs-lookup"><span data-stu-id="ba263-118">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="ba263-119">詳細については、「[Using ステートメント](../../../language-reference/statements/using-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba263-119">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba263-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba263-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="ba263-121">方法: シリアル ポートに接続されているモデムをダイヤルする</span><span class="sxs-lookup"><span data-stu-id="ba263-121">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="ba263-122">方法: 利用可能なシリアル ポートを表示する</span><span class="sxs-lookup"><span data-stu-id="ba263-122">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)
