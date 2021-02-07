---
description: '詳細については、次を参照してください: を参照してください。 \n Objectvalue:: IsValueClass メソッド'
title: ICorDebugObjectValue::IsValueClass メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.IsValueClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::IsValueClass
helpviewer_keywords:
- ICorDebugObjectValue::IsValueClass method [.NET Framework debugging]
- IsValueClass method [.NET Framework debugging]
ms.assetid: 13d89a4a-5d9d-4a79-9600-5e2a98c3d166
topic_type:
- apiref
ms.openlocfilehash: bf3ce94a06092209507fd1ff737e09a77b5d0c70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728926"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="229bb-103">ICorDebugObjectValue::IsValueClass メソッド</span><span class="sxs-lookup"><span data-stu-id="229bb-103">ICorDebugObjectValue::IsValueClass Method</span></span>

<span data-ttu-id="229bb-104">このオブジェクトの値が値の型であるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="229bb-104">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="229bb-105">構文</span><span class="sxs-lookup"><span data-stu-id="229bb-105">Syntax</span></span>  
  
```cpp  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="229bb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="229bb-106">Parameters</span></span>  

 `pbIsValueClass`  
 <span data-ttu-id="229bb-107">入出力 `true` この "いい Objectvalue" で表されるオブジェクト値が参照型ではなく値型である場合は、ブール値へのポインター。それ以外の場合は、 `pbIsValueClass` が `false` です。</span><span class="sxs-lookup"><span data-stu-id="229bb-107">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="229bb-108">要件</span><span class="sxs-lookup"><span data-stu-id="229bb-108">Requirements</span></span>  

 <span data-ttu-id="229bb-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="229bb-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="229bb-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="229bb-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="229bb-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="229bb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="229bb-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="229bb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="229bb-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="229bb-113">See also</span></span>
