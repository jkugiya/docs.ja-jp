---
description: '詳細情報: IObjectHandle:: ラップ解除メソッド'
title: IObjectHandle::Unwrap メソッド
ms.date: 03/30/2017
api_name:
- IObjectHandle.Unwrap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Unwrap
helpviewer_keywords:
- Unwrap method [.NET Framework hosting]
- IObjectHandle::Unwrap method [.NET Framework hosting]
ms.assetid: 794c6f8e-ed58-416b-b756-e864f2c958f7
topic_type:
- apiref
ms.openlocfilehash: 3f791eaf52abd045d495fe15e868423e464fd27e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728328"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="41b97-103">IObjectHandle::Unwrap メソッド</span><span class="sxs-lookup"><span data-stu-id="41b97-103">IObjectHandle::Unwrap Method</span></span>

<span data-ttu-id="41b97-104">間接参照から値渡しのマーシャリングオブジェクトをラップ解除します。</span><span class="sxs-lookup"><span data-stu-id="41b97-104">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41b97-105">構文</span><span class="sxs-lookup"><span data-stu-id="41b97-105">Syntax</span></span>  
  
```cpp  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41b97-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="41b97-106">Parameters</span></span>  

 `ppv`  
 <span data-ttu-id="41b97-107">入出力ラップを解除するオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="41b97-107">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41b97-108">要件</span><span class="sxs-lookup"><span data-stu-id="41b97-108">Requirements</span></span>  

 <span data-ttu-id="41b97-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41b97-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41b97-110">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="41b97-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41b97-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="41b97-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41b97-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41b97-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
