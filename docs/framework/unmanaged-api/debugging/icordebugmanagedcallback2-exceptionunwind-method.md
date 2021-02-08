---
description: '詳細情報: ICorDebugManagedCallback2:: ExceptionUnwind ワインドメソッド'
title: ICorDebugManagedCallback2::ExceptionUnwind メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
ms.openlocfilehash: 2d98fb21cdbb0db25a11761ac9b00e99e1526cc0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790848"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="4d476-103">ICorDebugManagedCallback2::ExceptionUnwind メソッド</span><span class="sxs-lookup"><span data-stu-id="4d476-103">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>

<span data-ttu-id="4d476-104">例外アンワインド処理中の状態通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="4d476-104">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d476-105">構文</span><span class="sxs-lookup"><span data-stu-id="4d476-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d476-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4d476-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="4d476-107">から例外がスローされたスレッドを含むアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4d476-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="4d476-108">から例外がスローされたスレッドを表す、スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4d476-108">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="4d476-109">からアンワインドフェーズ中にコールバックによって通知されるイベントを指定する CorDebugExceptionUnwindCallbackType 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="4d476-109">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4d476-110">から例外に関する追加情報を指定する [Cordebugexceptionflags](cordebugexceptionflags-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="4d476-110">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d476-111">解説</span><span class="sxs-lookup"><span data-stu-id="4d476-111">Remarks</span></span>  

 <span data-ttu-id="4d476-112">`ExceptionUnwind` は、例外処理プロセスのアンワインドフェーズ中にさまざまなポイントで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4d476-112">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="4d476-113">`ExceptionUnwind` 1つの例外をアンワインドしている間に、複数回呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="4d476-113">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="4d476-114">が `dwEventType` DEBUG_EXCEPTION_INTERCEPTED の場合、命令ポインターは、例外の原因となった命令の前 (これは複数の命令になることがあります) に、スレッドのリーフフレームに配置されます。</span><span class="sxs-lookup"><span data-stu-id="4d476-114">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d476-115">要件</span><span class="sxs-lookup"><span data-stu-id="4d476-115">Requirements</span></span>  

 <span data-ttu-id="4d476-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d476-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d476-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d476-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d476-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d476-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d476-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d476-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d476-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d476-120">See also</span></span>

- [<span data-ttu-id="4d476-121">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4d476-121">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="4d476-122">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4d476-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
