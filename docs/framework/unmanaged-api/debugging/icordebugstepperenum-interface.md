---
description: 詳細については、次をご覧ください。
title: ICorDebugStepperEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum
helpviewer_keywords:
- ICorDebugStepperEnum interface [.NET Framework debugging]
ms.assetid: 988718c1-1a4a-40f2-a04c-7d67e5cfe1e2
topic_type:
- apiref
ms.openlocfilehash: d645b20d54af6898afe00d19029747f9d53cdbe4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717525"
---
# <a name="icordebugstepperenum-interface"></a><span data-ttu-id="e6266-103">ICorDebugStepperEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6266-103">ICorDebugStepperEnum Interface</span></span>

<span data-ttu-id="e6266-104">ICorDebugEnum メソッドを実装し、ICorDebugStepper 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="e6266-104">Implements ICorDebugEnum methods, and enumerates ICorDebugStepper arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e6266-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e6266-105">Methods</span></span>  
  
|<span data-ttu-id="e6266-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="e6266-106">Method</span></span>|<span data-ttu-id="e6266-107">説明</span><span class="sxs-lookup"><span data-stu-id="e6266-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e6266-108">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="e6266-108">Next Method</span></span>](icordebugstepperenum-next-method.md)|<span data-ttu-id="e6266-109">現在の位置から開始して、指定した数の `ICorDebugStepper` インスタンスを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="e6266-109">Gets the specified number of `ICorDebugStepper` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6266-110">解説</span><span class="sxs-lookup"><span data-stu-id="e6266-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6266-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e6266-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6266-112">要件</span><span class="sxs-lookup"><span data-stu-id="e6266-112">Requirements</span></span>  

 <span data-ttu-id="e6266-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6266-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6266-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6266-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6266-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6266-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6266-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6266-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6266-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6266-117">See also</span></span>

- [<span data-ttu-id="e6266-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6266-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
