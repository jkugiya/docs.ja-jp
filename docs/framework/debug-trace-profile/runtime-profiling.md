---
title: ランタイム プロファイリング
description: 任意の開発シナリオまたは配置シナリオでパフォーマンス データを収集する方法の 1 つである .NET でのランタイム プロファイリングについて調べます。
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters
- common language runtime, profiling
- Perfmon.exe
- System Monitor
- profiling
- runtime, profiling
- profiling applications
- Performance Console
ms.assetid: ccd68284-f3a8-47b8-bc3f-92e5fe3a1640
ms.openlocfilehash: 5d1542c7f6afa2d683240d6d5cca837b961eb3be
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267105"
---
# <a name="runtime-profiling"></a><span data-ttu-id="2b4e6-103">ランタイム プロファイリング</span><span class="sxs-lookup"><span data-stu-id="2b4e6-103">Runtime Profiling</span></span>

<span data-ttu-id="2b4e6-104">プロファイリングは、任意の開発シナリオまたは配置シナリオでパフォーマンス データを収集する方法の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-104">Profiling is a method of gathering performance data in any development or deployment scenario.</span></span> <span data-ttu-id="2b4e6-105">このセクションは、アプリケーションのパフォーマンスに関する情報の収集を必要とする開発者およびシステム管理者を対象にしています。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-105">This section is for developers and system administrators who want to gather information about application performance.</span></span>  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a><span data-ttu-id="2b4e6-106">パフォーマンス モニター (Perfmon.exe) を使用したパフォーマンスの追跡</span><span class="sxs-lookup"><span data-stu-id="2b4e6-106">Tracking Performance Using the Performance Monitor (Perfmon.exe)</span></span>  

 <span data-ttu-id="2b4e6-107">パフォーマンス モニターは、.NET Framework アプリケーションをプロファイリングする場合に最も使いやすいツールです。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-107">The Performance Monitor is the easiest tool to use to profile your .NET Framework application.</span></span> <span data-ttu-id="2b4e6-108">パフォーマンス モニターは、共通言語ランタイムおよび Windows SDK と共にインストールされる .NET Framework パフォーマンス カウンター内のデータをグラフィカルに表示します。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-108">The Performance Monitor graphically represents data found in the .NET Framework performance counters that are installed with the common language runtime and the Windows SDK.</span></span> <span data-ttu-id="2b4e6-109">これらのカウンターを使用することにより、メモリ管理から Just-In-Time (JIT) コンパイラのパフォーマンスまで、あらゆる情報を監視できます。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-109">These counters can be used to monitor everything from memory management to just-in-time (JIT) compiler performance.</span></span> <span data-ttu-id="2b4e6-110">.NET パフォーマンス カウンターは、アプリケーションが使用するリソースに関する情報を提供します。この情報は、アプリケーションのパフォーマンスを判断するための間接的な指標となります。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-110">They tell you about the resources your application uses, which is an indirect measure of your application's performance.</span></span> <span data-ttu-id="2b4e6-111">これらのカウンターは、アプリケーション内部の動作状況を把握するために使用します。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-111">Use these counters to understand how your application works internally.</span></span>  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a><span data-ttu-id="2b4e6-112">perfmon.exe を Windows Vista 以降のバージョンで実行するには</span><span class="sxs-lookup"><span data-stu-id="2b4e6-112">To run Perfmon.exe on Windows Vista and later versions</span></span>  
  
1. <span data-ttu-id="2b4e6-113">コマンド プロンプトで、「 **perfmon**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-113">At the command prompt, type **perfmon**.</span></span> <span data-ttu-id="2b4e6-114">**[パフォーマンス モニター]** コンソールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-114">The **Performance Monitor** console appears.</span></span>  
  
2. <span data-ttu-id="2b4e6-115">**[監視ツール]** フォルダーで、 **[パフォーマンス モニター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-115">In the **Monitoring Tools** folder, click **Performance Monitor**.</span></span>  
  
3. <span data-ttu-id="2b4e6-116">パフォーマンス モニターのツールバーで、 **[追加]** アイコン (正符号) をクリックします (表示されている場合)。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-116">In the Performance Monitor toolbar, click the **Add** icon (the plus sign), if it is present.</span></span> <span data-ttu-id="2b4e6-117">表示されていない場合は、モニター ウィンドウで右クリックし、 **[カウンターの追加]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-117">If it is not present, right-click in the monitor window and select the **Add Counters** option.</span></span>  
  
     <span data-ttu-id="2b4e6-118">**[接続の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-118">This opens the **Add Counters** dialog box.</span></span> <span data-ttu-id="2b4e6-119">**[使用可能なカウンター]** リスト ボックスに、使用可能なパフォーマンス オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-119">The **Available counters** list box displays the available performance objects.</span></span> <span data-ttu-id="2b4e6-120">.NET Framework アプリケーション用には、さまざまな定義済みのオブジェクトがあります。これには、メモリ管理 (**.NET CLR メモリ**)、相互運用性 (**.NET CLR の相互運用性**)、例外処理 (**.NET CLR 例外**)、およびマルチスレッド (**.NET CLR LocksAndThreads**) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-120">There are a number of predefined objects for .NET Framework applications, including those for memory management (**.NET CLR Memory**), interoperability (**.NET CLR Interop**), exception handling (**.NET CLR Exceptions**), and multithreading (**.NET CLR LocksAndThreads**).</span></span> <span data-ttu-id="2b4e6-121">各パフォーマンス オブジェクトには、個々 のパフォーマンス カウンターが多数含まれています。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-121">Each performance object includes a number of individual performance counters.</span></span> <span data-ttu-id="2b4e6-122">パフォーマンス モニターで使用可能なパフォーマンス カウンターの一覧は、「 [Performance Counters](performance-counters.md)と共にインストールされる .NET Framework パフォーマンス カウンター内のデータをグラフィカルに表示します。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-122">For a list of the performance counters available in Performance Monitor, see [Performance Counters](performance-counters.md).</span></span>  
  
4. <span data-ttu-id="2b4e6-123">パフォーマンス オブジェクトの名前の横にあるチェック ボックスをオンにすると、サポートされている個々のパフォーマンス カウンターの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-123">Select the check box next to a performance object's name to view the list of individual performance counters that it supports.</span></span>  
  
5. <span data-ttu-id="2b4e6-124">表示するパフォーマンス カウンターをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-124">Click the performance counter you want to view.</span></span>  
  
6. <span data-ttu-id="2b4e6-125">**[選択したオブジェクトのインスタンス]** リスト ボックスで、 **\<All instances>** をクリックして、共通言語ランタイムのパフォーマンス カウンターをグローバルに (つまり、システム全体で) 監視するように指定します。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-125">In the **Instances of selected object** list box, click **\<All instances>** to specify that you want to monitor the performance counter for the common language runtime globally (that is, on a system-wide basis).</span></span>  
  
     <span data-ttu-id="2b4e6-126">または</span><span class="sxs-lookup"><span data-stu-id="2b4e6-126">-or-</span></span>  
  
     <span data-ttu-id="2b4e6-127">**[選択したオブジェクトのインスタンス]** リスト ボックスで、アプリケーション名をクリックして、そのアプリケーションのパフォーマンス カウンターを監視します。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-127">In the **Instances of selected object** list box, click an application name to monitor the performance counter for that application.</span></span>  
  
     <span data-ttu-id="2b4e6-128">複数のバージョンのランタイムを区別する必要がある場合、または同じ名前を持つ複数のアプリケーション間のあいまいさを解消する必要がある場合は、レジストリ キーも変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-128">To differentiate multiple versions of the runtime, or to disambiguate multiple applications with the same name, you must also modify a registry key.</span></span> <span data-ttu-id="2b4e6-129">詳細については、「 [Performance Counters and In-Process Side-By-Side Applications](performance-counters-and-in-process-side-by-side-applications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-129">For more information, see [Performance Counters and In-Process Side-By-Side Applications](performance-counters-and-in-process-side-by-side-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b4e6-130">パフォーマンス コンソールの実行中に新しいパフォーマンス カウンターがインストールされた場合は、新しいカウンターが表示されるように、パフォーマンス コンソールを停止して再起動してください。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-130">When new performance counters are installed while the Performance console is running, stop and restart the Performance console to make the new counters visible.</span></span>  
  
 <span data-ttu-id="2b4e6-131">特定のゾーンまたはリモート共有に存在するアセンブリをプロファイリングする場合は、リモート アセンブリがパフォーマンス カウンターを実行するコンピューターに対して完全な信頼関係を持っていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-131">If you want to profile an assembly that exists in a zone or on a remote share, make sure that the remote assembly has full trust on the computer that runs the performance counters.</span></span> <span data-ttu-id="2b4e6-132">アセンブリが十分な信頼関係を持っていない場合、パフォーマンス カウンターは機能しません。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-132">If the assembly does not have sufficient trust, the performance counters will not work.</span></span> <span data-ttu-id="2b4e6-133">さまざまなゾーンへの信頼の付与については、「[Caspol.exe (コード アクセス セキュリティ ポリシー ツール)](../tools/caspol-exe-code-access-security-policy-tool.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-133">For information about granting trust to different zones, see [Caspol.exe (Code Access Security Policy Tool)](../tools/caspol-exe-code-access-security-policy-tool.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b4e6-134">.NET Framework 4 がインストールされているシステムでは、パフォーマンス モニターで、.NET Framework 1.1 を使用して開発されたアプリケーションについて、 **.NET CLR データ** や **.NET CLR ネットワーク** などの一部のカテゴリでパフォーマンス カウンターのデータが表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-134">On systems on which the .NET Framework 4 is installed, the Performance Monitor may not display data for performance counters in some categories, such as **.NET CLR Data** and **.NET CLR Networking**, for applications that were developed using the .NET Framework 1.1.</span></span> <span data-ttu-id="2b4e6-135">このような場合、[\<forcePerformanceCounterUniqueSharedMemoryReads>](../configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) 要素をアプリケーションの構成ファイルに追加することで、このデータを表示するようにパフォーマンス モニターを構成できます。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-135">If this is the case, you can configure Performance Monitor to display this data by adding the [\<forcePerformanceCounterUniqueSharedMemoryReads>](../configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) element to the application's configuration file.</span></span>  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a><span data-ttu-id="2b4e6-136">プログラムを使用したパフォーマンス カウンターの読み取りと作成</span><span class="sxs-lookup"><span data-stu-id="2b4e6-136">Reading and Creating Performance Counters Programmatically</span></span>  

 <span data-ttu-id="2b4e6-137">.NET Framework には、パフォーマンス コンソールで利用できるものと同じパフォーマンス情報にコードからアクセスするのに使用するクラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-137">The .NET Framework provides classes you can use to programmatically access the same performance information that is available in the Performance console.</span></span> <span data-ttu-id="2b4e6-138">また、これらのクラスを使用すると、カスタム パフォーマンス カウンターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-138">You can also use these classes to create custom performance counters.</span></span> <span data-ttu-id="2b4e6-139">.NET Framework に用意されているパフォーマンス監視クラスの一部について、次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-139">The following table describes some of the performance monitoring classes that are provided in the .NET Framework.</span></span>  
  
|<span data-ttu-id="2b4e6-140">クラス</span><span class="sxs-lookup"><span data-stu-id="2b4e6-140">Class</span></span>|<span data-ttu-id="2b4e6-141">説明</span><span class="sxs-lookup"><span data-stu-id="2b4e6-141">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|<span data-ttu-id="2b4e6-142">Windows NT パフォーマンス カウンター コンポーネントを表します。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-142">Represents a Windows NT performance counter component.</span></span> <span data-ttu-id="2b4e6-143">既存の定義済みカウンターやカスタム カウンターを読み取ったり、カスタム カウンターにパフォーマンス データを書き込むには、このクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-143">Use this class to read existing predefined or custom counters and publish (write) performance data to custom counters.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|<span data-ttu-id="2b4e6-144">コンピューター上のカウンターおよびカウンター カテゴリと対話するためのいくつかのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-144">Provides several methods for interacting with counters and categories of counters on the computer.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|<span data-ttu-id="2b4e6-145">`PerformanceCounter` コンポーネントのインストーラーを指定します。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-145">Specifies an installer for the `PerformanceCounter` component.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|<span data-ttu-id="2b4e6-146">`NextValue` の `PerformanceCounter`メソッドを計算する数式を指定します。</span><span class="sxs-lookup"><span data-stu-id="2b4e6-146">Specifies the formula to calculate the `NextValue` method for a `PerformanceCounter`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b4e6-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b4e6-147">See also</span></span>

- [<span data-ttu-id="2b4e6-148">パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="2b4e6-148">Performance Counters</span></span>](performance-counters.md)
