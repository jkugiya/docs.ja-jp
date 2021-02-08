---
description: 詳細については、「ICorDebugILFrame3 インターフェイス」を参照してください。
title: ICorDebugILFrame3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
ms.openlocfilehash: a34a3f0941871a2d0a63fb2d9f78ccb7ff455866
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791258"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="7513f-103">ICorDebugILFrame3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7513f-103">ICorDebugILFrame3 Interface</span></span>

<span data-ttu-id="7513f-104">関数の戻り値をカプセル化するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="7513f-104">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="7513f-105">`ICorDebugILFrame3` は、ICorDebugILFrame2 インターフェイスとインターフェイスを論理的に拡張したものです。</span><span class="sxs-lookup"><span data-stu-id="7513f-105">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7513f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="7513f-106">Methods</span></span>  
  
|<span data-ttu-id="7513f-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="7513f-107">Method</span></span>|<span data-ttu-id="7513f-108">説明</span><span class="sxs-lookup"><span data-stu-id="7513f-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7513f-109">GetReturnValueForILOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="7513f-109">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="7513f-110">関数の戻り値をカプセル化する ICorDebugValue オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="7513f-110">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7513f-111">解説</span><span class="sxs-lookup"><span data-stu-id="7513f-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7513f-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="7513f-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7513f-113">要件</span><span class="sxs-lookup"><span data-stu-id="7513f-113">Requirements</span></span>  

 <span data-ttu-id="7513f-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7513f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7513f-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7513f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7513f-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7513f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7513f-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7513f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7513f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7513f-118">See also</span></span>

- [<span data-ttu-id="7513f-119">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7513f-119">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="7513f-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7513f-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
