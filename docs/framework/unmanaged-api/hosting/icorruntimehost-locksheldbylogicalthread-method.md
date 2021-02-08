---
description: '詳細について: ICorRuntimeHost:: LocksHeldByLogicalThread メソッド'
title: ICorRuntimeHost::LocksHeldByLogicalThread メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.LocksHeldByLogicalThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type:
- apiref
ms.openlocfilehash: bd64151bdc0c6aa0235192f0fc7f4badd8b0bbd6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789646"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="5bbe5-103">ICorRuntimeHost::LocksHeldByLogicalThread メソッド</span><span class="sxs-lookup"><span data-stu-id="5bbe5-103">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>

<span data-ttu-id="5bbe5-104">現在のスレッドが保持しているロックの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="5bbe5-104">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="5bbe5-105">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="5bbe5-105">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bbe5-106">構文</span><span class="sxs-lookup"><span data-stu-id="5bbe5-106">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bbe5-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5bbe5-107">Parameters</span></span>  

 `pCount`  
 <span data-ttu-id="5bbe5-108">入出力現在のスレッドが保持しているロックの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5bbe5-108">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bbe5-109">要件</span><span class="sxs-lookup"><span data-stu-id="5bbe5-109">Requirements</span></span>  

 <span data-ttu-id="5bbe5-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bbe5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bbe5-111">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5bbe5-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5bbe5-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="5bbe5-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5bbe5-113">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="5bbe5-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bbe5-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5bbe5-114">See also</span></span>

- [<span data-ttu-id="5bbe5-115">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5bbe5-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
