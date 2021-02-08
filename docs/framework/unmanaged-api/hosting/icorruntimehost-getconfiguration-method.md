---
description: '詳細について: ICorRuntimeHost:: GetConfiguration メソッド'
title: ICorRuntimeHost::GetConfiguration メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
ms.openlocfilehash: d3e3f065c3957fb29daa11ed7c46858a53865c91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784835"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="30821-103">ICorRuntimeHost::GetConfiguration メソッド</span><span class="sxs-lookup"><span data-stu-id="30821-103">ICorRuntimeHost::GetConfiguration Method</span></span>

<span data-ttu-id="30821-104">ホストが共通言語ランタイム (CLR) のコールバック構成を指定できるようにするオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="30821-104">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30821-105">構文</span><span class="sxs-lookup"><span data-stu-id="30821-105">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30821-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="30821-106">Parameters</span></span>  

 `pConfiguration`  
 <span data-ttu-id="30821-107">入出力CLR の構成に使用できる [ICorConfiguration](icorconfiguration-interface.md) オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="30821-107">[out] A pointer to the address of an [ICorConfiguration](icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30821-108">解説</span><span class="sxs-lookup"><span data-stu-id="30821-108">Remarks</span></span>  

 <span data-ttu-id="30821-109">CLR は、初期化の前に構成する必要があります。それ以外の場合、 `GetConfiguration` メソッドはエラーを示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="30821-109">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30821-110">要件</span><span class="sxs-lookup"><span data-stu-id="30821-110">Requirements</span></span>  

 <span data-ttu-id="30821-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30821-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30821-112">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="30821-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30821-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="30821-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30821-114">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="30821-114">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30821-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="30821-115">See also</span></span>

- [<span data-ttu-id="30821-116">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="30821-116">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
