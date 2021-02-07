---
description: '詳細については、次のページを参照してください: を参照'
title: ICorDebugExceptionDebugEvent::GetNativeIP メソッド
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 89bda36efc59e2462634c3d8a3a5835c9d4b3354
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693461"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="906af-103">ICorDebugExceptionDebugEvent::GetNativeIP メソッド</span><span class="sxs-lookup"><span data-stu-id="906af-103">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>

<span data-ttu-id="906af-104">この例外デバッグ イベントのネイティブ命令ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="906af-104">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="906af-105">構文</span><span class="sxs-lookup"><span data-stu-id="906af-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="906af-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="906af-106">Parameters</span></span>  

 `pIP`  
 <span data-ttu-id="906af-107">[out] この例外デバッグ イベントのネイティブ命令ポインターに対するポインター。</span><span class="sxs-lookup"><span data-stu-id="906af-107">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="906af-108">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="906af-108">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="906af-109">解説</span><span class="sxs-lookup"><span data-stu-id="906af-109">Remarks</span></span>  

 <span data-ttu-id="906af-110">この命令ポインターの意味は、次の表に示すように、イベントの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="906af-110">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="906af-111">イベントの種類</span><span class="sxs-lookup"><span data-stu-id="906af-111">Event type</span></span>|<span data-ttu-id="906af-112">`pStackPointer` 値の意味</span><span class="sxs-lookup"><span data-stu-id="906af-112">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="906af-113">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="906af-113">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="906af-114">障害の発生した命令のアドレス。</span><span class="sxs-lookup"><span data-stu-id="906af-114">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="906af-115">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="906af-115">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="906af-116">例外が発生しなかった場合に実行が再開される、 [Getstackpointer](icordebugexceptiondebugevent-getstackpointer-method.md) メソッドによって示されるフレーム内のコードアドレス。</span><span class="sxs-lookup"><span data-stu-id="906af-116">The code address in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="906af-117">例外によって、`try/catch/finally` 句の catch ブロックなどの別のコードがこのフレーム内で実行される原因となることもあれば、そうでない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="906af-117">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="906af-118">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="906af-118">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="906af-119">`catch` [Getstackpointer](icordebugexceptiondebugevent-getstackpointer-method.md)メソッドによって示されるフレーム内でハンドラーの実行が開始されるコードアドレス。</span><span class="sxs-lookup"><span data-stu-id="906af-119">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="906af-120">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="906af-120">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="906af-121">`pIP` が 0 です。</span><span class="sxs-lookup"><span data-stu-id="906af-121">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="906af-122">イベントの種類は、[テキスト形式の [イベント:: GetEventKind](icordebugdebugevent-geteventkind-method.md) メソッドから取得できます。</span><span class="sxs-lookup"><span data-stu-id="906af-122">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="906af-123">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="906af-123">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="906af-124">要件</span><span class="sxs-lookup"><span data-stu-id="906af-124">Requirements</span></span>  

 <span data-ttu-id="906af-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="906af-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="906af-126">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="906af-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="906af-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="906af-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="906af-128">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="906af-128">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="906af-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="906af-129">See also</span></span>

- [<span data-ttu-id="906af-130">ICorDebugExceptionDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="906af-130">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="906af-131">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="906af-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
