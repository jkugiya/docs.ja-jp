---
description: 詳細については、「ICorDebugProcess3 インターフェイス」を参照してください。
title: ICorDebugProcess3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3
helpviewer_keywords:
- ICorDebugProcess3 interface [.NET Framework debugging]
ms.assetid: ced9c82e-d7b0-4806-a151-98b6611d3097
topic_type:
- apiref
ms.openlocfilehash: 28b588bb4718f841e78b89ce44821971800b1f6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649976"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="dbb5c-103">ICorDebugProcess3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dbb5c-103">ICorDebugProcess3 Interface</span></span>

<span data-ttu-id="dbb5c-104">カスタムのデバッガー通知を制御します。</span><span class="sxs-lookup"><span data-stu-id="dbb5c-104">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dbb5c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="dbb5c-105">Methods</span></span>  
  
|<span data-ttu-id="dbb5c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="dbb5c-106">Method</span></span>|<span data-ttu-id="dbb5c-107">説明</span><span class="sxs-lookup"><span data-stu-id="dbb5c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dbb5c-108">SetEnableCustomNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="dbb5c-108">SetEnableCustomNotification Method</span></span>](icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="dbb5c-109">指定された型のカスタムデバッガー通知を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="dbb5c-109">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbb5c-110">解説</span><span class="sxs-lookup"><span data-stu-id="dbb5c-110">Remarks</span></span>  

 <span data-ttu-id="dbb5c-111">このインターフェイスは、ICorDebugProcess2 インターフェイスとインターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="dbb5c-111">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dbb5c-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="dbb5c-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbb5c-113">要件</span><span class="sxs-lookup"><span data-stu-id="dbb5c-113">Requirements</span></span>  

 <span data-ttu-id="dbb5c-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbb5c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbb5c-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbb5c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbb5c-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbb5c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbb5c-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbb5c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbb5c-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="dbb5c-118">See also</span></span>

- [<span data-ttu-id="dbb5c-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="dbb5c-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="dbb5c-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="dbb5c-120">Debugging</span></span>](index.md)
