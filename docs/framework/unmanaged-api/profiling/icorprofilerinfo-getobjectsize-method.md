---
description: '詳細について: ICorProfilerInfo:: GetObjectSize メソッド'
title: ICorProfilerInfo::GetObjectSize メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
ms.openlocfilehash: c762b43e87c6f25b301f3f677728ca8cbe19b138
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788632"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="fb1e8-103">ICorProfilerInfo::GetObjectSize メソッド</span><span class="sxs-lookup"><span data-stu-id="fb1e8-103">ICorProfilerInfo::GetObjectSize Method</span></span>

<span data-ttu-id="fb1e8-104">指定したオブジェクトのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="fb1e8-104">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb1e8-105">構文</span><span class="sxs-lookup"><span data-stu-id="fb1e8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb1e8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fb1e8-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="fb1e8-107">からオブジェクトの ID です。</span><span class="sxs-lookup"><span data-stu-id="fb1e8-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="fb1e8-108">入出力オブジェクトのサイズへのポインター (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="fb1e8-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb1e8-109">解説</span><span class="sxs-lookup"><span data-stu-id="fb1e8-109">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fb1e8-110">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="fb1e8-110">This method is obsolete.</span></span> <span data-ttu-id="fb1e8-111">64ビットプラットフォームで 4 GB を超えるオブジェクトの COR_E_OVERFLOW を返します。</span><span class="sxs-lookup"><span data-stu-id="fb1e8-111">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="fb1e8-112">代わりに  [ICorProfilerInfo4:: GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="fb1e8-112">Use the  [ICorProfilerInfo4::GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="fb1e8-113">多くの場合、同じ種類の異なるオブジェクトのサイズは同じです。</span><span class="sxs-lookup"><span data-stu-id="fb1e8-113">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="fb1e8-114">ただし、配列や文字列など、一部の型では、オブジェクトごとにサイズが異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="fb1e8-114">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="fb1e8-115">メソッドによって返されるサイズには、 `GetObjectSize` オブジェクトがガベージコレクションヒープに配置された後に表示されるアラインメントの埋め込みは含まれません。</span><span class="sxs-lookup"><span data-stu-id="fb1e8-115">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="fb1e8-116">メソッドを使用して `GetObjectSize` オブジェクトからガベージコレクションヒープ上のオブジェクトに進む場合は、必要に応じて、手動でアラインメントのパディングを追加します。</span><span class="sxs-lookup"><span data-stu-id="fb1e8-116">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="fb1e8-117">32ビットの Windows では、COR_PRF_GC_GEN_0、COR_PRF_GC_GEN_1、および COR_PRF_GC_GEN_2 は4バイトの配置を使用し、COR_PRF_GC_LARGE_OBJECT_HEAP は8バイトの配置を使用します。</span><span class="sxs-lookup"><span data-stu-id="fb1e8-117">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="fb1e8-118">64ビットの Windows では、アラインメントは常に8バイトです。</span><span class="sxs-lookup"><span data-stu-id="fb1e8-118">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb1e8-119">要件</span><span class="sxs-lookup"><span data-stu-id="fb1e8-119">Requirements</span></span>  

 <span data-ttu-id="fb1e8-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb1e8-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb1e8-121">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb1e8-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb1e8-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb1e8-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb1e8-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb1e8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb1e8-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb1e8-124">See also</span></span>

- [<span data-ttu-id="fb1e8-125">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fb1e8-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
