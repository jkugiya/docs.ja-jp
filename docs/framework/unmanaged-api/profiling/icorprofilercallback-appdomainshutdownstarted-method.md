---
description: '詳細について: ICorProfilerCallback:: AppDomainShutdownStarted メソッド'
title: ICorProfilerCallback::AppDomainShutdownStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
ms.openlocfilehash: 16545142a512ca1c5f4167f61b81ea949e3d14e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648117"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="ace73-103">ICorProfilerCallback::AppDomainShutdownStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="ace73-103">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>

<span data-ttu-id="ace73-104">アプリケーションドメインがプロセスからアンロードされていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="ace73-104">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ace73-105">構文</span><span class="sxs-lookup"><span data-stu-id="ace73-105">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ace73-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ace73-106">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="ace73-107">\[in] は、アプリケーションのアセンブリが格納されているドメインを識別します。</span><span class="sxs-lookup"><span data-stu-id="ace73-107">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

## <a name="remarks"></a><span data-ttu-id="ace73-108">解説</span><span class="sxs-lookup"><span data-stu-id="ace73-108">Remarks</span></span>  

 <span data-ttu-id="ace73-109">の値は、 `appDomainId` メソッドが返された後の情報要求に対して有効ではありません `AppDomainShutdownStarted` 。これは、このアプリケーションドメインに関する情報を取得する最後の機会です。</span><span class="sxs-lookup"><span data-stu-id="ace73-109">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ace73-110">要件</span><span class="sxs-lookup"><span data-stu-id="ace73-110">Requirements</span></span>  

 <span data-ttu-id="ace73-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ace73-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ace73-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ace73-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ace73-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ace73-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ace73-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ace73-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ace73-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ace73-115">See also</span></span>

- [<span data-ttu-id="ace73-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ace73-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
