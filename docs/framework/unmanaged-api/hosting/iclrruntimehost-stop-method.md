---
description: '詳細について: ICLRRuntimeHost:: Stop メソッド'
title: ICLRRuntimeHost::Stop メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type:
- apiref
ms.openlocfilehash: 3e6b1cf2aee95af6354905f6dcdcb678ff785aa6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799729"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="a1112-103">ICLRRuntimeHost::Stop メソッド</span><span class="sxs-lookup"><span data-stu-id="a1112-103">ICLRRuntimeHost::Stop Method</span></span>

<span data-ttu-id="a1112-104">共通言語ランタイム (CLR) によるコードの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="a1112-104">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a1112-105">このメソッドは、ホストへのリソースの解放、アプリケーションドメインのアンロード、またはスレッドの破棄を行いません。</span><span class="sxs-lookup"><span data-stu-id="a1112-105">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="a1112-106">これらのリソースを解放するには、プロセスを終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1112-106">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1112-107">構文</span><span class="sxs-lookup"><span data-stu-id="a1112-107">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a1112-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="a1112-108">Return Value</span></span>  
  
|<span data-ttu-id="a1112-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1112-109">HRESULT</span></span>|<span data-ttu-id="a1112-110">説明</span><span class="sxs-lookup"><span data-stu-id="a1112-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1112-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1112-111">S_OK</span></span>|<span data-ttu-id="a1112-112">`Stop` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="a1112-112">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="a1112-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a1112-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a1112-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="a1112-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a1112-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a1112-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a1112-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="a1112-116">The call timed out.</span></span>|  
|<span data-ttu-id="a1112-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a1112-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a1112-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="a1112-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a1112-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a1112-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a1112-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="a1112-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a1112-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a1112-121">E_FAIL</span></span>|<span data-ttu-id="a1112-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a1112-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a1112-123">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="a1112-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a1112-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="a1112-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1112-125">要件</span><span class="sxs-lookup"><span data-stu-id="a1112-125">Requirements</span></span>  

 <span data-ttu-id="a1112-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1112-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1112-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a1112-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1112-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a1112-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1112-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1112-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1112-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1112-130">See also</span></span>

- [<span data-ttu-id="a1112-131">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1112-131">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
