---
description: '詳細について: ICLRRuntimeHost:: Start メソッド'
title: ICLRRuntimeHost::Start メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Start
helpviewer_keywords:
- ICLRRuntimeHost::Start method [.NET Framework hosting]
- Start method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: c0a6dce5-0a8d-42e8-808b-6ca14df9d289
topic_type:
- apiref
ms.openlocfilehash: 0ada729c9a90b23fb1573a2101845028e5e2fe76
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785082"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="d70e4-103">ICLRRuntimeHost::Start メソッド</span><span class="sxs-lookup"><span data-stu-id="d70e4-103">ICLRRuntimeHost::Start Method</span></span>

<span data-ttu-id="d70e4-104">共通言語ランタイム (CLR) をプロセスに初期化します。</span><span class="sxs-lookup"><span data-stu-id="d70e4-104">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d70e4-105">構文</span><span class="sxs-lookup"><span data-stu-id="d70e4-105">Syntax</span></span>  
  
```cpp  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d70e4-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="d70e4-106">Return Value</span></span>  
  
|<span data-ttu-id="d70e4-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d70e4-107">HRESULT</span></span>|<span data-ttu-id="d70e4-108">説明</span><span class="sxs-lookup"><span data-stu-id="d70e4-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d70e4-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="d70e4-109">S_OK</span></span>|<span data-ttu-id="d70e4-110">`Start` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="d70e4-110">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="d70e4-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d70e4-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d70e4-112">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="d70e4-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d70e4-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d70e4-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d70e4-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="d70e4-114">The call timed out.</span></span>|  
|<span data-ttu-id="d70e4-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d70e4-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d70e4-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="d70e4-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d70e4-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d70e4-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d70e4-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="d70e4-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d70e4-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d70e4-119">E_FAIL</span></span>|<span data-ttu-id="d70e4-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d70e4-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d70e4-121">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d70e4-121">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d70e4-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="d70e4-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d70e4-123">解説</span><span class="sxs-lookup"><span data-stu-id="d70e4-123">Remarks</span></span>  

 <span data-ttu-id="d70e4-124">多くのシナリオでは、を呼び出す必要はありません。これは `Start` 、マネージコードを実行する最初の要求時にランタイムが自動的に初期化するためです。</span><span class="sxs-lookup"><span data-stu-id="d70e4-124">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="d70e4-125">ただし、を使用し `Start` て、ランタイムをいつ初期化するかを正確に指定できます。</span><span class="sxs-lookup"><span data-stu-id="d70e4-125">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d70e4-126">要件</span><span class="sxs-lookup"><span data-stu-id="d70e4-126">Requirements</span></span>  

 <span data-ttu-id="d70e4-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d70e4-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d70e4-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d70e4-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d70e4-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d70e4-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d70e4-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d70e4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d70e4-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="d70e4-131">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="d70e4-132">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d70e4-132">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
