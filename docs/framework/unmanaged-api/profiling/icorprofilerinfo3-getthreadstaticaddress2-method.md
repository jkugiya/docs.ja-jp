---
description: '詳細について: ICorProfilerInfo3:: GetThreadStaticAddress2 メソッド'
title: ICorProfilerInfo3::GetThreadStaticAddress2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
ms.openlocfilehash: 6734996435206f9e0c837eba39df1ad81677e54b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794547"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="e3dab-103">ICorProfilerInfo3::GetThreadStaticAddress2 メソッド</span><span class="sxs-lookup"><span data-stu-id="e3dab-103">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>

<span data-ttu-id="e3dab-104">指定したスレッドおよびアプリケーション ドメインのスコープ内にある、指定したスレッド内静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="e3dab-104">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3dab-105">構文</span><span class="sxs-lookup"><span data-stu-id="e3dab-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3dab-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e3dab-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="e3dab-107">から要求されたスレッド静的フィールドを含むクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="e3dab-107">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="e3dab-108">から要求されたスレッドの静的フィールドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="e3dab-108">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="e3dab-109">[in] アプリケーション ドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="e3dab-109">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="e3dab-110">から要求された静的フィールドのスコープであるスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="e3dab-110">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="e3dab-111">入出力指定したスレッド内の静的フィールドのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e3dab-111">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3dab-112">解説</span><span class="sxs-lookup"><span data-stu-id="e3dab-112">Remarks</span></span>  

 <span data-ttu-id="e3dab-113">`GetThreadStaticAddress2`メソッドは、次のいずれかを返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="e3dab-113">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
- <span data-ttu-id="e3dab-114">指定されたコンテキストで、指定された静的フィールドにアドレスが割り当てられていない場合は CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="e3dab-114">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="e3dab-115">ガベージコレクションヒープ内に存在する可能性があるオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="e3dab-115">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="e3dab-116">これらのアドレスは、ガベージコレクションの後に無効になることがあります。そのため、ガベージコレクションの後、プロファイラーはそれらが有効であると想定してはなりません。</span><span class="sxs-lookup"><span data-stu-id="e3dab-116">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="e3dab-117">では、クラスのクラスコンストラクターが完了する前に、 `GetThreadStaticAddress2` すべての静的フィールドに対して CORPROF_E_DATAINCOMPLETE が返されます。ただし、静的フィールドの一部は既に初期化されており、ガベージコレクションオブジェクトがルート化される場合があります。</span><span class="sxs-lookup"><span data-stu-id="e3dab-117">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="e3dab-118">[ICorProfilerInfo2:: GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md)メソッドはメソッドに似てい `GetThreadStaticAddress2` ますが、アプリケーションドメインの引数を受け取りません。</span><span class="sxs-lookup"><span data-stu-id="e3dab-118">The [ICorProfilerInfo2::GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3dab-119">要件</span><span class="sxs-lookup"><span data-stu-id="e3dab-119">Requirements</span></span>  

 <span data-ttu-id="e3dab-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3dab-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3dab-121">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e3dab-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e3dab-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3dab-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3dab-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3dab-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3dab-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3dab-124">See also</span></span>

- [<span data-ttu-id="e3dab-125">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e3dab-125">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="e3dab-126">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e3dab-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="e3dab-127">プロファイル</span><span class="sxs-lookup"><span data-stu-id="e3dab-127">Profiling</span></span>](index.md)
