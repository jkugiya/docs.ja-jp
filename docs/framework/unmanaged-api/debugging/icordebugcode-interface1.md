---
description: '詳細情報: のコードインターフェイス'
title: ICorDebugCode インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
ms.openlocfilehash: ce67c48501783bbe00152f0ba2c224e6e7dde6d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711145"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="6454b-103">ICorDebugCode インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6454b-103">ICorDebugCode Interface</span></span>

<span data-ttu-id="6454b-104">Microsoft Intermediate Language (MSIL) コードまたはネイティブ コードのセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="6454b-104">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6454b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6454b-105">Methods</span></span>  
  
|<span data-ttu-id="6454b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="6454b-106">Method</span></span>|<span data-ttu-id="6454b-107">説明</span><span class="sxs-lookup"><span data-stu-id="6454b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6454b-108">CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="6454b-108">CreateBreakpoint Method</span></span>](icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="6454b-109">指定したオフセット位置にブレークポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="6454b-109">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="6454b-110">GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="6454b-110">GetAddress Method</span></span>](icordebugcode-getaddress-method.md)|<span data-ttu-id="6454b-111">この `ICorDebugCode` が表すコード セグメントの RVA (Relative Virtual Address) を取得します。</span><span class="sxs-lookup"><span data-stu-id="6454b-111">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="6454b-112">GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="6454b-112">GetCode Method</span></span>](icordebugcode-getcode-method.md)|<span data-ttu-id="6454b-113">指定した関数のすべてのコードを取得し、逆アセンブリ用に書式設定します。</span><span class="sxs-lookup"><span data-stu-id="6454b-113">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="6454b-114">このメソッドは非推奨とされました。代わりに [ICorDebugCode2:: GetCodeChunks](icordebugcode2-getcodechunks-method.md) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="6454b-114">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="6454b-115">GetEnCRemapSequencePoints メソッド</span><span class="sxs-lookup"><span data-stu-id="6454b-115">GetEnCRemapSequencePoints Method</span></span>](icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="6454b-116">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="6454b-116">Not implemented.</span></span>|  
|[<span data-ttu-id="6454b-117">GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="6454b-117">GetFunction Method</span></span>](icordebugcode-getfunction-method.md)|<span data-ttu-id="6454b-118">このに関連付けられている "の関数" を取得し `ICorDebugCode` ます。</span><span class="sxs-lookup"><span data-stu-id="6454b-118">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="6454b-119">GetILToNativeMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="6454b-119">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="6454b-120">MSIL オフセットからネイティブオフセットへのマッピングを表す "COR_DEBUG_IL_TO_NATIVE_MAP" インスタンスの配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="6454b-120">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="6454b-121">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="6454b-121">GetSize Method</span></span>](icordebugcode-getsize-method.md)|<span data-ttu-id="6454b-122">この `ICorDebugCode` で表されるバイナリ コードのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="6454b-122">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="6454b-123">GetVersionNumber メソッド</span><span class="sxs-lookup"><span data-stu-id="6454b-123">GetVersionNumber Method</span></span>](icordebugcode-getversionnumber-method.md)|<span data-ttu-id="6454b-124">この `ICorDebugCode` が表すコードのバージョンを識別する、1 から始まる数字を取得します。</span><span class="sxs-lookup"><span data-stu-id="6454b-124">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="6454b-125">IsIL メソッド</span><span class="sxs-lookup"><span data-stu-id="6454b-125">IsIL Method</span></span>](icordebugcode-isil-method.md)|<span data-ttu-id="6454b-126">この `ICorDebugCode` が MSIL でコンパイルされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="6454b-126">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6454b-127">解説</span><span class="sxs-lookup"><span data-stu-id="6454b-127">Remarks</span></span>  

 <span data-ttu-id="6454b-128">`ICorDebugCode` は、MSIL またはネイティブ コードを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="6454b-128">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="6454b-129">MSIL コードを表す "の関数" オブジェクトは、0個または1個 `ICorDebugCode` のオブジェクトを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="6454b-129">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="6454b-130">ネイティブコードを表す "表示関数" オブジェクトには、任意の数のオブジェクトを関連付けることができ `ICorDebugCode` ます。</span><span class="sxs-lookup"><span data-stu-id="6454b-130">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6454b-131">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="6454b-131">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6454b-132">要件</span><span class="sxs-lookup"><span data-stu-id="6454b-132">Requirements</span></span>  

 <span data-ttu-id="6454b-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6454b-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6454b-134">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6454b-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6454b-135">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6454b-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6454b-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6454b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6454b-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="6454b-137">See also</span></span>

- [<span data-ttu-id="6454b-138">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6454b-138">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="6454b-139">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6454b-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
