---
description: '詳細については、次の情報を参照してください:: IsRunning メソッド'
title: ICorDebugController::IsRunning メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.IsRunning
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type:
- apiref
ms.openlocfilehash: 6a0628cc39765d9cb295877d912d92dbb27937da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764581"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="ae357-103">ICorDebugController::IsRunning メソッド</span><span class="sxs-lookup"><span data-stu-id="ae357-103">ICorDebugController::IsRunning Method</span></span>

<span data-ttu-id="ae357-104">プロセス内のスレッドが現在実行中であるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="ae357-104">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae357-105">構文</span><span class="sxs-lookup"><span data-stu-id="ae357-105">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae357-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ae357-106">Parameters</span></span>  

 `pbRunning`  
 <span data-ttu-id="ae357-107">入出力プロセス内のスレッドが自由に実行されている場合は、値へのポインター `true` 。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="ae357-107">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae357-108">要件</span><span class="sxs-lookup"><span data-stu-id="ae357-108">Requirements</span></span>  

 <span data-ttu-id="ae357-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae357-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae357-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae357-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae357-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae357-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae357-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae357-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae357-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae357-113">See also</span></span>
