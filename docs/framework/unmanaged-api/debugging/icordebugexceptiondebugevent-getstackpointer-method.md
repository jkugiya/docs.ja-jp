---
description: '詳細については、次のページを参照してください: を参照'
title: ICorDebugExceptionDebugEvent::GetStackPointer メソッド
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
ms.openlocfilehash: 5a62a5eb54fff1e94beebc222e3f18cc4655040f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693448"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="c607b-103">ICorDebugExceptionDebugEvent::GetStackPointer メソッド</span><span class="sxs-lookup"><span data-stu-id="c607b-103">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>

<span data-ttu-id="c607b-104">この例外デバッグ イベントのスタック ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c607b-104">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c607b-105">構文</span><span class="sxs-lookup"><span data-stu-id="c607b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c607b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c607b-106">Parameters</span></span>  

 `pStackPointer`  
 <span data-ttu-id="c607b-107">[out] この例外デバッグ イベントのスタック ポインターのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c607b-107">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="c607b-108">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c607b-108">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c607b-109">解説</span><span class="sxs-lookup"><span data-stu-id="c607b-109">Remarks</span></span>  

 <span data-ttu-id="c607b-110">このスタック ポインターの意味は、次の表に示すように、イベントの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="c607b-110">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="c607b-111">イベントの種類</span><span class="sxs-lookup"><span data-stu-id="c607b-111">Event type</span></span>|<span data-ttu-id="c607b-112">`pStackPointer` 値の意味</span><span class="sxs-lookup"><span data-stu-id="c607b-112">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="c607b-113">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="c607b-113">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="c607b-114">例外をスローしたフレームのスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="c607b-114">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="c607b-115">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="c607b-115">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="c607b-116">スローされた例外の位置に最も近いユーザー コード フレームのスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="c607b-116">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="c607b-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="c607b-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="c607b-118">catch ハンドラーを含むフレームのスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="c607b-118">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="c607b-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="c607b-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="c607b-120">`pStackPointer` が **null** です。</span><span class="sxs-lookup"><span data-stu-id="c607b-120">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="c607b-121">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c607b-121">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="c607b-122">イベントの種類は、[テキスト形式の [イベント:: GetEventKind](icordebugdebugevent-geteventkind-method.md) メソッドから取得できます。</span><span class="sxs-lookup"><span data-stu-id="c607b-122">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c607b-123">要件</span><span class="sxs-lookup"><span data-stu-id="c607b-123">Requirements</span></span>  

 <span data-ttu-id="c607b-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c607b-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c607b-125">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c607b-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c607b-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c607b-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c607b-127">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c607b-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c607b-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="c607b-128">See also</span></span>

- [<span data-ttu-id="c607b-129">ICorDebugExceptionDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c607b-129">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="c607b-130">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c607b-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
