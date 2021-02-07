---
description: '詳細について: ICLRRuntimeHost:: GetCLRControl メソッド'
title: ICLRRuntimeHost::GetCLRControl メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type:
- apiref
ms.openlocfilehash: 832ae03c0126f0c08afa9b5c0312a636ec1de294
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753940"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="3f5a7-103">ICLRRuntimeHost::GetCLRControl メソッド</span><span class="sxs-lookup"><span data-stu-id="3f5a7-103">ICLRRuntimeHost::GetCLRControl Method</span></span>

<span data-ttu-id="3f5a7-104">ホストが共通言語ランタイム (CLR) の側面をカスタマイズするために使用できる [ICLRControl interface](iclrcontrol-interface.md) 型のインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="3f5a7-104">Gets an interface pointer of type [ICLRControl Interface](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f5a7-105">構文</span><span class="sxs-lookup"><span data-stu-id="3f5a7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f5a7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3f5a7-106">Parameters</span></span>  

 `pCLRControl`  
 <span data-ttu-id="3f5a7-107">入出力ホストが CLR の追加の側面を構成できるようにする [ICLRControl interface](iclrcontrol-interface.md) 型のインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="3f5a7-107">[out] An interface pointer of type [ICLRControl Interface](iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f5a7-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="3f5a7-108">Return Value</span></span>  
  
|<span data-ttu-id="3f5a7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3f5a7-109">HRESULT</span></span>|<span data-ttu-id="3f5a7-110">説明</span><span class="sxs-lookup"><span data-stu-id="3f5a7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f5a7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3f5a7-111">S_OK</span></span>|<span data-ttu-id="3f5a7-112">`GetCLRControl` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="3f5a7-112">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="3f5a7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3f5a7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3f5a7-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="3f5a7-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3f5a7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3f5a7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3f5a7-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="3f5a7-116">The call timed out.</span></span>|  
|<span data-ttu-id="3f5a7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3f5a7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3f5a7-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="3f5a7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3f5a7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3f5a7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3f5a7-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="3f5a7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3f5a7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3f5a7-121">E_FAIL</span></span>|<span data-ttu-id="3f5a7-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3f5a7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3f5a7-123">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="3f5a7-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3f5a7-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="3f5a7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3f5a7-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="3f5a7-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="3f5a7-126">CLR は既に開始されています。</span><span class="sxs-lookup"><span data-stu-id="3f5a7-126">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f5a7-127">解説</span><span class="sxs-lookup"><span data-stu-id="3f5a7-127">Remarks</span></span>  

 <span data-ttu-id="3f5a7-128">`ICLRControl`[Getclrmanager メソッド](iclrcontrol-getclrmanager-method.md)を提供します。このメソッドを使用すると、ホストは、マネージャーの型のいずれかへのインターフェイスポインターを取得できます。</span><span class="sxs-lookup"><span data-stu-id="3f5a7-128">`ICLRControl` provides the [GetCLRManager Method](iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f5a7-129">要件</span><span class="sxs-lookup"><span data-stu-id="3f5a7-129">Requirements</span></span>  

 <span data-ttu-id="3f5a7-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f5a7-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f5a7-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3f5a7-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3f5a7-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3f5a7-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f5a7-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f5a7-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f5a7-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f5a7-134">See also</span></span>

- [<span data-ttu-id="3f5a7-135">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f5a7-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="3f5a7-136">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f5a7-136">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
