---
title: '方法: Windows サービス アプリケーションをデバッグする'
description: Windows サービス アプリケーションをデバッグする方法を理解します。これは、その他の種類の Visual Studio アプリケーションをデバッグするように単純ではありません。
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
ms.openlocfilehash: 29ab09e0de024ed4256dc5be6bd8e54ff28b101b
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494533"
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="21127-103">方法: Windows サービス アプリケーションをデバッグする</span><span class="sxs-lookup"><span data-stu-id="21127-103">How to: Debug Windows Service Applications</span></span>

<span data-ttu-id="21127-104">サービスは、Visual Studio 内からではなく、サービス コントロール マネージャーのコンテキスト内から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21127-104">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="21127-105">そのため、サービスのデバッグは、その他の種類の Visual Studio アプリケーションをデバッグするように単純ではありません。</span><span class="sxs-lookup"><span data-stu-id="21127-105">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="21127-106">サービスのデバッグを行うには、サービスを起動してから、サービスを実行しているプロセスにデバッガーをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="21127-106">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="21127-107">これにより、Visual Studio のすべての標準デバッグ機能を使用して、アプリケーションをデバッグできるようになります。</span><span class="sxs-lookup"><span data-stu-id="21127-107">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="21127-108">プロセスが強制終了される可能性もあるため、アタッチするプロセスの特性や、アタッチによる影響をよく理解している場合に限って、プロセスにデバッガーをアタッチしてください。</span><span class="sxs-lookup"><span data-stu-id="21127-108">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="21127-109">たとえば、システムは WinLogon プロセスがないと動作しないため、WinLogon プロセスにデバッガーをアタッチした後でデバッグを中止すると、システムは停止します。</span><span class="sxs-lookup"><span data-stu-id="21127-109">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="21127-110">デバッガーをアタッチできるのは、実行中のサービスだけです。</span><span class="sxs-lookup"><span data-stu-id="21127-110">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="21127-111">アタッチのプロセスは、サービスが現在実行している処理に割り込みます。実際にサービスの処理の停止や一時停止を行うのではありません。</span><span class="sxs-lookup"><span data-stu-id="21127-111">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="21127-112">つまり、実行中のサービスに対してデバッグを開始すると、デバッグの間、サービスは技術的には起動状態のままですが、処理は中断されます。</span><span class="sxs-lookup"><span data-stu-id="21127-112">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="21127-113">プロセスにデバッガーをアタッチした後で、ブレークポイントを設定し、設定したブレークポイントを使用してコードをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="21127-113">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="21127-114">プロセスへのアタッチに使用するダイアログ ボックスを閉じると、デバッグ モードが有効になります。</span><span class="sxs-lookup"><span data-stu-id="21127-114">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="21127-115">サービス コントロール マネージャーを使用して、サービスの開始、停止、一時停止、および再開を行うことができます。これによって、設定したブレークポイントにヒットします。</span><span class="sxs-lookup"><span data-stu-id="21127-115">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="21127-116">デバッグが正常に完了したら、このダミー サービスを削除できます。</span><span class="sxs-lookup"><span data-stu-id="21127-116">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="21127-117">この記事ではローカル コンピューターで実行されているサービスのデバッグについて説明しますが、リモート コンピューターで実行されている Windows サービスをデバッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="21127-117">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="21127-118">「[リモート デバッグ](/visualstudio/debugger/debug-installed-app-package)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="21127-118">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21127-119">サービス コントロール マネージャーではすべてのサービスの開始試行に対して 30 秒の制限が適用されるため、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドのデバッグが困難になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="21127-119">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="21127-120">詳細については、[トラブルシューティング:Windows サービスのデバッグ](troubleshooting-debugging-windows-services.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="21127-120">For more information, see [Troubleshooting: Debugging Windows Services](troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="21127-121">デバッグに有用な情報を取得するためには、Visual Studio デバッガーは、デバッグ対象のバイナリのシンボル ファイルを検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21127-121">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="21127-122">Visual Studio に組み込まれているサービスをデバッグしている場合は、シンボル ファイル (.pdb ファイル) は実行可能ファイルまたはライブラリと同じフォルダーにあり、デバッガーはそれらを自動的に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="21127-122">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="21127-123">構築していないサービスをデバッグしている場合は、最初にサービスのシンボルを検索し、デバッガーでこれらを検出できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="21127-123">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="21127-124">「[Specify Symbol (.pdb) and Source Files in the Visual Studio Debugger (Visual Studio デバッガーでシンボル ファイル (.pdb) とソース ファイルを指定する)](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="21127-124">See [Specify Symbol (.pdb) and Source Files in the Visual Studio Debugger](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span> <span data-ttu-id="21127-125">システム プロセスをデバッグしているか、サービスにシステム呼び出しのシンボルを含めたい場合は、Microsoft シンボル サーバーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21127-125">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="21127-126">[シンボルによるデバッグ](/windows/desktop/DxTechArts/debugging-with-symbols)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="21127-126">See [Debugging Symbols](/windows/desktop/DxTechArts/debugging-with-symbols).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="21127-127">サービスをデバッグするには</span><span class="sxs-lookup"><span data-stu-id="21127-127">To debug a service</span></span>  
  
1. <span data-ttu-id="21127-128">サービスをデバッグ構成で構築します。</span><span class="sxs-lookup"><span data-stu-id="21127-128">Build your service in the Debug configuration.</span></span>  
  
2. <span data-ttu-id="21127-129">サービスをインストールします。</span><span class="sxs-lookup"><span data-stu-id="21127-129">Install your service.</span></span> <span data-ttu-id="21127-130">詳細については、[サービスをインストールおよびアンインストールする](how-to-install-and-uninstall-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21127-130">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
3. <span data-ttu-id="21127-131">**サービス コントロール マネージャー**、**サーバー エクスプローラー**、またはコードで、サービスを起動します。</span><span class="sxs-lookup"><span data-stu-id="21127-131">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="21127-132">詳細については、[サービスを開始する](how-to-start-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21127-132">For more information, see [How to: Start Services](how-to-start-services.md).</span></span>  
  
4. <span data-ttu-id="21127-133">システム プロセスにアタッチすることができるように、管理者資格情報を使用して Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="21127-133">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5. <span data-ttu-id="21127-134">(省略可能) Visual Studio のメニュー バーで **[ツール]** 、 **[オプション]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="21127-134">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="21127-135">**[オプション]** ダイアログ ボックスで、 **[デバッグ]** 、 **[シンボル]** の順に選択し、 **[Microsoft シンボル サーバー]** チェック ボックスをオンにし、 **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="21127-135">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6. <span data-ttu-id="21127-136">メニュー バーの **[デバッグ]** または **[ツール]** メニューで、 **[プロセスにアタッチ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="21127-136">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="21127-137">(キーボード:Ctrl + Alt + P)</span><span class="sxs-lookup"><span data-stu-id="21127-137">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="21127-138">**[プロセス]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="21127-138">The **Processes** dialog box appears.</span></span>  
  
7. <span data-ttu-id="21127-139">**[全ユーザーのプロセスを表示する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="21127-139">Select the **Show processes from all users** check box.</span></span>  
  
8. <span data-ttu-id="21127-140">**[選択可能なプロセス]** セクションでサービスのプロセスを選択し、 **[アタッチ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="21127-140">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="21127-141">プロセスの名前は、サービスの実行可能ファイルの名前と同じになります。</span><span class="sxs-lookup"><span data-stu-id="21127-141">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="21127-142">**[プロセスにアタッチ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="21127-142">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="21127-143">適切なオプションを選択し、 **[OK]** を選択してダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="21127-143">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="21127-144">デバッグ モードになります。</span><span class="sxs-lookup"><span data-stu-id="21127-144">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="21127-145">コード内で使用する任意のブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="21127-145">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="21127-146">サービス コントロール マネージャーを起動し、停止、一時停止、再開の各コマンドを送信してサービスを操作して、ブレークポイントをヒットします。</span><span class="sxs-lookup"><span data-stu-id="21127-146">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="21127-147">サービス コントロール マネージャーの実行方法の詳細については、「[方法:サービスを開始する](how-to-start-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21127-147">For more information about running the Services Control Manager, see [How to: Start Services](how-to-start-services.md).</span></span> <span data-ttu-id="21127-148">[トラブルシューティング:Windows サービスのデバッグ](troubleshooting-debugging-windows-services.md)に関するページもご覧ください。</span><span class="sxs-lookup"><span data-stu-id="21127-148">Also, see [Troubleshooting: Debugging Windows Services](troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="21127-149">Windows サービスのデバッグのヒント</span><span class="sxs-lookup"><span data-stu-id="21127-149">Debugging Tips for Windows Services</span></span>  

 <span data-ttu-id="21127-150">サービスのプロセスにアタッチすると、そのサービスのコードのほとんど (すべてではない) をデバッグすることができます。</span><span class="sxs-lookup"><span data-stu-id="21127-150">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="21127-151">たとえば、サービスが既に開始されているため、そのサービスの <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッド内のコード、またはサービスをこの方法で読み込むために使用されている `Main` メソッド内のコードは、デバッグすることができません。</span><span class="sxs-lookup"><span data-stu-id="21127-151">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="21127-152">この制限に対処する方法の 1 つは、デバッグ専用の一時的な "ダミー" サービスを作成し、サービス アプリケーションに追加することです。</span><span class="sxs-lookup"><span data-stu-id="21127-152">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="21127-153">サービスを両方ともインストールし、ダミー サービスを開始してサービス プロセスを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="21127-153">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="21127-154">"ダミー" サービスがプロセスを起動した後は、Visual Studio の **[デバッグ]** メニューで、サービス プロセスへのアタッチを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="21127-154">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="21127-155"><xref:System.Threading.Thread.Sleep%2A> メソッドに呼び出しを追加して、プロセスにアタッチできるようになるまで動作を遅延します。</span><span class="sxs-lookup"><span data-stu-id="21127-155">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="21127-156">プログラムを通常のコンソール アプリケーションに変更します。</span><span class="sxs-lookup"><span data-stu-id="21127-156">Try changing the program to a regular console application.</span></span> <span data-ttu-id="21127-157">このためには、起動方法に応じて Windows サービスとコンソール アプリケーションの両方として実行することができるように、`Main` メソッドを次のように書き換えます。</span><span class="sxs-lookup"><span data-stu-id="21127-157">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="21127-158">方法: Windows サービスをコンソール アプリケーションとして実行する</span><span class="sxs-lookup"><span data-stu-id="21127-158">How to: Run a Windows Service as a console application</span></span>  
  
1. <span data-ttu-id="21127-159"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドと <xref:System.ServiceProcess.ServiceBase.OnStop%2A> メソッドを実行するサービスにメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="21127-159">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2. <span data-ttu-id="21127-160">`Main` メソッドを次のように書き換えます。</span><span class="sxs-lookup"><span data-stu-id="21127-160">Rewrite the `Main` method as follows:</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        if (Environment.UserInteractive)  
        {  
            MyNewService service1 = new MyNewService(args);  
            service1.TestStartupAndStop(args);  
        }  
        else  
        {  
            // Put the body of your old Main method here.  
        }  
    }
    ```  
  
3. <span data-ttu-id="21127-161">プロジェクトのプロパティの **[アプリケーション]** タブで、 **[出力の種類]** を **[コンソール アプリケーション]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="21127-161">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4. <span data-ttu-id="21127-162">**[デバッグの開始]** を選択します (F5)。</span><span class="sxs-lookup"><span data-stu-id="21127-162">Choose **Start Debugging** (F5).</span></span>  
  
5. <span data-ttu-id="21127-163">プログラムを再度 Windows サービスとして実行するには、プログラムをインストールして、Windows サービスとして通常どおり起動します。</span><span class="sxs-lookup"><span data-stu-id="21127-163">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="21127-164">これらの変更を反対にする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="21127-164">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="21127-165">システムの起動時にのみ発生する問題をデバッグするときなどのいくつかのケースでは、Windows デバッガーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21127-165">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="21127-166">[Windows Driver Kit (WDK) をダウンロード](/windows-hardware/drivers/download-the-wdk)し、「[Windows サービスをデバッグする方法](https://support.microsoft.com/kb/824344)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="21127-166">[Download the Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk) and see [How to debug Windows Services](https://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21127-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="21127-167">See also</span></span>

- [<span data-ttu-id="21127-168">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="21127-168">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="21127-169">方法: サービスをインストールおよびアンインストールする</span><span class="sxs-lookup"><span data-stu-id="21127-169">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="21127-170">方法: サービスを開始する</span><span class="sxs-lookup"><span data-stu-id="21127-170">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="21127-171">サービスのデバッグ</span><span class="sxs-lookup"><span data-stu-id="21127-171">Debugging a Service</span></span>](/windows/desktop/Services/debugging-a-service)
