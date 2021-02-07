---
description: '詳細情報: の説明'
title: ICorDebugChain インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
ms.openlocfilehash: 391c9a3e54d06d303728da5ab7f105bc8e2558ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661208"
---
# <a name="icordebugchain-interface"></a><span data-ttu-id="1ced0-103">ICorDebugChain インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1ced0-103">ICorDebugChain Interface</span></span>

<span data-ttu-id="1ced0-104">物理呼び出し履歴または論理呼び出し履歴のセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="1ced0-104">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1ced0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1ced0-105">Methods</span></span>  
  
|<span data-ttu-id="1ced0-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="1ced0-106">Method</span></span>|<span data-ttu-id="1ced0-107">説明</span><span class="sxs-lookup"><span data-stu-id="1ced0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1ced0-108">EnumerateFrames メソッド</span><span class="sxs-lookup"><span data-stu-id="1ced0-108">EnumerateFrames Method</span></span>](icordebugchain-enumerateframes-method.md)|<span data-ttu-id="1ced0-109">チェーン内のすべてのマネージスタックフレームが格納された列挙子を取得します。これは、最新のフレームから始まります。</span><span class="sxs-lookup"><span data-stu-id="1ced0-109">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="1ced0-110">GetActiveFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="1ced0-110">GetActiveFrame Method</span></span>](icordebugchain-getactiveframe-method.md)|<span data-ttu-id="1ced0-111">チェーンのアクティブな (つまり、最新の) フレームを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ced0-111">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="1ced0-112">GetCallee メソッド</span><span class="sxs-lookup"><span data-stu-id="1ced0-112">GetCallee Method</span></span>](icordebugchain-getcallee-method.md)|<span data-ttu-id="1ced0-113">このチェーンによって呼び出されたチェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ced0-113">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="1ced0-114">GetCaller メソッド</span><span class="sxs-lookup"><span data-stu-id="1ced0-114">GetCaller Method</span></span>](icordebugchain-getcaller-method.md)|<span data-ttu-id="1ced0-115">このチェーンを呼び出したチェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ced0-115">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="1ced0-116">GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="1ced0-116">GetContext Method</span></span>](icordebugchain-getcontext-method.md)|<span data-ttu-id="1ced0-117">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="1ced0-117">Not implemented.</span></span>|  
|[<span data-ttu-id="1ced0-118">GetNext メソッド</span><span class="sxs-lookup"><span data-stu-id="1ced0-118">GetNext Method</span></span>](icordebugchain-getnext-method.md)|<span data-ttu-id="1ced0-119">スレッドの次のフレームのチェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ced0-119">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="1ced0-120">GetPrevious メソッド</span><span class="sxs-lookup"><span data-stu-id="1ced0-120">GetPrevious Method</span></span>](icordebugchain-getprevious-method.md)|<span data-ttu-id="1ced0-121">スレッドの前のフレームのチェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ced0-121">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="1ced0-122">GetReason メソッド</span><span class="sxs-lookup"><span data-stu-id="1ced0-122">GetReason Method</span></span>](icordebugchain-getreason-method.md)|<span data-ttu-id="1ced0-123">この呼び出しチェーンの genesis の理由を取得します。</span><span class="sxs-lookup"><span data-stu-id="1ced0-123">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="1ced0-124">GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="1ced0-124">GetRegisterSet Method</span></span>](icordebugchain-getregisterset-method.md)|<span data-ttu-id="1ced0-125">このチェーンのアクティブな部分のレジスタセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ced0-125">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="1ced0-126">GetStackRange メソッド</span><span class="sxs-lookup"><span data-stu-id="1ced0-126">GetStackRange Method</span></span>](icordebugchain-getstackrange-method.md)|<span data-ttu-id="1ced0-127">このチェーンのスタックセグメントのアドレス範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="1ced0-127">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="1ced0-128">GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="1ced0-128">GetThread Method</span></span>](icordebugchain-getthread-method.md)|<span data-ttu-id="1ced0-129">この呼び出しチェーンが含まれている物理スレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ced0-129">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="1ced0-130">IsManaged メソッド</span><span class="sxs-lookup"><span data-stu-id="1ced0-130">IsManaged Method</span></span>](icordebugchain-ismanaged-method.md)|<span data-ttu-id="1ced0-131">このチェーンでマネージコードが実行されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="1ced0-131">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ced0-132">解説</span><span class="sxs-lookup"><span data-stu-id="1ced0-132">Remarks</span></span>  

 <span data-ttu-id="1ced0-133">チェーン内のスタックフレームは、連続したスタック領域を占有し、同じスレッドとコンテキストを共有します。</span><span class="sxs-lookup"><span data-stu-id="1ced0-133">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="1ced0-134">チェーンは、マネージコードチェーンまたはアンマネージコードチェーンを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="1ced0-134">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="1ced0-135">空 `ICorDebugChain` のインスタンスは、アンマネージコードチェーンを表します。</span><span class="sxs-lookup"><span data-stu-id="1ced0-135">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ced0-136">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1ced0-136">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ced0-137">要件</span><span class="sxs-lookup"><span data-stu-id="1ced0-137">Requirements</span></span>  

 <span data-ttu-id="1ced0-138">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ced0-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ced0-139">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ced0-139">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ced0-140">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ced0-140">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ced0-141">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ced0-141">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ced0-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ced0-142">See also</span></span>

- [<span data-ttu-id="1ced0-143">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1ced0-143">Debugging Interfaces</span></span>](debugging-interfaces.md)
