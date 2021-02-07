---
description: '詳細について: ICLRDebugging:: OpenVirtualProcess メソッド'
title: ICLRDebugging::OpenVirtualProcess メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
ms.openlocfilehash: f9f195e1202a26a13b09cace74328c3937a9fcf1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723297"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="ccb81-103">ICLRDebugging::OpenVirtualProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="ccb81-103">ICLRDebugging::OpenVirtualProcess Method</span></span>

<span data-ttu-id="ccb81-104">プロセスに読み込まれた共通言語ランタイム (CLR) モジュールに対応する、コンポーネントインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="ccb81-104">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccb81-105">構文</span><span class="sxs-lookup"><span data-stu-id="ccb81-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccb81-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ccb81-106">Parameters</span></span>  

 `moduleBaseAddress`  
 <span data-ttu-id="ccb81-107">からターゲットプロセス内のモジュールのベースアドレス。</span><span class="sxs-lookup"><span data-stu-id="ccb81-107">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="ccb81-108">指定したモジュールが CLR モジュールでない場合、COR_E_NOT_CLR が返されます。</span><span class="sxs-lookup"><span data-stu-id="ccb81-108">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="ccb81-109">からマネージデバッガーがプロセスの状態を検査できるデータターゲットの抽象化。</span><span class="sxs-lookup"><span data-stu-id="ccb81-109">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="ccb81-110">デバッガーでは、、のように、によっては、 [このインターフェイスを](icordebugdatatarget-interface.md) 実装してください。</span><span class="sxs-lookup"><span data-stu-id="ccb81-110">The debugger must implement the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="ccb81-111">デバッグ対象の CLR がコンピューターにローカルにインストールされていないシナリオをサポートするには、 [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ccb81-111">You should implement the [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="ccb81-112">からライブラリプロバイダーのコールバックインターフェイス。バージョン固有のデバッグライブラリをオンデマンドで検索し、読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ccb81-112">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="ccb81-113">このパラメーターは `ppProcess` 、または `pFlags` がではない場合にのみ必要です `null` 。</span><span class="sxs-lookup"><span data-stu-id="ccb81-113">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="ccb81-114">からこのデバッガーがデバッグできる CLR の最大バージョン。</span><span class="sxs-lookup"><span data-stu-id="ccb81-114">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="ccb81-115">このデバッガーでサポートされている最新の CLR バージョンからメジャー、マイナー、ビルドの各バージョンを指定し、将来の CLR サービスリリースに対応するためにリビジョン番号を65535に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ccb81-115">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="ccb81-116">から取得するコード処理インターフェイスの ID。</span><span class="sxs-lookup"><span data-stu-id="ccb81-116">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="ccb81-117">現時点で許容される値は、IID_CORDEBUGPROCESS3、IID_CORDEBUGPROCESS2、および IID_CORDEBUGPROCESS だけです。</span><span class="sxs-lookup"><span data-stu-id="ccb81-117">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="ccb81-118">入出力によって識別される COM インターフェイスへのポインター `riidProcess` 。</span><span class="sxs-lookup"><span data-stu-id="ccb81-118">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="ccb81-119">[入力、出力]CLR のバージョン。</span><span class="sxs-lookup"><span data-stu-id="ccb81-119">[in, out] The version of the CLR.</span></span> <span data-ttu-id="ccb81-120">入力時には、この値をにすることができ `null` ます。</span><span class="sxs-lookup"><span data-stu-id="ccb81-120">On input, this value can be `null`.</span></span> <span data-ttu-id="ccb81-121">また、 [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) 構造体を指すこともできます。この場合、構造体の `wStructVersion` フィールドを 0 (ゼロ) に初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ccb81-121">It can also point to a [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="ccb81-122">出力時には、返された `CLR_DEBUGGING_VERSION` 構造体に CLR のバージョン情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="ccb81-122">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="ccb81-123">入出力指定されたランタイムに関する情報フラグ。</span><span class="sxs-lookup"><span data-stu-id="ccb81-123">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="ccb81-124">フラグの説明については、 [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ccb81-124">See the [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ccb81-125">戻り値</span><span class="sxs-lookup"><span data-stu-id="ccb81-125">Return Value</span></span>  

 <span data-ttu-id="ccb81-126">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="ccb81-126">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ccb81-127">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ccb81-127">HRESULT</span></span>|<span data-ttu-id="ccb81-128">説明</span><span class="sxs-lookup"><span data-stu-id="ccb81-128">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ccb81-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="ccb81-129">S_OK</span></span>|<span data-ttu-id="ccb81-130">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="ccb81-130">The method completed successfully.</span></span>|  
|<span data-ttu-id="ccb81-131">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ccb81-131">E_POINTER</span></span>|<span data-ttu-id="ccb81-132">`pDataTarget` は `null` です。</span><span class="sxs-lookup"><span data-stu-id="ccb81-132">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="ccb81-133">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="ccb81-133">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="ccb81-134">[ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)コールバックによってエラーが返されたか、有効なハンドルが提供されていません。</span><span class="sxs-lookup"><span data-stu-id="ccb81-134">The [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="ccb81-135">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="ccb81-135">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="ccb81-136">`pDataTarget` は、このバージョンのランタイムに必要なデータターゲットインターフェイスを実装していません。</span><span class="sxs-lookup"><span data-stu-id="ccb81-136">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="ccb81-137">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="ccb81-137">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="ccb81-138">指定されたモジュールは CLR モジュールではありません。</span><span class="sxs-lookup"><span data-stu-id="ccb81-138">The indicated module is not a CLR module.</span></span> <span data-ttu-id="ccb81-139">この HRESULT は、メモリが破損している、モジュールが使用できない、または CLR バージョンが shim バージョンより後であるために CLR モジュールが検出できない場合にも返されます。</span><span class="sxs-lookup"><span data-stu-id="ccb81-139">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="ccb81-140">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="ccb81-140">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="ccb81-141">このランタイムバージョンでは、このデバッグモデルはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ccb81-141">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="ccb81-142">現時点では、.NET Framework 4 より前のバージョンの CLR では、デバッグモデルはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ccb81-142">Currently, the debugging model is not supported by CLR versions before the .NET Framework 4.</span></span> <span data-ttu-id="ccb81-143">`pwszVersion`このエラーが発生すると、出力パラメーターは正しい値に設定されたままになります。</span><span class="sxs-lookup"><span data-stu-id="ccb81-143">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="ccb81-144">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="ccb81-144">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="ccb81-145">CLR のバージョンが、このデバッガーがサポートするために要求するバージョンよりも大きくなっています。</span><span class="sxs-lookup"><span data-stu-id="ccb81-145">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="ccb81-146">`pwszVersion`このエラーが発生すると、出力パラメーターは正しい値に設定されたままになります。</span><span class="sxs-lookup"><span data-stu-id="ccb81-146">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="ccb81-147">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="ccb81-147">E_NO_INTERFACE</span></span>|<span data-ttu-id="ccb81-148">`riidProcess`インターフェイスは使用できません。</span><span class="sxs-lookup"><span data-stu-id="ccb81-148">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="ccb81-149">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="ccb81-149">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="ccb81-150">`CLR_DEBUGGING_VERSION`構造体に、の認識された値がありません `wStructVersion` 。</span><span class="sxs-lookup"><span data-stu-id="ccb81-150">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="ccb81-151">現時点で許容される値は0のみです。</span><span class="sxs-lookup"><span data-stu-id="ccb81-151">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="ccb81-152">例外</span><span class="sxs-lookup"><span data-stu-id="ccb81-152">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccb81-153">解説</span><span class="sxs-lookup"><span data-stu-id="ccb81-153">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccb81-154">必要条件</span><span class="sxs-lookup"><span data-stu-id="ccb81-154">Requirements</span></span>  

 <span data-ttu-id="ccb81-155">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ccb81-155">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccb81-156">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ccb81-156">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ccb81-157">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccb81-157">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccb81-158">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccb81-158">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb81-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="ccb81-159">See also</span></span>

- [<span data-ttu-id="ccb81-160">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ccb81-160">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ccb81-161">デバッグ</span><span class="sxs-lookup"><span data-stu-id="ccb81-161">Debugging</span></span>](index.md)
