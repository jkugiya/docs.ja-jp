---
description: '詳細については、次を参照してください: の関数:: GetToken メソッド'
title: ICorDebugFunction::GetToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
ms.openlocfilehash: 75c8680252c5047aa7263940da76166597e5a283
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692421"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="43c87-103">ICorDebugFunction::GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="43c87-103">ICorDebugFunction::GetToken Method</span></span>

<span data-ttu-id="43c87-104">この関数のメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="43c87-104">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43c87-105">構文</span><span class="sxs-lookup"><span data-stu-id="43c87-105">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43c87-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="43c87-106">Parameters</span></span>  

 `pMethodDef`  
 <span data-ttu-id="43c87-107">入出力 `mdMethodDef` この関数のメタデータを参照するトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="43c87-107">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43c87-108">要件</span><span class="sxs-lookup"><span data-stu-id="43c87-108">Requirements</span></span>  

 <span data-ttu-id="43c87-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43c87-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43c87-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43c87-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43c87-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43c87-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43c87-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43c87-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
