---
description: '詳細については、次を参照してください: を参照'
title: ICorDebugExceptionDebugEvent インターフェイス
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
ms.openlocfilehash: eacaa344763fb77faef5f66282809d741f017b37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693422"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="ff685-103">ICorDebugExceptionDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ff685-103">ICorDebugExceptionDebugEvent Interface</span></span>

<span data-ttu-id="ff685-104">は、例外イベントをサポートするために、の [イベント](icordebugdebugevent-interface.md) インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="ff685-104">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ff685-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ff685-105">Methods</span></span>  
  
|<span data-ttu-id="ff685-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="ff685-106">Method</span></span>|<span data-ttu-id="ff685-107">説明</span><span class="sxs-lookup"><span data-stu-id="ff685-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ff685-108">GetFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="ff685-108">GetFlags Method</span></span>](icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="ff685-109">例外をインターセプトできるかどうかを示すフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="ff685-109">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="ff685-110">GetNativeIP メソッド</span><span class="sxs-lookup"><span data-stu-id="ff685-110">GetNativeIP Method</span></span>](icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="ff685-111">この例外デバッグ イベントのネイティブ インターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="ff685-111">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="ff685-112">GetStackPointer メソッド</span><span class="sxs-lookup"><span data-stu-id="ff685-112">GetStackPointer Method</span></span>](icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="ff685-113">この例外デバッグ イベントのスタック ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="ff685-113">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff685-114">解説</span><span class="sxs-lookup"><span data-stu-id="ff685-114">Remarks</span></span>  

 <span data-ttu-id="ff685-115">`ICorDebugExceptionDebugEvent` インターフェイスは、次のイベントの種類によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="ff685-115">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="ff685-116">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="ff685-116">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="ff685-117">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="ff685-117">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="ff685-118">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="ff685-118">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="ff685-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="ff685-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="ff685-120">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="ff685-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="ff685-121">インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。</span><span class="sxs-lookup"><span data-stu-id="ff685-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff685-122">要件</span><span class="sxs-lookup"><span data-stu-id="ff685-122">Requirements</span></span>  

 <span data-ttu-id="ff685-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff685-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff685-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff685-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff685-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff685-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff685-126">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff685-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff685-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff685-127">See also</span></span>

- [<span data-ttu-id="ff685-128">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ff685-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ff685-129">デバッグ</span><span class="sxs-lookup"><span data-stu-id="ff685-129">Debugging</span></span>](index.md)
