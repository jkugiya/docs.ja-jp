---
description: 詳細については、「非推奨の CLR ホスト関数」を参照してください。
title: 非推奨の CLR ホスト関数
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 3d16b5829e29c5c963f4790bbb3be7adcaeedbfc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785667"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="6ec3a-103">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-103">Deprecated CLR Hosting Functions</span></span>

<span data-ttu-id="6ec3a-104">このセクションでは、以前のバージョンのホスト API で使用されていたアンマネージ グローバル静的関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-104">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="6ec3a-105">`_Cor*`.NET Framework によってのみ使用されるインフラストラクチャ関数 (functions) を除き、これらの関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-105">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="6ec3a-106">アクティブ化関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-106">Activation functions</span></span>  

 [<span data-ttu-id="6ec3a-107">ClrCreateManagedInstance 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-107">ClrCreateManagedInstance Function</span></span>](clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="6ec3a-108">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-108">Deprecated.</span></span> <span data-ttu-id="6ec3a-109">指定したマネージド型のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-109">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="6ec3a-110">CoInitializeCor 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-110">CoInitializeCor Function</span></span>](coinitializecor-function.md)  
 <span data-ttu-id="6ec3a-111">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-111">Obsolete.</span></span> <span data-ttu-id="6ec3a-112">共通言語ランタイム (CLR) を初期化するには、 [Corbindtoruntimeex](corbindtoruntimeex-function.md) または [Corbindtoの entruntime](corbindtocurrentruntime-function.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-112">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="6ec3a-113">CoInitializeEE 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-113">CoInitializeEE Function</span></span>](coinitializeee-function.md)  
 <span data-ttu-id="6ec3a-114">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-114">Deprecated.</span></span> <span data-ttu-id="6ec3a-115">CLR 実行エンジンがプロセスに読み込まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-115">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="6ec3a-116">代わりに [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-116">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="6ec3a-117">CorBindToCurrentRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-117">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)  
 <span data-ttu-id="6ec3a-118">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-118">Deprecated.</span></span> <span data-ttu-id="6ec3a-119">XML ファイルに格納されているバージョン情報を使用して、共通言語ランタイム (CLR: Common Language Runtime) をプロセスに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-119">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="6ec3a-120">CorBindToRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-120">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)  
 <span data-ttu-id="6ec3a-121">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-121">Deprecated.</span></span> <span data-ttu-id="6ec3a-122">アンマネージ ホストが CLR をプロセスに読み込めるようにします。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-122">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="6ec3a-123">CorBindToRuntimeByCfg 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-123">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="6ec3a-124">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-124">Deprecated.</span></span> <span data-ttu-id="6ec3a-125">XML ファイルから読み取ったバージョン情報を使用して、CLR をプロセスに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-125">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="6ec3a-126">CorBindToRuntimeEx 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-126">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)  
 <span data-ttu-id="6ec3a-127">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-127">Deprecated.</span></span> <span data-ttu-id="6ec3a-128">アンマネージ ホストが CLR をプロセスに読み込めるようにします。CLR の動作を指定するフラグを設定できます。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-128">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="6ec3a-129">CorBindToRuntimeHost 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-129">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)  
 <span data-ttu-id="6ec3a-130">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-130">Deprecated.</span></span> <span data-ttu-id="6ec3a-131">指定したバージョンの CLR をホストがプロセスに読み込めるようにします。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-131">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="6ec3a-132">GetCORRequiredVersion 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-132">GetCORRequiredVersion Function</span></span>](getcorrequiredversion-function.md)  
 <span data-ttu-id="6ec3a-133">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-133">Deprecated.</span></span> <span data-ttu-id="6ec3a-134">必要な CLR のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-134">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="6ec3a-135">GetCORSystemDirectory 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-135">GetCORSystemDirectory Function</span></span>](getcorsystemdirectory-function.md)  
 <span data-ttu-id="6ec3a-136">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-136">Deprecated.</span></span> <span data-ttu-id="6ec3a-137">プロセスに読み込まれた CLR のインストール ディレクトリを返します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-137">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="6ec3a-138">GetRealProcAddress 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-138">GetRealProcAddress Function</span></span>](getrealprocaddress-function.md)  
 <span data-ttu-id="6ec3a-139">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-139">Deprecated.</span></span> <span data-ttu-id="6ec3a-140">最後にインストールされたバージョンの CLR からエクスポートされる、指定した関数のアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-140">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="6ec3a-141">GetRequestedRuntimeInfo 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-141">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="6ec3a-142">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-142">Deprecated.</span></span> <span data-ttu-id="6ec3a-143">アプリケーションが要求した CLR についてのバージョン情報とディレクトリ情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-143">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="6ec3a-144">CLR バージョン関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-144">CLR version functions</span></span>  

 <span data-ttu-id="6ec3a-145">このセクションの関数は、CLR のバージョンを返します。CLR をアクティブ化することはありません。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-145">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="6ec3a-146">GetCORVersion 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-146">GetCORVersion Function</span></span>](getcorversion-function.md)  
 <span data-ttu-id="6ec3a-147">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-147">Deprecated.</span></span> <span data-ttu-id="6ec3a-148">現在のプロセスで実行されている CLR のバージョン番号を返します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-148">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="6ec3a-149">GetFileVersion 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-149">GetFileVersion Function</span></span>](getfileversion-function.md)  
 <span data-ttu-id="6ec3a-150">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-150">Deprecated.</span></span> <span data-ttu-id="6ec3a-151">指定したバッファーを使用して、指定したファイルの CLR バージョン情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-151">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="6ec3a-152">GetRequestedRuntimeVersion 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-152">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)  
 <span data-ttu-id="6ec3a-153">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-153">Deprecated.</span></span> <span data-ttu-id="6ec3a-154">指定したアプリケーションで要求される CLR のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-154">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="6ec3a-155">そのバージョンがインストールされていない場合は、要求されるバージョンより前にインストールされた最も新しいバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-155">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="6ec3a-156">GetRequestedRuntimeVersionForCLSID 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-156">GetRequestedRuntimeVersionForCLSID Function</span></span>](getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="6ec3a-157">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-157">Deprecated.</span></span> <span data-ttu-id="6ec3a-158">指定の CLSID を持つクラスに対応した CLR バージョンの情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-158">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="6ec3a-159">GetVersionFromProcess 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-159">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)  
 <span data-ttu-id="6ec3a-160">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-160">Deprecated.</span></span> <span data-ttu-id="6ec3a-161">指定のプロセス ハンドルに関連付けられた CLR のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-161">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="6ec3a-162">LockClrVersion 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-162">LockClrVersion Function</span></span>](lockclrversion-function.md)  
 <span data-ttu-id="6ec3a-163">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-163">Deprecated.</span></span> <span data-ttu-id="6ec3a-164">プロセス内で使用する CLR のバージョンを、CLR を明示的に初期化する前にホストが決定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-164">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="6ec3a-165">ホスト関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-165">Hosting functions</span></span>  

 [<span data-ttu-id="6ec3a-166">CallFunctionShim 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-166">CallFunctionShim Function</span></span>](callfunctionshim-function.md)  
 <span data-ttu-id="6ec3a-167">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-167">Deprecated.</span></span> <span data-ttu-id="6ec3a-168">指定したライブラリ内の関数を、名前とパラメーターを指定して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-168">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="6ec3a-169">CoEEShutDownCOM 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-169">CoEEShutDownCOM Function</span></span>](coeeshutdowncom-function.md)  
 <span data-ttu-id="6ec3a-170">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-170">Deprecated.</span></span> <span data-ttu-id="6ec3a-171">プロセスから COM アセンブリをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-171">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="6ec3a-172">CorExitProcess 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-172">CorExitProcess Function</span></span>](corexitprocess-function.md)  
 <span data-ttu-id="6ec3a-173">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-173">Deprecated.</span></span> <span data-ttu-id="6ec3a-174">現在のアンマネージ プロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-174">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="6ec3a-175">CorLaunchApplication 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-175">CorLaunchApplication Function</span></span>](corlaunchapplication-function.md)  
 <span data-ttu-id="6ec3a-176">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-176">Deprecated.</span></span> <span data-ttu-id="6ec3a-177">指定したネットワーク パスのアプリケーションを、指定したマニフェストとその他のアプリケーション データを使用して起動します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-177">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="6ec3a-178">CorMarkThreadInThreadPool 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-178">CorMarkThreadInThreadPool Function</span></span>](cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="6ec3a-179">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-179">Deprecated.</span></span> <span data-ttu-id="6ec3a-180">現在実行されているスレッド プールのスレッドに、マネージド コードの実行のマークを付けます。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-180">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="6ec3a-181">.NET Framework Version 2.0 以降では、この関数に効力はありません。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-181">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="6ec3a-182">必ずしも必要はありませんが、この関数はコードから削除できます。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-182">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="6ec3a-183">CoUninitializeCor 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-183">CoUninitializeCor Function</span></span>](couninitializecor-function.md)  
 <span data-ttu-id="6ec3a-184">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-184">Obsolete.</span></span> <span data-ttu-id="6ec3a-185">プロセスから CLR をアンロードできません。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-185">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="6ec3a-186">CoUninitializeEE 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-186">CoUninitializeEE Function</span></span>](couninitializeee-function.md)  
 <span data-ttu-id="6ec3a-187">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-187">Obsolete.</span></span>  
  
 [<span data-ttu-id="6ec3a-188">CreateDebuggingInterfaceFromVersion 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-188">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="6ec3a-189">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-189">Deprecated.</span></span> <span data-ttu-id="6ec3a-190">指定されたバージョン情報に基づいて [ICorDebug](../debugging/icordebug-interface.md) オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-190">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="6ec3a-191">CreateICeeFileGen 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-191">CreateICeeFileGen Function</span></span>](createiceefilegen-function.md)  
 <span data-ttu-id="6ec3a-192">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-192">Deprecated.</span></span> <span data-ttu-id="6ec3a-193">[ICeeFileGen](iceefilegen-class.md)オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-193">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="6ec3a-194">DestroyICeeFileGen 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-194">DestroyICeeFileGen Function</span></span>](destroyiceefilegen-function.md)  
 <span data-ttu-id="6ec3a-195">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-195">Deprecated.</span></span> <span data-ttu-id="6ec3a-196">[ICeeFileGen](iceefilegen-class.md)オブジェクトを破棄します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-196">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="6ec3a-197">FExecuteInAppDomainCallback 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="6ec3a-197">FExecuteInAppDomainCallback Function Pointer</span></span>](fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="6ec3a-198">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-198">Deprecated.</span></span> <span data-ttu-id="6ec3a-199">CLR がマネージド コードを実行するために呼び出す関数を指します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-199">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="6ec3a-200">FLockClrVersionCallback 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="6ec3a-200">FLockClrVersionCallback Function Pointer</span></span>](flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="6ec3a-201">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-201">Deprecated.</span></span> <span data-ttu-id="6ec3a-202">初期化が開始または完了したことをホストに通知するために CLR が呼び出す関数を指します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-202">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="6ec3a-203">GetCLRIdentityManager 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-203">GetCLRIdentityManager Function</span></span>](getclridentitymanager-function.md)  
 <span data-ttu-id="6ec3a-204">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-204">Deprecated.</span></span> <span data-ttu-id="6ec3a-205">CLR が ID を管理できるようにするインターフェイスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-205">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="6ec3a-206">LoadLibraryShim 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-206">LoadLibraryShim Function</span></span>](loadlibraryshim-function.md)  
 <span data-ttu-id="6ec3a-207">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-207">Deprecated.</span></span> <span data-ttu-id="6ec3a-208">指定したバージョンの .NET Framework DLL を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-208">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="6ec3a-209">LoadStringRC 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-209">LoadStringRC Function</span></span>](loadstringrc-function.md)  
 <span data-ttu-id="6ec3a-210">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-210">Deprecated.</span></span> <span data-ttu-id="6ec3a-211">現在のスレッドの既定のカルチャを使用して、HRESULT 値をエラー メッセージに変換します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-211">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="6ec3a-212">LoadStringRCEx 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-212">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)  
 <span data-ttu-id="6ec3a-213">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-213">Deprecated.</span></span> <span data-ttu-id="6ec3a-214">HRESULT 値を、指定したカルチャの適切なエラー メッセージに変換します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-214">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="6ec3a-215">LPOVERLAPPED_COMPLETION_ROUTINE 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="6ec3a-215">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="6ec3a-216">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-216">Deprecated.</span></span> <span data-ttu-id="6ec3a-217">デバイスに対する重複 I/O (非同期 I/O) が完了したときに、ホストに通知する関数を指します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-217">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="6ec3a-218">LPTHREAD_START_ROUTINE 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="6ec3a-218">LPTHREAD_START_ROUTINE Function Pointer</span></span>](lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="6ec3a-219">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-219">Deprecated.</span></span> <span data-ttu-id="6ec3a-220">スレッドの実行を開始したことをホストに通知する関数を指します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-220">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="6ec3a-221">RunDll32ShimW 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-221">RunDll32ShimW Function</span></span>](rundll32shimw-function.md)  
 <span data-ttu-id="6ec3a-222">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-222">Deprecated.</span></span> <span data-ttu-id="6ec3a-223">指定されたコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-223">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="6ec3a-224">WAITORTIMERCALLBACK 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="6ec3a-224">WAITORTIMERCALLBACK Function Pointer</span></span>](waitortimercallback-function-pointer.md)  
 <span data-ttu-id="6ec3a-225">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-225">Deprecated.</span></span> <span data-ttu-id="6ec3a-226">待機ハンドルがシグナル状態になったこと、またはタイムアウトしたことをホストに通知する関数を指します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-226">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="6ec3a-227">インフラストラクチャ関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-227">Infrastructure functions</span></span>  

 <span data-ttu-id="6ec3a-228">このセクションの関数は、.NET Framework によってのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-228">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="6ec3a-229">_CorDllMain 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-229">_CorDllMain Function</span></span>](cordllmain-function.md)  
 <span data-ttu-id="6ec3a-230">CLR を初期化し、DLL アセンブリの CLR ヘッダーでマネージド エントリ ポイントを検索して、その実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-230">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="6ec3a-231">_CorExeMain 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-231">_CorExeMain Function</span></span>](corexemain-function.md)  
 <span data-ttu-id="6ec3a-232">CLR を初期化し、実行可能アセンブリの CLR ヘッダーでマネージド エントリ ポイントを検索して、その実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-232">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="6ec3a-233">_CorExeMain2 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-233">_CorExeMain2 Function</span></span>](corexemain2-function.md)  
 <span data-ttu-id="6ec3a-234">指定されたメモリ マップト コードのエントリ ポイントを実行します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-234">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="6ec3a-235">この関数は、オペレーティング システム ローダーによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-235">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="6ec3a-236">_CorImageUnloading 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-236">_CorImageUnloading Function</span></span>](corimageunloading-function.md)  
 <span data-ttu-id="6ec3a-237">マネージド モジュール イメージがアンロードされたときに、ローダーに通知します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-237">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="6ec3a-238">_CorValidateImage 関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-238">_CorValidateImage Function</span></span>](corvalidateimage-function.md)  
 <span data-ttu-id="6ec3a-239">マネージド モジュール イメージを検証し、それらが読み込まれると、オペレーティング システム ローダーに通知します。</span><span class="sxs-lookup"><span data-stu-id="6ec3a-239">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ec3a-240">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ec3a-240">See also</span></span>

- [<span data-ttu-id="6ec3a-241">.NET Framework 4 ホスト グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="6ec3a-241">.NET Framework 4 Hosting Global Static Functions</span></span>](net-framework-4-hosting-global-static-functions.md)
