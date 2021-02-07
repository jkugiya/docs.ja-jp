---
description: '詳細については、次のページを参照してください: いいね:: Attach メソッド'
title: ICorDebugAppDomain::Attach メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.Attach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::Attach
helpviewer_keywords:
- ICorDebugAppDomain::Attach method [.NET Framework debugging]
- Attach method [.NET Framework debugging]
ms.assetid: 0358b84a-4236-4c34-945b-4babff7df570
topic_type:
- apiref
ms.openlocfilehash: 94448937a735b30d0403a207992dae29920a93bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754278"
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="3030d-103">ICorDebugAppDomain::Attach メソッド</span><span class="sxs-lookup"><span data-stu-id="3030d-103">ICorDebugAppDomain::Attach Method</span></span>

<span data-ttu-id="3030d-104">デバッガーをアプリケーションドメインにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="3030d-104">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3030d-105">構文</span><span class="sxs-lookup"><span data-stu-id="3030d-105">Syntax</span></span>  
  
```cpp  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3030d-106">解説</span><span class="sxs-lookup"><span data-stu-id="3030d-106">Remarks</span></span>  

 <span data-ttu-id="3030d-107">イベントを受信し、アプリケーションドメインのデバッグを有効にするには、デバッガーがアプリケーションドメインにアタッチされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3030d-107">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3030d-108">要件</span><span class="sxs-lookup"><span data-stu-id="3030d-108">Requirements</span></span>  

 <span data-ttu-id="3030d-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3030d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3030d-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3030d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3030d-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3030d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3030d-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3030d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
