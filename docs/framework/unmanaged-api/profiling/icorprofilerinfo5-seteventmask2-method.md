---
description: '詳細について: ICorProfilerInfo5:: SetEventMask2 メソッド'
title: ICorProfilerInfo5::SetEventMask2 メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
ms.openlocfilehash: 2928ec408f2fdeb363164530258a3bf5c9719e2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799006"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="b7016-103">ICorProfilerInfo5::SetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="b7016-103">ICorProfilerInfo5::SetEventMask2 Method</span></span>

<span data-ttu-id="b7016-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="b7016-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b7016-105">プロファイラーが共通言語ランタイム (CLR) からイベント通知を受け取ることを希望するイベントの型を指定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="b7016-105">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="b7016-106">[ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)メソッドよりも多くの機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="b7016-106">It provides more functionality than the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7016-107">構文</span><span class="sxs-lookup"><span data-stu-id="b7016-107">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7016-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b7016-108">Parameters</span></span>  

 `dwEventsLow`  
 <span data-ttu-id="b7016-109">[in] イベントのカテゴリを指定する 4 バイトの値。</span><span class="sxs-lookup"><span data-stu-id="b7016-109">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="b7016-110">各ビットは、異なる性能、動作、またはイベントの型を制御します。</span><span class="sxs-lookup"><span data-stu-id="b7016-110">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="b7016-111">ビットは、 [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) 列挙体に記述されています。</span><span class="sxs-lookup"><span data-stu-id="b7016-111">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="b7016-112">[in] イベントのカテゴリを指定する 4 バイトの値。</span><span class="sxs-lookup"><span data-stu-id="b7016-112">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="b7016-113">各ビットは、異なる性能、動作、またはイベントの型を制御します。</span><span class="sxs-lookup"><span data-stu-id="b7016-113">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="b7016-114">ビットは、 [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) 列挙体に記述されています。</span><span class="sxs-lookup"><span data-stu-id="b7016-114">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7016-115">解説</span><span class="sxs-lookup"><span data-stu-id="b7016-115">Remarks</span></span>  

 <span data-ttu-id="b7016-116">`SetEventMask2` メソッドは、プロファイラーが登録するコールバックを設定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="b7016-116">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="b7016-117">通常は、 [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) メソッドを呼び出して、どのビットが設定されているかを判断し、その値と値および設定する新しいビットの論理 OR を実行 `pdwEventsLow` `pdwEventsHigh` してから、メソッドを呼び出し `SetEventMask2` ます。</span><span class="sxs-lookup"><span data-stu-id="b7016-117">Typically, you call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="b7016-118">このメソッドは、 [Seteventmask](icorprofilerinfo-seteventmask-method.md) メソッドの代替手段として推奨されます。</span><span class="sxs-lookup"><span data-stu-id="b7016-118">This method is the recommended alternative to the [SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7016-119">要件</span><span class="sxs-lookup"><span data-stu-id="b7016-119">Requirements</span></span>  

 <span data-ttu-id="b7016-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7016-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7016-121">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b7016-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b7016-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7016-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7016-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7016-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7016-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7016-124">See also</span></span>

- [<span data-ttu-id="b7016-125">ICorProfilerInfo5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7016-125">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="b7016-126">GetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="b7016-126">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)
