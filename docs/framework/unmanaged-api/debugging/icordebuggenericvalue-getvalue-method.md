---
description: '詳細については、次を参照してください: を参照'
title: ICorDebugGenericValue::GetValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type:
- apiref
ms.openlocfilehash: 9c8459ce6a9fb59e934b1ebd355aa091a37b2d7b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661065"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="3c43b-103">ICorDebugGenericValue::GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="3c43b-103">ICorDebugGenericValue::GetValue Method</span></span>

<span data-ttu-id="3c43b-104">このジェネリックの値を、指定したバッファーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="3c43b-104">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c43b-105">構文</span><span class="sxs-lookup"><span data-stu-id="3c43b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c43b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3c43b-106">Parameters</span></span>  

 `pTo`  
 <span data-ttu-id="3c43b-107">入出力このは、この値オブジェクトによって表される値へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="3c43b-107">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="3c43b-108">値には、単純型または参照型 (つまり、ポインター) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3c43b-108">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c43b-109">要件</span><span class="sxs-lookup"><span data-stu-id="3c43b-109">Requirements</span></span>  

 <span data-ttu-id="3c43b-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c43b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c43b-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c43b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c43b-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c43b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c43b-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c43b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
