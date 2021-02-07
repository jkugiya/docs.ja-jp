---
description: '詳細については、次を参照してください: の関数:: GetModule メソッド'
title: ICorDebugFunction::GetModule メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetModule
helpviewer_keywords:
- ICorDebugFunction::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 5031a5d3-2564-412a-9007-e36d4631308a
topic_type:
- apiref
ms.openlocfilehash: 62087cdf0443b2ef495461aab74cfa047b95efca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692460"
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="9f900-103">ICorDebugFunction::GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="9f900-103">ICorDebugFunction::GetModule Method</span></span>

<span data-ttu-id="9f900-104">この関数が定義されているモジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="9f900-104">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f900-105">構文</span><span class="sxs-lookup"><span data-stu-id="9f900-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f900-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f900-106">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="9f900-107">入出力この関数が定義されているモジュールを表す、モジュールオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9f900-107">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f900-108">要件</span><span class="sxs-lookup"><span data-stu-id="9f900-108">Requirements</span></span>  

 <span data-ttu-id="9f900-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f900-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f900-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f900-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f900-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f900-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f900-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f900-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
