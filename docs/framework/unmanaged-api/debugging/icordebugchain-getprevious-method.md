---
description: '詳細については、次のページを参照してください: いいでしょう:: GetPrevious メソッド'
title: ICorDebugChain::GetPrevious メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetPrevious
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type:
- apiref
ms.openlocfilehash: 169c46afd545835e6da87686a8e74ecd12173904
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661286"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="601bd-103">ICorDebugChain::GetPrevious メソッド</span><span class="sxs-lookup"><span data-stu-id="601bd-103">ICorDebugChain::GetPrevious Method</span></span>

<span data-ttu-id="601bd-104">スレッドの前のフレームのチェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="601bd-104">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="601bd-105">構文</span><span class="sxs-lookup"><span data-stu-id="601bd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="601bd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="601bd-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="601bd-107">入出力このスレッドのフレームの前のチェーンを表す、のオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="601bd-107">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="601bd-108">このチェーンが最初のチェーンの場合、 `ppChain` は null です。</span><span class="sxs-lookup"><span data-stu-id="601bd-108">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="601bd-109">要件</span><span class="sxs-lookup"><span data-stu-id="601bd-109">Requirements</span></span>  

 <span data-ttu-id="601bd-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="601bd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="601bd-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="601bd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="601bd-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="601bd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="601bd-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="601bd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
