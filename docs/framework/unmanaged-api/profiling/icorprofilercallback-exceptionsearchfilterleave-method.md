---
description: '詳細について: ICorProfilerCallback:: ExceptionSearchFilterLeave メソッド'
title: ICorProfilerCallback::ExceptionSearchFilterLeave メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave method [.NET Framework profiling]
- ExceptionSearchFilterLeave method [.NET Framework profiling]
ms.assetid: c28a2a82-dd11-4385-843f-b509fb61753b
topic_type:
- apiref
ms.openlocfilehash: d2195e8e055b25f71efbfbcc71e933daa07a4e3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799123"
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="d3939-103">ICorProfilerCallback::ExceptionSearchFilterLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="d3939-103">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>

<span data-ttu-id="d3939-104">ユーザーフィルターの実行が完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="d3939-104">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3939-105">構文</span><span class="sxs-lookup"><span data-stu-id="d3939-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="d3939-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="d3939-106">Requirements</span></span>  

 <span data-ttu-id="d3939-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3939-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3939-108">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d3939-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d3939-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3939-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3939-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3939-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3939-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3939-111">See also</span></span>

- [<span data-ttu-id="d3939-112">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d3939-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d3939-113">ExceptionSearchFilterEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="d3939-113">ExceptionSearchFilterEnter Method</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)
