---
description: '詳細について: ICorProfilerInfo:: EndInprocDebugging メソッド'
title: ICorProfilerInfo::EndInprocDebugging メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
ms.openlocfilehash: 5e172abaa99e0a64031a9c1ec1beac5f23386d1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788619"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="d6928-103">ICorProfilerInfo::EndInprocDebugging メソッド</span><span class="sxs-lookup"><span data-stu-id="d6928-103">ICorProfilerInfo::EndInprocDebugging Method</span></span>

<span data-ttu-id="d6928-104">インプロセスデバッグセッションをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="d6928-104">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="d6928-105">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="d6928-105">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6928-106">構文</span><span class="sxs-lookup"><span data-stu-id="d6928-106">Syntax</span></span>  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6928-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d6928-107">Parameters</span></span>  

 `dwProfilerContext`  
 <span data-ttu-id="d6928-108">からデバッグセッションを識別する値。</span><span class="sxs-lookup"><span data-stu-id="d6928-108">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="d6928-109">この値は、 [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) メソッドで受け取った値と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6928-109">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6928-110">解説</span><span class="sxs-lookup"><span data-stu-id="d6928-110">Remarks</span></span>  

 <span data-ttu-id="d6928-111">同じコールバックメソッド内で [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) およびを呼び出す必要があり `EndInprocDebugging` ます。</span><span class="sxs-lookup"><span data-stu-id="d6928-111">You must call [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="d6928-112">CLR デバッグサービスでは、.NET Framework バージョン1.0 および1.1 でサポートされているプロセス内デバッグが制限されています。</span><span class="sxs-lookup"><span data-stu-id="d6928-112">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="d6928-113">インプロセスデバッグでは、デバッグ API の検査部分を使用するプロファイラーが有効になりました。</span><span class="sxs-lookup"><span data-stu-id="d6928-113">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="d6928-114">ただし、お客様からのフィードバックにより、プロセス内デバッグはバージョン2.0 の .NET Framework から削除され、プロファイル API により多くの機能を備えた一連の機能に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="d6928-114">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6928-115">要件</span><span class="sxs-lookup"><span data-stu-id="d6928-115">Requirements</span></span>  

 <span data-ttu-id="d6928-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6928-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6928-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d6928-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d6928-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6928-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6928-119">**.NET Framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="d6928-119">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6928-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6928-120">See also</span></span>

- [<span data-ttu-id="d6928-121">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6928-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
