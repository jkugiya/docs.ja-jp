---
description: '詳細情報: モジュールの列挙'
title: ICorDebugModuleEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
ms.openlocfilehash: c9c847f926984ed2b8aea87463e351cd97a62c80
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801047"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="ccb31-103">ICorDebugModuleEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ccb31-103">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="ccb31-104">ICorDebugEnum メソッドを実装し、モジュール配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="ccb31-104">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ccb31-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ccb31-105">Methods</span></span>  
  
|<span data-ttu-id="ccb31-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="ccb31-106">Method</span></span>|<span data-ttu-id="ccb31-107">説明</span><span class="sxs-lookup"><span data-stu-id="ccb31-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ccb31-108">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="ccb31-108">Next Method</span></span>](icordebugmoduleenum-next-method.md)|<span data-ttu-id="ccb31-109">現在の位置から開始して、指定した数の `ICorDebugModule` インスタンスを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="ccb31-109">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccb31-110">解説</span><span class="sxs-lookup"><span data-stu-id="ccb31-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ccb31-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="ccb31-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccb31-112">要件</span><span class="sxs-lookup"><span data-stu-id="ccb31-112">Requirements</span></span>  

 <span data-ttu-id="ccb31-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ccb31-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccb31-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ccb31-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ccb31-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccb31-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccb31-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccb31-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb31-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ccb31-117">See also</span></span>

- [<span data-ttu-id="ccb31-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ccb31-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
