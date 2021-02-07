---
description: '詳細について: ICorDebugValue3:: GetSize64 メソッド'
title: ICorDebugValue3::GetSize64 メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
ms.openlocfilehash: ce7db5211c6a8fc16b58e0197fa3142b5b744d96
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690198"
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="97d1e-103">ICorDebugValue3::GetSize64 メソッド</span><span class="sxs-lookup"><span data-stu-id="97d1e-103">ICorDebugValue3::GetSize64 Method</span></span>

<span data-ttu-id="97d1e-104">この [ICorDebugValue3](icordebugvalue3-interface.md) オブジェクトのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="97d1e-104">Gets the size, in bytes, of this [ICorDebugValue3](icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d1e-105">構文</span><span class="sxs-lookup"><span data-stu-id="97d1e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97d1e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="97d1e-106">Parameters</span></span>  

 <span data-ttu-id="97d1e-107">pSize</span><span class="sxs-lookup"><span data-stu-id="97d1e-107">pSize</span></span>  
 <span data-ttu-id="97d1e-108">入出力このオブジェクトのサイズ (バイト単位) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="97d1e-108">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97d1e-109">解説</span><span class="sxs-lookup"><span data-stu-id="97d1e-109">Remarks</span></span>  

 <span data-ttu-id="97d1e-110">この値の型が参照型の場合、このメソッドはオブジェクトのサイズではなく、ポインターのサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="97d1e-110">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="97d1e-111">メソッドは、 `ICorDebugValue3::GetSize` その出力パラメーターの型の [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md) メソッドとは異なります。</span><span class="sxs-lookup"><span data-stu-id="97d1e-111">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="97d1e-112">[ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md)では、出力パラメーターはです。では、は `ULONG32` `ICorDebugValue3::GetSize` `ULONG64` です。</span><span class="sxs-lookup"><span data-stu-id="97d1e-112">In [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="97d1e-113">これにより、 [ICorDebugValue3](icordebugvalue3-interface.md) インターフェイスは、2gb を超える配列のサイズを報告できます。</span><span class="sxs-lookup"><span data-stu-id="97d1e-113">This enables the [ICorDebugValue3](icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97d1e-114">要件</span><span class="sxs-lookup"><span data-stu-id="97d1e-114">Requirements</span></span>  

 <span data-ttu-id="97d1e-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97d1e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97d1e-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97d1e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97d1e-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97d1e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97d1e-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97d1e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d1e-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="97d1e-119">See also</span></span>

- [<span data-ttu-id="97d1e-120">ICorDebugValue3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="97d1e-120">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="97d1e-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="97d1e-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
