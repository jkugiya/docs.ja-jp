---
description: '詳細について: ICorRuntimeHost:: SwitchInLogicalThreadState メソッド'
title: ICorRuntimeHost::SwitchInLogicalThreadState メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchInLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type:
- apiref
ms.openlocfilehash: 3e375379cc5d6af7c3a8fb8d64a40a389e0f9dcc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789568"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="ff8bb-103">ICorRuntimeHost::SwitchInLogicalThreadState メソッド</span><span class="sxs-lookup"><span data-stu-id="ff8bb-103">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>

<span data-ttu-id="ff8bb-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="ff8bb-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff8bb-105">構文</span><span class="sxs-lookup"><span data-stu-id="ff8bb-105">Syntax</span></span>  
  
```cpp  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff8bb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff8bb-106">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="ff8bb-107">から使用するファイバーを示すクッキー。</span><span class="sxs-lookup"><span data-stu-id="ff8bb-107">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff8bb-108">要件</span><span class="sxs-lookup"><span data-stu-id="ff8bb-108">Requirements</span></span>  

 <span data-ttu-id="ff8bb-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff8bb-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff8bb-110">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ff8bb-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff8bb-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ff8bb-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff8bb-112">**.NET Framework バージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="ff8bb-112">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff8bb-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff8bb-113">See also</span></span>

- [<span data-ttu-id="ff8bb-114">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ff8bb-114">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
