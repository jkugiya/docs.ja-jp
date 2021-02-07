---
description: '詳細については、次を参照してください: を参照'
title: ICorDebugObjectValue::GetClass メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type:
- apiref
ms.openlocfilehash: 4ea6a47814777da934aa14bba947a047c075396c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722218"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="17077-103">ICorDebugObjectValue::GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="17077-103">ICorDebugObjectValue::GetClass Method</span></span>

<span data-ttu-id="17077-104">このオブジェクト値のクラスを取得します。</span><span class="sxs-lookup"><span data-stu-id="17077-104">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17077-105">構文</span><span class="sxs-lookup"><span data-stu-id="17077-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17077-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="17077-106">Parameters</span></span>  

 `ppClass`  
 <span data-ttu-id="17077-107">入出力この "いい Objectvalue" オブジェクトによって表されるオブジェクト値のクラスを表す "のクラス" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="17077-107">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17077-108">解説</span><span class="sxs-lookup"><span data-stu-id="17077-108">Remarks</span></span>  

 <span data-ttu-id="17077-109">`GetClass`および[ICorDebugValue:: GetType](icordebugvalue-gettype-method.md)メソッドはそれぞれ、値の型に関する情報を返します。これらはどちらも、ジェネリック対応[ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md)に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="17077-109">The `GetClass` and [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17077-110">要件</span><span class="sxs-lookup"><span data-stu-id="17077-110">Requirements</span></span>  

 <span data-ttu-id="17077-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17077-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17077-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17077-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17077-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17077-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17077-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17077-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17077-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="17077-115">See also</span></span>
