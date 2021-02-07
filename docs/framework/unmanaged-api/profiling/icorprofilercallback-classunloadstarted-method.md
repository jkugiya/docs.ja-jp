---
description: '詳細について: ICorProfilerCallback:: ClassUnloadStarted メソッド'
title: ICorProfilerCallback::ClassUnloadStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
ms.openlocfilehash: 3dae88d9cbe9ed2a2e234d02420a65c6a9ca003d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706371"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="1d0ec-103">ICorProfilerCallback::ClassUnloadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="1d0ec-103">ICorProfilerCallback::ClassUnloadStarted Method</span></span>

<span data-ttu-id="1d0ec-104">クラスがアンロードされていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="1d0ec-104">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d0ec-105">構文</span><span class="sxs-lookup"><span data-stu-id="1d0ec-105">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d0ec-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1d0ec-106">Parameters</span></span>

- `classId`

  <span data-ttu-id="1d0ec-107">\[in] は、アンロードするクラスを識別します。</span><span class="sxs-lookup"><span data-stu-id="1d0ec-107">\[in] Identifies the class that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="1d0ec-108">解説</span><span class="sxs-lookup"><span data-stu-id="1d0ec-108">Remarks</span></span>  

 <span data-ttu-id="1d0ec-109">`classId`メソッドから制御が戻った後、の値は情報要求に対して無効です `ClassUnloadStarted` 。このクラスに関する情報を取得するのは、プロファイラーの最後の機会です。</span><span class="sxs-lookup"><span data-stu-id="1d0ec-109">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d0ec-110">要件</span><span class="sxs-lookup"><span data-stu-id="1d0ec-110">Requirements</span></span>  

 <span data-ttu-id="1d0ec-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d0ec-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d0ec-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1d0ec-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1d0ec-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d0ec-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d0ec-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d0ec-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d0ec-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d0ec-115">See also</span></span>

- [<span data-ttu-id="1d0ec-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d0ec-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1d0ec-117">ClassUnloadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="1d0ec-117">ClassUnloadFinished Method</span></span>](icorprofilercallback-classunloadfinished-method.md)
