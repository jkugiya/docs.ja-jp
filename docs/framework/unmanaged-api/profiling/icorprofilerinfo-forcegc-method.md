---
description: '詳細について: ICorProfilerInfo:: ForceGC メソッド'
title: ICorProfilerInfo::ForceGC メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
ms.openlocfilehash: 1abed09450b72730a11a168223b6da05e9baf9be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737533"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="ee41a-103">ICorProfilerInfo::ForceGC メソッド</span><span class="sxs-lookup"><span data-stu-id="ee41a-103">ICorProfilerInfo::ForceGC Method</span></span>

<span data-ttu-id="ee41a-104">共通言語ランタイム (CLR) 内で強制的にガベージコレクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="ee41a-104">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee41a-105">構文</span><span class="sxs-lookup"><span data-stu-id="ee41a-105">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ee41a-106">解説</span><span class="sxs-lookup"><span data-stu-id="ee41a-106">Remarks</span></span>  

 <span data-ttu-id="ee41a-107">メソッドを呼び出す必要があるのは、 `ForceGC` マネージコードを実行しておらず、そのスタックにプロファイラーコールバックがないスレッドだけです。</span><span class="sxs-lookup"><span data-stu-id="ee41a-107">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="ee41a-108">最も便利な実装は、 `ForceGC` シグナル状態になったときにを呼び出す、プロファイラー内に個別のスレッドを作成することです。</span><span class="sxs-lookup"><span data-stu-id="ee41a-108">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee41a-109">要件</span><span class="sxs-lookup"><span data-stu-id="ee41a-109">Requirements</span></span>  

 <span data-ttu-id="ee41a-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee41a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee41a-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ee41a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ee41a-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee41a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee41a-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee41a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee41a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee41a-114">See also</span></span>

- [<span data-ttu-id="ee41a-115">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee41a-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
