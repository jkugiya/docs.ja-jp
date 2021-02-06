---
description: '詳細については、次を参照してください: ICorProfilerInfo2:: GetThreadStaticAddress メソッド'
title: ICorProfilerInfo2::GetThreadStaticAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
ms.openlocfilehash: bab4190f3751967031806dccbea2fdf6add73f6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647052"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="407bb-103">ICorProfilerInfo2::GetThreadStaticAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="407bb-103">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>

<span data-ttu-id="407bb-104">指定したスレッドのスコープ内にある、指定したスレッド静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="407bb-104">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="407bb-105">構文</span><span class="sxs-lookup"><span data-stu-id="407bb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="407bb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="407bb-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="407bb-107">から要求されたスレッド静的フィールドを含むクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="407bb-107">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="407bb-108">から要求されたスレッドの静的フィールドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="407bb-108">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="407bb-109">から要求された静的フィールドのスコープであるスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="407bb-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="407bb-110">入出力指定したスレッド内の静的フィールドのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="407bb-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="407bb-111">解説</span><span class="sxs-lookup"><span data-stu-id="407bb-111">Remarks</span></span>  

 <span data-ttu-id="407bb-112">`GetThreadStaticAddress`メソッドは、次のいずれかを返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="407bb-112">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="407bb-113">指定されたコンテキストで、指定された静的フィールドにアドレスが割り当てられていない場合は CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="407bb-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="407bb-114">ガベージコレクションヒープ内に存在する可能性があるオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="407bb-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="407bb-115">これらのアドレスは、ガベージコレクションの後に無効になることがあります。そのため、ガベージコレクションプロファイラーは、これらのアドレスが有効であると想定することはできません。</span><span class="sxs-lookup"><span data-stu-id="407bb-115">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="407bb-116">では、クラスのクラスコンストラクターが完了する前に、 `GetThreadStaticAddress` すべての静的フィールドに対して CORPROF_E_DATAINCOMPLETE が返されます。ただし、静的フィールドの一部は既に初期化されており、ガベージコレクションオブジェクトがルート化される場合があります。</span><span class="sxs-lookup"><span data-stu-id="407bb-116">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="407bb-117">要件</span><span class="sxs-lookup"><span data-stu-id="407bb-117">Requirements</span></span>  

 <span data-ttu-id="407bb-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="407bb-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="407bb-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="407bb-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="407bb-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="407bb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="407bb-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="407bb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="407bb-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="407bb-122">See also</span></span>

- [<span data-ttu-id="407bb-123">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="407bb-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="407bb-124">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="407bb-124">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
