---
description: '詳細について: ICorDebugValue2:: GetExactType メソッド'
title: ICorDebugValue2::GetExactType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
ms.openlocfilehash: d0ef08b119106ced89ec2094b5bf67d0c874b6bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690306"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="fb552-103">ICorDebugValue2::GetExactType メソッド</span><span class="sxs-lookup"><span data-stu-id="fb552-103">ICorDebugValue2::GetExactType Method</span></span>

<span data-ttu-id="fb552-104">この値のを表す "の型" オブジェクトへのインターフェイスポインターを取得し <xref:System.Type> ます。</span><span class="sxs-lookup"><span data-stu-id="fb552-104">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb552-105">構文</span><span class="sxs-lookup"><span data-stu-id="fb552-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb552-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fb552-106">Parameters</span></span>  

 `ppType`  
 <span data-ttu-id="fb552-107">入出力 `ICorDebugType` <xref:System.Type> この "ICorDebugValue2" オブジェクトによって表される値のを表すオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fb552-107">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb552-108">解説</span><span class="sxs-lookup"><span data-stu-id="fb552-108">Remarks</span></span>  

 <span data-ttu-id="fb552-109">ジェネリック対応のメソッドは、 `GetExactType` という2つ[のメソッド](icordebugvalue-gettype-method.md)(それぞれが値の型についての情報を返す) を置き換え[ます。](icordebugobjectvalue-getclass-method.md)</span><span class="sxs-lookup"><span data-stu-id="fb552-109">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb552-110">要件</span><span class="sxs-lookup"><span data-stu-id="fb552-110">Requirements</span></span>  

 <span data-ttu-id="fb552-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb552-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb552-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb552-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb552-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb552-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb552-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb552-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb552-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb552-115">See also</span></span>
