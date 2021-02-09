---
description: '詳細情報: サウンドの再生 (Visual Basic)'
title: サウンドの再生
ms.date: 07/20/2015
helpviewer_keywords:
- system sounds, playing
- system sounds
- playing sounds, Visual Basic
- sound loops
- My.Computer.Audio object, tasks
- sounds, playing
- sounds, background
- playing sounds
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
ms.openlocfilehash: 247af8274108ca8374cf87e53aa2aaad8e5e736c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641513"
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="59052-103">サウンドの再生 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59052-103">Playing Sounds (Visual Basic)</span></span>

<span data-ttu-id="59052-104">`My.Computer.Audio` オブジェクトには、サウンドを再生するためのメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="59052-104">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="59052-105">サウンドの再生</span><span class="sxs-lookup"><span data-stu-id="59052-105">Playing Sounds</span></span>  

 <span data-ttu-id="59052-106">バックグラウンド再生により、アプリケーションでサウンドを再生しながら他のコードを実行できます。</span><span class="sxs-lookup"><span data-stu-id="59052-106">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="59052-107">`My.Computer.Audio.Play` メソッドを使用すると、アプリケーションでバックグラウンド サウンドを一度に 1 つだけ再生できます。アプリケーションで新しいバックグラウンド サウンドが再生されると、その前のバックグラウンド サウンドの再生は停止します。</span><span class="sxs-lookup"><span data-stu-id="59052-107">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="59052-108">また、サウンドを再生してから、その再生が完了するまで待機することもできます。</span><span class="sxs-lookup"><span data-stu-id="59052-108">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="59052-109">次の例では、`My.Computer.Audio.Play` メソッドによってサウンドが再生されます。</span><span class="sxs-lookup"><span data-stu-id="59052-109">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="59052-110">`AudioPlayMode.WaitToComplete` が指定されている場合、`My.Computer.Audio.Play` はサウンドの再生が完了するまで待機し、その後呼び出し元のコードが処理を再開します。</span><span class="sxs-lookup"><span data-stu-id="59052-110">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="59052-111">この例を使用する場合は、必ず自分のコンピューター上の .wav サウンド ファイルを示すファイル名を指定してください。</span><span class="sxs-lookup"><span data-stu-id="59052-111">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 <span data-ttu-id="59052-112">次の例では、`My.Computer.Audio.Play` メソッドによってサウンドが再生されます。</span><span class="sxs-lookup"><span data-stu-id="59052-112">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="59052-113">この例を使用する場合は、アプリケーション リソースに Waterfall という名前の .wav サウンド ファイルが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="59052-113">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="59052-114">ループ サウンドの再生</span><span class="sxs-lookup"><span data-stu-id="59052-114">Playing Looping Sounds</span></span>  

 <span data-ttu-id="59052-115">次の例では、`PlayMode.BackgroundLoop` が指定されている場合に、指定されているサウンドが `My.Computer.Audio.Play` メソッドによってバックグラウンドで再生されます。</span><span class="sxs-lookup"><span data-stu-id="59052-115">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="59052-116">この例を使用する場合は、必ず自分のコンピューター上の .wav サウンド ファイルを示すファイル名を指定してください。</span><span class="sxs-lookup"><span data-stu-id="59052-116">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 <span data-ttu-id="59052-117">次の例では、`PlayMode.BackgroundLoop` が指定されている場合に、指定されているサウンドが `My.Computer.Audio.Play` メソッドによってバックグラウンドで再生されます。</span><span class="sxs-lookup"><span data-stu-id="59052-117">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="59052-118">この例を使用する場合は、アプリケーション リソースに Waterfall という名前の .wav サウンド ファイルが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="59052-118">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 <span data-ttu-id="59052-119">上記のコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="59052-119">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="59052-120">コード スニペット ピッカーでこのスニペットにアクセスするには、**[Windows フォーム アプリケーション]、[サウンド]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="59052-120">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="59052-121">詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59052-121">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="59052-122">一般に、アプリケーションでループ サウンドを再生する場合は、最終的にそのサウンドを停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59052-122">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="59052-123">バックグラウンドで再生しているサウンドの停止</span><span class="sxs-lookup"><span data-stu-id="59052-123">Stopping the Playing of Sounds in the Background</span></span>  

 <span data-ttu-id="59052-124">`My.Computer.Audio.Stop` メソッドを使用し、アプリケーションで現在再生中のバックグラウンド サウンドまたはループ サウンドを停止します。</span><span class="sxs-lookup"><span data-stu-id="59052-124">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="59052-125">一般に、アプリケーションでループ サウンドを再生する場合は、どこかの時点でそのサウンドを停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59052-125">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="59052-126">次の例では、バックグラウンドで再生中のサウンドを停止します。</span><span class="sxs-lookup"><span data-stu-id="59052-126">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 <span data-ttu-id="59052-127">上記のコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="59052-127">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="59052-128">コード スニペット ピッカーでこのスニペットにアクセスするには、**[Windows フォーム アプリケーション]、[サウンド]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="59052-128">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="59052-129">詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59052-129">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="59052-130">システム サウンドの再生</span><span class="sxs-lookup"><span data-stu-id="59052-130">Playing System Sounds</span></span>  

 <span data-ttu-id="59052-131">`My.Computer.Audio.PlaySystemSound` メソッドを使用して、指定したシステム サウンドを再生します。</span><span class="sxs-lookup"><span data-stu-id="59052-131">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="59052-132">`My.Computer.Audio.PlaySystemSound` メソッドは、<xref:System.Media.SystemSound> クラスのいずれかの共有メンバーをパラメーターとして受け取ります。</span><span class="sxs-lookup"><span data-stu-id="59052-132">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="59052-133">システム サウンド <xref:System.Media.SystemSounds.Asterisk%2A> は、一般にエラーを表します。</span><span class="sxs-lookup"><span data-stu-id="59052-133">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="59052-134">次の例では、`My.Computer.Audio.PlaySystemSound` メソッドを使用してシステム サウンドを再生しています。</span><span class="sxs-lookup"><span data-stu-id="59052-134">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="59052-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="59052-135">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
