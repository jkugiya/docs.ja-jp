---
description: '詳細については、次のページを参照してください:: いい評価:: Abort メソッド'
title: ICorDebugEval::Abort メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.Abort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::Abort
helpviewer_keywords:
- Abort method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::Abort method [.NET Framework debugging]
ms.assetid: 7070b6d0-f2e0-44ff-b124-0944cd807e69
topic_type:
- apiref
ms.openlocfilehash: d61cb0d696a8a134d992bc8dbbfdb61103ef469f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694319"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="f26b7-103">ICorDebugEval::Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="f26b7-103">ICorDebugEval::Abort Method</span></span>

<span data-ttu-id="f26b7-104">こののオブジェクトが現在実行している計算を中止します。</span><span class="sxs-lookup"><span data-stu-id="f26b7-104">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f26b7-105">構文</span><span class="sxs-lookup"><span data-stu-id="f26b7-105">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f26b7-106">解説</span><span class="sxs-lookup"><span data-stu-id="f26b7-106">Remarks</span></span>  

 <span data-ttu-id="f26b7-107">評価が入れ子になっていて、それが最新ではない場合、 `Abort` メソッドは失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f26b7-107">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f26b7-108">要件</span><span class="sxs-lookup"><span data-stu-id="f26b7-108">Requirements</span></span>  

 <span data-ttu-id="f26b7-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f26b7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f26b7-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f26b7-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f26b7-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f26b7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f26b7-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f26b7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
