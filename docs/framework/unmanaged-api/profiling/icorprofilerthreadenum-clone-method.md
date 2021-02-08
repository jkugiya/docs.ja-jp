---
description: '詳細情報: ICorProfilerThreadEnum:: Clone メソッド'
title: ICorProfilerThreadEnum::Clone メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Clone method [.NET Framework profiling]
ms.assetid: 5a278bc9-88e2-4c69-b035-9d550dd77081
topic_type:
- apiref
ms.openlocfilehash: 00920484ed6f089f40281ea2590e6d9c27cd3268
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783795"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="4126f-103">ICorProfilerThreadEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="4126f-103">ICorProfilerThreadEnum::Clone Method</span></span>

<span data-ttu-id="4126f-104">この [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) インターフェイスのコピーへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4126f-104">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4126f-105">構文</span><span class="sxs-lookup"><span data-stu-id="4126f-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4126f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4126f-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="4126f-107">入出力インターフェイスポインターへのポインター。これにより、この [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) インターフェイスのコピーが参照されます。</span><span class="sxs-lookup"><span data-stu-id="4126f-107">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="4126f-108">列挙子のコピーは、この列挙子とは別に独自の列挙状態を保持します。</span><span class="sxs-lookup"><span data-stu-id="4126f-108">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="4126f-109">ただし、コピーの最初のカーソル位置は、この列挙子の現在のカーソル位置と同じです。</span><span class="sxs-lookup"><span data-stu-id="4126f-109">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4126f-110">要件</span><span class="sxs-lookup"><span data-stu-id="4126f-110">Requirements</span></span>  

 <span data-ttu-id="4126f-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4126f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4126f-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4126f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4126f-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4126f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4126f-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4126f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4126f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="4126f-115">See also</span></span>

- [<span data-ttu-id="4126f-116">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="4126f-116">ICorProfilerThreadEnum</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="4126f-117">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="4126f-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
