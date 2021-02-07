---
description: 詳細については、「ICorDebugCode3 インターフェイス」を参照してください。
title: ICorDebugCode3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
ms.openlocfilehash: 378141395ab4d23e3e33a84c3b14ca4a75d847dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764841"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="d954c-103">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d954c-103">ICorDebugCode3 Interface</span></span>

<span data-ttu-id="d954c-104">"" のコード "と" ICorDebugCode2 "を拡張して、マネージ戻り値に関する情報を提供するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d954c-104">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d954c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d954c-105">Methods</span></span>  
  
|<span data-ttu-id="d954c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d954c-106">Method</span></span>|<span data-ttu-id="d954c-107">説明</span><span class="sxs-lookup"><span data-stu-id="d954c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d954c-108">GetReturnValueLiveOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="d954c-108">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="d954c-109">指定した IL オフセットについて、デバッガーが関数からの戻り値を取得できるように、ブレークポイントを配置する必要があるネイティブなオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="d954c-109">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d954c-110">解説</span><span class="sxs-lookup"><span data-stu-id="d954c-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d954c-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d954c-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d954c-112">要件</span><span class="sxs-lookup"><span data-stu-id="d954c-112">Requirements</span></span>  

 <span data-ttu-id="d954c-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d954c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d954c-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d954c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d954c-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d954c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d954c-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d954c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d954c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d954c-117">See also</span></span>

- [<span data-ttu-id="d954c-118">ICorDebugILFrame3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d954c-118">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
- [<span data-ttu-id="d954c-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d954c-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
