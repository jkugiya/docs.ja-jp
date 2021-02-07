---
description: '詳細については、次のページを参照してください:: いい評価:: GetThread メソッド'
title: ICorDebugEval::GetThread メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::GetThread method [.NET Framework debugging]
ms.assetid: 57163b0d-c8a7-44af-9078-e7a895d29f9a
topic_type:
- apiref
ms.openlocfilehash: 3e7120f618abce31b9940a886fd6b2b2f8639d2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694150"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="f57c9-103">ICorDebugEval::GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="f57c9-103">ICorDebugEval::GetThread Method</span></span>

<span data-ttu-id="f57c9-104">この評価が実行されている、または実行されるスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="f57c9-104">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f57c9-105">構文</span><span class="sxs-lookup"><span data-stu-id="f57c9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f57c9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f57c9-106">Parameters</span></span>  

 `ppThread`  
 <span data-ttu-id="f57c9-107">入出力スレッドを表す、スレッドオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f57c9-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f57c9-108">要件</span><span class="sxs-lookup"><span data-stu-id="f57c9-108">Requirements</span></span>  

 <span data-ttu-id="f57c9-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f57c9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f57c9-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f57c9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f57c9-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f57c9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f57c9-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f57c9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
