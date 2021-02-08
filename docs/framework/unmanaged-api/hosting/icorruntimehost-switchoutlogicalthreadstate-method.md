---
description: '詳細について: ICorRuntimeHost:: SwitchOutLogicalThreadState メソッド'
title: ICorRuntimeHost::SwitchOutLogicalThreadState メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchOutLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState method [.NET Framework hosting]
- SwitchOutLogicalThreadState method [.NET Framework hosting]
ms.assetid: e1968f0b-2675-4dc2-8507-46164e1df154
topic_type:
- apiref
ms.openlocfilehash: b4190ebe6b2c260f85afd8dd17127d0c63dca6c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799448"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="cf84d-103">ICorRuntimeHost::SwitchOutLogicalThreadState メソッド</span><span class="sxs-lookup"><span data-stu-id="cf84d-103">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>

<span data-ttu-id="cf84d-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="cf84d-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf84d-105">構文</span><span class="sxs-lookup"><span data-stu-id="cf84d-105">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf84d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cf84d-106">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="cf84d-107">入出力スイッチアウトされるファイバーを示すクッキー。</span><span class="sxs-lookup"><span data-stu-id="cf84d-107">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf84d-108">要件</span><span class="sxs-lookup"><span data-stu-id="cf84d-108">Requirements</span></span>  

 <span data-ttu-id="cf84d-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf84d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf84d-110">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="cf84d-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf84d-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="cf84d-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf84d-112">**.NET Framework バージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="cf84d-112">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf84d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf84d-113">See also</span></span>

- [<span data-ttu-id="cf84d-114">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf84d-114">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
