---
description: '詳細情報: Igチョーク Stcontrol:: RequestVirtualMemLimit メソッド'
title: IGCHostControl::RequestVirtualMemLimit メソッド
ms.date: 03/30/2017
api_name:
- IGCHostControl.RequestVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type:
- apiref
ms.openlocfilehash: b0ee22671b63be0ed0d23ebb103a6a5a7ca9f2b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709400"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="c5c68-103">IGCHostControl::RequestVirtualMemLimit メソッド</span><span class="sxs-lookup"><span data-stu-id="c5c68-103">IGCHostControl::RequestVirtualMemLimit Method</span></span>

<span data-ttu-id="c5c68-104">仮想メモリの制限を変更するようにホストに要求します。</span><span class="sxs-lookup"><span data-stu-id="c5c68-104">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5c68-105">構文</span><span class="sxs-lookup"><span data-stu-id="c5c68-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5c68-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c5c68-106">Parameters</span></span>  

 `sztMaxVirtualMemMB`  
 <span data-ttu-id="c5c68-107">から割り当てられるメモリの要求サイズ。</span><span class="sxs-lookup"><span data-stu-id="c5c68-107">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="c5c68-108">[入力、出力]割り当てられたメモリの実際のサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c5c68-108">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5c68-109">要件</span><span class="sxs-lookup"><span data-stu-id="c5c68-109">Requirements</span></span>  

 <span data-ttu-id="c5c68-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5c68-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5c68-111">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c5c68-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5c68-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c5c68-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5c68-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5c68-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c68-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5c68-114">See also</span></span>

- [<span data-ttu-id="c5c68-115">IGCHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c5c68-115">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)
