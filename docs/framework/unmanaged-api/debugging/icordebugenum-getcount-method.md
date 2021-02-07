---
description: '詳細について: ICorDebugEnum:: GetCount メソッド'
title: ICorDebugEnum::GetCount メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::GetCount
helpviewer_keywords:
- ICorDebugEnum::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: d8a74304-1cb2-4977-a21d-e1af48c563ff
topic_type:
- apiref
ms.openlocfilehash: 38fa85958ea0c6945a5575d12700701ed355891d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694557"
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="67590-103">ICorDebugEnum::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="67590-103">ICorDebugEnum::GetCount Method</span></span>

<span data-ttu-id="67590-104">列挙に含まれる項目の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="67590-104">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67590-105">構文</span><span class="sxs-lookup"><span data-stu-id="67590-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67590-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="67590-106">Parameters</span></span>  

 `pcelt`  
 <span data-ttu-id="67590-107">入出力列挙体に含まれる項目の数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="67590-107">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67590-108">要件</span><span class="sxs-lookup"><span data-stu-id="67590-108">Requirements</span></span>  

 <span data-ttu-id="67590-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67590-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67590-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67590-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67590-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67590-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67590-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67590-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
