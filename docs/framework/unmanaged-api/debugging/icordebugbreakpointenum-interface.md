---
description: '詳細については、次を参照してください: いいね。列挙型インターフェイス'
title: ICorDebugBreakpointEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum
helpviewer_keywords:
- ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type:
- apiref
ms.openlocfilehash: 71bd69c4fabba4a7d06f3b4cee5c0cf859d3c92b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711727"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="78df9-103">ICorDebugBreakpointEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78df9-103">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="78df9-104">ICorDebugEnum メソッドを実装し、ICorDebugBreakpoint 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="78df9-104">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78df9-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="78df9-105">Methods</span></span>  
  
|<span data-ttu-id="78df9-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="78df9-106">Method</span></span>|<span data-ttu-id="78df9-107">説明</span><span class="sxs-lookup"><span data-stu-id="78df9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="78df9-108">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="78df9-108">Next Method</span></span>](icordebugbreakpointenum-next-method.md)|<span data-ttu-id="78df9-109">現在の位置から開始して、指定した数の `ICorDebugBreakpoint` インスタンスを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="78df9-109">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78df9-110">解説</span><span class="sxs-lookup"><span data-stu-id="78df9-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78df9-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="78df9-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78df9-112">要件</span><span class="sxs-lookup"><span data-stu-id="78df9-112">Requirements</span></span>  

 <span data-ttu-id="78df9-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78df9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78df9-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78df9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78df9-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78df9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78df9-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78df9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78df9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="78df9-117">See also</span></span>

- [<span data-ttu-id="78df9-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="78df9-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
