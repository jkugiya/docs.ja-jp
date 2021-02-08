---
description: '詳細について: ICorProfilerCallback2:: ThreadNameChanged メソッド'
title: ICorProfilerCallback2::ThreadNameChanged メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.ThreadNameChanged
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::ThreadNameChanged
helpviewer_keywords:
- ThreadNameChanged method [.NET Framework profiling]
- ICorProfilerCallback2::ThreadNameChanged method [.NET Framework profiling]
ms.assetid: c8bbd76d-a9ff-44f2-87a6-be052819da36
topic_type:
- apiref
ms.openlocfilehash: 161247f9692d1307d063e244b200eb0d8f739e9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799045"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="7205e-103">ICorProfilerCallback2::ThreadNameChanged メソッド</span><span class="sxs-lookup"><span data-stu-id="7205e-103">ICorProfilerCallback2::ThreadNameChanged Method</span></span>

<span data-ttu-id="7205e-104">スレッドの名前が変更されたことをコードプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="7205e-104">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7205e-105">構文</span><span class="sxs-lookup"><span data-stu-id="7205e-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7205e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7205e-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="7205e-107">からスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="7205e-107">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="7205e-108">からスレッドの新しい名前の長さ。</span><span class="sxs-lookup"><span data-stu-id="7205e-108">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="7205e-109">からスレッドの新しい名前。</span><span class="sxs-lookup"><span data-stu-id="7205e-109">[in] The new name of the thread.</span></span> <span data-ttu-id="7205e-110">名前が null で終了していません。</span><span class="sxs-lookup"><span data-stu-id="7205e-110">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7205e-111">要件</span><span class="sxs-lookup"><span data-stu-id="7205e-111">Requirements</span></span>  

 <span data-ttu-id="7205e-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7205e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7205e-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7205e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7205e-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7205e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7205e-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7205e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7205e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="7205e-116">See also</span></span>

- [<span data-ttu-id="7205e-117">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7205e-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="7205e-118">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7205e-118">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
