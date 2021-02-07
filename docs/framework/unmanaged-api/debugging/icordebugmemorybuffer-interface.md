---
description: '詳細については、次を参照してください: いい Memorybuffer インターフェイス'
title: ICorDebugMemoryBuffer インターフェイス
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 94eeb0f31c0e1c053fabbd556768fa65dda2d328
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754018"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="4f83f-103">ICorDebugMemoryBuffer インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f83f-103">ICorDebugMemoryBuffer Interface</span></span>

<span data-ttu-id="4f83f-104">メモリ内のバッファーを表します。</span><span class="sxs-lookup"><span data-stu-id="4f83f-104">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4f83f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="4f83f-105">Methods</span></span>  
  
|<span data-ttu-id="4f83f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="4f83f-106">Method</span></span>|<span data-ttu-id="4f83f-107">説明</span><span class="sxs-lookup"><span data-stu-id="4f83f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4f83f-108">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="4f83f-108">GetSize Method</span></span>](icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="4f83f-109">メモリ バッファーのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="4f83f-109">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="4f83f-110">GetStartAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="4f83f-110">GetStartAddress Method</span></span>](icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="4f83f-111">メモリ バッファーの開始アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="4f83f-111">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f83f-112">解説</span><span class="sxs-lookup"><span data-stu-id="4f83f-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f83f-113">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="4f83f-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="4f83f-114">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="4f83f-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f83f-115">要件</span><span class="sxs-lookup"><span data-stu-id="4f83f-115">Requirements</span></span>  

 <span data-ttu-id="4f83f-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f83f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f83f-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f83f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f83f-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f83f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f83f-119">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f83f-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f83f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f83f-120">See also</span></span>

- [<span data-ttu-id="4f83f-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f83f-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4f83f-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="4f83f-122">Debugging</span></span>](index.md)
