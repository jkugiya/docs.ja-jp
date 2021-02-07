---
description: '詳細について: ICorProfilerInfo2:: GetStaticFieldInfo メソッド'
title: ICorProfilerInfo2::GetStaticFieldInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
ms.openlocfilehash: 1acde9d5ad1a35b11cb036bced99c1909f0b6b04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716358"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="8f399-103">ICorProfilerInfo2::GetStaticFieldInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="8f399-103">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>

<span data-ttu-id="8f399-104">指定したフィールドに適用される静的の種類を示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="8f399-104">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f399-105">構文</span><span class="sxs-lookup"><span data-stu-id="8f399-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f399-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8f399-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="8f399-107">から静的フィールドが定義されているクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="8f399-107">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="8f399-108">から静的フィールドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="8f399-108">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="8f399-109">入出力指定されたフィールドが静的かどうかを示す [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) 列挙体の値へのポインター。存在する場合は、フィールドに適用される静的の種類。</span><span class="sxs-lookup"><span data-stu-id="8f399-109">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f399-110">解説</span><span class="sxs-lookup"><span data-stu-id="8f399-110">Remarks</span></span>  

 <span data-ttu-id="8f399-111">この情報は、静的フィールドのアドレスを取得するために呼び出す関数を決定するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="8f399-111">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="8f399-112">プロファイラーコードでは、静的フィールドのメタデータを確認して、実際にアドレスがあることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f399-112">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="8f399-113">静的リテラル (つまり、定数) はメタデータにのみ存在し、アドレスを持ちません。</span><span class="sxs-lookup"><span data-stu-id="8f399-113">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f399-114">要件</span><span class="sxs-lookup"><span data-stu-id="8f399-114">Requirements</span></span>  

 <span data-ttu-id="8f399-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f399-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f399-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8f399-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8f399-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f399-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f399-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f399-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f399-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f399-119">See also</span></span>

- [<span data-ttu-id="8f399-120">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8f399-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="8f399-121">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8f399-121">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
