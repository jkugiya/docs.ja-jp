---
description: '詳細については、次を参照してください: を参照してください。値:: GetValue メソッド'
title: ICorDebugReferenceValue::GetValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::GetValue method [.NET Framework debugging]
ms.assetid: 5da07f99-6c70-46ec-b997-5ab6fb7106cd
topic_type:
- apiref
ms.openlocfilehash: 29e0c4997d3349b642381dcf69063de21c3f9330
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691022"
---
# <a name="icordebugreferencevaluegetvalue-method"></a><span data-ttu-id="e8ffd-103">ICorDebugReferenceValue::GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="e8ffd-103">ICorDebugReferenceValue::GetValue Method</span></span>

<span data-ttu-id="e8ffd-104">参照先のオブジェクトの現在のメモリアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-104">Gets the current memory address of the referenced object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8ffd-105">構文</span><span class="sxs-lookup"><span data-stu-id="e8ffd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] CORDB_ADDRESS   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8ffd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e8ffd-106">Parameters</span></span>  

 `pValue`  
 <span data-ttu-id="e8ffd-107">入出力このは、 `CORDB_ADDRESS` この参照値オブジェクトが指すオブジェクトのアドレスを指定する値へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-107">[out] A pointer to a `CORDB_ADDRESS` value that specifies the address of the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8ffd-108">要件</span><span class="sxs-lookup"><span data-stu-id="e8ffd-108">Requirements</span></span>  

 <span data-ttu-id="e8ffd-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8ffd-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8ffd-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8ffd-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8ffd-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8ffd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8ffd-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8ffd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
