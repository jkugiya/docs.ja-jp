---
description: '詳細について: ICorProfilerObjectEnum:: GetCount メソッド'
title: ICorProfilerObjectEnum::GetCount メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::GetCount
helpviewer_keywords:
- ICorProfilerObjectEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 166b0761-ed80-4ccd-9973-dc20e61bf8fa
topic_type:
- apiref
ms.openlocfilehash: b1bedfca913a099f88780807021497d15f75fcd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798941"
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="ee614-103">ICorProfilerObjectEnum::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="ee614-103">ICorProfilerObjectEnum::GetCount Method</span></span>

<span data-ttu-id="ee614-104">コレクション内の固定されたオブジェクトの合計数を取得します。</span><span class="sxs-lookup"><span data-stu-id="ee614-104">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee614-105">構文</span><span class="sxs-lookup"><span data-stu-id="ee614-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee614-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ee614-106">Parameters</span></span>  

 `pcelt`  
 <span data-ttu-id="ee614-107">入出力コレクション内の固定されたオブジェクトの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ee614-107">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="ee614-108">このメソッドは、.NET Framework バージョン 3.5 Service Pack 1 (SP1) 以降のバージョンで常に0を返します。</span><span class="sxs-lookup"><span data-stu-id="ee614-108">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee614-109">要件</span><span class="sxs-lookup"><span data-stu-id="ee614-109">Requirements</span></span>  

 <span data-ttu-id="ee614-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee614-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee614-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ee614-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ee614-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee614-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee614-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee614-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee614-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee614-114">See also</span></span>

- [<span data-ttu-id="ee614-115">ICorProfilerObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee614-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
