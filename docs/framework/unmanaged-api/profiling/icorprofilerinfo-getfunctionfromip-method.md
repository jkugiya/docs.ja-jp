---
description: '詳細について: ICorProfilerInfo:: GetFunctionFromIP メソッド'
title: ICorProfilerInfo::GetFunctionFromIP メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromIP
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromIP
helpviewer_keywords:
- GetFunctionFromIP method [.NET Framework profiling]
- ICorProfilerInfo::GetFunctionFromIP method [.NET Framework profiling]
ms.assetid: f069802a-198f-46dd-9f09-4f77adffc9ba
topic_type:
- apiref
ms.openlocfilehash: 1acea6943e74e65e4359c7da590d3888736dbd6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647597"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="4f175-103">ICorProfilerInfo::GetFunctionFromIP メソッド</span><span class="sxs-lookup"><span data-stu-id="4f175-103">ICorProfilerInfo::GetFunctionFromIP Method</span></span>

<span data-ttu-id="4f175-104">マネージコード命令ポインターをにマップ `FunctionID` します。</span><span class="sxs-lookup"><span data-stu-id="4f175-104">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f175-105">構文</span><span class="sxs-lookup"><span data-stu-id="4f175-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f175-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4f175-106">Parameters</span></span>

- `ip`

  <span data-ttu-id="4f175-107">\[in) マネージコード内の命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="4f175-107">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="4f175-108">\[out] 返された関数 ID。</span><span class="sxs-lookup"><span data-stu-id="4f175-108">\[out] The returned function ID.</span></span>

## <a name="requirements"></a><span data-ttu-id="4f175-109">要件</span><span class="sxs-lookup"><span data-stu-id="4f175-109">Requirements</span></span>  

 <span data-ttu-id="4f175-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f175-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f175-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4f175-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4f175-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f175-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f175-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f175-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f175-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f175-114">See also</span></span>

- [<span data-ttu-id="4f175-115">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f175-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
