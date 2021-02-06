---
description: '詳細について: ICorDebugHeapValue3:: GetThreadOwningMonitorLock メソッド'
title: ICorDebugHeapValue3::GetThreadOwningMonitorLock メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
ms.openlocfilehash: 9bd9e251c1e04bffd749c0569e4716d4c6fa89e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660701"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="5c7f6-103">ICorDebugHeapValue3::GetThreadOwningMonitorLock メソッド</span><span class="sxs-lookup"><span data-stu-id="5c7f6-103">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>

<span data-ttu-id="5c7f6-104">このオブジェクトのモニターロックを所有するマネージスレッドを返します。</span><span class="sxs-lookup"><span data-stu-id="5c7f6-104">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c7f6-105">構文</span><span class="sxs-lookup"><span data-stu-id="5c7f6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c7f6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5c7f6-106">Parameters</span></span>  

 `ppThread`  
 <span data-ttu-id="5c7f6-107">入出力このオブジェクトのモニターロックを所有するマネージスレッド。</span><span class="sxs-lookup"><span data-stu-id="5c7f6-107">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="5c7f6-108">入出力このスレッドがロックを解除してから、所有が解除されるまでの回数。</span><span class="sxs-lookup"><span data-stu-id="5c7f6-108">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c7f6-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="5c7f6-109">Return Value</span></span>  

 <span data-ttu-id="5c7f6-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="5c7f6-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5c7f6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c7f6-111">HRESULT</span></span>|<span data-ttu-id="5c7f6-112">説明</span><span class="sxs-lookup"><span data-stu-id="5c7f6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c7f6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c7f6-113">S_OK</span></span>|<span data-ttu-id="5c7f6-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="5c7f6-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="5c7f6-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="5c7f6-115">S_FALSE</span></span>|<span data-ttu-id="5c7f6-116">このオブジェクトのモニターロックを所有しているマネージスレッドはありません。</span><span class="sxs-lookup"><span data-stu-id="5c7f6-116">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="5c7f6-117">例外</span><span class="sxs-lookup"><span data-stu-id="5c7f6-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c7f6-118">解説</span><span class="sxs-lookup"><span data-stu-id="5c7f6-118">Remarks</span></span>  

 <span data-ttu-id="5c7f6-119">マネージスレッドがこのオブジェクトのモニターロックを所有している場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5c7f6-119">If a managed thread owns the monitor lock on this object:</span></span>  
  
- <span data-ttu-id="5c7f6-120">メソッドは S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="5c7f6-120">The method returns S_OK.</span></span>  
  
- <span data-ttu-id="5c7f6-121">スレッドオブジェクトは、スレッドが終了するまで有効です。</span><span class="sxs-lookup"><span data-stu-id="5c7f6-121">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="5c7f6-122">このオブジェクトのモニターロックを所有しているマネージスレッドが存在しない場合、 `ppThread` と `pAcquisitionCount` は変更されず、メソッドは S_FALSE を返します。</span><span class="sxs-lookup"><span data-stu-id="5c7f6-122">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="5c7f6-123">`ppThread`または `pAcquisitionCount` が有効なポインターでない場合、結果は未定義になります。</span><span class="sxs-lookup"><span data-stu-id="5c7f6-123">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="5c7f6-124">このオブジェクトのモニターロックを所有しているスレッドが特定できない場合にエラーが発生すると、メソッドはエラーを示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="5c7f6-124">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c7f6-125">要件</span><span class="sxs-lookup"><span data-stu-id="5c7f6-125">Requirements</span></span>  

 <span data-ttu-id="5c7f6-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c7f6-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c7f6-127">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c7f6-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c7f6-128">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c7f6-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c7f6-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c7f6-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c7f6-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c7f6-130">See also</span></span>

- [<span data-ttu-id="5c7f6-131">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c7f6-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5c7f6-132">デバッグ</span><span class="sxs-lookup"><span data-stu-id="5c7f6-132">Debugging</span></span>](index.md)
