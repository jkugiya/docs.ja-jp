---
description: '詳細情報: テキストチェーン:: GetActiveFrame メソッド'
title: ICorDebugChain::GetActiveFrame メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
ms.openlocfilehash: d46906d9d6c671880d9446d889cdf9f83f3b4366
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661423"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="ac0d1-103">ICorDebugChain::GetActiveFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="ac0d1-103">ICorDebugChain::GetActiveFrame Method</span></span>

<span data-ttu-id="ac0d1-104">チェーンのアクティブな (つまり、最新の) フレームを取得します。</span><span class="sxs-lookup"><span data-stu-id="ac0d1-104">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac0d1-105">構文</span><span class="sxs-lookup"><span data-stu-id="ac0d1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac0d1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac0d1-106">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="ac0d1-107">入出力チェーン上のアクティブな (つまり、最新の) フレームを表す、の各フレームオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac0d1-107">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac0d1-108">解説</span><span class="sxs-lookup"><span data-stu-id="ac0d1-108">Remarks</span></span>  

 <span data-ttu-id="ac0d1-109">使用できるマネージスタックフレームがない場合、 `ppFrame` は null に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ac0d1-109">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="ac0d1-110">アクティブなフレームが使用できない場合、呼び出しは成功し、 `ppFrame` は null になります。</span><span class="sxs-lookup"><span data-stu-id="ac0d1-110">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="ac0d1-111">CHAIN_ENTER_UNMANAGED によって開始されるチェーンと、CHAIN_CLASS_INIT によって開始されるチェーンに対して、アクティブなフレームは使用できません。</span><span class="sxs-lookup"><span data-stu-id="ac0d1-111">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="ac0d1-112">CorDebugChainReason 列挙体を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac0d1-112">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac0d1-113">要件</span><span class="sxs-lookup"><span data-stu-id="ac0d1-113">Requirements</span></span>  

 <span data-ttu-id="ac0d1-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac0d1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac0d1-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac0d1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac0d1-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac0d1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac0d1-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac0d1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
