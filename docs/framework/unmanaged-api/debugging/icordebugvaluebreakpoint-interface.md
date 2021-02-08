---
description: 詳細について
title: ICorDebugValueBreakpoint インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
ms.openlocfilehash: ff53b1f6e1557a3e98cc642f80eaaa2feaeac473
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790686"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="301d4-103">ICorDebugValueBreakpoint インターフェイス</span><span class="sxs-lookup"><span data-stu-id="301d4-103">ICorDebugValueBreakpoint Interface</span></span>

<span data-ttu-id="301d4-104">ICorDebugBreakpoint インターフェイスを拡張して、特定の値にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="301d4-104">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="301d4-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="301d4-105">Methods</span></span>  
  
|<span data-ttu-id="301d4-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="301d4-106">Method</span></span>|<span data-ttu-id="301d4-107">説明</span><span class="sxs-lookup"><span data-stu-id="301d4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="301d4-108">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="301d4-108">GetValue Method</span></span>](icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="301d4-109">ブレークポイントが設定されたオブジェクトの値を表す、ICorDebugValue オブジェクトへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="301d4-109">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="301d4-110">解説</span><span class="sxs-lookup"><span data-stu-id="301d4-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="301d4-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="301d4-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="301d4-112">要件</span><span class="sxs-lookup"><span data-stu-id="301d4-112">Requirements</span></span>  

 <span data-ttu-id="301d4-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="301d4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="301d4-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="301d4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="301d4-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="301d4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="301d4-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="301d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="301d4-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="301d4-117">See also</span></span>

- [<span data-ttu-id="301d4-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="301d4-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
