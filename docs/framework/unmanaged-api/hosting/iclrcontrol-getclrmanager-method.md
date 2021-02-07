---
description: '詳細について: ICLRControl:: GetCLRManager メソッド'
title: ICLRControl::GetCLRManager メソッド
ms.date: 03/30/2017
api_name:
- ICLRControl.GetCLRManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type:
- apiref
ms.openlocfilehash: fc24cbdfd4bebfff5c2f8d73a9cd6961a8c94e94
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716719"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="d9f70-103">ICLRControl::GetCLRManager メソッド</span><span class="sxs-lookup"><span data-stu-id="d9f70-103">ICLRControl::GetCLRManager Method</span></span>

<span data-ttu-id="d9f70-104">ホストが共通言語ランタイム (CLR) を構成するために使用できる任意のマネージャー型のインスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d9f70-104">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9f70-105">構文</span><span class="sxs-lookup"><span data-stu-id="d9f70-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9f70-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d9f70-106">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="d9f70-107">から `IID` 返されるマネージャーの型の。</span><span class="sxs-lookup"><span data-stu-id="d9f70-107">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="d9f70-108">次の `IID` 値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d9f70-108">The following `IID` values are supported.</span></span>  
  
- <span data-ttu-id="d9f70-109">IID_ICLRDebugManager: が ICLRDebugManager 型であることを指定し `ppObject` ます。 [](iclrdebugmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d9f70-109">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](iclrdebugmanager-interface.md).</span></span>  
  
- <span data-ttu-id="d9f70-110">IID_ICLRErrorReportingManager: が ICLRErrorReportingManager 型であることを指定し `ppObject` ます。 [](iclrerrorreportingmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d9f70-110">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md).</span></span>  
  
- <span data-ttu-id="d9f70-111">IID_ICLRGCManager: が ICLRGCManager 型であることを指定し `ppObject` ます。 [](iclrgcmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d9f70-111">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](iclrgcmanager-interface.md).</span></span>  
  
- <span data-ttu-id="d9f70-112">IID_ICLRHostProtectionManager: が ICLRHostProtectionManager 型であることを指定し `ppObject` ます。 [](iclrhostprotectionmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d9f70-112">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md).</span></span>  
  
- <span data-ttu-id="d9f70-113">IID_ICLROnEventManager: が ICLROnEventManager 型であることを指定し `ppObject` ます。 [](iclroneventmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d9f70-113">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](iclroneventmanager-interface.md).</span></span>  
  
- <span data-ttu-id="d9f70-114">IID_ICLRPolicyManager: が ICLRPolicyManager 型であることを指定し `ppObject` ます。 [](iclrpolicymanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d9f70-114">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>  
  
- <span data-ttu-id="d9f70-115">IID_ICLRTaskManager: が ICLRTaskManager 型であることを指定し `ppObject` ます。 [](iclrtaskmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d9f70-115">IID_ICLRTaskManager: Specifies that `ppObject` will be of type [ICLRTaskManager](iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="d9f70-116">入出力要求されたマネージャーへのインターフェイスポインター。無効なマネージャーの種類が要求された場合は null。</span><span class="sxs-lookup"><span data-stu-id="d9f70-116">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9f70-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="d9f70-117">Return Value</span></span>  
  
|<span data-ttu-id="d9f70-118">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9f70-118">HRESULT</span></span>|<span data-ttu-id="d9f70-119">説明</span><span class="sxs-lookup"><span data-stu-id="d9f70-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9f70-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9f70-120">S_OK</span></span>|<span data-ttu-id="d9f70-121">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="d9f70-121">The method returned successfully.</span></span>|  
|<span data-ttu-id="d9f70-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d9f70-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d9f70-123">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="d9f70-123">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d9f70-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d9f70-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d9f70-125">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="d9f70-125">The call timed out.</span></span>|  
|<span data-ttu-id="d9f70-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d9f70-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d9f70-127">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="d9f70-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d9f70-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d9f70-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d9f70-129">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="d9f70-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d9f70-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d9f70-130">E_FAIL</span></span>|<span data-ttu-id="d9f70-131">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d9f70-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d9f70-132">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d9f70-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d9f70-133">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="d9f70-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d9f70-134">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="d9f70-134">E_NOINTERFACE</span></span>|<span data-ttu-id="d9f70-135">インターフェイス型はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d9f70-135">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9f70-136">要件</span><span class="sxs-lookup"><span data-stu-id="d9f70-136">Requirements</span></span>  

 <span data-ttu-id="d9f70-137">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9f70-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9f70-138">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d9f70-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9f70-139">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d9f70-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9f70-140">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9f70-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9f70-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9f70-141">See also</span></span>

- [<span data-ttu-id="d9f70-142">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d9f70-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="d9f70-143">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d9f70-143">IHostControl Interface</span></span>](ihostcontrol-interface.md)
