---
description: '詳細情報: モジュールのブレークポイントインターフェイス'
title: ICorDebugModuleBreakpoint インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint
helpviewer_keywords:
- ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type:
- apiref
ms.openlocfilehash: c864850400471c9a3580de9bb94262c62656edf0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790751"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="d0bd0-103">ICorDebugModuleBreakpoint インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d0bd0-103">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="d0bd0-104">特定のモジュールへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="d0bd0-104">Provides access to specific modules.</span></span> <span data-ttu-id="d0bd0-105">このインターフェイスは、ICorDebugBreakpoint インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="d0bd0-105">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0bd0-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d0bd0-106">Methods</span></span>  
  
|<span data-ttu-id="d0bd0-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="d0bd0-107">Method</span></span>|<span data-ttu-id="d0bd0-108">説明</span><span class="sxs-lookup"><span data-stu-id="d0bd0-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0bd0-109">GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="d0bd0-109">GetModule Method</span></span>](icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="d0bd0-110">このブレークポイントが設定されているモジュールを参照するモジュールへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d0bd0-110">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0bd0-111">解説</span><span class="sxs-lookup"><span data-stu-id="d0bd0-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0bd0-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d0bd0-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0bd0-113">要件</span><span class="sxs-lookup"><span data-stu-id="d0bd0-113">Requirements</span></span>  

 <span data-ttu-id="d0bd0-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0bd0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0bd0-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0bd0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0bd0-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0bd0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0bd0-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0bd0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0bd0-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0bd0-118">See also</span></span>

- [<span data-ttu-id="d0bd0-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d0bd0-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
