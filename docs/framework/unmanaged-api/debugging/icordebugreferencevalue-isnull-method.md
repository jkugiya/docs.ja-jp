---
description: '詳細については、次を参照してください: を参照してください。値:: IsNull メソッド'
title: ICorDebugReferenceValue::IsNull メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
ms.openlocfilehash: 9fffc869e20d1d3aa3a347ff2e026e6b55e6bd4f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691030"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="cfbee-103">ICorDebugReferenceValue::IsNull メソッド</span><span class="sxs-lookup"><span data-stu-id="cfbee-103">ICorDebugReferenceValue::IsNull Method</span></span>

<span data-ttu-id="cfbee-104">この値が null 値であるかどうかを示す値を取得します。この場合、は `ICorDebugReferenceValue` オブジェクトを指していません。</span><span class="sxs-lookup"><span data-stu-id="cfbee-104">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfbee-105">構文</span><span class="sxs-lookup"><span data-stu-id="cfbee-105">Syntax</span></span>  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfbee-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cfbee-106">Parameters</span></span>  

 `pbNull`  
 <span data-ttu-id="cfbee-107">入出力このオブジェクトが null の場合はとなるブール値へのポインター。 `true` `ICorDebugReferenceValue` それ以外の場合は `pbNull` `false` 。</span><span class="sxs-lookup"><span data-stu-id="cfbee-107">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfbee-108">要件</span><span class="sxs-lookup"><span data-stu-id="cfbee-108">Requirements</span></span>  

 <span data-ttu-id="cfbee-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfbee-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfbee-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cfbee-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfbee-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfbee-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfbee-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfbee-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
