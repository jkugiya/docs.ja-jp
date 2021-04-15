---
description: '詳細情報: 方法:Visual Basic で利用可能なシリアル ポートを表示する'
title: '方法: 利用可能なシリアル ポートを表示する'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: 7fdbd5577ca40d1a900bc9442cb4bfeedae82c64
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494572"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="2c64e-103">方法 : Visual Basic で利用可能なシリアル ポートを表示する</span><span class="sxs-lookup"><span data-stu-id="2c64e-103">How to: Show Available Serial Ports in Visual Basic</span></span>

<span data-ttu-id="2c64e-104">このトピックでは、`My.Computer.Ports` を使用して、コンピューターで利用可能なシリアルポートを Visual Basic で表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2c64e-104">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="2c64e-105">使用するポートをユーザーが選択可能とするために、シリアル ポートの名前を <xref:System.Windows.Forms.ListBox> コントロールに格納します。</span><span class="sxs-lookup"><span data-stu-id="2c64e-105">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c64e-106">例</span><span class="sxs-lookup"><span data-stu-id="2c64e-106">Example</span></span>  

 <span data-ttu-id="2c64e-107">次の例では、`My.Computer.Ports.SerialPortNames` プロパティが返す文字列のすべてについてループします。</span><span class="sxs-lookup"><span data-stu-id="2c64e-107">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="2c64e-108">これらの文字列は、コンピューターで利用可能なシリアル ポートの名前です。</span><span class="sxs-lookup"><span data-stu-id="2c64e-108">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="2c64e-109">通常、利用可能なポートの一覧から、アプリケーションで使用するシリアル ポートをユーザーが選択します。</span><span class="sxs-lookup"><span data-stu-id="2c64e-109">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="2c64e-110">この例では、シリアル ポート名は <xref:System.Windows.Forms.ListBox> コントロールに格納されます。</span><span class="sxs-lookup"><span data-stu-id="2c64e-110">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="2c64e-111">詳細については、「[ListBox コントロール](/dotnet/desktop/winforms/controls/listbox-control-windows-forms)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c64e-111">For more information, see [ListBox Control](/dotnet/desktop/winforms/controls/listbox-control-windows-forms).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="2c64e-112">このコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="2c64e-112">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="2c64e-113">コード スニペット ピッカーでは、これは **[接続とネットワーク]** にあります。</span><span class="sxs-lookup"><span data-stu-id="2c64e-113">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="2c64e-114">詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c64e-114">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2c64e-115">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="2c64e-115">Compiling the Code</span></span>  

 <span data-ttu-id="2c64e-116">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2c64e-116">This example requires:</span></span>  
  
- <span data-ttu-id="2c64e-117">System.Windows.Forms.dll へのプロジェクト参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="2c64e-117">A project reference to System.Windows.Forms.dll.</span></span>  
  
- <span data-ttu-id="2c64e-118"><xref:System.Windows.Forms> 名前空間のメンバーへのアクセス許可。</span><span class="sxs-lookup"><span data-stu-id="2c64e-118">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="2c64e-119">コード内でメンバー名を完全修飾していない場合は、`Imports` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="2c64e-119">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="2c64e-120">詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c64e-120">For more information, see [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
- <span data-ttu-id="2c64e-121">`ListBox1` という名前の <xref:System.Windows.Forms.ListBox> コントロールを持つフォーム。</span><span class="sxs-lookup"><span data-stu-id="2c64e-121">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2c64e-122">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="2c64e-122">Robust Programming</span></span>  

 <span data-ttu-id="2c64e-123">利用可能なシリアル ポートの名前を表示するために、<xref:System.Windows.Forms.ListBox> コントロールを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2c64e-123">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="2c64e-124">代わりに、<xref:System.Windows.Forms.ComboBox> やその他のコントロールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2c64e-124">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="2c64e-125">ユーザーからの応答が不要なアプリケーションの場合、<xref:System.Windows.Forms.TextBox> コントロールを使用して情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="2c64e-125">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2c64e-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c64e-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="2c64e-127">方法: シリアル ポートに接続されているモデムをダイヤルする</span><span class="sxs-lookup"><span data-stu-id="2c64e-127">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="2c64e-128">方法: シリアル ポートに文字列を送信する</span><span class="sxs-lookup"><span data-stu-id="2c64e-128">How to: Send Strings to Serial Ports</span></span>](how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="2c64e-129">方法: シリアル ポートから文字列を受信する</span><span class="sxs-lookup"><span data-stu-id="2c64e-129">How to: Receive Strings From Serial Ports</span></span>](how-to-receive-strings-from-serial-ports.md)
