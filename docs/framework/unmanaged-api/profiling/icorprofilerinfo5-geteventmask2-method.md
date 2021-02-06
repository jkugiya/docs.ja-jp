---
description: '詳細について: ICorProfilerInfo5:: GetEventMask2 メソッド'
title: ICorProfilerInfo5::GetEventMask2 メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
ms.openlocfilehash: c6652ffe1b8fd0d99ce5493c8ba27a971363c423
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646661"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="2eef6-103">ICorProfilerInfo5::GetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="2eef6-103">ICorProfilerInfo5::GetEventMask2 Method</span></span>

<span data-ttu-id="2eef6-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="2eef6-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="2eef6-105">現在のイベント カテゴリを取得します。プロファイラーは、これに関する通知を共通言語ランタイム (CLR) から受け取ります。</span><span class="sxs-lookup"><span data-stu-id="2eef6-105">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="2eef6-106">[ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md)メソッドで提供されていない機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="2eef6-106">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eef6-107">構文</span><span class="sxs-lookup"><span data-stu-id="2eef6-107">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2eef6-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2eef6-108">Parameters</span></span>  

 `pdwEventsLow`  
 <span data-ttu-id="2eef6-109">[out] イベントのカテゴリを指定する 4 バイト値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="2eef6-109">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="2eef6-110">各ビットは、異なる性能、動作、またはイベントの型を制御します。</span><span class="sxs-lookup"><span data-stu-id="2eef6-110">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="2eef6-111">ビットは、 [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) 列挙体に記述されています。</span><span class="sxs-lookup"><span data-stu-id="2eef6-111">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="2eef6-112">[out] イベントのカテゴリを指定する 4 バイト値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="2eef6-112">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="2eef6-113">各ビットは、異なる性能、動作、またはイベントの型を制御します。</span><span class="sxs-lookup"><span data-stu-id="2eef6-113">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="2eef6-114">ビットは、 [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) 列挙体に記述されています。</span><span class="sxs-lookup"><span data-stu-id="2eef6-114">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2eef6-115">解説</span><span class="sxs-lookup"><span data-stu-id="2eef6-115">Remarks</span></span>  

 <span data-ttu-id="2eef6-116">`GetEventMask2` メソッドは、プロファイラーがサブスクライブしたコールバックを判断するのに使用します。</span><span class="sxs-lookup"><span data-stu-id="2eef6-116">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="2eef6-117">通常は、値と値、および設定する新しいビットの論理 OR を実行 `pdwEventsLow` `pdwEventsHigh` し、次に [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2eef6-117">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="2eef6-118">このメソッドは、 [Geteventmask](icorprofilerinfo-geteventmask-method.md) メソッドの代替手段として推奨されます。</span><span class="sxs-lookup"><span data-stu-id="2eef6-118">This method is the recommended alternative to the [GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2eef6-119">要件</span><span class="sxs-lookup"><span data-stu-id="2eef6-119">Requirements</span></span>  

 <span data-ttu-id="2eef6-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2eef6-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2eef6-121">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2eef6-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2eef6-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2eef6-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2eef6-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2eef6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eef6-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="2eef6-124">See also</span></span>

- [<span data-ttu-id="2eef6-125">ICorProfilerInfo5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2eef6-125">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="2eef6-126">SetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="2eef6-126">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
