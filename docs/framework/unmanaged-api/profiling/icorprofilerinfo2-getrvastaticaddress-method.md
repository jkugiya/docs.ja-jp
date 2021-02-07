---
description: '詳細について: ICorProfilerInfo2:: GetRVAStaticAddress メソッド'
title: ICorProfilerInfo2::GetRVAStaticAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
ms.openlocfilehash: e72a136ca0d8462d19c57da021e9429528555dac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716407"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="099f1-103">ICorProfilerInfo2::GetRVAStaticAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="099f1-103">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>

<span data-ttu-id="099f1-104">指定した相対仮想アドレス (RVA) の静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="099f1-104">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="099f1-105">構文</span><span class="sxs-lookup"><span data-stu-id="099f1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="099f1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="099f1-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="099f1-107">から要求された RVA 静的フィールドを含むクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="099f1-107">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="099f1-108">から要求された RVA 静的フィールドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="099f1-108">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="099f1-109">入出力RVA の静的フィールドのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="099f1-109">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="099f1-110">解説</span><span class="sxs-lookup"><span data-stu-id="099f1-110">Remarks</span></span>  

 <span data-ttu-id="099f1-111">`GetRVAStaticAddress`メソッドは、次のいずれかを返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="099f1-111">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="099f1-112">指定されたコンテキストで、指定された静的フィールドにアドレスが割り当てられていない場合は CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="099f1-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="099f1-113">ガベージコレクションヒープ内に存在する可能性があるオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="099f1-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="099f1-114">これらのアドレスは、ガベージコレクションの後に無効になることがあります。そのため、ガベージコレクションの後、プロファイラーはそれらが有効であると想定してはなりません。</span><span class="sxs-lookup"><span data-stu-id="099f1-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="099f1-115">では、クラスのクラスコンストラクターが完了する前に、 `GetRVAStaticAddress` すべての静的フィールドに対して CORPROF_E_DATAINCOMPLETE が返されます。ただし、一部の静的フィールドは既に初期化されており、ガベージコレクションオブジェクトをルート化する場合があります。</span><span class="sxs-lookup"><span data-stu-id="099f1-115">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="099f1-116">要件</span><span class="sxs-lookup"><span data-stu-id="099f1-116">Requirements</span></span>  

 <span data-ttu-id="099f1-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="099f1-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="099f1-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="099f1-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="099f1-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="099f1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="099f1-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="099f1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="099f1-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="099f1-121">See also</span></span>

- [<span data-ttu-id="099f1-122">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="099f1-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="099f1-123">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="099f1-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
