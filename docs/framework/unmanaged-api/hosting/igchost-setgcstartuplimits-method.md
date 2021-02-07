---
description: '詳細について: IGCHost:: SetGCStartupLimits メソッド'
title: IGCHost::SetGCStartupLimits メソッド
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
ms.openlocfilehash: 91c74d54189bbfb7e9f208e507fe6e75b7023e00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709491"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="1382c-103">IGCHost::SetGCStartupLimits メソッド</span><span class="sxs-lookup"><span data-stu-id="1382c-103">IGCHost::SetGCStartupLimits Method</span></span>

<span data-ttu-id="1382c-104">ジェネレーション0のセグメントサイズと最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="1382c-104">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1382c-105">.NET Framework 4.5 以降では、 `DWORD` [IGCHost2:: SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) メソッドを使用して、セグメントサイズと最大ジェネレーション0のサイズをより大きい値に設定できます。</span><span class="sxs-lookup"><span data-stu-id="1382c-105">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1382c-106">構文</span><span class="sxs-lookup"><span data-stu-id="1382c-106">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1382c-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1382c-107">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="1382c-108">からガベージコレクションシステムによって使用されるセグメントのサイズ。</span><span class="sxs-lookup"><span data-stu-id="1382c-108">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="1382c-109">からジェネレーション0の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="1382c-109">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1382c-110">解説</span><span class="sxs-lookup"><span data-stu-id="1382c-110">Remarks</span></span>  

 <span data-ttu-id="1382c-111">`SetGCStartupLimits`メソッドを呼び出すことができるのは1回だけです。</span><span class="sxs-lookup"><span data-stu-id="1382c-111">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="1382c-112">これらの値は後で変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="1382c-112">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1382c-113">要件</span><span class="sxs-lookup"><span data-stu-id="1382c-113">Requirements</span></span>  

 <span data-ttu-id="1382c-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1382c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1382c-115">**ヘッダー:** GCHost、GCHost</span><span class="sxs-lookup"><span data-stu-id="1382c-115">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="1382c-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1382c-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1382c-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1382c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1382c-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="1382c-118">See also</span></span>

- [<span data-ttu-id="1382c-119">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1382c-119">IGCHost Interface</span></span>](igchost-interface.md)
