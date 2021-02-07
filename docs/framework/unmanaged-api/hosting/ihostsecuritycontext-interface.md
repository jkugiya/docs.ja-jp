---
description: 詳細については、「IHostSecurityContext インターフェイス」を参照してください。
title: IHostSecurityContext インターフェイス
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
ms.openlocfilehash: c4c1be00a8b1c9df58797a0f2fc7e60abcab9673
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671647"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="55ad3-103">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55ad3-103">IHostSecurityContext Interface</span></span>

<span data-ttu-id="55ad3-104">共通言語ランタイム (CLR) が、ホストによって実装されたセキュリティコンテキスト情報を維持できるようにします。</span><span class="sxs-lookup"><span data-stu-id="55ad3-104">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="55ad3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="55ad3-105">Methods</span></span>  
  
|<span data-ttu-id="55ad3-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="55ad3-106">Method</span></span>|<span data-ttu-id="55ad3-107">説明</span><span class="sxs-lookup"><span data-stu-id="55ad3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="55ad3-108">Capture メソッド</span><span class="sxs-lookup"><span data-stu-id="55ad3-108">Capture Method</span></span>](ihostsecuritycontext-capture-method.md)|<span data-ttu-id="55ad3-109">`IHostSecurityContext` [IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md)への呼び出しから返されたインスタンスの複製を取得します。</span><span class="sxs-lookup"><span data-stu-id="55ad3-109">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55ad3-110">解説</span><span class="sxs-lookup"><span data-stu-id="55ad3-110">Remarks</span></span>  

 <span data-ttu-id="55ad3-111">ホストは、CLR とユーザーコードの両方によって、スレッドトークンへのすべてのコードアクセスを制御できます。</span><span class="sxs-lookup"><span data-stu-id="55ad3-111">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="55ad3-112">また、完全なセキュリティコンテキスト情報が、制限されたコードアクセスで非同期操作またはコードポイント全体に渡されるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="55ad3-112">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="55ad3-113">`IHostSecurityContext` このセキュリティコンテキスト情報をカプセル化します。この情報は、ランタイムに対して非透過的です。</span><span class="sxs-lookup"><span data-stu-id="55ad3-113">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="55ad3-114">ランタイムはを使用してこの情報をキャプチャ `Capture` し、スレッドプールのワーカー項目のディスパッチ、ファイナライザーの実行、およびモジュールコンストラクターとクラスコンストラクター間で移動します。</span><span class="sxs-lookup"><span data-stu-id="55ad3-114">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55ad3-115">要件</span><span class="sxs-lookup"><span data-stu-id="55ad3-115">Requirements</span></span>  

 <span data-ttu-id="55ad3-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ad3-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55ad3-117">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="55ad3-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="55ad3-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="55ad3-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="55ad3-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55ad3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55ad3-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="55ad3-120">See also</span></span>

- [<span data-ttu-id="55ad3-121">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55ad3-121">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="55ad3-122">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55ad3-122">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="55ad3-123">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55ad3-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
