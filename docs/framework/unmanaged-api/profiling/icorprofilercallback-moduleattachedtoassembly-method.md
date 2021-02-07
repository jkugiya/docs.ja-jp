---
description: '詳細について: ICorProfilerCallback:: ModuleAttachedToAssembly メソッド'
title: ICorProfilerCallback::ModuleAttachedToAssembly メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
ms.openlocfilehash: cc6a83188a8bdc4826232aa6ff6e416cbb8ae893
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705579"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="4102b-103">ICorProfilerCallback::ModuleAttachedToAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="4102b-103">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>

<span data-ttu-id="4102b-104">モジュールが親アセンブリにアタッチされていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="4102b-104">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4102b-105">構文</span><span class="sxs-lookup"><span data-stu-id="4102b-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4102b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4102b-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="4102b-107">からアタッチされているモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="4102b-107">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="4102b-108">からモジュールがアタッチされている親アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="4102b-108">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4102b-109">解説</span><span class="sxs-lookup"><span data-stu-id="4102b-109">Remarks</span></span>  

 <span data-ttu-id="4102b-110">モジュールは、インポートアドレステーブル (IAT)、の呼び出し、 `LoadLibrary` またはメタデータ参照を使用して読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="4102b-110">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="4102b-111">その結果、共通言語ランタイム (CLR) ローダーには、モジュールが存在するアセンブリを決定するための複数のコードパスがあります。</span><span class="sxs-lookup"><span data-stu-id="4102b-111">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="4102b-112">したがって、 [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) が呼び出された後、モジュールは、そのアセンブリを認識し、親アセンブリ ID を取得できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4102b-112">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="4102b-113">この `ModuleAttachedToAssembly` メソッドは、モジュールが親アセンブリにアタッチされ、その親アセンブリ ID を取得できる場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4102b-113">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4102b-114">要件</span><span class="sxs-lookup"><span data-stu-id="4102b-114">Requirements</span></span>  

 <span data-ttu-id="4102b-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4102b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4102b-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4102b-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4102b-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4102b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4102b-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4102b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4102b-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4102b-119">See also</span></span>

- [<span data-ttu-id="4102b-120">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4102b-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
