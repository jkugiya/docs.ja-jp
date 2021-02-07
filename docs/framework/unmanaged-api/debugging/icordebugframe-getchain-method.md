---
description: '詳細情報: テキストフレーム:: GetChain メソッド'
title: ICorDebugFrame::GetChain メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetChain
helpviewer_keywords:
- ICorDebugFrame::GetChain method [.NET Framework debugging]
- GetChain method [.NET Framework debugging]
ms.assetid: e28e51d3-8f73-494f-bcd4-48bac239fbe1
topic_type:
- apiref
ms.openlocfilehash: d162d484a54f107fb5937e57f60e2b82cad90ca1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693058"
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="06b9e-103">ICorDebugFrame::GetChain メソッド</span><span class="sxs-lookup"><span data-stu-id="06b9e-103">ICorDebugFrame::GetChain Method</span></span>

<span data-ttu-id="06b9e-104">このフレームが含まれているチェーンへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="06b9e-104">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06b9e-105">構文</span><span class="sxs-lookup"><span data-stu-id="06b9e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06b9e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="06b9e-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="06b9e-107">入出力このフレームを含むチェーンを表す、のオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="06b9e-107">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06b9e-108">要件</span><span class="sxs-lookup"><span data-stu-id="06b9e-108">Requirements</span></span>  

 <span data-ttu-id="06b9e-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06b9e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06b9e-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06b9e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06b9e-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06b9e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06b9e-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06b9e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
