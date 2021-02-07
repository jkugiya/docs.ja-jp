---
description: '詳細情報: テキスト枠インターフェイス'
title: ICorDebugFrame インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
ms.openlocfilehash: d0fd629672d535f89fe78c178032937443d9dfbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692850"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="2b56f-103">ICorDebugFrame インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b56f-103">ICorDebugFrame Interface</span></span>

<span data-ttu-id="2b56f-104">現在のスタックのフレームを表します。</span><span class="sxs-lookup"><span data-stu-id="2b56f-104">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2b56f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="2b56f-105">Methods</span></span>  
  
|<span data-ttu-id="2b56f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="2b56f-106">Method</span></span>|<span data-ttu-id="2b56f-107">説明</span><span class="sxs-lookup"><span data-stu-id="2b56f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2b56f-108">CreateStepper メソッド</span><span class="sxs-lookup"><span data-stu-id="2b56f-108">CreateStepper Method</span></span>](icordebugframe-createstepper-method.md)|<span data-ttu-id="2b56f-109">このに対して相対的なステップ実行操作を実行する ICorDebugStepper を取得し `ICorDebugFrame` ます。</span><span class="sxs-lookup"><span data-stu-id="2b56f-109">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="2b56f-110">GetCallee メソッド</span><span class="sxs-lookup"><span data-stu-id="2b56f-110">GetCallee Method</span></span>](icordebugframe-getcallee-method.md)|<span data-ttu-id="2b56f-111">このフレームが呼び出された現在のチェーン内のへのポインターを取得し `ICorDebugFrame` ます。または、このがチェーン内の最も内側のフレームである場合は null を返します。</span><span class="sxs-lookup"><span data-stu-id="2b56f-111">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="2b56f-112">GetCaller メソッド</span><span class="sxs-lookup"><span data-stu-id="2b56f-112">GetCaller Method</span></span>](icordebugframe-getcaller-method.md)|<span data-ttu-id="2b56f-113">このフレームを呼び出した現在のチェーン内のへのポインターを取得し `ICorDebugFrame` ます。これがチェーンの最も外側のフレームである場合は null を返します。</span><span class="sxs-lookup"><span data-stu-id="2b56f-113">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="2b56f-114">GetChain メソッド</span><span class="sxs-lookup"><span data-stu-id="2b56f-114">GetChain Method</span></span>](icordebugframe-getchain-method.md)|<span data-ttu-id="2b56f-115">このが含まれている、ツールチェーンへのポインターを取得し `ICorDebugFrame` ます。</span><span class="sxs-lookup"><span data-stu-id="2b56f-115">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="2b56f-116">GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="2b56f-116">GetCode Method</span></span>](icordebugframe-getcode-method.md)|<span data-ttu-id="2b56f-117">このスタックフレームに関連付けられているテキストコードへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="2b56f-117">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="2b56f-118">GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="2b56f-118">GetFunction Method</span></span>](icordebugframe-getfunction-method.md)|<span data-ttu-id="2b56f-119">このスタックフレームに関連付けられているコードを格納しているコードを指すポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="2b56f-119">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="2b56f-120">GetFunctionToken メソッド</span><span class="sxs-lookup"><span data-stu-id="2b56f-120">GetFunctionToken Method</span></span>](icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="2b56f-121">このスタックフレームに関連付けられているコードを含む関数のメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="2b56f-121">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="2b56f-122">GetStackRange メソッド</span><span class="sxs-lookup"><span data-stu-id="2b56f-122">GetStackRange Method</span></span>](icordebugframe-getstackrange-method.md)|<span data-ttu-id="2b56f-123">このによって表されるスタックフレームの絶対アドレス範囲を取得し `ICorDebugFrame` ます。</span><span class="sxs-lookup"><span data-stu-id="2b56f-123">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b56f-124">解説</span><span class="sxs-lookup"><span data-stu-id="2b56f-124">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b56f-125">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="2b56f-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b56f-126">要件</span><span class="sxs-lookup"><span data-stu-id="2b56f-126">Requirements</span></span>  

 <span data-ttu-id="2b56f-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b56f-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b56f-128">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b56f-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b56f-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b56f-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b56f-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b56f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b56f-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b56f-131">See also</span></span>

- [<span data-ttu-id="2b56f-132">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b56f-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
