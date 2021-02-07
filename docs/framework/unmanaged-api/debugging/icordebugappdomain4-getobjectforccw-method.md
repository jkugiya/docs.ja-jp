---
description: '詳細については、次を参照してください: ICorDebugAppDomain4:: GetObjectForCCW メソッド'
title: ICorDebugAppDomain4::GetObjectForCCW メソッド
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 5ba4923c933d02f5d6ad5c1fd8c4d0e2ddb410d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754135"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="d7afe-103">ICorDebugAppDomain4::GetObjectForCCW メソッド</span><span class="sxs-lookup"><span data-stu-id="d7afe-103">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>

<span data-ttu-id="d7afe-104">COM 呼び出し可能ラッパー (CCW: COM Callable Wrapper) ポインターからマネージド オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="d7afe-104">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7afe-105">構文</span><span class="sxs-lookup"><span data-stu-id="d7afe-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7afe-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d7afe-106">Parameters</span></span>  

 `ccwPointer`  
 <span data-ttu-id="d7afe-107">[in] COM 呼び出し可能ラッパー (CCW) ポインター。</span><span class="sxs-lookup"><span data-stu-id="d7afe-107">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="d7afe-108">入出力指定された CCW ポインターに対応するマネージオブジェクトを表す "ICorDebugValue" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d7afe-108">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7afe-109">解説</span><span class="sxs-lookup"><span data-stu-id="d7afe-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7afe-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="d7afe-110">Requirements</span></span>  

 <span data-ttu-id="d7afe-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7afe-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7afe-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7afe-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7afe-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7afe-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7afe-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7afe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7afe-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7afe-115">See also</span></span>

- [<span data-ttu-id="d7afe-116">ICorDebugAppDomain4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7afe-116">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="d7afe-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7afe-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
