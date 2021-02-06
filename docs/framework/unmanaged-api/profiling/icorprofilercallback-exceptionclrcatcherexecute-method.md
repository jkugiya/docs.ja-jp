---
description: '詳細について: ICorProfilerCallback:: ExceptionCLRCatcherExecute メソッド'
title: ICorProfilerCallback::ExceptionCLRCatcherExecute メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherExecute
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherExecute
helpviewer_keywords:
- ExceptionCLRCatcherExecute method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCLRCatcherExecute method [.NET Framework profiling]
ms.assetid: aaac8f98-5cf4-42c7-b04b-556cce367e36
topic_type:
- apiref
ms.openlocfilehash: cb6926fdfcc9b5ffef20cc69c71a3bafefd9f6ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657503"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="437d0-103">ICorProfilerCallback::ExceptionCLRCatcherExecute メソッド</span><span class="sxs-lookup"><span data-stu-id="437d0-103">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>

<span data-ttu-id="437d0-104">`catch`例外のブロックが共通言語ランタイム (CLR) 自体の内部で実行されるときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="437d0-104">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="437d0-105">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="437d0-105">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="437d0-106">構文</span><span class="sxs-lookup"><span data-stu-id="437d0-106">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="437d0-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="437d0-107">Requirements</span></span>  

 <span data-ttu-id="437d0-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="437d0-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="437d0-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="437d0-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="437d0-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="437d0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="437d0-111">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="437d0-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="437d0-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="437d0-112">See also</span></span>

- [<span data-ttu-id="437d0-113">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="437d0-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="437d0-114">ExceptionCLRCatcherFound メソッド</span><span class="sxs-lookup"><span data-stu-id="437d0-114">ExceptionCLRCatcherFound Method</span></span>](icorprofilercallback-exceptionclrcatcherfound-method.md)
