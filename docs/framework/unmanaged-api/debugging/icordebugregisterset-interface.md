---
description: '詳細情報: いいね!'
title: ICorDebugRegisterSet インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
ms.openlocfilehash: 7d888e9e395e9f5fa88c6a6d96b2b8e3171ef4ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690783"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="99593-103">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99593-103">ICorDebugRegisterSet Interface</span></span>

<span data-ttu-id="99593-104">現在コードを実行しているコンピューターで使用できるレジスタのセットを表します。</span><span class="sxs-lookup"><span data-stu-id="99593-104">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99593-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="99593-105">Methods</span></span>  
  
|<span data-ttu-id="99593-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="99593-106">Method</span></span>|<span data-ttu-id="99593-107">説明</span><span class="sxs-lookup"><span data-stu-id="99593-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99593-108">GetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="99593-108">GetRegisters Method</span></span>](icordebugregisterset-getregisters-method.md)|<span data-ttu-id="99593-109">ビットマスクによって指定された、(現在コードを実行しているコンピューター上の) 各レジスタの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="99593-109">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="99593-110">GetRegistersAvailable メソッド</span><span class="sxs-lookup"><span data-stu-id="99593-110">GetRegistersAvailable Method</span></span>](icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="99593-111">現在使用できるレジスタを示すビットマスクを取得し `ICorDebugRegisterSet` ます。</span><span class="sxs-lookup"><span data-stu-id="99593-111">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="99593-112">GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="99593-112">GetThreadContext Method</span></span>](icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="99593-113">現在のスレッドのコンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="99593-113">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="99593-114">SetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="99593-114">SetRegisters Method</span></span>](icordebugregisterset-setregisters-method.md)|<span data-ttu-id="99593-115">.NET Framework バージョン2.0 には実装されていません。</span><span class="sxs-lookup"><span data-stu-id="99593-115">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="99593-116">SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="99593-116">SetThreadContext Method</span></span>](icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="99593-117">.NET Framework 2.0 には実装されていません。</span><span class="sxs-lookup"><span data-stu-id="99593-117">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99593-118">解説</span><span class="sxs-lookup"><span data-stu-id="99593-118">Remarks</span></span>  

 <span data-ttu-id="99593-119">インターフェイスでは、 `ICorDebugRegisterSet` 32 ビットレジスタのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="99593-119">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="99593-120">追加のレジスタを必要とする IA-64 などのプラットフォームで [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) インターフェイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="99593-120">Use the [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99593-121">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="99593-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99593-122">要件</span><span class="sxs-lookup"><span data-stu-id="99593-122">Requirements</span></span>  

 <span data-ttu-id="99593-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99593-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99593-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99593-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99593-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99593-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99593-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99593-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99593-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="99593-127">See also</span></span>

- [<span data-ttu-id="99593-128">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="99593-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="99593-129">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99593-129">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
