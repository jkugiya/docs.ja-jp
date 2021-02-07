---
description: '詳細については、次の情報を参照してください: いいね::D etach メソッド'
title: ICorDebugController::Detach メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
ms.openlocfilehash: 763386fa72fab023becf4a360556e61d500c7949
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764651"
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="0ea19-103">ICorDebugController::Detach メソッド</span><span class="sxs-lookup"><span data-stu-id="0ea19-103">ICorDebugController::Detach Method</span></span>

<span data-ttu-id="0ea19-104">プロセスまたはアプリケーションドメインからデバッガーをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="0ea19-104">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ea19-105">構文</span><span class="sxs-lookup"><span data-stu-id="0ea19-105">Syntax</span></span>  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0ea19-106">解説</span><span class="sxs-lookup"><span data-stu-id="0ea19-106">Remarks</span></span>  

 <span data-ttu-id="0ea19-107">プロセスまたはアプリケーションドメインは通常どおり実行されますが、"" のプロセス "オブジェクトまたは" 表示されない Appdomain "オブジェクトは無効になり、それ以上のコールバックは発生しません。</span><span class="sxs-lookup"><span data-stu-id="0ea19-107">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="0ea19-108">.NET Framework バージョン2.0 では、アンマネージデバッグが有効になっている場合、オペレーティングシステムの制限により、このメソッドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="0ea19-108">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ea19-109">要件</span><span class="sxs-lookup"><span data-stu-id="0ea19-109">Requirements</span></span>  

 <span data-ttu-id="0ea19-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ea19-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ea19-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ea19-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ea19-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ea19-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ea19-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ea19-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ea19-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ea19-114">See also</span></span>
