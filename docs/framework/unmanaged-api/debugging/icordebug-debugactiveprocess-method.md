---
description: '詳細については、次を参照してください: ICorDebug::D Eて Activeprocess メソッド'
title: ICorDebug::DebugActiveProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
ms.openlocfilehash: 9c3a212adf962f96fd2c7345fe8b580b6af3b544
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801320"
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="1b32d-103">ICorDebug::DebugActiveProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="1b32d-103">ICorDebug::DebugActiveProcess Method</span></span>

<span data-ttu-id="1b32d-104">デバッガーを既存のプロセスにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="1b32d-104">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b32d-105">構文</span><span class="sxs-lookup"><span data-stu-id="1b32d-105">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b32d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1b32d-106">Parameters</span></span>  

 `id`  
 <span data-ttu-id="1b32d-107">からデバッガーがアタッチされるプロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="1b32d-107">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="1b32d-108">から `true` デバッガーがプロセスの Win32 デバッガーとして動作し、アンマネージコールバックをディスパッチする場合はに設定されるブール値。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="1b32d-108">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="1b32d-109">入出力デバッガーがアタッチされているプロセスを表す "いいプロセス" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1b32d-109">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b32d-110">解説</span><span class="sxs-lookup"><span data-stu-id="1b32d-110">Remarks</span></span>  

 <span data-ttu-id="1b32d-111">相互運用デバッグは、IA-64 ベースおよび AMD64 ベースのプラットフォームなど、Win9x および x86 以外のプラットフォームではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1b32d-111">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b32d-112">要件</span><span class="sxs-lookup"><span data-stu-id="1b32d-112">Requirements</span></span>  

 <span data-ttu-id="1b32d-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b32d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b32d-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b32d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b32d-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b32d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b32d-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b32d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b32d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b32d-117">See also</span></span>

- [<span data-ttu-id="1b32d-118">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b32d-118">ICorDebug Interface</span></span>](icordebug-interface.md)
