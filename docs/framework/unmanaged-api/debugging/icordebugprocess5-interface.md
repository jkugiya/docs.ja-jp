---
description: 詳細については、「ICorDebugProcess5 インターフェイス」を参照してください。
title: ICorDebugProcess5 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
ms.openlocfilehash: 880c305c1d9786f87d9727836a973696aa686ecf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649768"
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="85f5e-103">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85f5e-103">ICorDebugProcess5 Interface</span></span>

<span data-ttu-id="85f5e-104">は、アプリケーションインターフェイスを拡張して、マネージヒープへのアクセスをサポートし、マネージオブジェクトのガベージコレクションに関する情報を提供し、デバッガーがアプリケーションのローカルネイティブイメージキャッシュからイメージを読み込むかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="85f5e-104">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85f5e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="85f5e-105">Methods</span></span>  
  
|<span data-ttu-id="85f5e-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="85f5e-106">Method</span></span>|<span data-ttu-id="85f5e-107">説明</span><span class="sxs-lookup"><span data-stu-id="85f5e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85f5e-108">EnableNGenPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="85f5e-108">EnableNGenPolicy Method</span></span>](icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="85f5e-109">マネージデバッガーで実行中にアプリケーションがネイティブイメージを読み込む方法を決定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="85f5e-109">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="85f5e-110">EnumerateGCReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="85f5e-110">EnumerateGCReferences Method</span></span>](icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="85f5e-111">プロセスでガベージコレクトされるすべてのオブジェクトの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="85f5e-111">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="85f5e-112">EnumerateHandles メソッド</span><span class="sxs-lookup"><span data-stu-id="85f5e-112">EnumerateHandles Method</span></span>](icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="85f5e-113">プロセス内のオブジェクトハンドルの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="85f5e-113">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="85f5e-114">EnumerateHeap メソッド</span><span class="sxs-lookup"><span data-stu-id="85f5e-114">EnumerateHeap Method</span></span>](icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="85f5e-115">マネージヒープ上のオブジェクトの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="85f5e-115">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="85f5e-116">EnumerateHeapRegions メソッド</span><span class="sxs-lookup"><span data-stu-id="85f5e-116">EnumerateHeapRegions Method</span></span>](icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="85f5e-117">マネージヒープの領域の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="85f5e-117">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="85f5e-118">GetArrayLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="85f5e-118">GetArrayLayout Method</span></span>](icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="85f5e-119">メモリ内の配列のレイアウトに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="85f5e-119">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="85f5e-120">GetGCHeapInformation メソッド</span><span class="sxs-lookup"><span data-stu-id="85f5e-120">GetGCHeapInformation Method</span></span>](icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="85f5e-121">マネージヒープでガベージコレクトされるオブジェクトに関する情報を格納している [COR_HEAPINFO](cor-heapinfo-structure.md) 構造体へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="85f5e-121">Gets a pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="85f5e-122">GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="85f5e-122">GetObject Method</span></span>](icordebugprocess5-getobject-method.md)|<span data-ttu-id="85f5e-123">マネージヒープ上のオブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="85f5e-123">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="85f5e-124">GetTypeFields メソッド</span><span class="sxs-lookup"><span data-stu-id="85f5e-124">GetTypeFields Method</span></span>](icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="85f5e-125">型の識別子に基づいて、型のフィールド情報を格納している配列へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="85f5e-125">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="85f5e-126">GetTypeForTypeID メソッド</span><span class="sxs-lookup"><span data-stu-id="85f5e-126">GetTypeForTypeID Method</span></span>](icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="85f5e-127">型識別子に基づいてオブジェクトに関する情報を提供する型オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="85f5e-127">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="85f5e-128">GetTypeID メソッド</span><span class="sxs-lookup"><span data-stu-id="85f5e-128">GetTypeID Method</span></span>](icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="85f5e-129">指定したアドレスにあるオブジェクトの型識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="85f5e-129">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="85f5e-130">GetTypeLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="85f5e-130">GetTypeLayout Method</span></span>](icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="85f5e-131">型識別子に基づいて、メモリ内のオブジェクトのレイアウトに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="85f5e-131">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85f5e-132">解説</span><span class="sxs-lookup"><span data-stu-id="85f5e-132">Remarks</span></span>  

 <span data-ttu-id="85f5e-133">このインターフェイスは、ICorDebugProcess2、ICorDebugProcess3、および[](icordebugprocess3-interface.md)の各インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="85f5e-133">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85f5e-134">このインターフェイスは、別のコンピューターまたは別のプロセスからのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="85f5e-134">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85f5e-135">要件</span><span class="sxs-lookup"><span data-stu-id="85f5e-135">Requirements</span></span>  

 <span data-ttu-id="85f5e-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85f5e-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85f5e-137">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85f5e-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85f5e-138">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85f5e-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85f5e-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85f5e-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85f5e-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="85f5e-140">See also</span></span>

- [<span data-ttu-id="85f5e-141">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="85f5e-141">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="85f5e-142">デバッグ</span><span class="sxs-lookup"><span data-stu-id="85f5e-142">Debugging</span></span>](index.md)
