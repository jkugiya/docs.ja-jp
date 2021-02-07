---
description: '詳細については、次を参照してください: GetResult メソッド'
title: ICorDebugEval::GetResult メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
ms.openlocfilehash: 03ab00f5c9a538e11a2046da9cbfd5ad7225231c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694241"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="96565-103">ICorDebugEval::GetResult メソッド</span><span class="sxs-lookup"><span data-stu-id="96565-103">ICorDebugEval::GetResult Method</span></span>

<span data-ttu-id="96565-104">この評価の結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="96565-104">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96565-105">構文</span><span class="sxs-lookup"><span data-stu-id="96565-105">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96565-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="96565-106">Parameters</span></span>  

 `ppResult`  
 <span data-ttu-id="96565-107">入出力評価が正常に完了した場合に、この評価の結果を表す ICorDebugValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="96565-107">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96565-108">解説</span><span class="sxs-lookup"><span data-stu-id="96565-108">Remarks</span></span>  

 <span data-ttu-id="96565-109">`GetResult`メソッドは、評価が完了した後にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="96565-109">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="96565-110">評価が正常に完了した場合は、 `ppResult` 結果を指定します。</span><span class="sxs-lookup"><span data-stu-id="96565-110">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="96565-111">例外が発生して終了した場合は、スローされた例外が結果になります。</span><span class="sxs-lookup"><span data-stu-id="96565-111">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="96565-112">新しいオブジェクトの評価がの場合、結果は新しいオブジェクトへの参照になります。</span><span class="sxs-lookup"><span data-stu-id="96565-112">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96565-113">要件</span><span class="sxs-lookup"><span data-stu-id="96565-113">Requirements</span></span>  

 <span data-ttu-id="96565-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96565-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96565-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96565-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96565-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96565-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96565-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96565-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
