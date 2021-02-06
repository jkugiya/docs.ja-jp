---
description: '詳細について: ICorDebugProcess5:: EnumerateHandles メソッド'
title: ICorDebugProcess5::EnumerateHandles メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHandles
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type:
- apiref
ms.openlocfilehash: 62ca1390ceec634e6651dc013345688fe5892bcd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649911"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="5b032-103">ICorDebugProcess5::EnumerateHandles メソッド</span><span class="sxs-lookup"><span data-stu-id="5b032-103">ICorDebugProcess5::EnumerateHandles Method</span></span>

<span data-ttu-id="5b032-104">プロセス内のオブジェクトハンドルの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="5b032-104">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b032-105">構文</span><span class="sxs-lookup"><span data-stu-id="5b032-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b032-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5b032-106">Parameters</span></span>  

 `types`  
 <span data-ttu-id="5b032-107">からコレクションに含めるハンドルの種類を指定する [Corgcreの](corgcreferencetype-enumeration.md) 値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="5b032-107">[in] A bitwise combination of [CorGCReferenceType](corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="5b032-108">入出力ガベージコレクションの対象となるオブジェクトの列挙子 [である、](icordebuggcreferenceenum-interface.md) ツールのアドレスへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="5b032-108">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b032-109">解説</span><span class="sxs-lookup"><span data-stu-id="5b032-109">Remarks</span></span>  

 <span data-ttu-id="5b032-110">`EnumerateHandles` は、ハンドルテーブルの検査をサポートするヘルパー関数です。</span><span class="sxs-lookup"><span data-stu-id="5b032-110">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="5b032-111">これは [ICorDebugProcess5:: EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) メソッドに似ていますが、すべてのオブジェクトがガベージコレクトされるよう [に、すべて](icordebuggcreferenceenum-interface.md) のオブジェクトを使用してすべてのオブジェクトを作成するのではなく、handle テーブルからハンドルを持つオブジェクトのみが含まれる点が異なります。</span><span class="sxs-lookup"><span data-stu-id="5b032-111">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="5b032-112">パラメーターは、 `types` コレクションに含めるハンドルの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="5b032-112">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="5b032-113">`types` は、 [Corgcreの型](corgcreferencetype-enumeration.md) の列挙体の次の3つのメンバーのいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="5b032-113">`types` can be any of the following three members of the [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
- <span data-ttu-id="5b032-114">`CorHandleStrongOnly` (厳密な参照へのハンドルのみ)。</span><span class="sxs-lookup"><span data-stu-id="5b032-114">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
- <span data-ttu-id="5b032-115">`CorHandleWeakOnly` (弱参照のみを処理します)。</span><span class="sxs-lookup"><span data-stu-id="5b032-115">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
- <span data-ttu-id="5b032-116">`CorHandleAll` (すべてのハンドル)。</span><span class="sxs-lookup"><span data-stu-id="5b032-116">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b032-117">要件</span><span class="sxs-lookup"><span data-stu-id="5b032-117">Requirements</span></span>  

 <span data-ttu-id="5b032-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b032-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b032-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b032-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b032-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b032-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b032-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b032-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b032-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b032-122">See also</span></span>

- [<span data-ttu-id="5b032-123">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="5b032-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="5b032-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="5b032-124">Debugging</span></span>](index.md)
