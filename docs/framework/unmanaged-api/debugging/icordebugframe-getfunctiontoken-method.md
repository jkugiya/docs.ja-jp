---
description: '詳細については、次のページを参照してください: テキストフレーム:: GetFunctionToken メソッド'
title: ICorDebugFrame::GetFunctionToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunctionToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunctionToken
helpviewer_keywords:
- ICorDebugFrame::GetFunctionToken method [.NET Framework debugging]
- GetFunctionToken method [.NET Framework debugging]
ms.assetid: a46925b3-3bf8-404f-9f30-a86ae41032c1
topic_type:
- apiref
ms.openlocfilehash: c64bb8d59c8de03c3d8c667384ffe4118c996d8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692941"
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="c8c2d-103">ICorDebugFrame::GetFunctionToken メソッド</span><span class="sxs-lookup"><span data-stu-id="c8c2d-103">ICorDebugFrame::GetFunctionToken Method</span></span>

<span data-ttu-id="c8c2d-104">このスタックフレームに関連付けられているコードを含む関数のメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="c8c2d-104">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8c2d-105">構文</span><span class="sxs-lookup"><span data-stu-id="c8c2d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8c2d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c8c2d-106">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="c8c2d-107">入出力 `mdMethodDef` 関数のメタデータを参照するトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c8c2d-107">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8c2d-108">要件</span><span class="sxs-lookup"><span data-stu-id="c8c2d-108">Requirements</span></span>  

 <span data-ttu-id="c8c2d-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8c2d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8c2d-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8c2d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8c2d-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8c2d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8c2d-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8c2d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
