---
description: 詳細については、「IGCHost2 インターフェイス」を参照してください。
title: IGCHost2 インターフェイス
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
ms.openlocfilehash: e32a4894fcff3600c9385f0f559443e23b2bc307
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709322"
---
# <a name="igchost2-interface"></a><span data-ttu-id="0259d-103">IGCHost2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0259d-103">IGCHost2 Interface</span></span>

<span data-ttu-id="0259d-104">ガベージコレクションシステムに関する情報を取得し、ガベージコレクションのいくつかの側面を制御するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="0259d-104">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0259d-105">新しい開発では、代わりに [ICLRGCManager2](iclrgcmanager2-interface.md) インターフェイスを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0259d-105">For new development, we recommend that you use the [ICLRGCManager2](iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0259d-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="0259d-106">Methods</span></span>  
  
|<span data-ttu-id="0259d-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="0259d-107">Method</span></span>|<span data-ttu-id="0259d-108">説明</span><span class="sxs-lookup"><span data-stu-id="0259d-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0259d-109">SetGCStartupLimitsEx メソッド</span><span class="sxs-lookup"><span data-stu-id="0259d-109">SetGCStartupLimitsEx Method</span></span>](igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="0259d-110">ジェネレーション0のセグメントサイズと最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="0259d-110">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="0259d-111">より大きいジェネレーション0およびセグメントサイズを有効に `DWORD` します。</span><span class="sxs-lookup"><span data-stu-id="0259d-111">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0259d-112">要件</span><span class="sxs-lookup"><span data-stu-id="0259d-112">Requirements</span></span>  

 <span data-ttu-id="0259d-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0259d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0259d-114">**ヘッダー:** GCHost、GCHost</span><span class="sxs-lookup"><span data-stu-id="0259d-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="0259d-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0259d-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0259d-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0259d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0259d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0259d-117">See also</span></span>

- [<span data-ttu-id="0259d-118">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0259d-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="0259d-119">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0259d-119">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="0259d-120">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="0259d-120">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
