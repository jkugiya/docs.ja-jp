---
description: '詳細について: ICLRMetaHost:: RequestRuntimeLoadedNotification メソッド'
title: ICLRMetaHost::RequestRuntimeLoadedNotification メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
ms.openlocfilehash: c385d2d845642605ad47944794f6274e8d472071
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637496"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="634d3-103">ICLRMetaHost::RequestRuntimeLoadedNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="634d3-103">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>

<span data-ttu-id="634d3-104">共通言語ランタイム (CLR) のバージョンが最初に読み込まれたが、まだ開始されていないときに呼び出されることが保証されているコールバック関数を提供します。</span><span class="sxs-lookup"><span data-stu-id="634d3-104">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="634d3-105">このメソッドは、 [Lockclrversion](lockclrversion-function.md) 関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="634d3-105">This method supersedes the [LockClrVersion](lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="634d3-106">構文</span><span class="sxs-lookup"><span data-stu-id="634d3-106">Syntax</span></span>  
  
```cpp  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="634d3-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="634d3-107">Parameters</span></span>  

 `pCallbackFunction`  
 <span data-ttu-id="634d3-108">から新しいランタイムが読み込まれたときに呼び出されるコールバック関数。</span><span class="sxs-lookup"><span data-stu-id="634d3-108">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="634d3-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="634d3-109">Return Value</span></span>  

 <span data-ttu-id="634d3-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="634d3-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="634d3-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="634d3-111">HRESULT</span></span>|<span data-ttu-id="634d3-112">説明</span><span class="sxs-lookup"><span data-stu-id="634d3-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="634d3-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="634d3-113">S_OK</span></span>|<span data-ttu-id="634d3-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="634d3-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="634d3-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="634d3-115">E_POINTER</span></span>|<span data-ttu-id="634d3-116">`pCallbackFunction` が null です。</span><span class="sxs-lookup"><span data-stu-id="634d3-116">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="634d3-117">解説</span><span class="sxs-lookup"><span data-stu-id="634d3-117">Remarks</span></span>  

 <span data-ttu-id="634d3-118">コールバックは、次のように機能します。</span><span class="sxs-lookup"><span data-stu-id="634d3-118">The callback works in the following way:</span></span>  
  
- <span data-ttu-id="634d3-119">コールバックは、ランタイムが初めて読み込まれるときにのみ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="634d3-119">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
- <span data-ttu-id="634d3-120">同じランタイムの再入可能な読み込みに対してコールバックが呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="634d3-120">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
- <span data-ttu-id="634d3-121">再入可能でないランタイムの読み込みでは、コールバック関数の呼び出しがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="634d3-121">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="634d3-122">コールバック関数のプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="634d3-122">The callback function has the following prototype:</span></span>  
  
```cpp  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="634d3-123">コールバック関数のプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="634d3-123">The callback function prototypes are as follows:</span></span>  
  
- <span data-ttu-id="634d3-124">`pfnCallbackThreadSet`:</span><span class="sxs-lookup"><span data-stu-id="634d3-124">`pfnCallbackThreadSet`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- <span data-ttu-id="634d3-125">`pfnCallbackThreadUnset`:</span><span class="sxs-lookup"><span data-stu-id="634d3-125">`pfnCallbackThreadUnset`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="634d3-126">ホストの読み込みまたは再入によって別のランタイムの読み込みが発生する場合は、 `pfnCallbackThreadSet` `pfnCallbackThreadUnset` コールバック関数で指定されたパラメーターとパラメーターを次のように使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="634d3-126">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
- <span data-ttu-id="634d3-127">`pfnCallbackThreadSet` このような読み込みが試行される前に、ランタイムの読み込みを発生させる可能性のあるスレッドによって呼び出される必要があります。</span><span class="sxs-lookup"><span data-stu-id="634d3-127">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
- <span data-ttu-id="634d3-128">`pfnCallbackThreadUnset` は、スレッドがこのようなランタイム読み込みを行わなくなる場合 (および最初のコールバックから戻る前) に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="634d3-128">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
- <span data-ttu-id="634d3-129">`pfnCallbackThreadSet` と `pfnCallbackThreadUnset` はどちらも再入不可能です。</span><span class="sxs-lookup"><span data-stu-id="634d3-129">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="634d3-130">ホストアプリケーションは、 `pfnCallbackThreadSet` `pfnCallbackThreadUnset` パラメーターのスコープ外でおよびを呼び出すことはできません `pCallbackFunction` 。</span><span class="sxs-lookup"><span data-stu-id="634d3-130">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="634d3-131">要件</span><span class="sxs-lookup"><span data-stu-id="634d3-131">Requirements</span></span>  

 <span data-ttu-id="634d3-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="634d3-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="634d3-133">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="634d3-133">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="634d3-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="634d3-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="634d3-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="634d3-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="634d3-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="634d3-136">See also</span></span>

- [<span data-ttu-id="634d3-137">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="634d3-137">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="634d3-138">ホスティング</span><span class="sxs-lookup"><span data-stu-id="634d3-138">Hosting</span></span>](index.md)
