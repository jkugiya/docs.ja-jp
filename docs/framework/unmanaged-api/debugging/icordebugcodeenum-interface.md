---
description: '詳細については、次を参照してください: いいね。'
title: ICorDebugCodeEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum
helpviewer_keywords:
- ICorDebugCodeEnum interface [.NET Framework debugging]
ms.assetid: b5589171-a4a0-4c00-bbdc-6e0a42233b75
topic_type:
- apiref
ms.openlocfilehash: c2bf2ae5bcdbb1cae3222d0b8ed1f775689d3b84
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710973"
---
# <a name="icordebugcodeenum-interface"></a><span data-ttu-id="79a57-103">ICorDebugCodeEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79a57-103">ICorDebugCodeEnum Interface</span></span>

<span data-ttu-id="79a57-104">"ICorDebugEnum" メソッドを実装し、"コード" 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="79a57-104">Implements "ICorDebugEnum" methods, and enumerates "ICorDebugCode" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79a57-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="79a57-105">Methods</span></span>  
  
|<span data-ttu-id="79a57-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="79a57-106">Method</span></span>|<span data-ttu-id="79a57-107">説明</span><span class="sxs-lookup"><span data-stu-id="79a57-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="79a57-108">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="79a57-108">Next Method</span></span>](icordebugcodeenum-next-method.md)|<span data-ttu-id="79a57-109">現在の位置から開始して、指定した数の `ICorDebugCode` インスタンスを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="79a57-109">Gets the specified number of `ICorDebugCode` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79a57-110">解説</span><span class="sxs-lookup"><span data-stu-id="79a57-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79a57-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="79a57-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79a57-112">要件</span><span class="sxs-lookup"><span data-stu-id="79a57-112">Requirements</span></span>  

 <span data-ttu-id="79a57-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79a57-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79a57-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79a57-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79a57-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79a57-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79a57-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79a57-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79a57-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="79a57-117">See also</span></span>

- [<span data-ttu-id="79a57-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="79a57-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
