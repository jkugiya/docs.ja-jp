---
description: '詳細について: ICorDebug:: EnumerateProcesses メソッド'
title: ICorDebug::EnumerateProcesses メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.EnumerateProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type:
- apiref
ms.openlocfilehash: 44ee21a820a1c9f94f1d66c93ff040b504bfcc93
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791583"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="71ff7-103">ICorDebug::EnumerateProcesses メソッド</span><span class="sxs-lookup"><span data-stu-id="71ff7-103">ICorDebug::EnumerateProcesses Method</span></span>

<span data-ttu-id="71ff7-104">デバッグ中のプロセスの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="71ff7-104">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71ff7-105">構文</span><span class="sxs-lookup"><span data-stu-id="71ff7-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71ff7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="71ff7-106">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="71ff7-107">デバッグ中のプロセスの列挙子である、のオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="71ff7-107">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71ff7-108">要件</span><span class="sxs-lookup"><span data-stu-id="71ff7-108">Requirements</span></span>  

 <span data-ttu-id="71ff7-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71ff7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71ff7-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71ff7-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71ff7-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71ff7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71ff7-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71ff7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71ff7-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="71ff7-113">See also</span></span>

- [<span data-ttu-id="71ff7-114">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71ff7-114">ICorDebug Interface</span></span>](icordebug-interface.md)
