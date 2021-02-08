---
description: '詳細については、次のメソッドを参照してください: いいね。'
title: ICorDebugAssemblyEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum::Next method
helpviewer_keywords:
- ICorDebugAssemblyEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: b3e7d0c2-3baa-4ef8-8e3f-b865cf252940
topic_type:
- apiref
ms.openlocfilehash: feb77f22ec59fcc0e1b3f5590b7aee4efba13d01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772225"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="9d322-103">ICorDebugAssemblyEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="9d322-103">ICorDebugAssemblyEnum::Next Method</span></span>

<span data-ttu-id="9d322-104">現在のカーソル位置から開始して、指定した数のアセンブリをコレクションから取得します。</span><span class="sxs-lookup"><span data-stu-id="9d322-104">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d322-105">構文</span><span class="sxs-lookup"><span data-stu-id="9d322-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d322-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9d322-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="9d322-107">から取得するアセンブリの数。</span><span class="sxs-lookup"><span data-stu-id="9d322-107">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="9d322-108">入出力ポインターの配列。各ポインターは、アセンブリを表す、オブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="9d322-108">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9d322-109">入出力実際に返されたアセンブリの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9d322-109">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="9d322-110">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="9d322-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d322-111">要件</span><span class="sxs-lookup"><span data-stu-id="9d322-111">Requirements</span></span>  

 <span data-ttu-id="9d322-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d322-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d322-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d322-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d322-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d322-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d322-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d322-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
