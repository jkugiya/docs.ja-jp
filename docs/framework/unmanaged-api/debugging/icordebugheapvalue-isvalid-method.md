---
description: '詳細については、次の情報を参照してください:: の実行します。'
title: ICorDebugHeapValue::IsValid メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
ms.openlocfilehash: 27eca844170b31934cd32dad5cf5fccc0b0e324e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660791"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="e5533-103">ICorDebugHeapValue::IsValid メソッド</span><span class="sxs-lookup"><span data-stu-id="e5533-103">ICorDebugHeapValue::IsValid Method</span></span>

<span data-ttu-id="e5533-104">この値によって表されるオブジェクトが有効かどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="e5533-104">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="e5533-105">このメソッドは .NET Framework バージョン2.0 では非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="e5533-105">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5533-106">構文</span><span class="sxs-lookup"><span data-stu-id="e5533-106">Syntax</span></span>  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5533-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e5533-107">Parameters</span></span>  

 `pbValid`  
 <span data-ttu-id="e5533-108">入出力ヒープ上のこの値が有効かどうかを示すブール値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e5533-108">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5533-109">解説</span><span class="sxs-lookup"><span data-stu-id="e5533-109">Remarks</span></span>  

 <span data-ttu-id="e5533-110">値は、ガベージコレクターによって回収されている場合は無効です。</span><span class="sxs-lookup"><span data-stu-id="e5533-110">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="e5533-111">このメソッドの使用は非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="e5533-111">This method has been deprecated.</span></span> <span data-ttu-id="e5533-112">.NET Framework 2.0 では、すべての値は、"の値は無効になります。 [" が呼び出されるまで、](icordebugcontroller-continue-method.md) すべての値が有効になります。</span><span class="sxs-lookup"><span data-stu-id="e5533-112">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5533-113">要件</span><span class="sxs-lookup"><span data-stu-id="e5533-113">Requirements</span></span>  

 <span data-ttu-id="e5533-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5533-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5533-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5533-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5533-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5533-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5533-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5533-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
