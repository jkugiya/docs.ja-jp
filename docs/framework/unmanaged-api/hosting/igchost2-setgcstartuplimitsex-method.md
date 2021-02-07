---
description: '詳細について: IGCHost2:: SetGCStartupLimitsEx メソッド'
title: IGCHost2::SetGCStartupLimitsEx メソッド
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
ms.openlocfilehash: 32d3bcbb467a1a418c7123779c881c46e983edef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709309"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="e294b-103">IGCHost2::SetGCStartupLimitsEx メソッド</span><span class="sxs-lookup"><span data-stu-id="e294b-103">IGCHost2::SetGCStartupLimitsEx Method</span></span>

<span data-ttu-id="e294b-104">ジェネレーション0のセグメントサイズと最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="e294b-104">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e294b-105">構文</span><span class="sxs-lookup"><span data-stu-id="e294b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e294b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e294b-106">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="e294b-107">からガベージコレクションシステムによって使用されるセグメントのサイズ。</span><span class="sxs-lookup"><span data-stu-id="e294b-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="e294b-108">からジェネレーション0の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="e294b-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e294b-109">解説</span><span class="sxs-lookup"><span data-stu-id="e294b-109">Remarks</span></span>  

 <span data-ttu-id="e294b-110">を設定する値は、 `SetGCStartupLimitsEx` ホストを開始する前にのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="e294b-110">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="e294b-111">これらの値は後で変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="e294b-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e294b-112">要件</span><span class="sxs-lookup"><span data-stu-id="e294b-112">Requirements</span></span>  

 <span data-ttu-id="e294b-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e294b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e294b-114">**ヘッダー:** GCHost、GCHost</span><span class="sxs-lookup"><span data-stu-id="e294b-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="e294b-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e294b-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e294b-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e294b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e294b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e294b-117">See also</span></span>

- [<span data-ttu-id="e294b-118">IGCHost2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e294b-118">IGCHost2 Interface</span></span>](igchost2-interface.md)
