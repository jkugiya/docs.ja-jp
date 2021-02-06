---
description: '詳細については、次を参照してください: いいね。'
title: ICorDebugThreadEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum
helpviewer_keywords:
- ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: 796de687-7dd4-4b7b-a10b-8bf22dc7779f
topic_type:
- apiref
ms.openlocfilehash: 088b9bd56ae0049ad5f287b07cd2857f70a496c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658478"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="cf69f-103">ICorDebugThreadEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf69f-103">ICorDebugThreadEnum Interface</span></span>

<span data-ttu-id="cf69f-104">ICorDebugEnum メソッドを実装し、の各スレッド配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="cf69f-104">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf69f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="cf69f-105">Methods</span></span>  
  
|<span data-ttu-id="cf69f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="cf69f-106">Method</span></span>|<span data-ttu-id="cf69f-107">説明</span><span class="sxs-lookup"><span data-stu-id="cf69f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf69f-108">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="cf69f-108">Next Method</span></span>](icordebugthreadenum-next-method.md)|<span data-ttu-id="cf69f-109">現在の位置から開始して、指定した数の `ICorDebugThread` インスタンスを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="cf69f-109">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf69f-110">解説</span><span class="sxs-lookup"><span data-stu-id="cf69f-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf69f-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="cf69f-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf69f-112">要件</span><span class="sxs-lookup"><span data-stu-id="cf69f-112">Requirements</span></span>  

 <span data-ttu-id="cf69f-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf69f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf69f-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf69f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf69f-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf69f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf69f-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf69f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf69f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf69f-117">See also</span></span>

- [<span data-ttu-id="cf69f-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf69f-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
