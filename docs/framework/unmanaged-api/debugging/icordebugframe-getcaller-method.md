---
description: '詳細情報: テキストフレーム:: GetCaller メソッド'
title: ICorDebugFrame::GetCaller メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
ms.openlocfilehash: a042341f6edfa0e8f6ca00f758107852f9e381cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693045"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="4e094-103">ICorDebugFrame::GetCaller メソッド</span><span class="sxs-lookup"><span data-stu-id="4e094-103">ICorDebugFrame::GetCaller Method</span></span>

<span data-ttu-id="4e094-104">このフレームを呼び出した現在のチェーン内のテキストボックスオブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4e094-104">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e094-105">構文</span><span class="sxs-lookup"><span data-stu-id="4e094-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e094-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4e094-106">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="4e094-107">入出力呼び出し元のフレームを表すオブジェクトのアドレスへのポインター `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="4e094-107">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="4e094-108">呼び出されたフレームが現在のチェーンの最も外側のフレームである場合、この値は null になります。</span><span class="sxs-lookup"><span data-stu-id="4e094-108">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e094-109">要件</span><span class="sxs-lookup"><span data-stu-id="4e094-109">Requirements</span></span>  

 <span data-ttu-id="4e094-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e094-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e094-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e094-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e094-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e094-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e094-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e094-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
