---
description: '詳細については、次を参照してください: Okthread:: CreateEval メソッド'
title: ICorDebugThread::CreateEval メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type:
- apiref
ms.openlocfilehash: a789840e099a14b584e5713bee12f5c4b0717fe7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659388"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="a40db-103">ICorDebugThread::CreateEval メソッド</span><span class="sxs-lookup"><span data-stu-id="a40db-103">ICorDebugThread::CreateEval Method</span></span>

<span data-ttu-id="a40db-104">このスレッドの機能を収集して公開する、表示されるオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a40db-104">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a40db-105">構文</span><span class="sxs-lookup"><span data-stu-id="a40db-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a40db-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a40db-106">Parameters</span></span>  

 `ppEval`  
 <span data-ttu-id="a40db-107">入出力 `ICorDebugEval` このスレッドの機能を収集して公開するオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a40db-107">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a40db-108">解説</span><span class="sxs-lookup"><span data-stu-id="a40db-108">Remarks</span></span>  

 <span data-ttu-id="a40db-109">評価オブジェクトは、計算を実行する前に、スレッドに新しいチェーンをプッシュします。</span><span class="sxs-lookup"><span data-stu-id="a40db-109">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="a40db-110">これにより、評価が完了するまで、スレッドで現在実行されている計算が中断されます。</span><span class="sxs-lookup"><span data-stu-id="a40db-110">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a40db-111">要件</span><span class="sxs-lookup"><span data-stu-id="a40db-111">Requirements</span></span>  

 <span data-ttu-id="a40db-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a40db-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a40db-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a40db-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a40db-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a40db-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a40db-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a40db-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
