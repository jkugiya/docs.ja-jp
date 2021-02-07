---
description: '詳細について: ICorProfilerCallback:: ExceptionCLRCatcherFound メソッド'
title: ICorProfilerCallback::ExceptionCLRCatcherFound メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type:
- apiref
ms.openlocfilehash: 37027a00e488eed5681b1d99ada6332d59e6a632
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706306"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="cc849-103">ICorProfilerCallback::ExceptionCLRCatcherFound メソッド</span><span class="sxs-lookup"><span data-stu-id="cc849-103">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>

<span data-ttu-id="cc849-104">`catch`例外のブロックが共通言語ランタイム (CLR) 自体で見つかった場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="cc849-104">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="cc849-105">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="cc849-105">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc849-106">構文</span><span class="sxs-lookup"><span data-stu-id="cc849-106">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="cc849-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="cc849-107">Requirements</span></span>  

 <span data-ttu-id="cc849-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc849-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc849-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cc849-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cc849-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc849-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc849-111">**.NET Framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="cc849-111">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc849-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc849-112">See also</span></span>

- [<span data-ttu-id="cc849-113">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc849-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="cc849-114">ExceptionCLRCatcherExecute メソッド</span><span class="sxs-lookup"><span data-stu-id="cc849-114">ExceptionCLRCatcherExecute Method</span></span>](icorprofilercallback-exceptionclrcatcherexecute-method.md)
