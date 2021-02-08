---
description: '詳細情報: テキストの表示'
title: ICorDebugILFrame インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
ms.openlocfilehash: 251fa18151ff286bee3e1bcf7707bf5f7145b4f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791349"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="99068-103">ICorDebugILFrame インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99068-103">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="99068-104">Microsoft 中間言語 (MSIL) コードのスタックフレームを表します。</span><span class="sxs-lookup"><span data-stu-id="99068-104">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="99068-105">このインターフェイスは、テキストボックスのインターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="99068-105">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99068-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="99068-106">Methods</span></span>  
  
|<span data-ttu-id="99068-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="99068-107">Method</span></span>|<span data-ttu-id="99068-108">説明</span><span class="sxs-lookup"><span data-stu-id="99068-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99068-109">CanSetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="99068-109">CanSetIP Method</span></span>](icordebugilframe-cansetip-method.md)|<span data-ttu-id="99068-110">命令ポインターを指定したオフセット位置に安全に設定できるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="99068-110">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="99068-111">EnumerateArguments メソッド</span><span class="sxs-lookup"><span data-stu-id="99068-111">EnumerateArguments Method</span></span>](icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="99068-112">このフレーム内の引数の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="99068-112">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="99068-113">EnumerateLocalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="99068-113">EnumerateLocalVariables Method</span></span>](icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="99068-114">このフレーム内のローカル変数の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="99068-114">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="99068-115">GetArgument メソッド</span><span class="sxs-lookup"><span data-stu-id="99068-115">GetArgument Method</span></span>](icordebugilframe-getargument-method.md)|<span data-ttu-id="99068-116">この MSIL スタックフレーム内の指定された引数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="99068-116">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="99068-117">GetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="99068-117">GetIP Method</span></span>](icordebugilframe-getip-method.md)|<span data-ttu-id="99068-118">命令ポインターの値と、命令ポインターの値が取得された方法を示すビットごとの組み合わせ値を取得します。</span><span class="sxs-lookup"><span data-stu-id="99068-118">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="99068-119">GetLocalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="99068-119">GetLocalVariable Method</span></span>](icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="99068-120">この MSIL スタックフレーム内の指定したローカル変数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="99068-120">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="99068-121">GetStackDepth メソッド</span><span class="sxs-lookup"><span data-stu-id="99068-121">GetStackDepth Method</span></span>](icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="99068-122">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="99068-122">Not implemented.</span></span>|  
|[<span data-ttu-id="99068-123">GetStackValue メソッド</span><span class="sxs-lookup"><span data-stu-id="99068-123">GetStackValue Method</span></span>](icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="99068-124">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="99068-124">Not implemented.</span></span>|  
|[<span data-ttu-id="99068-125">SetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="99068-125">SetIP Method</span></span>](icordebugilframe-setip-method.md)|<span data-ttu-id="99068-126">命令ポインターを MSIL コード内の指定したオフセット位置に設定します。</span><span class="sxs-lookup"><span data-stu-id="99068-126">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99068-127">解説</span><span class="sxs-lookup"><span data-stu-id="99068-127">Remarks</span></span>  

 <span data-ttu-id="99068-128">インターフェイスは、 `ICorDebugILFrame` 特別なテキストフレームインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="99068-128">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="99068-129">これは、MSIL コードフレームまたは just-in-time (JIT) コンパイルフレームに対して使用されます。</span><span class="sxs-lookup"><span data-stu-id="99068-129">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="99068-130">JIT でコンパイルされたフレームは、 `ICorDebugILFrame` インターフェイスとの両方のフレームインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="99068-130">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99068-131">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="99068-131">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99068-132">要件</span><span class="sxs-lookup"><span data-stu-id="99068-132">Requirements</span></span>  

 <span data-ttu-id="99068-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99068-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99068-134">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99068-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99068-135">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99068-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99068-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99068-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99068-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="99068-137">See also</span></span>

- [<span data-ttu-id="99068-138">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="99068-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
