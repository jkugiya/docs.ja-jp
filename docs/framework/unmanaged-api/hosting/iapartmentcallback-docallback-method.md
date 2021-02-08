---
description: '詳細について: IApartmentCallback::D oCallback メソッド'
title: IApartmentCallback::DoCallback メソッド
ms.date: 03/30/2017
api_name:
- IApartmentCallback.DoCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- DoCallback
helpviewer_keywords:
- IApartmentCallback::DoCallback method [.NET Framework hosting]
- DoCallback method [.NET Framework hosting]
ms.assetid: 8edad30c-30ff-4bee-813c-75525a82fc93
topic_type:
- apiref
ms.openlocfilehash: 65b7f496f953f08e099bf13ef8212c7d6e1026ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785106"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="6bd6b-103">IApartmentCallback::DoCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="6bd6b-103">IApartmentCallback::DoCallback Method</span></span>

<span data-ttu-id="6bd6b-104">アパートメント内で指定された関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="6bd6b-104">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bd6b-105">構文</span><span class="sxs-lookup"><span data-stu-id="6bd6b-105">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bd6b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6bd6b-106">Parameters</span></span>  

 `pFunc`  
 <span data-ttu-id="6bd6b-107">からアパートメント内で実行される関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6bd6b-107">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="6bd6b-108">から関数の引数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6bd6b-108">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bd6b-109">要件</span><span class="sxs-lookup"><span data-stu-id="6bd6b-109">Requirements</span></span>  

 <span data-ttu-id="6bd6b-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bd6b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bd6b-111">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6bd6b-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6bd6b-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6bd6b-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6bd6b-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bd6b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd6b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6bd6b-114">See also</span></span>

- [<span data-ttu-id="6bd6b-115">IApartmentCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6bd6b-115">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)
