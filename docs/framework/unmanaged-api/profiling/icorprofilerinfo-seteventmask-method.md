---
description: '詳細について: ICorProfilerInfo:: SetEventMask メソッド'
title: ICorProfilerInfo::SetEventMask メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type:
- apiref
ms.openlocfilehash: e389d25abfecfc9a5dec8834e412fe618324e311
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687195"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="2c4eb-103">ICorProfilerInfo::SetEventMask メソッド</span><span class="sxs-lookup"><span data-stu-id="2c4eb-103">ICorProfilerInfo::SetEventMask Method</span></span>

<span data-ttu-id="2c4eb-104">共通言語ランタイム (CLR) からの通知を受け取るプロファイラーに対するイベントの種類を指定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="2c4eb-104">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c4eb-105">構文</span><span class="sxs-lookup"><span data-stu-id="2c4eb-105">Syntax</span></span>  
  
```cpp  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c4eb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2c4eb-106">Parameters</span></span>  

 `dwEvents`  
 <span data-ttu-id="2c4eb-107">[in] イベントのカテゴリを指定する 4 バイトの値。</span><span class="sxs-lookup"><span data-stu-id="2c4eb-107">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="2c4eb-108">各ビットは、異なる性能、動作、またはイベントの型を制御します。</span><span class="sxs-lookup"><span data-stu-id="2c4eb-108">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="2c4eb-109">ビットは、 [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) 列挙体に記述されています。</span><span class="sxs-lookup"><span data-stu-id="2c4eb-109">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c4eb-110">解説</span><span class="sxs-lookup"><span data-stu-id="2c4eb-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c4eb-111">このメソッドではなく、 [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c4eb-111">You should call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="2c4eb-112">メソッドは `SetEventMask` 引き続きサポートされますが、 [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) には追加機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="2c4eb-112">Although the `SetEventMask` method continues to be supported, [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c4eb-113">要件</span><span class="sxs-lookup"><span data-stu-id="2c4eb-113">Requirements</span></span>  

 <span data-ttu-id="2c4eb-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c4eb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c4eb-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2c4eb-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c4eb-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c4eb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c4eb-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c4eb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c4eb-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c4eb-118">See also</span></span>

- [<span data-ttu-id="2c4eb-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c4eb-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="2c4eb-120">SetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="2c4eb-120">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
