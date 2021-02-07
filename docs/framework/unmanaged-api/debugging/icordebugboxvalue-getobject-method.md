---
description: '詳細については、次を参照してください: を参照してください。値:: GetObject メソッド'
title: ICorDebugBoxValue::GetObject メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type:
- apiref
ms.openlocfilehash: fc5376fa7ddbbeae3464427b34caf991d0a2f59a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711862"
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="2e0d1-103">ICorDebugBoxValue::GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="2e0d1-103">ICorDebugBoxValue::GetObject Method</span></span>

<span data-ttu-id="2e0d1-104">ボックス化された値を取得します。</span><span class="sxs-lookup"><span data-stu-id="2e0d1-104">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e0d1-105">構文</span><span class="sxs-lookup"><span data-stu-id="2e0d1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e0d1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2e0d1-106">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="2e0d1-107">入出力ボックス化された値を表す、ボックス化された値を表すオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2e0d1-107">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e0d1-108">要件</span><span class="sxs-lookup"><span data-stu-id="2e0d1-108">Requirements</span></span>  

 <span data-ttu-id="2e0d1-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e0d1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e0d1-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e0d1-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e0d1-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e0d1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e0d1-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e0d1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
