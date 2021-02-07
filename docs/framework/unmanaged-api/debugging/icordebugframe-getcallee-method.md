---
description: '詳細情報: テキストフレーム:: GetCallee 先メソッド'
title: ICorDebugFrame::GetCallee メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
ms.openlocfilehash: 85b64933cb2f180445b88f7b19f8b78f1788252e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693071"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="14993-103">ICorDebugFrame::GetCallee メソッド</span><span class="sxs-lookup"><span data-stu-id="14993-103">ICorDebugFrame::GetCallee Method</span></span>

<span data-ttu-id="14993-104">このフレームが呼び出された現在のチェーン内のテキストボックスオブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="14993-104">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14993-105">構文</span><span class="sxs-lookup"><span data-stu-id="14993-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14993-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="14993-106">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="14993-107">入出力呼び出されたフレームを表すオブジェクトのアドレスへのポインター `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="14993-107">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="14993-108">呼び出し元のフレームが現在のチェーンの最も内側のフレームである場合、この値は null になります。</span><span class="sxs-lookup"><span data-stu-id="14993-108">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14993-109">要件</span><span class="sxs-lookup"><span data-stu-id="14993-109">Requirements</span></span>  

 <span data-ttu-id="14993-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14993-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14993-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14993-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14993-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14993-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14993-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14993-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
