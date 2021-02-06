---
description: 詳細については、「モジュールインターフェイス」を参照してください。
title: ICorDebugModule インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
ms.openlocfilehash: f78023fe9975b609309c1c511380a3a394426283
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660116"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="39920-103">ICorDebugModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="39920-103">ICorDebugModule Interface</span></span>

<span data-ttu-id="39920-104">実行可能ファイルまたはダイナミックリンクライブラリ (DLL) のいずれかである共通言語ランタイム (CLR) モジュールを表します。</span><span class="sxs-lookup"><span data-stu-id="39920-104">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="39920-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-105">Methods</span></span>  
  
|<span data-ttu-id="39920-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-106">Method</span></span>|<span data-ttu-id="39920-107">説明</span><span class="sxs-lookup"><span data-stu-id="39920-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="39920-108">CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-108">CreateBreakpoint Method</span></span>](icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="39920-109">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="39920-109">Not implemented.</span></span>|  
|[<span data-ttu-id="39920-110">EnableClassLoadCallbacks メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-110">EnableClassLoadCallbacks Method</span></span>](icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="39920-111">このモジュールに対して、" [UnloadClass](icordebugmanagedcallback-unloadclass-method.md) " コール[バック:: loadclass](icordebugmanagedcallback-loadclass-method.md)との各コールバックを呼び出すかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="39920-111">Determines whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="39920-112">EnableJITDebugging メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-112">EnableJITDebugging Method</span></span>](icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="39920-113">Just-in-time (JIT) コンパイラが、このモジュール内のメソッドのデバッグ情報を保持するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="39920-113">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="39920-114">GetAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-114">GetAssembly Method</span></span>](icordebugmodule-getassembly-method.md)|<span data-ttu-id="39920-115">このモジュールの格納アセンブリを取得します。</span><span class="sxs-lookup"><span data-stu-id="39920-115">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="39920-116">GetBaseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-116">GetBaseAddress Method</span></span>](icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="39920-117">モジュールのベースアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="39920-117">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="39920-118">GetClassFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-118">GetClassFromToken Method</span></span>](icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="39920-119">メタデータから、このクラスを取得します。</span><span class="sxs-lookup"><span data-stu-id="39920-119">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="39920-120">GetEditAndContinueSnapshot メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-120">GetEditAndContinueSnapshot Method</span></span>](icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="39920-121">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="39920-121">Deprecated.</span></span>|  
|[<span data-ttu-id="39920-122">GetFunctionFromRVA メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-122">GetFunctionFromRVA Method</span></span>](icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="39920-123">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="39920-123">Not implemented.</span></span>|  
|[<span data-ttu-id="39920-124">GetFunctionFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-124">GetFunctionFromToken Method</span></span>](icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="39920-125">メタデータトークンによって指定された関数を取得します。</span><span class="sxs-lookup"><span data-stu-id="39920-125">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="39920-126">GetGlobalVariableValue メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-126">GetGlobalVariableValue Method</span></span>](icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="39920-127">指定したグローバル変数の値オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="39920-127">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="39920-128">GetMetaDataInterface メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-128">GetMetaDataInterface Method</span></span>](icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="39920-129">モジュールのメタデータを調べるために使用できるメタデータインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="39920-129">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="39920-130">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-130">GetName Method</span></span>](icordebugmodule-getname-method.md)|<span data-ttu-id="39920-131">モジュールのファイル名を取得します。</span><span class="sxs-lookup"><span data-stu-id="39920-131">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="39920-132">GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-132">GetProcess Method</span></span>](icordebugmodule-getprocess-method.md)|<span data-ttu-id="39920-133">このモジュールの格納プロセスを取得します。</span><span class="sxs-lookup"><span data-stu-id="39920-133">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="39920-134">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-134">GetSize Method</span></span>](icordebugmodule-getsize-method.md)|<span data-ttu-id="39920-135">モジュールのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="39920-135">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="39920-136">GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-136">GetToken Method</span></span>](icordebugmodule-gettoken-method.md)|<span data-ttu-id="39920-137">このモジュールのテーブルエントリのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="39920-137">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="39920-138">IsDynamic メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-138">IsDynamic Method</span></span>](icordebugmodule-isdynamic-method.md)|<span data-ttu-id="39920-139">モジュールが動的かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="39920-139">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="39920-140">IsInMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="39920-140">IsInMemory Method</span></span>](icordebugmodule-isinmemory-method.md)|<span data-ttu-id="39920-141">このモジュールがメモリ内にのみ存在するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="39920-141">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39920-142">解説</span><span class="sxs-lookup"><span data-stu-id="39920-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39920-143">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="39920-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39920-144">要件</span><span class="sxs-lookup"><span data-stu-id="39920-144">Requirements</span></span>  

 <span data-ttu-id="39920-145">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39920-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39920-146">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39920-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39920-147">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39920-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39920-148">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39920-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39920-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="39920-149">See also</span></span>

- [<span data-ttu-id="39920-150">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="39920-150">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="39920-151">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="39920-151">Debugging Interfaces</span></span>](debugging-interfaces.md)
