---
description: 詳細については、「ICorDebugValue3 インターフェイス」を参照してください。
title: ICorDebugValue3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
ms.openlocfilehash: e5868b91d23426a2d8dd8fed87b13ec61fef95ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794651"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="489da-103">ICorDebugValue3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="489da-103">ICorDebugValue3 Interface</span></span>

<span data-ttu-id="489da-104">"ICorDebugValue" インターフェイスと "ICorDebugValue2" インターフェイスを拡張して、2 GB を超える配列のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="489da-104">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="489da-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="489da-105">Methods</span></span>  
  
|<span data-ttu-id="489da-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="489da-106">Method</span></span>|<span data-ttu-id="489da-107">説明</span><span class="sxs-lookup"><span data-stu-id="489da-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="489da-108">GetSize64 メソッド</span><span class="sxs-lookup"><span data-stu-id="489da-108">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)|<span data-ttu-id="489da-109">このオブジェクトのサイズ (バイト単位) を取得し `ICorDebugValue3` ます。</span><span class="sxs-lookup"><span data-stu-id="489da-109">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="489da-110">解説</span><span class="sxs-lookup"><span data-stu-id="489da-110">Remarks</span></span>  

 <span data-ttu-id="489da-111">[ICorDebugValue:: GetSize](icordebugvalue3-getsize64-method.md)メソッドは、0 ~ 2147483647 バイトの範囲のオブジェクトサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="489da-111">The [ICorDebugValue::GetSize](icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="489da-112">.NET Framework 4.5 では、配列のサイズが 2 GB を超える場合があります。</span><span class="sxs-lookup"><span data-stu-id="489da-112">In the .NET Framework 4.5, the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="489da-113">`ICorDebugValue3`インターフェイスを使用すると、これらの配列のサイズを決定できます。</span><span class="sxs-lookup"><span data-stu-id="489da-113">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="489da-114">要件</span><span class="sxs-lookup"><span data-stu-id="489da-114">Requirements</span></span>  

 <span data-ttu-id="489da-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="489da-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="489da-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="489da-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="489da-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="489da-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="489da-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="489da-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="489da-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="489da-119">See also</span></span>

- [<span data-ttu-id="489da-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="489da-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="489da-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="489da-121">Debugging</span></span>](index.md)
