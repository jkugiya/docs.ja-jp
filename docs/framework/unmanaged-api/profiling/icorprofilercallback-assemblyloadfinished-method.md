---
description: '詳細について: ICorProfilerCallback:: AssemblyLoadFinished メソッド'
title: ICorProfilerCallback::AssemblyLoadFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: 19c0871808455e64ad8a4eb002806a87030f7882
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648039"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="bfa18-103">ICorProfilerCallback::AssemblyLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="bfa18-103">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>

<span data-ttu-id="bfa18-104">アセンブリの読み込みが完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="bfa18-104">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfa18-105">構文</span><span class="sxs-lookup"><span data-stu-id="bfa18-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfa18-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bfa18-106">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="bfa18-107">\[in] は、読み込まれたアセンブリを識別します。</span><span class="sxs-lookup"><span data-stu-id="bfa18-107">\[in] Identifies the assembly that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="bfa18-108">\[in] アセンブリの読み込みが正常に完了したかどうかを示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="bfa18-108">\[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="bfa18-109">解説</span><span class="sxs-lookup"><span data-stu-id="bfa18-109">Remarks</span></span>  

 <span data-ttu-id="bfa18-110">の値 `assemblyId` は、 `AssemblyLoadFinished` メソッドが呼び出されるまで、情報要求に対して有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="bfa18-110">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="bfa18-111">アセンブリの読み込みの一部は、コールバック後も続行される場合があり `AssemblyLoadFinished` ます。</span><span class="sxs-lookup"><span data-stu-id="bfa18-111">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="bfa18-112">のエラー HRESULT は `hrStatus` エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="bfa18-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="bfa18-113">ただし、の成功 HRESULT は、 `hrStatus` アセンブリの読み込みの最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="bfa18-113">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfa18-114">要件</span><span class="sxs-lookup"><span data-stu-id="bfa18-114">Requirements</span></span>  

 <span data-ttu-id="bfa18-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfa18-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfa18-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bfa18-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bfa18-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfa18-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfa18-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfa18-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfa18-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="bfa18-119">See also</span></span>

- [<span data-ttu-id="bfa18-120">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfa18-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
