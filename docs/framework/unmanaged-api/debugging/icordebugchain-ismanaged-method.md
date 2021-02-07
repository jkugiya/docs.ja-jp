---
description: '詳細については、次のページを参照してください: いいでしょう:: IsManaged メソッド'
title: ICorDebugChain::IsManaged メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type:
- apiref
ms.openlocfilehash: 200b76350d474645a40f8ee35859c2db5420ea0a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694853"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="36194-103">ICorDebugChain::IsManaged メソッド</span><span class="sxs-lookup"><span data-stu-id="36194-103">ICorDebugChain::IsManaged Method</span></span>

<span data-ttu-id="36194-104">このチェーンでマネージコードが実行されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="36194-104">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36194-105">構文</span><span class="sxs-lookup"><span data-stu-id="36194-105">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36194-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="36194-106">Parameters</span></span>  

 `pManaged`  
 <span data-ttu-id="36194-107">[出力] `true` このチェーンでマネージコードが実行されている場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="36194-107">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36194-108">要件</span><span class="sxs-lookup"><span data-stu-id="36194-108">Requirements</span></span>  

 <span data-ttu-id="36194-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36194-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36194-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36194-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36194-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36194-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36194-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36194-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
