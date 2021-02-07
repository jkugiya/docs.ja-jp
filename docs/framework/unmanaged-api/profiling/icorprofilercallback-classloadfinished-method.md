---
description: '詳細情報: ICorProfilerCallback:: ClassLoadFinished メソッド'
title: ICorProfilerCallback::ClassLoadFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
ms.openlocfilehash: ba0a6a643ab49a4e7a0ed10dda0dadff5741234d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706423"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="8cc2c-103">ICorProfilerCallback::ClassLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="8cc2c-103">ICorProfilerCallback::ClassLoadFinished Method</span></span>

<span data-ttu-id="8cc2c-104">クラスが読み込みを完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="8cc2c-104">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cc2c-105">構文</span><span class="sxs-lookup"><span data-stu-id="8cc2c-105">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cc2c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8cc2c-106">Parameters</span></span>

- `classId`

  <span data-ttu-id="8cc2c-107">\[in] は、読み込まれたクラスを識別します。</span><span class="sxs-lookup"><span data-stu-id="8cc2c-107">\[in] Identifies the class that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="8cc2c-108">\[in] クラスが正常に読み込まれたかどうかを示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="8cc2c-108">\[in] An HRESULT that indicates whether the class loaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="8cc2c-109">解説</span><span class="sxs-lookup"><span data-stu-id="8cc2c-109">Remarks</span></span>  

 <span data-ttu-id="8cc2c-110">の値 `classId` は、 `ClassLoadFinished` メソッドが呼び出されるまで、情報要求に対して有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="8cc2c-110">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="8cc2c-111">クラスの読み込みの一部は、コールバック後に続行される場合があり `ClassLoadFinished` ます。</span><span class="sxs-lookup"><span data-stu-id="8cc2c-111">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="8cc2c-112">のエラー HRESULT は `hrStatus` エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="8cc2c-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="8cc2c-113">ただし、の成功 HRESULT は、 `hrStatus` クラスの読み込みの最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="8cc2c-113">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cc2c-114">要件</span><span class="sxs-lookup"><span data-stu-id="8cc2c-114">Requirements</span></span>  

 <span data-ttu-id="8cc2c-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8cc2c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cc2c-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8cc2c-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8cc2c-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cc2c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cc2c-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cc2c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc2c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="8cc2c-119">See also</span></span>

- [<span data-ttu-id="8cc2c-120">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8cc2c-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8cc2c-121">ClassLoadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="8cc2c-121">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
