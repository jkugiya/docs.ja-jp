---
description: 詳細については、「ICorDebugUnmanagedCallback インターフェイス」を参照してください。
title: ICorDebugUnmanagedCallback インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback
helpviewer_keywords:
- ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type:
- apiref
ms.openlocfilehash: 6d8aa398ff7121e360c3da66671781cd169b6228
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690549"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="1a43a-103">ICorDebugUnmanagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1a43a-103">ICorDebugUnmanagedCallback Interface</span></span>

<span data-ttu-id="1a43a-104">共通言語ランタイム (CLR) に直接関連しないネイティブイベントの通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="1a43a-104">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a43a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1a43a-105">Methods</span></span>  
  
|<span data-ttu-id="1a43a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="1a43a-106">Method</span></span>|<span data-ttu-id="1a43a-107">説明</span><span class="sxs-lookup"><span data-stu-id="1a43a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a43a-108">DebugEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="1a43a-108">DebugEvent Method</span></span>](icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="1a43a-109">ネイティブイベントが発生したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="1a43a-109">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a43a-110">解説</span><span class="sxs-lookup"><span data-stu-id="1a43a-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a43a-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1a43a-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a43a-112">要件</span><span class="sxs-lookup"><span data-stu-id="1a43a-112">Requirements</span></span>  

 <span data-ttu-id="1a43a-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a43a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a43a-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a43a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a43a-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a43a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a43a-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a43a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a43a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a43a-117">See also</span></span>

- [<span data-ttu-id="1a43a-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1a43a-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
