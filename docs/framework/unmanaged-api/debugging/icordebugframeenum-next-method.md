---
description: '詳細については、次のメソッドを参照してください:: いいね。'
title: ICorDebugFrameEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
ms.openlocfilehash: 67b7dd0282c07358f942990f8915150d6449fd32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692668"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="318de-103">ICorDebugFrameEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="318de-103">ICorDebugFrameEnum::Next Method</span></span>

<span data-ttu-id="318de-104">現在の位置から開始して、指定された数の表示フレームインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="318de-104">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="318de-105">構文</span><span class="sxs-lookup"><span data-stu-id="318de-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="318de-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="318de-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="318de-107">から `ICorDebugFrame` 取得するインスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="318de-107">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="318de-108">入出力ポインターの配列。それぞれがオブジェクトを指し `ICorDebugFrame` ます。</span><span class="sxs-lookup"><span data-stu-id="318de-108">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="318de-109">入出力実際に返されたインスタンスの数へのポインター `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="318de-109">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="318de-110">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="318de-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="318de-111">要件</span><span class="sxs-lookup"><span data-stu-id="318de-111">Requirements</span></span>  

 <span data-ttu-id="318de-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="318de-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="318de-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="318de-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="318de-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="318de-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="318de-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="318de-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
