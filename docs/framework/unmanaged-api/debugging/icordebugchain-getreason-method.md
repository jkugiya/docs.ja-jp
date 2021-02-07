---
description: '詳細情報: 動機チェーン:: GetReason メソッド'
title: ICorDebugChain::GetReason メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- GetReason
helpviewer_keywords:
- GetReason method [.NET Framework debugging]
- ICorDebugChain::GetReason method [.NET Framework debugging]
ms.assetid: 9f9f62b9-113a-4a98-8f9b-b593cef27b03
topic_type:
- apiref
ms.openlocfilehash: 0952d09db6d43f7970ba9e8c46c409fb2cd4b131
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694970"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="91db9-103">ICorDebugChain::GetReason メソッド</span><span class="sxs-lookup"><span data-stu-id="91db9-103">ICorDebugChain::GetReason Method</span></span>

<span data-ttu-id="91db9-104">この呼び出しチェーンの genesis の理由を取得します。</span><span class="sxs-lookup"><span data-stu-id="91db9-104">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91db9-105">構文</span><span class="sxs-lookup"><span data-stu-id="91db9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91db9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="91db9-106">Parameters</span></span>  

 `pReason`  
 <span data-ttu-id="91db9-107">入出力この呼び出しチェーンの genesis の理由を示す、CorDebugChainReason 列挙体の値 (ビットごとの組み合わせ) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="91db9-107">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91db9-108">要件</span><span class="sxs-lookup"><span data-stu-id="91db9-108">Requirements</span></span>  

 <span data-ttu-id="91db9-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91db9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91db9-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91db9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91db9-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91db9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91db9-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91db9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
