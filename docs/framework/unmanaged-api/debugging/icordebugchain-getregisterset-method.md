---
description: '詳細については、次を参照してください: いいね:: GetRegisterSet メソッド'
title: ICorDebugChain::GetRegisterSet メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetRegisterSet
helpviewer_keywords:
- ICorDebugChain::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: bc4288b6-3331-4ae3-990d-e1d6e62ecb67
topic_type:
- apiref
ms.openlocfilehash: 75c77838cb4ef49dd922a4e39b41e622693e928d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694957"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="92e58-103">ICorDebugChain::GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="92e58-103">ICorDebugChain::GetRegisterSet Method</span></span>

<span data-ttu-id="92e58-104">このチェーンのアクティブな部分のレジスタセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="92e58-104">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92e58-105">構文</span><span class="sxs-lookup"><span data-stu-id="92e58-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92e58-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="92e58-106">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="92e58-107">入出力このチェーンのアクティブな部分のレジスタセットを表す、 [のオブジェクトの](icordebugregisterset-interface.md) アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="92e58-107">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92e58-108">要件</span><span class="sxs-lookup"><span data-stu-id="92e58-108">Requirements</span></span>  

 <span data-ttu-id="92e58-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92e58-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92e58-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92e58-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92e58-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92e58-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92e58-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92e58-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
