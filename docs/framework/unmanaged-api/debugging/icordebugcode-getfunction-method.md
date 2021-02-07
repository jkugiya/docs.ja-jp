---
description: '詳細情報: ヘルプコード:: GetFunction メソッド'
title: ICorDebugCode::GetFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
ms.openlocfilehash: c90635bf1821d70d6d056d5cbd495ddfa2d2a2ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711207"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="e883c-103">ICorDebugCode::GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="e883c-103">ICorDebugCode::GetFunction Method</span></span>

<span data-ttu-id="e883c-104">この "コード" に関連付けられている "コード" を取得します。</span><span class="sxs-lookup"><span data-stu-id="e883c-104">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e883c-105">構文</span><span class="sxs-lookup"><span data-stu-id="e883c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e883c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e883c-106">Parameters</span></span>  

 `ppFunction`  
 <span data-ttu-id="e883c-107">入出力関数のアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e883c-107">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e883c-108">解説</span><span class="sxs-lookup"><span data-stu-id="e883c-108">Remarks</span></span>  

 <span data-ttu-id="e883c-109">`ICorDebugCode` と `ICorDebugFunction` は、一対一のリレーションシップを維持します。</span><span class="sxs-lookup"><span data-stu-id="e883c-109">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e883c-110">要件</span><span class="sxs-lookup"><span data-stu-id="e883c-110">Requirements</span></span>  

 <span data-ttu-id="e883c-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e883c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e883c-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e883c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e883c-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e883c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e883c-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e883c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
