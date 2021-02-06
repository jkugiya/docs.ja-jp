---
description: '詳細については、次のページを参照してください: いい Thread:: GetDebugState メソッド'
title: ICorDebugThread::GetDebugState メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
ms.openlocfilehash: 86534dded9b8e931fe2a7e44f1c95dc2ec7b6f0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659154"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="27499-103">ICorDebugThread::GetDebugState メソッド</span><span class="sxs-lookup"><span data-stu-id="27499-103">ICorDebugThread::GetDebugState Method</span></span>

<span data-ttu-id="27499-104">このスレッドオブジェクトの現在のデバッグ状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="27499-104">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27499-105">構文</span><span class="sxs-lookup"><span data-stu-id="27499-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27499-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="27499-106">Parameters</span></span>  

 `pState`  
 <span data-ttu-id="27499-107">入出力このスレッドの現在のデバッグ状態を示す CorDebugThreadState 列挙値のビットごとの組み合わせへのポインター。</span><span class="sxs-lookup"><span data-stu-id="27499-107">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27499-108">解説</span><span class="sxs-lookup"><span data-stu-id="27499-108">Remarks</span></span>  

 <span data-ttu-id="27499-109">プロセスが現在停止されている場合、は、 `pState` このスレッドの実際の現在の状態ではなく、プロセスが続行された場合に存在する可能性があるデバッグ状態を表します。</span><span class="sxs-lookup"><span data-stu-id="27499-109">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27499-110">要件</span><span class="sxs-lookup"><span data-stu-id="27499-110">Requirements</span></span>  

 <span data-ttu-id="27499-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27499-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27499-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27499-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27499-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27499-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27499-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27499-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
