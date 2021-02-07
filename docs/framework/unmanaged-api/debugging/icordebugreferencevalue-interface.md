---
description: '詳細については、次を参照してください: の値インターフェイス'
title: ICorDebugReferenceValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
ms.openlocfilehash: e516b1178b4f4268472dedd37d6443e673e16af6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690965"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="942e0-103">ICorDebugReferenceValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="942e0-103">ICorDebugReferenceValue Interface</span></span>

<span data-ttu-id="942e0-104">オブジェクトへの参照である値を管理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="942e0-104">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="942e0-105">(つまり、このインターフェイスには、ポインターを管理するメソッドが用意されています)。このインターフェイスは、"ICorDebugValue" を実装します。</span><span class="sxs-lookup"><span data-stu-id="942e0-105">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="942e0-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="942e0-106">Methods</span></span>  
  
|<span data-ttu-id="942e0-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="942e0-107">Method</span></span>|<span data-ttu-id="942e0-108">説明</span><span class="sxs-lookup"><span data-stu-id="942e0-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="942e0-109">Dereference メソッド</span><span class="sxs-lookup"><span data-stu-id="942e0-109">Dereference Method</span></span>](icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="942e0-110">参照されているオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="942e0-110">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="942e0-111">DereferenceStrong メソッド</span><span class="sxs-lookup"><span data-stu-id="942e0-111">DereferenceStrong Method</span></span>](icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="942e0-112">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="942e0-112">Not implemented.</span></span> <span data-ttu-id="942e0-113">このメソッドは呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="942e0-113">Do not call this method.</span></span>|  
|[<span data-ttu-id="942e0-114">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="942e0-114">GetValue Method</span></span>](icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="942e0-115">参照先のオブジェクトの現在のメモリアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="942e0-115">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="942e0-116">IsNull メソッド</span><span class="sxs-lookup"><span data-stu-id="942e0-116">IsNull Method</span></span>](icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="942e0-117">このが null 値であるかどうかを示す値を取得します。この値を指定した `ICorDebugReferenceValue` 場合、は `ICorDebugReferenceValue` オブジェクトをポイントしません。</span><span class="sxs-lookup"><span data-stu-id="942e0-117">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="942e0-118">SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="942e0-118">SetValue Method</span></span>](icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="942e0-119">現在のメモリアドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="942e0-119">Sets the current memory address.</span></span> <span data-ttu-id="942e0-120">つまり、このメソッドは、 `ICorDebugReferenceValue` オブジェクトを指すようにこれを設定します。</span><span class="sxs-lookup"><span data-stu-id="942e0-120">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="942e0-121">解説</span><span class="sxs-lookup"><span data-stu-id="942e0-121">Remarks</span></span>  

 <span data-ttu-id="942e0-122">共通言語ランタイム (CLR) は、デバッグされたプロセスが続行されると、オブジェクトのガベージコレクションを実行する場合があります。</span><span class="sxs-lookup"><span data-stu-id="942e0-122">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="942e0-123">ガベージコレクションでは、メモリ内でオブジェクトを移動できます。</span><span class="sxs-lookup"><span data-stu-id="942e0-123">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="942e0-124">はガベージコレクションと連携して、ガベージコレクション `ICorDebugReferenceValue` の後に情報が更新されるか、ガベージコレクションの前に暗黙的に無効にされます。</span><span class="sxs-lookup"><span data-stu-id="942e0-124">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="942e0-125">`ICorDebugReferenceValue`デバッグされたプロセスが続行されると、オブジェクトは暗黙的に無効になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="942e0-125">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="942e0-126">派生された "の値" は、明示的に解放または公開されるまで無効になりません。</span><span class="sxs-lookup"><span data-stu-id="942e0-126">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="942e0-127">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="942e0-127">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="942e0-128">要件</span><span class="sxs-lookup"><span data-stu-id="942e0-128">Requirements</span></span>  

 <span data-ttu-id="942e0-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="942e0-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="942e0-130">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="942e0-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="942e0-131">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="942e0-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="942e0-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="942e0-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="942e0-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="942e0-133">See also</span></span>

- [<span data-ttu-id="942e0-134">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="942e0-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
