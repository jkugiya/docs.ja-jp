---
description: 詳細については、「ereference メソッド」を参照してください:D。
title: ICorDebugReferenceValue::Dereference メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
ms.openlocfilehash: af225f746a9c67a90a7ad73046cd03401e4ba735
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691108"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="c9085-103">ICorDebugReferenceValue::Dereference メソッド</span><span class="sxs-lookup"><span data-stu-id="c9085-103">ICorDebugReferenceValue::Dereference Method</span></span>

<span data-ttu-id="c9085-104">参照されているオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="c9085-104">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9085-105">構文</span><span class="sxs-lookup"><span data-stu-id="c9085-105">Syntax</span></span>  
  
```cpp  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9085-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c9085-106">Parameters</span></span>  

 `ppValue`  
 <span data-ttu-id="c9085-107">入出力この値のオブジェクトが指すオブジェクトを表す ICorDebugValue のアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c9085-107">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9085-108">解説</span><span class="sxs-lookup"><span data-stu-id="c9085-108">Remarks</span></span>  

 <span data-ttu-id="c9085-109">`ICorDebugValue`オブジェクトは、その参照がまだ無効になっていない場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="c9085-109">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9085-110">要件</span><span class="sxs-lookup"><span data-stu-id="c9085-110">Requirements</span></span>  

 <span data-ttu-id="c9085-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9085-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9085-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9085-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9085-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9085-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9085-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9085-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
