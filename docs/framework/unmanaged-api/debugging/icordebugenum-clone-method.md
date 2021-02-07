---
description: '詳細情報: ICorDebugEnum:: Clone メソッド'
title: ICorDebugEnum::Clone メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Clone
helpviewer_keywords:
- Clone method, ICorDebugEnum interface [.NET Framework debugging]
- ICorDebugEnum::Clone method [.NET Framework debugging]
ms.assetid: 57eefaf3-75cf-4496-bc94-88c0706861b7
topic_type:
- apiref
ms.openlocfilehash: 18219757980870dcf9663477d195068a76814de1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694564"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="82720-103">ICorDebugEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="82720-103">ICorDebugEnum::Clone Method</span></span>

<span data-ttu-id="82720-104">この ICorDebugEnum オブジェクトのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="82720-104">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82720-105">構文</span><span class="sxs-lookup"><span data-stu-id="82720-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82720-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="82720-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="82720-107">入出力 `ICorDebugEnum` このオブジェクトのコピーであるオブジェクトのアドレスへのポインター `ICorDebugEnum` 。</span><span class="sxs-lookup"><span data-stu-id="82720-107">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82720-108">要件</span><span class="sxs-lookup"><span data-stu-id="82720-108">Requirements</span></span>  

 <span data-ttu-id="82720-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82720-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82720-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82720-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82720-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82720-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82720-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82720-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
