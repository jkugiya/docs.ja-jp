---
description: '詳細について: ICorProfilerInfo:: BeginInprocDebugging メソッド'
title: ICorProfilerInfo::BeginInprocDebugging メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
ms.openlocfilehash: 151aa3604d61e4c5d9e7e24fe9f17bf754d72233
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737403"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="182fe-103">ICorProfilerInfo::BeginInprocDebugging メソッド</span><span class="sxs-lookup"><span data-stu-id="182fe-103">ICorProfilerInfo::BeginInprocDebugging Method</span></span>

<span data-ttu-id="182fe-104">インプロセスデバッグサポートを初期化します。</span><span class="sxs-lookup"><span data-stu-id="182fe-104">Initializes in-process debugging support.</span></span> <span data-ttu-id="182fe-105">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="182fe-105">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="182fe-106">構文</span><span class="sxs-lookup"><span data-stu-id="182fe-106">Syntax</span></span>  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="182fe-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="182fe-107">Parameters</span></span>  

 `fThisThreadOnly`  
 <span data-ttu-id="182fe-108">から現在のスレッドのみのデバッグサポートを初期化するには、この値をに設定し `true` ます。 `false` すべてのスレッドのデバッグサポートを初期化するには、をに設定します。</span><span class="sxs-lookup"><span data-stu-id="182fe-108">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="182fe-109">入出力デバッグセッションを識別する戻り値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="182fe-109">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="182fe-110">解説</span><span class="sxs-lookup"><span data-stu-id="182fe-110">Remarks</span></span>  

 <span data-ttu-id="182fe-111">CLR デバッグサービスでは、.NET Framework バージョン1.0 および1.1 でサポートされているプロセス内デバッグが制限されています。</span><span class="sxs-lookup"><span data-stu-id="182fe-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="182fe-112">インプロセスデバッグでは、デバッグ API の検査部分を使用するプロファイラーが有効になりました。</span><span class="sxs-lookup"><span data-stu-id="182fe-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="182fe-113">ただし、お客様からのフィードバックにより、プロセス内デバッグはバージョン2.0 の .NET Framework から削除され、プロファイル API により多くの機能を備えた一連の機能に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="182fe-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="182fe-114">要件</span><span class="sxs-lookup"><span data-stu-id="182fe-114">Requirements</span></span>  

 <span data-ttu-id="182fe-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="182fe-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="182fe-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="182fe-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="182fe-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="182fe-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="182fe-118">**.NET Framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="182fe-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="182fe-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="182fe-119">See also</span></span>

- [<span data-ttu-id="182fe-120">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="182fe-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
