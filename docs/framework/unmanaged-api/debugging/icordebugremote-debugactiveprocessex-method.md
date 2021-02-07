---
description: '詳細については、次のページを参照してください: の場合::D Eて Activeprocessex メソッド'
title: ICorDebugRemote::DebugActiveProcessEx メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
ms.openlocfilehash: ccbde152e59146bd852a5a0a2f991d10333fa9d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717902"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="9f314-103">ICorDebugRemote::DebugActiveProcessEx メソッド</span><span class="sxs-lookup"><span data-stu-id="9f314-103">ICorDebugRemote::DebugActiveProcessEx Method</span></span>

<span data-ttu-id="9f314-104">デバッガーでリモートコンピューター上のプロセスを起動します。</span><span class="sxs-lookup"><span data-stu-id="9f314-104">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f314-105">構文</span><span class="sxs-lookup"><span data-stu-id="9f314-105">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f314-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f314-106">Parameters</span></span>  

 `pRemoteTarget`  
 <span data-ttu-id="9f314-107">からツールの [ターゲットインターフェイス](icordebugremotetarget-interface.md)を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="9f314-107">[in] Pointer to an [ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="9f314-108">このパラメーターは、プロセスが実行されているコンピューターを決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f314-108">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="9f314-109">からデバッガーがアタッチされるプロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="9f314-109">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="9f314-110">[入力] `true` デバッガーがプロセスの Win32 デバッガーとして動作し、アンマネージコールバックをディスパッチする必要がある場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="9f314-110">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="9f314-111">入出力デバッガーがアタッチされているプロセスを表す "いいプロセス" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9f314-111">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f314-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="9f314-112">Return Value</span></span>  

 <span data-ttu-id="9f314-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9f314-113">S_OK</span></span>  
 <span data-ttu-id="9f314-114">リモートコンピューター上のプロセスに正常にアタッチされました。</span><span class="sxs-lookup"><span data-stu-id="9f314-114">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="9f314-115">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="9f314-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="9f314-116">リモートコンピューター上のプロセスにアタッチできません。</span><span class="sxs-lookup"><span data-stu-id="9f314-116">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f314-117">解説</span><span class="sxs-lookup"><span data-stu-id="9f314-117">Remarks</span></span>  

 <span data-ttu-id="9f314-118">混合モードのデバッグは、Silverlight ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9f314-118">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f314-119">要件</span><span class="sxs-lookup"><span data-stu-id="9f314-119">Requirements</span></span>  

 <span data-ttu-id="9f314-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f314-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f314-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f314-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f314-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f314-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f314-123">**.NET Framework のバージョン:** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="9f314-123">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f314-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f314-124">See also</span></span>

- [<span data-ttu-id="9f314-125">ICorDebugRemote インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f314-125">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="9f314-126">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f314-126">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="9f314-127">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f314-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
