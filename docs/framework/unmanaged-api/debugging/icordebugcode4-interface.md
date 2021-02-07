---
description: 詳細については、「ICorDebugCode4 インターフェイス」を参照してください。
title: ICorDebugCode4 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugCode4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4
helpviewer_keywords:
- ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type:
- apiref
ms.openlocfilehash: 1276db5c55c3d98e5ffa379f6126f700d93c1670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764724"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="56a64-103">ICorDebugCode4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56a64-103">ICorDebugCode4 Interface</span></span>

<span data-ttu-id="56a64-104">デバッガーが関数のローカル変数と引数を列挙できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="56a64-104">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56a64-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="56a64-105">Methods</span></span>  
  
|<span data-ttu-id="56a64-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="56a64-106">Method</span></span>|<span data-ttu-id="56a64-107">説明</span><span class="sxs-lookup"><span data-stu-id="56a64-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56a64-108">EnumerateVariableHomes メソッド</span><span class="sxs-lookup"><span data-stu-id="56a64-108">EnumerateVariableHomes Method</span></span>](icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="56a64-109">関数のローカル変数および引数に対する列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="56a64-109">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56a64-110">解説</span><span class="sxs-lookup"><span data-stu-id="56a64-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56a64-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="56a64-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56a64-112">要件</span><span class="sxs-lookup"><span data-stu-id="56a64-112">Requirements</span></span>  

 <span data-ttu-id="56a64-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56a64-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56a64-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56a64-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56a64-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56a64-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56a64-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56a64-116">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56a64-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="56a64-117">See also</span></span>

- [<span data-ttu-id="56a64-118">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56a64-118">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="56a64-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="56a64-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
