---
description: '詳細について: ICorProfilerCallback:: AppDomainCreationFinished メソッド'
title: ICorProfilerCallback::AppDomainCreationFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
ms.openlocfilehash: 6995c6cda168b5be5815e6f7b2b4d900ae0d4d67
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648364"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="01e05-103">ICorProfilerCallback::AppDomainCreationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="01e05-103">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>

<span data-ttu-id="01e05-104">アプリケーションドメインが作成されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="01e05-104">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01e05-105">構文</span><span class="sxs-lookup"><span data-stu-id="01e05-105">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="01e05-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="01e05-106">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="01e05-107">\[in] は、作成されたドメインを識別します。</span><span class="sxs-lookup"><span data-stu-id="01e05-107">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="01e05-108">\[in] アプリケーションドメインの作成が正常に完了したかどうかを示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="01e05-108">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="01e05-109">解説</span><span class="sxs-lookup"><span data-stu-id="01e05-109">Remarks</span></span>  

 <span data-ttu-id="01e05-110">アプリケーション ID は、メソッドが呼び出されるまで、情報要求に対して有効ではありません `AppDomainCreationFinished` 。</span><span class="sxs-lookup"><span data-stu-id="01e05-110">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="01e05-111">アプリケーションドメインの読み込みの一部は、コールバック後も続行される場合があり `AppDomainCreationFinished` ます。</span><span class="sxs-lookup"><span data-stu-id="01e05-111">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="01e05-112">のエラー HRESULT は `hrStatus` エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="01e05-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="01e05-113">ただし、の成功 HRESULT は、 `hrStatus` アプリケーションドメインの作成の最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="01e05-113">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01e05-114">要件</span><span class="sxs-lookup"><span data-stu-id="01e05-114">Requirements</span></span>  

 <span data-ttu-id="01e05-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01e05-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01e05-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="01e05-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01e05-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01e05-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01e05-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01e05-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e05-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="01e05-119">See also</span></span>

- [<span data-ttu-id="01e05-120">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01e05-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
