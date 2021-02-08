---
description: '詳細情報: COR_GC_REFERENCE 構造'
title: COR_GC_REFERENCE 構造体
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
ms.openlocfilehash: 38518bb1eb870081621bf32af9e63cdaa208dbd3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801814"
---
# <a name="cor_gc_reference-structure"></a><span data-ttu-id="60c94-103">COR_GC_REFERENCE 構造体</span><span class="sxs-lookup"><span data-stu-id="60c94-103">COR_GC_REFERENCE Structure</span></span>

<span data-ttu-id="60c94-104">ガベージ コレクトされるオブジェクトに関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="60c94-104">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60c94-105">構文</span><span class="sxs-lookup"><span data-stu-id="60c94-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="60c94-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="60c94-106">Members</span></span>  
  
|<span data-ttu-id="60c94-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="60c94-107">Member</span></span>|<span data-ttu-id="60c94-108">説明</span><span class="sxs-lookup"><span data-stu-id="60c94-108">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="60c94-109">ハンドルまたはオブジェクトが属するアプリケーションドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60c94-109">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="60c94-110">この値は、の場合もあり `null` ます。</span><span class="sxs-lookup"><span data-stu-id="60c94-110">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="60c94-111">ガベージコレクションされるオブジェクトに対応する ICorDebugValue またはの値のインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="60c94-111">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="60c94-112">ルートの取得元を示す [Corgcreの Encetype](corgcreferencetype-enumeration.md) 列挙値。</span><span class="sxs-lookup"><span data-stu-id="60c94-112">A [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="60c94-113">詳細については、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60c94-113">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="60c94-114">ガベージコレクションされるオブジェクトに関する追加データ。</span><span class="sxs-lookup"><span data-stu-id="60c94-114">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="60c94-115">この情報は、フィールドに示されているように、オブジェクトのソースによって異なり `type` ます。</span><span class="sxs-lookup"><span data-stu-id="60c94-115">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="60c94-116">詳細については、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60c94-116">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60c94-117">解説</span><span class="sxs-lookup"><span data-stu-id="60c94-117">Remarks</span></span>  

 <span data-ttu-id="60c94-118">`type`フィールドは、参照の取得元を示す[Corgcreの型](corgcreferencetype-enumeration.md)の列挙値です。</span><span class="sxs-lookup"><span data-stu-id="60c94-118">The `type` field is a [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="60c94-119">特定の `COR_GC_REFERENCE` 値には、次のいずれかの種類のマネージオブジェクトを反映できます。</span><span class="sxs-lookup"><span data-stu-id="60c94-119">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="60c94-120">すべてのマネージスタックのオブジェクト ( `CorGCReferenceType.CorReferenceStack` )。</span><span class="sxs-lookup"><span data-stu-id="60c94-120">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="60c94-121">これには、マネージコードのライブ参照や、共通言語ランタイムによって作成されたオブジェクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="60c94-121">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="60c94-122">ハンドルテーブルからのオブジェクト ( `CorGCReferenceType.CorHandle*` )。</span><span class="sxs-lookup"><span data-stu-id="60c94-122">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="60c94-123">これには、モジュール内の厳密な参照 ( `HNDTYPE_STRONG` および `HNDTYPE_REFCOUNT` ) と静的変数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="60c94-123">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="60c94-124">ファイナライザーキュー () からのオブジェクト `CorGCReferenceType.CorReferenceFinalizer` 。</span><span class="sxs-lookup"><span data-stu-id="60c94-124">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="60c94-125">ファイナライザーが実行されるまで、ファイナライザーはオブジェクトをキューに置いています。</span><span class="sxs-lookup"><span data-stu-id="60c94-125">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="60c94-126">フィールドには、 `extraData` 参照のソース (または型) に応じて追加のデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="60c94-126">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="60c94-127">次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="60c94-127">Possible values are:</span></span>  
  
- <span data-ttu-id="60c94-128">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="60c94-128">`DependentSource`.</span></span> <span data-ttu-id="60c94-129">がの `type` 場合 `CorGCREferenceType.CorHandleStrongDependent` 、このフィールドはオブジェクトであり、alive の場合、ガベージコレクトされるオブジェクトがルートになり `COR_GC_REFERENCE.Location` ます。</span><span class="sxs-lookup"><span data-stu-id="60c94-129">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="60c94-130">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="60c94-130">`RefCount`.</span></span> <span data-ttu-id="60c94-131">がの `type` 場合 `CorGCREferenceType.CorHandleStrongRefCount` 、このフィールドはハンドルの参照カウントです。</span><span class="sxs-lookup"><span data-stu-id="60c94-131">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="60c94-132">`Size`.</span><span class="sxs-lookup"><span data-stu-id="60c94-132">`Size`.</span></span> <span data-ttu-id="60c94-133">がの `type` 場合 `CorGCREferenceType.CorHandleStrongSizedByref` 、このフィールドはガベージコレクターによってオブジェクトのルートが計算されたオブジェクトツリーの最後のサイズになります。</span><span class="sxs-lookup"><span data-stu-id="60c94-133">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="60c94-134">この計算は必ずしも最新の状態ではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="60c94-134">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60c94-135">要件</span><span class="sxs-lookup"><span data-stu-id="60c94-135">Requirements</span></span>  

 <span data-ttu-id="60c94-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60c94-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60c94-137">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60c94-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60c94-138">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60c94-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60c94-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60c94-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c94-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="60c94-140">See also</span></span>

- [<span data-ttu-id="60c94-141">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="60c94-141">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="60c94-142">デバッグ</span><span class="sxs-lookup"><span data-stu-id="60c94-142">Debugging</span></span>](index.md)
