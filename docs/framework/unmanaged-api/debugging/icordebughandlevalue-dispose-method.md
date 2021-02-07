---
description: '詳細については、次を参照してください: いいね Value::D ispose メソッド'
title: ICorDebugHandleValue::Dispose メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.Dispose
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::Dispose
helpviewer_keywords:
- ICorDebugHandleValue::Dispose method [.NET Framework debugging]
- Dispose method [.NET Framework debugging]
ms.assetid: c1542811-0a7f-4235-bcfd-b24370d6f24b
topic_type:
- apiref
ms.openlocfilehash: e39ff66137e12ebc939e1e060dd37ea8af9b623a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692057"
---
# <a name="icordebughandlevaluedispose-method"></a><span data-ttu-id="ff9e6-103">ICorDebugHandleValue::Dispose メソッド</span><span class="sxs-lookup"><span data-stu-id="ff9e6-103">ICorDebugHandleValue::Dispose Method</span></span>

<span data-ttu-id="ff9e6-104">インターフェイスポインターを明示的に解放せずに、このオブジェクトによって参照されるハンドルを解放します。</span><span class="sxs-lookup"><span data-stu-id="ff9e6-104">Releases the handle referenced by this ICorDebugHandleValue object without explicitly releasing the interface pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff9e6-105">構文</span><span class="sxs-lookup"><span data-stu-id="ff9e6-105">Syntax</span></span>  
  
```cpp  
HRESULT Dispose ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="ff9e6-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="ff9e6-106">Requirements</span></span>  

 <span data-ttu-id="ff9e6-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff9e6-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff9e6-108">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff9e6-108">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff9e6-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff9e6-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff9e6-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff9e6-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
