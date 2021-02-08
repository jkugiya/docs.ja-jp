---
description: '詳細情報: ICorDebugManagedCallback2:: Exception メソッド'
title: ICorDebugManagedCallback2::Exception メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
ms.openlocfilehash: 18fd4efcfbd1f13ce527b212d7450ba0d7651a3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790881"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="de1eb-103">ICorDebugManagedCallback2::Exception メソッド</span><span class="sxs-lookup"><span data-stu-id="de1eb-103">ICorDebugManagedCallback2::Exception Method</span></span>

<span data-ttu-id="de1eb-104">例外ハンドラーの検索が開始されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="de1eb-104">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de1eb-105">構文</span><span class="sxs-lookup"><span data-stu-id="de1eb-105">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de1eb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="de1eb-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="de1eb-107">から例外がスローされたスレッドを含むアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="de1eb-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="de1eb-108">から例外がスローされたスレッドを表す、スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="de1eb-108">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="de1eb-109">からパラメーターによって決定される、フレームを表すテキストボックスオブジェクトへのポインター `dwEventType` 。</span><span class="sxs-lookup"><span data-stu-id="de1eb-109">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="de1eb-110">詳細については、「解説」の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de1eb-110">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="de1eb-111">からパラメーターによって決定されるオフセットを指定する整数 `dwEventType` 。</span><span class="sxs-lookup"><span data-stu-id="de1eb-111">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="de1eb-112">詳細については、「解説」の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de1eb-112">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="de1eb-113">からこの例外コールバックの種類を指定する Cordebugexceptioncallback Type 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="de1eb-113">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="de1eb-114">から例外に関する追加情報を指定する [Cordebugexceptionflags](cordebugexceptionflags-enumeration.md) 列挙値</span><span class="sxs-lookup"><span data-stu-id="de1eb-114">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de1eb-115">解説</span><span class="sxs-lookup"><span data-stu-id="de1eb-115">Remarks</span></span>  

 <span data-ttu-id="de1eb-116">`Exception`コールバックは、例外処理プロセスの検索フェーズ中にさまざまなポイントで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="de1eb-116">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="de1eb-117">つまり、例外のアンワインド中に複数回呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="de1eb-117">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="de1eb-118">処理されている例外は、パラメーターによって参照されているスレッドオブジェクトから取得でき `pThread` ます。</span><span class="sxs-lookup"><span data-stu-id="de1eb-118">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="de1eb-119">特定のフレームとオフセットは、パラメーターによって次のように決定され `dwEventType` ます。</span><span class="sxs-lookup"><span data-stu-id="de1eb-119">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="de1eb-120">`dwEventType` の値</span><span class="sxs-lookup"><span data-stu-id="de1eb-120">Value of `dwEventType`</span></span>|<span data-ttu-id="de1eb-121">`pFrame` の値</span><span class="sxs-lookup"><span data-stu-id="de1eb-121">Value of `pFrame`</span></span>|<span data-ttu-id="de1eb-122">`nOffset` の値</span><span class="sxs-lookup"><span data-stu-id="de1eb-122">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="de1eb-123">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="de1eb-123">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="de1eb-124">例外をスローしたフレーム。</span><span class="sxs-lookup"><span data-stu-id="de1eb-124">The frame that threw the exception.</span></span>|<span data-ttu-id="de1eb-125">フレーム内の命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="de1eb-125">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="de1eb-126">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="de1eb-126">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="de1eb-127">スローされた例外のポイントに最も近いユーザーコードフレーム。</span><span class="sxs-lookup"><span data-stu-id="de1eb-127">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="de1eb-128">フレーム内の命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="de1eb-128">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="de1eb-129">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="de1eb-129">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="de1eb-130">Catch ハンドラーを格納しているフレーム。</span><span class="sxs-lookup"><span data-stu-id="de1eb-130">The frame that contains the catch handler.</span></span>|<span data-ttu-id="de1eb-131">Catch ハンドラーの先頭の MSIL (Microsoft 中間言語) オフセット。</span><span class="sxs-lookup"><span data-stu-id="de1eb-131">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="de1eb-132">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="de1eb-132">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="de1eb-133">NULL</span><span class="sxs-lookup"><span data-stu-id="de1eb-133">NULL</span></span>|<span data-ttu-id="de1eb-134">未定義です。</span><span class="sxs-lookup"><span data-stu-id="de1eb-134">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="de1eb-135">要件</span><span class="sxs-lookup"><span data-stu-id="de1eb-135">Requirements</span></span>  

 <span data-ttu-id="de1eb-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de1eb-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de1eb-137">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de1eb-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de1eb-138">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de1eb-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de1eb-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de1eb-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de1eb-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="de1eb-140">See also</span></span>

- [<span data-ttu-id="de1eb-141">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de1eb-141">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="de1eb-142">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de1eb-142">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
