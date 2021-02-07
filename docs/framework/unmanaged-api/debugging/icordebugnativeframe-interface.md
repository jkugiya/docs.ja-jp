---
description: '詳細情報: テキストボックスのインターフェイス'
title: ICorDebugNativeFrame インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
ms.openlocfilehash: e417184c9f1ca5136e1b4dba07820fd8242ae932
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729134"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="60a2d-103">ICorDebugNativeFrame インターフェイス</span><span class="sxs-lookup"><span data-stu-id="60a2d-103">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="60a2d-104">ネイティブフレームに使用される、特殊な実装のテキストフレーム。</span><span class="sxs-lookup"><span data-stu-id="60a2d-104">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="60a2d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="60a2d-105">Methods</span></span>  
  
|<span data-ttu-id="60a2d-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="60a2d-106">Method</span></span>|<span data-ttu-id="60a2d-107">説明</span><span class="sxs-lookup"><span data-stu-id="60a2d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="60a2d-108">CanSetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="60a2d-108">CanSetIP Method</span></span>](icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="60a2d-109">命令ポインターをネイティブコード内の指定したオフセット位置に安全に設定できるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="60a2d-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="60a2d-110">GetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="60a2d-110">GetIP Method</span></span>](icordebugnativeframe-getip-method.md)|<span data-ttu-id="60a2d-111">ネイティブコードへのスタックフレームのオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="60a2d-111">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="60a2d-112">GetLocalDoubleRegisterValue メソッド</span><span class="sxs-lookup"><span data-stu-id="60a2d-112">GetLocalDoubleRegisterValue Method</span></span>](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="60a2d-113">ネイティブフレームの2つのメモリレジスタに格納されている引数またはローカル変数の値を表す ICorDebugValue へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="60a2d-113">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="60a2d-114">GetLocalMemoryRegisterValue メソッド</span><span class="sxs-lookup"><span data-stu-id="60a2d-114">GetLocalMemoryRegisterValue Method</span></span>](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="60a2d-115">指定した `ICorDebugValue` レジスタに下位ビットが格納されているローカル変数の値を表すへのポインターを取得します。上位ビットは、指定したメモリアドレスに格納されます。</span><span class="sxs-lookup"><span data-stu-id="60a2d-115">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="60a2d-116">GetLocalMemoryValue メソッド</span><span class="sxs-lookup"><span data-stu-id="60a2d-116">GetLocalMemoryValue Method</span></span>](icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="60a2d-117">`ICorDebugValue`指定したメモリアドレスに格納されているローカル変数の値を表すへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="60a2d-117">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="60a2d-118">GetLocalRegisterMemoryValue メソッド</span><span class="sxs-lookup"><span data-stu-id="60a2d-118">GetLocalRegisterMemoryValue Method</span></span>](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="60a2d-119">指定した `ICorDebugValue` レジスタに上位ビットが格納され、下位ビットが指定したメモリアドレスに格納されているローカル変数の値を表すへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="60a2d-119">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="60a2d-120">GetLocalRegisterValue メソッド</span><span class="sxs-lookup"><span data-stu-id="60a2d-120">GetLocalRegisterValue Method</span></span>](icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="60a2d-121">`ICorDebugValue`引数の値または指定したネイティブレジスタに格納されているローカル変数を表すへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="60a2d-121">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="60a2d-122">GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="60a2d-122">GetRegisterSet Method</span></span>](icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="60a2d-123">こののレジスタセットを表す、ツール [のセットへ](icordebugregisterset-interface.md) のポインターを取得し `ICorDebugNativeFrame` ます。</span><span class="sxs-lookup"><span data-stu-id="60a2d-123">Gets a pointer to an [ICorDebugRegisterSet](icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="60a2d-124">SetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="60a2d-124">SetIP Method</span></span>](icordebugnativeframe-setip-method.md)|<span data-ttu-id="60a2d-125">命令ポインターをネイティブコード内の指定されたオフセット位置に設定します。</span><span class="sxs-lookup"><span data-stu-id="60a2d-125">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60a2d-126">解説</span><span class="sxs-lookup"><span data-stu-id="60a2d-126">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60a2d-127">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="60a2d-127">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60a2d-128">要件</span><span class="sxs-lookup"><span data-stu-id="60a2d-128">Requirements</span></span>  

 <span data-ttu-id="60a2d-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60a2d-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60a2d-130">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60a2d-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60a2d-131">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60a2d-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60a2d-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60a2d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60a2d-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="60a2d-133">See also</span></span>

- [<span data-ttu-id="60a2d-134">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="60a2d-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
