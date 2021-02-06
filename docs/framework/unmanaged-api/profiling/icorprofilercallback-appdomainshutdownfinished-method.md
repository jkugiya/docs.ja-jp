---
description: '詳細について: ICorProfilerCallback:: AppDomainShutdownFinished メソッド'
title: ICorProfilerCallback::AppDomainShutdownFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
ms.openlocfilehash: e08a4f7e03bfd18d9c6a2fdf56bfab8c68f9c379
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648224"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="9c29f-103">ICorProfilerCallback::AppDomainShutdownFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="9c29f-103">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>

<span data-ttu-id="9c29f-104">アプリケーションドメインがプロセスからアンロードされたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="9c29f-104">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c29f-105">構文</span><span class="sxs-lookup"><span data-stu-id="9c29f-105">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c29f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9c29f-106">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="9c29f-107">\[in] は、アプリケーションのアセンブリが格納されているドメインを識別します。</span><span class="sxs-lookup"><span data-stu-id="9c29f-107">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

- `hrStatus`

  <span data-ttu-id="9c29f-108">\[in] アプリケーションドメインが正常にアンロードされたかどうかを示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="9c29f-108">\[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="9c29f-109">解説</span><span class="sxs-lookup"><span data-stu-id="9c29f-109">Remarks</span></span>  

 <span data-ttu-id="9c29f-110">`appDomainId` [ICorProfilerCallback:: AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md)メソッドがを返すと、の値は情報要求に対して有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="9c29f-110">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="9c29f-111">アプリケーションドメインのアンロードの一部は、コールバック後に続行される場合があり `AppDomainCreationFinished` ます。</span><span class="sxs-lookup"><span data-stu-id="9c29f-111">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="9c29f-112">のエラー HRESULT は `hrStatus` エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="9c29f-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="9c29f-113">ただし、の成功 HRESULT は、 `hrStatus` アプリケーションドメインのアンロードの最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="9c29f-113">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c29f-114">要件</span><span class="sxs-lookup"><span data-stu-id="9c29f-114">Requirements</span></span>  

 <span data-ttu-id="9c29f-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c29f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c29f-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9c29f-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9c29f-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c29f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c29f-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c29f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c29f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c29f-119">See also</span></span>

- [<span data-ttu-id="9c29f-120">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9c29f-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
