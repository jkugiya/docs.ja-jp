---
description: 詳細については、「ICorDebugVirtualUnwinder インターフェイス」を参照してください。
title: ICorDebugVirtualUnwinder インターフェイス
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: e941ace2e7f72c9f7956c03bae19f9b92094b338
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738079"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="0fcd4-103">ICorDebugVirtualUnwinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0fcd4-103">ICorDebugVirtualUnwinder Interface</span></span>

<span data-ttu-id="0fcd4-104">スタック アンワインドを支援するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="0fcd4-104">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0fcd4-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="0fcd4-105">Methods</span></span>  
  
|<span data-ttu-id="0fcd4-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="0fcd4-106">Method</span></span>|<span data-ttu-id="0fcd4-107">名前</span><span class="sxs-lookup"><span data-stu-id="0fcd4-107">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="0fcd4-108">GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="0fcd4-108">GetContext Method</span></span>](icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="0fcd4-109">このアンワインダーの現在のコンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="0fcd4-109">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="0fcd4-110">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="0fcd4-110">Next Method</span></span>](icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="0fcd4-111">呼び出し元のコンテキストに進みます。</span><span class="sxs-lookup"><span data-stu-id="0fcd4-111">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fcd4-112">解説</span><span class="sxs-lookup"><span data-stu-id="0fcd4-112">Remarks</span></span>  

 <span data-ttu-id="0fcd4-113">スタック アンワインドを支援するため、`ICorDebugVirtualUnwinder` インターフェイスのメンバーがデバッガーにより実装されます。</span><span class="sxs-lookup"><span data-stu-id="0fcd4-113">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0fcd4-114">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="0fcd4-114">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0fcd4-115">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="0fcd4-115">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fcd4-116">要件</span><span class="sxs-lookup"><span data-stu-id="0fcd4-116">Requirements</span></span>  

 <span data-ttu-id="0fcd4-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fcd4-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fcd4-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0fcd4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0fcd4-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fcd4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fcd4-120">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fcd4-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fcd4-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="0fcd4-121">See also</span></span>

- [<span data-ttu-id="0fcd4-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="0fcd4-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0fcd4-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="0fcd4-123">Debugging</span></span>](index.md)
