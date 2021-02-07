---
description: '詳細については、次を参照してください: いいね:: GetStackRange メソッド'
title: ICorDebugChain::GetStackRange メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
ms.openlocfilehash: 066dda06564655350d799dabb54acd622b828172
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694931"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="ce81c-103">ICorDebugChain::GetStackRange メソッド</span><span class="sxs-lookup"><span data-stu-id="ce81c-103">ICorDebugChain::GetStackRange Method</span></span>

<span data-ttu-id="ce81c-104">このチェーンのスタックセグメントのアドレス範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="ce81c-104">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce81c-105">構文</span><span class="sxs-lookup"><span data-stu-id="ce81c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce81c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ce81c-106">Parameters</span></span>  

 `pStart`  
 <span data-ttu-id="ce81c-107">入出力 `CORDB_ADDRESS` スタックセグメントの開始アドレスを示す値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ce81c-107">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="ce81c-108">入出力 `CORDB_ADDRESS` スタックセグメントの終了アドレスを示す値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ce81c-108">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce81c-109">解説</span><span class="sxs-lookup"><span data-stu-id="ce81c-109">Remarks</span></span>  

 <span data-ttu-id="ce81c-110">数値の範囲は、スタックフレームの位置を比較する場合にのみ意味があります。</span><span class="sxs-lookup"><span data-stu-id="ce81c-110">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="ce81c-111">実際にスタックに格納されている内容について、想定を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="ce81c-111">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce81c-112">要件</span><span class="sxs-lookup"><span data-stu-id="ce81c-112">Requirements</span></span>  

 <span data-ttu-id="ce81c-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce81c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce81c-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce81c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce81c-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce81c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce81c-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce81c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
