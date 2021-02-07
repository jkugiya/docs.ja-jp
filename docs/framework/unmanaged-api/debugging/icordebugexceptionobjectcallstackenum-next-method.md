---
description: 詳細については、次のページを参照してください:、次のメソッド
title: ICorDebugExceptionObjectCallStackEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum::Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type:
- apiref
ms.openlocfilehash: df68eb6e4794d294fc39dd943065582dc52a58a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693318"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="2e9fa-103">ICorDebugExceptionObjectCallStackEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="2e9fa-103">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>

<span data-ttu-id="2e9fa-104">例外オブジェクトの呼び出し履歴の情報を格納している、指定した数の [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="2e9fa-104">Gets the specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e9fa-105">構文</span><span class="sxs-lookup"><span data-stu-id="2e9fa-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e9fa-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2e9fa-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="2e9fa-107">から取得する [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) インスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="2e9fa-107">[in] The number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="2e9fa-108">入出力ポインターの配列。それぞれが [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) オブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="2e9fa-108">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="2e9fa-109">入出力実際に返された [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) インスタンスの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="2e9fa-109">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e9fa-110">解説</span><span class="sxs-lookup"><span data-stu-id="2e9fa-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e9fa-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="2e9fa-111">Requirements</span></span>  

 <span data-ttu-id="2e9fa-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e9fa-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e9fa-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e9fa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e9fa-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e9fa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e9fa-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e9fa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e9fa-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e9fa-116">See also</span></span>

- [<span data-ttu-id="2e9fa-117">ICorDebugExceptionObjectCallStackEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2e9fa-117">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="2e9fa-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2e9fa-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
