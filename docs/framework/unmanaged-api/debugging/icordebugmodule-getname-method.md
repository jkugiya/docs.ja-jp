---
description: '詳細情報: ヘルプモジュール:: GetName メソッド'
title: ICorDebugModule::GetName メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
ms.openlocfilehash: 0f81271b2be283621027f4c835b6f220a383d771
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660194"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="92bd7-103">ICorDebugModule::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="92bd7-103">ICorDebugModule::GetName Method</span></span>

<span data-ttu-id="92bd7-104">モジュールのファイル名を取得します。</span><span class="sxs-lookup"><span data-stu-id="92bd7-104">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92bd7-105">構文</span><span class="sxs-lookup"><span data-stu-id="92bd7-105">Syntax</span></span>  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92bd7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="92bd7-106">Parameters</span></span>  

 `cchname`  
 <span data-ttu-id="92bd7-107">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="92bd7-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="92bd7-108">から返された名前の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="92bd7-108">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="92bd7-109">入出力返された名前を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="92bd7-109">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92bd7-110">解説</span><span class="sxs-lookup"><span data-stu-id="92bd7-110">Remarks</span></span>  

 <span data-ttu-id="92bd7-111">`GetName`モジュールのファイル名がディスク上の名前と一致する場合、メソッドは S_OK HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="92bd7-111">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="92bd7-112">`GetName` 動的またはメモリ内モジュールの場合など、名前が使用されている場合は S_FALSE HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="92bd7-112">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92bd7-113">要件</span><span class="sxs-lookup"><span data-stu-id="92bd7-113">Requirements</span></span>  

 <span data-ttu-id="92bd7-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92bd7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92bd7-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92bd7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92bd7-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92bd7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92bd7-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92bd7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92bd7-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="92bd7-118">See also</span></span>
