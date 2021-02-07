---
description: '詳細について: ICorDebugMutableDataTarget:: ContinueStatusChanged メソッド'
title: ICorDebugMutableDataTarget::ContinueStatusChanged メソッド
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: 6655d6f1a115b4879c73e356faa8e8785a110078
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722504"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="a0591-103">ICorDebugMutableDataTarget::ContinueStatusChanged メソッド</span><span class="sxs-lookup"><span data-stu-id="a0591-103">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>

<span data-ttu-id="a0591-104">指定されたスレッド上の未処理のデバッグ イベントの継続状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="a0591-104">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0591-105">構文</span><span class="sxs-lookup"><span data-stu-id="a0591-105">Syntax</span></span>  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0591-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0591-106">Parameters</span></span>  

 `dwThreadId`  
 <span data-ttu-id="a0591-107">オペレーティング システム定義のスレッド識別子です。</span><span class="sxs-lookup"><span data-stu-id="a0591-107">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="a0591-108">新たに要求された継続状態を表す [COREDB_CONTINUE_STATUS](../common-data-types-unmanaged-api-reference.md) 値。</span><span class="sxs-lookup"><span data-stu-id="a0591-108">A [COREDB_CONTINUE_STATUS](../common-data-types-unmanaged-api-reference.md) value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0591-109">解説</span><span class="sxs-lookup"><span data-stu-id="a0591-109">Remarks</span></span>  

 <span data-ttu-id="a0591-110">デバッガーは、通常の方法とは異なることがある方法で現在のデバッグ イベントを処理するように要求する ICorDebug メソッドを呼び出すときに、`ContinueStatusChanged` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a0591-110">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="a0591-111">たとえば、未処理の例外が発生して、デバッガーが例外をキャンセルする操作 ([ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) または `FuncEval` など) を要求する場合、この API は例外のキャンセルを要求するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a0591-111">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0591-112">要件</span><span class="sxs-lookup"><span data-stu-id="a0591-112">Requirements</span></span>  

 <span data-ttu-id="a0591-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0591-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0591-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0591-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0591-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0591-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0591-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0591-116">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0591-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0591-117">See also</span></span>

- [<span data-ttu-id="a0591-118">ICorDebugMutableDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0591-118">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="a0591-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0591-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
