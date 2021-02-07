---
description: '詳細については、次を参照してください: の関数:: CreateBreakpoint ポイントメソッド'
title: ICorDebugFunction::CreateBreakpoint メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::CreateBreakpoint
helpviewer_keywords:
- ICorDebugFunction::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: ffd0f708-0d21-4fae-a395-63b6c45828fa
topic_type:
- apiref
ms.openlocfilehash: 4d55a818352ff98b67c95d5ef15417f2e9e64d40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692629"
---
# <a name="icordebugfunctioncreatebreakpoint-method"></a><span data-ttu-id="7e91b-103">ICorDebugFunction::CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="7e91b-103">ICorDebugFunction::CreateBreakpoint Method</span></span>

<span data-ttu-id="7e91b-104">この関数の先頭にブレークポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="7e91b-104">Creates a breakpoint at the beginning of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e91b-105">構文</span><span class="sxs-lookup"><span data-stu-id="7e91b-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e91b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7e91b-106">Parameters</span></span>  

 `ppBreakpoint`  
 <span data-ttu-id="7e91b-107">入出力関数の新しいブレークポイントを表す、の新しいブレークポイントオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7e91b-107">[out] A pointer to the address of an ICorDebugFunctionBreakpoint object that represents the new breakpoint for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e91b-108">要件</span><span class="sxs-lookup"><span data-stu-id="7e91b-108">Requirements</span></span>  

 <span data-ttu-id="7e91b-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e91b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e91b-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e91b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e91b-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e91b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e91b-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e91b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
