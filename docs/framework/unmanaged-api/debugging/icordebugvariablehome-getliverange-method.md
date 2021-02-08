---
description: '詳細については、次のページを参照してください: GetLiveRange メソッド'
title: 'いい変数 Home:: GetLiveRange メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLiveRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLiveRange
helpviewer_keywords:
- ICorDebugVariableHome::GetLiveRange method [.NET Framework debugging]
- GetLiveRange method, ICorDebugVariableFrame interface [.NET Framework debugging]
ms.assetid: 87277e1a-1595-4729-9e25-d1c3ac18ce5f
topic_type:
- apiref
ms.openlocfilehash: daa53a164c7660826d44285ce21ecea1b649a727
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800839"
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="ad2cf-103">いい変数 Home:: GetLiveRange メソッド</span><span class="sxs-lookup"><span data-stu-id="ad2cf-103">IcorDebugVariableHome::GetLiveRange Method</span></span>

<span data-ttu-id="ad2cf-104">この変数がライブであるネイティブ範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="ad2cf-104">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad2cf-105">構文</span><span class="sxs-lookup"><span data-stu-id="ad2cf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad2cf-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad2cf-106">Parameters</span></span>  

 `pStartOffset`  
 <span data-ttu-id="ad2cf-107">入出力変数が最初にライブになる論理オフセット。</span><span class="sxs-lookup"><span data-stu-id="ad2cf-107">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="ad2cf-108">入出力変数が最後にライブになる位置の直後の論理オフセット。</span><span class="sxs-lookup"><span data-stu-id="ad2cf-108">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad2cf-109">要件</span><span class="sxs-lookup"><span data-stu-id="ad2cf-109">Requirements</span></span>  

 <span data-ttu-id="ad2cf-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad2cf-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad2cf-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad2cf-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad2cf-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad2cf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad2cf-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad2cf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad2cf-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad2cf-114">See also</span></span>

- [<span data-ttu-id="ad2cf-115">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad2cf-115">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
