---
description: '詳細について: ICorProfilerCallback:: AssemblyUnloadFinished メソッド'
title: ICorProfilerCallback::AssemblyUnloadFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
ms.openlocfilehash: 30d6bd805a1466d6a65728b22f677ba00e09ffb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648026"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="fe853-103">ICorProfilerCallback::AssemblyUnloadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="fe853-103">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>

<span data-ttu-id="fe853-104">アセンブリがアンロードされたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="fe853-104">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe853-105">構文</span><span class="sxs-lookup"><span data-stu-id="fe853-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe853-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fe853-106">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="fe853-107">\[in] は、アンロードされるアセンブリを識別します。</span><span class="sxs-lookup"><span data-stu-id="fe853-107">\[in] Identifies the assembly that is being unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="fe853-108">\[in] アセンブリが正常にアンロードされたかどうかを示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="fe853-108">\[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe853-109">解説</span><span class="sxs-lookup"><span data-stu-id="fe853-109">Remarks</span></span>  

 <span data-ttu-id="fe853-110">`assemblyId` [ICorProfilerCallback:: AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md)メソッドがを返すと、の値は情報要求に対して有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="fe853-110">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="fe853-111">アセンブリのアンロードの一部は、コールバック後に続行される場合があり `AssemblyUnloadFinished` ます。</span><span class="sxs-lookup"><span data-stu-id="fe853-111">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="fe853-112">のエラー HRESULT は `hrStatus` エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="fe853-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="fe853-113">ただし、の成功 HRESULT は、 `hrStatus` アセンブリのアンロードの最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="fe853-113">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe853-114">要件</span><span class="sxs-lookup"><span data-stu-id="fe853-114">Requirements</span></span>  

 <span data-ttu-id="fe853-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe853-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe853-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fe853-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe853-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe853-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe853-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe853-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe853-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe853-119">See also</span></span>

- [<span data-ttu-id="fe853-120">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe853-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
