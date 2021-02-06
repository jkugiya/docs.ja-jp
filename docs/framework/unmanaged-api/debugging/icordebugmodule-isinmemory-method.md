---
description: '詳細については、「IsInMemory Module:: メソッド」を参照してください。'
title: ICorDebugModule::IsInMemory メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
ms.openlocfilehash: 41454ede15e1d45775af8fb0ab7a6b571d9c0e41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660090"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="2d80c-103">ICorDebugModule::IsInMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="2d80c-103">ICorDebugModule::IsInMemory Method</span></span>

<span data-ttu-id="2d80c-104">このモジュールがメモリ内にのみ存在するかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="2d80c-104">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d80c-105">構文</span><span class="sxs-lookup"><span data-stu-id="2d80c-105">Syntax</span></span>  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d80c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2d80c-106">Parameters</span></span>  

 `pInMemory`  
 <span data-ttu-id="2d80c-107">[出力] `true` このモジュールがメモリ内にのみ存在する場合は、それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="2d80c-107">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d80c-108">解説</span><span class="sxs-lookup"><span data-stu-id="2d80c-108">Remarks</span></span>  

 <span data-ttu-id="2d80c-109">共通言語ランタイム (CLR) では、未加工のバイトストリームからのモジュールの読み込みがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2d80c-109">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="2d80c-110">このようなモジュールは *メモリ内モジュール* と呼ばれ、ディスク上には存在しません。</span><span class="sxs-lookup"><span data-stu-id="2d80c-110">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d80c-111">要件</span><span class="sxs-lookup"><span data-stu-id="2d80c-111">Requirements</span></span>  

 <span data-ttu-id="2d80c-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d80c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d80c-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d80c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d80c-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d80c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d80c-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d80c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d80c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d80c-116">See also</span></span>
