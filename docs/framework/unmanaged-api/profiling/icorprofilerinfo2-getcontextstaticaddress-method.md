---
description: '詳細について: ICorProfilerInfo2:: GetContextStaticAddress メソッド'
title: ICorProfilerInfo2::GetContextStaticAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
ms.openlocfilehash: 7ea8b81c8b1dba4577e070eda68e760cc39f9131
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760499"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="17d4e-103">ICorProfilerInfo2::GetContextStaticAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="17d4e-103">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>

<span data-ttu-id="17d4e-104">指定されたコンテキストのスコープ内にある、指定されたコンテキスト静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="17d4e-104">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17d4e-105">構文</span><span class="sxs-lookup"><span data-stu-id="17d4e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17d4e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="17d4e-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="17d4e-107">から要求されたコンテキスト静的フィールドを含むクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="17d4e-107">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="17d4e-108">から要求されたコンテキスト静的フィールドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="17d4e-108">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="17d4e-109">から要求されたコンテキスト静的フィールドのスコープであるコンテキストの ID。</span><span class="sxs-lookup"><span data-stu-id="17d4e-109">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="17d4e-110">入出力指定されたコンテキスト内の静的フィールドのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="17d4e-110">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17d4e-111">解説</span><span class="sxs-lookup"><span data-stu-id="17d4e-111">Remarks</span></span>  

 <span data-ttu-id="17d4e-112">`GetContextStaticAddress`メソッドは、次のいずれかを返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="17d4e-112">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="17d4e-113">指定されたコンテキストで、指定された静的フィールドにアドレスが割り当てられていない場合は CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="17d4e-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="17d4e-114">ガベージコレクションヒープ内に存在する可能性があるオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="17d4e-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="17d4e-115">これらのアドレスは、ガベージコレクションの後に無効になることがあります。そのため、ガベージコレクションの後、プロファイラーはそれらが有効であると想定してはなりません。</span><span class="sxs-lookup"><span data-stu-id="17d4e-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="17d4e-116">では、クラスのクラスコンストラクターが完了する前に、 `GetContextStaticAddress` すべての静的フィールドに対して CORPROF_E_DATAINCOMPLETE が返されます。ただし、静的フィールドの一部は既に初期化されており、ガベージコレクションオブジェクトがルート化される場合があります。</span><span class="sxs-lookup"><span data-stu-id="17d4e-116">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17d4e-117">要件</span><span class="sxs-lookup"><span data-stu-id="17d4e-117">Requirements</span></span>  

 <span data-ttu-id="17d4e-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17d4e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17d4e-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="17d4e-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="17d4e-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17d4e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17d4e-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17d4e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d4e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="17d4e-122">See also</span></span>

- [<span data-ttu-id="17d4e-123">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17d4e-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="17d4e-124">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17d4e-124">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
