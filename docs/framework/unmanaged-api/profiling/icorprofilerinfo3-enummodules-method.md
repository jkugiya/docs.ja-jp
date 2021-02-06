---
description: '詳細情報: ICorProfilerInfo3:: EnumModules メソッド'
title: ICorProfilerInfo3::EnumModules メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumModules Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type:
- apiref
ms.openlocfilehash: 9cdb76b77f78fa68eafa111e60b31b738173d658
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646856"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="1e5a9-103">ICorProfilerInfo3::EnumModules メソッド</span><span class="sxs-lookup"><span data-stu-id="1e5a9-103">ICorProfilerInfo3::EnumModules Method</span></span>

<span data-ttu-id="1e5a9-104">アプリケーションに読み込まれるマネージド モジュールのコレクションを順番に反復処理するメソッドを提供する列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="1e5a9-104">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e5a9-105">構文</span><span class="sxs-lookup"><span data-stu-id="1e5a9-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e5a9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e5a9-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="1e5a9-107">入出力 [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e5a9-107">[out] A pointer to an [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e5a9-108">解説</span><span class="sxs-lookup"><span data-stu-id="1e5a9-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e5a9-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="1e5a9-109">Requirements</span></span>  

 <span data-ttu-id="1e5a9-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e5a9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e5a9-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1e5a9-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1e5a9-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e5a9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e5a9-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e5a9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e5a9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e5a9-114">See also</span></span>

- [<span data-ttu-id="1e5a9-115">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e5a9-115">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="1e5a9-116">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e5a9-116">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="1e5a9-117">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e5a9-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="1e5a9-118">プロファイル</span><span class="sxs-lookup"><span data-stu-id="1e5a9-118">Profiling</span></span>](index.md)
