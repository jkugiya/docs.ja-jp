---
description: '詳細について: ICorDebugArrayValue:: HasBaseIndicies メソッド'
title: ICorDebugArrayValue::HasBaseIndicies メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.HasBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type:
- apiref
ms.openlocfilehash: b251653004801ff2d312dfb34749c413774ddf40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722959"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="7d25e-103">ICorDebugArrayValue::HasBaseIndicies メソッド</span><span class="sxs-lookup"><span data-stu-id="7d25e-103">ICorDebugArrayValue::HasBaseIndicies Method</span></span>

<span data-ttu-id="7d25e-104">この配列のどの次元にも0以外のベースインデックスがあるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="7d25e-104">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d25e-105">構文</span><span class="sxs-lookup"><span data-stu-id="7d25e-105">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d25e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7d25e-106">Parameters</span></span>  

 `pbHasBaseIndicies`  
 <span data-ttu-id="7d25e-107">入出力 `true` このオブジェクトの1つ以上の次元に0以外のベースインデックスがある場合は、ブール値へのポインター。それ以外の場合は、 `ICorDebugArrayValue` ブール値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="7d25e-107">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d25e-108">要件</span><span class="sxs-lookup"><span data-stu-id="7d25e-108">Requirements</span></span>  

 <span data-ttu-id="7d25e-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d25e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d25e-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d25e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d25e-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d25e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d25e-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d25e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
