---
description: '詳細について: ICorDebugFunction2:: GetJMCStatus メソッド'
title: ICorDebugFunction2::GetJMCStatus メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
ms.openlocfilehash: 42c72256df57b96a52737f4a0e5e90d6ba5d4e0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692291"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="e0c2f-103">ICorDebugFunction2::GetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="e0c2f-103">ICorDebugFunction2::GetJMCStatus Method</span></span>

<span data-ttu-id="e0c2f-104">この ICorDebugFunction2 オブジェクトによって表される関数がユーザーコードとしてマークされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="e0c2f-104">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0c2f-105">構文</span><span class="sxs-lookup"><span data-stu-id="e0c2f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0c2f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e0c2f-106">Parameters</span></span>  

 `pbIsJustMyCode`  
 <span data-ttu-id="e0c2f-107">入出力 `true`この関数がユーザーコードとしてマークされている場合は、ブール値へのポインター。それ以外の場合は、値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="e0c2f-107">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0c2f-108">解説</span><span class="sxs-lookup"><span data-stu-id="e0c2f-108">Remarks</span></span>  

 <span data-ttu-id="e0c2f-109">このによって表される関数を `ICorDebugFunction2` デバッグできない場合、 `pbIsJustMyCode` は常にになり `false` ます。</span><span class="sxs-lookup"><span data-stu-id="e0c2f-109">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0c2f-110">要件</span><span class="sxs-lookup"><span data-stu-id="e0c2f-110">Requirements</span></span>  

 <span data-ttu-id="e0c2f-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0c2f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0c2f-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0c2f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0c2f-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0c2f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0c2f-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0c2f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
