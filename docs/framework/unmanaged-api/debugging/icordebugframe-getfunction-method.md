---
description: '詳細情報: テキスト枠:: GetFunction メソッド'
title: ICorDebugFrame::GetFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type:
- apiref
ms.openlocfilehash: 0309a066f686e55d086de1cbb040eea58e031df3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692993"
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="c8437-103">ICorDebugFrame::GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="c8437-103">ICorDebugFrame::GetFunction Method</span></span>

<span data-ttu-id="c8437-104">このスタックフレームに関連付けられているコードを格納している関数を取得します。</span><span class="sxs-lookup"><span data-stu-id="c8437-104">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8437-105">構文</span><span class="sxs-lookup"><span data-stu-id="c8437-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8437-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c8437-106">Parameters</span></span>  

 `ppFunction`  
 <span data-ttu-id="c8437-107">入出力このスタックフレームに関連付けられているコードを格納している関数を表す、オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c8437-107">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8437-108">解説</span><span class="sxs-lookup"><span data-stu-id="c8437-108">Remarks</span></span>  

 <span data-ttu-id="c8437-109">`GetFunction`フレームが特定の関数に関連付けられていない場合、メソッドは失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c8437-109">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8437-110">要件</span><span class="sxs-lookup"><span data-stu-id="c8437-110">Requirements</span></span>  

 <span data-ttu-id="c8437-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8437-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8437-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8437-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8437-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8437-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8437-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8437-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
