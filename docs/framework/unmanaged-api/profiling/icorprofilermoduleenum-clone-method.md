---
description: '詳細情報: ICorProfilerModuleEnum:: Clone メソッド'
title: ICorProfilerModuleEnum::Clone メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
ms.openlocfilehash: 0d2a235def6d3b16d661e51979742426ebe1942f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736938"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="553c5-103">ICorProfilerModuleEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="553c5-103">ICorProfilerModuleEnum::Clone Method</span></span>

<span data-ttu-id="553c5-104">この [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) インターフェイスのコピーへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="553c5-104">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="553c5-105">構文</span><span class="sxs-lookup"><span data-stu-id="553c5-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="553c5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="553c5-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="553c5-107">入出力次に、この [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) インターフェイスのコピーを指すインターフェイスポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="553c5-107">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="553c5-108">列挙子のコピーは、この列挙子とは別に独自の列挙状態を保持します。</span><span class="sxs-lookup"><span data-stu-id="553c5-108">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="553c5-109">ただし、コピーの初期カーソル位置は、この列挙子の現在のカーソル位置と同じです。</span><span class="sxs-lookup"><span data-stu-id="553c5-109">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="553c5-110">要件</span><span class="sxs-lookup"><span data-stu-id="553c5-110">Requirements</span></span>  

 <span data-ttu-id="553c5-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="553c5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="553c5-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="553c5-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="553c5-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="553c5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="553c5-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="553c5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="553c5-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="553c5-115">See also</span></span>

- [<span data-ttu-id="553c5-116">ICorProfilerModuleEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="553c5-116">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="553c5-117">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="553c5-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
