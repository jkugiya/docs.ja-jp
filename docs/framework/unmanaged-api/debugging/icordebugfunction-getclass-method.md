---
description: '詳細については、次を参照してください: の関数:: GetClass メソッド'
title: ICorDebugFunction::GetClass メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetClass
helpviewer_keywords:
- GetClass method, ICorDebugFunction interface [.NET Framework debugging]
- ICorDebugFunction::GetClass method [.NET Framework debugging]
ms.assetid: 27967230-144f-40d3-9e23-961d0241abd9
topic_type:
- apiref
ms.openlocfilehash: 09049962082bc51cc47a56b0de591a26c2ef93fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692590"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="f8631-103">ICorDebugFunction::GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="f8631-103">ICorDebugFunction::GetClass Method</span></span>

<span data-ttu-id="f8631-104">この関数がメンバーとなっているクラスを表す、のオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="f8631-104">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8631-105">構文</span><span class="sxs-lookup"><span data-stu-id="f8631-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8631-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f8631-106">Parameters</span></span>  

 `ppClass`  
 <span data-ttu-id="f8631-107">入出力クラスを表すオブジェクトのアドレスへのポインター `ICorDebugClass` 。この関数がクラスのメンバーでない場合は null。</span><span class="sxs-lookup"><span data-stu-id="f8631-107">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8631-108">要件</span><span class="sxs-lookup"><span data-stu-id="f8631-108">Requirements</span></span>  

 <span data-ttu-id="f8631-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8631-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8631-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8631-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8631-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8631-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8631-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8631-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
