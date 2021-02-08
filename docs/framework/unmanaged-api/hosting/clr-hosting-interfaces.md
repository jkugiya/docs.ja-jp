---
description: 詳細については、「CLR ホストインターフェイス」を参照してください。
title: CLR ホスト インターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: f42a74698607ffbed4a981f061d13ea4e9d634d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799903"
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="998d3-103">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-103">CLR Hosting Interfaces</span></span>

<span data-ttu-id="998d3-104">ここでは、アンマネージホストが共通言語ランタイム (CLR) をアプリケーションに統合するために使用できるインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="998d3-104">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="998d3-105">この情報は .NET Framework バージョン2.0 以降のバージョンに関連します。</span><span class="sxs-lookup"><span data-stu-id="998d3-105">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="998d3-106">これらのインターフェイスを使用すると、ホストは、バージョン1.0 および1.1 で可能な限り多くのランタイムの側面を制御でき、CLR とホストの実行モデルとの間の統合が大幅に強化されます。</span><span class="sxs-lookup"><span data-stu-id="998d3-106">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="998d3-107">.NET Framework バージョン1.0 および1.1 では、ホストモデルによって、CLR をプロセスに読み込み、特定の設定を構成し、イベント通知を受信するために、管理されていないホストが有効になりました。</span><span class="sxs-lookup"><span data-stu-id="998d3-107">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="998d3-108">ただし、一般に、ホストと CLR は、そのプロセスで独立して実行されていました。</span><span class="sxs-lookup"><span data-stu-id="998d3-108">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="998d3-109">.NET Framework バージョン2.0 以降のバージョンでは、新しい階層の抽象化により、ホストは、Win32 アセンブリの型によって現在提供されている多くのリソースを提供し、ホストが構成できる一連の機能を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="998d3-109">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="998d3-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="998d3-110">In This Section</span></span>  

 [<span data-ttu-id="998d3-111">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-111">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)  
 <span data-ttu-id="998d3-112">登録されているイベントに対してコールバックを実行するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-112">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="998d3-113">IApartmentCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-113">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)  
 <span data-ttu-id="998d3-114">アパートメント内でコールバックを作成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-114">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="998d3-115">IAppDomainBinding インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-115">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)  
 <span data-ttu-id="998d3-116">実行時の構成を設定するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-116">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="998d3-117">ICatalogServices インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-117">ICatalogServices Interface</span></span>](icatalogservices-interface.md)  
 <span data-ttu-id="998d3-118">サービスのカタログ化を行うためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-118">Provides methods for cataloging services.</span></span> <span data-ttu-id="998d3-119">(このインターフェイスは .NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません)。</span><span class="sxs-lookup"><span data-stu-id="998d3-119">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="998d3-120">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-120">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="998d3-121">アセンブリに関するホストと CLR 間の通信をサポートするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-121">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="998d3-122">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-122">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="998d3-123">ホストではなく、CLR によって読み込まれるアセンブリの一覧を管理します。</span><span class="sxs-lookup"><span data-stu-id="998d3-123">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="998d3-124">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-124">ICLRControl Interface</span></span>](iclrcontrol-interface.md)  
 <span data-ttu-id="998d3-125">ホストが CLR に対してアクセスを取得し、さまざまな側面を構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-125">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="998d3-126">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-126">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)  
 <span data-ttu-id="998d3-127">ホストが一連のタスクを識別子とフレンドリ名に関連付けることができるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-127">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="998d3-128">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-128">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="998d3-129">エラー報告のためにホストがカスタムヒープダンプを構成できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-129">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="998d3-130">ICLRGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-130">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)  
 <span data-ttu-id="998d3-131">ホストが CLR のガベージコレクションシステムと対話できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-131">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="998d3-132">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-132">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="998d3-133">ホストがアセンブリのポリシー情報の変更を評価および通知するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-133">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="998d3-134">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-134">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="998d3-135">ホストが、部分的に信頼されたコードで実行される特定のマネージクラス、メソッド、プロパティ、およびフィールドをブロックできるようにします。</span><span class="sxs-lookup"><span data-stu-id="998d3-135">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="998d3-136">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)  
 <span data-ttu-id="998d3-137">ホストが、指定された i/o 要求のステータスを CLR に通知できるようにするコールバックメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="998d3-137">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="998d3-138">ICLRMemoryNotificationCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-138">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="998d3-139">Win32 関数と同様の方法を使用して、ホストがメモリ不足状態を報告できるようにし `CreateMemoryResourceNotification` ます。</span><span class="sxs-lookup"><span data-stu-id="998d3-139">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="998d3-140">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-140">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)  
 <span data-ttu-id="998d3-141">ホストが CLR イベントのコールバックを登録および登録解除できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-141">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="998d3-142">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-142">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)  
 <span data-ttu-id="998d3-143">エラーとタイムアウトが発生した場合に実行されるポリシーアクションをホストが指定できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-143">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="998d3-144">ICLRProbingAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-144">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="998d3-145">ホストが CLR 内部のアセンブリ id 情報を使用してアセンブリのプローブ id を取得できるようにするメソッドを提供します。このメソッドは、その id を作成したり、理解したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="998d3-145">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="998d3-146">ICLRReferenceAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-146">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="998d3-147">CLR 内部のアセンブリ id データを使用して、ファイルまたはストリームによって参照されるアセンブリのセットをホストが操作できるようにするメソッドを提供します。これらの id を作成したり、理解したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="998d3-147">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="998d3-148">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-148">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)  
 <span data-ttu-id="998d3-149">には、 [ICorRuntimeHost](icorruntimehost-interface.md)と同様の機能が用意されており、ホストコントロールインターフェイスを設定するための追加のメソッドもあります。</span><span class="sxs-lookup"><span data-stu-id="998d3-149">Provides capabilities similar to [ICorRuntimeHost](icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="998d3-150">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-150">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)  
 <span data-ttu-id="998d3-151">ホストが、要求されたタスクに関する情報を取得し、その同期実装でデッドロックを検出するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-151">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="998d3-152">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-152">ICLRTask Interface</span></span>](iclrtask-interface.md)  
 <span data-ttu-id="998d3-153">ホストが CLR の要求を行うことができるようにするメソッド、または関連付けられたタスクについて CLR に通知を提供するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-153">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="998d3-154">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-154">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)  
 <span data-ttu-id="998d3-155">CLR が新しいタスクを作成し、現在実行中のタスクを取得し、タスクの地理的言語とカルチャを設定することをホストが明示的に要求できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-155">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="998d3-156">ICLRValidator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-156">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)  
 <span data-ttu-id="998d3-157">ポータブル実行可能 (PE) イメージを検証し、検証エラーを報告するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-157">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="998d3-158">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-158">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)  
 <span data-ttu-id="998d3-159">CLR を構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-159">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="998d3-160">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-160">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)  
 <span data-ttu-id="998d3-161">スレッドプールにアクセスするためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-161">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="998d3-162">IDebuggerInfo Iインターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-162">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)  
 <span data-ttu-id="998d3-163">デバッグサービスの状態に関する情報を取得するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-163">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="998d3-164">IDebuggerThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-164">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="998d3-165">デバッグサービスによるスレッドのブロックおよびブロック解除についてホストに通知するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-165">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="998d3-166">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-166">IGCHost Interface</span></span>](igchost-interface.md)  
 <span data-ttu-id="998d3-167">ガベージコレクションシステムに関する情報を取得し、ガベージコレクションのいくつかの側面を制御するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-167">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="998d3-168">IGCHost2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-168">IGCHost2 Interface</span></span>](igchost2-interface.md)  
 <span data-ttu-id="998d3-169">ホストがガベージコレクションセグメントのサイズとガベージコレクションシステムのジェネレーション0の最大サイズをより大きい値に設定できるようにする [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) メソッドを提供し `DWORD` ます。</span><span class="sxs-lookup"><span data-stu-id="998d3-169">Provides the [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="998d3-170">IGCHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-170">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)  
 <span data-ttu-id="998d3-171">仮想メモリの制限を変更するように、ガベージコレクターがホストに要求できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-171">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="998d3-172">IGCThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-172">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)  
 <span data-ttu-id="998d3-173">ガベージコレクションのためにブロックされるスレッドのスケジュール設定に参加するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-173">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="998d3-174">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-174">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)  
 <span data-ttu-id="998d3-175">CLR またはホストによって読み込まれる必要があるアセンブリのセットをホストが指定できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-175">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="998d3-176">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-176">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)  
 <span data-ttu-id="998d3-177">ホストが CLR とは無関係にアセンブリおよびモジュールを読み込むことができるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-177">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="998d3-178">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-178">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)  
 <span data-ttu-id="998d3-179">ホストによって実装される自動リセットイベントの表現を提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-179">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="998d3-180">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-180">IHostControl Interface</span></span>](ihostcontrol-interface.md)  
 <span data-ttu-id="998d3-181">アセンブリの読み込みを構成し、ホストがサポートするホストインターフェイスを決定するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-181">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="998d3-182">IHostCrst インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-182">IHostCrst Interface</span></span>](ihostcrst-interface.md)  
 <span data-ttu-id="998d3-183">スレッド処理のためのクリティカルセクションのホストの表現として機能します。</span><span class="sxs-lookup"><span data-stu-id="998d3-183">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="998d3-184">IHostGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-184">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)  
 <span data-ttu-id="998d3-185">CLR によって実装されるガベージコレクション機構でイベントのホストに通知するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-185">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="998d3-186">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-186">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="998d3-187">ホストによって提供される i/o 完了ポートと CLR が対話できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-187">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="998d3-188">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-188">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)  
 <span data-ttu-id="998d3-189">CLR がホストを介してヒープから細かい割り当てを要求するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-189">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="998d3-190">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-190">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)  
 <span data-ttu-id="998d3-191">手動リセットイベントの表現のホストの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-191">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="998d3-192">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-192">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)  
 <span data-ttu-id="998d3-193">標準の Win32 仮想メモリ関数を使用する代わりに、CLR がホストを介して仮想メモリ要求を行うためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-193">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="998d3-194">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-194">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)  
 <span data-ttu-id="998d3-195">中止、タイムアウト、またはエラーが発生した場合に CLR が実行するアクションをホストに通知するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-195">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="998d3-196">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-196">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)  
 <span data-ttu-id="998d3-197">CLR がホストによって実装されたセキュリティコンテキスト情報を維持できるようにします。</span><span class="sxs-lookup"><span data-stu-id="998d3-197">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="998d3-198">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-198">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)  
 <span data-ttu-id="998d3-199">現在実行中のスレッドのセキュリティコンテキストに対するアクセスと制御を可能にするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-199">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="998d3-200">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-200">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)  
 <span data-ttu-id="998d3-201">ホストによって実装されるセマフォの表現を提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-201">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="998d3-202">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-202">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="998d3-203">Win32 同期関数を使用する代わりに、ホストを呼び出すことによって、CLR が同期プリミティブを作成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-203">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="998d3-204">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-204">IHostTask Interface</span></span>](ihosttask-interface.md)  
 <span data-ttu-id="998d3-205">CLR がホストと通信してタスクを管理できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-205">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="998d3-206">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-206">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)  
 <span data-ttu-id="998d3-207">標準のオペレーティングシステムのスレッド処理やファイバー関数を使用する代わりに、CLR がホストを通じてタスクを操作できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-207">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="998d3-208">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-208">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="998d3-209">CLR がスレッドプールを構成し、作業項目をスレッドプールにキューするためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-209">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="998d3-210">IManagedObject インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-210">IManagedObject Interface</span></span>](imanagedobject-interface.md)  
 <span data-ttu-id="998d3-211">マネージオブジェクトを制御するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-211">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="998d3-212">IObjectHandle</span><span class="sxs-lookup"><span data-stu-id="998d3-212">"IObjectHandle"</span></span>  
 <span data-ttu-id="998d3-213">値渡しのマーシャリングオブジェクトを間接参照からラップ解除するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-213">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="998d3-214">ITypeName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-214">ITypeName Interface</span></span>](itypename-interface.md)  
 <span data-ttu-id="998d3-215">型名の情報を取得するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-215">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="998d3-216">(このインターフェイスは .NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません)。</span><span class="sxs-lookup"><span data-stu-id="998d3-216">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="998d3-217">ITypeNameBuilder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-217">ITypeNameBuilder Interface</span></span>](itypenamebuilder-interface.md)  
 <span data-ttu-id="998d3-218">型名を構築するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-218">Provides methods for building a type name.</span></span> <span data-ttu-id="998d3-219">(このインターフェイスは .NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません)。</span><span class="sxs-lookup"><span data-stu-id="998d3-219">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="998d3-220">ITypeNameFactory インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-220">ITypeNameFactory Interface</span></span>](itypenamefactory-interface.md)  
 <span data-ttu-id="998d3-221">型名を分解するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-221">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="998d3-222">(このインターフェイスは .NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません)。</span><span class="sxs-lookup"><span data-stu-id="998d3-222">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="998d3-223">IValidator</span><span class="sxs-lookup"><span data-stu-id="998d3-223">"IValidator"</span></span>  
 <span data-ttu-id="998d3-224">ポータブル実行可能 (PE) イメージを検証し、検証エラーを報告するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="998d3-224">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="998d3-225">関連項目</span><span class="sxs-lookup"><span data-stu-id="998d3-225">Related Sections</span></span>  

 [<span data-ttu-id="998d3-226">非推奨の CLR のホスト インターフェイスおよびコクラス</span><span class="sxs-lookup"><span data-stu-id="998d3-226">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="998d3-227">.NET Framework バージョン1.0 および1.1 で提供されるホストインターフェイスについて説明するトピックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="998d3-227">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="998d3-228">.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="998d3-228">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="998d3-229">.NET Framework 4 で提供されるホスティングインターフェイスについて説明するトピックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="998d3-229">Contains topics that describe the hosting interfaces provided in the .NET Framework 4.</span></span>
