---
description: 詳細については、次を参照してください
title: ICorDebugMDA::GetFlags メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
ms.openlocfilehash: 53476da06252771627d4883ef9056eb7f945e1b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801177"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="a47c3-103">ICorDebugMDA::GetFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="a47c3-103">ICorDebugMDA::GetFlags Method</span></span>

<span data-ttu-id="a47c3-104">によって表されるマネージデバッグアシスタント (MDA) に関連付けら [れている](icordebugmda-interface.md)フラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="a47c3-104">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a47c3-105">構文</span><span class="sxs-lookup"><span data-stu-id="a47c3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a47c3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a47c3-106">Parameters</span></span>  

 `pFlags`  
 <span data-ttu-id="a47c3-107">からこの MDA のフラグの設定を指定する [Cordebugmdaflags](cordebugmdaflags-enumeration.md) 列挙値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="a47c3-107">[in] A bitwise combination of the [CorDebugMDAFlags](cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a47c3-108">要件</span><span class="sxs-lookup"><span data-stu-id="a47c3-108">Requirements</span></span>  

 <span data-ttu-id="a47c3-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a47c3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a47c3-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a47c3-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a47c3-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a47c3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a47c3-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a47c3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a47c3-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a47c3-113">See also</span></span>

- [<span data-ttu-id="a47c3-114">ICorDebugMDA インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a47c3-114">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="a47c3-115">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="a47c3-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
