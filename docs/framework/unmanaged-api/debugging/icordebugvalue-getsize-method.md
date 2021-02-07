---
description: '詳細については、「ICorDebugValue:: GetSize メソッド」を参照してください。'
title: ICorDebugValue::GetSize メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
ms.openlocfilehash: 3fc2582990d58fa2e42f240dfd3e563eed34e372
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690341"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="6992e-103">ICorDebugValue::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="6992e-103">ICorDebugValue::GetSize Method</span></span>

<span data-ttu-id="6992e-104">この "ICorDebugValue" オブジェクトのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="6992e-104">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6992e-105">構文</span><span class="sxs-lookup"><span data-stu-id="6992e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6992e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6992e-106">Parameters</span></span>  

 `pSize`  
 <span data-ttu-id="6992e-107">入出力この値オブジェクトのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="6992e-107">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6992e-108">解説</span><span class="sxs-lookup"><span data-stu-id="6992e-108">Remarks</span></span>  

 <span data-ttu-id="6992e-109">値の型が参照型の場合、このメソッドはオブジェクトのサイズではなく、ポインターのサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="6992e-109">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="6992e-110">`ICorDebugValue::GetSize` `COR_E_OVERFLOW` 64 ビットプラットフォームで 4 GB を超えるオブジェクトの場合、メソッドはを返します。</span><span class="sxs-lookup"><span data-stu-id="6992e-110">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="6992e-111">4 GB を超えるオブジェクトには、代わりに [ICorDebugValue3:: GetSize64](icordebugvalue3-getsize64-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="6992e-111">Use the [ICorDebugValue3::GetSize64](icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6992e-112">要件</span><span class="sxs-lookup"><span data-stu-id="6992e-112">Requirements</span></span>  

 <span data-ttu-id="6992e-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6992e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6992e-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6992e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6992e-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6992e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6992e-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6992e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6992e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6992e-117">See also</span></span>

- [<span data-ttu-id="6992e-118">GetSize64 メソッド</span><span class="sxs-lookup"><span data-stu-id="6992e-118">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)
