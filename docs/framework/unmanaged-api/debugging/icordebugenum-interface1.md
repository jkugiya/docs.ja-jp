---
description: 詳細については、「ICorDebugEnum インターフェイス」を参照してください。
title: ICorDebugEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
ms.openlocfilehash: 20d2bb14bddcaf40802567ec78a8e318ac1db380
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694475"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="9e72e-103">ICorDebugEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e72e-103">ICorDebugEnum Interface</span></span>

<span data-ttu-id="9e72e-104">デバッグアプリケーションで使用される列挙子の抽象基本インターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="9e72e-104">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e72e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9e72e-105">Methods</span></span>  
  
|<span data-ttu-id="9e72e-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="9e72e-106">Method</span></span>|<span data-ttu-id="9e72e-107">説明</span><span class="sxs-lookup"><span data-stu-id="9e72e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e72e-108">Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="9e72e-108">Clone Method</span></span>](icordebugenum-clone-method.md)|<span data-ttu-id="9e72e-109">この `ICorDebugEnum` オブジェクトのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="9e72e-109">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="9e72e-110">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="9e72e-110">GetCount Method</span></span>](icordebugenum-getcount-method.md)|<span data-ttu-id="9e72e-111">列挙に含まれる項目の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="9e72e-111">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="9e72e-112">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="9e72e-112">Reset Method</span></span>](icordebugenum-reset-method.md)|<span data-ttu-id="9e72e-113">カーソルを列挙体の先頭に移動します。</span><span class="sxs-lookup"><span data-stu-id="9e72e-113">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="9e72e-114">Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="9e72e-114">Skip Method</span></span>](icordebugenum-skip-method.md)|<span data-ttu-id="9e72e-115">指定した数の項目だけ、列挙内でカーソルを前方に移動します。</span><span class="sxs-lookup"><span data-stu-id="9e72e-115">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e72e-116">解説</span><span class="sxs-lookup"><span data-stu-id="9e72e-116">Remarks</span></span>  

 <span data-ttu-id="9e72e-117">次の列挙子は、から派生し `ICorDebugEnum` ます。</span><span class="sxs-lookup"><span data-stu-id="9e72e-117">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="9e72e-118">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-118">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="9e72e-119">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-119">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="9e72e-120">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-120">ICorDebugBlockingObjectEnum</span></span>](icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="9e72e-121">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-121">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="9e72e-122">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-122">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="9e72e-123">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-123">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="9e72e-124">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-124">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="9e72e-125">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-125">ICorDebugExceptionObjectCallStackEnum</span></span>](icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="9e72e-126">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-126">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="9e72e-127">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-127">ICorDebugGCReferenceEnum</span></span>](icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="9e72e-128">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-128">ICorDebugGuidToTypeEnum</span></span>](icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="9e72e-129">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-129">ICorDebugHeapEnum</span></span>](icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="9e72e-130">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-130">ICorDebugHeapSegmentEnum</span></span>](icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="9e72e-131">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-131">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="9e72e-132">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-132">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="9e72e-133">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-133">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="9e72e-134">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-134">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="9e72e-135">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-135">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="9e72e-136">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-136">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="9e72e-137">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-137">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="9e72e-138">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="9e72e-138">ICorDebugVariableHomeEnum</span></span>](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="9e72e-139">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9e72e-139">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e72e-140">要件</span><span class="sxs-lookup"><span data-stu-id="9e72e-140">Requirements</span></span>  

 <span data-ttu-id="9e72e-141">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e72e-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e72e-142">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e72e-142">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e72e-143">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e72e-143">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e72e-144">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e72e-144">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e72e-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e72e-145">See also</span></span>

- [<span data-ttu-id="9e72e-146">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e72e-146">Debugging Interfaces</span></span>](debugging-interfaces.md)
