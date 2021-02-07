---
description: 詳細について
title: ICorDebugFunctionBreakpoint インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint
helpviewer_keywords:
- ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type:
- apiref
ms.openlocfilehash: 5d7597369241272d91de4b94a60d787304dc1c6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661130"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="cf11b-103">ICorDebugFunctionBreakpoint インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf11b-103">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="cf11b-104">ICorDebugBreakpoint インターフェイスを拡張して、関数内のブレークポイントをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cf11b-104">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf11b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="cf11b-105">Methods</span></span>  
  
|<span data-ttu-id="cf11b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="cf11b-106">Method</span></span>|<span data-ttu-id="cf11b-107">説明</span><span class="sxs-lookup"><span data-stu-id="cf11b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf11b-108">GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="cf11b-108">GetFunction Method</span></span>](icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="cf11b-109">ブレークポイントが設定されている関数を参照する、のオブジェクトへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="cf11b-109">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="cf11b-110">GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="cf11b-110">GetOffset Method</span></span>](icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="cf11b-111">関数内のブレークポイントのオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="cf11b-111">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf11b-112">解説</span><span class="sxs-lookup"><span data-stu-id="cf11b-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf11b-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="cf11b-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf11b-114">要件</span><span class="sxs-lookup"><span data-stu-id="cf11b-114">Requirements</span></span>  

 <span data-ttu-id="cf11b-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf11b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf11b-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf11b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf11b-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf11b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf11b-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf11b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf11b-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf11b-119">See also</span></span>

- [<span data-ttu-id="cf11b-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf11b-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
