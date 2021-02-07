---
description: '詳細については、次のページを参照してください: いいでしょう:: GetCallee 先メソッド'
title: ICorDebugChain::GetCallee メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
ms.openlocfilehash: 4787893c86804c648dae14bf2e6f7425808104b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661424"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="76305-103">ICorDebugChain::GetCallee メソッド</span><span class="sxs-lookup"><span data-stu-id="76305-103">ICorDebugChain::GetCallee Method</span></span>

<span data-ttu-id="76305-104">このチェーンによって呼び出されたチェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="76305-104">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76305-105">構文</span><span class="sxs-lookup"><span data-stu-id="76305-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76305-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="76305-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="76305-107">入出力呼び出されたチェーンを表す、のオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="76305-107">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="76305-108">このチェーンが現在実行されている場合 (つまり、このチェーンが呼び出されたチェーンがを返すのを待機していない場合)、 `ppChain` は null になります。</span><span class="sxs-lookup"><span data-stu-id="76305-108">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76305-109">解説</span><span class="sxs-lookup"><span data-stu-id="76305-109">Remarks</span></span>  

 <span data-ttu-id="76305-110">このチェーンは、呼び出されたチェーンが返されるのを待機してから、実行を再開します。</span><span class="sxs-lookup"><span data-stu-id="76305-110">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="76305-111">スレッド間でマーシャリングされた呼び出しの場合、呼び出されたチェーンは別のスレッド上にある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="76305-111">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76305-112">要件</span><span class="sxs-lookup"><span data-stu-id="76305-112">Requirements</span></span>  

 <span data-ttu-id="76305-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76305-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76305-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76305-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76305-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76305-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76305-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76305-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
