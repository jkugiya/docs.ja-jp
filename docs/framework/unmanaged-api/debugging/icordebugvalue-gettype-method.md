---
description: '詳細情報: ICorDebugValue:: GetType メソッド'
title: ICorDebugValue::GetType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
ms.openlocfilehash: 750e73634683a03e811d2756cc62c16b6dcea3de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690328"
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="82fc5-103">ICorDebugValue::GetType メソッド</span><span class="sxs-lookup"><span data-stu-id="82fc5-103">ICorDebugValue::GetType Method</span></span>

<span data-ttu-id="82fc5-104">この "ICorDebugValue" オブジェクトのプリミティブ型を取得します。</span><span class="sxs-lookup"><span data-stu-id="82fc5-104">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82fc5-105">構文</span><span class="sxs-lookup"><span data-stu-id="82fc5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82fc5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="82fc5-106">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="82fc5-107">入出力値の型を示す "CorElementType" 列挙値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="82fc5-107">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82fc5-108">解説</span><span class="sxs-lookup"><span data-stu-id="82fc5-108">Remarks</span></span>  

 <span data-ttu-id="82fc5-109">オブジェクトが複雑な実行時の型である場合、その型はインターフェイスの適切なサブクラスを通じて検査される可能性があり `ICorDebugValue` ます。</span><span class="sxs-lookup"><span data-stu-id="82fc5-109">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="82fc5-110">たとえば、から継承する "" のような "という値は、 `ICorDebugValue` 複合型を表します。</span><span class="sxs-lookup"><span data-stu-id="82fc5-110">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="82fc5-111">`GetType`およびの各メソッドは、それぞれ値の型に関する情報[を](icordebugobjectvalue-getclass-method.md)返します。</span><span class="sxs-lookup"><span data-stu-id="82fc5-111">The `GetType` and [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="82fc5-112">これらはどちらも、ジェネリック対応 [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md) メソッドに置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="82fc5-112">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82fc5-113">要件</span><span class="sxs-lookup"><span data-stu-id="82fc5-113">Requirements</span></span>  

 <span data-ttu-id="82fc5-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82fc5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82fc5-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82fc5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82fc5-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82fc5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82fc5-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82fc5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82fc5-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="82fc5-118">See also</span></span>
