---
description: 詳細については、「ICorDebugAssembly2 インターフェイス」を参照してください。
title: ICorDebugAssembly2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2
helpviewer_keywords:
- ICorDebugAssembly2 interface [.NET Framework debugging]
ms.assetid: c0766e29-e573-4f9a-a928-167d1de5aa7e
topic_type:
- apiref
ms.openlocfilehash: 2a2d035329ba66153bfee83daa9501581f32842f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754122"
---
# <a name="icordebugassembly2-interface"></a><span data-ttu-id="250ea-103">ICorDebugAssembly2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="250ea-103">ICorDebugAssembly2 Interface</span></span>

<span data-ttu-id="250ea-104">アセンブリを表します。</span><span class="sxs-lookup"><span data-stu-id="250ea-104">Represents an assembly.</span></span> <span data-ttu-id="250ea-105">このインターフェイスは、というアセンブリインターフェイスの拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="250ea-105">This interface is an extension of the ICorDebugAssembly interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="250ea-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="250ea-106">Methods</span></span>  
  
|<span data-ttu-id="250ea-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="250ea-107">Method</span></span>|<span data-ttu-id="250ea-108">説明</span><span class="sxs-lookup"><span data-stu-id="250ea-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="250ea-109">IsFullyTrusted メソッド</span><span class="sxs-lookup"><span data-stu-id="250ea-109">IsFullyTrusted Method</span></span>](icordebugassembly2-isfullytrusted-method.md)|<span data-ttu-id="250ea-110">アセンブリにランタイムセキュリティシステムによる完全信頼が付与されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="250ea-110">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="250ea-111">解説</span><span class="sxs-lookup"><span data-stu-id="250ea-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="250ea-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="250ea-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="250ea-113">要件</span><span class="sxs-lookup"><span data-stu-id="250ea-113">Requirements</span></span>  

 <span data-ttu-id="250ea-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="250ea-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="250ea-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="250ea-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="250ea-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="250ea-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="250ea-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="250ea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="250ea-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="250ea-118">See also</span></span>

- [<span data-ttu-id="250ea-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="250ea-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
