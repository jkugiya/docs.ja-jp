---
description: '詳細について: ICorProfilerInfo:: GetInprocInspectionIThisThread メソッド'
title: ICorProfilerInfo::GetInprocInspectionIThisThread メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
ms.openlocfilehash: 07ff904170750976e54e623101a2552db0c7f290
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647246"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="67fa3-103">ICorProfilerInfo::GetInprocInspectionIThisThread メソッド</span><span class="sxs-lookup"><span data-stu-id="67fa3-103">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>

<span data-ttu-id="67fa3-104">のオブジェクトインターフェイスに対してクエリを実行できるオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="67fa3-104">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="67fa3-105">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="67fa3-105">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67fa3-106">構文</span><span class="sxs-lookup"><span data-stu-id="67fa3-106">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67fa3-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="67fa3-107">Parameters</span></span>  

 `ppicd`  
 <span data-ttu-id="67fa3-108">インターフェイスに対してクエリを実行できる[out](/cpp/atl/iunknown)オブジェクト `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="67fa3-108">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67fa3-109">解説</span><span class="sxs-lookup"><span data-stu-id="67fa3-109">Remarks</span></span>  

 <span data-ttu-id="67fa3-110">共通言語ランタイム (CLR) のデバッグサービスでは、.NET Framework バージョン1.0 でサポートされているプロセス内デバッグが制限されています。</span><span class="sxs-lookup"><span data-stu-id="67fa3-110">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="67fa3-111">インプロセスデバッグでは、デバッグ API の検査部分を使用するプロファイラーが有効になりました。</span><span class="sxs-lookup"><span data-stu-id="67fa3-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="67fa3-112">お客様からのフィードバックの結果として、プロセス内デバッグはバージョン2.0 の .NET Framework から削除され、プロファイル API により多くの機能を備えた一連の機能に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="67fa3-112">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67fa3-113">要件</span><span class="sxs-lookup"><span data-stu-id="67fa3-113">Requirements</span></span>  

 <span data-ttu-id="67fa3-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67fa3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67fa3-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="67fa3-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="67fa3-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67fa3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67fa3-117">**.NET Framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="67fa3-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67fa3-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="67fa3-118">See also</span></span>

- [<span data-ttu-id="67fa3-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="67fa3-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
