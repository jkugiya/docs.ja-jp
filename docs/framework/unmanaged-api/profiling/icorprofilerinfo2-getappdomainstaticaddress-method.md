---
description: '詳細について: ICorProfilerInfo2:: GetAppDomainStaticAddress メソッド'
title: ICorProfilerInfo2::GetAppDomainStaticAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
ms.openlocfilehash: 4ef8511e75a18f7626fa7a30ea194140de051bb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753238"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="085c0-103">ICorProfilerInfo2::GetAppDomainStaticAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="085c0-103">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>

<span data-ttu-id="085c0-104">指定したアプリケーションドメインのスコープ内にある、指定したアプリケーションドメインの静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="085c0-104">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="085c0-105">構文</span><span class="sxs-lookup"><span data-stu-id="085c0-105">Syntax</span></span>  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="085c0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="085c0-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="085c0-107">から要求されたアプリケーションドメインの静的フィールドを含むクラスのクラス ID。</span><span class="sxs-lookup"><span data-stu-id="085c0-107">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="085c0-108">から要求されたアプリケーションドメインの静的フィールドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="085c0-108">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="085c0-109">から要求された静的フィールドのスコープであるアプリケーションドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="085c0-109">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="085c0-110">入出力指定されたアプリケーションドメイン内の静的フィールドのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="085c0-110">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="085c0-111">解説</span><span class="sxs-lookup"><span data-stu-id="085c0-111">Remarks</span></span>  

 <span data-ttu-id="085c0-112">`GetAppDomainStaticAddress`メソッドは、次のいずれかを返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="085c0-112">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="085c0-113">指定されたコンテキストで、指定された静的フィールドにアドレスが割り当てられていない場合は CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="085c0-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="085c0-114">ガベージコレクションヒープ内に存在する可能性があるオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="085c0-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="085c0-115">これらのアドレスは、ガベージコレクションの後に無効になることがあります。そのため、ガベージコレクションの後、プロファイラーはそれらが有効であると想定してはなりません。</span><span class="sxs-lookup"><span data-stu-id="085c0-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="085c0-116">では、クラスのクラスコンストラクターが完了する前に、 `GetAppDomainStaticAddress` すべての静的フィールドに対して CORPROF_E_DATAINCOMPLETE が返されます。ただし、静的フィールドの一部は既に初期化されており、ガベージコレクションオブジェクトがルート化される場合があります。</span><span class="sxs-lookup"><span data-stu-id="085c0-116">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="085c0-117">要件</span><span class="sxs-lookup"><span data-stu-id="085c0-117">Requirements</span></span>  

 <span data-ttu-id="085c0-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="085c0-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="085c0-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="085c0-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="085c0-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="085c0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="085c0-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="085c0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="085c0-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="085c0-122">See also</span></span>

- [<span data-ttu-id="085c0-123">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="085c0-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="085c0-124">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="085c0-124">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
