---
description: '詳細については、次のページを参照してください: いいでしょう:: GetCaller メソッド'
title: ICorDebugChain::GetCaller メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
ms.openlocfilehash: 5af2132b7fec9e70704db980b95221db6eb273f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695022"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="e888f-103">ICorDebugChain::GetCaller メソッド</span><span class="sxs-lookup"><span data-stu-id="e888f-103">ICorDebugChain::GetCaller Method</span></span>

<span data-ttu-id="e888f-104">このチェーンを呼び出したチェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="e888f-104">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e888f-105">構文</span><span class="sxs-lookup"><span data-stu-id="e888f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e888f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e888f-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="e888f-107">入出力呼び出し元チェーンを表す、のオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e888f-107">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="e888f-108">(このチェーンまたはデバッガーが呼び出し履歴を初期化した場合のように) このチェーンが自発的に呼び出された場合、 `ppChain` は null になります。</span><span class="sxs-lookup"><span data-stu-id="e888f-108">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e888f-109">解説</span><span class="sxs-lookup"><span data-stu-id="e888f-109">Remarks</span></span>  

 <span data-ttu-id="e888f-110">呼び出しがスレッド間でマーシャリングされている場合は、呼び出し元のチェーンが別のスレッドに存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e888f-110">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e888f-111">要件</span><span class="sxs-lookup"><span data-stu-id="e888f-111">Requirements</span></span>  

 <span data-ttu-id="e888f-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e888f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e888f-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e888f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e888f-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e888f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e888f-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e888f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
