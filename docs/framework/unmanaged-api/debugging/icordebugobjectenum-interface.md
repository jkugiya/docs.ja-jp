---
description: 詳細については、次のページを参照してください。
title: ICorDebugObjectEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
ms.openlocfilehash: d5cd8580bfa81af7d644c2fb11524a43a9062ddf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722244"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="3c1e8-103">ICorDebugObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c1e8-103">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="3c1e8-104">ICorDebugEnum メソッドを実装し、相対仮想アドレス (RVAs) によってオブジェクトの配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="3c1e8-104">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3c1e8-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3c1e8-105">Methods</span></span>  
  
|<span data-ttu-id="3c1e8-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="3c1e8-106">Method</span></span>|<span data-ttu-id="3c1e8-107">説明</span><span class="sxs-lookup"><span data-stu-id="3c1e8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3c1e8-108">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="3c1e8-108">Next Method</span></span>](icordebugobjectenum-next-method.md)|<span data-ttu-id="3c1e8-109">現在の位置から開始して、指定した数のオブジェクトの RVAs を列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="3c1e8-109">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c1e8-110">解説</span><span class="sxs-lookup"><span data-stu-id="3c1e8-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c1e8-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="3c1e8-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c1e8-112">要件</span><span class="sxs-lookup"><span data-stu-id="3c1e8-112">Requirements</span></span>  

 <span data-ttu-id="3c1e8-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c1e8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c1e8-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c1e8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c1e8-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c1e8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c1e8-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c1e8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c1e8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c1e8-117">See also</span></span>

- [<span data-ttu-id="3c1e8-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c1e8-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
