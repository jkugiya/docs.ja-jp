---
description: '詳細について: ICorProfilerInfo4:: GetObjectSize2 メソッド'
title: ICorProfilerInfo4::GetObjectSize2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
ms.openlocfilehash: 986c3d99501e21feec95dd3b6014f8d11d809704
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794525"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="b3aea-103">ICorProfilerInfo4::GetObjectSize2 メソッド</span><span class="sxs-lookup"><span data-stu-id="b3aea-103">ICorProfilerInfo4::GetObjectSize2 Method</span></span>

<span data-ttu-id="b3aea-104">指定したオブジェクトのサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="b3aea-104">Returns the size of a specified object.</span></span> <span data-ttu-id="b3aea-105">で表現できる値よりも大きいオブジェクトのサイズをレポートすることによって、 [ICorProfilerInfo:: GetObjectSize](icorprofilerinfo-getobjectsize-method.md) メソッドを置き換え `ULONG` ます。</span><span class="sxs-lookup"><span data-stu-id="b3aea-105">Replaces the [ICorProfilerInfo::GetObjectSize](icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3aea-106">構文</span><span class="sxs-lookup"><span data-stu-id="b3aea-106">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3aea-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b3aea-107">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="b3aea-108">からオブジェクトの ID です。</span><span class="sxs-lookup"><span data-stu-id="b3aea-108">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="b3aea-109">入出力オブジェクトのサイズへのポインター (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="b3aea-109">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3aea-110">解説</span><span class="sxs-lookup"><span data-stu-id="b3aea-110">Remarks</span></span>  

 <span data-ttu-id="b3aea-111">多くの場合、同じ種類の異なるオブジェクトのサイズは同じです。</span><span class="sxs-lookup"><span data-stu-id="b3aea-111">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="b3aea-112">ただし、配列や文字列など、一部の型では、オブジェクトごとにサイズが異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b3aea-112">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3aea-113">要件</span><span class="sxs-lookup"><span data-stu-id="b3aea-113">Requirements</span></span>  

 <span data-ttu-id="b3aea-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3aea-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3aea-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b3aea-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b3aea-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3aea-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3aea-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3aea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3aea-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3aea-118">See also</span></span>

- [<span data-ttu-id="b3aea-119">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b3aea-119">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
