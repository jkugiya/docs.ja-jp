---
description: 詳細については、「ICorDebugInternalFrame2 インターフェイス」を参照してください。
title: ICorDebugInternalFrame2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2
helpviewer_keywords:
- ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type:
- apiref
ms.openlocfilehash: 3edc666c043513562b2fcece478b2879f294ce33
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791102"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="17cb7-103">ICorDebugInternalFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17cb7-103">ICorDebugInternalFrame2 Interface</span></span>

<span data-ttu-id="17cb7-104">内部フレームに関する情報を提供します。この情報には、スタック アドレス、および ICorDebugFrame オブジェクトを基準にした位置などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="17cb7-104">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17cb7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="17cb7-105">Methods</span></span>  
  
|<span data-ttu-id="17cb7-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="17cb7-106">Method</span></span>|<span data-ttu-id="17cb7-107">説明</span><span class="sxs-lookup"><span data-stu-id="17cb7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17cb7-108">GetFrameAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="17cb7-108">GetFrameAddress Method</span></span>](icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="17cb7-109">内部フレームのスタックアドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="17cb7-109">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="17cb7-110">IsCloserToLeaf メソッド</span><span class="sxs-lookup"><span data-stu-id="17cb7-110">IsCloserToLeaf Method</span></span>](icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="17cb7-111">内部フレームが、指定されたのは、指定されたとしての `this` オブジェクトよりもリーフの近くにあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="17cb7-111">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17cb7-112">解説</span><span class="sxs-lookup"><span data-stu-id="17cb7-112">Remarks</span></span>  

 <span data-ttu-id="17cb7-113">このインターフェイスは、によって、、の各フレームインターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="17cb7-113">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17cb7-114">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="17cb7-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17cb7-115">要件</span><span class="sxs-lookup"><span data-stu-id="17cb7-115">Requirements</span></span>  

 <span data-ttu-id="17cb7-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17cb7-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17cb7-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17cb7-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17cb7-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17cb7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17cb7-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17cb7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17cb7-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="17cb7-120">See also</span></span>

- [<span data-ttu-id="17cb7-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="17cb7-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="17cb7-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="17cb7-122">Debugging</span></span>](index.md)
