---
description: '詳細については、次を参照してください: GetHandleType メソッド'
title: ICorDebugHandleValue::GetHandleType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.GetHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::GetHandleType
helpviewer_keywords:
- GetHandleType method [.NET Framework debugging]
- ICorDebugHandleValue::GetHandleType method [.NET Framework debugging]
ms.assetid: d5e7b12d-835a-4e86-ae2f-d658d4f1c67c
topic_type:
- apiref
ms.openlocfilehash: 708d60cd8116cf3f0fdc436a34d863380be2543d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660961"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="b3229-103">ICorDebugHandleValue::GetHandleType メソッド</span><span class="sxs-lookup"><span data-stu-id="b3229-103">ICorDebugHandleValue::GetHandleType Method</span></span>

<span data-ttu-id="b3229-104">この値オブジェクトによって参照されるハンドルの種類を示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="b3229-104">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3229-105">構文</span><span class="sxs-lookup"><span data-stu-id="b3229-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3229-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b3229-106">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="b3229-107">入出力このハンドルの型を示す CorDebugHandleType 列挙値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b3229-107">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3229-108">要件</span><span class="sxs-lookup"><span data-stu-id="b3229-108">Requirements</span></span>  

 <span data-ttu-id="b3229-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3229-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3229-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3229-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3229-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3229-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3229-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3229-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
