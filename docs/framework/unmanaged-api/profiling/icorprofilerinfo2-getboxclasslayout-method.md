---
description: '詳細について: ICorProfilerInfo2:: GetBoxClassLayout メソッド'
title: ICorProfilerInfo2::GetBoxClassLayout メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetBoxClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type:
- apiref
ms.openlocfilehash: 0bc9ccc80da8bcc89cfe73eaa240310c01e6ca8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760509"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="cc075-103">ICorProfilerInfo2::GetBoxClassLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="cc075-103">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>

<span data-ttu-id="cc075-104">指定された値型がボックス化されている場合の位置に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc075-104">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc075-105">構文</span><span class="sxs-lookup"><span data-stu-id="cc075-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc075-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cc075-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="cc075-107">からボックス化された値の型を記述するクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="cc075-107">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="cc075-108">入出力値型のボックス化されたオブジェクト ID ポインターを基準とするオフセットを表す整数。</span><span class="sxs-lookup"><span data-stu-id="cc075-108">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc075-109">解説</span><span class="sxs-lookup"><span data-stu-id="cc075-109">Remarks</span></span>  

 <span data-ttu-id="cc075-110">`pBufferOffset`値は、ボックス内の値の型の場所です。</span><span class="sxs-lookup"><span data-stu-id="cc075-110">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="cc075-111">ボックス化されたオブジェクトにを適用した後 `pBufferOffset` 、値型のクラスレイアウトを使用して、オブジェクトの値を解釈できます。</span><span class="sxs-lookup"><span data-stu-id="cc075-111">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc075-112">要件</span><span class="sxs-lookup"><span data-stu-id="cc075-112">Requirements</span></span>  

 <span data-ttu-id="cc075-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc075-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc075-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cc075-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cc075-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc075-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc075-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc075-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc075-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc075-117">See also</span></span>

- [<span data-ttu-id="cc075-118">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc075-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="cc075-119">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc075-119">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
