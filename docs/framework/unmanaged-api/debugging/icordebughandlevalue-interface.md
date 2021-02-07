---
description: '詳細については、次を参照してください: いいね Value インターフェイス'
title: ICorDebugHandleValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
ms.openlocfilehash: 3bdb1f5668be283d8722c15f4779adfe4d7b3a2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692044"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="d1e5d-103">ICorDebugHandleValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d1e5d-103">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="d1e5d-104">デバッガーがガベージコレクションのハンドルを作成した参照値を表す、値のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="d1e5d-104">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d1e5d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d1e5d-105">Methods</span></span>  
  
|<span data-ttu-id="d1e5d-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d1e5d-106">Method</span></span>|<span data-ttu-id="d1e5d-107">説明</span><span class="sxs-lookup"><span data-stu-id="d1e5d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d1e5d-108">Dispose メソッド</span><span class="sxs-lookup"><span data-stu-id="d1e5d-108">Dispose Method</span></span>](icordebughandlevalue-dispose-method.md)|<span data-ttu-id="d1e5d-109">`ICorDebugHandleValue`インターフェイスポインターを明示的に解放せずに、このオブジェクトによって参照されるハンドルを解放します。</span><span class="sxs-lookup"><span data-stu-id="d1e5d-109">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="d1e5d-110">GetHandleType メソッド</span><span class="sxs-lookup"><span data-stu-id="d1e5d-110">GetHandleType Method</span></span>](icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="d1e5d-111">このによって参照されるハンドルの種類を記述する CorDebugHandleType 値を取得し `ICorDebugHandleValue` ます。</span><span class="sxs-lookup"><span data-stu-id="d1e5d-111">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1e5d-112">解説</span><span class="sxs-lookup"><span data-stu-id="d1e5d-112">Remarks</span></span>  

 <span data-ttu-id="d1e5d-113">`ICorDebugReferenceValue`デバッグ対象のコードの実行が中断された場合、オブジェクトは無効になります。</span><span class="sxs-lookup"><span data-stu-id="d1e5d-113">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="d1e5d-114">は、 `ICorDebugHandleValue` 明示的に解放されるまで、中断および継続による参照を保持します。</span><span class="sxs-lookup"><span data-stu-id="d1e5d-114">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1e5d-115">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d1e5d-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1e5d-116">要件</span><span class="sxs-lookup"><span data-stu-id="d1e5d-116">Requirements</span></span>  

 <span data-ttu-id="d1e5d-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1e5d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1e5d-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1e5d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1e5d-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1e5d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1e5d-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1e5d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1e5d-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1e5d-121">See also</span></span>

- [<span data-ttu-id="d1e5d-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d1e5d-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
