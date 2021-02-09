---
description: '詳細情報: 方法:Visual Basic でシリアル ポートから文字列を受信する'
title: '方法: シリアル ポートから文字列を受信する'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: 5e6de24392c6102b6dc613d909c827cc32f513d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666538"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="843ff-103">方法 : Visual Basic でシリアル ポートから文字列を受信する</span><span class="sxs-lookup"><span data-stu-id="843ff-103">How to: Receive Strings From Serial Ports in Visual Basic</span></span>

<span data-ttu-id="843ff-104">このトピックでは、Visual Basic で `My.Computer.Ports` を使用して、コンピューターのシリアル ポートから文字列を受信する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="843ff-104">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in Visual Basic.</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="843ff-105">シリアル ポートから文字列を受信する</span><span class="sxs-lookup"><span data-stu-id="843ff-105">To receive strings from the serial port</span></span>  
  
1. <span data-ttu-id="843ff-106">戻り値の文字列を初期化します。</span><span class="sxs-lookup"><span data-stu-id="843ff-106">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. <span data-ttu-id="843ff-107">どのシリアル ポートから文字列を取得するのかを決定します。</span><span class="sxs-lookup"><span data-stu-id="843ff-107">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="843ff-108">この例では、`COM1` です。</span><span class="sxs-lookup"><span data-stu-id="843ff-108">This example assumes it is `COM1`.</span></span>  
  
3. <span data-ttu-id="843ff-109">`My.Computer.Ports.OpenSerialPort` メソッドを使用して、ポートへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="843ff-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="843ff-110">詳細については、「<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="843ff-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="843ff-111">`Try...Catch...Finally` ブロックを使用すると、アプリケーションは、例外を生成した場合でもシリアル ポートを閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="843ff-111">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="843ff-112">シリアル ポートを操作するコードはすべて、このブロック内に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="843ff-112">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. <span data-ttu-id="843ff-113">利用可能な行がなくなるまでテキスト行を読み取るための `Do` ループを作成します。</span><span class="sxs-lookup"><span data-stu-id="843ff-113">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. <span data-ttu-id="843ff-114"><xref:System.IO.Ports.SerialPort.ReadLine> メソッドを使用して、次に利用可能なテキスト行をシリアル ポートから読み取ります。</span><span class="sxs-lookup"><span data-stu-id="843ff-114">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. <span data-ttu-id="843ff-115">`If` ステートメントを使用して、<xref:System.IO.Ports.SerialPort.ReadLine> メソッドが `Nothing` を返す (つまり、利用可能なテキストがこれ以上ない) かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="843ff-115">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="843ff-116">`Nothing` を返した場合は、`Do` ループを終了します。</span><span class="sxs-lookup"><span data-stu-id="843ff-116">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. <span data-ttu-id="843ff-117">`If` ステートメントに `Else` ブロックを追加して、文字列が実際に読み取られた場合のケースを処理します。</span><span class="sxs-lookup"><span data-stu-id="843ff-117">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="843ff-118">このブロックによって、シリアル ポートからの文字列を戻り値の文字列に追加します。</span><span class="sxs-lookup"><span data-stu-id="843ff-118">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. <span data-ttu-id="843ff-119">文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="843ff-119">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a><span data-ttu-id="843ff-120">例</span><span class="sxs-lookup"><span data-stu-id="843ff-120">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 <span data-ttu-id="843ff-121">このコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="843ff-121">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="843ff-122">コード スニペット ピッカーでは、これは **[接続とネットワーク]** にあります。</span><span class="sxs-lookup"><span data-stu-id="843ff-122">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="843ff-123">詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="843ff-123">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="843ff-124">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="843ff-124">Compiling the Code</span></span>  

 <span data-ttu-id="843ff-125">この例では、コンピューターが `COM1` を使用しているものと想定しています。</span><span class="sxs-lookup"><span data-stu-id="843ff-125">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="843ff-126">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="843ff-126">Robust Programming</span></span>  

 <span data-ttu-id="843ff-127">この例では、コンピューターが `COM1` を使用しているものと想定しています。</span><span class="sxs-lookup"><span data-stu-id="843ff-127">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="843ff-128">柔軟性を高めるためには、利用可能なポートの一覧から目的のシリアル ポートを選択できるようにコードを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="843ff-128">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="843ff-129">詳しくは、「[方法: 利用可能なシリアル ポートを表示する](how-to-show-available-serial-ports.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="843ff-129">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="843ff-130">この例では、アプリケーションによってポートが閉じられ、タイムアウト例外がキャッチされるようにするために、`Try...Catch...Finally` ブロックを使用しています。</span><span class="sxs-lookup"><span data-stu-id="843ff-130">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="843ff-131">詳しくは、「[Try...Catch...Finally ステートメント](../../../language-reference/statements/try-catch-finally-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="843ff-131">For more information, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="843ff-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="843ff-132">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="843ff-133">方法: シリアル ポートに接続されているモデムをダイヤルする</span><span class="sxs-lookup"><span data-stu-id="843ff-133">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="843ff-134">方法: シリアル ポートに文字列を送信する</span><span class="sxs-lookup"><span data-stu-id="843ff-134">How to: Send Strings to Serial Ports</span></span>](how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="843ff-135">方法: 利用可能なシリアル ポートを表示する</span><span class="sxs-lookup"><span data-stu-id="843ff-135">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)
